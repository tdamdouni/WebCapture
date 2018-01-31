# SOLID Principles Applied To Swift

_Captured: 2017-05-03 at 01:10 from [dzone.com](https://dzone.com/articles/solid-principles-applied-to-swift-1?oid=twitter&utm_content=bufferd324d&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

SOLID is an acronym created by [Robert C. Martin (Uncle Bob)](https://en.wikipedia.org/wiki/Robert_Cecil_Martin). It represents five principles of object-oriented programming: **S**ingle responsibility, **O**pen/Closed, **L**iskov Substitution, **I**nterface Segregation, and **D**ependency Inversion.

Thanks to these principles, you can solve the main problems of a bad architecture:

  * **Fragility**: A change may break unexpected parts--it is very difficult to detect if you don't have good test coverage.
  * **Immobility**: A component is difficult to reuse in another project--or in multiple places of the same project--because it has too many coupled dependencies.
  * **Rigidity**: A change requires a lot of efforts because affects several parts of the project.

Of course, as Uncle Bob pointed out in [his article](https://sites.google.com/site/unclebobconsultingllc/getting-a-solid-start) that these are not strict rules, but guidelines to improve the quality of your architecture.

Principles will not turn a bad programmer into a good programmer. Principles have to be applied with judgment. If they are applied by rote, it is just as bad as if they are not applied at all. You must be smart enough to understand when to apply these principles.

## Principles

### The Single Responsibility Principle (SRP)

"There should never be more than one reason for a class to change." -_[SRP: The Single Responsibility Principle_](https://web.archive.org/web/20150202200348/http://www.objectmentor.com/resources/articles/srp.pdf)

Every time you create/change a class, you should ask yourself: How many responsibilities does this class have?

Let's see an example:
    
    
            let array = parse(data: data)
    
    
        private func parse(data: Data) -> [String] {

How many responsibilities does this class have?

`Handler` retrieves the data from the API (1), parses the API response, creating an array of `String`, (2) and saves the array in a database (3).

Once you consider that you have to use in the same class [Alamofire](https://github.com/Alamofire/Alamofire) for the API request, [ObjectMapper](https://github.com/Hearst-DD/ObjectMapper) for the parsing and the [CoreData stack](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/CoreData/InitializingtheCoreDataStack.html) to save the data in the database, you will start understanding the smell of this class.

You can solve this problem moving the responsibilities down to little classes:
    
    
        init(apiHandler: APIHandler, parseHandler: ParseHandler, dbHandler: DBHandler) {
    
    
            let array = parseHandler.parse(data: data)
    
    
        func parse(data: Data) -> [String] {
    
    
        func saveToDB(array: [String]) {

This principle helps you to keep your classes as clean as possible. Moreover, in the first example you couldn't test `requestDataToAPI`, `parse` and `saveToDB` directly, since those were private methods. After the refactor, you can easily do it testing `APIHandler`, `ParseHandler` and `DBHandler`.

## The Open-Closed Principle (OCP)

"Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification." -_[The Open-Closed Principle](https://web.archive.org/web/20150905081105/http://www.objectmentor.com/resources/articles/ocp.pdf)_

If you want to create a class that is easy to maintain, it must have two important characteristics:

  * **Open for extension**: You should be able to extend or change the behaviors of a class without efforts.
  * **Closed for modification**: You must extend a class without changing the implementation.

You can achieve these characteristics thanks to the abstraction.

As an example, we have a class `Logger` which iterates an array of `Cars` and prints the details of each car:
    
    
                Car(name: "Batmobile", color: "Black"),
    
    
                Car(name: "SuperCar", color: "Gold"),
    
    
                Car(name: "FamilyCar", color: "Grey")
    
    
                print(car.printDetails())
    
    
        init(name: String, color: String) {
    
    
        func printDetails() -> String {
    
    
            return "I'm \(name) and my color is \(color)"

If you want to add the possibility to print also the details of a new class, we should change the implementation of `printData` every time we want to log a new class--breaking OCP:
    
    
                Car(name: "Batmobile", color: "Black"),
    
    
                Car(name: "SuperCar", color: "Gold"),
    
    
                Car(name: "FamilyCar", color: "Grey")
    
    
                print(car.printDetails())
    
    
                print(bicycles.printDetails())
    
    
        init(name: String, color: String) {

We can solve this problem creating a new protocol `Printable`, which will be implemented by the classes to log. Finally, `printData` will print an array of `Printable`.

In this way, we create a new abstract layer between `printData` and the class to log, allowing the print of other classes like `Bicycle` and without changing the `printData` implementation.

## The Liskov Substitution Principle (LSP)

"Functions that use pointers of references to base classes must be able to use objects of derived classes without knowing it." -_[The Liskov Substitution Principle](https://web.archive.org/web/20150905081111/http://www.objectmentor.com/resources/articles/lsp.pdf)_

Inheritance may be dangerous and you should use [composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) to avoid a messy codebase, even more so if you use inheritance in an improper way.

This principle can help you to use inheritance without messing it up. Let's see the main problems which break LSP:

### Preconditions Changes

We have a class `Handler`, it has the responsibility to save a string in a cloud service. Then, the business logic changes, and, sometimes, you must save the string just if its length is greater than five. Therefore, we decide to create a subclass `FilteredHandler`:

This example breaks LSP because, in the subclass, we add the precondition that `string` must have a length greater than 5. A client of `Handler` doesn't expect that `FilteredHandler` has a different precondition, since it should be the same for `Handler` and all its subclasses.

We can solve this problem getting rid of `FilteredHandler` and adding a new parameter to inject the minimum length of characters to filter:

### Postconditions Changes

We have a project where we must compute the area of some rectangle objects--so we create the class `Rectangle`. After a couple of months, we need to compute also the area of square objects--so we decide to create a subclass `Square`. Since in a square we need just a side to compute the area--and we don't want to override the computation of `area`--we decide to assign the same value of `width` to `length`:

With this approach, we break LSP because if the client has the current method:

The result should always be the same in the both calls:

Instead, the first one prints `10` and the second one `4`. This means that, with this inheritance, we have just broken the postcondition of the `width` setter which is: `((width == newValue) && (height == height))`.

We can solve it using a protocol with a method `area`, implemented by `Rectangle` and `Square` in different ways. Finally, we change the `printArea` parameter type to accept an object which implement this protocol:

## The Interface Segregation Principle (ISP)

"Clients should not be forced to depend upon interfaces that they do not use." -_[The Interface Segregation Principle](https://web.archive.org/web/20150905081110/http://www.objectmentor.com/resources/articles/isp.pdf)_

This principle introduces one of the problems of object-oriented programming: the fat interface.

A interface is called "fat" when has too many members/methods, which are not cohesive and contain more information than we really want. This problem can affect both classes and protocols.

### Fat Interface (Protocol)

We start with the protocol `GestureProtocol` with a method `didTap`:

After some time, you have to add new gestures to the protocol and it becomes:

Our `SuperButton` is happy to implement the methods which it needs:

The problem is that our app has also a `PoorButton` which needs just `didTap`. It must implement methods which it doesn't need, breaking ISP:

We can solve the problem using little protocols instead of a big one:

### Fat Interface (Class)

We can use, as an example, an application which has a collection of playable videos. This app has the class `Video` which represents a video of the user's collection:

And we inject it in the video player:

Unfortunately, we are injecting too much information in the method `play`, since it needs just `url`, `title` and `duration`.

You can solve this problem using a protocol `Playable` with just the information the player needs:

This approach is very useful also for the unit test. We can create a stub class which implements the protocol `Playable`:

## The Dependency Inversion Principle (DIP)

"A. High-level modules should not depend upon low-level modules. Both should depend upon abstractions. B. Abstractions should not depend upon details. Details should depend upon abstractions." -_[The Dependency Inversion Principle](https://web.archive.org/web/20150905081103/http://www.objectmentor.com/resources/articles/dip.pdf)_

This principle is the right one to follow if you believe in reusable components.

DIP is very similar to Open-Closed Principle: the approach to use, to have a clean architecture, is decoupling the dependencies. You can achieve it thanks to abstract layers.

Let's consider the class `Handler`, which saves a string in the filesystem. It calls, internally, `FilesystemManager` which manages how to save the string in the filesystem:

`FilesystemManager` is the low-level module and it's easy to reuse in other projects. The problem is the high-level module `Handler`, which is not reusable because is tightly coupled with `FilesystemManager`. We should be able to reuse the high-level module with different kind of storages like a database, cloud, and so on.

We can solve this dependency using a protocol `Storage`. In this way, `Handler` can use this abstract protocol without caring of the kind of storage used. With this approach, we can change easily from a filesystem to a database:

This principle is very useful also for testing. You can easily use a stub class--which implements `Storage`--and test if `handle` calls the method `save` of the `Storage` object injected:

If you follow SOLID principles judiciously, you can increase the quality of your code. Moreover, your components can become more maintainable and reusable.

The mastering of these principles is not the last step to become a perfect developer; actually, it's just the beginning. You will have to deal with different problems in your projects, understand the best approach and, finally, check if you're breaking some principles.

You have three enemies to defeat: Fragility, Immobility, and Rigidity. SOLID principles are your weapons. Enjoy!
