# SOLID Principles and the Foundation Behind Them

_Captured: 2018-08-29 at 06:57 from [dzone.com](https://dzone.com/articles/solid-principles-and-the-foundation-behindnbspthem)_

## Let's Start With Extreme Programming

I like to correlate SOLID principles with [XP](https://www.amazon.com/Extreme-Programming-Explained-Embrace-Change/dp/0321278658) principles. Just to remind you, a full XP chain is formed of values, principles, and practices -- in exactly this order, from the most fundamental elements to derivatives. Values are what drives us, what defines us and our behavior. Principles are certain rules that comply with values. Practices are some activities based on principles. Neither principles nor practices have no sense without values.

## If SOLID Are Just Principles, What Are the Values?

Before delving into this philosophical discussion, I want to say what mental image I see when I hear the word "program code" -- at least, when I'm involved in domain logic implementation. To me, program code is a representation of business processes in some programming language. Ideally, there is a [bijection](https://en.wikipedia.org/wiki/Bijection) between them. It's a [business-IT](https://hackernoon.com/why-you-should-split-the-monolith-e946f57db38c) alignment that is manifested in a lower level than [SOA](https://medium.com/@wrong.about/how-to-implement-soa-dc6bf08fba9a) -- in program code. That's why OOP is a better fit for that than, say, procedural programming: it has all the tooling for representing entities from real life's domains. Yes, I'm talking about [objects](https://www.yegor256.com/2014/11/20/seven-virtues-of-good-object.html). So [modeling correct abstractions](https://hackernoon.com/on-good-domain-decomposition-385ee8ce5a3), representing real-life processes, is apparently the most essential part in object-oriented software development. I would say that it is its values.

## Are SOLID Principles Necessary and Sufficient?

Let's take a look at all of them in turn.

### **Single Responsibility Principle**

Being rather ambiguous, [it basically tells](https://dzone.com/articles/single-responsibility-principle-1) that the object should be cohesive. If a class is cohesive, if there is a single higher-level purpose, if its responsibilities conform to its name, the SRP would come out naturally.

### **Open-Closed Principle**

The practical consequence of applying [OCP](https://dzone.com/articles/the-open-closed-principle-and-what-hides-behind-it) is that if any behavior, which is part of some class, can change, then its implementation should hide behind an interface, so you won't have to modify any code of that class. This has a name already -- it is [loose coupling](https://en.wikipedia.org/wiki/Loose_coupling).

### **Liskov Substitution Principle**

It is basically a definition of [Polymorphism](https://en.wikipedia.org/wiki/Polymorphism_%28computer_science%29), more precisely -- [Subtyping](https://en.wikipedia.org/wiki/Subtyping). I love them both, but I love encapsulation and composability as well. So, why there are no "e" and "c" letters in a SOLID abbreviation?

All in all, it's about loose coupling, [again](https://dzone.com/articles/liskov-substitution-principle-or-how-to-create-bea).

### **Interface Segregation Principle**

[Following the definition](https://dzone.com/articles/interface-segregation-principle-and-how-to-interpr), it goes against fat interfaces, the ones that have lots and lots of implementing classes. So once again it's about loose coupling.

### **Dependency Inversion Principle**

[Here](https://medium.com/@wrong.about/dependency-inversion-principle-e402e5b69e70), besides loose coupling, there is a concrete (and mechanical) guideline on how to modularize your software.

So, I can't see anything revolutionary in SOLID. It's all about low coupling and high cohesion.

## SOLID Principles and Encapsulation

High cohesion and low coupling are concepts broad enough so that encapsulation I believe can be derived from them. Just in case -- by [encapsulation](https://en.wikipedia.org/wiki/Encapsulation_%28computer_programming%29), I usually mean [information hiding](https://en.wikipedia.org/wiki/Information_hiding) as well, which is not [ubiquitously ](https://web.archive.org/web/20130307051858/http://www.itmweb.com/essay550.htm)[accepted](http://wiki.c2.com/?EncapsulationIsNotInformationHiding).

Take a look at the following code:

What makes objects of class _A_ and interfaces _IB_ and _IC_ highly encapsulated? None of them expose their internal structure or pure data: no public access to instance variables, [no getters](https://www.yegor256.com/2014/09/16/getters-and-setters-are-evil.html), no constants, no public static properties. Instead, all of the internal data is used internally, resulting in objects created by class _A_ being very [cohesive](https://en.wikipedia.org/wiki/Cohesion_%28computer_science%29). Besides, no other objects' data is required for object _A_. Instead, it relies only on behavior exposed by interfaces _IB_ and _IC_. And class _A_ doesn't bother about their concrete implementation, which apparently resides in some other module. That makes the whole system very [loosely coupled](https://en.wikipedia.org/wiki/Coupling_%28computer_programming%29).

I would consider an extent to which a class is encapsulated as a more tangible gauge of whether this class is good or bad -- in case high cohesion and loose coupling seem a bit abstract concepts. At least to my taste, encapsulation is way less ambiguous and vague notion than SOLID.

## SOLID Principles and Reusability

Originally, OOP was never about reusability. Again, it comes up naturally when your model is decomposed correctly. Reusability is a consequence of such decomposition. Putting it in the first place can hardly lead to [correct abstractions](https://hackernoon.com/how-to-avoid-anemic-domain-model-5e1c3e6fe4d0), and to maintainable code. And you could get a feel for what was OOP like originally by reading some [good ](https://www.amazon.com/Smalltalk-Objects-Design-Chamond-Liu/dp/1583484906)[books](https://www.amazon.com/Smalltalk-Best-Practice-Patterns-Kent/dp/013476904X) about Smalltalk. Don't worry, they are more about good object design than on Smalltalk.

## Final Thoughts

SOLID is not a comprehensive set of axioms that the whole OOP is based upon. It's a good gauge of already built design, but arguably not the best set of principles to pursue while actually building it. I believe high cohesion and loose coupling are way more clear beacons.

Moreover, one shouldn't forget that each one is meant to be a principle, not a core value of good software. So it doesn't make any sense to apply any of them purely mechanically, without identifying correct abstractions.
