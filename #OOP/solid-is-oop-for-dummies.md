# SOLID Is OOP for Dummies

_Captured: 2017-04-01 at 21:13 from [dzone.com](https://dzone.com/articles/solid-is-oop-for-dummies?edition=286969&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-01)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

You definitely know the [SOLID](https://en.wikipedia.org/wiki/SOLID_%28object-oriented_design%29) acronym. It stands for five principles of [object-oriented programming](http://www.yegor256.com/2016/08/15/what-is-wrong-object-oriented-programming.html) that, if followed, are supposed to make your code both [legible and extensible](https://en.wikipedia.org/wiki/SOLID_%28object-oriented_design%29). These principles were introduced almost 30 years ago, but have they really made us better programmers in the time since? Do we really understand OOP better thanks to them? Do we write more "legible and extensible" code? I don't think so.

Let's go one by one and see how they "help."

## S

The "S" refers to the [Single Responsibility Principle](https://en.wikipedia.org/wiki/Single_responsibility_principle), which, according to [Clean Code](http://amzn.to/2m7LmaA) by [Robert Martin](https://en.wikipedia.org/wiki/Robert_Cecil_Martin), means that "a class should have only one reason to change."

This statement sounds extremely vague to me, but the book explains it, stating that objects must be problem-centered and responsible for "one thing." It's up to us to decide what that _one thing_ is, of course.

This is what we know as "[high cohesion"](https://en.wikipedia.org/wiki/Cohesion_%28computer_science%29) since [Larry Constantine](https://en.wikipedia.org/wiki/Larry_Constantine) wrote about it in the IBM Systems Journal in 1974. Why was it necessary to create a new principle 15 years later with an ambiguous name and a very questionable definition?

## O

This letter is about the [Open/Close Principle](https://en.wikipedia.org/wiki/Open/closed_principle), which was introduced by Bertrand Meyer in [Object Oriented Software Construction](http://amzn.to/2lNxy44) in 1988. Simply put, it means that an object should not be modifiable. I can't agree more with this.

But then it says it should be _extendable_, literally through [implementation inheritance](https://en.wikipedia.org/wiki/Inheritance_%28object-oriented_programming%29), which is [known](http://www.yegor256.com/2016/09/13/inheritance-is-procedural.html) as an anti-OOP technology. Thus, this principle is not really applicable to objects and OOP. It may work with modules and services, but not with objects.

## L

The third letter stands for the [Liskov Substitution Principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle), which was introduced by [Barbara Liskov](https://en.wikipedia.org/wiki/Barbara_Liskov) in 1987. This one is the most innocent part in the SOLID pentad. Simply put, it states that if your method expects a `[Collection`](http://docs.oracle.com/javase/7/docs/api/java/util/Collection.html), an `[ArrayList`](http://docs.oracle.com/javase/7/docs/api/java/util/ArrayList.html) will work.

It is also known as [subtyping](https://en.wikipedia.org/wiki/Subtyping) and is the foundational component of any object-oriented language. Why do we need to call it a principle and "follow" it? Is it at all possible to create any object-oriented software without subtyping? If this one is a principle, let's add "variables" and "method calling" here too.

Honestly, I suspect that this principle was added to SOLID mostly in order to somehow fill the gap between "SO" and "ID."

## I and D

I guess they both were introduced by [Robert Martin](https://en.wikipedia.org/wiki/Robert_Cecil_Martin) while he was working at Xerox.

The [Interface Segregation Principle](https://en.wikipedia.org/wiki/Interface_segregation_principle) states that you must not declare `List x` if you only need `Collection x` or even `Iterable x.` I can't agree more. Let's see the next one.

The [Dependency Inversion Principle](https://en.wikipedia.org/wiki/Dependency_inversion_principle) means that instead of `ArrayList x,` you must declare `List x` and let the provider of the object decide whether it is an `[ArrayList`](http://docs.oracle.com/javase/7/docs/api/java/util/ArrayList.html) or a `[LinkedList`](http://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html). This one also sounds reasonable to me.

However, how is all this different from the good old "[loose coupling"](https://en.wikipedia.org/wiki/Coupling_%28computer_programming%29) introduced together with cohesion by Constantine in 1974? Do we really need to simplify and blur in order to learn better? No, not to learn better, but to _sell_ better. Here goes my point.

## My Point Is...

The point being these principles are nothing but an explanation of "cohesion and coupling" for dummies in a very primitive, ambiguous, and marketable way. Dummies will buy books, seminars, and trainings, but won't really be able to understand the logic behind them. Do they really need to? They are just monkeys [coders](http://www.yegor256.com/2014/10/26/hacker-vs-programmer-mentality.html), right?

SOLID is a money-making instrument, not an instrument to make code better. 

"But an object must be responsible for one thing!" is what I often hear at conferences. People learn that mantra without even knowing what cohesion is nor understanding what this "one thing" they are praying for really is. There is no such thing as "one thing," guys! There are different levels of cohesion.

Who is guilty? Uncle Bob and Co.

They are no better than [Ridley Scott](http://www.yegor256.com/2015/10/16/ridley-scott-and-joseph-goebbels.html) and other Hollywood money makers who deliver primitive and easy-to-cry-at movies just to generate a profit. People are getting dumber by watching--but this is not of their concern. The same happens with magic OOP principles--programmers rely on them, thinking the truth is right there while the real truth is not understood even by the creators of this "magic."

SOLID is a money-making instrument, not an instrument to make code better.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
