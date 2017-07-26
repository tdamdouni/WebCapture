# Swift Optionals, Functional Programming, and You

_Captured: 2015-09-22 at 16:52 from [www.mokacoding.com](http://www.mokacoding.com/blog/demistifying-swift-functor/)_

This post is the result of a talk I have given in various forms in the past months, in particular at [/dev/world](http://2015.devworld.com.au/) and [YOW! Connected](http://connected.yowconference.com.au/).

The goal is to demystify scary terms associated with functional programming, and show a practical application of the underlying concepts when used with array and optionals.

You can follow along on the [Playground](https://github.com/mokagio/yow-connected-2015) I used for the YOW! talk.

_Note:_ All the code above is written for Swift 2 and Xcode 7.

## Nasty if let

Probably one of the most disruptive features of Swift compared to Objective-C is the presence of optionals. Having a type _wrapped_ in an optional adds an extra layer of context. A constant or variable of type `Something?` could be nil, and consumers have to account for that.

The most common way to deal with optionals is by using an `if let`:
    
    
    var input: String? = "foo bar"
    var output: String
    
    if let someInput = input {
        output = "🐷 " + someInput
    } else {
        output = "😔"
    }
    

This construct can lead to a nasty nested indentation spiral of doom:
    
    
    func fancifiedEmojiForCurrentUser() -> String? {
    
        // currentUser: -> User?
        if let actuallyAUser = currentUser() {
            // joinedNameForUser: User -> String
            let joinedUserName = joinedNameForUser(actuallyAUser)
    
            // emojiFromString: String -> Emoji?
            if let emojiForUser = emojiFromString(joinedUserName) {
                // fancifyEmoji: Emoji -> Emoji
                return fancifyEmoji(emojiForUser)
            }
        }
    
        return .None
    }
    

In my opinion the code above, while being simple, is not easy to digest.

Swift 2 added the `guard` statement, which allows us to rewrite our example like this:
    
    
    func fancifiedEmojiForCurrentUser() -> String? {
    
        // currentUser: -> User?
        guard let actuallyAUser = currentUser() else {
          return .None
        }
    
        // joinedNameForUser: User -> String
        let joinedUserName = joinedNameForUser(actuallyAUser)
    
        // emojiFromString: String -> Emoji?
        guard let emojiForUser = emojiFromString(joinedUserName) {
          return .None
        }
    
        // fancifyEmoji: Emoji -> Emoji
        return fancifyEmoji(emojiForUser)
    }
    

This version is a bit nicer, and does good use of the early return pattern, but I still find it hard to grasp at first sight.

Let's see how we can pick some pages from the functional programming book and make that code leaner.

## What Functional Programming Is All About

When I used to think about functional programming is used to associate it to the academia world, and to programs that needed to crunch big amounts of data, or to work reliably on parallel architectures.

Then cryptic words like functors and monads started to appear in my Twitter feed, and the cool kids started making jokes I couldn't understand.

Good news everybody, functional programming is not about academia, abstract programs, or monadic laws. It is all about **functions**. For a programming language to be functional, or at least functional friendly, it simply needs to treat functions as first class citizens.

In Swift we can define a function like this:
    
    
    func plusOne(addend: Int) -> Int {
      return addend + 1
    }
    

The first class citizen requirements mean that we can treat functions the same way we'd do for any other value. For example we can assign a function to a constant:
    
    
    let plusTwo: Int -> Int = { $0 + 2 }
    
    let four = plusTwo(2) // => 4
    

The code above defines a variable of type `Int -> Int`, or `(Int) -> Int` if you prefer, and assigns it a closure.

## Functions as input

The ability of assigning functions to variables and constants means that we can also pass them as arguments to other functions. For example:
    
    
    func sumTwice(addend: Int, f: Int -> Int) -> Int {
      return f(addend) + f(addend)
    }
    
    let x = sumTwice(addend: 1, f: { $0 + 1 })
    // => (1 + 1) + (1 + 1)
    // => 4
    

## Functions as output

The same holds true for functions that return other functions:
    
    
    func multiplier(base: Int) -> (Int -> Int) {
      return { x in
        return base * x
      }
    }
    
    let timesThree = multiplier(3)
    

`timesThree` is now a function that multiplies the given parameter by three.
    
    
    let x = timesThree(2) // => 6
    

## Higher Order Functions

Here's the first demystification of a functional programming term. What we have seen above are example of "Higher Order Functions".

The working definition for the everyday Swift development of Higher Order Functions is simply: functions take other functions as input and/or output.

But what does this have to do with optionals? Let me introduce you to a very famous higher order function: `map`.

## map

Let's say you have an array of, for example, `Int`, and a certain transformation function that takes `Int` as input and return any other type, for example `String`. And let's say that you need to apply the given transformation function to each element of the array, and collect the result into another array. One option you have is to use an ugly for each loop, a more concise option is to use map.
    
    
    let numbers = [1, 2, 3]
    let toString: Int -> String = { "\$0" }
    
    let strings = numbers.map(toString) // => ["1", "2", "3"]
    

Or for the one liner fans:
    
    
    let strings = numbers.map { "\$0" }
    

`map` is pretty cool, but also a bit picky. The example below won't compile, can you guess why?
    
    
    let getLength: String -> Int = { $0.characters.count }
    
    let lenghts = numbers.map(getLength) // [!] won't compile
    

We will come back to this in a moment.

## The Array type

Something that we might forget due to the `[]` convenience is that an array constant or variable actually has type `Array<T>`, where the generic `T` is the type of the elements the array is allowed to contain.

We could rewrite the definition of `numbers` from the example above as:
    
    
    let numbers: Array<Int> = [1, 2, 3]
    

Looking at arrays through their type definition makes it clearer to understand why `numbers.map(getLenght)` doesn't compile.

Given an array `Array<T>` map expects a function `T -> U`.

In the example numbers is has type `Array<Int>`, and `toString` is `Int -> String` which matches the expected type signature for `map`. On the other hand `getLenght` is a `String -> Int` which is not compatible with `map` on an array of `Int`.

Sweet! But we haven't talked about optionals yet.

## The Optional type

Like for `Array` it might be easy to overlook the fact that optionals variable and constants actually have type `Optional<T>`, where `T` is the type of the value _wrapped_ by the optional.

These definitions are equivalent:
    
    
    let x: String? = "an optional string"
    
    let y: Optional<String> = "another optional string"
    
    let z = Opional.Some("yet another optional string")
    

As you might have notice the definition of optional and array variables are quite similar.
    
    
    let a: Array<Int> = [1, 2, 3]
    let b: Optional<Int> = Optional.Some(42)
    

`Optional` is similar to `Array`. `Array` has map. Can you guess what comes next?

## Optional map

Yes, you guessed right! The `Optional` type implements `map` as well.
    
    
    Optional.Some(42).map { $0 / 2 } // => Optional.Some(24)
    
    Optional.None.map { $0 / 2 } // => Optional.None
    

In the case of optionals, if there is a wrapped value `map` applies the function to the value, and returns the result wrapped in a new optional, otherwise simply returns `.None`.

The considerations regarding the type signatures made for `Array map` are valid for `Optional` too.
    
    
    let x: Optional<Int> = 42
    let f: Int -> Int = { $0 * 2 }
    let q: String -> Int = { $0.characters.count  }
    
    x.map(f) // compiles
    x.map(q) // [!] does not compile
    

`q` has type `String -> Int`, but `x` is `Optional<Int>`. Their types don't match for `map`.

## Functor

The definition of **functor** for the everyday Swift developer is a type that implements `map`.

There is more to the functors than just map, so if you want to create your own functor type be sure to learn about the [functor laws from the category theory definition](https://en.wikipedia.org/wiki/Functor) or functor.

Like for higher order functions, once you look into it there is nothing daunting about functor at all. It is just the name for a type that respect certain laws, with the practical result of exposing `map`.

## Better if let

Let's look back at `fancifiedEmojiForCurrentUser`.
    
    
    func fancifiedEmojiForCurrentUser() -> String? {
    
      // currentUser: -> User?
      if let actuallyAUser = currentUser() {
        // joinedNameForUser: User -> String
        let joinedUserName = joinedNameForUser(actuallyAUser)
    
        // emojiFromString: String -> Emoji?
        if let emojiForUser = emojiFromString(joinedUserName) {
          // fancifyEmoji: Emoji -> Emoji
          return fancifyEmoji(emojiForUser)
        }
      }
    
      return .None
    }
    

The `currentUser` function returns a `User?`, _as there migth not be a logged user_, and `joinedNameForUser` gets a `User` as input, and returns a `String`. We can use `map` there.

`emojyFromString` as type signature `String -> Emoji?`, _apparently not all the strings can be converted into emojis_, and `fancifyEmoji` expects an input of type `Emoji`. We can use `map` on them too.
    
    
    func fancifiedEmojiForCurrentUser() -> String? {
    
      if let joinedUserName = currentUser.map(joinedNameForUser) {
        return emojiFromString(joinedUserName).map(fancifyEmoji)
      }
    
      return .None
    }
    

Now, wouldn't it be nice to chain everything together using `map`?

Unfortunately this is not possible. Why? Let's follow the types.

`currentUser.map(joinedNameForUser)` is a `map` on a `User?` of a `User -> String` function, which from what we saw above returns a `String?`.

`emojiFromString` has type signature `String -> Emoji`. `String?`, `String -> Emoji?`, `map`... The result is `Emoji??`, or `Optional<Optional<Emoji>`.

`fancifyEmoji` is expecting an `Emoji` input parameter, and it is not compatible to be mapped on an `Emoji??`.

And by the way, what the heck is an `Optional<Optional<T>>`? A nested optional like that is not very useful.

To solve this mystery let's go back to `Array`.

## Nested arrays

What would happen if we mapped a function `Int -> [Int]` on an array of `Int`?
    
    
    [1, 2, 3].map { [ $0, $0 ] } // => [ [1, 1], [2, 2], [3, 3] ]
    

What we get is an array of arrays, or nested array.

Sometimes nested arrays are the data structure we need in our code, other times they are not an what we need is a linear array. The operation of converting a nested array into a linear one is called _flattening_.
    
    
    func flat<T>(array nestedArray: [ [T] ]) -> [T] {
      var linearArray: [T] = []
      for array in nestedArray {
        for element in array {
          linearArray.append(element)
        }
      }
    }
    

In the example above we can use `flat` to get a linear array:
    
    
    flat([1, 2, 3].map { [ $0, $0 ] }) // => [ 1, 1, 2, 2, 3, 3 ]
    

`flat`, `map`... `Array` has a `flatMap` method that does exactly that.

## flatMap
    
    
    [1, 2, 3].flatMap { [ $0, $0 ] }) // => [ 1, 1, 2, 2, 3, 3 ]
    

`flatMap` on an `Array<T>` expects a function `T -> Array<U>` and returns `Array<U>`. It `map`s then `flat`s. _Note that in our examples `U` is equal to `T`._

Before we saw that `Array` is similar to `Optional`, and that in fact they are both functors and have `map`. It won't surprise you to know then that `Optional` has a `flatMap` implementation itself.

## flatMap on optionals

Given an `Optional<T>`, `flatMap` expects a `T -> Optional<U>` as input, and has output of type `Optional<U>`

For example, consider this function `half` that returns an `Int?` because it attempts to divide by to only if the `number` parameter is even:
    
    
    func half(number: Int) -> Int? {
      switch number % 2 {
      case 0: return number / 2
      default: return .None
      }
    }
    

We can do:
    
    
    Optional<Int>.Some(4).flatMap(half)   // => Optional.Some(2)
    Optional<Int>.Some(3).flatMap(half)   // => Optional.None
    Optional<Int>.None                    // => Optional.None
    

## Monad

Here is demystified our third and final functional programming term. A Monad is a type that allows `map` and `flatMap`.

Like for functors, there is actually a very solid mathematical definition behind monads, with a set of [monadic laws](https://en.wikipedia.org/wiki/Monad_%28functional_programming%29#Monad_laws) governing them. For the everyday Swift developer like you and me though, a monad is a type on which we can `map` and `flatMap`, like `Array` and `Optional`.

## Even better if let

We left our `fancifiedEmojiForCurrentUser` for current user in this state:
    
    
    func fancifiedEmojiForCurrentUser() -> String? {
    
      if let joinedUserName = currentUser.map(joinedNameForUser) {
        return emojiFromString(joinedUserName).map(fancifyEmoji)
      }
    
      return .None
    }
    

We tried to chain everything together with `map` but got stuck when we got a nested optional `Emoji`. Now that we know `flatMap` we can achieve that result, in fact `currentUser.map(joinedNameForUser)` returns `String?` and `emojiFromString` has type signature `String -> Emoji?`, this looks like a good use case for `flatMap`.
    
    
    func fancifiedEmojiForCurrentUser() -> String? {
    
      return currentUser
        .map(joinedNameForUser)
        .flatMap(emojiFromString)
        .map(fancifyEmoji)
    
    }
    

There you go. Isn't that code nice?

To a reader familiar with `map` and `flatMap` this final example appear very clear, and is arguably easier on the eye then the version using `if let` or `guard`.

## Wrapping Up

In this post we saw how higher order functions, functors, and monads, are actually simpler things that their name suggest, and found out that we had been using them everyday without knowing.

The power of functors and monads is not the fact that you can sound like a snob hipster when you mention them, but actually that you can use `map` and `flatMap`.

A good use case for `map` and `flatMap` in the context of `Optional` is to simplify code using `if let`s.

I am not advocating to start writing our iOS apps in [Haskell](https://www.haskell.org/), but I hope to have set some wheels in motion, and to have shown you that just because it might sound a bit daunting it doesn't mean that functional programming is out of your reach, and that it can actually be used together with object oriented code for the greater good ☺️

If you have any question, suggestion or fix please leave a comment below, or hit me up on Twitter [@mokagio](http://twitter.com/mokagio).

_Happy coding, and leave the codebase better than you found it._
