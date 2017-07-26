# 50 iOS Interview Questions And Answers Part 3

_Captured: 2017-03-25 at 19:44 from [medium.com](https://medium.com/ios-os-x-development/50-ios-interview-questions-and-answers-part-3-3fad146b6c3d#.j2hmba4z5)_

![](https://cdn-images-1.medium.com/max/2000/1*fgy4_Lt8x-fxjrh8idaX9w.jpeg)

I decided to write a final piece on some of the questions that was asked to me in iOS interviews. Check out **[Part 1**](https://medium.com/ios-os-x-development/ios-interview-questions-13840247a57a) and **[Part 2**](https://medium.com/p/50-ios-interview-questions-and-answers-part-2-45f952230b9f) if you haven't already :).

**1- What is your favorite app and why ?**

Below are my real answers. These apps are my favorites. Here are the reasons:

  * **[Sleep Cycle**](http://t.co/FJgZ3RrsR3)** -** It has Apple health integration, wake up mood, world statistics and Philips Hue integration along with useful piechart report tool.
  * **[WaterMinder**](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0ahUKEwjm69a6mKnSAhVojVQKHdV5DMwQFggjMAE&url=http%3A%2F%2Fwaterminderapp.com%2F&usg=AFQjCNEofzBxOR0OjPDgH5ClWaapBRA8wQ&sig2=iK_ZrjS5RJdgF5x3dzVnXQ)** -** I can follow my daily water intake history. I can forget drinking water while coding. But this app notifies me for drinking water and you can enter the kinds of liquids as well (coffee counts!) .
  * **Facebook -All in one place, I **do not need to install another app such as sports, messaging, voip, weather or news.
  * **Medium -**I can easily find pure, native, organic, up-to-date and point shot technical articles and learn about the visions of companies and developers.

**2- What kind of JSONSerialization have ReadingOptions ?**

  * **_mutableContainers_** Specifies that arrays and dictionaries are created as variables objects, not constants.
  * **_mutableLeaves_** Specifies that leaf strings in the JSON object graph are created as instances of variable String.
  * **_allowFragments_** Specifies that the parser should allow top-level objects that are not an instance of Array or Dictionary.

**3- Explain subscripts ?**

Classes, structures, and enumerations can define subscripts, which are shortcuts for accessing the member elements of a collection, list, or sequence.

**4- What is DispatchGroup ?**

`DispatchGroup`_ allows for aggregate synchronization of work. We can use them to submit multiple different work items and track when they all complete, even though they might run on different queues. This behavior can be helpful when progress can't be made until all of the specified tasks are complete. -- __[Apple's Documentation_](https://developer.apple.com/reference/dispatch/dispatchgroup)

The most basic answer: If we need to wait on a couple of asynchronous or synchronous operations before proceeding, we can use `DispatchGroup.`

**5- What is RGR ( Red -- Green -- Refactor ) ?**

![](https://cdn-images-1.medium.com/max/600/1*aWKa228igWcNrjdh9G8FLQ.jpeg)

Red, Green and Refactor are stages of the TDD (Test Driven Development).

  1. **_Red:_** Write a small amount of test code usually no more than seven lines of code and watch it fail.
  2. **_Green:_** Write a small amount of production code. Again, usually no more than seven lines of code and make your test pass.
  3. **_Refactor:_** Tests are passing, you can make changes without worrying. Clean up your code. There are great workshop notes [here](https://gist.github.com/orkoden/201f811570582fab2b5b).

**6- Where do we use Dependency Injection ?**

We use a storyboard or xib in our iOS app, then we created IBOutlets. IBOutlet is a property related to a view. These are injected into the view controller when it is instantiated, which is essentially a form of Dependency Injection.

There are forms of dependency injection: constructor injection, property injection and method injection.

**7- Please explain types of notifications.**

There are two type of notifications: Remote and Local. Remote notification requires connection to a server. Local notifications don't require server connection. Local notifications happen on device.

**8- When is a good time for dependency injection in our projects?**

There is a few guidelines that you can follow.

Rule 1. Is Testability important to us? If so, then it is essential to identify external dependencies within the class that you wish to test. Once dependencies can be injected we can easily replace real services for mock ones to make it easy to testing easy.

Rules 2. Complex classes have complex dependencies, include application-level logic, or access external resources such as the disk or the network. Most of the classes in your application will be complex, including almost any controller object and most model objects. The easiest way to get started is to pick a complex class in your application and look for places where you initialize other complex objects within that class.

Rules 3. If an object is creating instances of other objects that are shared dependencies within other objects then it is a good candidate for a dependency injection.

**9- What kind of order functions can we use on collection types ?**

Check out for [more details](https://medium.com/@mimicatcodes/simple-higher-order-functions-in-swift-3-0-map-filter-reduce-and-flatmap-984fa00b2532#.1sbfvw5gj) about Map, filter, reduce and flatMap!

**10- What allows you to combine your commits ?**

`git squash`

**11- What is the difference ANY and ANYOBJECT ?**

According to Apple's Swift documentation:

  * **_Any_**_ can represent an instance of any type at all, including function types and optional types._
  * **_AnyObject _**_can represent an instance of any class type._

**12- Please explain SOAP and REST Basics differences ?**

Both of them helps us access Web services. **[SOAP**](https://en.wikipedia.org/wiki/SOAP) relies exclusively on XML to provide messaging services. SOAP is definitely the heavyweight choice for Web service access. Originally developed by Microsoft.

**[REST**](https://en.wikipedia.org/wiki/Representational_state_transfer) ( Representational State Transfer ) provides a lighter weight alternative. Instead of using XML to make a request, REST relies on a simple URL in many cases. REST can use four different HTTP 1.1 verbs (GET, POST, PUT, and DELETE) to perform tasks.

**13- What is you favorite Visualize** **Chart library ?**

**[Charts**](https://github.com/danielgindi/Charts) has support iOS,tvOS,OSX The Apple side of the cross platform MPAndroidChart.

**[Core Plot**](https://github.com/core-plot/core-plot) is a 2D plotting framework for macOS, iOS, and tvOS

**14- Which git command allows us to find bad commits ?**

`git bisect`

**15- Are you using ****[CharlesProxy**](http://www.charlesproxy.com/)** ? Why or why not ?**

If I need a proxy server I am using CharlesProxy. With CharlesProxy we can support binary protocols, rewriting and traffic throttling.

**16- Could you explain Associatedtype ?**

If you want to create Generic Protocol we can use associatedtype. For [more details](https://krakendev.io/blog/generic-protocols-and-their-shortcomings) check this out.

**17- Which git command saves your code without making a commit ?**

`git stash`

**18- Whats is you favorite Swift programming book ?**

My recommendations are <https://www.appcoda.com/swift/> and <https://store.raywenderlich.com/>

**19- What is Hashable ?**

[Hashable](https://developer.apple.com/reference/swift/hashable) allows us to use our objects as keys in a dictionary. So we can make our custom types.

**20- When do you use optional chaining vs. if let or guard ?**

We use optional chaining when we do not really care if the operation fails; otherwise, we use `if let` or `guard`. This answer comes straight from the Expanded Edition of [Parsing JSON in Swift](https://el2.convertkit-mail.com/c/4zuqel0rwteh52mkl/3ydpyg/aHR0cHM6Ly9yb2FkZmlyZXNvZnR3YXJlLmNvbS9wYXJzaW5nLWpzb24taW4tc3dpZnQv).

Using the question mark operator like this is called optional chaining. Apple's [documentation](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/OptionalChaining.html#//apple_ref/doc/uid/TP40014097-CH21-XID_368) explains it like this:

> Optional chaining_ is a process for querying and calling properties, methods, and subscripts on an optional that might currently be nil. If the optional contains a value, the property, method, or subscript call succeeds; if the optional is nil, the property, method, or subscript call returns nil. Multiple queries can be chained together, and the entire chain fails gracefully if any link in the chain is nil._

**21- How many different ways to pass data in Swift ?**

There are many different ways such as Delegate, KVO, Segue, and NSNotification, Target-Action, Callbacks.

**22- How do you follow up clean code for this project ?**

I follow style guide and coding conventions for Swift projects of [Github](https://github.com/github/swift-style-guide) and [SwiftLint](https://github.com/realm/SwiftLint).

**23- What is new in iOS 10 ?**

  * SiriKit
  * Proactive Suggestions
  * Integrating with the Messages App
  * User Notifications
  * App Extensions
  * CallKit
  * Speech Recognition
  * App Search Enhancements

**24- What's the difference optional between **`**nil**`** and **`**.None**`**?**

There is no difference. `**Optional.None**` (`**.None**` for short) is the correct way of initializing an optional variable lacking a value, whereas `**nil**` is just syntactic sugar for `**.None**`. Check this [out](https://www.raywenderlich.com/110982/swift-interview-questions-answers).

**25- Are you using another IDE for iOS Project ?**

**26- What is VIPER Architecture ?**

Continuous Integration allows us to get early feedback when something is going wrong during application development. There are a lot of continuous integration tools available.

#### Self hosted server

#### Cloud solutions

**28- What is the difference Delegates and Callbacks ?**

The difference between delegates and callbacks is that with delegates, the NetworkService is telling the delegate "There is something changed." With callbacks, the delegate is observing the NetworkService.

**29- Did you use design tool or protoype tool previously ?**

If you do not know any design tool you would be able to start today.

[Sketch](http://sketch.land/) \+ [Marvel](https://marvelapp.com/) are good team members. If you want to create prototype with coding, [Framer](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwjdlOLqkafSAhVKOSYKHcC8AFgQFggaMAA&url=https%3A%2F%2Fframer.com%2F&usg=AFQjCNEoDwEOWkneQHp2EePYdUEzEZFO_g&sig2=DX3Fh9hhkEfsALCG2H12eg&bvm=bv.148073327,d.eWE) is a good choice.

**30- Do you know Back End development ?**

Depends. I have experienced PARSE and I am awarded FBStart. I decided to learn pure back end. You have two choices. Either you can learn node.js + express.js and mongodb. **OR, y**ou can learn **[Vapor**](https://vapor.codes) or **[Kitura**](http://www.kitura.io).

Don't you like or use Firebase?
    
    
    **Firebase **doesn't have a path for macOS X developers.

If you want to learn Firebase, please just follow one month of [Firebase Google Group](https://groups.google.com/forum/#!forum/firebase-talk).

**31- How do you test new ideas ?**

Check out this [book](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwjnksTtlqfSAhUDRCYKHet-D6wQFggdMAA&url=http%3A%2F%2Fwww.thesprintbook.com%2F&usg=AFQjCNHxu7RmLoxG8z5LbNZjBSdBrI_zKQ&sig2=IarXT7JKwzZodvzHtSrwdA&bvm=bv.148073327,d.eWE), very amazing recommendations.

**32- What is the disadvantage to hard-coding log statements ?**

**First**, when you start to log. This starts to accumulate. It may not seem like a lot, but every minute adds up. By the end of a project, those stray minutes will equal to hours.

**Second**, Each time we add one to the code base, we take a risk of injecting new bugs into our code.

**33- What is Pointer ?**

A pointer is a direct reference to a memory address. Whereas a variable acts as a transparent container for a value, pointers remove a layer of abstraction and let you see how that value is stored.

**34- Have you worked as a contractor before?**

You should try. You can benefit from it. I think this is good experience to manage a client, networking and improve task management skills.

**35- What is pair programming?**

Pair programming is a tool to share information with junior developers. Junior and senior developer sitting side-by-side this is the best way for the junior to learn from senior developers.

**36- Explain blocks**

**Blocks** are a way of defining a single task or unit of behavior without having to write an entire Objective-C class. they are anonymous functions.

**37- What is Keychain ?**

Keychain is an API for persisting data securly in iOS App. There is a good library - **[Locksmith**](https://github.com/matthewpalmer/Locksmith)

**38- What is the biggest changes in UserNotifications ?**

  * We can add audio, video and images.
  * We can create custom interfaces for notifications.
  * We can manage notifications with interfaces in the notification center.
  * New Notification extensions allow us to manage remote notification payloads before they're delivered.

**39- Explain the difference between atomic and nonatomic synthesized properties**

**atomic : **It is the default behaviour. If an object is declared as atomic then it becomes thread-safe. Thread-safe means, at a time only one thread of a particular instance of that class can have the control over that object.

**nonatomic:** It is not thread-safe. We can use the nonatomic property attribute to specify that synthesized accessors simply set or return a value directly, with no guarantees about what happens if that same value is accessed simultaneously from different threads. For this reason, it's faster to access a nonatomic property than an atomic one.

**40- Why do we use ****[availability**](https://developer.apple.com/library/prerelease/content/documentation/Swift/Conceptual/Swift_Programming_Language/Attributes.html)** attributes ?**

Apple wants to support **one system version back**, meaning that we should support iOS9 or iOS8. [Availability Attributes](https://www.raywenderlich.com/139077/availability-attributes-swift) lets us to support previous version iOS.

**41- How could we get device token ?**

There are two steps to get device token. First, we must show the user's permission screen, after we can register for remote notifications. If these steps go well, the system will provide device token. If we uninstall or reinstall the app, the device token would change.

**42- What is Encapsulation ?**

Encapsulation is an object-oriented design principles and hides the internal states and functionality of objects. That means objects keep their state information private.

**43- What is big-o notation ?**

An algorithm is an impression method used to determine the working time for an input **N** size. The big-o notation grade is expressed by the highest value. And the **big-o notation **is finding the answer with the question of **O(n)**. Here is a **[cheat sheet**](http://bigocheatsheet.com) and **[swift algorithm club**](https://github.com/raywenderlich/swift-algorithm-club)**. **For example;

> For Loops big-o notation is O(N). Because For Loops work n times.

> Variables (var number:Int = 4) big-o notation is O(1).

**44- How do you evaluate your performance?**

  * StackOverflow repo.
  * Number of users reading my articles and blog posts.
  * Public speaking on MeetUp.

**45- What is UML Class Diagrams?**

UML Class Diagram is a set of rules and notations for the specification of a software system, managed and created by the Object Management Group.

**46- Explain throw**

We are telling the compiler that it can throw errors by using the throws keyword. Before we can throw an error, we need to make a list of all the possible errors you want to throw.

**47- What is Protocol Extensions?**

We can adopt protocols using extensions as well as on the original type declaration. This allows you to add protocols to types you don't necessarily own.

**48- What are The Trends on iOS App Development in 2017 ?**

  * Swift Coding
  * Augmented Reality
  * Internet of Things
  * Security improvement
  * Growth in enterprise apps
  * Growth in hybrid technologies ( react native )

**49- Explain Selectors in ObjC**

Selectors are Objective-C's internal representation of a method name.

**50- What is Remote Notifications attacment's limits ?**

We can be sent with video or image with push notification. But maximum payload is 4kb. If we want to sent high quality attachment, we should use **Notification Service Extension**.

### My recommendations

### That's it. 😃😃😃 Thanks for reading. I hope all these tools will help you to improve your productivity.

  
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
