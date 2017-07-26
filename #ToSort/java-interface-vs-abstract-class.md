# Java: Interface vs. Abstract Class

_Captured: 2017-03-15 at 22:11 from [dzone.com](https://dzone.com/articles/java-interface-vs-abstract-class?edition=283883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-15)_

## Preface

A class is named a concrete class when it has a name and implements every remaining method that is declared along the class hierarchy. Along with the hierarchy, its supertypes become a more general representation of the acting domain, and finally goes beyond that border and ends with the fact that almost everything is an object. A supertype can be either a concrete class that is apparently not final, an abstract class or even one or more interfaces. Combining a super or an abstract class with some interfaces is also a wide acknowledged way for characterizing a concrete class. Polymorphism is given when more than one class implements a particular method differently based on a class's nature. In this article, the focus is on two of three kinds of supertypes they distinguish from their essential characteristics. Both an interface as well as an abstract class can be instantiated in a manner of an anonymous class.

## Abstract Class

Typically, an abstract class implements common behaviors and member variables across any concrete class, and its method might have already specified an interface. The distinguishable behavior is gained through declaring abstract methods, which need to be implemented in a specific class. The abstract class can inherit features from another concrete or abstract class, and can enrich further behavior while adding interfaces. In Java, such tangible implementations can be explicitly emphasized with the annotation @Override that indicates a deviation of manner (docs.oracle.org, n.d.). The polymorphism stops at that point, where a concrete implementation of a method becomes final. As methods in an abstract class can also be private, it makes such a class most appropriate for encapsulating private methods while breaking down the complexity of shared methods into smaller pieces. (Martin, 2009). An abstract class is ultimately very close to a concrete implementation.

## Interface

Since Java 1.8, an interface can implement default methods to provide a general behavior (Panka, 2016). Consequently, both an abstract class and an interface approach each other regarding their features. While member variables of an interface are explicitly public and final, an abstract class does not sanction their members about access modifiers. Moreover, there is a small difference with a significant effect regarding possible access modifiers for a default method in interfaces. A default method is always public and is in contrast to an abstract method that accepts either default, protected, or public as an access modifier. Whatever an interface defines, it can be used anywhere and may enrich an object with specific behaviors. An interface allows only inheritance from another interface. Both an abstract class and an interface can implement static methods. (docs.oracle.com, n.d.). Another type of interfaces are such without any declared method and are fully accepted as a marker interface. They merely indicate the compliance from a developer that, for example, a class is serializable (java.io.Serializable) or cloneable (java.lang.Cloneable) (mrbool.com, n.d.).

## Example 1: Interface vs. Abstract Class

This comparison emphasizes the advantage of an abstract class over an interface focused on the calculation of the angle between two straight lines. However, both an interface and an abstract class can be used for that purpose while the first does not go in line with Martin's suggestions about clean code.

## Example 2: Combination of Interface and Abstract Class

This example is very close to the prior one, but is distinguished by a mix of interface and abstract classes. They both characterize concrete classes.

## References

docs.oracle.org (n.d.) Anonymous Classes. _Oracle_. Available from: <https://docs.oracle.com/javase/tutorial/java/javaOO/anonymousclasses.html>. [9 February 2017].

docs.oracle.org (n.d.) Overriding and Hiding Methods. _Oracle_. Available from: <https://docs.oracle.com/javase/tutorial/java/IandI/override.html>. [10 February 2017].

Martin, R. C. (2009) Clean Code: A Handbook of Agile Software Craftsmanship. _Prentice Hall_. [Kindle]. [11 February 2017].

Panka, J. (2016) Java 8 Interface Changes - static method, default method. _JournalDev_. Available from: <http://www.journaldev.com/2752/java-8-interface-changes-static-method-default-method>. [9 February 2017].

docs.oracle.com (n.d.) Lesson: Interfaces and Inheritance. Available from: <https://docs.oracle.com/javase/tutorial/java/IandI>. [10 February 2017].

mrbool.com (n.d.) What is Marker interface in Java? Available from: <http://mrbool.com/what-is-marker-interface-in-java/28557>. [11 February 2017].
