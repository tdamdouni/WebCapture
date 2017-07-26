# Object Oriented Tricks: #3 Death By Arguments

_Captured: 2017-04-26 at 09:08 from [hackernoon.com](https://hackernoon.com/object-oriented-tricks-3-death-by-arguments-d070ac86d996?source=userActivityShare-c79006fee040-1493190492)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*vfNMIYvU89Hr0P0I9aYGJQ.png?q=20)![](https://cdn-images-1.medium.com/max/800/1*vfNMIYvU89Hr0P0I9aYGJQ.png)

OOT is a mini series on writing maintainable Object Oriented code without pulling your hair out. Click here for [trick #1](https://hackernoon.com/oo-tricks-the-art-of-command-query-separation-9343e50a3de0), [trick #2](https://hackernoon.com/object-oriented-tricks-2-law-of-demeter-4ecc9becad85).

#### Arguments Arguments Arguments

  * Lengthy list of function arguments are tedious for the calling code to use. It also makes it all too easy to pass arguments in the wrong order with little type safety, and can reduce readability of the code.
  * They are hard to read and hard to understand till you double take on the function signature every time you call it.

> "Each one can confuse and confound, breaking your flow as you're reading down the code, causing you to double-take." -- Uncle Bob Martin

  * _Arguments make it harder to test a function._ It's difficult to write all the test cases ensuring all the various combinations of arguments work properly.

So rather than using them recklessly as conveniences, we should apply a significant amount of restraint and treat each argument as a liability.

#### Structure

The best functions have as few arguments as possible. Ideally zilch.
    
    
    niladic > monadic > dyadic > triadic > polyadic

The same guidelines apply for constructors.

#### Always Be Refactoring

  * **Argument Objects: **If you pass three or more arguments in your functions, then stop and think. If three or more variables are so cohesive that they can be passed together into a function, why aren't they an object? <https://www.refactoring.com/catalog/introduceParameterObject.html>
  * **Overloading:** One reason to overload functions is so that a client can call the appropriate version of the function for supplying just the necessary parameters.
  * **Builder Pattern: **Sometimes function overloading goes out of hand and leads to a situation called a [Telescoping Constructor anti-pattern](http://codethataint.com/blog/telescoping-constructor-pattern-java/). To avoid this, in the Second Edition of [Effective Java](http://www.pearsonhighered.com/educator/product/Effective-Java/9780321356680.page), Josh Bloch introduces use of the builder pattern for dealing with constructors that require too many parameters.
  * **Mutable State: *Not Recommended*  
**Perhaps the best known and most widely scorned approach in all of software development for using state to reduce parameter methods is the use of global, instance variables. Although not the best solution, but may be appropriate in some cases. Use with caution especially in highly concurrent programs.

> "Any global data is always guilty until proven innocent." -- Martin Fowler

#### Death By Booleans

Most of the time when you pass a `boolean` into a function, you are loudly declaring to the world that you've written a function that _does two things. _One thing for the `true` case and another for the `false` case. Instead, you should have written two functions, one for each case.

A boolean hanging out in the argument list can be a huge source of error and confusion. What does it mean if it's true? What does it mean if it's false? If the name of the function and the argument fail to make this perfectly clear, then every time you use this function, you need to dive into the implementation details to understand the right value to be passed. Passing in two booleans is even worse. A function that takes two booleans does four things!

Try guessing the booleans, their order and the behaviour:

![](https://cdn-images-1.medium.com/max/800/1*hA6jR813fqBk7bwBxLTLEA.png)

Makes you squint, doesn't it? Avoid guesses and double-takes by using the Builder Pattern:

#### The Null Defense

Passing `null` to a function or writing a function that expects `null` to be passed in is almost as bad as passing a boolean into it. In fact, it's even worse as it is not at all obvious that there are _just_ 2 possible states.

Ofcourse, there is behaviour for the non-null case and one for the null case. A better approach is to create two functions, one that takes a non-null argument and the other that doesn't take that argument at all. Don't use `null` as a pseudo-boolean.

> _Listen to Gandalf. Null args shall not pass._

Let's be honest, defensive programming sucks. It's horrible to litter code with null checks and error checks. We don't want to think that our teammates carelessly allowed to slip `null` into our functions. It also mean that we don't trust our unit tests that prevent us from passing that `null`.

This doesn't apply for public APIs, as we don't know who is gonna pass what. If your language supports the `@NotNull` annotation or a similar concept, use it to mark your public functions and you can _fail fast_ by throwing something like an `IllegalArgumentException`.

  


OOT is a mini series on writing maintainable Object Oriented code without pulling your hair out. Click here for [trick #1](https://hackernoon.com/oo-tricks-the-art-of-command-query-separation-9343e50a3de0).

![](https://cdn-images-1.medium.com/freeze/max/30/1*kvzV3t07oGAt-SKxqpmnhA.jpeg?q=20)![](https://cdn-images-1.medium.com/max/800/1*kvzV3t07oGAt-SKxqpmnhA.jpeg)

The are no real laws in programming, and that's sort of the only law. Law of Demeter(LoD) is more of a guideline than a principle to help reduce coupling between components.

#### Train Wrecks

We've all seen long chain of functions like these:
    
    
    obj.getX()  
          .getY()  
            .getZ()  
              .doSomething();

We _ask then ask then ask _before we _tell_ anything. Wouldn't it look better like this:
    
    
    obj.doSomething();

The call to `doSomething()` propagates outwards till it get's to `Z`. These long chains of queries, called train wrecks, violate something called the Law of Demeter.

#### Law of Demeter

LoD tells us that it is a bad idea for single functions to know the entire navigation structure of the system.

Consider how much knowledge `obj.getX().getY().getZ().doSomething()` has. It knows `obj` has an `X`, `X` has a `Y`, `Y` has a `Z` and that `Z` can do something. That's a huge amount of knowledge that this line has and it couples the function that contains it to too much of the whole system.

> "Each unit should have only limited knowledge about other units: only units "closely" related to the current unit. Each unit should only talk to its friends; don't talk to strangers."

When applied to object oriented programs, LoD formalizes the **_Tell Don't Ask _**principle with these set of rules:

> You may call methods of objects that are:  
1\. Passed as arguments  
2\. Created locally  
3\. Instance variables  
4\. Globals

Here `account.getPlan().getPrice()` violated the LoD. The most obvious fix is to delegate/_tell_:

#### Summary

We don't want our functions to know about the entire object map of the system. Individual functions should have a limited amount of knowledge. We want to tell our neighbouring objects what we need to have done and depend on them to propagate that message outwards to the appropriate destination.

Following this rule is very hard. Hence it is even been called as the **_Suggestion of Demeter _**because it's so easy to violate. But the benefits are obvious, any function that follows this rule, any function that _"tells"_ instead of _"asks"_ is decoupled from its surroundings.

Biological systems are an example of such systems. Cells don't ask each other questions, they tell each other what to do. We are an example of a _Tell Don't Ask_ system, **and within us the Law of Demeter prevails.**

### If you liked this post, please hit the little heart! ❤

As always, this post was inspired by Uncle Bob and his book **Clean Code.**
