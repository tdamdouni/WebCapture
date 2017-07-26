# GitDo: Designing the app infrastructure

_Captured: 2015-12-31 at 22:02 from [medium.com](https://medium.com/@gitdoapp/gitdo-designing-the-app-infrastructure-3b7710c0fd81#.skoe2379f)_

![](https://cdn-images-2.medium.com/max/2000/1*WR84lFtQcb-BHRfPtaJ8NQ.jpeg)

> _Photo by Buzac Marius_

Back in May when we decided to start this new project we had a lot of doubts moving around around:

> _Should we go ahead with Swift? Should we give a try to Carthage? CoreData or Realm? What architecture should we stick to?_

Since our first commits we have changed lot of things and we are still iterating over these questions. We have suffered the pain of Swift versions, the updates of [ReactiveCocoa](https://github.com/ReactiveCocoa/ReactiveCocoa) getting ready for Swift, or even migrations in our data models. In this post I will cover that decisions that we initially took for building GitDo, what they resulted into, and the outcomes of all these technical decisions that **might be useful for iOS developers starting new projects**.

### Choosing the language: Swift

![](https://cdn-images-2.medium.com/max/800/0*xtNhe3wy-3tROwi6.png)

Before starting the project we had done a few experiments with [Swift](http://swift.org/) and it was promising for us. It brought fresh syntax to the ecosystem and it was iterating quite fast. _Something positive_ from deciding Swift as a language for the project is that the language aims to write more secure code, and helps to build a more stable. One key component here is the security with types that are detected at compilation time. No more unknown id objects that we casted to access its properties. Since the first private versions we have been using, we haven't suffered any critical crash, but failures due to a bad use of the language and crashes in Xcode, _debugging was such a pain!_. **As a negative point**I could say that choosing Swift from a so early state requires an extra effort from developers making sure the code is up to date to the last versions if you want to use the last Xcode version. But it was almost one year ago, if you're starting a new project and you have to choose the language **Swift is your best option**, with the last 2.x version, the language is getting consolidated. With Swift getting Open Source we will see new improvements coming but in my opinion not a lot of breaking changes for your code base _(let's see)_.

### API interaction

![](https://cdn-images-2.medium.com/max/800/0*2GwKZDWqM3bZjhOo.png)

[GitDo](http://gitdo.io/) interacts with [GitHub](https://github.com/) and our own backend persisting some basic user information. Existing frameworks were written in Objective-C and offered a full interaction with the GitHub API. We just needed only a subset of these requests and also new ones for interacting with our own backend. We decided in this case to go ahead with our own API repository and internal requests builders. We use [Alamofire](https://github.com/alamofire/alamofire), especially its components for request and response serializing. NSURLSession has a nice API but does not offer any component to serialize request data into NSURLRequests, wee took that one from Alamofire. We implemented Routers that are responsible for creating requests that get executed. Implementing our custom solution was a great idea since it gives us a lot of flexibility and we can modify that layer easily without having to fork 3rd party repositories but we have found some problems with the design that we are solving in future iterations:

  * **Don't map API responses into database models**: We map the responses into Realm models that are created to be inserted into the database. Thinking that your API responses map 1-to-1 with your local database models was a very bad idea. APIs are designed to be flexible, thus, they offer a very different design from what you will end up needing in your app. Implement API models that can be Swift structs with explicit names ApiIssue, ApiRepository if you don't want to have naming conflicts with other models.
  * **Models should not be responsible of mapping themselves**: Single Responsibility Principle is called, isn't it? Models contain a set of attributes and methods specific to the model itself. They should include a constructor that take the initial attributes values and set them but… they should not know how to get initialized from another data model. _Models are the result of adapting API responses. Multiple response formats can be mapped into the same model, thus, multiple mappers are required for these responses_. As soon as you start adding mappers to the model your code will smell like you're adding responsibilities that shouldn't belong to your model. **Use adapters instead!**

typealias JSON = [NSObject: AnyObject]

struct ApiIssue {

let number: Int

let title: String

init(number: Int, title: String) {

self.number = number

self.issue = issue

}

}

class Adapter<T> {

func adapt(input: JSON) -> T

}

struct ApiIssueAdapter: Adapter<Issue> {

func adapt(input: JSON) -> Issue {

// Get the attributes from the JSON.

// Initialize the ApiIssue.

// Return it.

}

}

A lot of JSON parsing libraries _(yes… there're a lot out there)_, aim to conform pre-defined protocols and using protocol extensions you are automatically getting parsing methods that you can use. This is great if you are 100% your API responses map 1-to-1 with your models, but are you?

> _We use __[SwiftyJSON_](https://github.com/SwiftyJSON/SwiftyJSON)_ as a JSON parsing library, it was one of the first libraries coming out and its approach is very simple and enough for our requirements. It's not a protocol-extension based solution like for example Genome, so it'll allow us to use them for our mappers._

  * **Top level instances**: We created top level ApiRepository that behaves as singleton instance. These instances contain information about the base URL and they know how to perform given requests returning the result as a Reactive observable object. Using global instances leads to stateful code passing and referencing these instances instance across our code base. Do we really need it? What do we need to get data from the API?
  * Resource URL.
  * REST method.
  * Parameters and its serializer.
  * User authentication token.
  * Response serializer _(optional)_.

All of them can be wrapped in something called NSURLSession that can be passed to the NSURLSession, that's all! If we want to simplify the creation of these requests we can have requests factories that build these request for you and then you can use them with Alamofire, NSURLSession or any other HTTP framework you want to.

> _The idea of having ApiManager or ApiClient in our apps became very popular in the community inspired by the idea of having singleton instances that persist client configuration and session state. When we did only have NSURLConnection with a Delegate pattern having these manager instances made sense, but nowadays? I don't think so. When you keep the session in your ApiClient and in your Keychain you don't have a single source of true, both persist what should be the "same state", what if the user logouts, are you sure the session is cleaned from everywhere? _**_Try to have single sources of true in your code and don't duplicate states_**_._

I recently implemented a framework, [HTTPCommander](https://github.com/swiftreactive/httpcommander) that offers a Reactive Command pattern for HTTP requests, aiming for this repository based solution for creating request. We will likely start moving our requests to commands.

### Reusable business logic: Frameworks

We started coding GitDo as a tool for your pocket, an iOS app, but with the idea of porting it to OSX and other platforms. It implies bundling your business, non-ui dependent logic into its own bundle. We created a project, GitDoCore with targets to build a framework for iOS and OSX. Local dependencies are available in both, iOS and OSX and we selected external dependencies that were compatible with both platforms. Here's the list:

These dependencies are resolved using with [Carthage](https://github.com/carthage/carthage) and in case of our local frameworks we have them as git submodules and added to the project as_Target Dependencies_ which allows us debugging the code in these frameworks with the main app.

**Frameworks is a great idea** not only for the fact that you can easily reuse the code but also helps you to create decoupled and reusable code from any app, you focus in the business logic itself. If you are starting a new project that will scale in the future horizontal and vertically you should consider organizing your app in multiple frameworks. Try to design your how your map of frameworks would be and simplify the dependencies as much as possible, try vertical over horizontal design and use versioning. CocoaPods local pods can be a solution but if your frameworks have external dependencies, but if they don't Xcode offers everything you need:

  1. Create a project that compiles a target framework for iOS or OSX.
  2. Add the project to your app workspace.
  3. Add the target as a _Target dependency_ of your app target.
  4. Link your app target against that framework. Voila, your AppKit, AppFoundation, or AppUIKit!

> _When Apple launched the Apple Watch and aimed developers to extract the common business logic into a framework and link them in both, your App and Watch Extensions. Did you notice how difficult it was getting it out? When you code everything in a single bundle it is relatively easy to couple everything, the context aims for that._

Check out our [Github profile](https://github.com/gitdoapp), we also open source some libraries we implemented for our app like our delightful [Kanban](https://github.com/gitdoapp/gitdokanban) that [@isaacroldan](http://twitter.com/saky) implemented on Swift.

### Dependency manager: Carthage & CocoaPods

> _Should I use CocoaPods or Carthage?_

That question has become a very common in the community. Each of them have their own pros and cons that made them suitable for some scenarios and not for another. We use both in GitDo and we are satisfied with the integration.

  * **[Carthage**](https://github.com/carthage/carthage): As you might know the core idea behind Carthage is not being a centralized dependency manager but use Github and plain the dependencies tree into a flat list of frameworks that you add to the project on your own. _We resolve and build the dependencies for you, you add them to your project_. We use it for GitDoCore and GitDoKanban dependencies _(listed above)_ and so far we haven't had any major project. Some months ago it was a bit complicated to find libraries giving support to Carthage but nowadays most of them do. Moreover they've lately improved the build script using GitHub releases to make the build process much faster.

> _The only big downside we have found in Carthage is that when Apple releases a new Xcode version that implies changes in the project structure it is up to the developers to update their libraries to _**_make them compatible_**_ with these changes. That might take a lot of time depending on the library._

  * **[CocoaPods**](https://cocoapods.org/): On the other side, the most used dependency manager. In this case it's based on a centralized solution where projects include a .podspecfile with the information about how the libraries have to be linked with your project. The big advantage of using CocoaPods is that almost all the libraries offer support to CocoaPods, the community is more opened, and in comparison with Carthage, changes in the projects structure can be solved with a CocoaPods update.

We use CocoaPods for the main project mostly iOS dependencies.

### Architecture: VIPER

Regarding the architecture of the app we decided to use VIPER. If you have not heard about VIPER before [here](https://www.objc.io/issues/13-architecture/viper/) you have a very interesting post from [objc.io](https://www.objc.io/). In our case instead of having all the components within the app bundle we moved the interactors and repositories to our GitDoCore. All the presentation layer wich is platform dependent is in the main app target.

We created interactors for every feature of the app, IssueInteractor, AccountInteractor, UpgradeInteractor, their structure was quite similar, all of them depended on the API and Database repositories and exposed its operations as Observables. Their responsibility is then:

  * Keeping the reference to the repositories that are injected when the interactor is initialized.
  * Generating Observables that encapsulate the operations.
  * They create kind of namespaces for the business logic.

### Local persistence: Realm

The first version of GitDo was designed to use Realm, we liked Realm as a persistence solution, its API was very straightforward and avoided a lot of boilerplate working with data. We implemented our models inspired in the GitHub API models but after some months of development we came up with an idea, **why not having a non-relational storage with collections?** Our relationships were very simple and we could perform multiple fetches against these collections to get the data we needed to be presented.

We got rid of Realm and started moving the core towards that solution. _Guess what happened?_ The more we implemented the more we figured out that we needed the ease of fetching relationships in plain models, accessing relationships as attributes instead of adding that extra layer building queries on these multiples collections. Our ideal idea of non-relational database became inconsistent for us and we decided to **go back to Realm again**.

We rebuilt our core with Realm in the base, taking advantage of it to add Unit Tests to GitDoCore. We have been using Realm until now and we're very happy with it. As I mentioned earlier we did something wrong mapping our API responses directly into database models. We used Realm models in this case but that couples your entire data layer to that persistence layer. My **suggestion** regarding this question is that you have three plain models, ApiModel, DatabaseModel, Entity :

**Realm or CoreData?**

If you master CoreData, and found your perfect stack and wrapper that you are happy working with, keep with it. Realm is supposed to be faster than CoreData and the API is more friendly but, _do we really need that extra of performance in our apps?_. The only thing we miss from Realm is having a NSFetchedResultsController or better Notifications to have presentation layer that automatically updates its content according to the changes that committed in the database. **Independence between database operations and fetching**.

### Reactive Interfaces

> _No more completion blocks/closures_

And last but not least our decision to go with Reactive. We had heard about Reactive Programming and we were curious about how it would be in our app, so, without thinking twice, we started building the data layer with Reactive interfaces:

  * **HTTP Requests** That are Observables, they get executed when there is a subscriber interested. It allows us to build pipelines of data that flows from the API to the database mapping, combining, and subscribing to events.
  * **Database Fetches**: Our database wrapper is pure reactive, fetch your models subscribing to an Observable, fetch them in background and map them into a thread-safe struct that you can use in the main thread to update the UI, execute a high load operation in background and subscribe to its completion or error to revert your changes in the UI.

We started falling in love, there are some downsides in Reactive programming but the magic of designing streams and combining them is worth of try. We quickly fell in love and **move RP to the presentation layer. How?** ReactiveCocoa offers custom properties whose changes you can subscribe to. Internally they use didSet statement of Swift properties to notify the changes. If you combine that with the MVVM you can synchronize the view with the model changes.

> _RxSwift also Observable attributes and some other wrappers around Foundation patterns and UIKit components._

**Reactive Programming design examples are presented in the book ****[Reactive Programming in your Swift Apps**](https://leanpub.com/reactiveprogrammingswift)** that I am writing. The book introduces RP core ideas, the base components of RxSwift and ReactiveCocoa and get you through a real example implementing a GitHub client app.**
