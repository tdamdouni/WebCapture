# Library vs. Framework?

_Captured: 2015-11-22 at 14:16 from [www.programcreek.com](http://www.programcreek.com/2011/09/what-is-the-difference-between-a-java-library-and-a-framework/)_

What is the difference between a Java Library and a framework? The two concepts are important but sometimes confusing for Java developers.

**1\. Key Difference and Definition of Library and Framework**

The key difference between a library and a framework is "Inversion of Control". When you call a method from a library, you are in control. But with a framework, the control is inverted: the framework calls you.

![framework-vs-library](http://www.programcreek.com/wp-content/uploads/2011/09/framework-vs-library.png)

A library is just a collection of class definitions. The reason behind is simply code reuse, i.e. get the code that has already been written by other developers. The classes and methods normally define specific operations in a domain specific area. For example, there are some libraries of mathematics which can let developer just call the function without redo the implementation of how an algorithm works.

In framework, all the control flow is already there, and there's a bunch of predefined white spots that you should fill out with your code. A framework is normally more complex. It defines a skeleton where the application defines its own features to fill out the skeleton. In this way, your code will be called by the framework when appropriately. The benefit is that developers do not need to worry about if a design is good or not, but just about implementing domain specific functions.

**2\. Their Relation**

Both of them defined API, which is used for programmers to use. To put those together, we can think of a library as a certain function of an application, a framework as the skeleton of the application, and an API is connector to put those together. A typical development process normally starts with a framework, and fill out functions defined in libraries through API.

**3\. Examples**

1\. [How to make a Java library?](http://www.programcreek.com/2011/07/build-a-java-library-for-yourself/)  
2\. [How to design a framework?](http://www.programcreek.com/2011/09/how-to-design-a-java-framework/)

Reference:  
[Martin Fowler](http://martinfowler.com/articles/injection.html)
