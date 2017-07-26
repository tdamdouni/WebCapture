# GoF Design Patterns Using Java (Part 1)

_Captured: 2017-02-03 at 02:52 from [dzone.com](https://dzone.com/articles/gof-design-patterns-using-java-part-1?edition=268885&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-02)_

To understand the philosophical and historical perspective on the Gang of Four's design patterns, I made a short, 10-minute video. (This was also my PluralSight author audition).

I came up with my own examples to understand design patterns further. Try downloading the code and see if it helps you in comprehending the patterns in a better way. Some brief code snippets follow each pattern so you can get quick demonstrations. Feel free to bookmark this article as a quick reference/cheat sheet for when you want to quickly review each of them. Without further ado, let's jump into the Observer Pattern.

## **Observer Pattern**

The Observer Pattern, as the name suggests, is used in scenarios when updates need to be done at multiple points (Observers) depending on changes in state at another place (Subject). Each of the Observers has to register themselves with the Subject, individually. The Subject should also provide methods that allow the observers to remove themselves. Registered observers are informed of changes in state through a notify method. Usually.

The provided example is that of a StockBroker application, which involves the maintenance of various types of financial information. The Subject is the interface in the application that provides a template for the Observed class. StockData is the concrete implementation of the Subject and provides the implementation for addObserver(), removeObserver() and notifyObservers(). Additionally, it maintains a list of registered observers. IncomeHandler, InvestmentHandler and

PortfolioHandler includes the various observers used to maintain the income, investments, and portfolio of a specific StockBroker. All these depend on the constantly fluctuating values of stocks. They are specifically interested in the stockSymbol, stockValue, and stockUnits of each individual stock. Each of the Observers implements the interface Observer. The Observer interface provides the update() method, which is implemented by each of these concrete classes.

Only the core concept is provided in the snippets below. You can download the [sample code](http://www.sumithpuri.me/coderanch/observer.jar) for the complete code/application.
    
    
    package com.sumsoft.design.patterns.observer;
    
    
    package com.sumsoft.design.patterns.observer;
    
    
    package com.sumsoft.design.patterns.observer;

Use StockBroker.java to run the application. Try adding your own Observer to this application. Also, you can try picking up these values from a live web service and writing a custom observer which depends on this.

## **Decorator Pattern**

The Decorator Pattern provides an elegant way to use composition for enhancing functionality where the result expected has a direct dependency on the composed and composing class. A chain relation (via composition) or decoration can be finally used to achieve the desired output at runtime. In real-time, when the functionality of one particular product is expected to be built from a base product and various other related sub-products or fixtures, we can rely on the Decorator.

The attached example is that of a Pizza application. Here, the pizzas in the shop are made with various combinations of bases and topping combinations. This is a classic example to use the Decorator Pattern on. Pizza is the abstract base class for each of the pizza bases to implement, and ToppingDecorator is another abstract class that inherits from Pizza for each of the toppings to implement. Hawaiian, Italian, and Mexican are the concrete implementations of Pizza, whereas Mushroom, Onion, and Chicken are the concrete implementations of ToppingDecorator. Each of these toppings encapsulates a Pizza instance. This instance, at runtime, will hold another topping or the pizza base instance. Finally, it is when the cost has to be calculated on the entire pizza that the real value of decorator pattern is seen and just one call suffices to calculate the entire bill value.

Only the core concept is provided in the snippets below. You can download the [sample code](http://www.sumithpuri.me/coderanch/decorator.jar) for the complete code/application.

PizzaWorld is the main class. Try adding more decorators and pizza base classes to see if you can get a real taste of the Decorator.

## **Singleton Pattern**

The Singleton Pattern defines a way to maintain only a single instance of a class in the entire execution of a program/application and to provide a uniform way to access it. There are numerous methods that exist in which this pattern can be implemented. I have explained the three most common scenarios here:

### **Eager Singleton**

The simplest Singleton ([download the sample code here](http://www.sumithpuri.me/coderanch/singleton_eager.jar)) is the one in which the instance is created at class-load time and stored in a static instance variable. A static getter method is then used to get this instance when required. The instantiation of an object earlier than its first use might not be a recommended approach.

In the given example, MediaContract (Main Thread) works on an instance of the ProductionHouse (Singleton). The Singleton is instantiated at class-load time and maintained in the private static instance variable. getInstance() in ProductionHouse helps in retrieving the instance.

### **Thread-Safe Singleton (Most Common)**

To overcome the above drawback, the recommended approach is to instantiate the object at the first access time and also to make it thread-safe ([download the sample code](http://www.sumithpuri.me/coderanch/singleton_threadsafe.jar)) to prevent concurrent thread instantiation. The disadvantage of this method is poorer performance, as the method is synchronized.

As in the earlier example, the classes are MediaContract (Main Thread) and ProductionHouse (Singleton). The getInstance() method is synchronized, and the instance is created only if it is null.

### **Double-Checked Locking**

The disadvantage mentioned above can be critical for a highly accessed object in an application. To improve this, the scope of the synchronized block is reduced to affect only the first access. This, again, has some disadvantages.

The example remains the same, the difference being in the reduced scope of synchronization within the getInstance() method -- and also that it affects only the first access and not subsequent accesses. You can download the [sample code her](http://www.sumithpuri.me/coderanch/singleton_doublechecked.jar)e.

For all the three partial samples above, you may use the following code to run and understand the different ways to instantiate Singletons_._

## **Command Pattern**

In scenarios where we need to create a sequence of actions (or operations) and perform them at a specified (later) point in time, we have a candidate for usage of the Command Pattern. Though it very closely resembles the Observer pattern in implementation, the usage is different and the command (actions) is invoked only on a single chosen receiver by an invoker, rather than on all Observers.

We'll look at an example of an auction house where there are various items for auction. The base abstract class of the lots is represented by AuctionItem. The abstract method to be implemented by implementing classes is sell(). AuctionVase, AuctionFurniture, and AuctionJewel are all concrete implementations of AuctionItem. Instances of each of these are created and set (mapped by an itemKey) into the AuctionControl, which can be thought of as a remote control for presenting items in the AuctionStore. Whenever the presentItem() is invoked on the AuctionControl class, passing in an itemKey, the appropriate AuctionItem instance is selected and sell() is invoked on this instance.

Only the core concept is provided in the snippets below. You can download the [sample code](http://www.sumithpuri.me/coderanch/command.jar) for the complete code/application.

## **Factory Pattern**

The Factory Pattern, I am made to believe, is the most widely used and implemented pattern in software projects, after the Singleton Pattern. Since Singleton is only a creational pattern at a single class level, the scale for using the Factory Pattern should be much higher. The Factory Pattern deals with the creation of similar types of objects and producing them in a centralized manner, depending on the condition or type of object requested. There are plenty of variations of the Factory Pattern, three of which I have listed below.

### **Simple Factory**

The [simplest Factory Pattern](http://www.sumithpuri.me/coderanch/simple_factory.jar) is the one that is used to create (instantiate) a specific type of product (object) depending on a condition. The specific types of objects that can be created in a single factory are all expected to implement a single interface.

In the attached example, the factory is used to instantiate a specific type of object depending on the operating system. All the specific systems implement the System interface, which defines the common methods that the concrete class of this type should implement. SystemFactory is the factory class that provides the create() method, which takes a type argument. The type argument decides which concrete factory should be instantiated.

### **Factory Method**

When there can be various families of products (objects) that can be instantiated, but each family of these products needs to be created by a specific type of factory, we define a [factory method](http://www.sumithpuri.me/coderanch/factory_method.jar) in the base factory class. The concrete implementations of the base factory then override this method to produce concrete type of products, depending on the condition.

In the example, you can notice the presence of two abstract classes, Mobile (Product) and MobileStore (Creator). One family of concrete product implementations are NokiaASeries, NokiaBSeries, and NokiaCSeries -- to be created by the NokiaStore, which is the concrete implementation of the creator. In a similar fashion, another family of products, such as SonyASeries, SonyBSeries, and SonyCSeries are to be created by SonyStore, another concrete implementation of MobileStore. MobileStoreCentre is the main class to run this application. The createMobile() method is the abstract method (factory method) that is to be overridden by the creator implementations.

### **Abstract Factory**

The [Abstract Factory](http://www.sumithpuri.me/coderanch/abstract_factory.jar) defines a template or interface for the creation of similar types of objects or implementations. Usually, an Abstract Factory will encapsulate one or more factory methods within it for actually creating the product.

Taking the same example as above, MobileStoreFactory instantiates the concrete instance of the abstract factory (MobileStore) based upon the variable specified, either "Nokia" (NokiaStore) or "Sony"(SonyStore). The factory is then responsible for creating the objects of similar types based upon the choice -- such as "ASeries" or "BSeries" or "CSeries". The mobile is then assembled based upon this by the MobileStore. You may use MobileStoreCentre to run this example and understand the design pattern based on the output.

**Note**: Only the code to explain the various design patterns' core concepts are included int he snippets above. You may download the **code from each of the links above and run them on your system **for a more thorough understanding. You may also choose to modify the code with your own examples to cement your knowledge.

I will continue this article in another post outlining more design patterns, including the Adapter, Facade, Iterator, and Template patterns.
