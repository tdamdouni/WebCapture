# Everything About Method Overloading vs. Method Overriding

_Captured: 2017-06-13 at 23:05 from [dzone.com](https://dzone.com/articles/everything-about-method-overloading-vs-method-overriding?edition=303098&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-13)_

What every Java engineer should know about microservices: [Reactive Microservices Architecture](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone). Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).

In a previous article, [ClassNotFoundException vs. NoClassDefFoundError](https://dzone.com/articles/classnotfoundexception-vs-noclassdeffounderror), I explained the titular ClassNotFoundException and NoClassDefFoundError in detail and discussed their differences and how to avoid them. If you have not read it, please go ahead and give it a look.

Similar to that, here in this article, we will look into another core concept of Java -- method overloading and overriding. As soon as we start learning Java, we get introduced to them and their contracts, which are pretty simple to understand. But sometimes, programmers get confused between them, or they do not remember the rules on when to use which one.

Here, we will discuss method overloading and overriding in more detail, the contract one must follow to correctly overload or override a method, the different rules of method overloading and overriding, and the differences between them.

## Method Overloading

Method overloading means providing two separate methods in a class with the same name but different arguments, while the method return type may or may not be different, which allows us to reuse the same method name.

And this becomes very handy for the consumer of our class. They can pass different types of parameters to the same method (in their eyes, but they are actually different) and get the response according to the input. For example, we might have a System.out.println() method that accepts all primitive object types and prints them, but in reality, there several PrintStream classes.

> While overloading has nothing to deal with polymorphism, Java programmers also refer to method overloading as ** Compile Time Polymorphism **because the method that is going to get called will be decided at compile time. 

In the case of method overloading, the compiler decides which method is going to get called based on the reference upon which it is getting called and the method name, return type, and argument list.

There are some rules we need to follow to overload a method. Some of them are mandatory while some are optional.

Two methods will be treated as overloaded if both follow the mandatory rules below:

  * Both must have the same method name.
  * Both must have different argument lists.

And if both methods follow the above mandatory rules, then they may or may not:

  * Have different return types.
  * Have different access modifiers.
  * Throw different checked or unchecked exceptions.

Usually, method overloading happens inside a single class, but a method can also be treated as overloaded in the subclass of that class -- because the subclass inherits one version of the method from the parent class and then can have another overloaded version in its class definition.

## Method Overriding

Method overriding means defining a method in a child class that is already defined in the parent class with the same method signature -- same name, arguments, and return type (after Java 5, you can also use a covariant type as the return type).

Whenever we extend a super class in a child class, the child class automatically gets all the methods defined in the super. We call them derived methods. But in some cases, we do not want some derived methods to work in the manner that they do in the parent. We can override those methods in the child class. For example, we always override `equals`, `hashCode`, and `toString` from the `Object` class. If you're interested, you can read more on [Why can't we override clone() method from the Object class](https://programmingmitra.blogspot.in/2016/11/Java-Cloning-Types-of-Cloning-Shallow-Deep-in-Details-with-Example.html).

In the case of abstract methods, either from a parent abstract class or an interface, we do not have any option: We need implement or, in other words, override all the abstract methods.

> Method overriding is also known as **Runtime Polymorphism **and ** Dynamic Method Dispatch** because the method that is going to be called is decided at runtime by the JVM. 

> Using the `@Override` annotation on the overridden methods is not necessary, but using it will tell you if you are not obeying overriding rules. 

At the line mammal.speak(), the compiler says the speak() method of reference type Mammal is getting called. So, for the compiler, this call is Mammal.speak().

But at execution time, the JVM clearly knows that the `mammal` reference is holding the reference of the `Cat` object, so for the JVM, this call is `Cat.speak()`. You can read more on [How Does the JVM Handle Method Overloading and Overriding Internally](https://programmingmitra.blogspot.in/2017/05/how-does-jvm-handle-method-overriding-internally.html).

### Method Overriding Rules

Similar to method overloading, we also have some mandatory and optional rules we need to follow to override a method.

With respect to the method it overrides, the overriding method must follow following mandatory rules:

  * It must have the same method name.
  * It must have the same arguments.
  * It must have the same return type. From Java 5 onward, the return type can also be a subclass (subclasses are a covariant type to their parents).
  * It must not have a more restrictive access modifier (if parent --> protected then child --> private is not allowed).
  * It must not throw new or broader checked exceptions.

And if both overriding methods follow the above mandatory rules, then they:

  * May have a less restrictive access modifier (if parent --> protected then child --> public is allowed).
  * May throw fewer or narrower checked exceptions or any unchecked exception.

Apart from the above rules, there are also some facts to keep in mind:

  * Only inherited methods can be overridden. That means methods can be overridden only in child classes.
  * Constructors and private methods are not inherited, so they cannot be overridden.
  * Abstract methods must be overridden by the first concrete (non-abstract) subclass.
  * `final` methods cannot be overridden.
  * A subclass can use super.overridden_method() to call the superclass version of an overridden method.

## Differences Between Overloading and Overriding

![difference-between-method-overloading-and-method-overriding](https://4.bp.blogspot.com/-3ql1-a86D5A/WS2ESC-g9mI/AAAAAAAALKM/Z0lPP-hXwLAOOH7h2M1HYe_dLGmjVXZSACK4B/s1600/difference-between-method-overloading-and-method-overriding.png)

You can find the complete code in this [GitHub repository](https://github.com/njnareshjoshi/exercises/blob/master/src/org/programming/mitra/exercises/OverloadingOverridingExample.java) and please feel free to provide your valuable feedback.

Microservices for Java, explained. Revitalize your legacy systems (and your career) with [Reactive Microservices Architecture](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone), a free O'Reilly book. Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).
