# Swift Tutorial: Introducing Structures

_Captured: 2015-11-25 at 20:51 from [www.raywenderlich.com](http://www.raywenderlich.com/116714/swift-tutorial-introducing-structures)_

_Note from Ray:_ This is an abridged version of a chapter from the [Swift Apprentice](http://www.raywenderlich.com/store), to give you a sneak peek of what's inside the book, released as part of the [iOS 9 Feast](http://www.raywenderlich.com/113226/introducing-the-ios-9-feast). We hope you enjoy!

![A Swift 2 tutorial for the iOS 9 Feast!](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/iOS9_feast_Swift2-250x250.jpg)

> _[A Swift 2 tutorial for the iOS 9 Feast!](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/iOS9_feast_Swift2.jpg)_

Using the fundamental building blocks such as variables and constants (some of which you learned about in [our previous free excerpt from the Swift Apprentice](http://www.raywenderlich.com/?p=117139)), you might think you're ready to conquer the world! Almost ;]

Most programs that perform complex tasks would probably benefit from higher levels of abstraction. In other words, in addition to an `Int`, `String` or `Array`, they'll need new types that are specific to the domain of the task at hand.

This tutorial will introduce _structures_, which are a "named type". Like a `String`, `Int` or `Array`, you can define your own structures to create named types to later use in your code. By the end of this tutorial, you'll know how to define and use your own structures.

## Introducing Structures

Imagine you're writing a program that calculates if a potential customer is within range of a pizza delivery restaurant. You might write code like this:
    
    
    let latitude: Double = 44.9871
    let longitude: Double = -93.2758
    let range: Double = 200.0
     
    func isInRange(lat: Double, long: Double) -> Bool {
      // And you thought in Math class
      // you would never use the Pythagorean theorem!
      let difference = sqrt(pow((latitude - lat), 2) +
        pow((longitude - long), 2))
      let distance = difference * 0.002
      return distance < range
    }

Simple enough, right? A successful pizza delivery business may eventually expand to include multiple locations, which adds a minor twist to the deliverable calculator:
    
    
    let latitude_1: Double = 44.9871
    let longitude_1: Double = -93.2758
     
    let latitude_2: Double = 44.9513
    let longitude_2: Double = -93.0942

Now what? Do you update your function to check against both sets of coordinates? Eventually, the rising number of customers will force the business to expand, and soon it might grow to a total of 10 stores! Not only that, but some new stores might have different delivery ranges, depending on whether they're in a big city or a sprawling suburb.

You might briefly consider creating an array of latitudes and longitudes, but it would be difficult to both read and maintain. Fortunately, Swift has additional tools to help you simplify the problem.

### Your First Structure

Structures, or _structs_, are one of the _named types_ in Swift that allow you to encapsulate related properties and behaviors. You can define it, give it a name and then use it in your code.

In the example of the pizza business, it's clear that latitude and longitude are closely related--close enough that you could think of them as a single value:
    
    
    struct Location {
      let latitude: Double
      let longitude: Double
    }

This block of code demonstrates the basic syntax for defining a `struct`. In this case, it's a type named `Location` that combines both latitude and longitude.

The basic syntax begins with the `struct` keyword followed by the name and a pair of curly braces. Everything between the curly braces is a "member" of the struct.

Now that you've defined your first struct, you can instantiate one and store it in a constant or variable just like any other type you've worked with:

Instead of storing the coordinates in two separate variables, you store them together!

To create the `Location` value, you use the name of the type along with parentheses containing both the `latitude` and the `longitude` parameters. Swift defines this _initializer_ automatically, and it's a subject this tutorial will cover in more detail later.

You may remember that there's also a range involved, and now that the pizza business is expanding, there may be different ranges associated with different restaurants. You can create another struct that represents the location and the range, like so:
    
    
    struct DeliveryRange {
      var range: Double
      let center: Location
    }
     
    let storeLocation = Location(latitude: 44.9871, longitude: -93.2758)
    var pizzaRange = DeliveryRange(range: 200, center: storeLocation)

Now there's a new struct named `DeliveryRange` that contains a variable `range` of the pizza restaurant along with the `Location` center.

### Accessing Members

With your `DeliveryRange` defined and an instantiated value in hand, you may be wondering how you can _use_ these values. In Swift, structures and the other types you'll learn about use a simple "dot syntax" to access their members:

You can even access _members of members_ using dot syntax:

Similar to how you can read values with dot syntax, you can also _assign_ them. If the delivery range of one pizza location becomes larger, you could assign the new value to the existing variable:

![image001](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/come_pizza.png)

In addition to properties, you must declare the struct itself as a variable to be able to modify it:

Now that you have the range and location together in one struct, how would you rewrite isInRange(_:long:) to take a struct parameter instead of two `Double` values?

### Initializing a Struct

When you defined the `Location` and `DeliveryRange` structs, Swift automatically generated a way to create these values:

When you create an instance of a type such as `Location`, you need to use a special kind of function called an _initializer_. Swift will automatically create a default initializer, such as the one shown above, that takes each member as a named parameter.

You can also create your own initializer, which allows you to customize how a structure's members are assigned:
    
    
    struct Location {
      let latitude: Double
      let longitude: Double
     
      // String in GPS format "44.9871,-93.2758"
      init(coordinateString: String) {
        let crdSplit = coordinateString.characters.split(",")
        latitude = atof(String(crdSplit.first!))
        longitude = atof(String(crdSplit.last!))
      }
    }

Here, the `init` keyword marks this function as an initializer for the `Location` struct.

In this case, the initializer takes a latitude and longitude together as a comma-separated string. This could be useful if you're reading locations from a text file.

Keep in mind that as soon as you define a custom initializer, Swift won't add the automatically-generated one. If you still need it, you'll have to define it yourself!

### Introducing Self

If a method parameter and property have the same name, you can use the `self` keyword to give the compiler explicit context if you want to operate on the property. When you use `self` in code, you're explicitly accessing the current value of the named type.

In other words, using dot synax on `self` is just like using dot syntax on a variable storing that value.

You're not required to use `self` when writing code within a named type; Swift infers it automatically, which is why you've been able to write code without it so far.

Why use it then? It's especially useful in initializers: When two variables of the same name exist in the same scope, `self` can prevent what's known as _shadowing_.

There's an initializer argument `latitude` as well as a property `latitude`. Which one are you referring to in this code snippet?

It's actually the argument, which isn't what you want. Instead, you can simply add `self.` before the variable you're assigning, as follows:

This makes it clear that you're assigning the parameter values to the properties.

### Initializer Rules

Initializers in structs have a few rules that guard against unset values. By the end of the initializer, the struct _must_ have initial values set in all of its stored properties.

If you were to forget to assign the value of `longitude`, for instance, you would see an error at compile time:

![image001](http://cdn3.raywenderlich.com/wp-content/uploads/2015/10/structures1.png)

Its purpose is simple: Stored properties need to be initialized with a value.

Other languages have types similar to structs and may assign default values, such as a value of 0 for an integer. Swift, focusing on safety, ensures that every value has been explicitly set.

There's one exception to the rule that stored properties must have values: optionals!
    
    
    struct ClimateControl {
      var temperature: Double
      var humidity: Double?
     
      init(temp: Double) {
        temperature = temp
      }
    }

In this simplified example, humidity is an optional--perhaps an "optional" setting on a thermostat! Here, the initializer doesn't specify a value for `humidity`. Because `humidity` is an optional, the compiler will happily oblige.

For convenience, you can specify another initializer that would include both values:
    
    
    struct ClimateControl {
      var temperature: Double
      var humidity: Double?
     
      init(temp: Double) {
        temperature = temp
      }
     
      init(temp: Double, hum: Double) {
        temperature = temp
        humidity = hum
      }
    }

Now you can create `ClimateControl` values with or without a humidity value:

Optional variables _do_ get a default value of `nil`, which means the first initializer with only a temperature parameter is valid.

## Introducing Methods

Using some of the capabilities of structs, you could now make a pizza delivery range calculator that looks something like this:
    
    
    let pizzaJoints = [
      DeliveryRange(location: Location(coordinateString: "44.9871,-93.2758")),
      DeliveryRange(location: Location(coordinateString: "44.9513,-93.0942")),
    ]
     
    func isInRange(location: customer) -> Bool {
      for pizzaRange in pizzaJoints {
        let difference = sqrt(pow((latitude - lat), 2) + pow((longitude - long), 2))
        if (difference < joint.range) {
          return true
        }
      }
      return false
    }
     
    let customer = Location(“44.9850,-93.2750")
     
    print(isInRange(location: customer)) // Pizza time!

In this example, there's an array `pizzaJoints` and a function that uses that array to determine if a customer's location is within range of any of them.

The idea of being "in range" is very tightly coupled to the characteristics of a single pizza restaurant. In fact, all of the calculations in `isInRange` occur on one location at a time. Wouldn't it be great if `DeliveryRange` itself could tell you if the restaurant can deliver to a certain customer?

Much like a struct can have constants and variables, it can also define its _own_ functions:
    
    
    struct DeliveryRange {
      var range: Double
      let center: Location
     
      func isInRange(customer: Location) -> Bool {
        let difference = sqrt(pow((customer.latitude - center.latitude), 2) +
              pow((customer.longitude - center.longitude), 2))
        return difference < range
      }
    }

This code defines the _method_ `isInRange(_:)`, which is now a member of `DeliveryRange`. In Swift, methods are simply functions that are associated with a type. Just like other members of structs, you can use dot syntax to access a method through a value of its associated type:

## Structures as Values

The term _value_ has an important meaning when it comes to structs in Swift, and that's because structs create what are known as _value types_.

A value type is an object or a piece of data that is _copied_ on assignment, which means the assignment gets an _exact copy of the data_ rather than a reference to the very same data.
    
    
    // Assign the literal ‘5’ into a, an Int.
    var a: Int = 5
     
    // Assign the value in a to b.
    var b: Int = a
     
    print(a) // 5
    print(b) // 5
     
    // Assign the value ’10’ to a
    a = 10
     
    // a now has ’10’, b still has ‘5’
    print(a) // 10
    print(b) // 5

Simple, right! Obvious, even?

Notice that even though `a` and `b` have the same value to start, changing the value of `a` later doesn't affect `b`. They're separate variables with separate values.

How about the same principle, except with the `Location` struct:
    
    
    // Build a DeliveryRange value
    var range1: DeliveryRange = DeliveryRange(range: 200, center: Location(“44.9871,-93.2758”))
     
    // Assign the value in range1 to range2
    var range2: DeliveryRange = range1
     
    print(range1.range) // 200
    print(range2.range) // 200
     
    // Modify the range of range1 to ‘100’
    range1.range = 100
     
    // range1 now has ’100’, b still has ‘200’
    print(range1.range) // 100
    print(range2.range) // 200

As with the `Int` example, `range2` didn't pick up the new value set in `range1`. The important thing is that this demonstrates the _value semantics_ of working with structs. When you assign `range2` the value from `range1`, it gets an exact copy of the value. That means you can modify `range1` without also modifying the range in `range2`.

## Where To Go From Here?

Structs are just one of the named types available to you in Swift, and now that you understand struct basics you're ready to learn about their **reference type** counterparts: classes!

If you like what you see, we also cover enums and protocols and So Much More! in the book. These named types are what you'll use to define the things specific to your apps--people, windows, in-app purchases, and so on--and are an important part of learning Swift.

This post is an excerpt from the [Swift Apprentice](http://www.raywenderlich.com/store/swift-apprentice). Pick up a copy of the book if you'd like to learn more about Swift right from the foundations.

If you have any questions or comments on this tutorial, please join the forum discussion below!
