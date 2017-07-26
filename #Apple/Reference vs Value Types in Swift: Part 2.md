# Reference vs Value Types in Swift: Part 2

_Captured: 2015-11-25 at 20:39 from [www.raywenderlich.com](http://www.raywenderlich.com/112029/reference-value-types-in-swift-part-2)_

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
