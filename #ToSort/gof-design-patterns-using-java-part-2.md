# GoF Design Patterns Using Java (Part 2)

_Captured: 2017-02-09 at 21:14 from [dzone.com](https://dzone.com/articles/gof-design-patterns-using-java-02?edition=267886&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-09)_

My concluding write-up on design patterns, with some examples. Please first check out Part-1 of this article under '[GoF Design Patterns Using Java (Part 1)](https://dzone.com/articles/gof-design-patterns-using-java-part-1).'

To understand the philosophical and historical perspective on the Gang of Four's design patterns, I made a short, 10-minute video. (This was also my PluralSight author audition).

I came up with my own examples to understand 'Design Patterns' further. Try downloading the code and see if it helps you in comprehending these in a better way. You may refer to (bookmark) this article as Quick Reference/Cheatsheet when you want to quickly revisit each of them.

## **Adapter Pattern**

What can you do if you need to use an Asian hairdryer in a European country, each with different socket types? I would us an adapter! As in real life, when we want to plug and play with similar but incompatible interfaces, we use [the Adapter](http://www.sumithpuri.me/coderanch/adapter.jar). The Adapter adapts the adaptee to the desired interface by composing the adaptee object and inheriting the desired interface -- or through multiple inheritance.

The attached example is a real-world computer scenario where I want to plug in an external hard drive (pre-USB era!), a SeagateDrive of interface type SeagateGeneric, to an incompatible computer, a SamsungComputer of type Computer. SeagateGeneric provides read() and write() methods for these purposes, which need to be adapted to the actual bufferData(), flushData(), and purgeData() methods of the Computer. Note that there is no equivalent of purgeData(). The ideal way to handle this scenario is to throw an exception whenever this method is invoked on the hard drive, as it would do in the real world. The adapter to perform the translation in this scenario is the SeagateAdapter, which implements the Computer interface. It encapsulates a SeagateGeneric instance reference and adapts it to the Computer interface. Whenever a bufferData() method is invoked on the Computer interface, it actually requires three invocations of read() on the SeagateGeneric implementation to match up to the Computer's standards. These kinds of translations are done by the adaptee.

Only the core concept is provided in the snippets below. You can download the [sample code](http://www.sumithpuri.me/coderanch/adapter.jar) for the complete code/application.
    
    
    package com.sumsoft.design.patterns.adapter;
    
    
    package com.sumsoft.design.patterns.adapter;
    
    
    package com.sumsoft.design.patterns.adapter;
    
    
    package com.sumsoft.design.patterns.adapter;

**  
PCAssembler **is the main class here. Try adding your own device and its adapter to the computer.

## **Facade Pattern**

Consider a scenario where we require multiple method invocations on various classes to achieve a desired functionality. Also, consider that this functionality is repeatedly being used in your code. If you are thinking of an option where you will perform direct invocations, you are bound to end up with code maintenance issues and tightly coupled code. If these invocations are remote, it is going to be worse with respect to performance. This is where the [facade](http://www.sumithpuri.me/coderanch/facade.jar) comes into play, wherein multiple method invocations are encapsulated into a single method of the facade class to achieve the desired functionality. It provides us with a single point of change and looser coupling with respect to the individual implementations. Remote method invocation patterns like SessionFacade (EJB) adapt from here to improve the overall performance and lower complexity.

The example attached is a very simple scenario of an InvoiceManagerFacade which has addInvoice() and deleteInvoice() methods. To achieve the desired result, each of these methods encapsulates the method invocations from OrderManager, LedgerManager, and BillingManager classes.

**AccountsCentral** is the main class. Try adding your own method to the facade class, or try plugging in a new type of facade.

## **Template Pattern**

Imagine a real-world scenario where a factory is creating both aluminum nails and screws. Though the machine has to create both of them through similar processes, the way some steps are implemented may vary in each of these. When we think of such scenarios in software, we utilize the [template pattern](http://www.sumithpuri.me/coderanch/template.jar). The Template Pattern defines a way to re-use algorithms for various implementations with different or slightly different outcomes.

In the attached example, the abstract class SoftwareProcessor defines a general set of algorithmic steps (functions) to deliverSoftware(). This class is my template class. Since the implementation and testing phases differ in projects based on the technology stack being used, CProcessor and JavaProcessor classes adapt this algorithm for these phases. The common methods are all implemented in SoftwareProcessor and the specific ones are left as abstract.

Only the core concept is provided in the snippets below. You can download the [sample code](http://www.sumithpuri.me/coderanch/template.jar) for the complete code/application.

**SoftwareConsultants**can be used to run this example. Try adding your own processor.

## **Iterator Pattern**

The need to have a handle to a collection of elements, without exposing its internal implementation, is met by the [Iterator Pattern](http://www.sumithpuri.me/coderanch/iterator.jar). I would term this as a pure programming pattern, in its own right. By utilizing this handle (Iterator), the client using the collection can easily process the same without any dependency on the internal logic.

In the attached example, ProductMenu holds a menu or list of ProductItem. This list and its usage should be implementation agnostic to the clients. Hence, the need for a ProductIterator which implements the generic Iterator interface. The createIterator() method of ProductMenu passes the array implementation of ProductItem to the constructor of ProductIterator.

Only the core concept is provided in the snippets below. You can download the [sample code](http://www.sumithpuri.me/coderanch/iterator.jar) for the complete code/application.

The example can be run using **ProductMenuTester**.

## **State Pattern**

The [State Pattern ](http://www.sumithpuri.me/coderanch/state.jar)defines a way to maintain various steps or states of the same machine or class. The word machine comes to mind easily because it is the simplest example of a real-world scenario where there is a need to operate the same object in steps or set states -- with the transition from one step to the next defined by a single action (or multiple actions).

The example attached is a very crude but helpful one -- that of an online shopping site, aptly named OnlineShopping. The limitation of this site is that at any given point, only a single item can be purchased and processed. The various states during the purchase and processing are SelectionState, PurchaseState, AuthoriseState, AssembleState (optional), and DispatchState. Each of these states is processed and followed in a sequential manner. OnlineShopping maintains an instance variable of each of these states -- and also a currentState variable. The various state methods that exist within OnlineShopping are selection(), purchase(), authorise(), assemble(), and dispatch(). When a client calls these methods, the actual invocations are performed on the state implementation held in the currentState variable. All state implementations implement the State interface, which specifies the lifecycle methods.

Only the core concept is provided in the snippets below. You can download the [sample code](http://www.sumithpuri.me/coderanch/state.jar) for the complete code/application.

**  
ShoppingClient** is the main class. _Try adding your own states along with the required lifecycle method_.

**Note**: The snippets above explain the various design patterns' core concepts. You may download the code from each of the links above and run them on your system for a more thorough understanding. You may also choose to modify the code with your own examples to cement your knowledge.
