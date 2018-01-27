# An Overview of Architectural Design Patterns for iOS Developers

_Captured: 2018-01-25 at 15:37 from [dzone.com](https://dzone.com/articles/an-overview-of-architectural-design-patterns-for-i?edition=355136&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=mobile%202018-01-25)_

A widespread bad practice in app development is to start building an app without following any app architecture patterns. While they aren't absolutely a need, but an architectural design pattern based development can help you build a really solid foundation for your app.

Ignoring architecture patterns also brings in clustered, cluttered code and badly organized modules. This goes against the principle of separation of concerns that we usually follow.

Apps that do not follow an architectural design pattern are tightly coupled, difficult to change, and are more prone to bugs. With this article, we will review some common app architecture patterns and their underlying characteristics, evaluating their strengths and weaknesses.

Following are some commonly used architectural design patterns in iOS app development.

## Model-View-Controller Pattern for iOS Development

By default, iOS supports the Model-View-Controller architectural pattern, which is best suited for simpler applications. MVC was the first architectural concept by Apple and defines a better separation of concerns.

As the name implies, it is divided into three parts:

![Image title](https://dzone.com/storage/temp/7798193-1-pkwjdu0jqgjob972cmsrna.png)

**Model** \- In iOS, the Model is a collection of different classes that represent the business logic (i.e. business model and data model). The model also defines the rules by which your data can be altered and manipulated.

**View** \- View represents user interfaces through which users interact and view the app functionalities. For example, in iOS, your view can be the UI button. The View displays data which is received from the controller as input.

**Controller** \- The Controller is a mediator between model and view. It is the actual manager which decides how a model should be represented in a view. In iOS, the Controller is represented by **UIViewController**. The main function of the controller is to get input from users via the View and process the data through the model, thereby passing back the results to the View.

### Concerns With the MVC Pattern in iOS

Although MVC is suitable for developing mobile applications in iOS, at the same time, it also contains some underlying concerns related to the bloated ViewControllers. The problem is that ViewControllers in iOS are overburdened with a lot of responsibilities, from handling presentation layer logic to network logic as your application's complexity grows. As a result of this, the code becomes difficult to maintain and test.

## Model-View-Presenter in iOS App Development

![Image title](https://dzone.com/storage/temp/7798197-1-hkucpehg6tdz6gtolnfywq.png)

> _The MVP pattern in iOS consists of:_

**Model -** The Model remains the same as it was in MVC.   
**View -** The View in MVP consists of both UIView and UIViewController. The View hands over any user interaction to the presenter.   
**Presenter** \- The controller in MVC is replaced by Presenter in MVP. Now the presenter holds the responsibility of addressing all user events on the behalf of View. The presenter communicates with the model layer, converting the data to a UI-friendly format, and updates the View.

## Model-View-View-Model in iOS

![Image title](https://dzone.com/storage/temp/7798198-1-uhppthyztmhgrazy8him7w.png)

The MVVM design pattern is an improved version of MVC. In MVVM, the View and Controller are united to form a view with an additional introduction of ViewModel, which now handles the presentation logic.

The ViewModel introduce changes in Model and updates itself regularly with it. Furthermore, since View is bound strongly with View Model, the communication between Model and ViewModel with ease.

This decoupling results in thin, clean ViewControllers, which introduces more readability and maintainability due to the better-defined separation of concerns.

### Data-Binding in MVVM

A common question which arises in MVVM is that if ViewModel and View both don't contain any references, then how does the UI get updated in MVVM?

The answer to this question is Data Binding, which connects UI elements to the observable properties of the ViewModel.

Although MVVM in iOS doesn't support Data Binding by default, there are few libraries which can be used to implement data binding with MVVM in your iOS app, such as [Bond ](https://github.com/ReactiveKit/Bond)(Swift), [ReactiveCocoa ](https://github.com/ReactiveCocoa/ReactiveCocoa)(Swift) and [Bind](https://github.com/markohlebar/BIND) (Objective C).

## VIPER for iOS App Development

![Image title](https://dzone.com/storage/temp/7798190-viper.jpeg)

VIPER is an architectural design pattern which follows a clean architecture approach in iOS. VIPER divides an application into distinct and individual layers of responsibilities. The word VIPER is an acronym for View, Interactor, Presenter, Entity, and Routing.

Following are the main parts of VIPER:

  * **View (V)** \- View displays the input which is delegated by presenter

  * **Interactor (I)** \- Interactor contains the business logic

  * **Presenter (P)** \- Presenter receives input from the view and reacts to it by requesting data to the interactor. On the other hand, it also receives data from interactor, apply view logic to the data and tells the View to display the data.

  * **Entity (E)** \- Entity is the smallest element inside VIPER. It handles the responsibility to encapsulate different types of data. It contains the basic model object, which is later being used by interactor.

  * **Router (R)** \- Router is responsible for handling navigation between screens. It also decides the actual order of the navigation.

VIPER architecture follows the [single repository principle](http://www.objectmentor.com/resources/articles/srp.pdf), which leads to a better structure in your iOS application. It introduces the router layer which easily solves the problem to navigate between screen.

Since responsibilities are more clearly defined in VIPER - It reduces the chances of conflicts between the development team.

Also, VIPER defines the better separation of concerns than any other architectural design pattern such as MVC, MVP or MVVM which makes test-driven development more easier.

## Conclusion

Above mentioned are some common iOS architectural design patterns which you can use while developing your iOS application. To conclude in simpler terms, MVC as an architecture provides good separation of concern but it often introduces the so-called concept of bloated ViewControllers. MVP and MVVM both eliminates the problem of bloated ViewControllers in MVC. So, they are good architectural patterns.
