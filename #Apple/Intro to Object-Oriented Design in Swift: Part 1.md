# Intro to Object-Oriented Design in Swift: Part 1/2

_Captured: 2015-11-25 at 20:44 from [www.raywenderlich.com](http://www.raywenderlich.com/81952/intro-object-oriented-design-swift-part-1)_

![Object-oriented design](http://cdn3.raywenderlich.com/wp-content/uploads/2013/11/oop.jpg)

> _Object-oriented programmers love vehicle hierarchies._

_Update 4/11/2015_: Updated for Xcode 6.3 / Swift 1.2

_Update note:_ This tutorial was updated for iOS 8 and Swift by Ray Fix. [Original post](http://www.raywenderlich.com/?p=45940) by Tutorial Team member [Ellen Shapiro](http://www.raywenderlich.com/u/designatednerd).

A huge piece of the programming puzzle in working with Cocoa, Objective-C and Swift is _Object-Oriented Programming_. Almost all modern programming languages use this approach, and wrapping your head around its concepts and patterns can be incredibly helpful when reading and writing code.

Underneath the relation between `UITableView` and `UIScrollView` or `UIView` and `UIButton` are the fundamental concepts of object-oriented design. By understanding these concepts you'll have a better grasp on why things are organized the way they are in Cocoa and Cocoa Touch, and you'll be a more thoughtful programmer when writing your own apps and frameworks.

In this series you'll learn more about object-oriented design, including the following concepts:

  * The Basics Of Objects
  * Inheritance
  * Model-View-Controller
  * Polymorphism
  * Common Object-Oriented Patterns

This series is designed for developers who are fairly new to programming overall. You likely haven't worked with other languages extensively, and you're not quite sure why everything is being done in a particular way.

This tutorial will cover object-oriented design principles rather than specific syntax, so you should already know the basics of Swift and Xcode before reading on. If you need a refresher on the basics, check out the [Quick Start Tutorial](http://www.raywenderlich.com/?p=74438).

## Getting Started

In order to try and understand some of these concepts in a more concrete manner, you'll build an application called _Vehicles_. This uses one of the most common metaphors for translating real-world items into virtual objects: the "vehicle", which could be a bicycle, a car, or really anything with wheels.

For instance, this is a vehicle:

![Kleinwagen_16](http://cdn4.raywenderlich.com/wp-content/uploads/2013/11/Fotolia_56206137_XS.jpg)

But so is this:

![Motorcycle on a white background](http://cdn1.raywenderlich.com/wp-content/uploads/2013/11/Fotolia_47228812_XS.jpg)

> _[Motorcycle on a white background](http://cdn1.raywenderlich.com/wp-content/uploads/2013/11/Fotolia_47228812_XS.jpg)_

Or this:

![B](http://cdn5.raywenderlich.com/wp-content/uploads/2013/11/Fotolia_47970160_XS.jpg)

Or this:

![European 18-wheeler with canvas trailer](http://cdn2.raywenderlich.com/wp-content/uploads/2013/11/Fotolia_56277265_XS.jpg)

> _[European 18-wheeler with canvas trailer](http://cdn2.raywenderlich.com/wp-content/uploads/2013/11/Fotolia_56277265_XS.jpg)_

In this part of the tutorial, you'll create a data model using basic object-oriented techniques to represent all of these vehicles, and a simple application which implements the data model and displays vehicle data to the user.

Download [the starter project](http://cdn3.raywenderlich.com/wp-content/uploads/2014/11/SwiftVehiclesStarter11.zip), which contains a basic framework for the application you'll use to learn about Object-Oriented Programming.

## The Basics Of Objects

In object-oriented programming, the basic goal is to break down the characteristics of a "thing" to create an _object_ or _objects_ that describe what that thing _is_ and what that thing _does_.

Sometimes, as with vehicles, your "thing" has a real-world equivalent. Sometimes it doesn't, as with the many different types of `UIViewController` objects. For the sake of simplicity, you'll start out by creating objects that have real-world analogs.

In order to answer the question of what a "thing" is, you have to first determine what its defining characteristics are.

Other languages will refer to this as a "field", a "member", or even just a "variable". However, in Swift the defining characteristics of an object are shown by its _properties_.

Think about the generic concept of a "vehicle" for a moment -- something that describes all of the photos above. What common characteristics of a "vehicle" spring to mind?

  * It has a number of wheels.
  * It has some sort of power source, whether human, gas, electric, or hybrid, which makes it move.
  * It has a brand*, like Ford, Chevy, Harley-Davidson, or Schwinn.
  * It has a model name like Mustang, Corvette, Sportster, or Fastback.
  * It has a year associated with its manufacture.

_*- this is sometimes referred to in cars and trucks as a "Make", but we'll refer to it as a "brand" across the board for clarity._

Now that you have the basic characteristics of a vehicle, you can create an Object with these characteristics.

The file _Vehicle.swift_ defines a class of objects named `Vehicle`.

Open _Vehicle.swift_ and add the following code within the `class` braces:
    
    
    var brandName = "null"
    var modelName = "null"
    var modelYear = 0
    var powerSource = "null"
    var numberOfWheels = 0

These property declarations describe the characteristics of the object you want to keep track of. For now you are just providing placeholder values so that the Swift compiler can infer the types as a `String` or `Int`. (Later, in Part 2, you will add a real initializer to get rid of these dummy, placeholder values. This is why you are not using Swift _Optionals_ to represent them.)

### Minor Digression: Initialization and Properties

One of the important safety features of Swift is how it enables and enforces proper initialization of objects. This means that it's virtually impossible to use uninitialized memory. The above properties are called _stored properties_ and must be initialized either by setting them explicitly as you have done, or by initializing them in an `init()` method. If you supply all of your stored properties with values, the compiler won't require you to explicitly set them in the `init()` method.

### Minor Digression: Class versus Struct

In Swift, you can define an object-like thing with the keyword `class` or `struct`. In this tutorial, you will be using `class` to define objects because these allow you to build class hierarchies and override methods. Structs, while very useful for many things, are more static in nature and don't allow for this. For more information on when to use a `class` versus a `struct` see [The Swift Programming Language Book](https://developer.apple.com/library/prerelease/mac/documentation/Swift/Conceptual/Swift_Programming_Language/ClassesAndStructures.html).

## Describing the Object

On to the second critical question for every object -- what exactly does the object _do_?

A programmatic description of what an object does is almost universally called a _method_. Think about the common actions of the vehicles in the photos above:

  * It can go forward
  * It can go backward
  * It can stop
  * It can turn
  * It can change gears
  * It can make some sort of noise (e.g. a horn or a bell)

Most often, you'd be using methods that don't return anything. However, to make it a little easier to display what's happening in your app, you're going to use some methods that return `String` objects.

### A Minor Digression: Class Methods vs. Instance Methods

You've probably noticed when writing code that some methods have the `class` keyword in front of them. These indicate that a method is a Class method as opposed to a normal Instance method.

The simplest way to think of the difference is like a schematic blueprint in the physical world: There's only one blueprint for something, but using that blueprint, you can make many different copies.

A class method is an action that can be performed with that blueprint, but without creating a specific copy of the object from that blueprint. For example, `UIColor` has the class method `blackColor()` that returns a new instance of `UIColor` set to black.

An instance method, requires a specific copy of the object created using that blueprint to perform any action. For example, the `String` instance `"Hello There"` has an instance method `lowercaseString` that would return `"hello there"`. A class method `lowercaseString` wouldn't make any sense since that's just the blueprint for a string - there's no actual text to lower case!

### Adding Basic Methods to Your Class

Still in _Vehicle.swift_, add the following methods to your Vehicle class.
    
    
    func goForward() -> String {
      return "null"
    }
     
    func goBackward() -> String {
      return "null"
    }
     
    func stopMoving() -> String {
      return "null"
    }
     
    func turn(degrees:Int) -> String {
      var normalizedDegrees = degrees
     
      //Since there are only 360 degrees in a circle, calculate what a single turn would be.
      let degreesInACircle = 360
     
      if (normalizedDegrees > degreesInACircle || normalizedDegrees < -degreesInACircle) {
        // The % operator returns the remainder after dividing.
        normalizedDegrees = normalizedDegrees % degreesInACircle
      }
     
      return String(format: "Turn %d degrees.", normalizedDegrees)
    }
     
    func changeGears(newGearName:String) -> String {
      return String(format: "Put %@ into %@ gear.",self.modelName, newGearName)
    }
     
    func makeNoise() -> String {
      return "null"
    }

Most of this code is just the skeleton of setting up the methods; you'll fill in the implementation details later. The `turn()` and `changeGears()` methods have some logging output too, which will help you test that your methods are working before you continue any further in the tutorial.

Open _AppDelegate.swift_, and replace the implementation of `application(_:didFinishLaunchingWithOptions:)` with the following:
    
    
    func application(application: UIApplication, 
                     didFinishLaunchingWithOptions launchOptions: [NSObject: AnyObject]?) -> Bool {
     
      var vehicle = Vehicle()
      // Test methods with implementations
      println("Vehicle turn: \(vehicle.turn(700))")
      var changeGearResult = vehicle.changeGears("Test")
      println("Vehicle change gears: \(changeGearResult)")
     
      // Test methods without implementations
      println("Vehicle make noise: \(vehicle.makeNoise())")
      println("Vehicle go forward: \(vehicle.goForward())")
      println("Vehicle go backward: \(vehicle.goBackward())")
      println("Vehicle stop moving: \(vehicle.stopMoving())")
     
      return true
    }

Once the vehicle instance is instantiated, you'll call each of the instance methods and log the output to see what they do.

Build and run your app; you'll see that all implemented strings return proper logs with the appropriate items filled in. Since you have put in placeholder values for most of the properties, you will see this in the debug console:

![Debugger](http://cdn3.raywenderlich.com/wp-content/uploads/2014/09/Screen-Shot-2014-09-22-at-11.12.21-PM-700x115.png)

You'll be using _Inheritance_ to provide more specific implementations of each of these methods.

## Inheritance

The basic concept of inheritance is similar to that of genetics: children inherit the characteristics of their parents.  
However, it's a lot more strict than real world genetics in a single-inheritance language like Swift. Rather than having two parents from whom you inherit a mix of characteristics, "child" classes, or _subclasses_, inherit all the characteristics of their "parent" classes, or _superclasses_.

To see inheritance in action, create a subclass of `Vehicle` called `Car`. Go to _File\New\File…_ and select _iOS\Source\Swift File_. Name the file _Car_.

Now open _Car.swift_ and add the following class definition for Car:
    
    
    class Car : Vehicle { 
      override init() {
        super.init()
        numberOfWheels = 4
      }
    }

`Car` derives from your `Vehicle` class and inherits all of its methods and properties. Note that it makes perfect sense to say, "A `Car` is-a `Vehicle`". If you can naturally say, "Subclass is-a Superclass", derivation usually makes sense.

Since you provided values for all of the properties in the superclass, there's no need to explicitly set each in your subclass. You may only want to set certain properties and leave the others as their defaults. For `Car`s, we know that the `numberOfWheels` will be four. To express this you `override` the initializer, call the superclass initializer, and then customize the `numberOfWheels` property to four. The order is significant. If you called `super.init()` last, `numberOfWheels` would get reset back to 0. Fortunately, the Swift complier will not allow you to make this mistake.

But what if you need more information to describe the car? Cars have more specific characteristics than just the number of wheels How many doors does it have? Is it a hatchback or does it have a normal trunk? Is it a convertible? Does it have a sunroof?

Well, you can easily add those new properties! In _Car.swift_, above your initializer, add:

Now, any _Car_ object can be customized with all properties from the _Vehicle_ and _Car_ classes.

### Overriding Methods

Now that you've added the appropriate additional properties, you can _override_ several methods from the superclass to provide full implementations of those methods.

Overriding a method means "taking a method declared in the superclass and creating your own implementation." For example, when you add a new _UIViewController_ object, it already comes with overridden methods for `viewDidLoad` and others. In Swift, when you override a method, you must use the `override` keyword. This communicates your intent to the compiler. If you accidentally misspell a method parameter, for example, the compiler can let you know that something is wrong. Also, if you didn't know you were overriding a method, the compiler will also let you know.

Unlike an initializer method, when you override a normal method, you can do one of two things:

  1. Include a call to the `super.method()` to take advantage of everything happening higher up the inheritance chain, or
  2. Provide your own implementation from scratch.

In all of the _UIViewController_ methods, you can tell that Apple wants you to call the `[super method]` - there's some important stuff in there that needs to execute before your _UIViewController_ subclass can do its work.

However, since most of the methods you're going to override in the _Car_ class are returning empty values, you can just create your own implementations. There's nothing useful in the superclass's implementation so there's no need to call it.

Still in _Car.swift_ add the following private helper method to simplify your superclass override:

Some vehicles such as bicycles don't need to be started, but cars do! Here you use the access control keyword `private` to express the fact that this method should not be used outside of this file.

Next, add the remaining superclass overrides:
    
    
    // MARK: - Superclass Overrides
    override func goForward() -> String {
      return String(format: "%@ %@ Then depress gas pedal.", start(), changeGears("Forward"))
    }
     
    override func goBackward() -> String {
      return String(format: "%@ %@ Check your rear view mirror. Then depress gas pedal.", start(), changeGears("Reverse"))
    }
     
    override func stopMoving() -> String {
      return String(format: "Depress brake pedal. %@", changeGears("Park"))
    }
     
    override func makeNoise() -> String {
      return "Beep beep!"
    }

Now that you have a concrete, or fully implemented, subclass of Vehicle, you can start building out your Table View controller.

## Building out the User Interface

Open _VehicleListTableViewController.swift_ and add the following method just after `viewDidLoad`:
    
    
    // MARK: - Data setup
    func setupVehicleArray() {
      // Clear the array. (Start from scratch.)
      vehicles.removeAll(keepCapacity: true)
     
      // Create a car.
      var mustang = Car()
      mustang.brandName = "Ford"
      mustang.modelName = "Mustang"
      mustang.modelYear = 1968
      mustang.isConvertible = true
      mustang.isHatchback = false
      mustang.hasSunroof = false
      mustang.numberOfDoors = 2
      mustang.powerSource = "gas engine"
     
      // Add it to the array
      vehicles.append(mustang)
     
      // Create another car.
      var outback = Car()
      outback.brandName = "Subaru"
      outback.modelName = "Outback"
      outback.modelYear = 1999
      outback.isConvertible = false
      outback.isHatchback = true
      outback.hasSunroof = false
      outback.numberOfDoors = 5
      outback.powerSource = "gas engine"
     
      // Add it to the array.
      vehicles.append(outback)
     
      // Create another car
      var prius = Car()
      prius.brandName = "Toyota"
      prius.modelName = "Prius"
      prius.modelYear = 2002
      prius.hasSunroof = true
      prius.isConvertible = false
      prius.isHatchback = true
      prius.numberOfDoors = 4
      prius.powerSource = "hybrid engine"
     
      // Add it to the array.
      vehicles.append(prius)
     
      // Sort the array by the model year
      vehicles.sort { $0.modelYear < $1.modelYear }
    }

This simply adds a data setup method to construct your vehicle array. Each _Car_ is created and customized based on the values set on its properties.

In `viewDidLoad()` add the following after its `super.viewDidLoad()`:

The above method executes just after your view loads from the Storyboard. It calls the _setupVehicleArray()_ method you just created, and sets the title of the _VehicleListTableViewController_ to reflect its contents.

Build and run your application; you'll see something like the following:

![Car Build](http://cdn5.raywenderlich.com/wp-content/uploads/2014/09/Build-281x500.png)

> _[Car Build](http://cdn5.raywenderlich.com/wp-content/uploads/2014/09/Build.png)_

Your table view is populated with three entries of "Vehicle.Car". Vehicle is the name of the module (app, in this case) and Car is the name of the class.

The good news is that these objects are being recognized as _Car_ objects. The bad news is that what's being displayed isn't terribly useful. Take a look at what's set up in the `UITableViewDataSource` method `tableView(_:cellForRowAtIndexPath:)`:
    
    
    override func tableView(tableView: UITableView, cellForRowAtIndexPath indexPath: NSIndexPath) -> UITableViewCell {
      let cell = tableView.dequeueReusableCellWithIdentifier("Cell", forIndexPath: indexPath) as! UITableViewCell
     
      let vehicle = vehicles[indexPath.row]
      cell.textLabel?.text = "\(vehicle)"
      return cell
    }

Here, you're grabbing a _UITableViewCell_ object then getting the _Vehicle_ at the index in the `self.vehicles` array matching the `row` of the cell you're constructing. Next, you set that specific _Vehicle_'s string representation as the text for the cell's `textLabel`.

The default string produced method isn't very human-friendly. You'll want to define a method in _Vehicle_ that describes what each `Vehicle` object represents in a way that is easy for your users to understand.

Go to _Vehicle.swift_ and add the following property below your other properties:

Until now, you have been using _stored properties_ to keep track of attributes associated with your objects. This is an example of a _computed property_. This is a read-only property that isn't backed by a variable; instead, it runs the code inside braces and generates a fresh string every time.

Go back to _VehicleListTableViewController.swift_ and update `tableView(_:cellForRowAtIndexPath:)` to use this new property on `Vehicle` as follows:
    
    
    override func tableView(tableView: UITableView, cellForRowAtIndexPath indexPath: NSIndexPath) -> UITableViewCell {
      let cell = tableView.dequeueReusableCellWithIdentifier("Cell", forIndexPath: indexPath) as! UITableViewCell
     
      let vehicle = vehicles[indexPath.row] as Vehicle
      cell.textLabel?.text = vehicle.vehicleTitle
      return cell
    }

Build and run your application; it should look a little nicer now:

![Three Vehicles With Readable Titles](http://cdn5.raywenderlich.com/wp-content/uploads/2013/09/iOS-Simulator-Screen-shot-Jul-8-2013-10.14.08-PM-213x320.png)

> _[Three Vehicles With Readable Titles](http://www.raywenderlich.com/45940/intro-object-oriented-design-part-1/ios-simulator-screen-shot-jul-8-2013-10-14-08-pm)_

However, if you select a `Vehicle` from the list, all you'll see are the same elements visible in the storyboard, with none of the details from the `Vehicle` you selected:

![Before Data Hookup Detail](http://cdn4.raywenderlich.com/wp-content/uploads/2013/09/iOS-Simulator-Screen-shot-Sep-8-2013-5.21.51-PM-213x320.png)

> _[Before Data Hookup Detail](http://www.raywenderlich.com/45940/intro-object-oriented-design-part-1/ios-simulator-screen-shot-sep-8-2013-5-21-51-pm)_

What's up with that?

Open _VehicleDetailViewController.swift_; you'll see that while the UI was constructed in the Storyboard and all the `@IBOutlets` are already hooked up to save you some time fighting with AutoLayout, none of the data is hooked up.

### Hooking Your Data to Your View

To hook up the data, go to _VehicleDetailViewController.swift_ and fill in the method `configureView()` to take advantage of the vehicle set by the segue as follows:
    
    
    func configureView() {
      // Update the user interface for the detail item.
      if let vehicle = detailVehicle {
        title = vehicle.vehicleTitle
     
        var basicDetails = "Basic vehicle details:\n\n"
        basicDetails += "Brand name: \(vehicle.brandName)\n"
        basicDetails += "Model name: \(vehicle.modelName)\n"
        basicDetails += "Model year: \(vehicle.modelYear)\n"
        basicDetails += "Power source: \(vehicle.powerSource)\n"
        basicDetails += "# of wheels: \(vehicle.numberOfWheels)\n"
     
        detailDescriptionLabel?.text = basicDetails
      }
    }

Build and run your application; select a vehicle from the table view and you'll see that the detail view is now showing the correct title and details, as so:

![Basic vehicle details](http://cdn3.raywenderlich.com/wp-content/uploads/2013/09/iOS-Simulator-Screen-shot-Sep-8-2013-5.35.38-PM-213x320.png)

> _[Basic vehicle details](http://www.raywenderlich.com/45940/intro-object-oriented-design-part-1/ios-simulator-screen-shot-sep-8-2013-5-35-38-pm)_

### Model-View-Controller Encapsulation of Logic

iOS and many other modern programming languages have a design pattern known as _Model-View-Controller_ , or MVC for short.

The idea behind MVC is that views should only care about how they are presented, models should only care about their data, and controllers should work to marry the two without necessarily knowing too much about their internal structure.

The biggest benefit to the MVC pattern is making sure that if your data model changes, you only have to make changes once.

One of the biggest rookie mistakes that programmers make is putting far too much of the logic in their `UIViewController` classes. This ties views and `UIViewControllers` too closely to one particular type of model, making it harder to reuse views to display different kinds of details.

Why would you want to do implement the MVC pattern in your app? Well, imagine that you wanted to add more specific details about a car to `VehicleDetailViewController`. You could start by going back into `configureView()` and adding some information specifically about the car, as so:

But you'll notice that this does not work because the compiler doesn't know what the property `numberOfDoors` is. That property is associated with the `Car` subclass and not part of the `Vehicle` base class.

There are a couple of ways you can fix this.

One way is to have the view controller attempt to _downcast_ the `vehicle` to a `Car` type using the `as? Car` operation. If it succeeds, access the `Car` properties and display them.

Any time you catch yourself downcasting, ask yourself: "is my view controller trying to do too much?"

In this case, the answer is yes. You can take advantage of inheritance to use the same method to supply the string to be displayed for the appropriate details for each subclass. This way the view controllers doesn't need to concern itself with the details of specific subclasses.

### Creating Subclasses via Inheritance

First, go to _Vehicle.swift_ and add a new computed property to get a details string:
    
    
    var vehicleDetails: String {
      var details = "Basic vehicle details:\n\n"
      details += "Brand name: \(brandName)\n"
      details += "Model name: \(modelName)\n"
      details += "Model year: \(modelYear)\n"
      details += "Power source: \(powerSource)\n"
      details += "# of wheels: \(numberOfWheels)\n"
      return details
    }

The method is similar to what you added to _VehicleDetailViewController.swift_, except it returns the generated string rather than display it somewhere directly.

Now, you can use inheritance to take this basic vehicle string and add the specific details for the `Car` class. Open _Car.swift_ and add the override the property `vehicleDetails`:
    
    
    override var vehicleDetails: String {
      // Get basic details from superclass
      let basicDetails = super.vehicleDetails
     
      // Initialize mutable string
      var carDetailsBuilder = "\n\nCar-Specific Details:\n\n"
     
      // String helpers for booleans
      let yes = "Yes\n"
      let no = "No\n"
     
      // Add info about car-specific features.
      carDetailsBuilder += "Has sunroof: "
      carDetailsBuilder += hasSunroof ? yes : no
     
      carDetailsBuilder += "Is Hatchback: "
      carDetailsBuilder += isHatchback ? yes : no
     
      carDetailsBuilder += "Is Convertible: "
      carDetailsBuilder += isConvertible ? yes : no
     
      carDetailsBuilder += "Number of doors: \(numberOfDoors)"
     
      // Create the final string by combining basic and car-specific details.
      let carDetails = basicDetails + carDetailsBuilder
     
      return carDetails
    }

`Car`'s version of the method starts by calling the superclass's implementation to get the vehicle details. It then builds the car-specific details string into `carDetailsBuilder` and then combines the two at the very end.

Now go back to _VehicleDetailViewController.swift_ and replace `configureView()` with the much simpler implementation below to display this string that you've created:
    
    
    func configureView() {
      // Update the user interface for the detail item.
      if let vehicle = detailVehicle {
        title = vehicle.vehicleTitle
        detailDescriptionLabel?.text = vehicle.vehicleDetails
      }
    }

Build and run your application; select one of the cars, and you should now be able to see both general details and car-specific details as shown below:

![Basic and car-specific details](http://cdn4.raywenderlich.com/wp-content/uploads/2013/09/iOS-Simulator-Screen-shot-Aug-28-2013-8.43.53-PM-213x320.png)

> _[Basic and car-specific details](http://www.raywenderlich.com/45940/intro-object-oriented-design-part-1/ios-simulator-screen-shot-aug-28-2013-8-43-53-pm)_

Your `VehicleDetailViewController` class now allows the `Vehicle` and `Car` classes to determine the data to be displayed. The only thing `VehicleDetailsViewController` is doing is connecting that information up with the view!

The real power in this is evident when you create further subclasses of _Vehicle_. Start with a fairly simple one for a motorcycle.

Go to File\New\File… and select iOS\Source\Swift File. Name the file _Motorcycle_. Inside _Motorcycle.swift_, create a new subclass of `Vehicle` called `Motorcycle` as shown below:

Since motorcycles can have either a deep booming engine noise, or a high-pitched whine of an engine noise, each `Motorcycle` object you create should specify which type of noise it makes. Add the following property and method to your new class:
    
    
    var engineNoise = ""
     
    override init() {
      super.init()
      numberOfWheels = 2
      powerSource = "gas engine"
    }

Since all motorcycles have two wheels and are gas-powered (for the sake of this example, anything that's electric-powered would be considered a scooter, not a motorcycle), you can set up the number of wheels and power source when the object is instantiated.

Next, add the following methods to override the superclass methods.
    
    
    // MARK: - Superclass Overrides
    override func goForward() -> String {
      return String(format: "%@ Open throttle.", changeGears("Forward"))
    }
     
    override func goBackward() -> String {
      return String(format: "%@ Walk %@ backwards using feet.", changeGears("Neutral"), modelName)
    }
     
    override func stopMoving() -> String {
      return "Squeeze brakes"
    }
     
    override func makeNoise() -> String {
      return self.engineNoise
    }

Finally, override the `vehicleDetails` property in order to add the `Motorcycle`-specific details to the `vehicleDetails` as shown below:
    
    
    override var vehicleDetails: String {
      //Get basic details from superclass
      let basicDetails = super.vehicleDetails
     
      //Initialize mutable string
      var motorcycleDetailsBuilder = "\n\nMotorcycle-Specific Details:\n\n"
     
      //Add info about motorcycle-specific features.
      motorcycleDetailsBuilder += "Engine Noise: \(engineNoise)"
     
      let motorcycleDetails = basicDetails + motorcycleDetailsBuilder
     
      return motorcycleDetails
    }

Now, it's time to create some instances of `Motorcycle`.

Open _VehicleListTableViewController.swift_, find `setupVehicleArray()` and add the following code below the _Cars_ you've already added but above where you sort the array:
    
    
    // Create a motorcycle
    var harley = Motorcycle()
    harley.brandName = "Harley-Davidson"
    harley.modelName = "Softail"
    harley.modelYear = 1979
    harley.engineNoise = "Vrrrrrrrroooooooooom!"
     
    // Add it to the array.
    vehicles.append(harley)
     
    // Create another motorcycle
    var kawasaki = Motorcycle()
    kawasaki.brandName = "Kawasaki"
    kawasaki.modelName = "Ninja"
    kawasaki.modelYear = 2005
    kawasaki.engineNoise = "Neeeeeeeeeeeeeeeeow!"
     
    // Add it to the array
    self.vehicles.append(kawasaki)

The above code simply instantiates two Motorcycle objects and adds them to the vehicles array.

Build and run your application; you'll see the two `Motorcycle` objects you added in the list:

![Added Motorcycles](http://cdn1.raywenderlich.com/wp-content/uploads/2013/09/iOS-Simulator-Screen-shot-Aug-28-2013-9.05.00-PM-213x320.png)

> _[Added Motorcycles](http://www.raywenderlich.com/45940/intro-object-oriented-design-part-1/ios-simulator-screen-shot-aug-28-2013-9-05-00-pm)_

Tap on one of them, and you'll be taken to the details for that `Motorcycle`, as shown below:

![Motorcycle Details](http://cdn2.raywenderlich.com/wp-content/uploads/2013/09/iOS-Simulator-Screen-shot-Aug-28-2013-9.05.04-PM-213x320.png)

> _[Motorcycle Details](http://www.raywenderlich.com/45940/intro-object-oriented-design-part-1/ios-simulator-screen-shot-aug-28-2013-9-05-04-pm)_

Whether it's a car or a motorcycle (or even a plain old vehicle), you can call `vehicleDetails` and get the relevant details.

By using proper separation between the model, the view, and the view controller and inheritance, you're now able to display data for several subclasses of the same superclass without having to write tons of extra code to handle different subclass types. Less code written == happier developers! :]

### Housing Logic in the Model Class

You can also use this approach to keep some of the more complicated logic encapsulated within the model class. Think about a `Truck` object: many different types of vehicles are referred to as a "truck", ranging from pickup trucks to tractor-trailers. Your truck class will have a little bit of logic to change the truck's behavior based on the number of cubic feet of cargo it can haul.

Go to File\New\File… and select iOS\Source\Swift File. Name the file _Truck_. Inside _Truck.swift_, create a new subclass of `Vehicle` called `Truck` as you did for _Car_ and _Motorcycle_:

Add the following integer property to _Truck.swift_ to hold the truck's capacity data:

Since there are so many different types of trucks, you don't need to create an initializer method that provides any of those details automatically. You can simply override the superclass methods which would be the same no matter the size of the truck.
    
    
    //MARK: - Superclass overrides
    override func goForward() -> String {
      return String(format:"%@ Depress gas pedal.", changeGears("Drive"))
    }
     
    override func stopMoving() -> String {
      return String(format:"Depress brake pedal. %@", changeGears("Park"))
    }

Next, you'll want to override a couple of methods so that the string returned is dependent on the amount of cargo the truck can haul. A big truck needs to sound a backup alarm, so you can create a private method.

Add the following private method code to your `Truck` class:

Then back in the superclass overrides section, you can use that `soundBackupAlarm()` method to create a `goBackward()` method that sounds the alarm for big trucks:
    
    
    override func goBackward() -> String {
      if cargoCapacityCubicFeet > 100 {
        // Sound a backup alarm first
        return String(format:"Wait for \"%@\", then %@", soundBackupAlarm(), changeGears("Reverse"))
      } else {
        return String(format:"%@ Depress gas pedal.", changeGears("Reverse"))
      }
    }

Trucks also have very different horns; a pickup truck, for instance, would have a horn similar to that of a car, while progressively larger trucks have progressively louder horns. You can handle this with a switch statement in the `makeNoise()` method.

Add _makeNoise()_ as follows:
    
    
    override func makeNoise() -> String {
      switch numberOfWheels {
      case Int.min...4:
        return "Beep beep!"
      case 5...8:
        return "Honk!"
      default:
        return "HOOOOOOOOONK!"
      }
    }

Finally, you can override the `vehicleDetails` property in order to get the appropriate details for your `Truck` object. Add the method as follows:
    
    
    override var vehicleDetails: String {
      // Get basic details from superclass
      let basicDetails = super.vehicleDetails
     
      // Initialize mutable string
      var truckDetailsBuilder = "\n\nTruck-Specific Details:\n\n"
     
      // Add info about truck-specific features.
      truckDetailsBuilder += "Cargo Capacity: \(cargoCapacityCubicFeet) cubic feet"
     
      // Create the final string by combining basic and truck-specific details.
      let truckDetails = basicDetails + truckDetailsBuilder
     
      return truckDetails
    }

Now that you've got your `Truck` object set up, you can create a few instances of it. Head back to _VehicleListTableViewController.swift_, find the `setupVehicleArray()` method and add the following code right above where you sort the array:
    
    
    // Create a truck
    var silverado = Truck()
    silverado.brandName = "Chevrolet"
    silverado.modelName = "Silverado"
    silverado.modelYear = 2011
    silverado.numberOfWheels = 4
    silverado.cargoCapacityCubicFeet = 53
    silverado.powerSource = "gas engine"
     
    // Add it to the array
    vehicles.append(silverado)
     
    // Create another truck
    var eighteenWheeler = Truck()
    eighteenWheeler.brandName = "Peterbilt"
    eighteenWheeler.modelName = "579"
    eighteenWheeler.modelYear = 2013
    eighteenWheeler.numberOfWheels = 18
    eighteenWheeler.cargoCapacityCubicFeet = 408
    eighteenWheeler.powerSource = "diesel engine"
     
    // Add it to the array
    vehicles.append(eighteenWheeler)

This will create a couple of `Truck` objects with the truck-specific properties to join the cars and motorcycles in the array.

Build and run you application; select one of the `Trucks` to verify that you can now see the appropriate `Truck`-specific details, as demonstrated below:

![Truck-specific Details](http://cdn1.raywenderlich.com/wp-content/uploads/2013/09/iOS-Simulator-Screen-shot-Sep-4-2013-1.54.57-PM-213x320.png)

> _[Truck-specific Details](http://www.raywenderlich.com/45940/intro-object-oriented-design-part-1/ios-simulator-screen-shot-sep-4-2013-1-54-57-pm)_

That looks pretty great! The truck details are coming through thanks to the `vehicleDetails` computed property, inheritance, and overridden implementations.

## Where To Go From Here?

You can [download a copy](http://cdn5.raywenderlich.com/wp-content/uploads/2014/11/SwiftVehiclesPart1Final3.zip) of the project up to this point.

You've set up a base `Vehicle` class with `Car`, `Motorcycle`, and `Truck` subclasses, all listed in the same table view. However, there's no way to verify that all of your truck's size-specific handling is working correctly.

[Part 2 of this tutorial](http://www.raywenderlich.com/?p=81953) will fill out the rest of the app to display more vehicle details. Along the way, you'll learn about polymorphism, proper initialization, and a couple of additional major design patterns for Object-Oriented Programming.

Got questions? Ask in the comments below!
