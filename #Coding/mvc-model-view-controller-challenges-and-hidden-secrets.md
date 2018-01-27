# MVC - Model View Controller: Challenges and Hidden Secrets

_Captured: 2017-11-12 at 11:21 from [dzone.com](https://dzone.com/articles/mvc-model-view-controller-challenges?edition=334864&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-10)_

### Let's take a deeper look at the MVC software architecture, how it's arranged, how it came to be, and its various implementations.

The Nexus Suite is uniquely architected for a DevOps native world and creates value early in the development pipeline, provides precise contextual controls at every phase, and accelerates DevOps innovation with automation you can trust. [Read how in this ebook](https://dzone.com/go?i=222229&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

In this article, I'm going to talk about the MVC architecture (Model View Controller). I'm going to start with a little bit of history, then go through different possible implementations of MVC. The main aim of this article is to take a deep dive into how to write an application that respects the MVC pattern.

## Definition

Model View Controller is a software architecture mainly used in GUI applications to separate an application into three main components: the view for displaying and representing data in various forms, the controller for handling user actions and inputs, and the model where we put our business model.

This is the most widely spread definition on the internet. The problem, going through several references, is that I find slight differences in how these tiers communicate with each other. Also, I noticed there is a lack of resources of how to properly implement this pattern. Indeed, when we write an application with respect to this architecture we encounter many challenges and we will be in the obligation to take some decisions that may or may not be suitable.

## History

MVC was first introduced by Trygve Reenskaug in one of his white papers, which can be found [here](https://heim.ifi.uio.no/~trygver/themes/mvc/mvc-index.html). The Smalltalk-80 was one of the first implementations using this architecture, although they made quite some changes from what was described by Trygve Reenskaug as their product grew larger and more mature.

Since then, MVC has had many variants, like MVP (Model View Presenter), HMVC (hierarchical model-view-controller), and others.

## MVC Implementations

In this section, I decided to compare four architectures from four different resources: [Trygve Reenskaug's paper](https://heim.ifi.uio.no/~trygver/1979/mvc-2/1979-12-MVC.pdf), "[Patterns of enterprise application architecture" by Martin Fowler](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420), [Design patterns: elements of reusable object-oriented software - Gang of four](https://www.amazon.fr/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612), and [PureMVC](http://puremvc.org/) framework. So, I made some applications that simulate a small example of a library in each one of them.

The repository can be found [here](https://github.com/isabiq/mvc).

### Trygve Reenskaug

As described in the paper, the model is an independent component containing our business logic (as is the case for the other references). The view builds the interface and manages its components. It also receives commands from the controller, updates the model, and asks about the new state of the model. Finally, the controller manages user actions and inputs.

As you may notice from the project, the view has many responsibilities. Also, if we did have many views and controllers, we would find a problem in making these objects interact with each other, as every object will need to know about the others.

### Patterns of Enterprise Application Architecture

The model again contains our business logic, and the view does everything else, though we can use the controller if necessary to handle user actions. This design is natural to follow, but the view, again, has many responsibilities.

### Design Patterns: Elements of Reusable Object-Oriented Software

The model(subject) holds our business logic and can notify views using the observer pattern.

The view uses the composite pattern already build into swing, so there is no implementation of the pattern in the project. The view also asks for updates when receiving notifications from the model.

**Note:** Here it's a bit tricky because you'll need to manage the way the model notifies views. You probably don't want all the views calling the model for changing that doesn't concern them.

The controller can be used with the strategy pattern (not implemented in the example), but still, there is a need for communication between controllers. Consequently, it ends up with a controller knowing about every other controller.

**Note:** Use of the factory is important for creating and linking objects and returning a default controller.

### PureMVC

PureMVC is a framework used to develop applications based on the MVC architecture. It exists in many languages like Java, ActionScript, PHP, and others. The official repository can be found [here](https://github.com/PureMVC/).

In this implementation, there are other components apart from the model, view, and controller that help reach the desired design. The framework uses proxies which expose the model API, mediators for manipulating and reusing views, commands which are basically logic to be called whenever needed, and a facade to provide a single point for manipulating the application. You can find more details [here](http://puremvc.org/docs/PureMVC_Framework_Overview_with_UML.pdf).

Mediators and commands can easily communicate with each other in a loosely coupled way through the notification listener mechanism(an implementation slightly different from the observer pattern). Also, the use of the proxy is very efficient for caching and adding new responsibilities not concerned with the model.

But as you may notice from the project, the mediator still has many responsibilities in contrast with commands which seem only to have a role in starting the application. Also, the notification system is being centralized into the view (if you see inside the framework), which can have drawbacks as we can lose control of our system with notifications being thrown all over the application. Moreover, the notification holds in in itself the object being sent or received. This technique has some limitations like managing the object type (testing and casting) and the fact that we are only limited to one object (we can't send more than one object in the notification).

### Conclusion

As you can see, writing an application with a good design based on the MVC is architecture is very challenging and can cause problems if bad decisions were made. I think the main problems come from the need to strictly define the roles of the view and the controller even in the smallest details and to ensure a good communication mechanism between these components. The examples discussed here are not exhaustive, you can find other implementations and patterns used with MVC architecture.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. See how the Nexus platform infuses precise open source component intelligence into the DevOps pipeline early, everywhere, and at scale. [Read how in this ebook](https://dzone.com/go?i=222230&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).
