# Object-Oriented Programming Strikes Back!

_Captured: 2017-08-07 at 08:16 from [dzone.com](https://dzone.com/articles/object-oriented-programming-strikes-back?edition=313395&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-06)_

### There is not an absolute right or absolute wrong opinion on this dilemma. But here is why I think there is a misunderstanding of what functional programming really is.

The single app analytics solutions to [take your web and mobile apps to the next level.](https://dzone.com/go?i=208121&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143155%3Bdc_trk_aid%3D322361301%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) Try today! Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=208121&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143155%3Bdc_trk_aid%3D321036346%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

_Disclaimer: The post contains some humor. If you are sensible to humorism, please, do not continue to read._

Recently, I read the article [Beginning to Doubt Object-Oriented Programming](https://dzone.com/articles/beginning-to-doubt-object-oriented-programming-1) on DZone. It is not the first post that I find on a blog that praises functional programming with respect to object-oriented programming. For all of these posts, object-oriented programming is dead (more or less). I think that at the basis of all these posts there is a misunderstanding of what functional programming really is. Now it's time for me to give my two cents to the fight among different programming paradigms.

First of all, I want to say that I respect the opinion of the author of the above article. What I am going to say it is my personal point of view on the issue. There is not an absolute right or absolute wrong opinion on this dilemma. So, peace and love to everyone.

## What Is Functional Programming?

I think that to better understand my point of view on functional programming, it is important to first understand what I mean with this term.

In computer science, functional programming is a programming paradigm [..] that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.

This is the definition given by Wikipedia. Did you read any references to _lambda expression_? Nope. So, abusing of lambda expression in your code does not mean you're using functional programming paradigm.

![Batman does not like functional bulls!](https://i.imgflip.com/1sy6bf.jpg)

First of all, you need referential transparency, which means that any time a function is called with the same inputs must return the same output. A precondition to implement referential transparency correctly is the immutability of state. Once a structure (can we say a type?) is created, it cannot be subsequently modified in any way.

Easy? Referential transparency means no side effects, no exceptions thrown, no reading from external sources and so on. How can we be productive without these capabilities?

## The Hard Part of the Story

It seems that we are stuck in a black hole, doesn't it? I cannot have side effects inside a function (not that bad), I cannot signal to function callers that something could go wrong, I cannot access to any external resources. Oh Gosh!

Have you ever heard about _Monoids_, _Functors_, _Monads_? These are structures coming directly from _category theory_, a branch of Mathematics. Describing these structures are behind the scope of this post, but let's do some examples.

I know for sure that you are using at least some Monads in your code. If you are a Scala developer, probably you used `Option[T]` type, or `Either[T, E]`, or any kind of collection such as `List[T]`, `Set[T]` and so on. If you are a Java developer you can take into consideration types like `Optional<T>`, `Collection<T>` and `Stream<T>`. All of these types are Monads.

These types have nothing in common from a behavioural point of view, which means that Monads are a mechanisms to share some properties (basically, code reuse) among different types that are not directly related to each others. What does this mean? Quoting the book [Scala Design Patterns](https://www.amazon.com/Scala-Design-Patterns-Ivan-Nikolov/dp/1785882503),

_monads are structures that represent computation as sequences of steps. Monads are useful for building pipelines, adding operations with side effects cleanly to a language where everything is immutable._

Let's borrow the definition of Monads from the excellent book [Functional Programming in Scala](https://www.manning.com/books/functional-programming-in-scala).

_A monad is an implementation of one of the minimal sets of monadic combinators (i.e. `unit` and `flatMap`), satisfying tha laws of associativity and identity._

Monadic combinators? Associativity? Identity? Unicorn? Wtf?!!? I am a simple developer: I hear about mathematics, I change programming paradigm.

![Functional programming is easy :P](https://i.imgflip.com/1sydmc.jpg)

Where do I want to go with this dissertation? The real functional programming really deals with mathematical laws and theories. If you develop your programs following these laws, you will benefit of a bunch of good properties, such as composability, testability, thread confinement, coming directly from mathematical theory.

However, you need to study and learn mathematics. Little drops of Category theory will wet your face.

## Object-Oriented Programming

What about Object Oriented programming? Have you ever heard about boring mathematical laws you have to follow? Have you ever heard about esoteric terms like monads or functors, or anything else? Have you ever applied some mathematic theory to your object oriented programs?

Nope. The beautiful thing about object oriented programming is that is almost math-free. Everyone can start to study and learn an object oriented programming language such as Java, C++ or Kotlin. At first sight, object orientated programming is very close to how we perceive reality.

As human beings living in the lucky part of the world, we know that every car is made by an engine, some wheels, a body and so on. We understand what a `Car` type means and why it owns attributes of type `Engine`, `Wheel` and `Body`.

Object oriented programming is easier to learn than functional programming. Stop. This is the only truth. Both paradigms exist more or less from the beginning of Computer era (think about Lisp, for example, which is born in 1958). Have you ever heard about an operating system written in a functional programming language? Nope.

## Simplicity Leads to Tradeoffs

Simpler means less constrained. Less constrained means less formality to respect. Less formality means that is simpler to use the programming language's features in an erroneous way.

Take the definition of monads that we gave just a moment ago. In the definition the constraints that a type must fulfill to be considered a monad are clear. Math does not lie.

Now, take any principle of object oriented programming: For example, the Single Responsibility Principle. The principle states that

A class should have only one reason to change.

What the f**ck is a _reason to change_? Where is all the mathematical magic that principles that apply to functional programming languages have? No trace.

Neither the definition of _coupling_, which is at the base of all the theories related to object oriented programming, is defined in a formal way.

Coupling between components measures exactly their degree of dependency.

Ok, so, how can I measure the degree of dependency between components? No formal way. I tried to give a mathematical definition of such concepts in one of my past posts, [Dependency](http://rcardin.github.io/programming/oop/software-engineering/2017/04/10/dependency-dot.html), but it was only an attempt.

The lack of rigorousness in principles definitions leads to principles' interpretation. Personal interpretation often leads to errors and bad practices.

## Conclusion

Having discussed the differences between functional programming and object oriented programming paradigms we discover and understand an important concept, which is:

_The more a programming language is easy to learn, the easier it is to make mistakes using it._

The following graph tries to show visually the meaning of this sentence.

![Programming language curve](http://rcardin.github.io/assets/2017-08-01/programming_languages_curve.png)

Finally, object oriented programming languages are not going anywhere. We will continue to use them because they are easy to learn. Also, functional programming languages are here to stay. Every time we need to ensure some nice properties relative to our programs, they will help us a lot.

The world is full of trade-off. So, stop this war among programming paradigms and start to get the best from both sides of the force.

CA App Experience Analytics, a whole new level of visibility. [Learn more.](https://dzone.com/go?i=208122&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143157%3Bdc_trk_aid%3D322361143%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=208122&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143157%3Bdc_trk_aid%3D322361143%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
