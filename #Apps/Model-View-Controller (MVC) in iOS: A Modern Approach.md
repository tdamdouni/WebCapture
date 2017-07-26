# Model-View-Controller (MVC) in iOS: A Modern Approach

_Captured: 2016-06-26 at 13:08 from [www.raywenderlich.com](https://www.raywenderlich.com/132662/mvc-in-ios-a-modern-approach)_

![MVC-feature](https://cdn2.raywenderlich.com/wp-content/uploads/2016/06/MVC-feature-250x250.png)

Every new iOS developer is exposed to a huge amount of information that is crucial to master: a new language, new frameworks, and Apple's recommended architectural pattern: [Model-View-Controller](https://developer.apple.com/library/ios/documentation/General/Conceptual/DevPedia-CocoaCore/MVC.html), or MVC for short.

Getting up to speed with iOS development can be a daunting task, and more often than not, developers don't pay MVC enough attention, sometimes leading to major headaches down the road.

This article will help you avoid the common mistake of an app that's become too difficult to extend. You'll learn a modern approach of what to do--and what not to do--as you use MVC to build out your app, using best practices learned through the school of hard knocks.

By the end of this article, you'll know how to use modern best practices in your apps and prevent structural problems before they become a headache. Let's go!

## MVC 101

_Note:_ If you already know the concept of MVC, feel free to skip ahead to the next section, where we'll start getting into best practices.

From a high level, MVC is as straightforward as its name. It's made up of three layers: the model, the view and the controller.

  * The _Model_ is where your data resides. Things like persistence, model objects, parsers and networking code normally live there.
  * The _View_ layer is the face of your app. Its classes are typically reusable, since there aren't any domain-specific logic in them. For example, a `UILabel` is a view that presents text on the screen, and it's easily reusable.
  * The _Controller_ mediates between the view and the model, typically via the delegation pattern. In the ideal scenario, the controller entity won't know the concrete view it's dealing with. Instead, it will communicate with an abstraction via a protocol. A classic example is the way a `UITableView` communicates with its data source via the `UITableViewDataSource` protocol.

When you put everything together, it looks like this:

![diagram-mvc](https://cdn5.raywenderlich.com/wp-content/uploads/2016/04/diagram-mvc-480x241.png)

Simple, right?

As they say, the devil is in the details. When you're in the process of applying MVC, things can get tricky, as you'll see.

[Apple's MVC documentation](https://developer.apple.com/library/ios/documentation/General/Conceptual/CocoaEncyclopedia/Model-View-Controller/Model-View-Controller.html) explains these layers in detail and can give you a theoretical understanding that will help you avoid potential pitfalls.

From a practical perspective, though, it leaves a lot to be desired. So instead of talking theory, let's talk shop.

## What Goes Where?

Although it's easy to understand the theory of MVC, it sometimes is tricky to figure out what goes where from a practical standpoint. Let's take some time to focus on this.

### The View Layer

When a user interacts with your app, they are interacting with the view layer. The view is considered the "dumb" part of your app, since it shouldn't contain any business logic. In code terms, you'll normally see:

  * `UIView` subclasses. These range from a basic `UIView` to complex custom UI controls.
  * A `UIViewController` (arguably). Since a `UIViewController` is strongly coupled with its own root `UIView` and its different cycles (`loadView`, `viewDidLoad`), I personally consider it to be part of this layer, but not everyone agrees.
  * Animations and `UIViewController` transitions.
  * Classes that are part of UIKit/AppKit, Core Animation and Core Graphics. 

Typical [code smells](https://en.wikipedia.org/wiki/Code_smell) found in this layer manifest in different ways, but boil down to including anything unrelated to UI in your view layer. A classic code smell is making a network call from a `UIViewController`.

It's tempting to put a bunch of code in your `UIViewController` and be done with it, so you can meet that deadline. Don't do it! In the short term, you might save a couple of minutes, but in the long term, you could lose hours looking for a bug, or have trouble when you want to reuse code inside one view controller in another.

![Devil_details](https://cdn2.raywenderlich.com/wp-content/uploads/2016/05/Devil_details.png)

Use the following as a checklist when inspecting your view layer:

  * Does it interact with the model layer?
  * Does it contain any business logic?
  * Does it try to do anything not related to UI?

If you answer "yes" to any of these questions, you probably have an opportunity to clean up and refactor.

Of course, these rules aren't written in stone and sometimes you'll need to bend them. Nonetheless, it's important to pay them respect.

Finally, if you write these classes well, you can almost always reuse them. If you don't believe me, just look at the number of UI components on GitHub!

### The Controller Layer

The controller layer is the least reusable part of your app, because it involves your domain-specific rules. It should be no surprise that what makes sense in your app probably wouldn't make sense in someone else's.

Usually, you'll see classes from this layer deciding things like:

  * What should be accessed first: the persistence or the network?
  * How often should you refresh the app?
  * What should the next screen be and in what circumstances?
  * If the app goes to the background, what should be cleaned?

You should think of the controller layer as the brain of the app: It decides what happens next. Usually you'll want to heavily test these classes to make sure everything works as expected.

_An Example_

Now that you have a better understanding of the controller layer, let's see it in action with a simple example.

_Note:_ Optionally, if you'd like to see how this fits into the context of an app as you follow along, download this simple [example app](https://github.com/raywenderlich/mvc-modern-approach) I've made for you.

Imagine you have a `UIViewController` subclass that wants to know the list of WWDC attendees this year. To achieve this, it makes use of a controller class. Since Apple's been preaching that we should always start with a protocol, you'll do that here:
    
    
    enum UIState {
        case Loading
        case Success([Attendee])
        case Failure(Error)
    }
     
    protocol WWDCAttendesDelegate: class {
        var state: UIState { get set}
    }

The idea is that you'll initially set `state` to `Loading`, then update it when the list of WWDC attendees is successfully loaded (or fails).

Since you don't want the `UIViewController` to handle the response, it will use a separate object (`WWDCAttendeesUIController`) that will implement `WWDCAttendesDelegate`. This separation, allows you to easily test `WWDCAttendeesUIController` independently.

The next step is to create an abstraction for the controller, so you can inject it into your `UIViewController`:
    
    
    protocol WWDCAttendeesHandler: class {
     
        var delegate: WWDCAttendesDelegate? { get set }
        func fetchAttendees()
    }

From the point of view of the `UIViewController` subclass, the implementation would look like this:
    
    
    init(attendeesHandler: WWDCAttendeesHandler) {
     
        self.attendeesHandler = attendeesHandler
        super.init(nibName: nil, bundle: nil)
    }
     
    override func viewDidLoad() {
        super.viewDidLoad()
     
        atteendeesUIController = WWDCAttendeesUIController(view: view, tableView: tableView)
        attendeesHandler.delegate = atteendeesUIController
     
        attendeesHandler.fetchAttendees()
    }

This approach will put the fetching action on the `UIViewController` side, but leave the response handling to the `WWDCAttendeesUIController`:
    
    
    extension WWDCAttendeesUIController: WWDCAttendesDelegate {
     
        func update(newState: UIState) {
     
            switch(state, newState) {
     
            case (.Loading, .Loading): loadingToLoading()
            case (.Loading, .Success(let attendees)): loadingToSuccess(attendees)
     
            default: fatalError("Not yet implemented \(state) to \(newState)")
            }
        }
     
        func loadingToLoading() {
            view.addSubview(loadingView)
            loadingView.frame = CGRect(origin: .zero, size: view.frame.size)
        }
     
        func loadingToSuccess(attendees: [Attendee]) {
            loadingView.removeFromSuperview()
            tableViewDataSource.dataSource = attendees.map(AttendeeCellController.init)
        }
    }

You can see the `WWDCAttendeesUIController` as the UI brain, while the `WWDCAttendeesController` as the business logic brain.

Wow, that wasn't hard! But this example begs the question: Who creates the controller?

I recommend always making the controller injectable -- so the owner of your `UIViewController` would provide the controller. This has two main benefits:

  * _It's easily testable._ You can simply pass any object that complies with the `FetchNumberOfTickets` protocol.
  * _The layers are cleanly decoupled._ This helps in defining responsibilities, which leads to an overall healthier code base.
![not_bad](https://cdn2.raywenderlich.com/wp-content/uploads/2016/04/not_bad-1.png)

### The Model Layer

The model layer is not as self-explanatory as it may seem.

As you would expect, it will have your model objects, potentially covering most of the layer surface. In the tickets example, you would have a `Ticket` struct that would live in your model.

I find the following components to also be part of the model layer:

  * _Network Code._ The shape should be something like [this](https://github.com/MailOnline/Reactor/blob/master/Reactor/Core/Network/Network.swift). Ideally, you'd only use a single class for network communication across your entire app.
  * _Persistence Code._ You would implement this with Core Data or simply by saving an `NSData` blob directly to disk.
  * _Parsing Code._ Any objects that parse network responses and the like should be included in the Model layer as well.

While the model objects and the parser are domain-specific, the network code will be highly reusable.

The controller will then use all the elements in your model layer to define the flow of information in your app.

## MVC: Massive View Controller?

For those of you who don't know, a `UIViewController` that starts to acquire responsibilities that aren't its to have is colloquially known as a Massive View Controller. It begins by accumulating things like networking and parsing, and eventually gets so big you lose track of the information flow. Even worse, you can't really refactor in a safe manner, because this approach makes it very difficult to write unit tests.

It's difficult to come up with a quick solution to the Massive ViewController, so it often winds up becoming technical debt. This is a common problem in the iOS community, and it's how MVC got a bad reputation.

But the Massive View Controller is not your destiny!

As a rule of the thumb, a `UIViewController` shouldn't have more than 130 lines of code. That might seem difficult to achieve, but if you're disciplined, it's easy. Here are the guidelines I usually follow:

  * Most of the code inside the view controller is related to its root `UIView` customization.
  * It should be responsible for hooking up the controller (remember `FetchNumberOfTickets`) with its root `UIView`--for example, calling a controller's method on an `IBAction`.
  * Things like `UITableDataSource`, `UITableViewDelegate` and other delegates shouldn't be inside it. If they are, it's impossible to test them.
  * If you think your view controller has too many properties, you can either break it down into multiple view controllers or create a custom `UIView`. 

These are just guidelines. Sometimes your `UIViewController` is so simple, it might not be worth it to create all those entities. Keep in mind that for each new responsibility you give your view controller, you give up the opportunity to test and reuse that piece of code.

## What About MVVM?

Model-View-ViewModel, or MVVM, is an MVC derivation. Conceptually, it's similar. The biggest difference is in the communication between layers, and instead of a controller, you use a view model.

In practice, MVVM shines when it has an FRP framework to support it. Since the model is now observed by the view model and the view model by the view, the FRP paradigm becomes a natural choice to manage the information flow. This leads to a better separation between layers, which translates in decoupled components that are easy to test.

Bottom line: architecture is important, but in my opinion the right programming paradigm will influence more the overall quality of your code. It's also important to note, that most often that not, you will have in the same app different approaches. This includes both architecture and paradigm. You might think this will disrupt consistency inside the codebase, but you should always use the right tool for the job.

## Where to Go From Here?

MVC has been around longer than many of us and it's not going anywhere. Although it's gained a bad reputation lately, it shouldn't take the blame for mistakes we make in our apps.

MVC is a blueprint that leaves quite a bit for you to decide. You should see it as instructions, for a recipe. Nevertheless, there a ton of things that it leaves out for you to decide. This is both bad and good. It's bad, because if you don't have the necessary experience, you might make the wrong call and it's good, because it gives you flexibility in your design.

No architecture, old or new, is a silver bullet, and you should always focus on [good engineering principles](https://en.wikipedia.org/wiki/SOLID_\(object-oriented_design\)) first.

If I could give advice to my younger self regarding MVC, I would say this:

  1. First, understand the responsibility of each object. Once you know that, start thinking about the code.
  2. Don't underestimate dependency injection; it will do wonders for your code, both in terms of reusability and testability.
  3. Try as much as possible to keep your `UIViewController` free of logic. The cleaner it is, the easier it will be to reason about its behavior.

For an example of a small project that illustrates the best practices discussed in this article, check out this [example app](https://github.com/raywenderlich/mvc-modern-approach) I made. It's a simple example showcasing some of the best practices I've discussed here.

Here's to a good working relationship with MVC--if you follow these principles, you can make MVC your friend rather than your enemy.

If you have any comments or questions, please join the forum discussion below!
