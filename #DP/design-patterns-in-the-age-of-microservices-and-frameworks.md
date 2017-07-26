# Design Patterns in the Age of Microservices and Frameworks

_Captured: 2017-06-30 at 07:14 from [dzone.com](https://dzone.com/articles/design-patterns-in-the-age-of-microservices-and-frameworks?edition=306191&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-29)_

### The Gang of Four were instrumental in solidifying the classic Java design patterns, but has their usefulness fallen off in a world with microservices and frameworks?

Find your next Integration job at [DZone Jobs](https://dzone.com/go?i=224226&u=https%3A%2F%2Fjobs.dzone.com%2Fjobs%2Fsearch%3Futf8%3D%25E2%259C%2593%26q%3DIntegration). See [jobs focused on integration](https://dzone.com/go?i=224226&u=https%3A%2F%2Fjobs.dzone.com%2Fjobs%2Fsearch%3Futf8%3D%25E2%259C%2593%26q%3DIntegration), or [create your profile](https://dzone.com/go?i=224226&u=https%3A%2F%2Fjobs.dzone.com%2Fprofiles%2Fsign_up) and have the employers come to you!

_[This article is featured in the new DZone Guide to Java: Development and Evolution. Get your free copy for more insightful articles, industry statistics, and more!_](https://dzone.com/guides/java-development-and-evolution)

We are in the age of web applications, frameworks, and microservices architectures. We can spin a module of our application within a day from zero to production. Any technical concern other than coding up our business rules has already been taken care of for us. We simply write the business rules, put them in a framework, and it works. What does that mean for design patterns? Do we still need them or we can safely put them in a museum?

## Back to the Roots

To answer the questions posed in the introduction, we will need to go back in time a little and answer other questions first. Why did we need the patterns in the first place? What problems did they solve back then? Do we still face these problems today? Each of the patterns has, of course, its own separate motivation and reason for existence, yet, in general, the goal is pretty much the same. We want our code to be as simple as possible, while at the same time, meeting all the users' current needs and ensuring future maintainability.

If we are to judge the usefulness of design patterns, we should look towards that general goal. Not flexibility, configurability, or any other fancy characteristic. These either lie within our users' current needs or they don't. These are either necessary for future maintainability or can be added later on in the project and therefore should be kept out for the sake of simplicity.

## Gang of Four Patterns

The GoF patterns have garnered a bad reputation in the industry. I suppose that's because of the typical developer learning process - we learn something new, overuse it, notice problems when it's too late, and only then use the thing with caution. The same can be said about design patterns. I remember my own feeling of enlightenment when I read the book for the first time. I saw the patterns EVERYWHERE. I was sure I could build entire applications using them almost exclusively.

All that being said, if we are to stay objective, we should forget this bad reputation and any bad memories associated with it. The fact that either we, or someone else, overused the Gang of Four's design patterns in the past has nothing to do with their usefulness. Taking this into account would be like demanding a ban of rope production because some people used ropes to hang themselves. Instead, we'll look towards our general goal from the previous section.

When it comes to coding up business rules and configuring frameworks, especially in a microservices (or even serverless) architecture, most of the GoF patterns are not very useful. Actually, it would be faster to enumerate those that might be. The strategy pattern is a good fit when there is a group of business algorithms to choose from. When the same conditionals start popping up in different places in the code, using an interface and injecting strategies provides a simpler and more maintainable solution. It's not that common, but it happens.

The façade pattern can be used when implementing an anticorruption layer, to shield our brand new microservice from the influence of legacy systems. Otherwise, the complexity of the old system might start spilling into the new one, making things harder to understand and maintain.

The adapter pattern can help us decouple our business code from the frameworks and libraries that our application builds upon. One use case for this type of usage of the pattern would be to deal with a library that has a particularly annoying API. In such a case, we could use the pattern to simplify our business code. In another approach, the pattern can be used to build an application-wide architectural style, commonly known as Hexagonal Architecture or Ports and Adapters.

The decorator pattern allows us to add our own bits to the code provided by those frameworks and libraries. These usually include simple operations like logging or gathering some kind of metrics.

To be honest, I can't think of any other GoF pattern that I have used recently, and I don't use the ones above too often either. They just somehow don't fit with the nature of the business code. Now, does that mean that the GoF patterns are almost entirely useless?

> Rubies are red,   
Some threads are green,   
But only Java has AbstractSingletonProxyFactoryBean. 

The poem above might give you a little hint. My answer is obviously negative. The frameworks and libraries, that make our work so pleasant and easy, have to use the GoF patterns themselves to remain flexible and configurable. For a framework, this is an actual "current" user need, not some kind of a developer whim.

Often these patterns are not even under the hood - we as programmers take advantage of them. The most notable examples would be the usage of Proxy patterns by Hibernate and developers implementing template methods to configure Spring.

## Domain-Driven Design Patterns

The GoF patterns were more suitable for technical problems, like the ones framework designers face. But if a pattern is domain-driven, and I really mean domain-driven here, it has to be useful in writing business code, right? Well, the answer is not so simple.

As written in the original Domain-Driven Design book, and various other sources, DDD techniques are not suitable for every single project. The same applies to DDD patterns, both strategic and tactical ones. Let's take at some of them from the perspective of our general goal.

Entities are a great pattern to represent domain concepts that are defined by their identity, rather than their attributes. If they come from a domain model built upon a ubiquitous language, they greatly simplify the understanding and, therefore, the maintainability of the system. At the same time, if there is no clearly defined domain model, it's worth exploring if the same work can be done without having entities at all. I have recently seen such a case in practice. By replacing a bunch of entities and their associated repositories with simple SQL and JDBC, we built the exact same thing with much less code and hassle.

Value Objects are a great example of a pattern that can both simplify and complicate your code. Whenever your value field requires certain validation logic or special manipulating operations, putting them together in the same place can easily save you a headache. At the same time, if a value field has no such logic or operations, we're just complicating the system by adding extra wrapper classes, each in an extra source file (at least in Java). Does it improve maintainability or user experience? Not really.

Last in this section but surely not least, let's touch on aggregates. When an aggregate scope is reasonably small, it provides an easy mechanism for maintaining consistency and a central place for associated business rules. On the other hand, when an aggregate gets too big, it can literally slow down the entire system, reduce code maintainability, and start turning into a "god class." Therefore, aggregates should be used with caution, especially if they are not used as a part of a full-blown DDD process.

## Patterns of Enterprise Application Architecture

I expect that some readers might not be familiar with Martin Fowler's great book, but, at the same time, I'd expect the majority of you to have used the patterns described in it. Maybe my picture of the entire Java world is a bit limited, but from what I've seen so far, it seems that almost every Java web application is built upon three patterns described in the book: Domain Model, Service Layer, and Repository.

I don't want to say here that it's necessarily a bad thing. In the end, most web applications are conceptually similar and it's the business rules that differentiate them. What I'd merely like to achieve here is to challenge the status quo a bit.

The same way I described my SQL/JDBC solution as an alternative to DDD patterns, this same solution could be considered as an alternative to the triplet above. I invite you to do the same thing in your projects. Read the book or the pattern descriptions online and see if you could simplify your code by abandoning or switching a pattern or two. Maybe an active record or a transaction script is just what your project needs right now?

## Conclusion

Currently, the development world is full of patterns. From tricks to avoid inheritance to big architectural decisions - we have a pattern for everything. The keys to right ones are code simplicity, users' needs, and future maintainability. These keys drive us pretty far from the GoF patterns, at least as long as we're not writing a framework or a library. They make us look cautiously on the DDD patterns, unless we're following a full-blown DDD process. Last, but not least, they make us continuously challenge the architectural status quo, so that we pick the right tool for the job at hand.

_[This article is featured in the new DZone Guide to Java: Development and Evolution. Get your free copy for more insightful articles, industry statistics, and more!_](https://dzone.com/guides/java-development-and-evolution)

Find your next Integration job at [DZone Jobs](https://dzone.com/go?i=224227&u=https%3A%2F%2Fjobs.dzone.com%2Fjobs%2Fsearch%3Futf8%3D%25E2%259C%2593%26q%3DIntegration). See [jobs focused on integration](https://dzone.com/go?i=224227&u=https%3A%2F%2Fjobs.dzone.com%2Fjobs%2Fsearch%3Futf8%3D%25E2%259C%2593%26q%3DIntegration), or [create your profile](https://dzone.com/go?i=224227&u=https%3A%2F%2Fjobs.dzone.com%2Fprofiles%2Fsign_up) and have the employers come to you!
