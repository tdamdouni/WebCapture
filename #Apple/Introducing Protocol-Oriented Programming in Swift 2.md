# Introducing Protocol-Oriented Programming in Swift 2

_Captured: 2015-11-25 at 20:50 from [www.raywenderlich.com](http://www.raywenderlich.com/109156/introducing-protocol-oriented-programming-in-swift-2)_

![Swift Bird brings speedy new features to Swift 2!](http://cdn2.raywenderlich.com/wp-content/uploads/2015/06/swift-new.jpg)

> _Swift Bird brings speedy new features to Swift 2!_

_Note:_ This tutorial requires Xcode 7 and Swift 2, which will be in beta until this fall. You can download the latest beta on [Apple's developer portal](https://developer.apple.com/xcode/downloads/).

At WWDC 2015, Apple announced the second major revision of the Swift language with Swift 2, which includes [several new language features](http://www.raywenderlich.com/108522/whats-new-in-swift-2) to help improve the way you write code.

Among the more exciting new features are _protocol extensions_. In the first version of Swift, it was possible to extend the functionality of existing `class`, `struct` and `enum` types. Now with Swift 2, you can extend a `protocol` as well.

While it may only seem like a minor feature at first, protocol extensions are extremely powerful and can transform the way you write code. In this tutorial, you'll explore the ways you can create and use protocol extensions, as well as the new techniques and protocol-oriented programming patterns they open up to your code.

You'll also see how the Swift team was able to use protocol extensions to improve the Swift standard library itself, and how it impacts the code you write.

## Getting Started

Begin by creating a new playground. In Xcode, select _File_\_New_\_Playground…_ and name the playground _SwiftProtocols_. You can select any platform, since all the code in this tutorial is platform-agnostic. Click _Next_ to choose where you would like to save it, and finally click _Create_.

Once your new playground is open, add the following code to it:
    
    
    protocol Bird {
      var name: String { get }
      var canFly: Bool { get }
    }
     
    protocol Flyable {
      var airspeedVelocity: Double { get }
    }

This defines a simple protocol `Bird` with properties `name` and `canFly`, as well as a `Flyable` protocol which defines `airspeedVelocity`.

In a pre-protocol world, you might have started with `Flyable` as a base class and then relied on inheritance to define `Bird` as well as other things that fly, such as airplanes. Note that here, _everything_ is starting out as a protocol!

You'll see how this makes the entire system more flexible when you start to define actual types next.

## Defining Protocol-conforming Types

Add the following `struct` definition to the bottom of the playground:
    
    
    struct FlappyBird: Bird, Flyable {
      let name: String
      let flappyAmplitude: Double
      let flappyFrequency: Double
      let canFly = true
     
      var airspeedVelocity: Double {
        return 3 * flappyFrequency * flappyAmplitude
      }
    }

This defines a new struct `FlappyBird`, which conforms to both the `Bird` and `Flyable` protocols. Its `airspeedVelocity` is calculated as a function of `flappyFrequency` and `flappyAmplitude`. Being flappy, it returns `true` for `canFly`. :]

Next, add the following two struct definitions to the bottom of the playground:
    
    
    struct Penguin: Bird {
      let name: String
      let canFly = false
    }
     
    struct SwiftBird: Bird, Flyable {
      var name: String { return "Swift \(version)" }
      let version: Double
      let canFly = true
     
      // Swift is FAST!
      var airspeedVelocity: Double { return 2000.0 }
    }

A `Penguin` is a `Bird`, but cannot fly. A-ha - It's a good thing you didn't take the inheritance approach, and make all birds flyable after all! A `SwiftBird` is of course very fast with a high airspeed velocity.

Already you can see some redundancies. Every type of `Bird` has to declare whether it `canFly` or not, even though there's already a notion of `Flyable` in your system.

## Extending Protocols With Default Implementations

With protocol extensions, you can define default behavior for a protocol. Add the following just below the `Bird` protocol definition:

This defines an extension on `Bird` that sets the default behavior for `canFly` to return `true` whenever the type is also `Flyable`. In other words, any `Flyable` bird no longer need to explicitly declare so!

![protocols-extend](http://cdn3.raywenderlich.com/wp-content/uploads/2015/06/protocols-extend-480x280.png)

Swift 1.2 introduced this `where` syntax to if-let binding, and Swift 2 brings that power to _conditionally_ extend a protocol.

Delete the `let canFly = true` from both the `FlappyBird` and `SwiftBird` struct declarations. You'll see that the playground successfully builds since the protocol extension now handles that requirement for you.

## Why Not Base Classes?

Protocol extensions and default implementations may seem similar to using a base class or even [abstract classes](https://en.wikipedia.org/wiki/Abstract_type) in other languages, but they offer a few key advantages in Swift:

  * Because types can conform to more than one protocol, they can be _decorated_ with default behaviors from multiple protocols. Unlike multiple inheritance of classes which some programming languages support, protocol extensions do not introduce any additional state. 
  * Protocols can be adopted by classes, structs and enums. Base classes and inheritance are restricted to class types. 

In other words, protocol extensions provide the ability to define default behavior for _value_ types and not just classes.

You've already seen this in action with a struct; next, add the following enum definition to the end of the playground:
    
    
    enum UnladenSwallow: Bird, Flyable {
      case African
      case European
      case Unknown
     
      var name: String {
        switch self {
          case .African:
            return "African"
          case .European:
            return "European"
          case .Unknown:
            return "What do you mean? African or European?"
        }
      }
     
      var airspeedVelocity: Double {
        switch self {
          case .African:
            return 10.0
          case .European:
            return 9.9
          case .Unknown:
            fatalError("You are thrown from the bridge of death!")
        }
      }
    }

As with any other value type, all you need to do is define the correct properties so `UnladenSwallow` conforms to the two protocols. Because it conforms to both `Bird` and `Flyable`, it also gets the default implementation for `canFly`!

Did you really think this tutorial involving `airspeedVelocity` wouldn't include a Monty Python reference? :]

## Extending Protocols

Perhaps the most common use of protocol extensions is extending external protocols, either those defined in the Swift standard library or a third party framework.

Add the following to the bottom of the playground:
    
    
    extension CollectionType {
      func skip(skip: Int) -> [Generator.Element] {
        guard skip != 0 else { return [] }
     
        var index = self.startIndex
        var result: [Generator.Element] = []
        var i = 0
        repeat {
          if i % skip == 0 {
            result.append(self[index])
          }
          index = index.successor()
          i++
        } while (index != self.endIndex)
     
        return result
      }
    }

This defines an extension on `CollectionType` that defines a new `skip(_:)` method that "skips" every `skip` elements in the collection and returns an array of just the unskipped elements.

`CollectionType` is a protocol conformed to by types such as arrays and dictionaries in Swift. That means this new behavior now exists on every `CollectionType` in your app! Add the following code to the bottom of the playground to see it in action:
    
    
    let bunchaBirds: [Bird] =
      [UnladenSwallow.African,
       UnladenSwallow.European,
       UnladenSwallow.Unknown,
       Penguin(name: "King Penguin"),
       SwiftBird(version: 2.0),
       FlappyBird(name: "Felipe", flappyAmplitude: 3.0, flappyFrequency: 20.0)]
     
    bunchaBirds.skip(3)

Here, you're defining an array of birds including many of the types you've already defined. Since arrays conform to `CollectionType`, that means `skip(_:)` is available to them too.

### Extending Your Own Protocols

Perhaps as exciting as adding new behaviors on protocols from the Swift standard library, you can also define _default_ behaviors.

Modify the `Bird` protocol declaration to conform to the `BooleanType` protocol:

Conforming to `BooleanType` means your type needs to have a `boolValue` property so it acts like a Boolean. Does that mean you now have to add this property to _every_ current and future `Bird` type?

Of course, there's an easier way with protocol extensions. Add the code underneath the `Bird` definition:

This extension will make the `canFly` property represent each `Bird` type's Boolean value.

To try it out, add the following to the bottom of the playground:

You should see `"I can fly!"` appear in the assistant editor. But more notably, you just used an African Unladen Swallow in an `if` statement!

## Effects on the Swift Standard Library

You've seen how protocol extensions are a great way to customize and extend the capabilities of your code as well protocols defined outside of your app. What may surprise you is how the Swift team was able to use protocol extensions to even improve the way the Swift standard library is written as well.

Swift helps promote functional programming paradigms by including methods such as `map`, `reduce`, and `filter` in the standard library. These methods exist on various `CollectionType` members such as `Array`:

Calling `map` on the array returns another array, on which `reduce` is called to reduce the result down to the final value _9_.

In this case, `map` and `reduce` are included on `Array` as part of the Swift standard library. If you _Cmd-Click_ on `map`, you can see how it is defined.

In Swift 1.2, you'd see a definition that looks like this:
    
    
    // Swift 1.2
    extension Array : _ArrayType {
      /// Return an `Array` containing the results of calling
      /// `transform(x)` on each element `x` of `self`
      func map<U>(transform: (T) -> U) -> [U]
    }

The `map` function here is defined as an extension on `Array`. Swift's functional functions work for more than just `Array` however, and should be for any `CollectionType`, so how does Swift 1.2 make this work?

If you call `map` on a `Range` and _Cmd-Click_ on `map` from there, you'll see the following definition:
    
    
    // Swift 1.2
    extension Range {
      /// Return an array containing the results of calling
      /// `transform(x)` on each element `x` of `self`.
      func map<U>(transform: (T) -> U) -> [U]
    }

It turns out that in Swift 1.2, `map` needed to be re-defined for each `CollectionType` in the Swift standard library! This is because although `Array` and `Range` are both `CollectionType`, structs cannot be subclassed and cannot have common implementations.

This isn't just a nuance of how the Swift standard library is made, it also limits what you can do with Swift types.

The generic function below takes in a `CollectionType` of `Flyable` and returns the element with the highest `airspeedVelocity`:

In Swift 1.2 without protocol extensions, this is actually a build error. The `map` and `reduce` functions only exist on a set of predefined types and will not work on any arbitrary `CollectionType`.

With Swift 2.0 and protocol extensions, the definition for `map` in both `Array` and `Range` looks like this:
    
    
    // Swift 2.0
    extension CollectionType {
      /// Return an `Array` containing the results of mapping `transform`
      /// over `self`.
      ///
      /// - Complexity: O(N).
      func map<T>(@noescape transform: (Self.Generator.Element) -> T) -> [T]
    }

Although you can't see the source code of `map` -- at least until Swift 2 is open sourced! -- `CollectionType` now has a default implementation of `map` that all `CollectionType` types get for free!

Add the generic function mentioned earlier to the bottom of the playground:

The `map` and `reduce` methods are available to your collection of `Flyable` instances. Now you can finally answer the question of who is the fastest of them all by adding the following code to the bottom of the playground:
    
    
    let flyingBirds: [Flyable] = 
      [UnladenSwallow.African,
      UnladenSwallow.European,
      SwiftBird(version: 2.0)]
     
    topSpeed(flyingBirds) // 2000.0

As if it were ever in doubt! :]

## Where To Go From Here?

You can download the complete playground with all the code in this tutorial [here](http://cdn1.raywenderlich.com/wp-content/uploads/2015/06/SwiftProtocols.playground.zip).

You've seen the power of protocol-oriented programming by creating your own simple protocols and extending them using protocol extensions. With default implementations, you can give existing protocols common and automatic behavior, much like a base class but better since it can apply to structs and enums too.

In addition, protocol extensions can not only be used to extend your own protocols, but can extend and provide default behavior to protocols in the Swift standard library, Cocoa, and Cocoa Touch.

To get an overview of the other exciting features in Swift 2, you can read [our "what's new in Swift 2.0" article](http://www.raywenderlich.com/108522/whats-new-in-swift-2), or the Swift 2 announcement on [Apple's Swift blog](https://developer.apple.com/swift/blog/?id=29).

You can view an excellent WWDC session on [Protocol Oriented Programming](https://developer.apple.com/videos/wwdc/2015/?id=408) on Apple's developer portal for a more in-depth look into the theory behind it all.

Have any questions? Let us know in the forum discussion below!
