# The Secret Life of Objects: Inheritance

_Captured: 2018-08-09 at 00:19 from [dzone.com](https://dzone.com/articles/the-secret-life-of-objects-inheritance?edition=385348&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-08-08)_

How do you break a Monolith into Microservices at Scale? [This ebook](https://dzone.com/go?i=296455&u=https%3A%2F%2Finfo.lightbend.com%2Febook-reactive-microservices-the-evolution-of-microservices-at-scale-register.html%3Futm_source%3Ddzone%26utm_medium%3Dpost-roll-text%26utm_campaign%3DCOLL-2017-Reactive-Microsystems-The-Evolution-of-Microservices-at-Scale%26utm_term%3Dnone%26utm_content%3Djava-zone) shows strategies and techniques for building scalable and resilient microservices.

This post is the second part of a series of posts concerning the basic concepts of object-oriented programming. The first post was focused on [Information Hiding](http://rcardin.github.io/design/programming/oop/fp/2018/06/13/the-secret-life-of-objects.html). This time, I will focus on the concept of _inheritance_. Whereas most people think that it is easy to understand, the inheritance is a piece of knowledge that is very difficult to master correctly. It subtends a lot of other object-oriented programming principles that are not always directly related to it. Moreover, it is directly related to one of the most potent forms of dependency between objects.

Out of there, many articles and posts rant against object-oriented programming and its principles, just because they don't understand them. One of these posts is [Goodbye, Object Oriented Programming](https://medium.com/@cscalfani/goodbye-object-oriented-programming-a59cda4c0e53), which treats inheritance and the others object-oriented principles with a very biased and naive perspective.

So, let's get this party started, and let's demystify the inheritance in object-oriented programming once for all.

## Inheritance Defined

Providing the definition of inheritance would be a good place start, as we being to analyze the concept:

> Inheritance is a language feature that allows new objects to be defined from existing ones.

Given that we have a class for each object,

> an object's class defines how the object is implemented, i.e. the internal state and the implementation of its operations. [..] In contrast, an object's type only refers to its interface, i.e. the set of requests to which it can respond.

Because of this:

> It is important to understand the difference between class inheritance and interface inheritance (or subtyping). Class inheritance defines an object's implementation in terms of another object's implementation. In short, it's a mechanism for code sharing. In contrast, interface (or subtyping) describes when an object can be used in place of another.

## The Big Misunderstanding

By now, we understood that there are two types of inheritance -- class inheritance and interface inheritance (or subtyping). When you used the former, you're performing _code reuse_ that you know you will need a class and a piece of code. You are extending it to reuse that code, redefining all the stuff that you don't need.
    
    
      def write(lines: List[String]): Unit = {
    
    
      def write(lines: List[String]): Unit = {

Clearly, the class `AlgorithmThatReadFromKafkaAndWriteOnMongo` inherits from `AlgorithmThatReadFromCsvAndWriteOnMongo` only to reuse the code that writes on MongoDB. The drawback is that we have to pass `null` to the constructor of the parent class. However, something is not right here.

> The problem with object-oriented languages is they've got all this implicit environment that they carry around with them. You wanted a banana, but what you got was a gorilla holding the banana and the entire jungle.

This quote is by Joe Armstrong, the creator of Erlang. For this principle, every time you try to reuse some class, you need to add dependencies to its parent class, and to the parent class of the parent class, and so on.

Using the previous example, if you want to reuse the class `AlgorithmThatReadFromKafkaAndWriteOnMongoAndLogs`, you also need to import classes `AlgorithmThatReadFromCsvAndWriteOnMongo` and `AlgorithmThatReadFromKafkaAndWriteOnMongo`

This code demonstrated above is the problem with class inheritance and _code reuse_.

As discussed in the post [about dependency](http://rcardin.github.io/programming/oop/software-engineering/2017/04/10/dependency-dot.html), class inheritance is the worst form of dependency between two classes. We already related the concept of dependency between classes and the probability of modifying one against one change in another.

It is normal that, if two classes are linked through this type of relation, they must be used together. This fact is that the problem of inheritance is _tight coupling_.

First of all, do not use class inheritance. Do not use inheritance to reuse some code. Use inheritance so share **behavior** among components.

Afterward, do not put more than one _responsibility_ inside a class. I don' t dwell on responsibility. I already wrote about this topic in the [Single-Responsibility Principle done right](http://rcardin.github.io/solid/srp/programming/2017/12/31/srp-done-right.html). However, if you let your components implement more than one use case, you let two different clients of a component depend from different slices of it. Then, the problem is not inheritance; it is in your whole design. A component that implements only one responsibility is very likely to inherit from a hierarchy that contains only one type, which is most of the times an _abstract type_.

Concerning our previous example, there is a problem of code reuse and a violation of the Single-Responsibility Principle. Each class is doing too much, and it is doing in the wrong way.

If you think about it, there is a big problem with class inheritance -- it seems to break encapsulation. A subclass (a class that inherits from another) knows and can virtually access the internal state of the base class. We are breaking encapsulation. So, we are violating the first principle of object-oriented programming, are not we?

Well, not properly. If a class you inherit from exposes some `protected` state, it is like that class is exposing two kinds of interfaces.

> The _public_ interface lists what the general client may see, whereas the _protected_ interface lists what inheritors may see.

The problem is that maintaining two different interfaces of the same type is very hard. Adding more types of clients to a class means to add dependencies. The more dependencies, the higher the coupling. A high coupling means a higher probability of changes cascades among types.

So, don't use class inheritance. Stop!

If you can't use inheritance, why is this considered one of the essential principles of object-oriented programming? Technically, inheritance is still possible under certain circumstances.

## Subtyping or Reusing Behavior

The first case in which you are allowed to use inheritance is **subtyping**, also known as behavior inheritance or interface inheritance.

> Class inheritance defines an object's implementation in terms of another object's implementation. In short, it's a mechanism for code and representation sharing. In contrast, interface inheritance (or subtyping) describes when an object can be used in place of another.

The above sentence is very informative. It screams to the world that you **must not** override methods of superclasses if you want to reuse behavior.

Following this principle, the only types from which we can inherit are _interfaces_ and _abstract classes_, avoiding the override of any concrete method of the latter.

> When inheritance is used carefully (some will say properly), all classes derived from an abstract class will share its interface. [..] Subclasses merely adds or overrides operations and **does not hide the operations of the parent class**.

Why is this principle so important? Because of _polymorphism_ depends on it. In this way, clients remain unaware of the specific type of objects they use, **reducing implementation dependencies drastically**.

> Program to an interface, not an implementation.

### Favor Object Composition Over Class Inheritance

The only way we have to extend the behavior of a class is to use _object composition_. This can be done by obtaining new functionalities by assembling objects to get more complex functionalities. Objects are composed using their well-defined interfaces only.

This style of reuse is called the **black-box reuse**. No internal details of objects are visible from the outside, producing the lowest possible dependency degree.

> Object composition has another effect on system design. Favoring object composition over class inheritance helps you keep each class encapsulated and focused on one task and on a single responsibility.

Our initial example can be rewritten using two new highly specialized types: a `Reader` and a `Writer`.
    
    
      def write(lines: List[String]): Unit = {
    
    
    class KafkaReader(broker: String, topic: String) extends Reader {
    
    
      def write(lines: List[String]): Unit = {
    
    
      def write(lines: List[String]): Unit = {
    
    
      writers.foreach(_.write(lines))

## The Liskov Substitution Principle

It seems that inheritance should not be used in any case. You must not inherit from a concrete class, only from abstract types. Is it correct? Well, there is a specific case in which the inheritance from concrete classes is allowed.

The Liskov Substitution Principle (LSP) tells us exactly which is the case.

> Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it.

A class can inherit from another concrete class if -- and only if -- it does not override the pre-postcondition of the base class. In a derivated class, preconditions must not be stronger than in the base class. In a derivate class, postconditions must be stronger than in the base class.

> When redefining a routine [in a derivative], you may only replace its precondition by a weaker one, and its postcondition by a stronger one.

The above is called _design-by-contract_. Respecting this principle avoids the redefinition of the _extrinsic public behavior_ of a base class -- that is the behavior the clients of a class depend upon.

![Ducks and the Liskov Substitution Principle](https://image.ibb.co/cyshi7/lsp.jpg)

> _Ducks and the Liskov Substitution Principle_

Returning to our previous example, take the class `AlgorithmThatReadFromCsvAndWriteOnMongo`and its subclass `AlgorithmThatReadFromKafkaAndWriteOnMongo`. The LSP tells us that, whenever we need a reference to the first, we can use a reference to the second instead. However, in our example, we can't. The first read from a CSV; the second from Kafka.

It's easy to write a test that uses an object of type `AlgorithmThatReadFromKafkaAndWriteOnMongo`where an object of type `AlgorithmThatReadFromCsvAndWriteOnMongo` is requested. It's easy to see it fail.

Why? The reason is that we have violated base class _invariants_. We tried to reuse code and not to reuse behavior.

The same, old story.

## Conclusion

To sum up, let's try to avoid the reuse of code and avoid class inheritance, if possible. Try to reuse behavior and try to use subtyping. I prefer not to extend a concrete class. Alternatively, if you have to, verify that you fulfill the Liskov Substitution Principle.

If you follow these simple rules, the dependency degree between your classes will stay low, and your architecture will be simpler to maintain and evolve. Easy, right?

## References

How do you break a Monolith into Microservices at Scale? [This ebook](https://dzone.com/go?i=296456&u=https%3A%2F%2Finfo.lightbend.com%2Febook-reactive-microservices-the-evolution-of-microservices-at-scale-register.html%3Futm_source%3Ddzone%26utm_medium%3Dpost-roll-text%26utm_campaign%3DCOLL-2017-Reactive-Microsystems-The-Evolution-of-Microservices-at-Scale%26utm_term%3Dnone%26utm_content%3Djava-zone) shows strategies and techniques for building scalable and resilient microservices.

Topics:

java ,tutorial ,code reuse ,inheritance ,liskov substitution principle ,object oriented programming ,class inheritance ,subtyping ,interface inheritance
