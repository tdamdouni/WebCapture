# Mixins over Inheritance

_Captured: 2015-11-13 at 09:38 from [alisoftware.github.io](http://alisoftware.github.io/swift/protocol/2015/11/08/mixins-over-inheritance/)_

When coming from an Object-Oriented Programming language like ObjC, inheritence is often used to share code between multiple classes. But that solution is not always the best, and have some issues.  
In today's article, we'll see how Swift's Protocol Extensions and their usage as "Mixins" can change the deal.

> _TL;DR: You can download [the Swift Playground containing all the code of that article here](http://alisoftware.github.io/assets/Mixins.playground.zip)._

## The problem with Inheritance

Say you have an app with a lot of `UIViewController` classes that share the same behavior, for example they all have a Burger Menu. You don't want to reimplement the Burger Menu logic (setting up the `leftBarButtonItem`, opening and closing the menu when the button is tapped, etc) in every View Controllers of your app of course.

Well the solution is easy, you'll just create a `CommonViewController`, subclass of `UIViewController` that implement all those behaviors, and then make all your ViewControllers inherit from that `CommonViewController` instead of inheriting from `UIViewController` directly, right? That way, they'll all inherit those methods and behave the same, no need to reimplement all the things every time.
    
    
    class CommonViewController: UIViewController {
      func setupBurgerMenu() { … }
      func onBurgerMenuTapped() { … }
      var burgerMenuIsOpen: Bool {
        didSet { … }
      }
    }
    
    class MyViewController: CommonViewController {
      func viewDidLoad() {
        super.viewDidLoad()
        setupBurgerMenu()
      }
    }
    

But then later during the development phase, you realize that you need an `UITableViewController` or `UICollectionViewController`… Damn, can't use that `CommonViewController`, because it inherits `UIViewController`, not `UITableViewController`!

What would you do, make a `CommonTableViewController` that implement the same things as `CommonViewController` but inherit from `UITableViewController` instead? That'd be a lot of code duplication and quite a bad design.

## Composition to the rescue

Of course, the typical and rightful answer is this:

> Prefer Composition over Inheritence.

That means that insteed of making use of inheritance, we'll make our `UIViewController` contain / be composed of inner classes that provide the behavior.

In our case, we could imagine a `BurgerMenuManager` class that provides all the needed methods to setup the burger menu icon and interact with it, and our various `UIViewControllers` will then have a _property_ holding a `BurgerMenuManager` and can use it to interact with the Burger Menu:
    
    
    class BurgerMenuManager {
      func setupBurgerMenu() { … }
      func onBurgerMenuTapped() { burgerMenuIsOpen = !burgerMenuisOpen }
      func burgerMenuIsOpen: Bool { didSet { … } }
    }
    
    class MyViewController: UIViewController {
      var menuManager: BurgerMenuManager()
      func viewDidLoad() {
        super.viewDidLoad()
        menuManager.setupBurgerMenu()
      }
    }
    
    class MyOtherViewController: UITableViewController {
      var menuManager: BurgerMenuManager()
      func viewDidLoad() {
        super.viewDidLoad()
        menuManager.setupBurgerMenu()
      }  
    }
    

But you can see how that can become cumbersome. And you need to reference the intermediate object `menuManager` each time explicitly.

## Multiple inheritance

Another problem with inheritance is the fact that a lot of Object-Oriented languages don't allow _multiple inheritance_ (for a good reason, especially because of [the diamond problem](https://en.wikipedia.org/wiki/Multiple_inheritance#The_diamond_problem)).

The means that a class can't inherit multiple superclasses.

Let's say you're implementing model classes representing sci-fi characters. You will obviously have to represent `DocEmmettBrown`, `DoctorWho` & `TimeLord`, `IronMan`, `Superman`… so how do they relate each others? Some can time-travel, some can space-travel, some can do both, some can fly and some can't, some are humans and some aren't…

`class IronMan` and `class Superman` can both fly, so we can imagine a `class Flyer` superclass which provides the implementation of the `func fly()` method. But `IronMan` and `DocEmmettBrown` are both human, so we can also imagine a `class Human` superclass, while `Superman` and `TimeLord` will be subclasses of `class Alien`. Wait… so `IronMan` both inherit from `Flyer` and from `Human`? That's not possible in Swift (and neither in a lot of OOP languages).

Should we choose one over the other? But if we make `IronMan` a subclass of `Human` then what about the implementation of the `func fly()` method? We can't obviously implement it in `Human` because not every human can fly, but `Superman` will need that method too, and we don't want to duplicate it.

So, we could use composition there, like make `class SuperMan` be _composed_ of a `var flyingEngine: Flyer` property.

But having to write `superman.flyingEngine.fly()` instead of just `superman.fly()` is not that pretty.

## Mixins & Traits

![Long Live and Mixin](http://alisoftware.github.io/assets/long-live-and-mixin.png)

> _Long Live and Mixin_

That's where the concept of Mixins & Traits[1](http://alisoftware.github.io/swift/protocol/2015/11/08/mixins-over-inheritance/) comes into play.

  * With Inheritance, you define what your classes are. For example every `Dog` _is_ an `Animal`.
  * With Traits, you define what classes _can do_. For example, every `Animal` _can_ `eat()`, but Humans can eat too, and [Doctor Who can eat fish fingers and custard](https://www.youtube.com/watch?v=Oo2RKAHu-kI), even if he's Gallifreyan and not Human nor Animal.

So with Traits, the important stuff is not so much what they are, but what they can do.

> While Inheritance let you describe what an object _is_, Traits let you describe what an object _can do_.

And best of all, a class can adopt multiple `Traits`, as it can do multiple things, while it can only be one thing (inherit only one superclass).

So how does this apply to Swift?

## Protocols with Default Implementation

In Swift 2.0, when you define a `protocol`, you can give default implementations to some or all methods of that protocol, using an `extension` of that protocol. Here's what it looks like:
    
    
    protocol Flyer {
      func fly()
    }
    
    extension Flyer {
      func fly() {
        print("I believe I can flyyyyy ♬")
      }
    }
    

Given that, when you create a class or struct that conforms to that `Flyer` protocol, it gets an implementation of the `fly()` method for free!

That's still a _default implementation_ so you're free to redefine that method if you need to, but if you don't you'll still have the default one:
    
    
    class SuperMan: Flyer {
      // we don't implement fly() there so we get the default implementation and hear Clark sing
    }
    
    class IronMan: Flyer {
      // be we can also give a specific implementation if needs be
      func fly() {
        thrusters.start()
      }
    }  
    

That feature of Protocols with Default Implementation is great for many things, one being of course as you guessed to bring the "Traits" concept to Swift.

## One identity, multiple abilities

The great thing about Traits is that they don't depend on the identity of the object you apply them on. They don't care what the class is and what it inherits from: they just define some functions on that class.

That solves our problem of Doctor Who being both a Time Traveler and an Alien while Dr Emmett Brown being a Time Traveler and a Human. Or IronMan being a Human who can fly while Superman being an Alien who can fly.

> What you are does not define what you can do.

So let's implement our model classes by taking advantage of Traits now.

First, let's define the various Traits:
    
    
    protocol Flyer {
      func fly()
    }
    protocol TimeTraveler {
      var currentDate: NSDate { get set }
      mutating func travelTo(date: NSDate)
    }
    

Then let's give them some default implementations:
    
    
    extension Flyer {
      func fly() {
        print("I believe I can flyyyyy ♬")
      }
    }
    
    extension TimeTraveler {
      mutating func travelTo(date: NSDate) {
        currentDate = date
      }
    }
    

At that point, we'll still use inheritance to define the identities of our characters (what they are), so let's have some parent classes:
    
    
    class Character {
      var name: String
      init(name: String) {
        self.name = name
      }
    }
    
    class Human: Character {
      var countryOfOrigin: String?
      init(name: String, countryOfOrigin: String? = nil) {
        self.countryOfOrigin = countryOfOrigin
        super.init(name: name)
      }
    }
    
    class Alien: Character {
      let species: String
      init(name: String, species: String) {
        self.species = species
        super.init(name: name)
      }
    }
    

And now we can define our characters by both their identity (via inheritance) and abilities (traits / protocol conformance):
    
    
    class TimeLord: Alien, TimeTraveler {
      var currentDate = NSDate()
      init() {
        super.init(name: "I'm the Doctor", species: "Gallifreyan")
      }
    }
    
    class DocEmmettBrown: Human, TimeTraveler {
      var currentDate = NSDate()
      init() {
        super.init(name: "Emmett Brown", countryOfOrigin: "USA")
      }
    }
    
    class Superman: Alien, Flyer {
      init() {
        super.init(name: "Clark Kent", species: "Kryptonian")
      }
    }
    
    class IronMan: Human, Flyer {
      init() {
        super.init(name: "Tony Stark", countryOfOrigin: "USA")
      }
    }
    

Now both `Superman` and `IronMan` use the same implementation of `fly()` even if they inherit from a different superclass (`Alien` for one, `Human` for the other), and both doctors know how to Time Travel even if one is Human and the other is from Gallifrey:
    
    
    let tony = IronMan()
    tony.fly() // prints "I believe I can flyyyyy ♬"
    tony.name  // returns "Tony Stark"
    
    let clark = Superman()
    clark.fly() // prints "I believe I can flyyyyy ♬"
    clark.species  // returns "Kryptonian"
    
    var docBrown = DocEmmettBrown()
    docBrown.travelTo(NSDate(timeIntervalSince1970: 499161600))
    docBrown.name // "Emmett Brown"
    docBrown.countryOfOrigin // "USA"
    docBrown.currentDate // Oct 26, 1985, 9:00 AM
    
    var doctorWho = TimeLord()
    doctorWho.travelTo(NSDate(timeIntervalSince1970: 1303484520))
    doctorWho.species // "Gallifreyan"
    doctorWho.currentDate // Apr 22, 2011, 5:02 PM
    

## An adventure in Space and Time

Now let's introduce a new Space Travel ability/trait:
    
    
    protocol SpaceTraveler {
      func travelTo(location: String)
    }
    

And give it a default implementaton:
    
    
    extension SpaceTraveler {
      func travelTo(location: String) {
        print("Let's go to \(location)!")
      }
    }
    

We can then use Swift's `extensions` to **add conformance to a protocol to an existing class**, so let's add those abilities to the characters we already have defined. If we omit that time when IronMan went to the portal above New York and briefely flew to space, then only The Doctor and Superman can actually Space Travel:
    
    
    extension TimeLord: SpaceTraveler {}
    extension Superman: SpaceTraveler {}
    

![Great Scott!](http://alisoftware.github.io/assets/great-scott.gif)

> _Great Scott!_

Yes, that's all it takes to add this ability/trait to the existing classes! And just like that, they can now `travelTo()` any place! Pretty neat, right?
    
    
    doctorWho.travelTo("Trenzalore") // prints "Let's go to Trenzalore!"
    

## Let's invite more people to the party!

Now let's introduce some more people to the mix:
    
    
    // Come along, Pond!
    let amy = Human(name: "Amelia Pond", countryOfOrigin: "UK")
    // Damn, isn't she not a Time and Space Traveler too? Which doesn't make her a TimeLord, though
    
    class Astraunaut: Human, SpaceTraveler {}
    let neilArmstrong = Astraunaut(name: "Neil Armstrong", countryOfOrigin: "USA")
    let laika = Astraunaut(name: "Laïka", countryOfOrigin: "Russia")
    // Wait, Leïka is a Dog, right?
    
    class MilleniumFalconPilot: Human, SpaceTraveler {}
    let hanSolo = MilleniumFalconPilot(name: "Han Solo")
    let chewbacca = MilleniumFalconPilot(name: "Chewie")
    // Wait, isn't MilleniumFalconPilot defined as "Human"?!
    
    class Spock: Alien, SpaceTraveler {
      init() {
        super.init(name: "Spock", species: "Vulcan")
        // Woops not 100% right
      }
    }
    

Ok, Huston, we have a problem here. Laika is not a Human, neither is Chewie, and Spock is half Human, half Vulcan, so those definitions are quite wrong.

You see what's the problem here? We've taken for granted that `Human` and `Alien` are identities, and we've been bitten by the inheritance again as some classes were forced to be of some Type / inherit from some parent class, whereas in fact it's not always the reality, especially in Sci-Fi.

That's also why using Protocols in Swift, and Protocols Default Implementations, can help removing those constraints imposed on your classes by inheritance.

If `Human` and `Alien` were `protocols` instead of `classes`, we'd have a lot of benefits:

  * We could define a `MilleniumFalconPilot` type without forcing it to be a `Human` and thus allowing Chewie to drive it
  * We could define Laika as an `Astronaut` even if she's not `Human`
  * We could define `Spock` as being both `Human` and `Alien`
  * We could even totally get rid of inheritance in our case, and define our types as `structs` instead of `classes`. A `struct` doesn't support inheritance, but can still conform to as many protocols as you want.

## Protocol everywhere!

So, one solution to this is to make everything a Protocol and get rid of the inheritance completely. After all, we don't care _what_ our characters are, what define heroes is the _abilities_ they have!

![Exterminate Inheritance!](http://alisoftware.github.io/assets/dalek-exterminate-inheritance.png)

> _Exterminate Inheritance!_

I've included [a Swift Playground that you can download here](http://alisoftware.github.io/assets/Mixins.playground.zip) that contains the code shown in that blog post, and demonstrate in Page 2 of the Playground a solution with everything made a Protocol and Structs, with no inheritance at all. Don't hesitate to take a look!

Of course that doesn't mean that you have to get rid of inheritance at all cost (don't listen too much to that Dalek, they lack feelings after all 😉). Inheritance is still useful and can still make sense -- e.g. it still feels logical that a `UILabel` is a _subclass_ of `UIView`. But that gives you a taste of what Mixins & Protocols with Default Implementations can offer.

## Conclusion

When practicing Swift, you'll realize that it's really a Protocols-Oriented language, and that using a Protocol is more common and more powerful in Swift that it was in Objective-C. After all, protocols like `Equatable`, `CustomStringConvertible` and any protocol in `-able` in the Swift Standard Library can actually be seen as Mixins!

With Swift Protocols and Protocols Default Implementations, you can implement Mixins & Traits, but you can also implement something similar to Abstract Classes[2](http://alisoftware.github.io/swift/protocol/2015/11/08/mixins-over-inheritance/) and more, and make your code way more flexible.

The Mixins & Traits approach allows you to describe types by **what they can do rather than what they are**, and more importantly, to opt-in capabilities into your types. It's like doing your shopping and **pick the capabilities you want for your type, whatever the class they inherit**, if any.

Back at the first example, you can for example create a `protocol BurgerMenuManager` with a default implementation, then simply make your View Controllers (whether they are `UIViewController`, `UITableViewController` or whatnot) conform to that protocol so it will automatically gain those abilities and features from `BurgerMenuManager` for free, without worrying about the parent class of the `UIViewController`!

![I don't wanna go](http://alisoftware.github.io/assets/i-dont-wanna-go.gif)

> _I don't wanna go_

There's a lot more to say about Protocol Extensions, and I'm tempted to continue that article to tell you a lot more about them, as they can improve your code in a lot more ways. But hey, that post is already long enough, and let's keep some more for future blog posts, hoping to so see you there!

In the meantime, long live and prosper, and Geronimo! 😎

  1. I'm not gonna enter in the details of the difference between the concept of "Mixin" and "Traits" here. Let's say for the sake of simplicity that these two are similar and those two words can be used interchangeably in the context of this article. [↩](http://alisoftware.github.io/swift/protocol/2015/11/08/mixins-over-inheritance/)

  2. That's probably gonna be a topic for a future blog post. [↩](http://alisoftware.github.io/swift/protocol/2015/11/08/mixins-over-inheritance/)
