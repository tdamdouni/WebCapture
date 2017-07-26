# Reference vs Value Types in Swift: Part 1/2

_Captured: 2015-11-25 at 20:38 from [www.raywenderlich.com](http://www.raywenderlich.com/112027/reference-value-types-in-swift-part-1)_

If you're new here, you may want to subscribe to my [RSS feed](http://www.raywenderlich.com/feed/) or follow me on [Twitter](http://twitter.com/rwenderlich). Thanks for visiting!

![Value? Reference? Shared? Copy? Get your swift variables under control!](http://cdn5.raywenderlich.com/wp-content/uploads/2015/08/value-vs-reference-250x250.png)

> _Value? Reference? Shared? Copy? Get your swift variables under control!_

If you've been keeping up with the sessions from WWDC 2015, you might have noticed a real emphasis on re-thinking code architecture in Swift. One of the biggest differences developers note when coming to Swift from Objective-C is the heavy preference of _value types_ over _reference types_.

This two-part series illustrates the differences between each type and shows you when each type is appropriate to use. You'll learn about the main concepts of each type in Part 1, while in [Part 2](http://www.raywenderlich.com/112029/reference-value-types-in-swift-part-2) you'll work through a real-world problem as you learn more advanced concepts and discover some subtle but important points about both types.

Whether you're coming from a traditional Objective-C background, or you're more versed in Swift, you're sure to learn something about the ins and outs of typing in Swift.

## Getting Started

First, create a new playground: in Xcode, select _File__\__New__\__Playground…_ and name the playground _ValueSemanticsPart1_. You can select either platform since this tutorial is platform-agnostic and only focuses on the Swift language aspects.

Click _Next_, choose a convenient location to save the playground and click _Create_ to open it.

## Reference Types vs. Value Types

So what's the core difference between these two types? The quick-and-dirty explanation is that value types _keep_ a unique copy of their data, while reference types _share_ a single copy of their data.

Swift represents a reference type as a `class`. This is similar to Objective-C, where everything that inherits from `NSObject` is stored as a reference type.

There are many kinds of value types in Swift, such as `struct`, `enum`, and tuples. You might not realize that Objective-C also uses value types in number literals like `NSInteger` or even C structures like `CGPoint`.

To better understand the difference between the two, it's best to start out with what you'll recognize from Objective-C: reference types.

### Reference Types

In Objective-C -- and most other object-oriented languages -- you hold references to objects. In Swift, however, you use `class` which is implemented using reference semantics.

Add the following to your playground:
    
    
    // Reference Types:
     
    class Dog {
      var wasFed = false
    }

The above class represents a pet dog and whether or not the dog has been fed. Create a new instance of your Dog class by adding the following:

This simply points to a location in memory that stores `dog`. To add another object to hold a reference to the same dog, add the following:

Because `dog` is a reference to a memory address, `puppy` points to the exact same address. Feed your pet by setting `wasFed` to `true`:

`puppy` and `dog` both point to the exact same memory address.

![value-reference](http://cdn3.raywenderlich.com/wp-content/uploads/2015/08/value-reference-480x196.png)

Therefore you'd expect any change in one to be reflected in the other. Check that this is true by viewing the property values in your playground:

Changing one named instance affects the other since they both _reference_ the same object. This is exactly what you'd expect in Objective-C.

### Value Types

Value types are referenced completely differently than reference types are. You'll explore this with some simple Swift primitives.

Add the following `Int` variable assignments and the corresponding operations to your playground:
    
    
    // Value Types:
     
    var a = 42
    var b = a
    ++b
     
    a    // 42
    b    // 43

What would you expect `a` and `b` to equal? Clearly, `a` equals _42_ and `b` equals _43_. If you'd declared them as reference types instead, _both_ `a` and `b` would equal _43_ since both would point to the same memory address.

The same holds true for any other value type. In your playground, implement the following `Cat` `struct`:
    
    
    struct Cat {
      var wasFed = false
    }
     
    var cat = Cat()
    var kitty = cat
    kitty.wasFed = true
     
    cat.wasFed        // false
    kitty.wasFed      // true

This shows a subtle, but important difference between reference and value types: setting `kitty`'s `wasFed` property has no effect on `cat`. The `kitty` variable received a copy of the _value_ of `cat` instead of a _reference_.

![value-value](http://cdn2.raywenderlich.com/wp-content/uploads/2015/08/value-value-480x206.png)

Looks like your `cat`'s going hungry tonight! :]

Although it's much faster to assign a reference to a variable, copies are almost as cheap. Copy operations run in constant O(n) time since they use a fixed number of reference-counting operations based on the size of the data.

This performance hit may seem like a reason to always use reference types, but Part 2 of this series shows you the clever methods in Swift that optimize these copy operations.

### Mutability

`var` and `let` function differently for reference types and value types. Notice that you defined `dog` and `puppy` as constants with `let`, yet you were able to change the `wasFed` property. How's that possible?

For reference types, `let` means the _reference_ must remain constant. In other words, you can't change the _instance_ the constant references, but you _can_ mutate the instance itself.

For value types, `let` means the _instance_ must remain constant. No properties of the instance will ever change, regardless whether the property is declared with `let` or `var`.

It's much easier to control mutability with value types. To achive the same immutability/mutability behavior with reference types, you'd need to implement immutable and mutable class variants such as `NSString` and `NSMutableString`.

## What Type Does Swift Favor?

It may surprise you that the Swift standard library uses value types almost exclusively. The results of a quick search for `enum`, `struct`, and `class` in Swift 1.2 and Swift 2.0 show a bias in the direction of value types:

Swift 1.2:

  * _struct_: 81 
  * _enum_: 8 
  * _class_: 3 

Swift 2.0:

  * _struct_: 87 
  * _enum_: 8 
  * _class_: 4 

This includes types like `String`, `Array`, and `Dictionary` which are all implemented as `struct`s.

## Which to Use and When

Now that you know the difference between the two types, when should you choose one over the other?

There's one case where the choice is forced upon you: many Cocoa APIs require `NSObject` subclasses, which forces you into using `class`. But other than that, you can use the following cases from Apple's [Swift blog](https://developer.apple.com/swift/blog/?id=10) to decide whether to use a `struct` / `enum` value type or a `class` reference type.

### When to Use a Value Type

Generally speaking, use value types in the following instances:

_Comparing instance _data_ with _==_ makes sense_

"But of course," you say. "I want every object to be comparable!". But you need to consider whether the _data_ should be comparable. Consider the following implementation of a point:

Does that mean two variables with the exact same `x` and `y` members should be considered equal?

It's clear that two `Point`s with the same internal values should be considered equal. The memory location of those values doesn't matter; you're concerned about the values themselves.

Therefore, you'd need to conform to the `Equatable` protocol, which is good practice for all value types. This protocol defines only one function which you must implement globally in order to compare two instances of the object. This means that the `==` operator must have the following characteristics:

  * _Reflexive_: `x == x` is true 
  * _Symmetric_: if `x == y` then `y == x`
  * _Transitive_: if `x == y` and `y == z` then `x == z`

Here's a sample implementation of `==` for your `Point`:

_Copies should have independent state_

Taking your `Point` example a little further, consider the following two `Shape` instances with their centers as two initially equivalent `Point`s:
    
    
    struct Shape {
      var center: Point
    }
     
    let initialPoint = Point(x: 0, y: 0)
    let circle = Shape(center: initialPoint)
    var square = Shape(center: initialPoint)

What would happen if you altered the centerpoint of one of the shapes?

Each `Shape` needs its own copy of a `Point` so you can maintain their state independent of each other. Could you imagine the chaos of all shapes sharing the same copy of a center `Point`? :]

_The data will be used in code across multiple threads_

This one's a little more complex. Will multiple threads access this data? If so, will it _really_ matter if the data isn't equal across all threads at all times?

To make your data accessible from multiple threads and equal across threads, you'll need to use a reference type and implement [locking](https://en.wikipedia.org/wiki/Lock_\(computer_science\)) as well -- no easy task!

If threads _can_ uniquely own the data, using value types makes the whole point moot since each owner of the data only references the data instead of holding a copy.

### When to Use a Reference Type

Although value types are useful in many cases, reference types are still useful in the following situations:

_Comparing instance identity with _===_ makes sense_

`===` checks if two objects are _exactly_ identical, right down to the memory address that stores the data.

To put this in real-world terms, consider the following: if your cubicle-mate swaps one of your $20 bills with another legitimate $20 bill, you don't really care, as you're only concerned about the _value_ of the object.

However, if someone stole the Magna Carta and created an identical parchment copy of the document in its place, that _would_ matter greatly because the inherent _identity_ of the document is not the same at all.

You can use the same thought process when deciding whether to use reference types; usually there are very few times when you really care about the inherent identity -- that is, the memory location -- of the data. You usually just care about comparing the data values.

_You want to create a shared, mutable state_

Sometimes you want a piece of data to be stored as a single instance and accessed and mutated by multiple consumers.

A common object with a shared, mutable state is a shared bank account. You might implement a basic representation of an account and person as follows:
    
    
    class Account {
      var balance = 0.0
    }
     
    class Person {
      let account: Account
      init(_ account: Account) {
        self.account = account
      }
    }

If any joint account holders add money to the account, then the new balance should be reflected on all debit cards linked to the account:
    
    
    let account = Account()
     
    let person1 = Person(account)
    let person2 = Person(account)
     
    person2.account.balance += 100.0
     
    person1.account.balance    // 100
    person2.account.balance    // 100

Since `Account` is a `class`, each `Person` holds a _reference_ to the account, and everything stays in sync.

### Still Undecided?

If you're not quite sure which mechanism applies to your situation, default to value types. You can always move to a `class` later with little effort.

![value-struct](http://cdn2.raywenderlich.com/wp-content/uploads/2015/08/value-struct-417x320.png)

Consider, though, that Swift uses value types almost exclusively, which is mind-boggling when you consider that the situation in Objective-C is completely the reverse.

As a code architect under the new Swift paradigm, you need to do a bit of up-front planning as to how your data will be used. You can solve almost any situation with either value types or reference types -- but using them incorrectly could result in tons of bugs and confusing code.

In all cases, common sense and a willingness to change your architecture when new requirements come up is the best approach. Challenge yourself to follow the Swift model; you just might turn out some nicer code than you originally thought!

## Where to Go From Here?

You can download the complete playground with all the code in this article [here](http://cdn3.raywenderlich.com/wp-content/uploads/2015/08/ValueSemanticsPart1Final.playground.zip).

By this point you've covered the differences between value types and reference types and when to use one over the other. In [Part 2 of this tutorial series](http://www.raywenderlich.com/112029/reference-value-types-in-swift-part-2), you'll work through a real-world problem and learn some advanced mechanics of value types.

If you have any comments or questions, feel free to join in the forum discussion below!

  
![Value? Reference? Why not both in combination?](http://cdn4.raywenderlich.com/wp-content/uploads/2015/08/value-reference-com-250x250.png)

> _Value? Reference? Why not both in combination?_

Welcome to the second and final part of our series on reference and value semantics in Swift! In [Part 1](http://www.raywenderlich.com/?p=112027), you explored the difference between _reference_ and _value_ types and the appropriate scenarios for each.

Part 2 uses a real-world example to illustrate each value type in more detail -- and show you some of their more subtle characteristics.

## Getting Started

First, create a new playground: in Xcode, select _File__\__New__\__Playground…_ and name the playground _ValueSemanticsPart2_. You can select either platform since this tutorial is platform-agnostic and only focuses on the Swift aspects.

Click _Next_, choose a convenient location to save the playground and click _Create_ to open it.

## Copy-on-Write

Part 1 showed you how value types work on the surface, but how do they work under the hood?

Value types implement an awesome feature called _copy-on-write_: when assigned, each reference points to the same memory address. It's only when one of the references modifies the underlying data that Swift actually copies the original instance and makes the modification.

To see how this works, add the following basic implementation of an address to your playground:
    
    
    struct Address {
      var streetAddress: String
      var city: String
      var state: String
      var postalCode: String
    }

All properties of `Address` together form a unique physical address of a building in the real world. The properties are all value types represented by `String`; the validation logic has been left out to keep things simple.

Next, you'll need to create a few variables to store the same exact `Address` structure. Add the following to the end of your playground:
    
    
    var test1 = Address(streetAddress: "1 King Way", city: "Kings Landing", state: "Westeros", postalCode: "12345")
    var test2 = test1
    var test3 = test2

To see how copy-on-write works, you'll need to inspect the memory addresses of each instance of `Address`. That will take a little bit of hackery as Swift hides these values from you.

### Seeing Memory

Add the following code below your `Address` implementation:
    
    
    struct AddressBits {
      let underlyingPtr: UnsafeMutablePointer<Void>
      let padding1: Int
      let padding2: Int
      let padding3: String
      let padding4: String
      let padding5: String
    }

This structure represents the exact size of the `Address` object you created earlier. You'll pass this type to a function along with an `Address` object that will output its address in memory.

The `UnsafeMutablePointer` constant will store the memory address, while the padding variables are simply there to make this structure match the size of `Address`. Don't worry about the specifics of this structure; its sole purpose is to populate the correct amount of bits.

As noted earlier, on each assignment Swift creates a new copy of the original data and references it. To see what's happening under the hood, add the following code to the end of your playground:
    
    
    let bits1 = unsafeBitCast(test1, AddressBits.self)
    let bits2 = unsafeBitCast(test2, AddressBits.self)
    let bits3 = unsafeBitCast(test3, AddressBits.self)
     
    bits1.underlyingPtr
    bits2.underlyingPtr
    bits3.underlyingPtr

The code above calls `unsafeBitCast(_:type:)` with the structure you created earlier along with the `AddressBits` representation to store the memory location. It then prints out the `underlyingPtr` variable to see the exact memory address.

You should see something like the following:

![SS1](http://cdn2.raywenderlich.com/wp-content/uploads/2015/08/SS1-700x110.png)

Whoa -- each variable has the exact same memory address! This seems to go against how you _thought_ value types worked. It's clear there's some Swift magic involved in the process. :]

### Triggering Copy-on-Write

What happens when you mutate one of the variable's properties? Add the following above the calls to `unsafeBitCast(_:type:)`:

Then have a look at the pointer addresses:

![SS2](http://cdn3.raywenderlich.com/wp-content/uploads/2015/08/SS2-700x127.png)

When you mutate `test2`, Swift creates a new, unique copy and assigns it back to the original variable! You'll notice that `test1` and `test3` still point to the same instance because nothing's mutated them yet.

### Intelligent Memory

To see an even crazier result, add the following code to mutate `test3` to the same value you just assigned to `test2`:

Swift saw that both `test2` and `test3` had the same underlying data and pointed each to the same instance.

![SS3](http://cdn5.raywenderlich.com/wp-content/uploads/2015/08/SS3-700x135.png)

Not only can Swift lazily copy the data, it can also intelligently assign equal value types to the same memory address.

### Copy-on-Write Summary

The above behavior is what makes value types so powerful in Swift. Swift intelligently references equal objects until they've mutated, which results in optimized memory usage as well as optimized CPU cycles for incredibly fast performance.

But the performance improvements don't end there. When two value types share the same space in memory, Swift doesn't even rely on the `==` comparison as it knows they _must_ be equal by definition. Small details like these go a long way in making Swift so efficient.

All of these optimizations are hidden away from you, the developer, so you can realize the benefits of reference types at a low-level while never having to worry about two value type variables referencing the same instance. Pretty neat!

## Mixing Value and Reference Types

As promised, here's the real-world scenario that shows you some of the decisions and tradeoffs you must make when choosing either value types or reference types.

### Reference Types Containing Value Type Properties

It's quite common for a reference type to contain value types. An example would be the combination of a `Person` class where _identity_ matters, and an `Address` structure where _equality_ matters.

Add the following code to the bottom of your playground:
    
    
    class Person {          // Reference type
      var name: String      // Value type
      var address: Address  // Value type
     
      init(name: String, address: Address) {
        self.name = name
        self.address = address
      }
    }

This mixing of types makes perfect sense in this scenario. Each class instance has its own value type property instances that aren't shared.

Where things get messy is when a value type contains a reference type, as shown in the section below.

### Value Types Containing Reference Type Properties

Add the following code to your playground:

Each copy of the `Bill` object is a unique copy of the data, but the `billedTo` `Person` will be shared by numerous `Bill` instances. This adds quite a bit of complexity in maintaining the value semantics of your objects. For instance, how do you compare two `Bill` objects since value types should be `Equatable`?

You _could_ try the following:
    
    
    // Do not add this to your playground!
     
    extension Bill: Equatable { }
    func ==(lhs: Bill, rhs: Bill) -> Bool {
      return lhs.amount == rhs.amount && lhs.billedTo === rhs.billedTo
    }

Using the identity operator `===` checks that the two objects have the exact same reference, which means two value types share data. That's exactly what you _don't_ want when following value semantics.

So what can you do?

## Getting Value Semantics From Mixed Types

You obviously created `Bill` as a `struct` for a reason, and making it rely on a shared instance defeats the original purpose. Add the following code to the bottom of your playground:
    
    
    // 1
    let billAddress = Address(streetAddress: "1 King Way", city: "Kings Landing", state: "Westeros", postalCode: "12345")
    let billPayer = Person(name: "Robert", address: billAddress)
     
    // 2
    let bill = Bill(amount: 42.99, billedTo: billPayer)
    let bill2 = bill
     
    // 3
    billPayer.name = "Bob"
     
    // Inspect values
    bill.billedTo.name    // "Bob"
    bill2.billedTo.name   // "Bob"

Taking each numbered comment in turn:

  1. First, you create a new `Person` based on an `Address` and name. 
  2. Next, you instantiate a new `Bill` using the default initializer and create a copy by assigning it to a new constant. 
  3. Finally, you mutate the passed-in `Person` object, which in turn…affects the supposedly unique instances. 

Hmm, that's not what you want. What you _could_ do is make `Bill` copy a new unique reference in `init(amount:billedTo:)`. You'll have to write your own `copy` method, though, since `Person` isn't an `NSObject` and doesn't have its own version.

### Copying References During Initialization

Replace your implementation of `Bill` with the following:
    
    
    struct Bill {
      let amount: Float
      let billedTo: Person
     
      init(amount: Float, billedTo: Person) {
        self.amount = amount
        self.billedTo = Person(name: billedTo.name, address: billedTo.address)
      }
    }

// Create a new Person reference from the parameter

All you added here was an explicit initializer. Instead of simply assigning `billedTo`, you create a new `Person` instance with the same data (name and address) as the one passed in. The caller won't be able to edit their original copy of `Person` and affect `Bill`.

Look at the two printout lines at the bottom of your playground where you check the value of each instance of `Bill`. You'll see that each kept their original values even after mutating the passed-in parameter:

One big issue with this design is that you can access `billedTo` from outside the struct; that means it could be mutated by an outside entity in an unexpected manner.

Add the following to the bottom of the playground, just above the printout lines:

Check the printout values now; they've been mutated by some outside entity -- that is, your rogue code above. The issue here is that even if your struct is immutable, anyone with access to it could mutate its underlying data.

### Using Copy-on-Write Computed Properties

You could fix this by making `billedTo` private and only returning a copy on write.

Remove the test lines at the end of the playground:
    
    
    // Remove these lines:
    /*
    bill.billedTo.name = "Bob"
     
    bill.billedTo.name
    bill2.billedTo.name
    */

Now consider the following implementation of `Bill`:
    
    
    struct Bill {
      let amount: Float
      private var _billedTo: Person // 1
     
      // 2
      var billedToForRead: Person {
        return _billedTo
      }
      // 3
      var billedToForWrite: Person {
        mutating get {
          _billedTo = Person(name: _billedTo.name, address: _billedTo.address)
          return _billedTo
        }
      }
     
      init(amount: Float, billedTo: Person) {
        self.amount = amount
        _billedTo = Person(name: billedTo.name, address: billedTo.address)
      }
    }

Here's what's going on here:

  1. First, you created a private variable to hold a reference to the `Person` object. 
  2. Next, you created a computed property to return the private variable for _read_ operations. 
  3. Finally, you created a computed property which will always make a new, unique copy of `Person` for _write_ operations. Note that this property must also be declared as mutating, since it changes the underlying value of the structure. 

If you can guarantee that your caller will use your structure exactly as you meant, this approach would solve your issue. In a perfect world, your caller would always use `billedToForRead` to get data from your reference and `billedToForWrite` to make a change to the reference.

![value-apirage](http://cdn2.raywenderlich.com/wp-content/uploads/2015/08/value-apirage-480x300.png)

But that's not how the world works, does it? :]

### Defensive Mutating Methods

You'll have to add a bit of defensive code here. To solve this, you could hide the two new properties from the outside and create methods to interact with them properly.

Replace your implementation of `Bill` with the following:
    
    
    struct Bill {
      let amount: Float
      private var _billedTo: Person
     
      // 1
      private var billedToForRead: Person {
        return _billedTo
      }
     
      private var billedToForWrite: Person {
        mutating get {
          _billedTo = Person(name: _billedTo.name, address: _billedTo.address)
          return _billedTo
        }
      }
     
      init(amount: Float, billedTo: Person) {
        self.amount = amount
        _billedTo = Person(name: billedTo.name, address: billedTo.address)
      }
     
      // 2
      mutating func updateBilledToAddress(address: Address) {
        billedToForWrite.address = address
      }
     
      mutating func updateBilledToName(name: String) {
        billedToForWrite.name = name
      }
     
    }

Here's what you changed above:

  1. You made both computed properties `private` so that callers can't access the properties directly. 
  2. You also added methods to mutate the `Person` reference with a new name or address. This makes it impossible for someone else to use it incorrectly, since you're hiding the underlying `billedTo` property. 

Declaring this method as `mutating` means you can only call it when you instantiate your `Bill` object using `var` instead of `let`. This behavior is exactly what you'd expect when working with value semantics.

### A More Efficient Copy-on-Write

The last thing to do is improve the efficiency of your code. You currently copy the reference type `Person` _every single time_ you write to it. A better way is to only copy the data if multiple objects hold reference to it.

Replace the implementation of `billedToForWrite` with the following:
    
    
    private var billedToForWrite: Person {
      mutating get {
        if !isUniquelyReferencedNonObjC(&_billedTo) {
          _billedTo = Person(name: _billedTo.name, address: _billedTo.address)
        }
        return _billedTo
      }
    }

`isUniquelyReferencedNonObjC(_:)` checks that no other object holds a reference to the passed-in parameter. If no other object shares the reference, then there's no need to make a copy and you return the current reference. That will save you a copy, and mimics what Swift itself does when working with value types.

## Where to Go From Here?

You can download the complete playground with all the code in this series [here](http://cdn2.raywenderlich.com/wp-content/uploads/2015/08/ValueSemanticsPart2Final.playground.zip).

In this tutorial you learned that both value and reference types have some very specific functionality which you can leverage to make your code work in a predictable manner. You also learned how copy-on-write keeps value types performant by lazily copying the data only when needed and how to circumvent the confusing state of combining value and reference types in one object.

Hopefully this exercise in mixing value and reference types has shown you how challenging it can be to keep your semantics consistent, even in a simple scenario like the one above. If you find yourself in this scenario, it's a good sign something needs a bit of redesign.

The example in this tutorial was bent on ensuring a `Bill` could hold reference to a `Person`, but perhaps you could have used a `Person`'s unique ID or simply `name`. To take it a step further, maybe the whole design of a `Person` as a `class` was wrong from the outset! These are the types of things you have to evaluate as your project requirements change.

I hope you enjoyed this series; you can use what you've learned here to modify the way you approach value types in your code and hopefully avoid confusing and obfuscated code.

If you have any comments or questions feel free to join in the forum discussion below!
