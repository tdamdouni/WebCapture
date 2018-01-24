# MVP Pattern in iOS

_Captured: 2017-12-12 at 21:19 from [dzone.com](https://dzone.com/articles/mvp-pattern-in-ios?edition=342139&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-12)_

[Download](https://dzone.com/go?i=242231&u=http%3A%2F%2Finfo.saucelabs.com%2FFY17Q3-AST-Mobile-Testing-Reference-Guide_LP-Dzone.html) this comprehensive Mobile Testing Reference Guide to help prioritize which mobile devices and OSs to test against, brought to you in partnership with Sauce Labs.

The development of mobile apps has changed and evolved a lot in recent years. Thanks to the interest of developers and the growth of mobile platforms, it is getting more and more common that the development team pays more attention to creating reusable components and using best practices in software development, like those in desktop apps, web apps, and backend apps. This interest has brought that proliferate, more diverse patterns, able to get a more testable, modularized and reusable code, which caused improvement of the app performance, error reduction, and quality software development. And this article is about the MVP pattern for iOS development.

Here at [Apiumhub](https://apiumhub.com/), we have always focused on creating quality and working software, using in an intensive way the patterns and software development techniques which worked best for each platform, adapting to the clients' needs.

Let's focus on explaining the MVP pattern which we have already used on other platforms and that it's showing that it adapts relatively good to mobile technologies. Just like Android, which has become a "standard by default."

We will explain to you how we have adapted the MVP pattern to the iOS app development, our proposition, and the reasons why we believe that it is a valid alternative to other patterns and how we have plugged our own different development pieces with such iOS patterns.

The MVP pattern was invented in the 90s as a common C++ initiative from Apple, IBM, and HP as an alternative to the MVC pattern. It is an acronym for Model, View, Presenter, which are the vital components of this pattern. There are different implementations of this pattern and some important variances like [Supervising Controller](https://martinfowler.com/eaaDev/SupervisingPresenter.html) or [Passive View](https://martinfowler.com/eaaDev/PassiveScreen.html).

The main difference between the MVP pattern and other UI patterns is the full independence between view and model; in other words, the view doesn't know that a model exists and the other way around.

In our case, we have adopted a variance of this pattern, implemented in a framework named [Claymore](http://claymore.codeplex.com/wikipage?title=DOC_UNDERSTAND_MVP_PATTERN&referringTitle=Documentation) (here is an example in [C#](http://claymore.codeplex.com/wikipage?title=DOC_SAMPLE_CLOCK&referringTitle=Home)).

## Pure MVP Pattern

Just like in all the definitions of the MVP pattern, in our case, it has 3 separated and clearly differentiated parts, but with some peculiarities:

### **The View**

The view is a layout which task is to render the UI and to react to the user events. In the case of iOS, the View will consist of a Protocol that exposes the methods of the user's events and a ViewController that is responsible for materializing and rendering the UI components and capturing the events that pass to the next component of the pattern, the presenter.

### **The Presenter**

It is responsible for making a connector between the events emitted by the view and connecting them with the model, specifically with the services of the model. We understand the presenter as a piece of software that connects View with Model, but that lacks logic, the whole state of the data of the view and its behavior is handled in the service and through the presenter, again that returns the transformed data or responds to an event as appropriate. In iOS, usually, the presenter is a class that receives in the init method the view and the service and connects the needed methods. The presenter is normally being used inside an extension class from the main ViewController and it happens when the connection settings are done.

### **The Model**

It is the system that contains the logic of the business and it is made up of different software pieces depending on the complexity of the app. In a "Domain oriented" system we will have to structure the layers of the tactic [DDD](https://apiumhub.com/tech-blog-barcelona/introduction-domain-driven-design/), with some variations coming from the particularity of every front-end app. In the mobile apps, the main parts of the model that we perceive here at Apiumhub are:

  1. **The services:** they are responsible for executing the logic of the business (if there is one) within the domain objects of the App and if it´s necessary to call the repository (o gateway) to have access to the external services or local database. In the iOS case, the service will be made out of a Class and a Protocol. The Class will contain the implementation of the methods exposed by the protocol.

  2. **The entities:** they are the domain objects. They contain logic that reflects the application status. Normally, these objects are kind of DTOs because the logic of the transactions would be in the server, however, there are some exceptions. These objects should never arrive in the view, however, sometimes exceptions can be done when we are talking about simple data transfer objects without logic. Normally, entities are represented as a Class.

  3. **The repository:** They call the external services (APIs or other services) or to local databases if the app has them. Just like the services will be made out of a Class and a Protocol.

  4. **DTO PresentationModel:** These are the objects which are given back from the service and represent the state of a view after the execution or any state change from the app. Usually, they are built from one or more entities. In this case, we will use Structs to carry out the representation of this type of objects, since when representing states of a view, there should be no hierarchy between them.

The main feature of this "Pure" MVP pattern is that the Presenter has no logic and acts like a common plug connector. This allows the presenter to act as an isolated component and it can be re-used again in more than part of the app.

### **Advantages of the Presenter**

It is a component that expresses directly its intention and responsibility without adding logic that could make us think that does more than one task at the same time.

The presenter centralizes the flow of the events, that help us to:

  * Debug, in the opposite it gets more complicated, especially if you work with binding systems.
  * It is easier to trace the origin of the events, the relations between an event and the service responsible for managing it are known at a glance.
  * Avoiding "hidden" chain of events because they lack logic and handle the state of the data in the service
  * The same component can be reused in different context and services.
  * You don't strictly need a test, especially in statically typed environments, because being essentially declarative makes it difficult to introduce errors by logic or change of state of the data.

### Global Features That This Pattern Brings to the Table

  * The state of the data its always managed from a model level, more specifically in the service layer, when not managed in the server.
  * Chain of events is avoided, usually an iteration from a user it´s considered an event
  * Since we avoid event chains, the number of calls to the server are minimized, because the logic and the state of the data is solved at the level service. 
  * Reduce the coupling and increase the cohesion because each software piece has clear responsibilities and strength to distribute the logic between the model and the View.
  * Improves the use of the unit test in order to verify the correct functionality of each software pieces.

To sum up, adapting this MVP pattern in Apiumhub allowed us to be able to do it extensible to a more variety of platforms, create a more modulated system with the clear responsibility of the components, which allowed the coverage of the test to be bigger and reusable. It adapts and meets our needs, that doesn't mean that we keep the pattern in continuous evolution and improve it with new features that are introduced in each platform. This allows us to compare this pattern with others that are already being used in the iOS architectures such as [Viper](https://apiumhub.com/tech-blog-barcelona/viper-architecture/), MVVM, Clean Architecture, and more that we will try to evaluate in the next article.

Analysts agree that a mix of emulators/simulators and real devices are necessary to optimize your mobile app testing - learn more in this [white paper](https://dzone.com/go?i=242232&u=http%3A%2F%2Finfo.saucelabs.com%2FFY17-ADV-EmuSimRealDevices-WP-LP-DZone.html), brought to you in partnership with Sauce Labs.
