# Choosing the Correct Architecture for an iOS Application

_Captured: 2017-06-24 at 00:32 from [dzone.com](https://dzone.com/articles/choosing-the-correct-architecture-for-ios-applicat?edition=305134&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-23)_

### Knowing the ins and outs of design patterns such as MVC, MVP, and MVVM is essential to create a stable, reliable iOS app.

[Launching an app doesn't need to be daunting.](https://dzone.com/go?i=204132&u=http%3A%2F%2Finfo.perfectomobile.com%2Febook-mobile-app-testing-best-practices.html%3Futm_source%3Dbgm-dzonespon) Whether you're just getting started or need a refresher on mobile app testing best practices, [this guide is your resource!](https://dzone.com/go?i=204132&u=http%3A%2F%2Finfo.perfectomobile.com%2Febook-mobile-app-testing-best-practices.html%3Futm_source%3Dbgm-dzonespon) Brought to you in partnership with [Perfecto](https://dzone.com/go?i=204132&u=http%3A%2F%2Finfo.perfectomobile.com%2Febook-mobile-app-testing-best-practices.html%3Futm_source%3Dbgm-dzonespon).

Design patterns and architectures are very important today in creating a successful and reliable application and there I stumbled upon a question about choosing the architecture for creating the iOS application. The main objective is to explain what features make good architecture. And what having good architecture can do for your application.

## Why Do We Care About Choosing the Correct Architecture?

It's because if we don't care, then one day it will be a nightmare to find and fix bugs. We can probably ignore architecture in simple applications like "Hello World," or ones with a small number of screens and lines of code where you can simply end write all your code in your View Controller. But what if it's not just Hello World? Then we might end up with a huge pile of code in the View Controller, making it a "Messy View Controller" or "Massive View Controller." This can happen even if we follow [Apple's MVC](https://developer.apple.com/library/content/documentation/General/Conceptual/DevPedia-CocoaCore/MVC.html) guidelines.

## What Can Be Considered Good Architecture?

Let's define some of the features of good architecture:

  * Balanced distribution among entities.

  * Measurability.

  * Testability.

  * Ease of use and maintainability.

### Why Balanced Distribution Among Entities?

The easiest way to reduce complexity is to divide the responsibilities among different entities. It should follow the [Single Responsibility principle](https://en.wikipedia.org/wiki/Single_responsibility_principle). A class should have one and only one reason to change.

Let's consider an example about a class that creates a pdf in a view and prints that report. Now imagine a class that can perform these two changes. First, it loads the data coming from the web server or database, and second, it changes the user interface format. Both these tasks are entirely different from one other; the first one is a substantial change, while setting the user interface is entirely a cosmetic change. The single responsibility principle says that the two are entirely separate responsibilities which should be independent.

It would be bad to couple two things for entirely different reasons and that's why the balance of distribution comes in. Distributing the class will be focused on a single concern and make the class robust.

### Why Testability?

Testability does not mean testing. An application is testable when there is an effective test strategy used to verify the conformance of some implementation with regards to its specification. Writing automated tests becomes very easy because at the time you complete one composition root, it becomes ready to test independently. These tests save developers finding and fixing the bugs before the application is handed to the user's device.

### Why Ease of Use?

The less code you write, the fewer chances it has of going wrong. The more code you have, the more places there are for bugs. If the code is bad, it rots, so one should not look for quick solutions while keeping your eyes closed to the later maintenance cost. Even if a new developer starts to work, it should not feel lost in your code.

Now we have many design patterns that we can apply based on requirements of our project, like

  * MVC

  * MVP

  * MVVM

### MVC

Model-View-Controller is a widely used pattern for creating software applications. Most Cocoa applications and frameworks created by Apple have implemented this design pattern.

![MVC](https://dzone.com/storage/temp/5670547-byacl.png)

  * The model is where your domain data resides, which manages reading and writing data and persisting states. Things like persistence, networking codes, model objects, and parsers which manipulate the data stay here.

  * The view is the face of your application. This is responsible for the the presentation (User Interface) and handles user interactions.

  * The controllers act as glue, or mediators between the model layers and presentation layers (Model and View). It alters the model by reacting to actions performed by the user on view and updating the view that comes from the changes in the model.

Now, what is wrong with MVC? If we try building complex applications, it gets difficult. Over time, more and more code gets transferred to the controllers, making them more fragile and bloated. The controllers are so tightly coupled with the views that if we try to change something in the view, we have to go back to the controller and make changes there, too. This violates balanced distribution among entitied features.

Who comes to the rescue for MVC now?

### MVP

MVP stands for Model-View-Presenter; Cocoa's MVC promise is fulfilled here. It fulfills testability surface and clean separation of view and model.

![Image title](https://dzone.com/storage/temp/5673058-byacl.png)

  * The model is the same as MVC's model. It manages reading and writing data and persisting states. There is no change.

  * Here, the view part includes both view and view controllers. The view here delegates user interactions to the presenter. The view in MVP is as dumb as possible and contains no logic that can query the model.

  * The presenter contains the logic that handles user interactions. It does not have any UIKit dependencies. The responsibility of the presenter is to communicate with the model, convert the data to a user friendly format, then update the view.

Here in MVP, the view controllers are considered the subclasses of view, not presenter. Now the responsibility is divided between the model and presenter as the view is dumb and contains no logic, fulfilling the balanced distribution feature. The code is much cleaner now and can easily do unit tests for the presenter.

We cannot say that MVP is a perfect pattern or that one should follow MVP without going with the requirements of the application. MVP is not suitable for simple screen applications; it would lead to boilerplate code written to get the interface of the view to start working.

### MVVM

MMVM is one of the latest of Model-View patterns. It stands for Model-View-ViewModel. Here, the mediator is ViewModel. It is an implementation of observer design pattern where any changes in the model are represented in the view and viewmodel. Nowadays, when we think of using MVVM, we think of Reactive Cocoa, although it is possible to build the MVVM pattern with simple bindings, too. MVVM includes:

  * Model: This represents a data model that our app consumes. This class declares the properties to manage business data similar to the above two design patterns.

  * View: It is similar to MVP. The MVVM view includes both view and view controllers. It simply holds data and delegates everything to the model.

  * ViewModel: The viewmodel acts as a link between the model and view. It is responsible for wrapping up the model and preparing the observable data needed by the view.

One can use MVVM by keeping in mind some points:

  1. The view is dumb it should only know how to present data.

  2. The controller knows nothing about the model.

  3. The model knows nothing about the viewmodel.

  4. The viewmodel owns the model.

  5. The view controller owns the view.

  6. The controller owns the view model and interacts with the model layer through the ViewModel.

The MMVM satisfies almost all the features of good architecture.The responsibility is now distributed among the view model and view. One of the advantage of using MMVM is testability as view model has nothing to do with the view so each entity can be separately tested.

But as we know, "With great power comes great responsibility." It could be very easy to mess up with Reactive Cocoa; if you did something wrong, then you have to spend a lot of time debugging and fixing the issue. This pattern cannot be used for simple linited screen applications otherwise it could end up making your code more complex and difficult to maintain for new developers.

I hope this artice helps you in understanding the importance of choosing correct architecture and design patterns based on requirements and scale of your application.

[Keep up with the latest DevTest Jargon](https://dzone.com/go?i=204133&u=http%3A%2F%2Finfo.perfectomobile.com%2Fmobile-devtest-dictionary.html%3Futm_source%3Dmmg-dzonespon) with the latest Mobile DevTest Dictionary. Brought to you in partnership with [Perfecto](https://dzone.com/go?i=204133&u=http%3A%2F%2Finfo.perfectomobile.com%2Fmobile-devtest-dictionary.html%3Futm_source%3Dmmg-dzonespon).
