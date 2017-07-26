# Re...throws?

_Captured: 2015-07-02 at 23:47 from [robnapier.net](http://robnapier.net/re-throws)_

[Last time](http://robnapier.net/throw-what-dont-throw) we talked about how a function that can throw errors is a different type in Swift than a function that cannot throw errors. And then I briefly mentioned this other thing, "rethrows." Let's talk about that, and along the way explore closure types a little more and their weird and woolly ways.

Like last time, we start with `map` (`mymap` so there's no confusion with the built-in).

    extension Array {
        func mymap<T>(@noescape transform: (Generator.Element) -> T) -> [T] {
            var ts: [T] = []
            for x in self {
                ts.append(transform(x))
            }
            return ts
        }
    }

So that's the simple `map`. As we discussed previously, we can't pass a throwing closure to it because it would be the wrong type. Let's rewrite `mymap` so it can throw:

    extension Array {
        func mymapThrows<T>(@noescape transform: (Generator.Element) throws -> T) throws -> [T] {
            var ts: [T] = []
            for x in self {
                ts.append(try transform(x))
            }
            return ts
        }
    }

Now `transforms` can throw, and so it needs `try` when we call it. And since we don't handle the error ourselves, the whole method has to be marked `throws`.

Let's create a couple of functions to check this out:

    func double(x: Int) -> Int { return x*2 }
    extension NSCalculationError: ErrorType {}
    func reciprocal(x: Int) throws -> Double {
        guard x != 0 else { throw NSCalculationError.DivideByZero }
        return 1.0 / Double(x)
    }

The first function, `double`, always succeeds. The second function, `reciprocal`, may throw.

    let xs = [1,2,3]
    let ds = xs.mymap(double) // No problem
    let rs = try xs.mymapThrows(reciprocal) // No problem

And if we pass them to the other methods?

    let ds = try xs.mymapThrows(double) // No problem
    let rs = xs.mymap(reciprocal) 
    // Invalid conversion from throwing function of type '(Int) throws -> Double' to non-throwing function type '@noescape Int -> `T'

So we can pass a non-throwing closure to the throwing `map`, but not vice versa. Why? Let's take a step back and talk about subtypes.

A good way to think about types is as a set of promises. In the OOP world, we create types like this:

    class Animal {
      func eat() {...}
    }
    class Cat : Animal {
      func purr() {...}
    }

Every Animal promises it can eat. Every Cat promises it can purr. Since a Cat is an Animal, it also promises it can eat. But not every Animal promises to purr (other Animals _may_ be able to purr, it's just not promised). You're used to calling Cat a subclass of Animal, and that's true. But it's more generally a _subtype_. This idea isn't restricted to classes. After all, the same thing is true of protocols:

    protocol Animal {
      func eat()
    }
    protocol Cat : Animal {
      func purr()
    }

No classes required. The important thing about the type/subtype relationship is that a subtype can only _add_ promises. It can never remove promises. Understanding what promises are being made is very important to understanding your types.

`NSArray` doesn't promise to be immutable. That may surprise you, but you know it's true because you copy them when they're passed as parameters. If `NSArray` promised to be immutable (like `NSDate` does), you'd never do that. If `NSArray` promised to be immutable, then `NSMutableArray` couldn't be its subclass, because it breaks that promise.

`NSArray` only promises to be _readable_. That's a completely different thing. `NSMutableArray` _also_ promises to be readable. It keeps the promise `NSArray` made. `NSMutableArray` also promises to be writable, and any subclass of `NSMutableArray` would also have to keep that promise.

> A subtype can only add promises. It can never remove them.

So, what promises does `(T) throws -> U` make? It promises to accept a `T`. And it promises that it will either return a `U` or it will throw an error.

What promises does `(T) -> U` make? It promises to accept a `T`. And it promises that it will return a `U`.

How are these types related? Which one makes the stronger promise? A good way to figure this out is to think through some cases.

  * Function returns `U`. Keeps both promises.
  * Function throws an error. Keeps one promise, breaks the other.

The stronger promise is the one that we broke. It's the non-throwing function that added a new, stricter promise. "I will do X or Y, and furthermore I will only do X." Doing X keeps that promise. Doing Y breaks it.

So that tells us that a non-throwing closure can be used anywhere a throwing closure is requested, just like a Cat can be used anywhere an Animal is requested. No conversions necessary. It's just types.

So great, we have `mymapThrows`, and it takes either kind, so we're done, right? Well, we could be, but it'd be really annoying. Consider if `map` were marked `throws`. That would mean that _every_ `map` would have to include a `try`, and somewhere you'd have to catch the error.

    let ds: [Int]
    do {
        ds = try xs.map { $0 * 2 }
    } catch {
        // Really, Swift? Really? Every time? Even when it can't possibly throw?
        // No, not really. Swift is smarter than that.
    }

There are two ways out of this annoyance. The obvious way is overloading. We can just have two methods with the same name but different types:

    map<T>(@noescape transform: (Generator.Element) throws -> T) throws -> [T]
    map<T>(@noescape transform: (Generator.Element) -> T) -> [T]

Since overloading picks the most specific subtype available, this works fine for the caller. But it's a serious pain for the dev who has to write `map`. There's the obvious annoyance of needing two methods to do the job of one, but it gets worse if you try to share code between the implementations. You'd think you could just call the throwing version from the non-throwing version like:

    func map<T>(@noescape transform: (Generator.Element) -> T) -> [T] {
        return try! self.map(transform as (Generator.Element) throws -> T))
    }

But that runs afoul of `@noescape`, which doesn't allow the conversion. And even if that worked (might be a Swift bug), having to use `try!` all over the place is crazy, on top of the madness of having two (or three) methods for everything. My overload implementation looks like this:

    extension Array {
        func mymap<T>(@noescape transform: (Generator.Element) throws -> T) throws -> [T] {
            return try self._mymap(transform)
        }
        func mymap<T>(@noescape transform: (Generator.Element) -> T) -> [T] {
            return try! self._mymap(transform)
        }
        func _mymap<T>(@noescape transform: (Generator.Element) throws -> T) throws -> [T] {
            var ts: [T] = []
            for x in self {
                ts.append(try transform(x))
            }
            return ts
        }
    }

If Swift had shipped this way, I suspect the stdlib folks would be having words with the compiler folks by now. "Please come over to my desk. I'd like to introduce you to another kind of throws."

Luckily, Swift is much smarter than that. It's nice that you can overload based on throwing, but in many cases we have a better tool. We can mark the method `rethrows` rather than `throws`.

    func map<T>(@noescape transform: (Generator.Element) throws -> T) rethrows -> [T]

So what promise does `rethrows` make? It promises that the only way it will throw is if a closure it is passed throws. So if it's passed a closure that can't throw, the compiler knows that the function can't throw either.

(Why isn't stdlib's `map` marked `rethrows` today? Because it's beta 1, and the Swift team hasn't updated all of stdlib yet. They've indicated that a lot of stdlib will be fixed in future betas. Have patience.)

It's natural to think of `rethrows` as a subtype of `throws`, and non-throwing closures as a subtype of `rethrows`, but that doesn't quite seem to be true. Swift doesn't treat `rethrows` as a full type. For example, you can't write overloads with both `throws` and `rethrows`, and closures can't include `rethrows` in their type. Instead, `rethrows` acts more like a function attribute (like `@noreturn`). It just modifies the rules around what contexts can call the function. The real types are throwing and non-throwing, and "rethrowing" can just morph between the two based on context.

A function that accepts a closure has three throwing options:

  * It can throw. That means that the function may throw errors whether or not the closure throws errors.

  * It can rethrow, like `map`. This means that the function cannot create any errors of its own, but may propagate errors from the closure it was passed.

  * It can not throw. That means that it either handles the errors thrown by the closure, or it does not evaluate the closure. For example, a setter on a closure property doesn't throw just because the closure might throw. It just sets the property and returns.

Which one you use is completely dependent on your situation. There's no "best" answer, though you should generally choose the most restrictive one you can. You shouldn't just make all your functions `throws` for the same reasons you shouldn't make all your variables `Any`. It's all about choosing the right type.

So when you use the new Swift error handling system, don't think "exceptions." Think types. Your function returns "either X or an error." And sometimes, you can promise it'll only return X.

Throw in peace.
