# Generic Protocols & Their Shortcomings

_Captured: 2015-12-11 at 01:36 from [krakendev.io](http://krakendev.io/blog/generic-protocols-and-their-shortcomings)_

For the past couple of weeks, [@micheletitolo](http://www.twitter.com/micheletitolo) and I have played with ways to re-architect an app. In particular, we settled on a blend of [VIPER](https://www.objc.io/issues/13-architecture/viper/) and [Protocol Oriented MVVM](http://natashatherobot.com/swift-2-0-protocol-oriented-mvvm/). Knowing that we had the opportunity to re-architect an app in Swift, we went crazy discussing ways to liberally apply generics, protocols, and value types throughout! Once we had our ingredients for a well-architected app, we proceeded to mix them together in code. However, much like oil and water, generics and protocols don't mix very well. But never fear! With added ingredients, we can totally work with these two and cook something beautiful together. 🐥🍰🎂

![giphy-1.gif](http://static1.squarespace.com/static/5592eb03e4b051859f0b377f/t/56622a23e4b0d6ae9d02cc7e/1449273892685/giphy-1.gif?format=300w)

# Making a Protocol Generic

There are two ways to create a generic protocol - either by defining an abstract typealias or the use of `Self` (with a capital S). Either of these types are what's known as an **_associated type_**. This is because they are only associated with the protocol they are defined in.

Here's how both of these look like:

## Self

The use of `Self` is actually pretty cool. When you use `Self` in a protocol declaration, not only do you make that protocol generic but you are also basically putting in a placeholder for your conforming type without having to know that type in advance. (Pay special attention to the return types of the `holdAMeetingWithTheClan` function)
    
    
    protocol MythicalType {
        func holdAMeetingWithTheClan(clan: [Self])
    }
    
    class Kraken: MythicalType {
        func holdAMeetingWithTheClan(clan: [Kraken]) {
              //Time to discuss whether or not it's time to release the kraken.
        }
    }
    
    class Elf: MythicalType {
        func holdAMeetingWithTheClan(clan: [Elf]) {
            //Elves are humanity's only hope against the Kraken.
        }
    }

In particular, they're **very** useful when using protocol extensions:
    
    
    extension MythicalType where Self: Kraken {
        func holdAMeetingWithTheClan(clan: [Kraken]) {
            //There's absolutely nothing to discuss. WREAK DESTRUCTION ON THE VILLAGE!!!
            releaseTheKrakens(clan)
        }
    }

This extension, as you can see, will only work if the object conforming to `MythicalType` is of type `Kraken`! As for our `Elf` type, the compiler will tell you that you still need to conform to it if you haven't already.

**_EXCEPTION_** \- If you happen to **only** use `Self` as the return type of the functions in your protocol declaration, then your protocol will **NOT** be generic. If you are only using `Self` and not a typealias, then only way to make your protocol generic is by using it in your protocol declaration after following any of these two rules:

  * As the parameter of a function
  * Or as the type of a get/set variable

## Typealias

As for using a typealias, there isn't anything too special about it. Using our `MythicalType` protocol, let's add to it using a typealias.
    
    
    protocol MythicalType {
        typealias FoodType
    
        func prepareFood() -> [FoodType]
        func devour(edible: FoodType)
    }
    
    class Kraken: MythicalType {
        func prepareFood() -> [Human] {
            //attack the village. Gather all the humans for DINNER TIME!
            return village.inhabitants
        }
    
        func devour(edible: Human) {
            //It's DINNER TIME YO. Nom nom nom.
        }
    }
    
    class Elf: MythicalType {
        func prepareFood() -> [Vegetable] {
            //Elves are vegetarian. Obvi.
            return gatherCrops(nearbyFarm)
        }
    
        func devour(edible: Vegetable) {
            //Yum. Greens. How tasty.
        }
    }

In this example, we create a generic protocol that can work for all `MythicalType`s that can eat a generic `FoodType`. All mythical creatures have to eat, right? Since our typealias `FoodType` is not a concrete type, any conformance to this protocol needs to be replaced with a real, concrete type at compile time. Our typealias here makes our `FoodType` _homogenous_; meaning that whenever we conform to this protocol, we can only replace `FoodType` with **_one_** type throughout the conforming class/struct/enum. This is demonstrated by replacing all instances of `FoodType` with `Human` in our `Kraken` class and `Vegetable` in our `Elf` class. The important thing to remember is that every type you replace `FoodType` with **_must match exactly_**.

# Why Generic Protocols Can Sometimes Suck

So far, Swift isn't quite ready in some aspects, and this couldn't be more true than with generics. According to the docs, protocols are fully-fledged types:

> "Because it is a type, you can use a protocol in many places where other types are allowed."

It goes on to list where they can be used:

  * As a parameter type or return type in a function, method, or initializer
  * As the type of a constant, variable, or property
  * As the type of items in an array, dictionary, or other container

However, this is not completely true. For _generic_ protocols, you can't use them in two of the above scenarios. Instead, they can only be used as generic constraints in a class or function declaration. This means they can only be used in the <> bracket syntax you see in generics like so:
    
    
    class Storybook<T: MythicalType> {}
    
    //Or in a function declaration
    func writeBookAbout<T: MythicalType>(myth: T) {}

Unfortunately, using generic protocols outside of generic constraints fail with this error:

![](http://static1.squarespace.com/static/5592eb03e4b051859f0b377f/t/5663d28de4b032b04c63e65c/1449382541947/?format=1000w)

But that begs the question; _Why can't we use generic protocols outside of generic constraints?_

The **_short_** answer is: Swift wants to be type-safe. Couple that with the fact that it's an [ahead-of-time](https://en.wikipedia.org/wiki/Ahead-of-time_compilation) compiled language, and you have a language **_that NEEDS to be able to infer a concrete type at anytime during compilation_**. I can't stress that enough. At compile time, every one of your types that aren't function/class constraints need to be concrete. Associated types within a protocol are abstract. Which means they aren't concrete. They're fake. And no one likes a fake.

"But Hector...I need **examples**."

Ok, fine! What follows are two clarifying examples where I use our generic `MythicalType` protocol like I would use a regular protocol and **_why_** they fail.

![](http://static1.squarespace.com/static/5592eb03e4b051859f0b377f/t/5663b8d0e4b078c56b4fd03a/1449375955737/?format=300w)

### Scenario #1 - As a property
    
    
    var myth: MythicalType = random() % 2 == 0 ? kraken : elf
    can't figure out what type this is...and rightfully so.
    let allTheFood = myth.prepareFood()

In our first scenario, we find ourselves with a `MythicalType` variable that is (randomly) either an `Elf` or a `Kraken`. When we move forward after our assignment and make calls on our `myth` to get our `myth`'s food, what kind of food is it? At compile time, we can't figure out it's type so Swift can't either. This is yet one reason why we can't use generic protocols as a first-class type like concrete protocols.

### Scenario #2 - As a typed array
    
    
    let edibles: [Food] = [human, incorrectQuestionGuesser, stupidWizard, spinach]
    let mythicalCreatures: [MythicalType] = [elf, kraken, sphinx, hippogriff]
    
    for (myth, index) in mythicalCreatures.enumerate() {
        myth.devour(edibles[index])
    }

Maybe you have an array of `Food` objects that you want to feed to your zoo of mythical creatures. Using our `MythicalType` protocol, our code could look very similar to scenario above! However, during our enumeration, it would be very hard to infer a concrete type from `mythicalCreatures` array. Since the parameter of our `MythicalType` protocol's `devour()` function doesn't accept a concrete type, Swift can't infer that you are doing a legal function call when enumerating over your `mythicalCreatures` array. What would our `MythicalType`'s `FoodType` be in each step of our enumeration? No one knows! Can the compiler infer that we are matching types when passing our food in to our `devour()` function throughout the enumeration? No! If you pass the wrong food to the wrong mythical creature at runtime, you could potentially have a pretty nasty crash.

# Well, How do we fix it? With Type Erasure, of Course! Duh.

Because **everyone** knows what _type erasure_ is.

Aaaaand in case you don't, then prepare yourselves...because it's **_LESSON TIME!_**

![](http://static1.squarespace.com/static/5592eb03e4b051859f0b377f/t/5663ba54e4b02fb59907427e/1449376349727/?format=500w)

Even with Swift's shortcomings, that doesn't stop us from being able to do certain workarounds. Above, I stated that we can't use abstract protocols as concrete types. Thankfully, that isn't **completely** true. In programming there is a concept known as a **_[thunk_**](https://en.wikipedia.org/wiki/Thunk) that can help us out with this particular shortcoming! A thunk is a helper struct/class that forwards calls from one object to another object. This is useful for scenarios where those two objects can't normally talk to one another. Using this, we can effectively **_erase_** our abstract generic protocol types in favor of another concrete, more fully-fledged type. This is often referred to as **_type erasure_**.

By creating a class that conforms to our original protocol and uses generics, we can more explicitly define our protocol's associated type. Here is an example of our `MythicalType` protocol, fully type erased as a new, `AnyMythicalType` class (fully commented so you know what's happening with each part of the class):
    
    
    //By making this class a generic class, we can define a type T that we forward to our dependency injected MythicalType.
    //Since this class conforms to our MythicalType protocol, we can call MythicalType's functions regularly.
    
    class AnyMythicalType<T>: MythicalType {
        //These variables are private, preventing others from assigning to them or calling them directly. 
        //Since each type is the exact same type as the functions in our MythicalType, we can assign a MythicalType instance's function signatures to these variables.
        //By assigning a MythicalType instance's function signatures to these variables, we can effectively forward any calls made to AnyMythicalType's functions to the original Spaceship instance.
        private let _prepareFood: (Void -> [T])
        private let _devour: (T -> Void)
    
        //By creating only one required init, we ensure that we can only initialize this class one way.
        required init<U: MythicalType where MythicalType.FoodType == T>(_ mythicalCreature: U) {
            _prepareFood = mythicalCreature.prepareFood
            _devour = mythicalCreature.devour
        }
    
        //Because this forwarding class does conform to the MythicalType protocol, we can call the MythicalType functions directly on this class. This class, as you can see, will forward that message to the function signatures that we assigned at the time of initialization.
        func prepareFood() -> [T] {
            return _prepareFood()
        }
    
        //Here is the second function in the MythicalType protocol and the forwarded message.
        func devour(edible: T) {
            _devour(edible)
        }
    }

Now, using our thunk, we can more concretely express our `MythicalType` protocol's associated FoodType.
    
    
    let kraken = Kraken()
    
    //Here is the magic at work! We can now define our generic `MythicalType`'s FoodType explicitly.
    let mythicalCreature: AnyMythicalType<Human>
    
    mythicalCreature = AnyMythicalType(kraken)

In this example, we've limited our variable so we can only use an instance of `AnyMythicalType` to wrap any `MythicalType` whose `FoodType` is a `Human`. No more compiler complaints! 💖

And by the way, while this may look like a hack, Apple actually uses type erasure for the `[AnySequence`](https://developer.apple.com/library/ios/documentation/Swift/Reference/Swift_AnySequence_Structure/index.html) type in the Swift Standard Library!

# But hold the phone

As of this writing, there is still one issue with using type-erased thunks in Swift: Since the type-erased thunk is just a generic class, it does not **_yet_** support [covariance](https://mikeash.com/pyblog/friday-qa-2015-11-20-covariance-and-contravariance.html).

From a member of the Swift team at Apple:

What this essentially means is that you can't have code that behaves like this quite yet:
    
    
    let anyMythicalCreature: AnyMythicalType
    
    //Logically, these should work, BUT THEY DON'T
    anyMythicalCreature = AnyMythicalType(kraken)
    anyMythicalCreature = AnyMythicalType(elf)
    anyMythicalCreature = AnyMythicalType(sphinx)
    anyMythicalCreature = AnyMythicalType(hippogriff)

In our example, our `anyMythicalCreature` variable is of type `AnyMythicalType<AnyObject>`. Even though normally we can assign anything to a variable of type `AnyObject` because of covariance, our generic types don't support this behavior quite yet. Because of this, you may find that using type erasure may not work for your generic protocols for anything more complex than a one to one assignment in your logic. But never fear! Apple has finally released Swift as [open source](https://www.github.com/apple/swift) so this may mean that one of you can fix this problem! (Or me 🤓).

![](http://static1.squarespace.com/static/5592eb03e4b051859f0b377f/t/5663e11ae4b043ef278af211/1449386271628/?format=500w)

This post was really fun for me to write. And even at a high level, I hope that some of you got to understand complex ideas such as type erasure better than I did when I read about it for the first time. However, if you want to learn more about it, I suggest either [@segiddins](https://www.twitter.com/segiddins)' wonderful [post here](https://realm.io/news/type-erased-wrappers-in-swift/), or this other [awesome post](http://robnapier.net/erasure) by [@cocoaphony](https://www.twitter.com/cocoaphony). The actual creation of a generic protocol is not hard at all. Where you find your real trouble is when trying to use one as you would a regular protocol. Hopefully, all of this can help you with your troubles along the way whilst giving you some extra wisdom as to how to structure your respective architectures when considering using generic protocols. POP is awesome (protocol oriented programming) but sometimes we all need a helping hand. And of course, as always:

![KrakenDevIcon.png](http://static1.squarespace.com/static/5592eb03e4b051859f0b377f/t/56622805e4b055b21a2ec806/1449273349694/KrakenDevIcon.png?format=500w)
