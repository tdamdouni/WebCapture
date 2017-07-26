# Optionals in Swift

_Captured: 2015-06-12 at 23:15 from [medium.com](https://medium.com/p/c94fd231e7a4)_

#### To nil or not to nil.

While watching the _[Intermediate Swift_](https://developer.apple.com/videos/wwdc/2014/) video (Session 403 at WWDC2014), I saw that the Optionals language construct in Swift can be used in two really cool ways:

  * Optionals can be implicitly unwrapped using _Optional Binding_
  * _Optional Chaining_ lessens the need for nested conditionals

### The Basics

For completeness, an _Optional_ is a constant or variable in swift that can or cannot be nil. It is defined by adding a question mark **?** after the type declaration:
    
    
    // Constant string that is declared as an optional.  
    let constantOptional: String? = "Test" 
    
    
    // Variable string that is declared as an optional.  
    var variableOptional: String? = "Test" 

On the contrary, a non-optional is just your run-of-the-mill constant or variable. A runtime error is thrown if a non-optional constant/variable ever becomes nil. Apple had safety in mind when developing Swift, and this is one explicit example of it.

Traditionally, in Objective-C, we would test is a variable was not nil by doing the following (assume a string variable **_testVar_**exists for this example):
    
    
    if (!testVar) {  
        NSLog(@"testVar is nil");  
    } else {   
        NSLog(@"testVar is equal to %@", testVar);  
    }

With optionals, testing is slightly simplified, as we don't have to explicitly add a character to test for the non-existence of our **_testVar _**variable (see example block):
    
    
    var testVar: String? = myRandomFunction() // May return nil
    
    
    if testVar { // testVar is not nil  
     println("testVar is equal to \(testVar!)")  
    } else {   
     println("testVar is equal to nil")  
    }

The **! **at the end of the interpolated **_testVar_** string gets the value of the optional by _unwrapping_ it from the optional. The **! **should only be used when we know we have a value for a fact, otherwise a runtime error is thrown with the following message:
    
    
    fatal error: Can’t unwrap Optional.None

However, there's an easier way to test if an optional constant/variable has a value, and that's by using _Optional Bindings._

### Optional Binding

Optional Bindings essentially boils down to the use of two Swift keywords:

Let me get straight to the example:
    
    
    var testVar: String? = myRandomFunction() // May return nil
    
    
    **if let **constVar = testVar {   
     println("testVar is equal to \(constVar)")  
    } else {   
     println("testVar is equal to nil")  
    }

In this conditional, the existence of a value for **_testVar_**is tested first. If it's nil, the else statement is executed. If it's not nil, the value of **_testVar_** is _implicitly unwrapped_ and assigned to a new, temporary constant called **_constVar_**. This **_constVar_** can then be used in the conditional block without using the "**!**".In other words, you don't need to use the "**!**"character, because the value was copied over to a new constant variable.

We can simplify this example even further by evaluating the function within the conditional statement:
    
    
    **if let** testVar = myRandomFunction() {   
       println("testVar is equal to \(testVar)")  
    } else {   
       println("testVar is equal to nil")  
    }

This example shows that we don't even have to worry about explicitly declaring or unwrapping optionals. If the return value of **_myRandomFunction() _**is nil, the else statement block is executed. Otherwise, the result is copied to **_testVar_**, and that block is executed.

Now, what if we have nested conditionals that all depend on optional constants/variables having a value? The code will get dirty quickly if we explicitly nest them. However, Swift takes care of this with the use of **_Optional Chaining_**_._

### Optional Chaining

Optional Chaining allows us to chain multiple optionals together using dot-syntax, and conditionally check if each value in the chain exists. The optional chaining operator is:

Let's say we have the following two classes
    
    
    class House {  
        let garage: Garage?  
    }
    
    
    class Garage {  
        var numberOfCars: Int?  
    }

Here's how we would check to find the number of cars that exist for a given house using the traditional method:
    
    
    let house = House()  
    let garage = house.garage
    
    
    if let garage = garage {  
        // The house has a garage  
        if let numberOfCars = garage.numberOfCars {  
            // One or more cars in the garage   
        } else {  
            // No cars in the garage  
        }  
    } else {  
        // The house does not have a garage  
    }

Here's how we would achieve the same functionality using Optional Chaining:
    
    
    let house = House()  
    let numberOfCars = house.garage?.numberOfCars
    
    
    if let numberOfCars = numberOfCars {  
        // One more more cars in the garage  
    } else {  
        // No cars in the garage  
    }

In this example, optional chaining allowed us to get rid of the out conditional statement. Think of **?.** as a slightly modified ternary operator [**?:**] that is equivalent to a complete if-else block. The more you have in your chain, the more if-else statements you are avoiding having to write. This is a great example of Swift's terseness! Unfortunately, the downside of using this optional chaining operator lessens our ability to debug/log any issues that may occur.

Regardless, optionals are very cool safety feature in Swift. More info can be found in [Apple's iBook](https://itunes.apple.com/us/book/swift-programming-language/id881256329?mt=11).
