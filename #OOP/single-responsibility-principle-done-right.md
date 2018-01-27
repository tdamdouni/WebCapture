# Single-Responsibility Principle Done Right

_Captured: 2018-01-05 at 18:14 from [dzone.com](https://dzone.com/articles/single-responsibility-principle-done-right?edition=347165&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-04)_

Just released, a [free O'Reilly book on Reactive Microsystems: The Evolution of Microservices at Scale](https://dzone.com/go?i=237227&u=https%3A%2F%2Finfo.lightbend.com%2Febook-reactive-microservices-the-evolution-of-microservices-at-scale-register.html%3Futm_source%3Ddzone%26utm_medium%3Dpost-roll-text%26utm_campaign%3DCOLL-2017-Reactive-Microsystems-The-Evolution-of-Microservices-at-Scale%26utm_term%3Dnone%26utm_content%3Djava-zone). Brought to you in partnership with Lightbend.

I am a big fan of the SOLID programming principles by Robert C. Martin. In my opinion, Uncle Bob did a great job when he first defined them in his books. In particular, I thought that the Single-Responsibility Principle was one of the most powerful among these principles, yet one of the most misleading. Its definition does not give any rigorous detail on how to apply it. Every developer is left to their own experiences and knowledge to define what a responsibility is. Well, maybe I found a way to standardize the application of this principle during the development process. Let me explain how.

## The Single-Responsibility Principle

As is normal for all the big stories, I think it is better to start from the beginning. In 2006, Robert C. Marting, a.k.a. Uncle Bob, collected in the book [Agile Principles, Patterns, And Practices in C#](https://www.amazon.it/Agile-Principles-Patterns-Practices-C/dp/0131857258) a series of articles that represent the basis of clean programming -- the principles are also known as SOLID. Each letter of the word SOLID refers to a programming principle:

  * **S** stands for Single-Responsibility Principle
  * **O** stands for Open-Closed Principle
  * **L** stands for Liskov Substitution Principle
  * **I** stands for Interface Segregation Principle
  * **D** stands for Dependency Inversion Principle

Despite the resonant names and the clearly marketing intent behind them, in the above principles are described some interesting best practices of object-oriented programming.

The Single-Responsibility principle is one of the most famous of the five. Robert uses a very attractive sentence to define it:

> A class should have only one reason to change.

Boom. Concise, attractive, but so ambiguous. To explain the principle, the author uses an example that is summarized in the following class diagram.

![Violation of SRP](http://rcardin.github.io/assets/2017-12-26/srp_wrong_design.png)

In the above example, the class `Rectangle` is said to have at least _two responsibilities_: drawing a rectangle on a GUI and calculating the area of that rectangle. Is that really bad? Well, yes. For example, this design forces the `ComputationalGeometryApp` class to have a dependency on the class `GUI`.

Moreover, having more than one responsibility means that every time a change to a requirement linked to the user interface comes, there is a non-zero probability that the class `ComputationalGeometryApp` could be changed, too. This is also the link between _responsibilities_ and _reasons to change_.

The design that completely adheres to the Single-Responsibility Principle is the following.

![Design SRP-proof](http://rcardin.github.io/assets/2017-12-26/srp_design.png)

Arranging the dependencies among classes as depicted in the above class diagram, the geometrical application does not depend on user interface stuff anymore.

## The Dark Side of the Single-Responsibility Principle

Well, this is probably a problem with me, but I never thought that a principle should be defined in such a way that two different people can understand it the same way. There should be no space left for interpretation. A principle should be defined using a _quantitative approach_, rather than a _qualitative approach_. Again, probably my fault -- it comes from my mathematical extraction.

But given the above definition of the Single-Responsibility Principle, it is clear that there is no mathematical rigor to it.

Every developer, using their own experience can give a different meaning to the word _responsibility_. The most common misunderstanding regarding responsibilities is finding the right grain to achieve.

Recently, a "famous" blogger in the field of programming, Yegor Bugayenko, published a post on his blog in which he discusses how the Single-Responsibility Principle is a hoax: [SRP is a Hoax](http://www.yegor256.com/2017/12/19/srp-is-hoax.html). In the post, he gave an incorrect interpretation of the conception of responsibility, in my opinion.

He started from a simple type that aims to manage objects stored in AWS S3.
    
    
        void read(final OutputStream output) { /* ... */ }    

In his opinion, the above class has more than one responsibility:

  1. Checking the existence of an object in AWS S3
  2. Reading its content
  3. Modifying its content

Hmm.

So, he proposes to split the class into three different new types, `ExistenceChecker`, `ContentReader`, and `ContentWriter`. With this new type, in order to read the content and print it to the console, the following code is needed.

As you can see, Yegor's experience drives him to define too finely grained responsibilities, leading to three types that clearly are not properly **cohesive**.

Where is the problem with Yegor's interpretation? What is the keystone to comprehending the Single-Responsibility Principle? _Cohesion_.

## It's All about Cohesion

Uncle Bob opens the chapter dedicated to the Single-Responsibility Principle with the following two sentences.

> This principle was described in the work of Tom DeMarco and Meilir Page-Jones. They called it cohesion. They defined cohesion as the functional relatedness of the elements of a module.

Wikipedia defines cohesion as:

> the degree to which the elements inside a module belong together. In one sense, it is a measure of the strength of relationship between the methods and data of a class and some unifying purpose or concept served by that class.

So, what is the relationship between the Single-Responsibility Principle and cohesion? Cohesion gives us a formal rule to apply when we are in doubt if a type owns more than one responsibility. If a client of a type tends to always use all the functions of that type, then the type is probably highly cohesive. This means that it owns only one responsibility, and hence has only one reason for changing.

It turns out that, like the Open-Closed Principle, you cannot say whether a class fulfills the Single-Responsibility Principle in isolation. You need to look at its _incoming dependencies_. In other words, _the clients of a class define whether it fulfills the principle_.

Shocking.

Looking back at Yegor's example, it is clear that the three classes he created, thinking of adhering to the Single-Responsibility Principle in this way, are loosely cohesive and hence tightly coupled. The classes `ExistenceChecker`, `ContentReader`, and `ContentWriter` will probably always be used together.

## Pushing to the Limit: Effects on the Degree of Dependency

In the post [Dependency](http://rcardin.github.io/programming/oop/software-engineering/2017/04/10/dependency-dot.html), I defined a mathematical framework to derive a _degree of dependency_ between types. The natural question that arises is that, upon applying the above reasoning, does the degree of dependency of the overall architecture decrease or increase?

Well, first of all, let's recall how we can obtain the total degree of dependency of a type `A`.

δAtot=1n∑Cj∈C1,…,CnδA->Cj

In our case, type `A` is the client of the class `AwsOcket`. Recalling that the value of δA->Cj ranges between 0 and 1, dividing without any motivation the class `AwsOcket` into three different types will not increase the overall degree of dependency of client `A`. In fact, the normalizing factor 1n assure us that refactoring processes will not increase the local degree of dependency.

The overall degree of the entire architecture will instead increase since we have three new types that still depend on `AwsOcket`.

Does this mean that the view of the Single-Responsibility Principle I gave during the post is wrong? No, it does not. However, it shows us that the mathematical framework is incomplete. Probably, the formula for the degree of dependency should be recursive, in order to take into consideration the addition of new tightly coupled types.

## Conclusions

Starting from the definition given by Robert C. Martin of the Single-Responsibility Principle, we showed how simple is to misunderstand it. In order to give some more formal definition, we showed how the principle can be viewed in terms of the concept of cohesion. Finally, we try to give a mathematical proof of what we have done, but we went onto the conclusion that the framework that we were using is incomplete.

Happy new year!

## References

Strategies and techniques for building scalable and resilient microservices to refactor a monolithic application step-by-step, [a free O'Reilly book](https://dzone.com/go?i=237228&u=https%3A%2F%2Finfo.lightbend.com%2Febook-reactive-microservices-the-evolution-of-microservices-at-scale-register.html%3Futm_source%3Ddzone%26utm_medium%3Dpost-roll-text%26utm_campaign%3DCOLL-2017-Reactive-Microsystems-The-Evolution-of-Microservices-at-Scale%26utm_term%3Dnone%26utm_content%3Djava-zone). Brought to you in partnership with Lightbend.
