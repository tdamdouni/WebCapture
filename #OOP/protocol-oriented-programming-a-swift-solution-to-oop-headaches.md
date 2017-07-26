# Protocol Oriented Programming: A Swift Solution to OOP Headaches

_Captured: 2017-03-25 at 19:47 from [medium.com](https://medium.com/ios-seminar/protocol-oriented-programming-a-swift-solution-to-oop-headaches-e05d9c5d29a1#.smacwa2q1)_

### Why is OOP so Popular?

Object Oriented Programming (OOP) was the classic strategy to write modular code for decades, and with good reason.

  1. **Reusability: **Well-written objects are stand-alone entities that can be plugged into other programs. If I implement an optimized tree, I can use it in any part of an existing project, or in a brand new one, without writing more code.
  2. **Skip the details**: Another programmer doesn't need to know your object's implementation. If I see a "Sort" function, I can use without worrying what the code looks like.
  3. **Error-Proofing**: We can hide access to functions or variables in a class, which prevents other developers, that are less familiar with our code, from create bugs. Others see only what they need to see.
  4. **Make Big Projects Manageable: **Big projects get complicated. OOP lets us break a large problem into sub problems -- each of which are handled by different objects. If Nabil, Julia, and Alex are making a [space invaders](http://www.pacxon4u.com/space-invaders/) game. Nabil can build an object to represent Aliens, Julia can build a GameBoard object that keeps track of my score, number of lives, and when the game starts/finishes, and Alex can make objects representing my tank and its missiles. In end, we compose these objects to build a functioning game.
  5. **Updating Code: **With modular code we can write easily add to, update, or remove specific components as time goes on. **e.g. **In a building made of bricks, you can swap out a cracked brick with a new one instead of replacing entire sections of the building.

### Out With the Old

Though very handy, OOP comes with its fair share of issues:

  1. **"GOD" objects, Massive View Controller**: To maintain modularity programmers use the one class, one purpose principal. However bloated viewControllers and models are common by-products of popular swift design patterns (MVC, MVVM). Passing around chunky objects slows your code, and makes modularity difficult as you build out. If an object holds too much of the functionality you need, new code you write will end up depending on it too.
  2. **Multiple Ownership: **Lets suppose you and a fellow engineer (Nick), are working on separate ViewControllers that reference the same **_BankAccount_** object. If you add credit in **_firstViewController_** while the Nick removes credit in **_secondViewController_**, both of you will end up with an unexpected result. Classes are passed by reference, so changing the values in one area of your project will cause changes to that object's values in every other place. This makes it difficult to test the isolated effect of your functions on a given object.
  3. **The Subclassing Problem:** A Problem so big is deserves its own section

Your stomach grumbles, so you decide to check out the old "OOP burgers" joint, where they're famous for their cheeseburger. The cheeseburger comes with Pickles, Tomatoes, Onions, and Mushrooms. But you're allergic to Mushrooms! So you ask the waiter to substitute the mushrooms for Kale -- you LOVE Kale. The waiter shakes his head and says it's impossible. He tells you the only way you can have Kale is to get a CheeseBurger with all its standard ingredients, with the kale will get placed on top of everything else…Bummer.

OOP driven inheritance often gives subclasses more baggage than we desire. Lets first take a look at how inheritance can be used effectively, then take a look at how this can lead us into problems. Finally I'll introduce you to Protocol Oriented Programming: A "Swifty" way to achieve everything OOP offers, while skipping many of its issues.

Here's an example of a typical inheritance pattern:

class Vehicle {

var wheels: Int

var isMoving: Bool

var topSpeed: Int

var gasTank: Int

init(wheels:Int = 4, isMoving:Bool = false, topSpeed:Int = 100, gasTank:Int = 100){

self.wheels = wheels

self.isMoving = isMoving

self.topSpeed = topSpeed

self.gasTank = gasTank

}

func start(){}

func stop(){}

func park(){}

func fillGas(){}

}

// Sports Vehicle class inherits from vehicle

class SportsVehicle: Vehicle {

var isTurbo: Bool

func goTurbo(){}

init(){

self.isTurbo = false

super.init()

}

}

> _SportsVehicle Inherits from Vehicle_

This is effective use of inheritance because a `SportsCar` will utilize everything in `Vehicle`, plus some extra features that should only be in sports vehicles. But hey, we're in the age the electric vehicle, so lets create a subclass for that too!

class ElectricVehicle: Vehicle {

var batteryLevel: Int

func rechargeBattery(){}

init(){

self.batteryLevel = 5

super.init()

}

}

This is an example of poor inheritance.

We get extraneous features, `fillGas` and `gasTank` that are irrelevant in an `ElectricVehicle` class because

  1. Electric vehicles don't use these components by design. Having them in an electric vehicle class is unintuitive.
  2. For a developer using your electric vehicle object, it's really confusing to see functions that modify obsolete features -- Why are they here? Its unnecessary bloating.

Now lets say I want to add a `superCharging` feature to `ElectricVehicle`. This feature will get inherited (along with `gasTank`), by every class that subclasses `ElectricVehicle`. But not everything that needs inheritance from `ElectricVehicle` uses `superCharging`! Suppose 8/10 electric vehicles use supercharging -- our choices are to either implement supercharging in 8 subclasses of `ElectricVehicle` or bloat two subclasses with code for supercharging that will not get used.

This problem only gets worse as we continue down subclass down the chain.

![](https://cdn-images-1.medium.com/max/800/1*ZBy1cMNKlZOYR_AHRVNadQ.jpeg)

> _Every function and field in ElectricVehicle is dumped into each of these three subclasses_

In bigger projects, we get massive inheritance structures that go several layers deep:

![](https://cdn-images-1.medium.com/max/800/1*pljS68QSe16eb_y4EQs61A.png)

These structures are prone to causing architectural headaches. For example, What if we wanted to add a penguin class to the following structure?

![](https://cdn-images-1.medium.com/max/800/1*ziWdISgNakU3t2HyKkPpPg.png)

> _Where does penguin go?_

Penguins don't fly. So we'd have to create a two new classes "Flying Birds" and "Flightless Birds" and reorganize all of our birds under these classes. Wait, what about birds that can swim? The headache goes on…

How do we prevent the subclassing problem without knowing all the classes we are going to add ahead of time?

Swift is a language designed to give power to value types. The standard library is designed with just 4 classes, and 95 instances of structs and enums.

Protocol Oriented Programming (POP) is an architecture encourages developers to leverage the functionality packed into value types: Use structs, enums, and protocols in place of additional classes.

Why is this helpful?

Lets go back to our Vehicle problem.

We have features that need to be shared between electric and gas vehicles (such as the ability to `start`, `stop`, `park`), and others that belong exclusively to one group (filling gas, charging batteries).

Lets build protocols for each of these feature sets!

// Electric Cars

protocol Chargeable {

func recharge()

}

// Gas Cars

protocol Fillable {

func fillTank()

}

// Features Needed by both

protocol Driveable {

func start()

func stop()

func park()

}

// Now each struct only uses the features it needs!

struct ElectricVehicle: Driveable, Chargeable{

}

struct SportsVehicle: Driveable, Fillable{

}

> _Separate individual "Behaviors" into protocols_

Now we can put functions exclusively where needed, while getting the added flexibility of conforming very disparate classes to the same protocol. Before the `fillable()` functionality was confined to the `Vehicle` class and classes that inherited from it. But if I wanted to create an unrelated type now, let's say a `Bucket` struct, I can conform that to the fillable protocol as well!

Another bonus is that we can use `Structs` in place of classes. Previously we used classes in order to take advantage of inheritance, but that is no longer necessary because we get the desired functionality through protocols.
