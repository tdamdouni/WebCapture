# What we learned from rewriting our robotic control software in Swift

_Captured: 2015-11-06 at 09:38 from [www.sunsetlakesoftware.com](http://www.sunsetlakesoftware.com/2015/11/03/what-we-learned-rewriting-our-robotic-control-software-swift)_

![Apple_Swift_Logo.png](http://www.sunsetlakesoftware.com/sites/default/files/images/Apple_Swift_Logo.png)

At the beginning of this year we started a complete rewrite of our robotics software from Objective-C to Swift, for reasons [described here](http://www.sunsetlakesoftware.com/2014/12/02/why-were-rewriting-our-robotics-software-swift). That rewrite was concluded two months ago, passed testing a month ago, and has been deployed to all of our customers. As a result, I wanted to do a final analysis of the rewrite and what we learned from it.

### An overview

To recap my previous post about this, we sell [robotic systems for printing microscale elements](http://www.sonoplot.com/products) from a variety of materials for electronics, life sciences, and other research applications. These systems use controlled ultrasonic vibrations and precise three-axis positioning systems to dispense picoliter volumes of fluid.

We use Macs to drive these robots, with control software that was written in Objective-C. We made the decision to rewrite this software in Swift late last year, but only after a careful survey of the bugs that had impacted our customers over the years. That survey revealed that most of these shipped bugs would have been prevented or detected early in Swift-based code.

We believed that redesigning this application using Swift would allow us to create a safer, more maintainable, and more testable application. Not only did we achieve those goals, but the resulting application is more responsive, nearly doubles the printing speed of our systems, and has a slew of other improvements. Unit testing is now implemented from the lowest levels to the highest in the application, catching issues that were impractical to test for before.

To illustrate how maintainable this new codebase is, a useful statistic is lines of code:

The Swift version of our Objective-C application, with the same user interface and features, is only 39% as large. In fact, the Swift version has a number of additional features and several optional windows that were not present in the old Objective-C version. While a chunk of the code reduction is due to removing redundancies (replicated definitions in interfaces and implementations, etc.) and abandoning my trusty Allman indentation style, most is due to better code reuse and better design that Swift encourages.

I should state that I was proud of how much we were able to do with very little code in our old Objective-C codebase, so I did not expect to see the kind of reduction in code size that we did. [Others have seen code reductions on the same scale](http://www.fastcompany.com/3050266/tech-forecast/lyft-goes-swift-how-and-why-it-rewrote-its-app-from-scratch-in-apples-new-lang), but a direct translation of Objective-C code to Swift probably wouldn't. The greatest benefit comes from rethinking how you approach problems in this new language.

We started this rewrite in December of 2014, finished it in August 2015, and deployed this to all of our customers after thorough testing in early October. A few notes on timing of this: all of this was done by only two developers, [Janie Clayton](http://redqueencoder.com) and myself (Brad Larson), and I could only work on this part time. This rewrite came at the same time as we were designing, building, and launching [a completely new robot](http://www.sonoplot.com/products/microplotter-proto), which drew our attention away for months at a time. We also were extremely careful in our tests, as many final system tests needed to be run on large and expensive hardware.

Do I think this rewrite was worth the time and effort? Absolutely. I have much greater confidence in the correctness and design of this software. Our customers have already expressed their happiness with the increased responsiveness and throughput of our robots. We have a very solid foundation to start implementing capabilities we've wanted for years, but were afraid to add because they might break other things.

### Eliminating bug sources

With that overview, I'd like to talk about the specifics of what we observed during our rewrite. When we started this, I [wrote about](http://www.sunsetlakesoftware.com/2014/12/02/why-were-rewriting-our-robotics-software-swift) how we had identified four primary causes of bugs shipped to customers in the last few years:

  * Silent failures due to nil-messaging
  * Wrong enum lookup tables being used for values
  * Improperly handled NSErrors, or other Objective-C error failures
  * Bad object typecasts

Swift's explicit optionals pretty much eliminated the first group of bugs, for reasons described in that previous post. They forced us to think about when and where optional values could be returned or passed into a function, identifying many places where we had made bad assumptions before. They even allowed us to get rid of some magic constants we'd previously used to express a non-value returned from a function. The evolution of the language (something I'll talk about later) has reduced the code needed for common optional uses over time.

Let's talk about the other bug sources in detail.

### The power of enums

It might be surprising to see bad enum usage being implicated in a number of bugs, but it was embarrassing to see how often this came up in our survey. It was all too easy to provide one integer type into something that expected another, or to use the wrong values in a switch statement. Swift's non-integer enums did away with that.

This also gives me an excuse to talk about the surprising power of the Swift enum data type. Perhaps because of the name, I've seen many Objective-C developers regard Swift enums as nothing more than cleaner versions of C enums. The ability for Swift enum cases to have distinct associated values of any type, particularly when combined with generics, makes them far more capable than that.

Swift enums let you create a type for mutually exclusive values, an "OR" type. These pair with tuples, structs, and objects, which are "AND" types. With the addition of tuples and enums with associated values, Swift addresses a huge shortcoming of C and Objective-C: the fact that a function / method can only return a single value.

### Swift error handling

This is a powerful enough concept to build an entire error handling system on top of, which [we did using a Result enum type](http://www.sunsetlakesoftware.com/2015/06/12/swift-2-error-handling-practice). Even when we swapped that out for Swift 2's error handling system, it still informed our design. Functions can return errors or a result, and that both cleans up our logic and makes it safer.

In the example provided in the link above, I showed how a bit of Objective-C NSError-based code that was 38 lines long could be converted into 12 lines of Swift code using a Result type. Swift 2's try/catch error handling dropped that to 9 lines of code. This kind of a code reduction held true across our entire codebase, and the compiler-enforced capture and handling of all errors found a number of places we had missed in our Objective-C code.

However, I have only become more convinced over time that there should be the ability to specify error types in the Swift 2 model. For example, we have a CommunicationsError enum type for any RS-232 serial communication errors that occur. At a higher level, we have RoboticsError and ElectronicsError types that reflect specific issues with both of those hardware subsystems. Both our robotics and control electronics use RS-232 communications, so they catch CommunicationsErrors and either attempt silent recoveries or convert them into appropriate RoboticsErrors or ElectronicsErrors.

We use these two error types to present the appropriate information to the user and to recover from errors in an context-sensitive way. If we get a CommunicationsError indicating that a cable is unplugged, we want that to be converted into a RoboticsError or ElectronicsError so the user will be told which piece of hardware is disconnected.

At present, I have no way of telling the compiler that the only error type a function should return return is a RoboticsError, so if I miss a conversion from a CommunicationsError to a RoboticsError at some point, I'm accidentally bubbling up a generic CommunicationsError and losing error recovery information (and potentially exposing myself to a crash if I make assumptions about error types higher up).

This also prevents me from writing catch statements that are exhaustive without a default clause. I'd love to be able to do this, so that as I add error cases to my enums I'm notified of all the places I need to update my error presentation or recovery code.

I'm not saying typing of errors should be mandatory, just that I'd love to be able to write something like

and have the compiler give me an error if I can throw something other than a RoboticsError within that, as well as know that I can only get a RoboticsError error type out of that. For those who don't need this, they can keep using an implied ErrorType as is done today.

### The value of strong types

That complaint shows how much I value Swift's type system. Strong types and type inference have given me greater confidence in the correctness of my code.

There have been [good arguments from long-time Objective-C developers about the value of Objective-C's dynamism](http://edgecasesshow.com/099-swift-is-a-really-good-thing-and-a-step-back.html). I once felt the same way, but I now favor compiler checks for correctness over flexibility at run time. I've burned myself with run time flexibility in my code more than I've benefited from it.

I'll let you in on a secret: I don't trust any of the code I write. I've been programming for decades, and I still keep making the same stupid mistakes. I need as much help as I can get to verify the correctness of my code, and Swift's strong types aid me here. Every mistake that the compiler can catch is one that I don't need to find in testing or end up shipping out to my customers.

As an example, we have a series of functions that need to process an array of exactly five values, and that output a resulting array of exactly five values of a different type. In Objective-C, we would use an NSArray for the inputs and outputs. There are several things that could go wrong with this. The input array could be nil, could contain more or fewer than five values, or the values could be of the wrong type. The same problems could happen at the output.

Now, I could trust that every input to each of these functions came from a correctly-written function and that each function in turn could only output results of the type we expect. After seeing this go wrong in every possible way, I can't help but think of the good Dr. Malcolm lecturing us about how "life finds a way." Therefore, our Objective-C code ended up with checks and assertions for nil values, bad sizes, and bad types in many of these functions.

I tried to approach this in a different way in Swift. Rather than passing in an untyped array, I instead used five-element tuples of a defined type for inputs and outputs. By doing so, I could use the compiler to guarantee that exactly five elements of a given type needed to be passed into a function, and that another five elements of a different type needed to be passed out. None of the cases I tested for in Objective-C were possible in this Swift code, so I could remove all of the verification code and stop worrying that I missed something.

I can see a future in which we might get [dependent types](https://jeremywsherman.com/blog/2015/08/26/read-why-dependent-types-matter/) to handle this in Swift, which if possible would be pretty great.

The ease with which you can create lightweight data types in Swift also worked for cases where we were getting physical units mixed up in our code. We created small structs for frequency units like Hertz and Kilohertz that were incompatible and used them to make it clear when we were using one unit and when another. Conversions were made explicit, and it was easier to read the code of many functions.

Well-defined types like this have let our code fit together like puzzle pieces, rather than amorphous blobs. If this fits with that, I feel more confident that I've written correct code. By no means does it guarantee this, but it certainly helps.

### Designing for testability

Using Swift features, we were able to prevent ourselves from being able to write classes of bugs, but we still needed to test our code. In our previous Objective-C codebase, this was impractical. We had large classes talking to other classes, coupled through mutable state in ways that were hard to see. These classes also talked to expensive external hardware, and I couldn't see an easy way to build unit tests around any of this.

For years, I'd heard people like [Dave Dribin](http://www.dribin.org/dave/blog/archives/2010/01/18/why_unit_test_cocoa_and_iphone/) and [Graham Lee](http://www.amazon.com/Test-Driven-iOS-Development-Developers-Library/dp/0321774183) advocate for writing testable Objective-C, and knew that I should, but I found it hard to put their lessons into practice.

This rewrite gave us the opportunity to completely rethink the design of our application. The previously-mentioned "AND" and "OR" data types of Swift make it easy to separate inputs from outputs when writing functions, and to remove side effects. It's easy to build tests for functions like this, so we decided to write as much of our logic in this functional style. I've been studying Haskell for the last year in order to teach myself to think this way.

Our application isn't purely functional, but a hybrid. At the top level, we have lightweight window and view controllers to handle user interactions, with a minimal amount of logic inside them. They exist to kick off actions and display results, and that's it. At the bottom, we have small classes that interface with external hardware. Reference types (classes) are used to map to pieces of hardware and UI elements (windows and view controllers). These are both places where side-effects exist as the software interacts with the outside world. Value types are used everywhere else for data passed between functions.

Everything in between is functional in nature. The vast majority of the code for this application can be subjected to easy-to-write unit tests, with only the thin UI layer needing a little more work to test.

Our design approach was to start each bit of logic as a top-level function. We would figure out the inputs and outputs needed to perform an operation, and break up the steps of this operation into manageable chunks as needed. In the cases where it made sense for this to be a method on a class (functionality that varies with the specific robot type, etc.) we would then move it into one, but be careful that we limited the hidden inputs and side-effects within that method.

Because the classes representing pieces of hardware are passed in by reference to these functions, we could create mock classes that took input and gave output in a scripted manner. At the lowest level, we created a fake serial port class that we could rig up to verify an exact sequence of bytes being sent out as well as send back a known series of bytes (or known communication errors). We could simulate all aspects of our large, expensive hardware in simple unit tests. In my [previous post](http://www.sunsetlakesoftware.com/2014/12/02/why-were-rewriting-our-robotics-software-swift), I showed some examples of how we used function currying and enums to build these mock classes and tests.

When crafting these unit tests, we used generics to assemble a series of helper functions that made testing error-throwing functions a little easier. One example is the following:
    
    
    func assertCommandSucceedsWithResult<T:Equatable>(targetResult:T, _ command:() throws -> T, file: String = __FILE__, line: UInt = __LINE__) {
        do {
            let result = try command()
            XCTAssert(result == targetResult, "Received value of \(result), which doesn't match target of \(targetResult).", file:file, line:line)
        } catch {
            XCTFail("Operation should have succeeded, but failed with error \(error).", file:file, line:line)
        }
    }

which tests to verify that a function / method which can throw an error successfully produces a result matching a certain value. It uses the [Swift builtins](http://practicalswift.com/2014/06/10/list-of-implicitly-defined-variables-in-swift/) of __FILE__ and __LINE__ to make sure that the XCTest functions mark the line where the function is called on a failure, not the inside of this function.

It's used in the following way:
    
    
    assertCommandSucceedsWithResult([4,3,2,1], {
        try readBytesFromSerialPort(4, serialPort:self.fakeSerialPort)
    })

That's a compact, readable way to test two conditions: that the function didn't throw an error, and that the result it produced exactly matched the target.

Inspired by [Erica Sadun's post on the matter](http://ericasadun.com/2015/08/27/capturing-context-swiftlang/), we also replaced many uses of print() with the following printWithContext():
    
    
    func printWithContext(stringToPrint:String, file: String = __FILE__, line: UInt = __LINE__, function: StaticString = __FUNCTION__) {
    #if DEBUG
        print("\(stringToPrint) --> \((file as NSString).lastPathComponent): \(function): \(line)")
    #endif
    }

that captures the file, line, and function within the application where something was logged to the console. It also is silenced in release builds. When you do place a log statement like

you get something like the following on the console:

### Code reuse via generics and higher-order functions

These helper functions show something that became more important as the project grew: code reuse via generics and higher-order functions. One of the grand promises of object-oriented programming is that you would be able to reuse a ton of code via subclassing, etc. That didn't always work out, and sometimes even went in the other direction.

Instead of trying to plan out some grand architecture and figure out how we were going to reuse code, we just started writing. It was only at the point when we felt like we were repeating ourselves that we stopped and thought about extracting the common code from these sections.

Generics made this easier by letting us write functions that operated on broad groupings of types, yet preserved the strong typing we found so useful. Higher-order functions let us pull out larger chunks of code that were the same, but that had smaller parts within them that changed. Those smaller parts were filled in by functions or closures provided as arguments.

Even operator overloading played a part. Three-dimensional math is a lot simpler to write when you can overload arithmetic operators to work on (X, Y, Z) coordinates.

Generics and higher-order functions also caused us to rethink design patterns that are widely used in Objective-C. For example, if I had an elaborate operation that was used in several places and was mostly the same except for a different callback or calculation performed at each place, I might reach for the delegate pattern in Objective-C. Place that code within a class, create a delegate protocol, add a delegate property, and call a delegate method at the right place within that reused code.

In Swift I approached this differently. I'd create a top-level, standalone function containing the common code and take a function as an argument that became the part that changed or acted as a callback. No class, no protocol, no property, just a higher-order function. In my eyes, this became a simpler way of solving these problem and required less support code.

Could I have done this in Objective-C? With blocks, yes in most cases. Swift just makes this easy, so I started thinking about problems in a different way.

### Working with an evolving language

One of the big complaints about Swift has been its rapid pace of evolution over the last year. I started exploring Swift right after it was announced, followed it through the beta period, and we kept moving our project to the latest Swift betas as they were released. This did complicate development somewhat, but I don't think it led to a significant slowdown in this project. At worst, we found ourselves spending a few hours with major Swift updates migrating our code to the latest language changes.

It was interesting to observe our thought process as features were added or changed in the language. Like with the language itself, we typically would see some new thing be added and think that it was interesting but not something we'd use right away. We had other problems to solve.

Then at some point we'd find a possible use case for the new feature and try it out. Almost always, that feature would simplify or make safer the code we tried it on. Then we'd recognize other places to use it, and pretty soon it would be all over our code. Swift is a pragmatic language, and after working with it for a while you can tell that the new features are all intended to solve real, not theoretical, problems.

A good example of this is our property list serialization implementation that [Janie describes in her blog](http://redqueencoder.com/property-lists-and-user-defaults-in-swift/). If you get to the Swift code at the end, you'll see the use of failable initializers (Swift 1.1), chained if-let statements (Swift 1.2), and guards (Swift 2.0) all in a single snippet. Each one of these language features was added over the last year, and all had utility.

Even minor language additions, like ?? for default optional values, or let variables whose value is assigned within an if statement, seem indispensable in the code I write today. I think I yawned at all of them when they were added.

While we have used protocols and protocol extensions throughout our code, we haven't leaned as hard into protocols as others. The Swift team seems to be trending in that direction, but I still like starting with top-level functions, defining the inputs and outputs, and going from there. Like the other language additions, I might someday see the broad applications for this and start using it everywhere.

### A better application

As I said at the start, I feel our investment in rewriting our control software in Swift has paid off. We have a smaller, more manageable codebase that has unit tests from the bottom up. Longstanding, subtle issues with the software were exposed and fixed as we built this in a hybrid functional style. We were able to make better algorithmic and structural decisions that led to a much faster and more responsive application.

This all-Swift control software has been running robots in research institutes and companies across the globe for over a month now, and the response has been overwhelmingly positive. I always hold my breath after every software release, but this one has been the smoothest we've had in years.

If you want to know more about this, Janie [gave a talk about our work at [360|iDev min] 2015](https://vimeo.com/141942228) that I recommend watching.
