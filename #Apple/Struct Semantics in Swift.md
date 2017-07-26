# Struct Semantics in Swift

_Captured: 2015-08-30 at 15:21 from [chris.eidhof.nl](http://chris.eidhof.nl/posts/struct-semantics-in-swift.html)_

In our book [Advanced Swift](https://www.objc.io/books/advanced-swift/), we show how to implement your own copy-on-write structs in detail. This blogpost shows the same technique, but in less detail.

One big difference between Swift strings and Cocoa strings is how they deal with mutability. If you define a Swift string using `let`, the compiler enforces immutability: there is no way to change the string:
    
    
    let myString = "immutable string"
    myString += " test" // Illegal
    

In Cocoa, the same is done using classes: an `NSString` is immutable, and an `NSMutableString` is mutable. However, there is a catch: NSMutableString is a subclass of NSString. Therefore, we can do the following:
    
    
    let x: NSMutableString = "Hello"
    let y: NSString = x
    x.appendString(" world")
    // Now x and y both point to the string "Hello world"
    

Even if we have a variable that's an NSString, we cannot be sure that it's immutable, in order to be completely sure, we need to make a copy:
    
    
    let x: NSMutableString = "Hello"
    let y: NSString = x.copy() as! NSString
    x.appendString(" world")
    // Now x is "Hello world", and y is "Hello"
    

With Swift strings, this works a bit differently. Because they are defined as structs, they have copy semantics. If you have a constant string, there is no way it can change under your nose:
    
    
    var x = "Hello"
    let y = x
    x += " world"
    // Now x is "Hello world", and y is still "Hello"
    

Another advantage of Swift's approach is that both `x` and `y` are the same String type. They have methods defined that can mutate the string, but all those methods are marked as `mutating`. You simply cannot call them on constant values: the compiler won't let you.

In order to understand how they work, we will make a wrapper around `NSData`. For mutation, `NSData` also has a subclass `NSMutableData`, but it suffers from the same problem as `NSString`: you always have to make a copy if you want to be sure that you the data doesn't change accidentally.

Before we can start, we will need a small wrapper type: `Box`. This can wrap anything, be it a class, or a struct, and the result will be a Swift class.
    
    
    final class Box<A> {
        let unbox: A
        init(_ value: A) { unbox = value }
    }
    

Now we can create our own `Data` struct. It just contains a single field, `boxedData`. We also add a convience accessor `data` which just unboxes the data. We provide an initializer, which also has a default (empty) value.
    
    
    struct Data {
        private var boxedData: Box<NSMutableData>
        var data: NSData { return boxedData.unbox }
        init(data: NSData = NSData()) {
            self.boxedData = Box(NSMutableData(data: data))
        }
    }
    

First, we'll define some read-only functions: these can be used on immutable values of our struct. They just call their respective methods on `NSData`:
    
    
    extension Data {
        var length: Int { return data.length }
        var bytes: UnsafePointer<Void> {
            return data.bytes
        }
    }
    

To create a mutating variant, we first write a mutating accessor for `boxedData`. This accessor makes a copy of the data before returning it. This allows us to implemement `append`: whenever we `append` to a Swift `var`, we now automatically make a copy. This way, our data has the same semantics as other Swift structs such as strings and arrays.
    
    
    private var mutableData: NSMutableData {
        mutating get {
            boxedData = Box(NSMutableData(data: data))
            return boxedData.unbox
        }
    }
    
    mutating func append(other: NSData) {
        mutableData.appendData(other)
    }
    

There is one problem with the code above. It is very inefficient. If we define a single variable and mutate it a couple of times, each time the internal data will be copied, even though no other variable is referring to the same data:
    
    
    var myData = Data()
    myData.append(someOtherData) // copy
    myData.append(moreData) // copy
    

Instead, we can change our `mutableData` accessor to prevent copying when there are no other references to the `data` variable. To do this, we need to check if the data is uniquely referenced. In other words, we only make a copy of the data if the data is shared. We can do this using the `isUniquelyReferencedNonObjC` function. This is the reason why we need `Box`: it only works on Swift classes. `NSMutableData` is an Objective-C class, and then the function doesn't work.
    
    
    private var mutableData: NSMutableData {
        mutating get {
            if !isUniquelyReferencedNonObjC(&boxedData) {
                boxedData = Box(NSMutableData(data: data))
            }
            return boxedData.unbox
        }
    }
    

Now we have full copy semantics, and efficient behavior: only when a copy is really necessary, it is made. This way, we never have to remember to write `data.copy()` ourselves, we implemented it correctly once and can then forget about it. I think it's probably a matter of time until the Swift Standard Library will get extended with a `Data` type, but even then, this technique is very useful when you want to make your own efficient structs by wrapping pointers.

To test our behavior, we can add some `print` statements to the `mutableData` accessor, and verify that our behavior is correct:
    
    
    private var mutableData: NSMutableData {
        mutating get {
            if !isUniquelyReferencedNonObjC(&boxedData) {
                print("Making a copy")
                boxedData = Box(NSMutableData(data: data))
            } else {
                print("Not making a copy")
            }
            return boxedData.unbox
        }
    }
    

As stated in the introduction, we describe this technique in more detail in our book [Advanced Swift](https://www.objc.io/books/advanced-swift/). If you've enjoyed this post, be sure to grab a copy. Finally, a gist of the code is [here](https://gist.github.com/chriseidhof/d96f0f652a7c6358d865).
