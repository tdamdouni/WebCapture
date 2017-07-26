# What The Heck Is A Monad

_Captured: 2015-12-12 at 18:28 from [khanlou.com](http://khanlou.com/2015/09/what-the-heck-is-a-monad/)_

There's an [everpresent hilarious thread](https://byorgey.wordpress.com/2009/01/12/abstraction-intuition-and-the-monad-tutorial-fallacy/) in programming blogs where an author tries to explain what a monad is, starts strong, and then ends up losing everyone with some nonsense about an endofunctor.

I'm going to take a crack at it. I'm probably going to fail, and I'm going to prove Soroush's Burrito Law in the process: anyone trying to explain monads is going to fail, even if they account for how hard explaining monads is.

A monad is a wrapper for a thing. ([It honestly is like a burrito.](http://blog.plover.com/prog/burritos.html))

### The Maybe Type

So. Let's talk Swift. Let's say you have a function that reads something from disk. It can either return the thing, or it can return nothing. Swift calls this type `Optional`, but let's recreate it and call it `Maybe`.
    
    
    enum Maybe<WrappedType> {
        case Something(WrappedType)
        case Nothing
    }
    

Angle-bracket blindness is real. `WrappedType` here just means that our `Maybe` can have anything inside of it, and we can refer to whatever type that thing is with `WrappedType`. This lets the compiler know the type of what's coming out is the same as the type of what's put in. Let's continue. Imagine a function called `readString()` reads a string from the disk, where its provenance is doubtful. It "maybe" doesn't exist.
    
    
    func readString() -> Maybe<String> {
        return .Something("someString");
    }
    
    let maybeString = readString()
    

This is the first important part of a monad. You have to have a way to create one. In this case, the constructor, `Maybe.Something`, fills that role. In other languages, this is known as `unit` or the inconveniently-named function `return`. It's a function that takes one parameter, and returns a monad that wraps that parameter.

If this is all we have, it's kind of frustrating to use. To get access to the information inside that `Maybe`, you have to explicitly unwrap it. The structure of the type forces you to check it, every time.
    
    
    switch (maybeString) {
        case let .Something(definitelyString):
            print(definitelyString)
        case .Nothing:
            print("Nothing!")
    }
    

After we use `Maybe` with a case statement like this for a while, we notice that we're writing this `switch` statement over and over. It's a lot of boilerplate just so we can access the `Something`.

Maybe we can wrap up the `switch` into a function, and pass that function a block that will be executed if the Maybe is a `Something` and not a `Nothing`.
    
    
    extension Maybe {
        func ifSomething<NewWrappedType>(block: (WrappedType) -> Maybe<NewWrappedType>) -> Maybe<NewWrappedType> {
            switch self {
            case let .Something(wrapped):
                return block(wrapped)
            case .Nothing:
                return .Nothing
            }
        }
    }
    

I would love to remove the types in the function declaration to make it shorter and clearer, but they actually confer a very important piece of information: The `block` that we're accepting takes a `WrappedType` (a string, in the example above), and returns a new type _wrapped in a monad_.

This is very important. `ifSomething` doesn't just give us access to the `Something`, it also lets us transform it, but _requires_ that it be wrapped in the Monad type again. (Sometimes we want to transform but not wrap it, and I'll address that in a moment.)

It's important that the block returns an already-wrapped monad, so that we can chain these calls. This is a big part of why monads are useful.

Now that we have this power of transforming the wrapped thing, we can do something very cool. Imagine we had a function that converts strings to JSON objects. It returns a `Maybe`, since deserializing JSON can fail.
    
    
    readDataFromDisk().ifSomething({ string in
        return convertToJSON(string)
    })
    

or, more succinctly:
    
    
    readDataFromDisk().ifSomething(convertToJSON);
    

At the end of `.ifSomething(convertToJSON)`, we just get back a new `Maybe` monad, on which we can again call `ifSomething`. This is how monads let us chain stuff. Imagine another function called `getProperty`, which also returns a `Maybe`.
    
    
    readDataFromDisk().ifSomething({ string in
        return convertToJSON(string)
    }).ifSomething({ JSON in
        return getProperty(JSON, "username")
    })
    

Et cetera. We can keep chaining like this, as long as we need to. Notice how this is flat, instead of nested. We've totally skipped the part where you have to unwrap an `Optional` with an `if let`, then unwrap another one, then another one, and you end up with something 5 levels deep.

If we didn't have `ifSomething`, our code would look like this:
    
    
    var maybeData = readDataFromDisk()
    if let data = maybeData {
        let maybeJSON = convertToJSON(string)
        if let JSON = maybeJSON {
            let maybeUsername = getProperty(JSON, "username")
            if let username = maybeUsername {
                //we can finally use the username
            }
        }
    }
    

While indented code like this might work in early stages, the fact that it continues to indent inwards means that it's not scalable. With monads, we can remove the nesting and organize our code much better.

Functional programmers took a great name like `ifSomething` and made it totally inscrutable by calling it `flatMap`. (In some of the literature, it's also known as `bind`. In Haskell, aka peak inscrutability, it's invoked with the operator `>>=`.)

`bind` (or `flatMap`) and `unit` (the constructor) are all it takes to be considered a monad. From those two, we can also build `map`. `map` lets us transform the wrapped object without having to rewrap it ourselves at the end of the function. This is particularly useful for arrays and other collection types.

To build `map`, we wrap the result of the `map` block with the constructor and send that to `flatMap`:
    
    
    extension Maybe {
        func map<NewWrappedType>(block: (WrappedType) -> NewWrappedType) -> Maybe<NewWrappedType> {
            return flatMap({ wrapped in
                return .Something(block(wrapped));
            });
        }
    }
    

In this way, map can be written in terms of `bind` and `unit`.

### The Monadic Laws

For something to be monad, in addition to implementing `bind` and `unit`, it has to follow some special rules.

First, left identity.
    
    
    unit(a).flatMap(f) == f(a)
    

Wrapping `a` in the monad, then calling `flatMap` with any function `f` will have same result as just calling `f` with `a`, since `f` returns a new monad.

Second, right identity.
    
    
    m.flatMap(unit) == m
    

Since the `unit` function doesn't do anything but take the unwrapped value and wrap it, calling `flatMap` on an existing monad `m` with `unit` will have no effect.

The first two monadic laws exist to assert that `unit`, the constructor, doesn't do anything other than wrap `a`.

Lastly, associativity.
    
    
    m.flatMap(f).flatMap(g) == m.flatMap({ a in
        return f(a).flatMap(g)
    })
    

This says that we can combine two functions `f` and `g` into a new function, and calling `flatMap` with the new function is the same as calling `flatMap` with each of the functions separately.

### In Swift

You don't need to write your own `Maybe` type to start using this in Swift today. Swift's `Optional` type supports `flatMap`.
    
    
    let optionalString = Optional.Some("123");
    let optionalInt = optionalString.flatMap { string in
        return Int(string)
    }
    

Because all versions of `flatMap` behave the same, you can use this just like the `flatMap` we wrote above, chaining it over and over.

### In A Nutshell

That's monads in a nutshell. Well, they are the nutshell. They wrap a value, like a shell.

Other monads you might have seen include:

  * `Result`, which wraps a "Something" with an optional "Error".
  * `Eventually`/`Promise`/`Deferred`, which wraps a value that doesn't exist yet.
  * `Array`, which wraps many values.

With `Result` in particular, it's easy to see how you might have a series of functions where each is dependent on the previous one, and where each can fail and generate an error. You would have a pyramid of doom without being able to `flatMap` them repeatedly.

I've used the `Promise` monad a lot in Javascript, and it organizes code greatly:
    
    
    User.signup = function(user) {
        return new Promise(function(resolve, reject) {
            User.validate(user).then(function() {
                return Bcrypt.genSalt(10);
            }).then(function(salt) {
                return Bcrypt.hash(user.password, salt, null);
            }).then(function(saltedHashedPassword) {
                return User.insertIntoDatabase(user, saltedHashedPassword);
            }).then(function(userRecord) {
                resolve(userRecord);
            }).catch(function(error) {
                reject(error);
            });
        });
    };
    

The chaining that the promise monad affords us is crucial when all of your operations are asynchronous and can fail. We return a new Promise in each `then` block, and the chain continues. In this way, we've described an inherently complex, asynchronous task in a serial list of steps.

Monads are weird thing. The idea lets us treat all these different wrappers, which all serve different functions, similarly. When we know that something is a monad, we gain a ton of knowledge about how we can use it and what it can do.

After all, they're just monoids in the category of endofunctors.

* I am Soroush Khanlou, and this is my blog. I write about programming, primarily Objective-C and learning what I can from other languages, like Ruby and Haskell. You can catch me talking about photography, politics, eating, and fonts.

* (C) Soroush Khanlou 
