# Testing Without Mocks: A Pattern Language

_Captured: 2018-05-18 at 14:44 from [dzone.com](https://dzone.com/articles/james-shore-testing-without-mocks-a-pattern-langua?edition=376324&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-05-18)_

When programmers use test-driven development (TDD), the code they test interacts with other parts of the system that aren't being tested. To test those interactions, and to prevent the other code from interfering with their tests, programmers often use mock objects or other test doubles. However, this approach requires additional integration tests to ensure the system works as a whole, and it can make structural refactorings difficult.

This pattern language1 describes a way of testing object-oriented code without using mocks. It avoids the downsides of mock-based testing, but it has tradeoffs of its own.

(The structure of this article was inspired by Ward Cunningham's [CHECKS Pattern Language of Information Integrity](http://c2.com/ppr/checks.html), which is a model of clarity and usefulness.)

For example code demonstrating these ideas, see [my example on GitHub](https://github.com/jamesshore/testing-without-mocks-example).

  * _No broad tests required._ The test suite consists entirely of "[narrow](https://martinfowler.com/bliki/IntegrationTest.html)" tests that are focused on specific concepts. Although broad integration tests can be added as a safety net, their failure indicates a gap in the main test suite.
  * _Easy refactoring._ Object interactions are considered implementation to be encapsulated, not behavior to be tested. Although the consequences of object interactions are tested, the specific method calls aren't. This allows structural refactorings to be made without breaking tests.
  * _Readable tests._ Tests follow a straightforward "arrange, act, assert" structure. They describe the externally-visible behavior of the unit under test, not its implementation. They can act as documentation for the unit under test.
  * _No magic._ Tools that automatically remove busywork, such as dependency-injection frameworks and auto-mocking frameworks, are not required.
  * _Fast and deterministic._ The test suite only executes "slow" code, such as network calls or file system requests, when that behavior is explicitly part of the unit under test. Such tests are organized so they produce the same results on every test run.
  * _Test-specific production code._ Some code needed for the tests is written as tested production code, particularly for infrastructure classes. It requires extra time to write and adds noise to class APIs.
  * _Hand-written stub code._ Some third-party infrastructure code has to be mimicked with hand-written stub code. It can't be auto-generated and takes extra time to write.
  * _Sociable tests._ Although tests are written to focus on specific concepts, the units under test execute code in their dependencies. (Jay Fields coined the term "[sociable tests](https://martinfowler.com/bliki/UnitTest.html)" for this behavior.) This can result in multiple tests failing when a bug is introduced.
  * _Not a silver bullet._ Code must be written with careful thought to design. Design mistakes are inevitable and this necessitates continuous attention to design and refactoring.

### Architectural Patterns

Testing without mocks requires careful attention to the dependencies in your codebase. These patterns help establish the ground rules.

Our goal is to create a test suite consisting entirely of "narrow" tests, with no need for "broad" end-to-end tests. But most narrow tests don't test that the system is wired together correctly. _Therefore:_

When testing the interactions between an object and its dependencies, inject real dependency instances (not test doubles) into the unit under test. Don't test the dependencies' behavior itself, but do test that the unit under test uses the dependencies correctly.

This will create a strong linked chain of tests. Each test will overlap with dependencies' tests and dependents' tests. The test suite as a whole should cover your entire application in a fine overlapping mesh, giving you the coverage of broad tests without the need to write them.

To avoid constructing the entire dependency chain, use [Zero-Impact Instantiation](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#zero-impact) and [Parameterless Instantiation](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#instantiation). To isolate your unit under test, use [Collaborator-Based Isolation](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#isolation) and [Nullable Infrastructure](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#nullable-infrastructure). To test code that depends on infrastructure, use [Configurable Responses](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#configurable-responses), [Send State](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#send-state), [Send Events](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#send-events), and [Behavior Simulation](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#behavior-simulation).

Because we aren't using mocks to isolate our dependencies, it's easiest to test code that doesn't depend on infrastructure (external systems such as databases, file systems, and services). However, a typical layered architecture puts infrastructure at the bottom of the dependency chain:

_Therefore:_

Structure your application so that infrastructure and logic are peers under the application layer, with no dependencies between Infrastructure and Logic. Coordinate between them at the application layer with a [Logic Sandwich](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#logic-sandwich) or [Traffic Cop](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#traffic-cop).

Build the bottom two layers using [Infrastructure Patterns](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#infrastructure-patterns) and [Logic Patterns](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#logic-patterns).

Although A-Frame Architecture is a nice way to simplify application dependencies, it's optional. You can test code that mixes infrastructure and logic using [Infrastructure Wrappers](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#infrastructure-wrappers) and [Nullable Infrastructure](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#nullable-infrastructure).

To build a new application using A-Frame Architecture, [Grow Evolutionary Seeds](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#grow-seeds). To convert an existing layered architecture, [Climb the Ladder](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#climb-ladder).

When using an [A-Frame Architecture](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#a-frame-arch), the infrastructure and logic layers can't communicate with each other. But the logic layer needs to read and write data controlled by the infrastructure layer. _Therefore:_

Implement the top-level code as a "logic sandwich," where data is read by the infrastructure layer, then processed by the logic layer, then written by the infrastructure layer. Repeat as needed. Each piece can then be tested independently.

This simple algorithm can handle sophisticated needs if put into a loop with a stateful logic layer.

For applications with complicated infrastructure, use a [Traffic Cop](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#traffic-cop) instead.

The [Logic Sandwich](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#logic-sandwich) boils infrastructure down into simple `infrastructure.readData()` and `infrastructure.writeData()`abstractions. Applications with complex infrastructure may not be a good fit for this approach. _Therefore:_

Instead of asking the infrastructure for its data, use the [Observer pattern](https://en.wikipedia.org/wiki/Observer_pattern) to send events from the infrastructure layer to the application layer. For each event, implement a Logic Sandwich. In some cases, your application code might need a bit of logic of its own.

Be careful not to let your Traffic Cop turn into a [God Class](http://wiki.c2.com/?GodClass). If it gets complicated, better infrastructure abstractions might help. Sometimes taking a less "pure" approach and moving some Logic code into the Infrastructure layer can simplify the overall design. In other cases, splitting the application layer into multiple classes, each with its own [Logic Sandwich](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#logic-sandwich) or simple Traffic Cop, can help.

One popular design technique is [outside-in design](https://www.amazon.com/gp/product/0321503627), in which an application is programmed by starting with the externally-visible behavior of the application, then working your way into the details.

This is typically done by writing a broad integration test to describe the externally-visible behavior, then using narrow unit tests to define the details. But we want to avoid broad tests. _Therefore:_

Use [evolutionary design](http://www.jamesshore.com/Agile-Book/incremental_design.html) to grow your application from a single file. Choose a simple end-to-end behavior as a starting point and test-drive a single class to implement a trivial version of that behavior. Hardcode one value that would normally come from the Infrastructure layer, don't implement any significant logic, and return the result to your tests rather than displaying in a UI. This class forms the seed of your Application layer.

Next, implement a barebones [Infrastructure Wrapper](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#infrastructure-wrappers) for the one infrastructure value you hardcoded. Code just enough infrastructure to provide one real result to your application layer class. Don't worry about making it robust or reliable yet. This Infrastructure Wrapper class forms the seed of your Infrastructure layer.

Before integrating your new Infrastructure class into your Application layer class, implement [Nullable Infrastructure](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#nullable-infrastructure). Then modify your application layer class to use the infrastructure wrapper, injecting the Null version in your tests.

Next, do the same for your UI. Choose one simple output mechanism that your application will use (such as rendering to the console, the DOM, or responding to a network request) and implement a barebones Infrastructure Wrapper for it. Add support for Nullable Infrastructure and modify your application layer tests and code to use it.

Now your application tests serve the same purpose as broad end-to-end tests: they document and test the externally-visible behavior of the application. Because they inject Null application dependencies, they're narrow tests, not broad tests, and they don't communicate with external systems. That makes them fast and reliable. They're also [Overlapping Sociable Tests](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#sociable-tests), so they provide the same safety net that broad tests do.

At this point, you have the beginnings of a [walking skeleton](http://alistair.cockburn.us/Walking+skeleton): an application that works end-to-end, but is far from complete. You can evolve that skeleton to support more features. Choose some aspect of your code that's obviously incomplete and test-drive a slightly better solution. Repeat forever.

At some point, probably fairly early, your Application layer class will start feeling messy. When it does, look for a concept that can be factored into its own class. This forms the seed of your Logic layer. As your application continues to grow, continue refactoring so that class collaborations are easy to understand and responsibilities are clearly defined.

To convert existing code to an [A-Frame Architecture](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#a-frame-arch), [Climb the Ladder](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#climb-ladder) instead.

Most pre-existing code you encounter will be designed with a layered architecture, where Logic code has Infrastructure dependencies. Some of this code will be difficult to test or resist refactoring. _Therefore:_

Refactor problem code into a miniature A-Frame Architecture. Start at the lowest levels of your Logic layer and choose a single method that depends on one clearly-defined piece of infrastructure. If the Infrastructure code is intertwingled with the Logic code, disintertwingle it by factoring out an [Infrastructure Wrapper](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#infrastructure-wrappers).

When the Infrastructure code has been separated from the rest of the code, the method will act similarly to an Application layer class: it will have a mix of logic and calls to infrastructure. Make this code easier to refactor by rewriting its tests to use [Nullable Infrastructure](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#nullable-infrastructure) dependencies instead of mocks. Then factor all the logic code into methods with no infrastructure dependencies.

At this point, your original method will have nothing left but a small [Logic Sandwich](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#logic-sandwich): a call or two to the infrastructure class and a call to the new logic method. Now eliminate the original method by inlining it to its callers. This will cause the logic sandwich to climb one step up your dependency chain.

Repeat until the class no longer has any dependencies on infrastructure. At that point, review its design and refactor as desired to better fit the [Logic Patterns](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#logic-patterns) and your application's needs. Continue with the next class.

Climbing the Ladder takes a lot of time and effort, so do it gradually, as part of your normal work, rather than all at once. Focus your efforts on code where testing without mocks will have noticeable benefit. Don't waste time refactoring code that's already easy to maintain, regardless of whether it uses mocks.

When building a new system from scratch, [Grow Evolutionary Seeds](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#grow-seeds) instead.

[Overlapping Sociable Tests](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#sociable-tests) instantiate their dependencies, which in turn instantiate their dependencies, and so forth. If instantiating this web of dependencies takes too long or causes side effects, the tests could be slow, difficult to set up, or fail unpredictably. _Therefore:_

Don't do significant work in constructors. Don't connect to external systems, start services, or perform long calculations. For code that needs to connect to an external system or start a service, provide a `connect()` or `start()`method. For code that needs to perform a long calculation, consider [lazy initialization](https://martinfowler.com/bliki/LazyInitialization.html). (But even complex calculations aren't likely to be a problem, so profile before optimizing.)

As you refactor your application, method signatures will change. If your code is well-designed, this won't be a problem for production code, because most methods will only be used in a few places. But tests can have many duplicated method and constructor calls. When you change those methods or constructors, you'll have a lot of busywork to update the tests. _Therefore:_

If a file has a lot of tests that call a specific method, provide a proxy function for that method. Similarly, if it has a lot of tests that instantiate a class, provide a factory method. Program the proxies and factories so their parameters are all optional. That way you can add additional parameters in the future without breaking existing tests.

When using [A-Frame Architecture](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#a-frame-arch), the application's Logic layer has no infrastructure dependencies. It represents pure computation, so it's fast and deterministic. To qualify for the Logic layer, code can't talk to a database, communicate across a network, or touch the file system.2 Neither can its tests or dependencies. Any code that breaks these rules belongs in the Application layer or Infrastructure layer instead. Code that modifies global state _can_ be put in the Logic layer, but it should be avoided, because then you can't parallelize your tests.

Pure computation is easy to test. The following patterns make it even easier.

This list inspired by Michael Feathers' [unit testing rules](https://www.artima.com/weblogs/viewpost.jsp?thread=126923).

Logic layer computation can only be tested if the results of the computation are visible to tests. _Therefore:_

Prefer pure functions where possible. Pure functions' return values are determined only by their input parameters.

When pure functions aren't possible, prefer immutable objects. The state of immutable objects is determined when the object is constructed, and never changes afterwards.

For methods that change object state, provide a way for the change in state to be observed, either with a getter method or an [event](https://en.wikipedia.org/wiki/Observer_pattern).

In all cases, avoid writing code that explicitly depends on (or changes) the state of dependencies more than one level deep. That makes test setup difficult, and it's a sign of poor design anyway. Instead, design dependencies so they completely encapsulate their next-level-down dependencies.

Third-party code doesn't always have [Easily-Visible Behavior](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#visible-behavior). It also tends to introduce breaking API changes with new releases, or simply stop being maintained. _Therefore:_

Wrap third-party code in code that you control. Ensure your application's use of the third-party code is mediated through your wrapper. Write your wrapper's API to match the needs of your application, not the third-party code, and add methods as needed to provide Easily-Visible Behavior. (This will typically involve writing getter methods to expose deeply-buried state.) When the third-party code introduces a breaking change, or needs to be replaced, modify the wrapper so no other code is affected.

Frameworks and libraries with sprawling APIs are more difficult to wrap, so prefer libraries that have a narrowly-defined purpose and a simple API.

If the third-party code interfaces with an external system, use an [Infrastructure Wrapper](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#infrastructure-wrappers) instead.

Multi-level dependency chains are difficult to set up in tests. Dependency injection (DI) frameworks work around the problem, but we're avoiding magic like DI frameworks. _Therefore:_

Ensure that all Logic classes can be constructed without providing any parameters (and without using a DI framework). In practice, this means that most objects instantiate their dependencies in their constructor by default, although they may also accept them as optional parameters.

For some classes, a parameterless constructor won't make any sense. For example, an immutable "Address" class would be constructed with its street, city, and so forth. For these sorts of classes, provide a test-only factory method. The factory method should provide overridable defaults for mandatory parameters.

The factory method is easiest to maintain if it's located in the production code next to the real constructors. It should be marked as test-specific and should be simple enough to not need tests of its own.

[Overlapping Sociable Tests](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#sociable-tests) ensure that any changes to the semantics of a unit's dependencies will cause that unit's tests to break, no matter how far down the dependency chain they may be. On the one hand, this is nice, because we'll learn when we accidentally break something. On the other hand, this could make feature changes terribly expensive. We don't want a change in the rendering of addresses to break hundreds of unrelated reports' tests. _Therefore:_

Call dependencies' methods to help define test expectations. For example, if you're testing a InventoryReport that includes an address in its header, don't hardcode "123 Main St." as your expectation for the report header test. Instead, call Address.renderAsOneLine() as part of defining your test expectation.

This provides the best of both worlds: Overlapping Sociable Tests ensure that your application is wired together correctly and Collaborator-Based Isolation allows you to change features without modifying a lot of tests.

The Infrastructure layer contains code for communicating with the outside world. Although it may contain some logic, that logic should be focused on making infrastructure easier to work with. Everything else belongs in the Application and Logic layers.

Infrastructure code is unreliable and difficult to test because of its dependencies on external systems. The following patterns work around those problems.

In the Logic layer, you can design your code to avoid complex, global state. In the Infrastructure layer, your code deals with nothing else. Testing infrastructure code that depends on other infrastructure code is particularly difficult. _Therefore:_

Keep your infrastructure dependencies simple and straightforward. For each external system--service, database, file system, or even environment variables--create one wrapper class that's responsible for interfacing with that system. Design your wrappers to provide a crisp, clean view of the messy outside world, in whatever format is most useful to the Logic and Application layers.

Avoid creating complex webs of dependencies. In some cases, high-level Infrastructure classes may depend on generic, low-level classes. For example, a LoginClient might depend on RestClient. In other cases, high-level infrastructure classes might unify multiple low-level classes, such as a DataStore class that depends on a RelationalDb class and a NoSqlDb class. Other than these sorts of simple one-way dependency chains, design your Infrastructure classes to stand alone.

Test your Infrastructure Wrappers with [Focused Integration Tests](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#focused-integration-tests) and [Paranoic Telemetry](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#paranoic-telemetry). Enable them to be used in other tests by creating [Nullable Infrastructure](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#nullable-infrastructure).

Ultimately, Infrastructure code talks over a network, interacts with a file system, or involves some other communication with an external system. Its correctness depends on communicating properly. _Therefore:_

Test your external communication for real. For file system code, check that it reads and writes real files. For databases and services, access a real database or service. Make sure that your test systems use the same configuration as your production environment. Otherwise, your code will fail in production when it encounters subtle incompatibilities.

Run your focused integration tests against test systems that are reserved exclusively for one machine's use. It's best if they run locally on your development machine, and are started and stopped by your tests or build script. If you share test systems with other developers, you'll experience unpredictable test failures when multiple people run the tests at the same time.

You won't be able to get a local test system for every external system your application uses. When you can't, use a [Spy Server](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#spy-server) instead.

Some high-level Infrastructure classes will use lower-level classes to do the real work, such as a LoginClient class that uses a RestClient class to make the network call. They can [Fake It Once You Make It](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#fake-it).

Some external systems are too unreliable, expensive, or difficult to use for [Focused Integration Tests](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#focused-integration-tests). It's one thing to run dozens of tests against your local file system every few minutes; quite another to do that to your credit card gateway. _Therefore:_

Create a test server that you can run locally. Program it to record requests and respond with pre-configured results. Make it very simple and generic. For example, all REST-based services should be tested by the same HTTPS Spy Server.

To test against the Spy Server, start by making a real call to your external system. Record the call and its results and paste them into your test code (or save them to a file). In your test, check that the expected request was made to the Spy Server and the response was processed correctly.

External systems can change out from under you. In the case of cloud-based services, it can happen with no warning. A Spy Server won't be able to detect those changes. To protect yourself, implement [Paranoic Telemetry](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#paranoic-telemetry).

This is a complete example of a real-world Node.js HTTPS Spy Server. You can use this code in your own projects:

External systems are unreliable. The only thing that's certain is their eventual failure. File systems lose data and become unwritable. Services return error codes, suddenly change their specifications, and refuse to terminate connections. _Therefore:_

Instrument the snot out of your infrastructure code. Assume that everything will break eventually. Test that every failure case either logs an error and sends an alert, or throws an exception that ultimately logs an error and sends an alert. Remember to test your code's ability to handle requests that hang, too.

All these failure cases are expensive to support and maintain. Whenever possible, use [Testable Libraries](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#testable-libraries) rather than external services.

(An alternative to Paranoic Telemetry is [Contract Tests](https://martinfowler.com/bliki/ContractTest.html), but they're not paranoid enough to catch changes that happen between test runs.)

[Focused Integration Tests](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#focused-integration-tests) are slow and difficult to set up. Although they're useful for ensuring that infrastructure code works in practice, they're overkill for code that depends on that infrastructure code. _Therefore:_

Program each infrastructure class with a factory method, such as "createNull()," that disables communication with the external system. Instances should behave normally in every other respect. This is similar to how [Null Objects](https://en.wikipedia.org/wiki/Null_object_pattern) work. For example, calling LoginClient.createNull().getUserInfo("...") would return a default response without actually talking to the third-party login service.

The createNull() factory is production code and should be test-driven accordingly. Ensure that it doesn't have any mandatory parameters. (Nullable Infrastructure is the Infrastructure layer equivalent of [Parameterless Instantiation](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#instantiation).)

To implement Nullable Infrastructure cleanly, use an [Embedded Stub](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#embedded-stub). To test code that has infrastructure dependencies, use [Configurable Responses](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#configurable-responses), [Send State](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#send-state), [Send Events](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#send-events), and [Behavior Simulation](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#behavior-simulation).

In order for [Nullable Infrastructure](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#nullable-infrastructure) to be useful to tests, null instances need to disable the external system while running everything else normally. The obvious approach is to use a flag and bunch of "if" statements, but that's a recipe for spaghetti. _Therefore:_

Stub out the third-party library that performs external communication rather than changing your infrastructure code. In the stub, implement the bare minimum needed to make your infrastructure code run. Ensure you don't overbuild the stub by test-driving it through your infrastructure code's public interface. Put the stub in the same file as your infrastructure code so it's easy to remember and update when your infrastructure code changes.

Some high-level infrastructure classes depend on low-level infrastructure classes to talk to the outside world. For example, a LoginClient class might use a RestClient class to perform its network calls. The high-level code is typically more concerned with parsing and processing responses than the low-level communication details. However, there will still be some communication details that need to be tested. _Therefore:_

Use a mix of [Focused Integration Tests](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#focused-integration-tests) and [Nullable Infrastructure](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#nullable-infrastructure) in your high-level infrastructure classes. For tests that check if external communication is done properly, use a Focused Integration Test (and possibly a [Spy Server](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#spy-server)). For parsing and processing tests, use simpler and faster [Nullable Infrastructure](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#nullable-infrastructure) dependencies.

This Node.js JavaScript example demonstrates two tests of a LoginClient. The LoginClient depends on a RestClient. Note how the network request test uses a Spy Server and the error handling test uses a Null RestClient.

Application and high-level infrastructure tests need a way of configuring the data returned by their infrastructure dependencies. _Therefore:_

Allow infrastructure methods' responses to be configured with an optional "responses" parameter to the [Nullable Infrastructure](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#nullable-infrastructure)'s createNull() factory. Pass it through to the class's [Embedded Stub](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#embedded-stub) and test-drive the stub accordingly.

When your infrastructure class has multiple methods that can return data, give each one its own createNull() parameter. Used named and optional parameters so they can be added and removed without breaking existing tests.

If a method needs to provide multiple different responses, pass them as an array. However, this may be a sign that your Infrastructure layer is too complicated.

To test code that uses infrastructure to send data, use [Send State](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#send-state) or [Send Events](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#send-events). To test code that responds to infrastructure events, use [Behavior Simulation](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#behavior-simulation).

Application and high-level infrastructure code use their infrastructure dependencies to send data to external systems. They need a way of checking that the data was sent. _Therefore:_

For infrastructure methods that send data, and provide no way to observe that the data was sent, store the last sent value in a variable. Make that data available via a method call.

If you need more than one send result, or you can't store the sent data, use [Send Events](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#send-events) instead. To test code that uses infrastructure to get data, use [Configurable Responses](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#configurable-responses). To test code that responds to infrastructure events, use [Behavior Simulation](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#behavior-simulation).

When you test code that uses infrastructure dependencies to send large blobs of data, or sends data multiple times in a row, [Send State](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#send-state) will consume too much memory. _Therefore:_

Rather than storing the sent data in a variable, use the [Observer pattern](https://en.wikipedia.org/wiki/Observer_pattern) to emit an event when your infrastructure code sends data. Include the data as part of the event payload. When tests need to make assertions about the data that was sent, they can listen for the events.

Send Events require complicated test setup. To make your tests easier to read, create a helper function in your tests that listens for send events and stores their data in an array. Doing this in production could cause a memory leak, but it's not a problem in your tests because the memory will be freed when the test ends.

This JavaScript example involves Application layer code for a real-time web application. When a browser connects, the server should send it all the messages the server had previously received. This test uses Send Events to check that the server sends those messages when a new browser connects.

To test code that uses infrastructure to get data, use [Configurable Responses](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#configurable-responses). To test code that responds to infrastructure events, use [Behavior Simulation](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#behavior-simulation).

Some external systems will push data to you rather than waiting for you to ask for it. Your application and high-level infrastructure code need a way to test what happens when their infrastructure dependencies generate those events. _Therefore:_

Add methods to your infrastructure code that simulate receiving an event from an external system. Share as much code as possible with the code that handles real external events, while remaining convenient for tests to use.

To test code that uses infrastructure to get data, use [Configurable Responses](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#configurable-responses). To test code that uses infrastructure to send data, use Send Stream or [Send Events](http://www.jamesshore.com/Blog/Testing-Without-Mocks.html#send-events).

These patterns are an effective way of writing code that can be tested without test doubles, DI frameworks, or end-to-end tests.
