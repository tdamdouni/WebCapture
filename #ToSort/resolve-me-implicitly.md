# Resolve Me, Implicitly

_Captured: 2017-11-11 at 00:39 from [dzone.com](https://dzone.com/articles/resolve-me-implicitly?edition=334862&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-10)_

Reading my posts, you can easily find that there is a topic that I care about a lot: Dependency management in the development process. There is a feature of the Scala programming language that I've liked since the beginning. Without any external library, it is possible to successfully implement various dependency injection mechanisms. In the past, I wrote about the [Cake pattern](http://rcardin.github.io/design/2014/08/28/eat-that-cake.html). Now it's time to talk about dependency injection through the use of implicits. Let's start the race!

## The Problem: Dependency Injection

### Dependency

I have written many times about this topic, so I will not make a long introduction. To summarize, every time a component needs to send a message to another component, a dependency is defined between them. Components may be packages, classes, functions, and so on. Messages are always associated with methods or functions calls. Dependency between two components can have many levels of strength. If you want a complete explanation of the dependency concept, have a look at this post: [Dependency](http://rcardin.github.io/programming/oop/software-engineering/2017/04/10/dependency-dot.html). For the sake of completeness, let's give an example of the simplest type of dependency: Association.

An association means that a class is _made of_ references to other classes.

### Dependency Injection

Other than the coupling between components that derives from dependencies, the problem with dependencies is the process that a component has to take place to resolve them. Dependency resolution is a complex problem. To treat it successfully, the best thing to do is to apply the _divide et impera_ principle.

Dependency resolution can be divided into two different tasks: dependency declarations and resolution.

![Resolve your declared dependencies](https://i.imgflip.com/1xlkmb.jpg)

First of all, a component should be able to declare its dependencies. A component should be able to scream "_Hey, anybody listening, I need these f*cking classes to work!_" There are many ways a component may choose to declare its dependencies. The most accredited by the developer community is _constructor injection_.

Using constructor injection, a component declares its dependencies as the parameters of its constructor.

In the above example, the class `Connection` is screaming to everyone that it needs an instance of an `ActorSelection` class to work properly.

If you want to know which other types of dependency declarations are available, please have a look at the post [Resolving your problems with Dependency Injection](http://rcardin.github.io/programming/software-design/java/scala/di/2016/08/01/resolve-problems-dependency-injection.html).

Now that we know how to declare which kinds of objects a component needs to work, we also need a technique to resolve these objects. And it's here that the "_injection_" part comes into play.

## Resolving Dependencies in Scala

In the JVM ecosystem, there are a lot of libraries that implement the injection technique. We have many alternatives, such as the following.

  1. Spring Framework
  2. Guice
  3. Weld
  4. Dagger 2

There is also a JSR dedicated to dependency injection, [JSR 330](https://jcp.org/en/jsr/detail?id=330). As you can see, the JDK needs external libraries to implement the dependency injection mechanism.

But, **Scala is different**. The Scala programming language has a richer semantic that allows implementing dependency injection mechanisms without the need for any kind of external library. As you we will see in a moment, this technique applies both to classes and to functions. That's awesome!

In the past, I wrote about the [Cake Pattern](http://rcardin.github.io/design/2014/08/28/eat-that-cake.html), which implements dependency resolution using traits and [self-type](https://docs.scala-lang.org/tour/self-types.html). This time, I want to write about a dependency injection mechanism that uses two other features of Scala, _function currying_ and _implicits_.

As you know, Scala is known as a functional programming language. Functional programming languages have many nice features. One of these features is function currying.

Let's take, for example, a function that takes two arguments:

We can refactor this function into a new one that takes only one parameter and returns a new function.

To multiply two integers, you have to call the last function in the following way.

We said the function `mulOneAtTime` is equal to the curried function of the original function `mul`.

> In mathematics and computer science, currying is the technique of translating the evaluation of a function that takes multiple arguments (or a tuple of arguments) into evaluating a sequence of functions, each with a single argument.

There is a shortcut for defining such curried function in Scala:

The language saves us from defining a lot of intermediate functions, giving us some vanilla-flavored syntactic sugar.

I suppose that you are asking why are we talking about currying instead of dependency injection. Be patient.

![Function currying be like](https://i.imgflip.com/1xlkul.jpg)

Implicits are another awesome feature of the Scala programming language. Hated by some and feared by most, implicits can be applied to resolve a lot of problems -- from automatic conversion between two types to the automatic resolution of dependencies. What we are going to explain is how _implicit parameters_ work in Scala.

The parameters of a function (or a method) can be marked with the keyword `implicit`. In this case, the _compiler_ will automagically look for a value to supply to these parameters. Here is a simple example of a function using an `implicit` parameter, taken directly from the Scala SDK:

In the above example, the parameter `execctx` of the method `apply` is automatically resolved and provided by the compiler to the program. How does the Scala compiler know how to resolve `implicit` parameters? It searches for an object that has the same type of an `implicit` parameter and that is declared using the word `implicit`. In the case of `execctx` in the `object scala.concurrent.ExecutionContext.Implicits`, it is defined with the constant `global`.

During implicit resolution, the compiler searches for `var/val/def` that are available in the same scope of the function as some parameters marked as `implicit`.

Implicit resolution is also one of the reasons why the Scala compiler is so slow. In fact, implicit resolution has no impact on runtime performance, as it is done completely at compile time. For a more detailed explanation of implicit resolution, have a look at [Implicit Parameter Resolution](http://daily-scala.blogspot.it/2010/04/implicit-parameter-resolution.html).

![Implicits, implicits everywhere](https://i.imgflip.com/1xll84.jpg)

So far, so good. We just added another piece to our dependency injection puzzle. Now it's time to put all the ingredients together and bake a tasty dependency injection cake.

### Dependency Injection Using Implicits

Until now, we learned how to curry a function and how implicits work in Scala. It's time to put them all together.

As you probably already understood, we can use implicits to instruct the compiler to automatically resolve component dependencies. Let's start with types. We have already learned that dependencies of a class should be declared in its constructor. We learned that for every parameter of a function or method that is marked as `implicit`, the compiler searches for an object of the same type in the appropriate scope.

In the above example, we declared a `SimpleUserService` class, which declares as its unique external dependency an instance of the type `UserRepository`. The dependency is marked as `implicit`. To let the compiler properly resolve this dependency, we have to provide an object of type `UserRepository` marked as `implicit` in the same scope of the clients of the class `SimpleUserService`.

We have declared also a `UserService` trait over the class so that clients of this class do not have to deal with the boilerplate code of implicits.

We have two main possibilities to provide this information to the compiler. The first is to use a _configuration trait_ to mix with every class that declares an implicit dependency.

We chose to mix the trait into the _companion object_ of the class to avoid replication of the instances of the variable `repository`.

The second approach is to use a package object placed in the same package of the class `UserController`.

Using the latter approach, the definition of the object `UserController` is not polluted by any external and strange extensions. The drawback is that it becomes harder to trace how each implicit parameter is resolved by the compiler.

![Y U not explicit the implicits!](https://i.imgflip.com/1xn1z9.jpg)

Easy enough! We have just implemented dependency injection in Scala using implicits! Wow! But, wait: Why did we also introduce function currying? We did not use it.

The secret is soon unveiled. The above examples consider dependency injection in _object-oriented programming_. But, what about _functional programming_? In functional programming, there is the same requirement for functions to declare and resolve their dependencies. In this world, the only way to declare a dependency is to put it into the signature. In this way, a client of the function can provide the needed dependency at the same time as the function call.

To clearly divide the inputs of the functions and the declaration of dependencies, avoiding polluting the signature, we can use currying.

Finally, to let the compiler to automatically resolve the dependencies, we can use implicits, as we did for the object-oriented case. This technique is called _implicit parameters_.

## Conclusions

"_This is the end, my only friend, the end._" We just analyzed the techniques we can use to natively implement dependency injection in Scala: implicits. We analyzed in detail the features of the language that help us to achieve our goal: implicits and function currying. We showed an example both using object-oriented programming and functional programming.

Different from the Cake Pattern, implicits give us a mechanism to implement dependency injection that is concise and sexy.

> Dependencies are resolved at compile-time, you write less code, there is no boilerplate, classes are loosely coupled, everything is extendable yet still typesafe.

On the other hand, implicit resolution can become hard to understand and maintain very quickly.

> It is common to use package objects with implicits, so there is no way to eyeball that this small import on top of a file feeds several function calls with implicit variables. Even worse, it is impossible to understand from code that this particular function call needs implicits.

As for any other technique in programming, we always have to compare pros and cons. In my opinion, if used properly, implicits offer more pros than cons. What do you think? Anybody with some bad story about implicits out of there? Cheers.

## References
