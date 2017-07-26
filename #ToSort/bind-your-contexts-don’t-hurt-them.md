# Bind Your Contexts, Don’t Hurt Them!

_Captured: 2017-02-19 at 19:10 from [dzone.com](https://dzone.com/articles/bind-your-contexts-dont-hurt-them?edition=271897&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-19)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

This article is a response to a comment under one of my previous ones - [Layered Architecture Is Good](https://dzone.com/articles/layered-architecture-is-good). The comment says:

> Domain driven design does not conflict with layered architecture! The first example has a strict separation of layers.
> 
> The second solution is very dirty. Every method must be public, instead of being only visible within the package. Contract is brutally growing, as well as documentation of packages public API. Dependencies between packages are across dozens of classes, change to a single domain implies the need to change the whole application. Chances painlessly transfer of applications into separate modules or replace them with others is minimal.

"The second solution" in the comment refers to the Layered Architecture presented in this image:

![Image title](https://dzone.com/storage/temp/4361132-architecture-comparison.png)

I agree that Layered Architecture and DDD play very well together, but the rest of this comment is based on misconceptions that I feel can be very detrimental for project's clarity, maintainability and probably even it's eventual success.

## Don't Cut Your Contexts

> [..] change to a single domain implies the need to change the whole application. [..] 

Spring Pet Clinic is a really small application that ultimately contains only one or two useful use cases - everything boils down to scheduling visits. The domain is really small, too - you have an owner, a pet, a visit, and a vet. These things are really closely related: an owner has a pet, visits are scheduled for certain pets, and (it's not even modeled in the application) the visits should have a vet assigned. This is a single bounded context inside a single domain! It's succinct, cohesive, clear; why would you like to cut it? How's the "visit" domain different from an "owner" domain? Is this stuff really so complicated that we need to have separate models for each of them? Separate modules? Teams? Microservices maybe?

I could go on and on with these rhetorical questions. The point is simple: **Don't cut a single domain, or rather a single bounded context into smaller pieces just because it would imply fewer methods being public or fewer dependencies between packages**. The whole point of Domain-Driven Design is to capture your domain model as precisely as possible and making it as visible and clear in the code as possible. Cutting it into pieces that nobody understands for the purpose of encapsulation is a crime!

Now, I'm not saying that you should never slice your domain. Eric Evans, in his [wonderful DDD book](http://amzn.to/2kz6gNp), explains how you can introduce layering inside a domain to make things more digestible. But **that process is a result of a domain model growing to a substantial size and the designers having a good understanding of how things work and how things flow in the system**. It's not something that you should do out of the blue, that's not the point! Just look at the [DDD Cargo Tracker](https://cargotracker.java.net/) example below; how the _domain_ complexity of each layer is totally different than what you can see in Spring's Pet Clinic.

![Image title](https://dzone.com/storage/temp/4361130-ss2017-02-15at094004.png)

## Don't Squeeze Your Contexts

The second part of my semi-rant is not related to any particular sentence of that comment. It's related to the general idea that the original packaging is better, because of fewer dependencies, better encapsulation and such. Well, our nerdy metrics are better, that's true. But we're literally hiding our entities and their relationships between different packages, controllers, formatters, and such. How am I supposed to reason about the model's correctness and implications this way? How is a newcomer supposed to find the domain model in the project? By reading each class' implementations to check if it's an entity or [a wrapper for XML serialization purposes](https://github.com/spring-projects/spring-petclinic/blob/master/src/main/java/org/springframework/samples/petclinic/vet/Vets.java)? How would you handle the situation when the business wants you to add a vet relationship to the visit? Bash all the vet stuff into "owner" package, because of public methods and dependencies?

Here comes my second advice for this article: **Don't mix your domain model with all the nerdy stuff! **Really, making some methods on your domain models public for the sake of keeping the domain objects together and hence understanding the domain easier is a really, really low price. Domains are tangled, their rules are complicated. Real systems are far, far more complex than the Pet Clinic example. **The most important logic of your system lives there**. Why would you want to mix it with something as irrelevant as choosing an appropriate view to render HTML?

Look at the domain model in the Cargo Tracker again. Do you see any controllers? Formatters? XML wrappers? No, you see a clear picture of the domain. You can easily recognize what aggregates and entities we have in the system, which objects are most related to each other and what are the domain exceptions. This is what we're after here. The domain stuff, not the nerdy stuff.

## Bind Your Contexts

Even though I found this particular comment way off, I fully agree with the general idea of cutting large systems with regard to business concerns. That's what the whole topic of bounded contexts is about. We want to cut a large system so that it's architecture aligns with the way our business works. We want to do it in a way that minimizes the amount and strength of relationships between the contexts. We want to keep related things together and unrelated things apart. We want to limit the number of stakeholders concerned by a single piece of code so that their requirements don't diverge. We want to keep the integrity of the ubiquitous language. There are a million other reasons why we should bind our contexts. So do it! Bind them! Just… don't hurt them, please!

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).
