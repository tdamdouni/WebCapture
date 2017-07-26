# iOS Architecture Patterns

_Captured: 2016-03-23 at 15:09 from [medium.com](https://medium.com/ios-os-x-development/ios-architecture-patterns-ecba4c38de52)_

![](https://cdn-images-1.medium.com/max/2000/1*yAQxTFJwEKXnAr2JrOFs7w.jpeg)

#### Demystifying MVC, MVP, MVVM and VIPER

![](https://cdn-images-1.medium.com/max/2000/1*yAQxTFJwEKXnAr2JrOFs7w.jpeg)

_UPD: Slides which I presented at NSLondon available __[here_](http://slides.com/borlov/arch/fullscreen)_._

Feeling weird while doing MVC in iOS? Have doubts about switching to MVVM? Heard about VIPER, but not sure if it worth it?

Keep reading, and you will find answers to questions above, if you don’t — feel free to complain in comments.

You are about to structure your knowledge about architectural patterns in iOS environment. We’ll briefly review some popular ones and compare them in theory and practice going over a few tiny examples. Follow links if you need more details about any particular one.

_Mastering design patterns might be addictive, so beware: you might end up asking yourself more questions now than before reading this article, like these:_

_Who supposed to own networking request: a Model or a Controller?_

_How do I pass a Model into a View Model of a new View?_

_Who creates a new VIPER module: Router or Presenter?_

![](https://cdn-images-1.medium.com/max/800/1*79nWxPpKgL7JGjYp0HrT6A.png)

* * *

### Why care about choosing the architecture?

Because if you don’t, one day, debugging a huge class with dozens different things, you’ll find yourself being unable to find and fix any bugs in your class.”. Naturally, it is hard to keep this class in mind as whole entity, thus, you’ll always be missing some important details. If you are already in this situation with your application, it is very likely that:

  * This class is the UIViewController subclass.
  * Your data stored directly in the UIViewController
  * Your UIViews do almost nothing
  * The Model is a dumb data structure
  * Your Unit Tests cover nothing

And this can happen, even despite the fact that you are following Apple’s guidelines and implementing [Apple’s MVC](https://developer.apple.com/library/ios/documentation/General/Conceptual/DevPedia-CocoaCore/MVC.html) pattern, so don’t feel bad. There is something wrong with the [Apple’s MVC](https://developer.apple.com/library/ios/documentation/General/Conceptual/DevPedia-CocoaCore/MVC.html), but we’ll get back to it later.

Let’s define **features **of a _good_ architecture:

  1. Balanced **distribution** of responsibilities among entities with strict roles.
  2. **Testability **usually comes from the first feature (and don’t worry: it is easy with appropriate architecture).
  3. **Ease of use** and a low maintenance cost.

#### Why Distribution?

Distribution keeps a fair load on our brain while we trying to figure out how things work. If you think the more you develop the better your brain will adapt to understanding complexity, then you are right. But this ability doesn’t scale linearly and reaches the cap very quickly. So the easiest way to defeat complexity is to divide responsibilities among multiple entities following the **[single responsibility principle**](https://en.wikipedia.org/wiki/Single_responsibility_principle).

#### Why Testability?

This is usually not a question for those who already felt gratitude to unit tests, which **failed **after adding new features or due to refactoring some intricacies of the class. This means the tests **saved** those developers from finding issues in runtime, which might happen when an app is on a user’s device and the fix [takes a week](http://appreviewtimes.com/) to reach the user.

#### Why Ease of use?

This does not require an answer but it is worth mentioning that the best code is the code that has **never been** **written**. Therefore the less code you have, the less bugs you have. This means that desire to write **less code** should never be explained solely by laziness of a developer, and you should not favour a _smarter_ solution closing your eyes to its **maintenance cost**.

* * *

### MV(X) essentials

Nowadays we have many options when it comes to architecture design patterns:

  * [MVC](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)
  * [MVP](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93presenter)
  * [MVVM](https://en.wikipedia.org/wiki/Model_View_ViewModel)
  * [VIPER](https://www.objc.io/issues/13-architecture/viper/)

First three of them assume putting the entities of the app into one of 3 categories:

  * **Models** — responsible for the domain data or a [data access layer](https://en.wikipedia.org/wiki/Data_access_layer) which manipulates the data, think of ‘**Person**’ or ‘**PersonDataProvider**’ classes.
  * **Views** — responsible for the presentation layer (**GUI**), for iOS environment think of everything starting with ‘**UI**’ prefix.
  * **Controller/Presenter/ViewModel** — the glue or the mediator between the **Model** and the **View**, in general responsible for altering the **Model** by reacting to the user’s actions performed on the **View** and updating the **View** with changes from the **Model.**

Having entities divided allows us to:

  * understand them better (as we already know)
  * reuse them (mostly applicable to the **View** and the **Model**)
  * test them independently

_Let’s start with MV(X) patterns and get back to VIPER later._

### MVC

#### How it used to be

Before discussing Apple’s vision of MVC let’s have a look on the [traditional one](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller).

![](https://cdn-images-1.medium.com/max/600/1*E9A5fOrSr0yVmc7Kly5C6A.png)

Traditional MVC

In this case, the **View **is stateless. It is simply rendered by the **Controller** once the **Model** is changed. Think of the web page completely reloaded once you press on the link to navigate somewhere else. Although it is possible to implement the traditional MVC in iOS application, it doesn’t make much sense due to the architectural problem — all three entities are tightly coupled, each entity **knows **about the other two. This dramatically reduces reusability of each of them — that is not what you want to have in your application. For this reason, we skip even trying to write a canonical MVC example.

> Traditional MVC doesn't seems to be applicable to modern iOS development.

### Apple’s MVC

#### Expectation

![](https://cdn-images-1.medium.com/max/600/1*c0aGaDNX41qu6e8E4OEgwQ.png)

Cocoa MVC

The** Controller **is a mediator between the **View** and the **Model **so that they don’t know about each other. The least reusable is the **Controller **and this is usually fine for us, since we must have a place for all that tricky business logic that doesn’t fit into the **Model**.

In theory, it looks very straightforward, but you feel that something is wrong, right? You even heard people unabbreviating MVC as the **Massive View Controller**. Moreover, [view controller offloading](https://www.objc.io/issues/1-view-controllers/lighter-view-controllers/) became an important topic for the iOS developers. Why does this happen if Apple just took the traditional MVC and improved it a bit?

### Apple’s MVC

#### Reality

![](https://cdn-images-1.medium.com/max/800/1*PkWjDU0jqGJOB972cMsrnA.png)

Realistic Cocoa MVC

Cocoa MVC encourages you to write **Massive** View Controllers, because they are so involved in **View’s** life cycle that it’s hard to say they are separate. Although you still have ability to offload some of the business logic and data transformation to the **Model**, you don’t have much choice when it comes to offloading work to the **View, **at most of times** **all the responsibility of the **View** is to send actions to the **Controller**. The view controller ends up being a delegate and a data source of everything, and is usually responsible for dispatching and cancelling the network requests and… you name it.

How many times have you seen code like this:

The cell, which is the **View **configured directly with the **Model**, so MVC guidelines are violated, but this happens all the time, and usually people don’t feel it is wrong. If you strictly follow the MVC, then you supposed to configure the cell from the controller, and don’t pass the **Model** into the **View**, and this will increase the size of your **Controller** even more.

> Cocoa MVC is reasonably unabbreviated as the Massive View Controller.

The problem might not be evident until it comes to the **[Unit Testing**](http://nshipster.com/unit-testing/) (hopefully, it does in your project). Since your view controller is tightly coupled with the view, it becomes difficult to test because you have to be very creative in mocking views and their life cycle, while writing the view controller’s code in such a way, that your business logic is separated as much as possible from the view layout code.

Let’s have a look on the simple playground example:

MVC example

> MVC assembling can be performed in the presenting view controller

This doesn’t seem very testable, right? We can move generation of greeting into the new _GreetingModel_ class and test it separately, but we can’t test any presentation logic (although there is not much of such logic in the example above) inside the _GreetingViewController_ without calling the UIView related methods directly_ (viewDidLoad, didTapButton)_ which might cause loading all views, and this is bad for the unit testing.

In fact, loading and testing UIViews on one simulator (e.g. iPhone 4S) doesn’t guarantee that it would work fine on the other devices (e.g. iPad), so I’d recommend to remove “Host Application” from your Unit Test target configuration and run your tests without your application running on simulator.

> The interactions between the **View** and the **Controller** [aren’t really testable with Unit Tests](http://ashfurrow.com/blog/whats-worth-unit-testing-in-objective-c/)

With all that said, it might seems that Cocoa MVC is a pretty bad pattern to choose. But let’s assess it in terms of **features **defined in the beginning of the article:

  * **Distribution **—** **the** View** and the **Model** in fact separated, but the **View** and the **Controller** are tightly coupled.
  * **Testability** — due to the bad distribution you’ll probably only test your **Model.**
  * **Ease of use** — the least amount of code among others patterns. In addition everyone is familiar with it, thus, it’s easily maintained even by the unexperienced developers.

Cocoa MVC is the pattern of your choice if you are not ready to invest more time in your architecture, and you feel that something with higher maintenance cost is an overkill for your tiny pet project.

> Cocoa MVC is the best architectural pattern in terms of the speed of the development.

### MVP

#### Cocoa MVC’s promises delivered

![](https://cdn-images-1.medium.com/max/800/1*hKUCPEHg6TDz6gtOlnFYwQ.png)

Passive View variant of MVP

Doesn’t it look exactly like the Apple’s MVC? Yes, it does, and it’s name is [MVP](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93presenter) (Passive View variant). But wait a minute… Does this mean that Apple’s MVC is in fact a MVP? No, its not, because if you recall, there, the **View** is tightly coupled with the **Controller**, while the MVP’s mediator, **Presenter, **has nothing to do with the life cycle of the view controller, and the **View** can be mocked easily, so there is no layout code in the **Presenter** at all, but it is responsible for updating the **View** with data and state.

![](https://cdn-images-1.medium.com/max/800/1*mQVS34naM6TD2Fj4hU-LxA.jpeg)

> **What if I told you, the UIViewController is the View.**

In terms of the **MVP**, the UIViewController subclasses are in fact the **Views **and not** **the **Presenters. **This distinction provides superb testability, which comes at cost of the development speed, because you have to make manual data and event binding, as you can see from the example:

MVP example

#### Important note regarding assembly

The MVP is the first pattern that reveals the assembly problem which happens due to having three _actually_ separate layers. Since we don’t want the **View** to know about the **Model**, it is not right to perform assembly in presenting view controller (which is the **View**), thus we have to do it somewhere else. For example, we can make the app-wide **Router** service which will be responsible for performing assembly and the **View-to-View** presentation. This issue arises and has to be addressed not only in the MVP but also in **all the following patterns**.

Let’s look on the **features** of the MVP:

  * **Distribution** — we have the most of responsibilities divided between the **Presenter** and the **Model**, with the pretty dumb **View** (in the example above the **Model** is dumb as well).
  * **Testability** — is excellent, we can test most of the business logic due to the dumb **View**.
  * **Easy of use** — in our unrealistically simple example, the amount of code is doubled compared to the MVC, but at the same time, idea of the MVP is very clear.

> MVP in iOS means superb testability and a lot of code.

### MVP

#### With Bindings and Hooters

There is the other flavour of the MVP — the Supervising Controller MVP. This variant includes direct binding of the **View **and the **Model** while the **Presenter** (The Supervising Controller) still handles actions from the **View** and is capable of changing the **View**.

![](https://cdn-images-1.medium.com/max/600/1*bkB6Ho_G5De47IkJpaX5XQ.png)

Supervising Presenter variant of the MVP

But as we have already learned before, vague responsibility separation is bad, as well as tight coupling of the **View** and the **Model**. That is similar to how things work in Cocoa desktop development.

Same as with the traditional MVC, I don’t see a point in writing an example for the flawed architecture.

### MVVM

#### The latest and the greatest of the MV(X) kind

The [MVVM](https://en.wikipedia.org/wiki/Model_View_ViewModel) is the newest of MV(X) kind thus, let’s hope it emerged taking into account problems MV(X) was facing previously.

In theory the Model-View-ViewModel looks very good. The **View** and the **Model** are already familiar to us, but also the **Mediator,** represented as the **View Model.**

![](https://cdn-images-1.medium.com/max/800/1*uhPpTHYzTmHGrAZy8hiM7w.png)

MVVM

It is pretty similar to the MVP:

  * the MVVM treats the view controller as the **View**
  * There is no tight coupling between the **View** and the **Model**

In addition, it does **binding** like the Supervising version of the MVP; however, this time not between the **View** and the **Model**, but between the **View** and the **View Model**.

So what is the **View Model** in the iOS reality? It is basically UIKit **independent** representation of your **View** and its state. The **View Model **invokes changes in the **Model** and updates itself with the updated **Model, **and since we have a binding between the **View** and the **View Model**, the first is updated accordingly.

#### Bindings

I briefly mentioned them in the MVP part, but let’s discuss them a bit here. Bindings come out of box for the OS X development, but we don’t have them in the iOS toolbox. Of course we have the KVO and notifications, but they aren’t as convenient as bindings.

So, provided we don’t want to write them ourselves, we have two options:

  * One of the KVO based binding libraries like the [RZDataBinding](https://github.com/Raizlabs/RZDataBinding) or the [SwiftBond](https://github.com/SwiftBond/Bond)
  * The full scale [functional reactive programming](https://gist.github.com/JaviLorbada/4a7bd6129275ebefd5a6) beasts like [ReactiveCocoa](https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB4QFjAAahUKEwj2l6rZv5jJAhUFUhQKHWahCKs&url=https%3A%2F%2Fgithub.com%2FReactiveCocoa%2FReactiveCocoa&usg=AFQjCNHM-pOkluiSuPsaVwVujCDTknVFUA&sig2=54zu-ATo8vDMvtXbxZYTvQ), [RxSwift](https://github.com/ReactiveX/RxSwift/) or [PromiseKit](https://github.com/mxcl/PromiseKit).

In fact, nowadays, if you hear “MVVM” — you think ReactiveCocoa, and vice versa. Although it is possible to build the MVVM with the simple bindings, ReactiveCocoa (or siblings) will allow you to get most of the MVVM.

There is one bitter truth about reactive frameworks: the great power comes with the great responsibility. It’s really easy to mess up things when you go _reactive_. In other words, if do something wrong, you might spend a lot of time debugging the app, so just take a look at this call stack.

![](https://cdn-images-1.medium.com/max/800/1*WGIs3XQL1MtKiyApr-m9bg.png)

Reactive Debugging

In our simple example, the FRF framework or even the KVO is an overkill, instead we’ll explicitly ask the **View Model **to update using _showGreeting_ method and use the simple property for _greetingDidChange_ callback function.

MVVM example

And again back to our **feature** assessment:

  * **Distribution** — it is not clear in our tiny example, but, in fact, the MVVM’s **View** has more responsibilities than the MVP’s **View**. Because the first one updates it’s state from the **View Model **by setting up bindings, when the second one just forwards all events to the **Presenter **and doesn’t update itself**.**
  * **Testability** — the **View Model** knows nothing about the **View**, this allows us to test it easily. The **View** might be also tested, but since it is UIKit dependant you might want to skip it.
  * **Easy of use** — its has the same amount of code as the MVP in our example, but in the real app where you’d have to forward **all **events from the **View** to the **Presenter **and to update the **View **manually**, MVVM **would be much skinnier if you used bindings.

> The MVVM is very attractive, since it combines benefits of the aforementioned approaches, and, in addition, it doesn’t require extra code for the View updates due to the bindings on the View side. Nevertheless, testability is still on a good level.

* * *

### VIPER

#### LEGO building experience transferred into the iOS app design

[VIPER](https://www.objc.io/issues/13-architecture/viper/) is our last candidate, which is particularly interesting because it doesn’t come from the MV(X) category.

By now, you must agree that the granularity in responsibilities is very good. VIPER makes another iteration on the idea of separating responsibilities, and this time we have **five** layers.

![](https://cdn-images-1.medium.com/max/800/1*0pN3BNTXfwKbf08lhwutag.png)

VIPER

  * **Interactor** — contains business logic related to the data (**Entities**) or networking, like creating new instances of entities or fetching them from the server. For those purposes you’ll use some _Services_ and _Managers _which are not considered as a part of VIPER module but rather an external dependency.
  * **Presenter** — contains the UI related (but UIKit _independent_) business logic, invokes methods on the **Interactor**.
  * **Entities** — your plain data objects, not the _data access layer, _because that is a responsibility of the **Interactor**.
  * **Router** — responsible for the segues between the VIPER **modules**.

Basically, VIPER module can be a one _screen_ or the whole _user story _of your application — think of authentication, which can be one screen or several related ones. How small are your “LEGO” blocks supposed to be? — It’s up to you.

If we compare it with the MV(X) kind, we’ll see a few differences of the distribution of responsibilities:

  * **Model **(data interaction)** **logic shifted into the **Interactor **with the **Entities** as dumb data structures.
  * Only the UI representation duties of the **Controller/Presenter/ViewModel **moved into the **Presenter, **but not the data altering capabilities.
  * **VIPER **is the first pattern which explicitly addresses navigation responsibility, which is supposed to be resolved by the **Router.**

> Proper way of doing routing is a challenge for the iOS applications, the MV(X) patterns simply don’t address this issue.

The example doesn’t cover **routing** or **interaction between modules**, as those topics are not covered by the MV(X) patterns at all.

Yet again, back to the **features**:

  * **Distribution** — undoubtedly, VIPER is a champion in distribution of responsibilities.
  * **Testability** —no surprises here, better distribution — better testability.
  * **Easy of use** — finally, two above come in cost of maintainability as you already guessed. You have to write huge amount of interface for classes with very small responsibilities.

#### **So what about LEGO?**

While using VIPER, you might feel like building The Empire State Building from LEGO blocks, and that is a signal that you [have a problem](https://inessential.com/2014/03/16/smaller_please). Maybe, it’s too early to adopt VIPER for your application and you should consider something simpler. Some people ignore this and continue shooting out of cannon into sparrows. I assume they believe that their apps will benefit from VIPER at least in the future, even if now the maintenance cost is unreasonably high. If you believe the same, then I’d recommend you to try [Generamba](https://github.com/rambler-ios/Generamba) — a tool for generating VIPER skeletons. Although for me personally it feels like using an _automated targeting system_ for cannon instead of simply taking a _sling shot_.

### **Conclusion**

We went though several architectural patterns, and I hope you have found some answers to what bothered you, but I have no doubt that you realised that there is **no** **silver bullet** so choosing architecture pattern is a matter of weighting tradeoffs in your particular situation.

Therefore, it is natural to have a mix of architectures in same app. For example: you’ve started with MVC, then you realised that one particular screen became too hard to maintain efficiently with the MVC and switched to the MVVM, but only for this particular screen. There is no need to refactor other screens for which the MVC actually does work fine, because both of architectures are easily compatible.

> Make everything as simple as possible, but not simpler — Albert Einstein

#### Thank you for reading! If you liked this article, please hit ‘Recommend’ (the ❤ button) so other people can read it too :)

_Hit it me on Twitter if you want to chat: __<https://twitter.com/bohdan_orlov>_

