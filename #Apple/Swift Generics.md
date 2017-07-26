# Generics

_Captured: 2015-10-30 at 10:52 from [swift.ayaka.me](http://swift.ayaka.me/posts/2015/10/21/generics)_

Generics are one of my favorite features of Swift. Like [Optional](http://swift.ayaka.me/posts/2015/10/5/optional), it makes your code safer to work with, makes your app have fewer crashes and unexpected bahaviors, and at the end of the day, it makes your users happier. It's one of the core features of Swift that make it great language to work with, and I think you'll love it as well. Without further ado, let's get started!

Let's say you want to define a struct that lets you have pairs of things. Maybe we can call it `Pair`. (I recommend downloading the [example Playground](http://swift.ayaka.me/s/genericsplayground.zip) or cloning [the repo](https://github.com/ayanonagon/learn-swift) and following along. This one has multiple modules so make sure Xcode's Project Navigator is visible by pressing `⇧⌘J`.)
    
    
    struct Pair {
        let first: String
        let second: String
    }
    
    
    let things = Pair(first: "Thing 1", second: "Thing 2")

This is pretty useful! It'd be nice to be able make pairs of other things too, like the result of two dice rolls like below. 🎲🎲
    
    
    let snakeEyes = Pair(first: 1, second: 1)

But we get an error `Cannot convert value of type 'Int' to expected argument type 'String'.`

![](http://static1.squarespace.com/static/56129a82e4b0147725b391f5/t/562a4cb2e4b0b1b4cb87981c/1445612723219/?format=1000w)

That's kind of a bummer. What if we really do want to use this in other places? What if we wanted to make it a little more… _generic_? That's where the aptly named generics come in handy! 😏

We can redefine `Pair` as below. Note the addition of `<T>` and `T` for both of the types.
    
    
    struct Pair<T> {
        let first: T
        let second: T
    }

If you're trying to figure out how to read this out loud, I'd probably say something like "`Pair` is a `struct` that is generic on type `T` and has two properties: `first` of type `T` and `second` of type `T`."

Now we can do all things.
    
    
    let things = Pair(first: "Thing 1", second: "Thing 2")
    
    
    let snakeEyes = Pair(first: 1, second: 1)

You can even make a `Pair` of `Pair`s if you wanted to!
    
    
    let pairOfPairs = Pair(first: Pair(first: "First First", second: "First Second"),
        second: Pair(first: "Second First", second: "Second Second"))

Magical, eh? And who said pairs of things have to be of the same type? What if `"Thing 1"` wanted to hang out with `1` for a change? Let's try it.
    
    
    let ones = Pair(first: "Thing 1", second: 1)

![](http://static1.squarespace.com/static/56129a82e4b0147725b391f5/t/5628fc42e4b0ace1ab7562b2/1445526595179/?format=1000w)

🚨 `Cannot invoke initializer for type 'Pair<T>' with an argument list of type '(first: String, second: Int)'` 🚨

The error is saying that we can't create a `Pair` that has different types for `first` and `second` because we said they are both type `T`. How do we fix this? We add a another generic to `Pair`!
    
    
    struct Pair<T, U> {
        let first: T
        let second: U
    }

`Pair` now is generic on `T` and `U`, where `first` is of type `T` and `second` is of type `U`. If we try to initialize `ones` again, it now works.
    
    
    let ones = Pair(first: "Thing 1", second: 1)

It's old convention to use `T` (for "Type"), `U`, `V`, etc. to signify the generic type, but you can really name it anything. [@UINT_MIN](https://twitter.com/UINT_MIN/status/657581908381990913) pointed out that Swift is moving toward more descriptive naming, like `Optional.Wrapped` and `Array.Element`. I also learned today that you can even use emoji 😻 (with a [few caveats](https://twitter.com/jckarter/status/657584862572974080) so see the [full list of allowed emoji](https://gist.github.com/natecook1000/c5fb2b8cd0967f53770e)). Thanks [@jckarter](https://twitter.com/jckarter/status/657582575095930880) and [@nnnnnnnn](https://twitter.com/nnnnnnnn/status/657585773114433536)!

Even if you don't find yourself defining your own classes and structs that are generic immediately, I bet you've used them before whether you knew it or not.

As programmers, we very often work with arrays. On any given day, you might declare an array of `monkeys`. Sometimes, we get sleepy, doze off a bit, and accidentally try to insert a number into our array of monkey emoji. 😪 But Swift being Swift, the compiler has our back and says: `Cannot convert type 'Int' to expected argument type 'String'`.

![](http://static1.squarespace.com/static/56129a82e4b0147725b391f5/t/5629027be4b0cf893b98982b/1445528188422/?format=1000w)

How did Swift know that we can't do that? Because Swift is good at figuring out what type something is, when we write `var monkeys = ["🙈", "🙉", "🙊"]` it infers to the type of `var monkeys` as below:
    
    
    var monkeys: [String] = ["🙈", "🙉", "🙊"]
    
    
    var monkeys: Array<String> = ["🙈", "🙉", "🙊"]

Look! Those angle brackets. They look familiar. They are our good friend generics. `var monkeys` is of type `Array<String>`. If you look at [Apple's documentation on Array](https://developer.apple.com/library/ios/documentation/Swift/Reference/Swift_Array_Structure/index.html), you'll see that `Array` is defined as `struct Array<Element>`. ("`Array` is a `struct` that is generic on type `Element`.")

![](http://static1.squarespace.com/static/56129a82e4b0147725b391f5/t/562907a2e4b07d02a8b90333/1445529507219/?format=1000w)

If you scroll down a little further, you'll find the documentation for the `append` function.

![](http://static1.squarespace.com/static/56129a82e4b0147725b391f5/t/5629084ae4b030ca91e67db2/1445529675345/?format=1000w)

Aha! `append` takes type `Element` as a parameter, `Element` as in the type that `Array` is generic on. So if we initialize `var monkeys` with type `Array<String>` we have to call `append` with a `String` and `Int` won't work. And now you know.

Generics are everywhere in the [Swift Standard Library](https://developer.apple.com/library/prerelease/ios/documentation/General/Reference/SwiftStandardLibraryReference/index.html) and you'll definitely be using them all the time. If you're curious, I recommend perusing through the library and see where you see classes and structs that are generic on some type. (Just look for those angle brackets!)

That's it for now. If you have any questions, feel free to leave them in the comments below, or tweet at me [@ayanonagon](https://twitter.com/ayanonagon). The biggest reason I'm writing these posts is to get better at explaining concepts and how amazing they are, so any feedback about what was clear vs. not would be much appreciated as well. Also let me know what other topics you want to hear about. Hope you had fun learning, and thanks for reading!

### Recommended Reading
