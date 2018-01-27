# Why We Should Follow Method Overloading Rules

_Captured: 2017-12-27 at 13:30 from [dzone.com](https://dzone.com/articles/why-we-should-follow-method-overriding-rules?edition=347123&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-26)_

[Download Microservices for Java Developers](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034): A hands-on introduction to frameworks and containers. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034).

In my previous articles , I discussed method overloading and the rules we need to follow to overload a method. I also discussed why we need to follow these rules and why some method overloading rules are necessary and others are optional.

In a similar manner, in this article, we will see what rules we need to follow to override a method and why we should follow these rules.

## Method Overriding and its Rules

As discussed in [Everything About Method Overloading vs Method Overriding](https://programmingmitra.blogspot.in/2017/05/everything-about-method-overloading-vs-method-overriding.html), every child class inherits all the inheritable behavior from its parent class -- but the child class can also define its own new behaviors or override some of the inherited behavior.

Overriding means redefining a behavior (method) again in the child class that was already defined by its parent class.

But to do so the overriding method in the child class must follow certain rules and guidelines.

With respect to the method it overrides, the overriding method must follow these rules.

![Why We Should Follow Method Overriding Rules](https://3.bp.blogspot.com/-hhpGgaXYUgg/WjqobOrC3PI/AAAAAAAAMr8/HMu27uIEnLg9MkvYSGfxYy_8mjc0ZEq8QCK4BGAYYCw/s1600/method-overriding-rules.JPG)

> _Why We Should Follow Method Overriding Rules_

To understand these reasons properly, let's consider the following example where we have class Mammal that defines a readAndGet method, which is reading some file and returning an instance of class Mammal.

Class Human extends class Mammal and overrides the readAndGet method to return an instance of Human instead of an instance of Mammal.

And we know that in the case of method overriding, we can make polymorphic calls. That means if we assign a child instance to a parent reference and call an overridden method on that reference, eventually, the method from the child class will get called.

Let's do that:

As discussed in [How Does the JVM Handle Method Overloading and Overriding Internally](https://programmingmitra.blogspot.in/2017/05/how-does-jvm-handle-method-overriding-internally.html), until the compilation phase, the compiler thinks the method is getting called from the parent class. Meanwhile, the bytecode generation phase compiler generates a constant pool where it maps every method string literal and class reference to a memory reference

During runtime, the JVM creates a vtable, or virtual table, to identify which method is getting called. The JVM creates a vtable for every class, and it is common for all the objects of that class. The Mammal row in a vtable contains the method name and memory reference of that method.

First, the JVM creates a vtable for the parent class and then copies that parent's vtable to the child class's vtable and updates just the memory reference for the overloaded method while keeping the same method name.

So as of now, we are clear that

  * For the compiler, `mammal.readAndGet()` means the method is getting called from an instance of class `Mammal`
  * For the JVM, `mammal.readAndGet()` is getting called from a memory address, which a `vtable` is holding for `Mammal.readAndGet()`, which is pointing to a method call from class `Human`

## The Same Name and Argument List

Conceptually, Mammal is pointing to an object of class Human, and we are calling the readAndGet method on Mammal. So, to get this call resolved at runtime, Human should also have a readAndGet method. If Human has inherited that method from Mammal, then there is no problem. But if Human is overriding readAndGet, it should provide the same method signature as provided by Mammal because the method has been already been called, according to that method signature.

But you may be asking how it is handled physically from vtables. The JVM creates a vtable for every class, and when it encounters an overriding method, it keeps the same method name (Mammal.readAndGet()) while just updating the memory address for that method. So both the overridden and overriding methods must have the same method and argument list.

## The Same or Covariant Return Type

So we know that, for the compiler, the method is getting called from class Mammal. Meanwhile, for the JVM, the call is from the instance of class Human. But in both cases, the readAndGet method call must return an object that can be assigned to obj. And since obj is of the type Mammal, it can either hold an instance of the Mammal class or an instance of a child class of Mammal (children of Mammal are covariant to Mammal).

Now suppose the readAndGet method in the Human class is returning something else. During compile time, mammal.readAndGet() will not create any problems. But at runtime, this will cause a ClassCastException because at runtime, mammal.readAndGet() will get resolved to a new Human().readAndGet() -- and this call will not return an object of type `Mammal`.

And this why having a different return type is not allowed by the compiler in the first place.

## More Restrictive Access Modifiers

The same logic is applicable here as well. The call to the readAndGet method will be resolved at runtime, and as we can see, readAndGet is public in class Mammal. Now suppose:

  * If we define `readAndGet` as `default` or `protected` in `Human`, but Human is defined in another package
  * If we define `readAndGet` as `private` in `Human`

In both cases, the code will compile successfully because, for the compiler, readAndGet is getting called from class Mammal. But in both cases, the JVM will not be able to access readAndGet from Human because it will be restricted.

So to avoid this uncertainty, assigning restrictive access to the overriding method in the child class is not allowed at all.

## Less Restrictive Access Modifiers

If the readAndGet method is accessible from Mammal and we are able to execute mammal.readAndGet(), that means this method is accessible. And if we make readAndGet accessible from the less restrictive Human, that means it will be more open to getting called.

So, making the overriding method less restrictive cannot create any problems in the future, and it is allowed.

## Checked Exceptions

Because `IOException` is a checked exception, the compiler will force us to catch it whenever we call `readAndGet` on Mammal.

Now suppose `readAndGet` in `Human` is throwing any other checked exception, e.g. `Exception`, and we know `readAndGet` will get called from the instance of `Human` because `Mammal` is holding `new Human()`.

For the compiler, the method is getting called from `Mammal`, so the compiler will force us to handle only IOException, but at runtime, we know the method will be throwing an `Exception` that is not getting handled -- and our code will break if the method throws an exception.

That's why it is prevented at the compiler level itself and we are not allowed to throw any new or broader checked exception -- because it will not be handled by the JVM in the end.

But if readAndGet in Human throws any sub-exception of IOException, e.g., `FileNotFoundException`, it will be handled because `catch (IOException ex)` can handle all children of `IOException`.

And we know unchecked exceptions (subclasses of `RuntimeException`) are called unchecked because we don't necessarily need to handle them.

And that's why overriding methods are allowed to throw narrower checked and other unchecked exceptions.

To force our code to adhere to method overriding rules, we should always use the @Override annotation on our overriding methods. The @Override annotation forces the compiler to check if the method is a valid override or not.

You can find the complete code on this [GitHub Repository](https://github.com/njnareshjoshi/exercises/blob/master/src/org/programming/mitra/exercises/OverridingInternalExample.java), and please feel free to provide your valuable feedback.

[Download Building Reactive Microservices in Java](https://dzone.com/go?i=219225&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F166031): Asynchronous and Event-Based Application Design. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=219225&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F166031).
