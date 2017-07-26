# Object Oriented Tricks: #2 Law of Demeter

_Captured: 2017-04-26 at 09:10 from [hackernoon.com](https://hackernoon.com/object-oriented-tricks-2-law-of-demeter-4ecc9becad85?source=userActivityShare-c79006fee040-1493190611)_

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
