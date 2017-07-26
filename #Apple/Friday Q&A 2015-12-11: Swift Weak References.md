# Friday Q&A 2015-12-11: Swift Weak References

_Captured: 2015-12-12 at 18:30 from [www.mikeash.com](https://www.mikeash.com/pyblog/friday-qa-2015-12-11-swift-weak-references.html)_

In case you have been on Mars, in a cave, with your eyes shut and your fingers in your ears, [Swift has been open sourced](https://swift.org). This makes it convenient to explore one of the more interesting features of Swift's implementation: how weak references work.

## **Weak References**

In a garbage collected or reference counted language, a strong reference is one which keeps the target object alive. A weak reference is one which doesn't. An object can't be destroyed while there are strong references to it, but it can be destroyed while there are weak references to it.

When we say "weak reference," we usually mean a _zeroing_ weak reference. That is, when the target of the weak reference is destroyed, the weak reference becomes `nil`. It's also possible to have non-zeroing weak references, which trap, crash, or invoke nasal demons. This is what you get when you use `unsafe_unretained` in Objective-C, or `unowned` in Swift. (Note that Objective-C gives us the nasal-demons version, while Swift takes care to crash reliably.)

Zeroing weak references are handy to have around, and they're extremely useful in reference counted languages. They allow circular references to exist without creating retain cycles, and without having to manually break back references. They're so useful that I [implemented my own version of weak references](https://www.mikeash.com/pyblog/introducing-mazeroingweakref.html) back before Apple introduced ARC and made language-level weak references available outside of garbage collected code.

## **How Does It Work?**
  
The typical implementation for zeroing weak references is to keep a list of all the weak references to each object. When a weak reference is created to an object, that reference is added to the list. When that reference is reassigned or goes out of scope, it's removed from the list. When an object is destroyed, all of the references in the list are zeroed. In a multithreaded environment (i.e. all of them these days), the implementation must synchronize obtaining a weak reference and destroying an object to avoid race conditions when one thread releases the last strong reference to an object at the same time another thread tries to load a weak reference to it.

In my implementation, each weak reference is a full-fledged object. The list of weak references is just a set of weak reference objects. This adds some inefficiency because of the extra indirection and memory use, but it's convenient to have the references be full objects.

In Apple's Objective-C implementation, each weak reference is a plain pointer to the target object. Rather than reading and writing the pointers directly, the compiler uses helper functions. When storing to a weak pointer, the store function registers the pointer location as a weak reference to the target. When reading from a weak pointer, the read function integrates with the reference counting system to ensure that it never returns a pointer to an object that's being deallocated.

## **Zeroing in Action**

Let's build a bit of code so we can watch this stuff happen.

We want to be able to dump the contents of an object's memory. This function takes a region of memory, breaks it into pointer-sized chunks, and turns the whole thing into a convenient hex string:
    
    
        func contents(ptr: UnsafePointer<Void>, _ length: Int) -> String {
            let wordPtr = UnsafePointer<UInt>(ptr)
            let words = length / sizeof(UInt.self)
            let wordChars = sizeof(UInt.self) * 2
    
            let buffer = UnsafeBufferPointer<UInt>(start: wordPtr, count: words)
            let wordStrings = buffer.map({ word -> String in
                var wordString = String(word, radix: 16)
                while wordString.characters.count < wordChars {
                    wordString = "0" + wordString
                }
                return wordString
            })
            return wordStrings.joinWithSeparator(" ")
        }
    

The next function creates a dumper function for an object. Call it once with an object, and it returns a function that will dump the content of this object. Internally, it saves an `UnsafePointer` to the object, rather than using a normal reference. This ensures that it doesn't interact with the language's reference counting system. It also allows us to dump the memory of an object after it has been destroyed, which will come in handy later.

Here's a class that exists to hold a weak reference so we can inspect it. I added dummy variables on either side to make it clear where the weak reference lives in the memory dump:

Let's give it a try! We'll start by creating a referer and dumping it:

This prints:

We can see the `isa` at the beginning, followed by some other internal fields. `dummy1` occupies the 4th chunk, and `dummy2` occupies the 6th. We can see that the weak reference in between them is zero, as expected.

Let's point it at an object now, and see what it looks like. I'll do this inside a `do` block so we can control when the target goes out of scope and is destroyed:

This prints:

As expected, the pointer to the target is stored directly in the weak reference. Let's dump it again after the target is destroyed at the end of the `do` block:

It gets zeroed out. Perfect!

Just for fun, let's repeat the experiment with a pure Swift object as the target. It's not nice to bring Objective-C into the picture when it's not necessary. Here's a pure Swift target:

Let's try it out:

The target starts out zeroed as expected, then gets assigned:

Then when the target goes away, the reference should be zeroed:

Oh dear. It didn't get zeroed. Maybe the target didn't get destroyed. Something must be keeping it alive! Let's double-check:

Running the code again, we get:

So it is going away, but the weak reference isn't being zeroed out. How about that, we found a bug in Swift! It's pretty amazing that it hasn't been fixed after all this time. You'd think somebody would have noticed before now. Let's go ahead and generate a nice crash by accessing the reference, then we can file a bug with the Swift project:

Here comes the crash:

Oh dear squared! Where's the kaboom? There was supposed to be an Earth-shattering kaboom! The output says everything is working after all, but we can see clearly from the dump that it isn't working at all.

Let's inspect everything really carefully. Here's a revised version of `WeakTarget` with a dummy variable to make it nicer to dump its contents as well:

Here's some new code that runs through the same procedure and dumps both objects at every step:

Let's walk through the output. The referer starts out life as before, with a zeroed-out `target` field:

The target starts out life as a normal object, with various header fields followed by our dummy field:

Upon assigning to the `target` field, we can see the pointer value get filled in:

The target is much as before, but one of the header fields went up by `2`:

The target gets destroyed as expected:

We see the referer object still has a pointer to the target:

And the target itself still looks very much alive, although a different header field went down by `2` compared to the last time we saw it:

Accessing the `target` field produces `nil` even though it wasn't zeroed out:

Dumping the referer again shows that the mere act of accessing the `target` field has altered it. _Now_ it's zeroed out:

The target is now totally obliterated:

More and more interesting. We saw header fields incrementing and decremeting a bit, let's see if we can make that happen more:

This prints:

We can see that the first number in this header field goes up by `2` with every new weak reference. The second number goes up by `4` with every new strong reference.

To recap, here's what we've seen so far:

  * Weak pointers look like regular pointers in memory.
  * When a weak target's `deinit` runs, the target is _not_ deallocated, and the weak pointer is _not_ zeroed.
  * When the weak pointer is accessed after the target's `deinit` runs, it is zeroed on access and the weak target is deallocated.
  * The weak target contains a reference count for weak references, separate from the count of strong references.

## **Swift Code**

Now that Swift is open source, we can actually go relate this observed behavior to the source code.

The Swift standard library represents objects allocated on the heap with a `HeapObject` type located in [stdlib/public/SwiftShims/HeapObject.h](https://github.com/apple/swift/blob/swift-2.2-SNAPSHOT-2015-12-01-b/stdlib/public/SwiftShims/HeapObject.h#L33). It looks like:

The `metadata` field is the Swift equivalent of the `isa` field in Objective-C, and in fact it's compatible. Then there are these `NON_OBJC_MEMBERS` defined in a macro:

Well, look at that! There are our two reference counts.

(Bonus question: why is the strong count first here, while in the dumps above the weak count was first?)

The reference counts are managed by a bunch of functions located in [stdlib/public/runtime/HeapObject.cpp](https://github.com/apple/swift/blob/swift-2.2-SNAPSHOT-2015-12-01-b/stdlib/public/runtime/HeapObject.cpp). For example, here's `swift_retain`:

There's a bunch of indirection, but it eventually calls through to this inline function in the header:

As you'd expect, it increments the reference count. Here's the implementation of `increment`:

`RC_ONE` comes from an `enum`:

We can see why the count went up by `4` with each new strong reference. The first two bits of the field are used for flags. Looking back at the dumps, we can see those flags in action. Here's a weak target before and after the last strong reference went away:

The field went from `4`, denoting a reference count of 1 and no flags, to `2`, denoting a reference count of zero and `RC_DEALLOCATING_FLAG` set. This post-`deinit` object is placed in some sort of `DEALLOCATING` limbo.

(Incidentally, what is `RC_PINNED_FLAG` for? I poked through the code base and couldn't figure out anything beyond that it indicates a "pinned object," which is already pretty obvious from the name. If you figure it out or have an informed guess, please post a comment.)

Let's check out the weak reference count's implementation, while we're here. It has the same sort of `enum`:

That's where the `2` comes from: there's space reserved for one flag, which is currently unused. Oddly, the comment in this code appears to be incorrect, as `RC_ONE` here is equal to `2`, whereas the strong `RC_ONE` is equal to `4`. I'd guess they were once equal, and then it was changed and the comment wasn't updated. Just goes to show that comments are useless and you shouldn't ever write them.

How does all of this tie in to loading weak references? That's handled by a [function called `swift_weakLoadStrong`](https://github.com/apple/swift/blob/swift-2.2-SNAPSHOT-2015-12-01-b/stdlib/public/runtime/HeapObject.cpp#L636):

From this, it's clear how the lazy zeroing works. When loading a weak reference, if the target is deallocating, zero out the reference. Otherwise, try to retain the target, and return it. Digging a bit further, we can see how `swift_weakRelease` deallocates the object's memory if it's the last reference:

(Note: if you're looking at the code in the repository, the naming has changed to use "unowned" instead of "weak" for most cases. The naming above is current as of the latest snapshot as of the time of this writing, but development moves on. You can view the repository as of the 2.2 snapshot to see it as I have it here, or grab the latest but be aware of the naming changes, and possibly implementation changes.)

## **Putting it All Together**

We've seen it all from top to bottom now. What's the high-level view on how Swift weak references actually work?

  1. Weak references are just pointers to the target object.
  2. Weak references are _not_ individually tracked the way they are in Objective-C.
  3. Instead, each Swift object has a weak reference count next to its strong reference count.
  4. Swift decouples object deinitialization from object deallocation. An object can be deinitialized, freeing its external resources, without deallocating the memory occupied by the object itself.
  5. When a Swift object's strong reference count reaches zero while the weak count is still greater than zero, the object is deinitialized but not deallocated.
  6. This means that weak pointers to a deallocated object _are still valid pointers_ and can be dereferenced without crashing or loading garbage data. They merely point to an object in a zombie state.
  7. When a weak reference is loaded, the runtime checks the target's state. If the target is a zombie, then it zeroes the weak reference, decrements the weak reference count, and returns `nil`.
  8. When all weak references to a zombie object are zeroed out, the zombie is deallocated.

This design has some interesting consequences compared to Objective-C's approach:

  * There is no list of weak references maintained anywhere. This simplifies code and improves performance.
  * There is no race condition between zeroing a weak reference on one thread, and loading that weak reference on another thread. This means that loading a weak reference and destroying a weakly-referenced object can be done without acquiring locks. This improves performance.
  * Weak references to an object will cause that object's memory to remain allocated even after there are no strong references to it, until all weak references are either loaded or discarded. This temporarily increases memory usage. Note that the effect is small, because while the target object's memory remains allocated, it's only the memory for the instance itself. All external resources (including storage for `Array` or `Dictionary` properties) are freed when the last strong reference goes away. A weak reference can cause a single instance to stay allocated, but not a whole tree of objects.
  * Extra memory is required to store the weak reference count on every object. In practice it appears that this is inconsequential on 64-bit. The header fields want to occupy a whole number of pointer-sized chunks, and the strong and weak reference counts share one. If the weak reference count weren't there, the strong reference count would just occupy all 64 bits by itself. It's possible that the strong reference could otherwise be moved into the `isa` by using a [non-pointer `isa`](http://www.sealiesoftware.com/blog/archive/2013/09/24/objc_explain_Non-pointer_isa.html), but I'm not sure how important that is or how it's going to shake out in the long term. For 32-bit, it looks like the weak count increases object sizes by four bytes. The importance of 32-bit is diminishing by the day, however.
  * Because accessing a weak pointer is so cheap, the same mechanism can be used to implement reliable semantics for `unowned`. Under the hood, `unowned` works exactly like `weak`, except that it fails loudly if the target went away rather than returning `nil`. In Objective-C, `__unsafe_unretained` is implemented as a raw pointer with undefined behavior if you access it late because it's supposed to be fast, and loading a weak pointer is somewhat slow.

## **Conclusion**

Swift's weak pointers use an interesting approach that provides correctness, speed, and low memory overhead. By tracking a weak reference count for each object and decoupling object deinitialization from objct deallocation, weak references can be resolved both safely and quickly. The availability of the source code for the standard library lets us see exactly what's going on at the source level, instead of groveling through disassemblies and memory dumps as we often do. Of course, as you can see above, it's hard to break that habit fully.

That's it for today. Come back next time for more goodies. That might be a few weeks, as the holidays intervene, but I'm going to shoot for one shortish article before that happens. In any case, keep your suggestions for topics coming in. Friday Q&A is driven by reader ideas, so if you have one you'd like to see covered, [let me know](mailto:mike@mikeash.com)!

Comments: [Comments RSS feed for this page](https://www.mikeash.com/commentsrss.py?page=pyblog/friday-qa-2015-12-11-swift-weak-references.html)

Add your thoughts, post a comment:

Spam and off-topic posts will be deleted without notice. Culprits may be publicly humiliated at my sole discretion.
