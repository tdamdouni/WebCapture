# Swift 2 Tutorial: A Quick Start

_Captured: 2015-11-25 at 16:45 from [www.raywenderlich.com](http://www.raywenderlich.com/115253/swift-2-tutorial-a-quick-start)_

If you're new here, you may want to subscribe to my [RSS feed](http://www.raywenderlich.com/feed/) or follow me on [Twitter](http://twitter.com/rwenderlich). Thanks for visiting!

![Get started quickly with this Swift 2 tutorial!](http://cdn4.raywenderlich.com/wp-content/uploads/2014/06/swift_tut-250x250.jpg)

> _Get started quickly with this Swift 2 tutorial!_

_Update 9/21/15_: Series updated for Xcode 7.0.

Swift is Apple's brand new programming language. Swift 1 was released last year at WWDC 2014, and just recently Swift 2 was released as part of Xcode 7.

Along with the language, Apple released an excellent [Swift reference guide](https://itunes.apple.com/us/book/swift-programming-language/id881256329?mt=11&uo=8&at=11ld4k&uo=8&at=11ld4k&uo=8&at=11ld4k) that I highly recommend.

However, the reference guide is long! So if you don't have a lot of time and just want to learn Swift quickly, this Swift 2 tutorial is for you.

This Swift 2 tutorial will take around 15 minutes and will give you a quick tour of the Swift language, including variables, control flow, classes, best practices, and more.

You'll even make a handy tip calculator along the way!

For this Swift 2 tutorial, make sure you have the very latest public copy of Xcode (Xcode 7.0 at the time of writing this Swift 2 tutorial). Swift is changing quickly and we are doing our best to update this tutorial as each beta comes out; the code may not work on older versions of Xcode or Pre-Release versions of Xcode.

_Note:_ This tutorial is best if you are already an experienced programmer and want a "quick start" to Swift. If you are brand new to programming and want something a bit slower-paced, you should check out [this tutorial series](http://www.raywenderlich.com/114148/learn-to-code-ios-apps-with-swift-tutorial-1-welcome-to-programming) instead.

## Introduction to Playgrounds

Start up Xcode 7, and go to _File\New\File_. Select _iOS\Source\Playground_, and click _Next_.

![Creating a new playground](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/000_Playground-452x320.png)

> _Creating a new playground_

Name the file _SwiftTutorial.playground_, click _Create_, and save the file somewhere convenient. Delete everything from your file so you start with a clean slate.

A _playground_ is a new type of file that allows you to test out Swift code, and see the results of each line in the sidebar. For example, add the following lines to your playground:
    
    
    let swiftTeam = 13
    let iOSTeam = 54
    let otherTeams = 48
    let totalTeam = swiftTeam + iOSTeam + otherTeams

As you type these lines, you will see the result of each line on the sidebar. Handy, eh?

Playgrounds are a great way to learn about Swift (like you're doing in this Swift 2 tutorial), to experiment with new APIs, to prototype code or algorithms, or to visualize your drawing code. In the rest of this Swift 2 tutorial, you will be working in this playground.

## Variables vs. Constants in Swift

Try adding the following line to the bottom of your playground:

You'll notice an error when you add this line. This is because `totalTeam` is a constant, meaning its value can never change. You declare constants with the keyword `let`.

You want `totalTeam` to be a variable instead -- a value that can change -- so you need to declare it with a different keyword: `var`.

To do this, replace the line that initializes `totalTeam` with the following:

Now it works! You may think to yourself, "why not just declare everything with `var`, since it's less restrictive?"

Well, declaring things with `let` whenever possible is best practice, because that will allow the compiler to perform optimizations that it wouldn't be able to do otherwise. So remember: prefer `let`!

## Explicit vs. Inferred Typing

So far, you haven't explicitly set any types for these constants and variables, because the compiler had enough information to infer it automatically.

For example, because you set `swiftTeam` to `13`, the compiler knows 13 is an `Int`, so it set the type of `swiftTeam` to an `Int` for you automatically.

However, you can set the type explicitly if you want. Try this out by replacing the line that sets `swiftTeam` to the following:

You may wonder if you should set types explicitly, or let the compiler infer the types for you. We believe it's better practice to let the compiler infer types automatically where possible, because then you get one of the main advantages of Swift: concise and easy to read code.

Because of this, switch the line back to inferred typing:

## Basic Types and Control Flow in Swift

So far, you've seen an example of _Int_, which is the Swift type that is used for integer values, but there's a bunch more.

Try out using some basic types by pasting the lines in each section below at the bottom of your playground.

_Floats and Doubles_

There are two types for decimal point values like this: `Float` and `Double`. `Double` has more precision, and is the default for inferring decimal values. That means `priceInferred` is a `Double` too.

_Bools_

Note that in Swift you use true/false for boolean values (unlike the convention of using YES/NO in Objective-C).

_Strings_

Strings are as you'd expect, except note that you no longer use the @ sign like you do in Objective-C. That might take your muscle memory a bit to get used to! :]

_If statements and string interpolation_

This is an example of an if statement, just like you'd expect in different languages. The parentheses around the condition are optional, and braces are required even for 1-line statements - w00t!

This also shows an example of a new technique called string interpolation. Whenever you want to substitute something in a string in Swift, simply use this syntax: `\\(your expression)`.

At this point, you can see the result of the `print` in the sidebar, but it may be difficult to read due to the limited space. To see the output, move your mouse over that line and click the eyeball that appears:

![001_Eyeball](http://cdn5.raywenderlich.com/wp-content/uploads/2015/09/001_Eyeball-480x305.png)

Here is the [playground file](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/SwiftTutorial-Demo1.playground.zip) up to this point in the tutorial.

## Classes and Methods

One of the most common things you'll be doing in Swift development is creating classes and methods, so let's jump in right away!

First, delete everything in your playground file so you're at a clean start.

Next, you'll create a tip calculator class that will help you figure out what you should tip at a restaurant. You'll add the code one small piece at a time, with explanations here each step along the way.

To create a class, simply enter the `class` keyword and the name of your class. You then put two curly braces for the class body.

If you were subclassing another class, you would put a `:` and then the name of the class you are subclassing. Note that you do not necessarily need to subclass anything (unlike in Objective-C, where you must subclass `NSObject` or something that derives from `NSObject`).

Add this code inside the curly braces:

You'll notice some errors after you add these but don't worry, you will fix them soon.

This is how you create properties on a class - the same way as creating variables or constants. Here you create three constant properties - one for the bill's total (post-tax), one for the tax percentage that was applied to the bill, and one for the bill's subtotal (pre-tax).

Note that any properties you declare must be set to an initial value when you declare them, or in your initializer - that's why you're currently getting errors. If you don't want to set your properties to an initial value, you'll have to declare them as optional (more on that in a future tutorial).

Add this code after the previous block (inside the curly braces):
    
    
      // 3
      init(total: Double, taxPct: Double) {
        self.total = total
        self.taxPct = taxPct
        subtotal = total / (taxPct + 1)
      }

This creates an initializer for the class that takes two parameters. Initializers are always named `init` in Swift - you can have more than one if you want, but they need to take different parameters.

Note that I have given the parameters of this method and the properties of this class the same names. Because of this, I need to distinguish between the two by putting the `self` prefix before the property names.

Note that since there is no name conflict for the `subtotal` property, you don't need to add the `self` keyword, because the compiler can automatically infer that. Pretty cool, huh?

Add this code after the previous block (inside the curly braces):

To declare a method, you use the _func_ keyword. You then list the parameters (you must be explicit with the types), add the `->` symbol, and finally list the return type.

This is a function that determines the amount to tip, which is as simple as multiplying the subtotal by the tip percentage.

Add this code after the previous block (inside the curly braces):
    
    
    // 5
    func printPossibleTips() {
      print("15%: \(calcTipWithTipPct(0.15))")
      print("18%: \(calcTipWithTipPct(0.18))")
      print("20%: \(calcTipWithTipPct(0.20))")
    }

This is a new method that prints out three possible tips.

Note that when you call a method on an instance of a class, the first parameter does not need to be named (but the rest do).

Also, notice how string interpolation isn't limited to printing out variables. You can have all kinds of complicated method calls and operations right inline if you like!

Add this code to the bottom of the playground (after the curly braces):

Finally, you create an instance of the tip calculator and call the method to print the possible tips.

Here's what your playground file should look like at this point:
    
    
    // 1
    class TipCalculator {
     
      // 2
      let total: Double
      let taxPct: Double
      let subtotal: Double
     
      // 3
      init(total: Double, taxPct: Double) {
        self.total = total
        self.taxPct = taxPct
        subtotal = total / (taxPct + 1)
      }
     
      // 4
      func calcTipWithTipPct(tipPct: Double) -> Double {
        return subtotal * tipPct
      }
     
      // 5
      func printPossibleTips() {
        print("15%: \(calcTipWithTipPct(0.15))")
        print("18%: \(calcTipWithTipPct(0.18))")
        print("20%: \(calcTipWithTipPct(0.20))")
      }
     
    }
     
    // 6
    let tipCalc = TipCalculator(total: 33.25, taxPct: 0.06)
    tipCalc.printPossibleTips()

Check your sidebar for the results:

![002_Results](http://cdn5.raywenderlich.com/wp-content/uploads/2015/09/002_Results-480x279.png)

## Arrays and For Loops

Currently there is some duplication in the above code, because you're calling the `calcTipWithTotal` method several times with different tip percentages. You could reduce the duplication here by using an array.

Replace the contents of `printPossibleTips()` with the following:

This shows an example of creating an array of doubles, with both inferred and explicit typing (you create both just for demonstration purposes). Note that `[Double]` is just a shortcut for `Array<Double>`.

Ignore the warnings for now. Then add these lines underneath:

Enumerating through items in an array is similar to fast enumeration in Objective-C - note that there are no parentheses needed!

You could also have written this loop like this (but the current syntax is preferred style):

The `..<` operator is a non-inclusive range operator and doesn't include the upper bound value. There's also a `...` operator which is inclusive.

Arrays have a `count` property for the number of items in the array. You can also look up a particular item in an array with the `arrayName[index]` syntax, like you see here.

## Viewing Print Output

Notice that with the new loop, you can no longer see the lines that are printed in the sidebar, but instead see the line "(3 times)":

![003_Sidebar](http://cdn5.raywenderlich.com/wp-content/uploads/2015/09/003_Sidebar-480x113.png)

Don't worry - you just need to bring up the Playground console to see the print results. Click the button in the bottom left of your playground that looks like an up arrow:

![004_UpArrow](http://cdn2.raywenderlich.com/wp-content/uploads/2015/09/004_UpArrow-480x195.png)

You should now be able to see the results of all of your print statements!

![005_ConsoleOutput](http://cdn3.raywenderlich.com/wp-content/uploads/2015/09/005_ConsoleOutput-480x261.png)

## Dictionaries

Let's make one last change to your tip calculator. Instead of simply printing out the tips, you can return a dictionary with the results instead. This would make it easier to display the results in some sort of user interface for the app.

Delete the `printPossibleTips()` method and replace it with the following:
    
    
    // 1
    func returnPossibleTips() -> [Int: Double] {
     
      let possibleTipsInferred = [0.15, 0.18, 0.20]
     
      // 2
      var retval = [Int: Double]()
      for possibleTip in possibleTipsInferred {
        let intPct = Int(possibleTip*100)
        // 3
        retval[intPct] = calcTipWithTipPct(possibleTip)
      }
      return retval
     
    }

You'll get an error in your playground, but you'll fix that in a moment.

First let's go over the code section by section:

  1. Here you mark the method as returning a dictionary, where the key is an Int (the tip percentage as an int, like 15 or 20), and the value is a Double (the calculated tip). Note that `[Int: Double]` is just a shortcut for `Dictionary<Int, Double>`.
  2. This is how you create an empty dictionary. Note that since you are modifying this dictionary, you need to declare it as a variable (with var) rather than a constant (with let). Otherwise you will get a compile error.
  3. This is how you set an item in a dictionary. As you can see, it's similar to the literal syntax in Objective-C.

Finally, modify the last line in your playground to call this method (this fixes the error):

Once the playground evaluates, you should see the results as a dictionary in the inspector (click the eyeball for an expanded view and use the down arrows to expand).

![Final results](http://cdn4.raywenderlich.com/wp-content/uploads/2015/09/006_Final-700x394.png)

> _Final results_

And that's it - congratulations, you have a fully functional Tip Calculator in Swift!

## Where To Go From Here?

Here is the [final playground file](http://cdn5.raywenderlich.com/wp-content/uploads/2015/09/SwiftTutorial-Demo2.playground.zip) with all the Swift code from this tutorial.

Want to learn more? Keep reading for the [next part of this series](http://www.raywenderlich.com/?p=74904), where you'll learn how to create a user interface for this app, or check out our [new Swift books](http://www.raywenderlich.com/store)!

I hope you've enjoyed this tutorial, and welcome to the world of Swift! :]
