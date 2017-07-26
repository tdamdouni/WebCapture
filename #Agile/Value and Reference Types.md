# Value and Reference Types

_Captured: 2015-12-03 at 19:32 from [developer.apple.com](https://developer.apple.com/swift/blog/?id=10)_

Types in Swift fall into one of two categories: first, "value types", where each instance keeps a unique copy of its data, usually defined as a struct, enum, or tuple. The second, "reference types", where instances share a single copy of the data, and the type is usually defined as a class. In this post we explore the merits of value and reference types, and how to choose between them.

###  What's the Difference? 

The most basic distinguishing feature of a _value type_ is that copying -- the effect of assignment, initialization, and argument passing -- creates an _independent instance_ with its own unique copy of its data:
    
    
    // Value type example
    struct S { var data: Int = -1 }
    var a = S()
    var b = a						// a is copied to b
    a.data = 42						// Changes a, not b
    println("\(a.data), \(b.data)")	// prints "42, -1"

Copying a reference, on the other hand, implicitly creates a shared instance. After a copy, two variables then refer to a single instance of the data, so modifying data in the second variable also affects the original, e.g.:
    
    
    // Reference type example
    class C { var data: Int = -1 }
    var x = C()
    var y = x						// x is copied to y
    x.data = 42						// changes the instance referred to by x (and y)
    println("\(x.data), \(y.data)")	// prints "42, 42"

### The Role of Mutation in Safety

One of the primary reasons to choose value types over reference types is the ability to more easily reason about your code. If you always get a unique, copied instance, you can trust that no other part of your app is changing the data under the covers. This is especially helpful in multi-threaded environments where a different thread could alter your data out from under you. This can create nasty bugs that are extremely hard to debug.

Because the difference is defined in terms of what happens when you change data, there's one case where value and reference types overlap: when instances have no writable data. In the absence of mutation, values and references act exactly the same way.

You may be thinking that it could be valuable, then, to have a case where a class is completely immutable. This would make it easier to use Cocoa NSObject objects, while maintaining the benefits of value semantics. Today, you can write an immutable class in Swift by using only immutable stored properties and avoiding exposing any APIs that can modify state. In fact, many common Cocoa classes, such as NSURL, are designed as immutable classes. However, Swift does not currently provide any language mechanism to enforce class immutability (e.g. on subclasses) the way it enforces immutability for struct and enum.

### How to Choose?

So if you want to build a new type, how do you decide which kind to make? When you're working with Cocoa, many APIs expect subclasses of NSObject, so you have to use a class. For the other cases, here are some guidelines:

Use a value type when:

  * Comparing instance data with == makes sense
  * You want copies to have independent state
  * The data will be used in code across multiple threads

Use a reference type (e.g. use a class) when:

  * Comparing instance identity with === makes sense
  * You want to create shared, mutable state

In Swift, Array, String, and Dictionary are all value types. They behave much like a simple int value in C, acting as a unique instance of that data. You don't need to do anything special -- such as making an explicit copy -- to prevent other code from modifying that data behind your back. Importantly, you can safely pass copies of values across threads without synchronization. In the spirit of improving safety, this model will help you write more predictable code in Swift.
