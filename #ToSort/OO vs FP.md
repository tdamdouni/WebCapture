# The Clean Code Blog

_Captured: 2015-10-17 at 21:46 from [blog.cleancoder.com](http://blog.cleancoder.com/uncle-bob/2014/11/24/FPvsOO.html)_

# OO vs. FP

A friend of mine posted the following on facebook. He meant it as a troll; and it worked, because it _irked_ me.

![](http://blog.cleancoder.com/uncle-bob/images/fpvsoo.jpg)

There are many programmers who have said similar things over the years. They consider Object Orientation and Functional Programming to be mutually exclusive forms of programming. From their ivory towers in the clouds some FP super-beings occasionally look down on the poor naive OO programmers and cluck their tongues.

That clucking is echoed by the OO super-beings in _their_ ivory towers, who look askance at the waste and parentheses pollution of functional languages.

These views are based on a deep ignorance of what OO and FP really are.

Let me make a few points:

  * **OO is not about state**.

Objects are not data structures. Objects may _use_ data structures; but the manner in which those data structures are used or contained is hidden. This is why data fields are private. From the outside looking in you cannot see any state. All you can see are functions. Therefore Objects are about functions not about state.

When objects are used as data structures it is a _design smell_; and it always has been. When tools like _Hibernate_ call themselves object-relational mappers, they are incorrect. ORMs don't map relational data to objects; they map relational data to data structures. Those data structures _are not objects_.

Objects are bags of functions, not bags of data.

  * **Functional Programs, like OO Programs, are composed of functions that operate on data.**

Every functional program ever written is composed of a set of functions that operate on data. Every OO program ever written is composed of a set of functions that operate on data.

It is common for OO programmers to define OO as functions and data bound together. This is true so far as it goes; but then it has _always_ been true irrespective of OO. All programs are functions bound to data.

You might protest and suggest that it is the _manner_ of that binding that matters. But think about it. That's silly. Is there really so much difference between `f(o)`, `o.f()`, and `(f o)`? Are we really saying that the difference is just about the syntax of a function call?[0]

## The Differences

So what are the differences between OO and FP? What does OO have that FP doesn't, and what does FP have that OO doesn't?

  * **FP imposes discipline upon assignment.**

A true functional programming language has no assignment operator. You cannot change the state of a variable. Indeed, the word "variable" is a misnomer in a functional language because you cannot vary them.

Yes, I know, Funcitonal Programmers often say hi-falutin' things like "Functions are first-class objects in functional languages." That may be true; but functions are first-class objects in Smalltalk, and Smalltalk is an OO language, not a functional language.

The overriding difference between a functional language and a non-functional language is that functional languages don't have assignment statements.[1]

Does this mean that you can _never_ change the state of something in a functional language? No, not at all. Functional languages generally offer ceremonies that you can perform in order to change the state of something. F# allows you to declare "mutable variables" for example. Clojure allows you to create special, uh, objects who's values can be changed using various magic incantations.

The point is that a functional language imposes some kind of ceremony or discipline on changes of state. You have to jump through the right hoops in order to do it.

And so, for the most part, you don't.

  * **OO imposes discipline on function pointers.**

"Huh?" you say. But that, in fact, is what OO comes down to. For all the hi-falutin' rhetoric about OO and "real-world objects" and "programming closer to the way we think", what OO really comes down to is that OO languages replace function pointers with convenient polymorphism. [2]

How do you implement polymorphism? You implement it with function pointers. OO languages simply do that implementation for you, and hide the function pointers from you. This is nice because function pointers are very difficult to manage well. Trying to write polymorphic code with function pointers (as in C) depends on complex and inconvenient conventions that everyone must follow _in every case_. This is usually unrealistic.

In Java, every function you call is polymorphic. There is no way you can call a function that is _not_ polymorphic. And that means that every java function is called _indirectly_ through a pointer to a function.[3]

If you wanted polymophism in C, you'd have to manage those pointers yourself; and that's hard. If you wanted polymorphism in Lisp you'd have to manage those pointers yourself (pass them in as arguments to some higher level algorithm (which, by the way _IS_ the **Strategy** pattern.)) But in an OO language, those pointers are managed for you. The language takes care to initialize them, and marshal them, and call all the functions through them.

## Mutually Exclusive?

Are these two disciplines mutually exclusive? Can you have a language that imposes discipline on both assignment and pointers to functions? Of course you can. These two things don't have anything to do with each other. And that means that OO and FP are _not_ mutually exclusive at all. It means that you can write OO-Functional programs.

It also means that all the design principles, and design patterns, used by OO programmers can be used by functional programmers if they care to accept the discipline that OO imposes on their pointers to functions.

But why would a functional programmer do that? What benefit does polymorphism have that normal Functional Programs don't have? By the same token, what benefit would OO programmers gain from imposing discipline on assignment?

## Benefits of Polymorphism.

There really is only one benefit to Polymorphism; but it's a big one. It is the inversion of source code and run time dependencies.

In most software systems when one function calls another, the runtime dependency and the source code dependency point in the same direction. The calling module depends on the called module. However, when polymorphism is injected between the two there is an inversion of the source code dependency. The calling module still depends on the called module at run time. However, the source code of the calling module does not depend upon the source code of the called module. Rather both modules depend upon a polymorphic interface.

This inversion allows the called module to act like a plugin. Indeed, this is how all plugins work.

Plugin architectures are very robust because stable high value business rules can be kept from depending upon volatile low value modules such as user interfaces and databases.

The net result is that in order to be robust a system must employ polymorphism across significant architectural boundaries.

## Benefits of Immutability

The benefit of not using assignment statements should be obvious. You can't have concurrent update problems if you never update anything.

Since functional programming languages do not have assignment statements, programs written in those languages don't change the state of very many variables. Mutation is reserved for very specific sections of the system that can tolerate the high ceremony required. Those sections are inherently safe from multiple threads and multiple cores.

The bottom line is that functional programs are much safer in multiprocessing and multiprocessor environments.

## The Deep Philosophies

Of course adherents to both Object Orientation and Functional Programming will protest my reductionist analysis. They will contend that there are deep philosophical, psychological, and mathematical reasons why their favorite style is better than the other.

My reaction to that is: _Phooey!_

Everybody thinks their way is the best. Everybody is wrong.

## What about Design Principles, and Design Patterns?

The passage at the start of this article that _irked_ me suggests that all the design principles and design patterns that we've identified over the last several decades apply only to OO; and that Functional Programming reduces them all down to: _functions._

Wow! Talk about being reductionist!

This idea is bonkers in the extreme. The principles of software design still apply, regardless of your programming style. The fact that you've decided to use a language that doesn't have an assignment operator does not mean that you can ignore the Single Responsibility Principle; or that the Open Closed Principle is somehow automatic. The fact that the Strategy pattern makes use of polymorphism does not mean that the pattern cannot be used in a good functional language[4].

The bottom, bottom line here is simply this. OO programming is good, when you know what it is. Functional programming is good when you know what it is. And functional OO programming is also good once you know what it is.

  * [0] I imagine there are a few python programmers who might have something to say about that.
  * [1] This, of course, means that Scala is not a "true" functional language.
  * [2] This, of course, means that C++ is not a "true" OO language.
  * [3] Yeah, don't say it, I know. OK, an "analog" to a pointer to a function. (sigh).
  * [4] A good functional language is one that allows for convenient polymorphism. Clojure is a good example.
