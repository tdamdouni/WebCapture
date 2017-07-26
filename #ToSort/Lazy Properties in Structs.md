# Lazy Properties in Structs

_Captured: 2015-12-17 at 19:53 from [oleb.net](http://oleb.net/blog/2015/12/lazy-properties-in-structs-swift/)_

Swift's `[lazy` keyword](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Properties.html#//apple_ref/doc/uid/TP40014097-CH14-ID257) allows you to define a property whose initial value is computed when it is first accessed. As an example, imagine a struct to represent an image. The image's metadata dictionary might be expensive to create, and we want to defer this cost until the data is needed. We can declare a `lazy var` like this:
    
    
    1
    2
    3
    4
    5
    6
    7
    
    
    struct Image {
        lazy var metadata: [String:AnyObject] = {
            // Load image file and parse metadata, expensive
            // ...
            return ...
        }()
    }
    

Note that we have to use `var` in the property declaration. `let` constants must always have a value before instance initialization is complete, and this is not guaranteed for lazy variables.

Accessing the lazy property is a mutating operation because the property's initial value is set on the first access. When a struct (which is a value type) contains a lazy property, any owner of the struct that accesses the lazy property must therefore declare the struct as a variable, too, because accessing the property means potentially mutating its container. So this is not allowed:
    
    
    1
    2
    3
    
    
    let image = Image()
    print(image.metadata)
    // error: Cannot use mutating getter on immutable value: 'image' is a 'let' constant.
    

We could force users of our `Image` type to use `var`, but that could be inconvenient (for example, if it is used [as a function parameter](https://github.com/apple/swift-evolution/blob/master/proposals/0003-remove-var-parameters-patterns.md)) or confusing (because getters are usually not mutating).

# Box all the things

Another option is to wrap the lazy value in a class, similar to the often-used `[Box` type](https://github.com/robrix/Box). Because classes are reference types, a struct can contain a `let` constant to a class instance and still be immutable even if the referenced object itself is mutated.

Let's first define an enum, called `LazyValue`, to represent a value of type `T` that can be computed lazily. It has two possible states: either the computation has yet to be performed, or the value has already been computed. In the former case, it stores the function that performs the computation. In the latter case, it stores the computed value:
    
    
    1
    2
    3
    4
    
    
    private enum LazyValue<T> {
        case NotYetComputed(() -> T)
        case Computed(T)
    }
    

Now we wrap this enum in a class, called `LazyBox`, so that we can mutate it independently of its container. The owner of the `LazyBox` instance can remain immutable. The implementation could look like this:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    
    
    final class LazyBox<T> {
        init(computation: () -> T) {
            _value = .NotYetComputed(computation)
        }
    
        private var _value: LazyValue<T>
    
        var value: T {
            switch self._value {
            case .NotYetComputed(let computation):
                let result = computation()
                self._value = .Computed(result)
                return result
            case .Computed(let result):
                return result
            }
        }
    }
    

The class is initialized with the function it should use to compute the value. We store this function in a private `LazyValue` property until we need it. The public interface of the class is the read-only `value` property. In the getter we check if we have already computed the value, and return it if we have. If not, we evaluate the computation function and cache the value for subsequent reads.

We can use `LazyBox` like this, and verify that the computation function is indeed only evaluated once:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    
    
    var counter = 0
    let box = LazyBox<Int> {
        counter += 1;
        return counter * 10
    }
    assert(box.value == 10)
    assert(box.value == 10)
    assert(counter == 1)
    

And it has the benefit that it can be used with constant structs. In other aspects it's a little less convenient to use than a plain `lazy` variable would be because clients have to use the `value` property to access the value. If that's not good enough, we could hide the implementation by exposing another computed property that returns `LazyBox.value` and making the `LazyBox` property private.
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    
    
    struct Image {
        // Lazy storage
        private let _metadata = LazyBox<[String:AnyObject]> {
            // Load image file and parse metadata, expensive
            // ...
            return ...
        }
    
        var metadata: [String:AnyObject] {
            return _metadata.value
        }
    }
    
    let image = Image()
    print(image.metadata) // no error
    

And the containing struct retains its value semantics. It's a common pattern to use reference types internally inside a value type and implement it in a way that guarantees value semantics. The standard library uses it for many of the collection types.

# Concurrency

There's one final potential issue with this implementation, and that is concurrency. If `LazyBox.value` is accessed simultaneously from multiple threads before it has computed the value, it could evaluate the computation function multiple times. This is something you may want to avoid if the computation function has side effects or is expensive.

We can guarantee that the function is only evaluated once by routing all reads and writes of the internal `_value` property through a private serial queue. Here is the new implementation:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    21
    22
    23
    24
    25
    26
    27
    
    
    final class LazyBox<T> {
        init(computation: () -> T) {
            _value = .NotYetComputed(computation)
        }
    
        private var _value: LazyValue<T>
    
        /// All reads and writes of `_value` must happen on this queue.
        private let queue = dispatch_queue_create(
            "LazyBox._value", DISPATCH_QUEUE_SERIAL)
    
        var value: T {
            var returnValue: T? = nil
            dispatch_sync(queue) {
                switch self._value {
                case .NotYetComputed(let computation):
                    let result = computation()
                    self._value = .Computed(result)
                    returnValue = result
                case .Computed(let result):
                    returnValue = result
                }
            }
            assert(returnValue != nil)
            return returnValue!
        }
    }
    

The downside is a small performance hit on every access of `value`, and possible contention if many threads read the value simultaneously because they all have to go through the same serial queue. Given that very little work is performed on the queue after the cached value has been computed once, this latter aspect should be negligible in the vast majority of cases.

It's worth noting that Swift doesn't make this guarantee for the `lazy` keyword. [Apple says this in the Swift book](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Properties.html#//apple_ref/doc/uid/TP40014097-CH14-ID257):

> Note: If a property marked with the `lazy` modifier is accessed by multiple threads simultaneously and the property has not yet been initialized, there is no guarantee that the property will be initialized only once.
