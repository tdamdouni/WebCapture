# Intro to Object-Oriented Design in Swift: Part 2/2

_Captured: 2015-11-25 at 20:46 from [www.raywenderlich.com](http://www.raywenderlich.com/81953/intro-object-oriented-design-swift-part-2)_

If you're new here, you may want to subscribe to my [RSS feed](http://www.raywenderlich.com/feed/) or follow me on [Twitter](http://twitter.com/rwenderlich). Thanks for visiting!

![Object-oriented design](http://cdn3.raywenderlich.com/wp-content/uploads/2013/11/oop.jpg)

> _Wheels, engines, movement…alike, yet different._

_Update 4/11/2015_: Updated for Xcode 6.3 / Swift 1.2

_Update note:_ This tutorial was updated for iOS 8 and Swift by Ray Fix. [Original post](http://www.raywenderlich.com/?p=45942) by Tutorial Team member [Ellen Shapiro](http://www.raywenderlich.com/u/designatednerd).

In [Part 1 of this tutorial](http://www.raywenderlich.com/?p=81952), you learned the basics of object-oriented design: objects, inheritance, and the model-view-controller pattern. You created the beginnings of a simple application called _Vehicles_ to help you gain a better understanding of these concepts.

Here in the second part, you're going to learn about polymorphism and initialization. Along the way, you will learn about a few of Object-Oriented programming patterns including the Decorator, the Adapter, and the Singleton.

If you completed the previous tutorial, great! You can pick up where you left off with your previous project. However, if you want to jump right into things, you can [download the completed project from Part 1](http://cdn5.raywenderlich.com/wp-content/uploads/2014/11/SwiftVehiclesPart1Final3.zip) to get started.

## Polymorphism

The general definition of Polymorphism comes from its Greek roots - "Poly" means many, and "Morph" means forms.

The computer-science specific definition, pulled from the [Free Online Dictionary of Computing](http://foldoc.org/polymorphism), is:

_A variable that may refer to objects whose class is not known at compile time and which respond at run time according to the actual class of the object to which they refer._

You have already seen polymorphism in action in Part 1. In `VehicleDetailViewController`'s `configureView()` method, you used the computed property `vehicleDetails` that was overridden in each subclass. You know that any kind of vehicle will have that `vehicleDetails` property, but you'll get a different value depending on whether the object is a `Car`, `Motorocycle` or `Truck`.

There are several patterns related to polymorphism that can be used within Swift, but two key ones you'll see often are the _Decorator_ and _Adapter_ patterns. These are implemented using the language keywords `extension` and `protocol` respectively.

### The Decorator Pattern

From Apple's Cocoa Fundamentals guide's section on [Cocoa Design Patterns](https://developer.apple.com/library/ios/documentation/cocoa/Conceptual/CocoaFundamentals/CocoaDesignPatterns/CocoaDesignPatterns.html):

_The Decorator design pattern attaches additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality. As does subclassing, adaptation of the Decorator pattern allows you to incorporate new behavior without modifying existing code. Decorators wrap an object of the class whose behavior they extend._

The primary example of the Decorator pattern in Swift is when you create an _extension_. In Objective-C, there is a similar mechanism with class categories.

Extensions allow you to add additional methods to classes and structs without having to subclass or alter the original source code. For example, they can be used to add functionality to the stock UIKit components such as additional helper methods on UIView or custom color constructors on UIColor.

The difference between an extension and a subclass is pretty simple: You can add new methods but not new properties with an extension. If you want to add a new property, you'll probably need to create a subclass and use the power of inheritance to create your additional properties and methods.

But what if you don't need to add new properties? What if you just want to create a simple way to encapsulate something you have to do repeatedly with a particular UIKit object? In this case, an extension is a possible solution.

To try this out, you're going to add a convenience method to `UIAlertController` to do away with performing the setup dance required for simple alerts over and over again in your code.

### Implementing the Decorator Pattern

You could put the definition of your `UIAlertController` extension in any file and it would be visible to the entire app. However, to keep things neat and to facilitate it being used in other future projects, create it in a separate file. Go to _File\New\File…_ and select _iOS\Source\Swift File_. Then name the file _UIAlertController+Convenience_. The format _[Component]+[Extension Name]_ borrows a page from Objective-C category file naming conventions. While this is just a convention, it helps communicate your intent. In this case, you are adding some convenience methods to `UIAlertController`.

Creating a method within an `extension` is very similar to creating a method on a normal class. Open _UIAlertController+Convenience.swift_ and add the following:
    
    
    import UIKit
     
    extension UIAlertController {
      class func alertControllerWithTitle(title:String, message:String) -> UIAlertController {
        let controller = UIAlertController(title: title, message: message, preferredStyle: .Alert)
        controller.addAction(UIAlertAction(title: "OK", style: .Default, handler: nil))
        return controller
      }  
    }

Rather than defining a new `class`, you create an `extension` on the existing `UIAlertController` class.

You're not doing anything revolutionary here -- just packaging up and returning a `UIAlertController` that has a single button dismiss action.

Bonus: In addition to using the _Decorator_ pattern by adding functionality to `UIAlertController` you are also implementing what is called the _Factory_ pattern. The Factory pattern returns an initialized instance configured in a particular way. You might say this is a Decorated Factory. :]

Time to use your new extension. Open _VehicleDetailViewController.swift_. Towards the bottom of the file, you'll find several methods marked `@IBAction` that are empty. Update `goForward()`, `goBackward()`, `stopMoving()` and `makeNoise()` as shown below to use your new extension:
    
    
    @IBAction func goForward(sender: AnyObject) {
      if let vehicle = detailVehicle {
        let controller = UIAlertController.alertControllerWithTitle("Go Forward", message: vehicle.goForward())
        presentViewController(controller, animated: true) {}
      }
    }
     
    @IBAction func goBackward(sender: AnyObject) {
      if let vehicle = detailVehicle {
        let controller = UIAlertController.alertControllerWithTitle("Go Backward", message: vehicle.goBackward())
        presentViewController(controller, animated: true) {}
      }
    }
     
    @IBAction func stopMoving(sender: AnyObject) {
      if let vehicle = detailVehicle {
        let controller = UIAlertController.alertControllerWithTitle("Stop Moving", message: vehicle.stopMoving())
        presentViewController(controller, animated: true) {}
      }
    }
     
    @IBAction func makeNoise(sender: AnyObject) {
      if let vehicle = detailVehicle {
        let controller = UIAlertController.alertControllerWithTitle("Make Some Noise!", message: vehicle.makeNoise())
        presentViewController(controller, animated: true) {}
      }
    }

The `if let` statement makes sure that `vehicle` exists, and if it does, creates an alert controller using your extension and presents it.

Build and run your application; after selecting a vehicle, press any button except the "Turn…" button, and you'll see the appropriate message for each instance of a `Vehicle`. For example, if you press the "Make Some Noise!" button for various Vehicles, you'll see the following:

![Make some noise!](http://cdn4.raywenderlich.com/wp-content/uploads/2013/09/making-noise-480x239.jpg)

> _[Make some noise!](http://www.raywenderlich.com/45942/intro-object-oriented-design-part-2/making-noise)_

To implement the `turn()` method, you'll need to pass some information from the `UIAlertController` back to your view controller. You can do this with Swift closures. You can think of a closure as an unnamed function similar to a block in Objective-C. First, go back to _UIAlertController+Convenience.swift_ and add the following method:
    
    
    class func alertControllerWithNumberInput(#title:String, message:String, buttonTitle:String, handler:(Int?)->Void) -> UIAlertController {
      let controller = UIAlertController(title: title, message: message, preferredStyle: .Alert)
     
      controller.addTextFieldWithConfigurationHandler { $0.keyboardType = .NumberPad }
     
      controller.addAction(UIAlertAction(title: "Cancel", style: .Cancel, handler: nil))
     
      controller.addAction(UIAlertAction(title: buttonTitle, style: .Default) { action in
        let textFields = controller.textFields as? [UITextField]
        let value = textFields?[0].text.toInt()
        handler(value)
        } )
     
      return controller
    }

This method configures a `UIAlertController` with a text field that takes numeric input from the keypad and returns it. When the button is pressed, it attempts to parse the text into an `Int`. The value is an optional type because parsing might fail. This value is passed to a handler function supplied as an argument to the function.

To use the extension, open _VehicleDetailsViewController.swift_ file and add the implementation for `turn()`
    
    
    @IBAction func turn(sender: AnyObject) {
      if let vehicle = detailVehicle {
        let controller = UIAlertController.alertControllerWithNumberInput(title: "Turn", message: "Enter number of degrees to turn:", buttonTitle: "Go!") {
          integerValue in
          if let value = integerValue {
            let controller = UIAlertController.alertControllerWithTitle("Turn", message: vehicle.turn(value))
            self.presentViewController(controller, animated: true, completion: nil)
          }
        }
        presentViewController(controller, animated: true) {}
      }
    }

This sets a controller with numeric input is created via your extension. Your handler checks if you have a valid value and then throws up another alert view with the turn message.

Build and run your project; select a Vehicle from the list, tap the Turn button and enter a number of degrees to turn, like so:

![Turn 90 degrees](http://cdn5.raywenderlich.com/wp-content/uploads/2013/09/iOS-Simulator-Screen-shot-Sep-4-2013-4.29.34-PM-213x320.png)

> _[Turn 90 degrees](http://www.raywenderlich.com/45942/intro-object-oriented-design-part-2/ios-simulator-screen-shot-sep-4-2013-4-29-34-pm)_

If you hit _Cancel_, nothing will happen. However, if you hit _Go!_, the first `UIAlertController` disappears and the following `UIAlertController` will appear:

![Turn complete!](http://cdn5.raywenderlich.com/wp-content/uploads/2013/09/iOS-Simulator-Screen-shot-Sep-4-2013-4.29.38-PM-213x320.png)

> _[Turn complete!](http://www.raywenderlich.com/45942/intro-object-oriented-design-part-2/ios-simulator-screen-shot-sep-4-2013-4-29-38-pm)_

Your application is now functionally complete. However, what if you want to make your code a little more elegant so it's easier to maintain and add to it later? It's time to refactor how your objects are initialized and learn about some more object-oriented design patterns to make your coding life easier!

## Proper Initialization

One of the big safety features of Swift is its ability to do proper initialization. Through a process called two-phase initialization, the Swift complier guarantees that you never access uninitialized memory.

Swift uses two phase initialization that works roughly like the following. First, initialization of your Derived class begins.

_Phase 1_

  1. The stored properties of the most derived class are set either at the point where the stored property is declared or at the beginning of the `init()` method. In Phase 1, properties declared with `let` must be set exactly once.
  2. `super.init()` is called. The same rule above applies. That is, the super class also sets all of it's stored properties _that it introduces_ and calls up the chain.
  3. The process continues until the top of the inheritance hierarchy is finally reached.

_Phase 2_

  1. The highest level `init()` method returns starting the chain back down towards the most derived class
  2. As each derived class returns, it can overwrite stored properties defined in the super classes above it.
  3. This process continues back down to the most derived class.
  4. Finally, any convenience initializers in the chain have the option to customize the instance and to work with self. More on convenience initializers in the next section. 

You can find a longer explanation of initialization in the [Swift Programming Language Book](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Initialization.html). While the rules are a bit subtle, they are simple to follow and avoid corner cases where properties would not be initialized or confusingly over-written.

### Designated vs Convenience Initializers

Every class must have at least one designated initializer that is responsible for initializing everything in that class. If you set all of the stored properties (or they have their own default initializers) the compiler will provide you with a default designated initializer automatically.

It is typical for a class to have only one designated initializer. Sometimes you can declare additional convenience initializers that are marked with the keyword `convenience`. While this tutorial doesn't show any `convenience` initializers in action, they can be convenient (as the name suggests) in shortening common initialization calls.

Convenience initializers may only call the designated initializer or other convenience initializers of the same class. Ultimately they must eventually lead to the designated initializers of the same class. This simple rule ensures instances are in a usable state by the end of the initialization process.

Unlike convenience initializers, designated initializers of a derived class must only call the designated of the superclass.

### Back to the Code

When you created `Vehicle`, `Car`, `Motorcycle` and `Truck` in Part 1 you used a bunch of placeholder values to set the properties. After creating `Vehicle` instances, you immediately set the values to something more reasonable. This, however, is an error prone process. It is easy to forget setting one of the values resulting in a bug. It would be better if you could set the values explicitly right at initialization so the compiler can check your work.

In this section you'll set the values right in the initializer. This will make your classes easy to use correctly and conversely, difficult to use incorrectly.

Because you specified all of the initial values and didn't write a default initializer, the compiler created one for you behind the scenes. When you write your own, the compiler-created one goes away. So, along with creating a new member-wise initializer, add a default initializer to prevent breakage while you are refactoring. Open _Vehicle.swift_ and add these below your computed properties:
    
    
    // Mark: - Initialization Methods
     
    init() {}
     
    init(brandName:String, modelName:String, modelYear:Int, powerSource:String, numberOfWheels:Int) {
      self.brandName = brandName
      self.modelName = modelName
      self.modelYear = modelYear
      self.powerSource = powerSource
      self.numberOfWheels = numberOfWheels
    }

The blank initializer is just temporary to keep the compiler from complaining. You will remove this later.

The new initializer with arguments simply sets each property with the value coming in.

Now open _Car.swift_. Change the declaration of the four stored properties to remove their default values. They should look like the following:

Next, replace the current overridden `init()` with the following:
    
    
    init(brandName: String, modelName: String, modelYear: Int, powerSource: String,
      isConvertible: Bool, isHatchback: Bool, hasSunroof: Bool, numberOfDoors: Int) {
     
        self.isConvertible = isConvertible
        self.isHatchback = isHatchback
        self.hasSunroof = hasSunroof
        self.numberOfDoors = numberOfDoors
     
        super.init(brandName: brandName, modelName: modelName, modelYear: modelYear,
          powerSource: powerSource, numberOfWheels: 4)
    }

This initializes a `Car` object in one call. In the initializer you first initialize the properties that the `Car` class introduces. Then you call the superclass's designated initializer. By declaring your stored properties with the `let` keyword, they are now immutable so they can never change after they are initialized. Using `let` is a good idea because it more appropriately models these properties. The number of doors on a car, for example, does not change from minute to minute.

Now repeat the process for `Motorcycle`. Open _Motorcycle.swift_ and replace the stored property and overridden `init()` with the following:
    
    
    let engineNoise: String
     
    init(brandName: String, modelName: String, modelYear: Int, engineNoise: String) {
      self.engineNoise = engineNoise
      super.init(brandName: brandName, modelName: modelName, modelYear: modelYear,
        powerSource: "gas engine", numberOfWheels: 2)
    }

And the some thing for `Truck`. Open _Truck.swift_ and replace the stored property and `init` with the following:
    
    
    let cargoCapacityCubicFeet: Int
     
    init(brandName: String, modelName: String, modelYear: Int, powerSource: String, numberOfWheels: Int, cargoCapacityInCubicFeet:Int) {
      self.cargoCapacityCubicFeet = cargoCapacityInCubicFeet
      super.init(brandName: brandName, modelName: modelName, modelYear: modelYear,
        powerSource: powerSource, numberOfWheels: numberOfWheels)
    }

Finally you are ready to remove the temporary `init()` with no parameters in the Vehicle class and change all of the properties to immutable values with no dummy placeholders. Go to _Vehicle.swift_ and change the stored properties to the following:

Also, remove the temporary `init() {}` you had.

The test code that you put in AppDelegate in Part 1 will no longer compile because it used the default initializer `Vehicle()` that no longer exists. Open _AppDelegate.swift_ and remove it. `application(_:didFinishLaunchingWithOptions:)` should simply return true:

Now you can use your new initializers to create all the different Vehicle objects. Open _VehicleListViewController.swift_ and replace the current method body of `setupVehicle()` with the following:
    
    
    // Clear the array. (Start from scratch.)
    vehicles.removeAll(keepCapacity: true)
     
    // Create a car.
    var mustang = Car(brandName: "Ford", modelName: "Mustang", modelYear: 1968, powerSource: "gas engine",
      isConvertible: true, isHatchback: false, hasSunroof: false, numberOfDoors: 2)
     
    // Add it to the array
    vehicles.append(mustang)
     
    // Create another car.
    var outback = Car(brandName: "Subaru", modelName: "Outback", modelYear: 1999, powerSource: "gas engine",
      isConvertible: false, isHatchback: true, hasSunroof: false, numberOfDoors: 5)
     
    // Add it to the array.
    vehicles.append(outback)
     
    // Create another car
    var prius = Car(brandName: "Toyota", modelName: "Prius", modelYear: 2002, powerSource: "hybrid engine",
      isConvertible: false, isHatchback: true, hasSunroof: true, numberOfDoors: 4)
     
    // Add it to the array.
    vehicles.append(prius)
     
    // Create a motorcycle
    var harley = Motorcycle(brandName: "Harley-Davidson", modelName: "Softail", modelYear: 1979,
      engineNoise: "Vrrrrrrrroooooooooom!")
     
    // Add it to the array.
    vehicles.append(harley)
     
    // Create another motorcycle
    var kawasaki = Motorcycle(brandName: "Kawasaki", modelName: "Ninja", modelYear: 2005,
      engineNoise: "Neeeeeeeeeeeeeeeeow!")
     
    // Add it to the array
    self.vehicles.append(kawasaki)
     
    // Create a truck
    var silverado = Truck(brandName: "Chevrolet", modelName: "Silverado", modelYear: 2011,
      powerSource: "gas engine", numberOfWheels: 4, cargoCapacityInCubicFeet: 53)
     
    // Add it to the array
    vehicles.append(silverado)
     
    // Create another truck
    var eighteenWheeler = Truck(brandName: "Peterbilt", modelName: "579", modelYear: 2013,
      powerSource: "diesel engine", numberOfWheels: 18, cargoCapacityInCubicFeet: 408)
     
    // Add it to the array
    vehicles.append(eighteenWheeler)
     
    // Sort the array by the model year
    vehicles.sort { $0.modelYear < $1.modelYear }

Build and run the application. Everything should look as it did before, and there should be no difference in behavior.

![VehicleList](http://cdn3.raywenderlich.com/wp-content/uploads/2014/09/VehicleList-281x500.png)

Although things behave the same way, your code is now much more robust and much less susceptible errors when creating new objects. With proper initialization in the Vehicle class hierarchy, you can be sure your objects and properties start off in a known good state.

## Additional Object-Oriented Patterns

There are many more Object-Oriented design patterns that you can use to improve your code. Let's look at two more: the _Adapter_ and the _Singleton_.

Both of these patterns are used extensively in iOS development, and understanding what they do under the hood will help you understand the design of the code you'll encounter as an iOS developer.

### The Adapter Pattern (Protocols)

Again from the [Cocoa Fundamentals Guide](https://developer.apple.com/library/ios/documentation/cocoa/Conceptual/CocoaFundamentals/CocoaDesignPatterns/CocoaDesignPatterns.html):

_The Adapter design pattern converts the interface of a class into another interface that clients expect. Adapter lets classes work together that couldn't otherwise because of incompatible interfaces. It decouples the client from the class of the targeted object._

Protocols are the primary example of the Adapter pattern in Swift. This designates a number of methods and properties that can be implemented by any class. They're most often used for `DataSource` and `Delegate` methods, but can also be used to help two unrelated classes communicate with each other.

The advantage of this pattern is that as long as a class declares that it conforms to the protocol, it really doesn't matter whether it's a model, a view, or a controller. It simply needs to know what is happening in the other class, and will implement any required methods or properties needed to know about this.

To make it easier to `println()` a Vehicle object, you will create what is called a _protocol extension_. This is one example of the adapter pattern in action. Open up _Vehicle.swift_ and at the end of the file add the following stand-alone code outside of the `Vehicle` definition:
    
    
    // MARK: An extension to make Vehicle printable
     
    extension Vehicle : Printable {
      var description:String {
        return vehicleTitle + "\n" + vehicleDetails
      }
    }

This declares the `Vehicle` class as conforming to the `Printable` protocol defined by the Swift Standard Library. `Printable` only requires that your class return a string property `description`. With this addition you can now `println(vehicle)`. In other words, you have _adapted_ `Vehicle` to be used as a String. To test it out, open _VehicleDetailsViewController.swift_ and add `viewWillAppear()` just below `viewDidLoad()`:
    
    
    override func viewWillAppear(animated: Bool) {
      super.viewWillAppear(animated)
      if let vehicle = detailVehicle {
        println(vehicle)
      }
    }

Build and run your application. Notice that whenever you tap on a vehicle, the vehicle information is printed to the Xcode console:

![VehicleDebugger](http://cdn4.raywenderlich.com/wp-content/uploads/2014/09/VehicleDebugger-439x320.png)

Before conforming to the `Printable` protocol, all `println()` could do was print the module and class name: "Vehicle.Car".

Bonus: Notice that Swift lets you conform to a protocol using an extension. This is called a _Protocol Extension_. It is a nice way to organizer your code. Here too, you are applying two patterns simultaneously again. The Adapter (via protocol conformance) and the Decorator (via extension).

### The Singleton Pattern

One very specific, very useful initialization pattern is the _Singleton_. This ensures that a particular instance of a class is only initialized once.

This is great for items that need to only have a single instance -- for instance, the _UIApplication_ singleton `sharedApplication` -- or for those classes that are expensive to initialize, or which store small amounts of data which need to be accessed and updated throughout your app.

In the case of your Vehicles app, you can see there's one piece of data that might need to be accessed and updated all over the place: your list of Vehicles. The current list also violates MVC rules by letting _VehicleListTableViewController_ manage its creation and existence. By moving the list of vehicles into its own singleton class, you gain a lot of flexibility for the future.

Go to _File\New\File…_ and select _iOS\Source\Swift File_ and name the file _VehicleList_. Open the file and create the singleton:
    
    
    class VehicleList {
      let vehicles: [Vehicle]
     
      static var sharedInstance = VehicleList()
     
      private init() {
        vehicles = []
      }
    }

The class `VehicleList` has property variable called `sharedInstance` which is declared `static` so you don't need an instance to get it. By making the `init()` private, you force clients to not make their own and use the shared instance.

Right now, you are returning an immutable empty vehicles list that is not so useful. To fix that, replace the ` private init()` that creates the list.
    
    
      private init() {
        // Create a car.
        let mustang = Car(brandName: "Ford", modelName: "Mustang", modelYear: 1968, powerSource: "gas engine", isConvertible: true, isHatchback: false, hasSunroof: false, numberOfDoors: 2)
     
        // Create another car.
        let outback = Car(brandName: "Subaru", modelName: "Outback", modelYear: 1999, powerSource: "gas engine", isConvertible: false, isHatchback: true, hasSunroof: false, numberOfDoors: 5)
     
        // Create another car.
        let prius = Car(brandName: "Toyota", modelName: "Prius", modelYear: 2002, powerSource: "hybrid engine", isConvertible: false, isHatchback: true, hasSunroof: true, numberOfDoors: 4)
     
        // Create a motorcycle.
        let harley = Motorcycle(brandName: "Harley-Davidson", modelName: "Softail", modelYear: 1979, engineNoise: "Vrrrrrrrroooooooooom!")
     
        // Create another motorcycle.
        let kawasaki = Motorcycle(brandName: "Kawasaki", modelName: "Ninja", modelYear: 2005, engineNoise: "Neeeeeeeeeeeeeeeeow!")
     
        // Create a truck.
        let silverado = Truck(brandName: "Chevrolet", modelName: "Silverado", modelYear: 2011, powerSource: "gas engine", numberOfWheels: 4, cargoCapacityInCubicFeet: 53)
     
        // Create another truck.
        let eighteenWheeler = Truck(brandName: "Peterbilt", modelName: "579", modelYear: 2013, powerSource: "diesel engine", numberOfWheels: 18, cargoCapacityInCubicFeet: 408)
     
        // Sort the array by the model year
        let v = [mustang, outback, prius, harley, kawasaki, silverado, eighteenWheeler]
     
        vehicles = v.sorted { $0.modelYear < $1.modelYear }
      }

Now anywhere you reference `VehicleList.sharedInstance.vehicles` in your app, the list will be initialized the first time, and simply returned on subsequent references. Under the hood, Swift uses the lib dispatch to ensure that initialization occurs exactly once, even if multiple threads access it asynchronously.

Now go back to _VehicleListTableViewController.swift_ and remove the `vehicles` property as well as the entire `setupVehiclesArray()` method.

Modify your `viewDidLoad()` method by removing the call to `setupVehicleArray()` since you just removed the method.

You'll notice that Xcode shows you have three errors, since there are three places where you used the vehicles property to feed the _UITableViewDataSource_ and segue handling methods. You'll need to update these to use your new singleton instead.

Find the three spots where Xcode indicates an error and update the code to use the _VehicleList_ singleton's array of `vehicles` instead, as shown below:
    
    
    override func prepareForSegue(segue: UIStoryboardSegue, sender: AnyObject?) {
      if segue.identifier == "showDetail" {
        if let indexPath = self.tableView.indexPathForSelectedRow() {
          let vehicle = VehicleList.sharedInstance.vehicles[indexPath.row]
          (segue.destinationViewController as! VehicleDetailViewController).detailVehicle = vehicle
        }
      }
    } 
     
    override func tableView(tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
      return VehicleList.sharedInstance.vehicles.count
    }
     
    override func tableView(tableView: UITableView, cellForRowAtIndexPath indexPath: NSIndexPath) -> UITableViewCell {
      let cell = tableView.dequeueReusableCellWithIdentifier("Cell", forIndexPath: indexPath) as! UITableViewCell
     
      let vehicle = VehicleList.sharedInstance.vehicles[indexPath.row]
      cell.textLabel?.text = vehicle.vehicleTitle
      return cell
    }

Build and run your application; you'll see the same list as you did before, but you can sleep better knowing that the code behind the app is clean, concise, and easily extensible.

With all the changes above, you'll be able to easily add new _Vehicles_ to this list in the future. For instance, if you were to add a new _UIViewController_ that allows the user to add their own _Vehicle_, you'd only need to add it to the singleton array.

There's one tricky thing to watch out for with singletons: they will stay alive for the entire duration of your app's lifecycle, therefore you don't want to load them down with too much data. They can be great for lightweight data storage or to make objects accessible throughout your application.

If you're storing a lot of data in your app, you'll want to look at something more robust like _Core Data_ to handle the data storage and retrieval of your objects.

Finally, keep in mind that singletons, if overused, can lead to hard to reuse code. This is because they couple modules tightly together in the same way that global variables do. This goes to show that while patterns can be very useful in some contexts, they are not a silver bullet and can sometimes be misused.

## Where To Go From Here?

In one single app, you've created a clean, object-oriented application using basic objects, inheritance, MVC design, polymorphism, as well as singleton and factory methods. You can review the source code of the [finished project](http://cdn3.raywenderlich.com/wp-content/uploads/2014/11/SwiftVehiclesPart2Final2.zip).

Apple describes how to adopt a few common Cocoa design patterns in [ Adopting Cocoa Design Patterns](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/BuildingCocoaApps/AdoptingCocoaDesignPatterns.html).

For more sample code, there's a work-in-progress [Design Patterns in Swift Github project](https://github.com/ochococo/Design-Patterns-In-Swift) trying to catalog how many common software design patterns can be implemented in Swift. Check it out and see if you can come up with better implementations yourself!

If you've got questions, ask away in the comments below!
