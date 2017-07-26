# 50 iOS Interview Questions And Answers Part 2

_Captured: 2017-03-25 at 19:45 from [medium.com](https://medium.com/ios-os-x-development/50-ios-interview-questions-and-answers-part-2-45f952230b9f#.34pif1l3m)_

![](https://cdn-images-1.medium.com/max/600/1*ovd-UHga2TNvP0xwLaoJMg.png)

Hello, Part 2 is ready and waiting to be bitten. :) If you need check part 1 [here you are.](https://medium.com/@duruldalkanat/ios-interview-questions-13840247a57a#.p6nkhl76a)

**1- Please explain Method Swizzling in Swift**

Method Swizzling is a well known practice in Objective-C and in other languages that support dynamic method dispatching.

Through swizzling, the implementation of a method can be replaced with a different one _at runtime_, by changing the mapping between a specific #selector(method) and the function that contains its implementation.

To use method swizzling with your Swift classes there are two requirements that you must comply with:

  * The class containing the methods to be swizzled must extend NSObject
  * The methods you want to swizzle must have the dynamic attribute

**2- What is the difference Non-Escaping and Escaping Closures ?**

The lifecycle of a non-escaping closure is simple:

  1. Pass a closure into a function
  2. The function runs the closure (or not)
  3. The function returns

**Escaping closure means**, inside the function, you can still run the closure (or not); the extra bit of the closure is stored some place that will outlive the function. There are several ways to have a closure escape its containing function:

  * **Asynchronous execution**: If you execute the closure asynchronously on a dispatch queue, the queue will hold onto the closure for you. You have no idea _when_ the closure will be executed and there's no guarantee it will complete before the function returns.
  * **Storage**: Storing the closure to a global variable, property, or any other bit of storage that lives on past the function call means the closure has also escaped.

**3- Explain **`**[weak self] and [unowned self] ?**`

**unowned **does the same as weak with one exception: The variable will not become nil and therefore the variable must not be an optional.

But when you try to access the variable after its instance has been deallocated. That means, you should only use **unowned** when you are sure, that this variable will never be accessed after the corresponding instance has been deallocated.

However, if you don't want the variable to be weak AND you are sure that it can't be accessed after the corresponding instance has been deallocated, you can use unowned.

By declaring it **[weak self] **you get to handle the case that it might be nil inside the closure at some point and therefore the variable must be an optional. A case for using **[weak self] **in an asynchronous network request, is in a **view controller** where that request is used to populate the view.

**4- What is ARC ?**

ARC is a compile time feature that is Apple's version of automated memory management. It stands for _Automatic Reference Counting. _This means that it **_only_** frees up memory for objects when there are **_zero strong_** references/ to them.

**5- Explain #keyPath() ?**

Using #keyPath(), a static type check will be performed by virtue of the key-path literal string being used as a StaticString or StringLiteralConvertible. At this point, it's then checked to ensure that it

> A) is actually a thing that exists and

> B) is properly exposed to Objective-C.

**6- What is IGListKit providing for Developers ?**

IGListKit automatically diffs our objects and performs animated batch updates on the `**UICollectionView**`for whatever changed. This way we never have to write batch updates for ourself.

**7- What makes React Native special for iOS?**

  1. (Unlike PhoneGap) with React Native your application logic is written and runs in JavaScript, whereas your application UI is fully native; therefore you have none of the compromises typically associated with HTML5 UI.
  2. Additionally (unlike Titanium), React introduces a novel, radical and highly functional approach to constructing user interfaces. In brief, the application UI is simply expressed as a function of the current application state.

**8- What is NSFetchRequest ?**

NSFetchRequest is the class responsible for fetching from Core Data. Fetch requests are both powerful and flexible. You can use fetch requests to fetch a set of objects meeting the provided criteria, individual values and more.

**9- Explain NSPersistentContainer ?**

The persistent container creates and returns a container, having loaded the store for the application to it. This property is optional since there are legitimate error conditions that could cause the creation of the store to fail.

**10- Explain NSFetchedResultsController ?**

NSFetchedResultsController is a controller, but it's not a _view _controller. It has no user interface. Its purpose is to make developers' lives easier by abstracting away much of the code needed to synchronize a table view with a data source backed by Core Data.

Set up an NSFetchedResultsController correctly, and your table will mimic its data source without you have to write more than a few lines of code.

**11- What is the three major debugging improvements in Xcode 8 ?**

  * The **View Debugger **lets us visualize our layouts and see constraint definitions at runtime. Although this has been around since Xcode 6, Xcode 8 introduces some handy new warnings for constraint conflicts and other great convenience features.
  * The **Thread Sanitizer **is an all new runtime tool in Xcode 8 that alerts you to threading issues -- most notably, potential race conditions.
  * The **Memory Graph Debugger **is also brand new to Xcode 8. It provides visualization of your app's memory graph at a point in time and flags leaks in the Issue navigator.

**12- What is the Test Driven Development of three simple rules ?**

  1. You are not allowed to write any production code unless it is to make a failing unit test pass.
  2. You are not allowed to write any more of a unit test than is sufficient to fail; and compilation failures are failures.
  3. You are not allowed to write any more production code than is sufficient to pass the one failing unit test.

**13- Please explain final keyword into the class ?**

By adding the keyword final in front of the method name, we prevent the method from being overridden. If we can replace the final class keyword with a single word static and get the same behavior.

**14- What does Yak Shaving mean ?**

Yak shaving is a programing term that refers to a series of tasks that need to be performed before a project can progress to its next milestone.

**15- What is the difference open & public access level ?**

**open** allows other modules to use the class and inherit the class; for members, it allows others modules to use the member and override it.

**public** only allows other modules to use the public classes and the public members. Public classes can no longer be subclassed, nor public members can be overridden.

**16- What is the difference fileprivate &private access level ?**

**fileprivate** is accessible within the current file, **private** is accessible within the current declaration.

**17- What is Internal access ?**

Internal access enables entities to be used within any source file from their defining module, but not in any source file outside of the module.

Internal access is the default level of access. So even though we haven't been writing any access control specifiers in our code, our code has been at an internal level by default.

**18- What is difference between BDD and TDD ?**

The main difference between BDD and TDD is the fact that BDD test cases can be read by non-engineers, which can be very useful in teams.

iOS I prefer [Quick](https://github.com/Quick/Quick) BDD framework and its "matcher framework," called [Nimble](https://github.com/Quick/Nimble).

**19- Please explain "Arrange-Act-Assert"**

**AAA** is a pattern for arranging and formatting code in Unit Tests. If we were to write XCTests each of our tests would group these functional sections, separated by blank lines:

  * **Arrange** all necessary preconditions and inputs.
  * **Act** on the object or method under test.
  * **Assert** that the expected results have occurred.

**20- What is the benefit writing tests in iOS apps ?**

  * Writing tests first gives us a clear perspective on the API design, by getting into the mindset of being a client of the API before it exists.
  * Good tests serve as great documentation of expected behavior.
  * It gives us confidence to constantly refactor our code because we know that if we break anything our tests fail.
  * If tests are hard to write its usually a sign architecture could be improved. Following RGR ( Red -- Green -- Refactor ) helps you make improvements early on.

**21- What is five essential practical guidelines to improve your typographic quality of mobile product designs ?**

1\. Start by choosing your body text typeface.  
2\. Try to avoid mixing typefaces.  
3\. Watch your line length.  
4\. Balance line height and point size.  
5\. Use proper Apostrophes and Dashes.

**22- Explain If let structure**

If let is a special structure in Swift that allows you to check if an Optional rhs holds a value, and in case it does -- unwraps and assigns it to the lhs.

**23- How to educate app with Context ?**

Education in context technique helping users interact with an element or surface in a way they have not done so previously. This technique often includes _slight visual cues_ and _subtle animation_.

![](https://cdn-images-1.medium.com/max/800/1*gzwrzLt-ocdJ-b_O38kbXQ.jpeg)

**24- What is bitcode ?**

It's a very general encoding format that we can use for XML-type purposes. It's a self-describing file format and multiple different things can be encoded in Bitcode. Apple Watch apps have to be in Bitcode and Apple TV is required. iOS is still optional. The advantage is compiler keeps getting better.

**25- Explain Swift Standart Library Protocol ?**

There are three protocol. **[Equatable**](https://developer.apple.com/reference/swift/equatable) protocol, that governs how we can distinguish between two instances of the same type. That means we can analyze. If we have a specific value is in our array. The **[comparable**](https://developer.apple.com/reference/swift/comparable) protocol, to compare two instances of the same type and **ExpressibleByStringLiteral**.

**26- What is the difference SVN and Git ?**

**SVN** relies on a centralised system for version management. It's a central repository where working copies are generated and a network connection is required for access.

**Git** relies on a distributed system for version management. You will have a local repository on which you can work, with a network connection only required to synchronise.

**27- What is the difference CollectionViews & TableViews ?**

**TableViews** display a list of items, in a single column, a vertical fashion, and limited to vertical scrolling only.

**CollectionViews** also display a list of items, however, they can have multiple columns and rows.

**28- What is Alamofire doing ?**

Alamofire provides chainable request/response methods, JSON parameter and response serialization, authentication, and many other features.

**29- REST, HTTP, JSON -- What's that?**

**HTTP** is the application protocol, or set of rules, web sites use to transfer data from the web server to client. The client (your web browser or app) use to indicate the desired action:

  * **GET**: Used to retrieve data, such as a web page, but doesn't alter any data on the server.
  * **HEAD**: Identical to GET but only sends back the headers and none of the actual data.
  * **POST**: Used to send data to the server, commonly used when filling a form and clicking submit.
  * **PUT**: Used to send data to the specific location provided.
  * **DELETE**: Deletes data from the specific location provided.

**REST**, or REpresentational State Transfer, is a set of rules for designing consistent, easy-to-use and maintainable web APIs.

**JSON** stands for JavaScript Object Notation; it provides a straightforward, human-readable and portable mechanism for transporting data between two systems. Apple supplies the `**JSONSerialization**` class to help convert your objects in memory to JSON and vice-versa.

**30- What problems does delegation solve?**

  * Avoiding tight coupling of objects
  * Modifying behavior and appearance without the need to subclass objects
  * Allowing tasks to be handed off to any arbitrary object

**31- What is the major purposes of Frameworks?**

Frameworks have three major purposes:

  * Code encapsulation
  * Code modularity
  * Code reuse

You can share your framework with your other apps, team members, or the iOS community. When combined with Swift's access control, frameworks help define strong, testable interfaces between code modules.

**32- Explain Swift Package Manager**

The Swift Package Manager will help to vastly improve the Swift ecosystem, making Swift much easier to use and deploy on platforms without Xcode such as Linux. The Swift Package Manager also addresses the problem of [dependency hell](https://en.wikipedia.org/wiki/Dependency_hell) that can happen when using many interdependent libraries.

**33- Which of the communication methods allows for a loosely coupled, one-to-many pattern?**

Notification

34- **Which of the communication methods allows for a loosely coupled, one-to-one pattern?**

A Calling a method on an object.

**35- Why do we use a delegate pattern to be notified of the text field's events?**

Because at most only a single object needs to know about the event.

**36- How is an inout parameter different from a regular parameter?**

A Inout passes by reference while a regular parameter passes by value.

**37- Explain View Controller Lifecycle events order ?**

There are a few different lifecycle event

**\- loadView**

> _Creates the view that the controller manages. _It's only called when the view controller is created and only when done programatically.

**\- viewDidLoad**

> Called after the controller's view is loaded into memory. It's only called when the view is created.

**\- viewWillAppear**

> It's called whenever the view is presented on the screen. In this step the view has bounds defined but **the orientation is not applied**.

**\- viewWillLayoutSubviews**

> Called to notify the view controller that its view is about to layout its subviews. This method is called every time the frame changes

**\- viewDidLayoutSubviews**

> Called to notify the view controller that its view has just laid out its subviews. Make additional changes here after the view lays out its subviews.

**\- viewDidAppear**

> _Notifies the view controller that its view was added to a view hierarchy._

**\- viewWillDisappear**

> Before the transition to the next view controller happens and the origin view controller gets removed from screen, this method gets called.

**\- viewDidDisappear**

> After a view controller gets removed from the screen, this method gets called. You usually override this method to stop tasks that are should not run while a view controller is not on screen.

**38- What is the difference between LLVM and Clang?**

[Clang](http://en.wikipedia.org/wiki/Clang) is the front end of LLVM tool chain ( "[clang" C Language Family Frontend for LLVM](http://clang.llvm.org/) ). Every [Compiler](http://en.wikipedia.org/wiki/Compiler#Front_end) has three parts .  
1\. Front end ( lexical analysis, parsing )  
2\. Optimizer ( Optimizing abstract syntax tree )  
3\. Back end ( machine code generation )

> Front end ( Clang ) takes the source code and generates abstract syntax tree ( LLVM IR ).

**39- What is Class ?**

A **class** is meant to define an object and how it works. In this way, a **class** is like a blueprint of an object.

**40- What is Object?**

An **object** is an instance of a class.

**41- What is interface?**

The **@interface** in Objective-C has nothing to do with Java interfaces. It simply declares a public interface of a class, its public API.

**42- When and why do we use an object as opposed to a struct?**

Structs are value types. Classes(Objects) are reference types.

**43- What is UIStackView?**

UIStackView provides a way to layout a series of views horizontally or vertically. We can define how the contained views adjust themselves to the available space. Don't miss this [article](https://www.raywenderlich.com/114552/uistackview-tutorial-introducing-stack-views).

**44- What are the states of an iOS App?**

  1. **_Non-running_** -- The app is not running.
  2. **_Inactive_** -- The app is running in the foreground, but not receiving events. An iOS app can be placed into an inactive state, for example, when a call or SMS message is received.
  3. **_Active_** -- The app is running in the foreground, and receiving events.
  4. **_Background_** -- The app is running in the background, and executing code.
  5. **_Suspended_** -- The app is in the background, but no code is being executed.

**45- What are the most important application delegate methods a developer should handle ?**

The operating system calls specific methods within the application delegate to facilitate transitioning to and from various states. The seven most important application delegate methods a developer should handle are:
    
    
    application:willFinishLaunchingWithOptions

Method called when the launch process is initiated. This is the first opportunity to execute any code within the app.
    
    
    application:didFinishLaunchingWithOptions

Method called when the launch process is nearly complete. Since this method is called is before any of the app's windows are displayed, it is the last opportunity to prepare the interface and make any final adjustments.
    
    
    applicationDidBecomeActive

Once the application has become active, the application delegate will receive a callback notification message via the method applicationDidBecomeActive.

This method is also called each time the app returns to an active state from a previous switch to inactive from a resulting phone call or SMS.
    
    
    applicationWillResignActive

There are several conditions that will spawn the applicationWillResignActive method. Each time a temporary event, such as a phone call, happens this method gets called. It is also important to note that "quitting" an iOS app does not terminate the processes, but rather moves the app to the background.
    
    
    applicationDidEnterBackground

This method is called when an iOS app is running, but no longer in the foreground. In other words, the user interface is not currently being displayed. According to Apple's [UIApplicationDelegate Protocol Reference](http://developer.apple.com/library/ios/#documentation/uikit/reference/UIApplicationDelegate_Protocol/Reference/Reference.html), the app has approximately five seconds to perform tasks and return. If the method does not return within five seconds, the application is terminated.
    
    
    applicationWillEnterForeground

This method is called as an app is preparing to move from the background to the foreground. The app, however, is not moved into an active state without the applicationDidBecomeActive method being called. This method gives a developer the opportunity to re-establish the settings of the previous running state before the app becomes active.
    
    
    applicationWillTerminate

This method notifies your application delegate when a termination event has been triggered. Hitting the home button no longer quits the application. Force quitting the iOS app, or shutting down the device triggers the applicationWillTerminate method. This is the opportunity to save the application configuration, settings, and user preferences.

**45- What does code signing do?**

_Signing_ our app allows _iOS_ to identify who signed our app and to verify that our app hasn't been modified since you signed it. The **Signing Identity** consists of a **public-private key pair** that Apple creates for us.

**46- What is the difference between property and instance variable?**

A property is a more abstract concept. An instance variable is literally just a storage slot, like a slot in a struct. Normally other objects are never supposed to access them directly. Usually a property will return or set an instance variable, but it could use data from several or none at all.

**47- How can we add UIKit for Swift Package Manager ?**

Swift Package Manager is not supporting UIKit. We can create File Template or Framework for other projects.

**48- Explain difference between SDK and Framework ?**

SDK is a set of software development tools. This set is used for creation of applications. Framework is basically a platform which is used for developing software applications. It provides the necessary foundation on which the programs can be developed for a specific platform. SDK and Framework complement each other, and SDKs are available for frameworks.

**49- What is Downcasting ?**

When we're casting an object to another type in Objective-C, it's pretty simple since there's only one way to do it. In Swift, though, there are two ways to cast -- one that's safe and one that's not .

  * **as** used for upcasting and type casting to bridged type
  * **as?** used for safe casting, return nil if failed
  * **as!** used to force casting, crash if failed. should only be used when we know the downcast will succeed.

**50- Why is everything in a do-catch block?**

In Swift, errors are thrown and handled inside of do-catch blocks.

### That's it. 😃😃😃 Thanks for reading.
