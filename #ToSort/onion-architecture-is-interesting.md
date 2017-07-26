# Onion Architecture Is Interesting

_Captured: 2017-02-28 at 11:19 from [dzone.com](https://dzone.com/articles/onion-architecture-is-interesting?edition=271921&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-27)_

Check out this [8-step guide](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code! Brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431).

After [Layered](https://dzone.com/articles/layered-architecture-is-good) and [Hexagonal](https://dzone.com/articles/hexagonal-architecture-is-powerful) architectures, the time has come to talk about their close cousin - the Onion Architecture initially introduced in [a ](http://jeffreypalermo.com/blog/the-onion-architecture-part-1/)[series](http://jeffreypalermo.com/blog/the-onion-architecture-part-2/) [of](http://jeffreypalermo.com/blog/the-onion-architecture-part-3/) [posts](http://jeffreypalermo.com/blog/onion-architecture-part-4-after-four-years/) by Jeffrey Palermo.

## What is Onion Architecture?

As we said in the introduction, the concept of Onion Architecture is closely connected to two other architectural styles - Layered and Hexagonal. Similarly to the Layered approach, Onion Architecture uses the concept of layers, but they are a little different:

  * **Domain Model layer**, where our entities and classes closely related to them e.g. value objects reside
  * **Domain Services layer**, where domain-defined processes reside
  * **Application Services layer**, where application-specific logic i.e. our use cases reside
  * **Outer layer**, which keeps peripheral concerns like UI, databases or tests

Those layers when presented as circles, each wrapping around the previous one, form the famous "onion":

![](https://dzone.com/storage/temp/4436217-kolka.png)

Between the layers of the Onion, there is a strong _dependency rule_: **outer layers can depend on lower layers, but no code in the lower layer can depend directly on any code in the outer layer**. This is essentially the [Dependency Inversion Principle](https://dzone.com/articles/perfecting-your-solid-meal-with-dip), just presented in terms of the overall architecture, not just single classes.

As you can see in the picture, the three inner layers i.e. _domain model_, _domain services_, and _application services_ are parts of the _application core_. _Application core_ contains all logic necessary to run and test the application as long as necessary dependencies are provided at runtime. This is possible thanks to the _dependency rule_ that we introduced in the previous paragraph. Since no code in the _application core_ depends on outer layers, we can just swap out the UI or the database for the testing (or any other) purposes.

## The Essence of Onion Architecture

To me, the essence of Onion Architecture is the application of Dependency Inversion Principle with architecturally defined priorities between layers. Jeffrey Palermo, in his original texts about Onion Architecture, stresses this a lot - the major difference between Onion Architecture and Layered Architecture is the direction of the dependencies (and hence coupling).

In the Layered Architecture, as understood by the majority of people, virtually all layers can depend on the infrastructure layer, as in the picture below:

![](http://tidyjava.com/wp-content/uploads/2017/02/dependencies.png)

This causes some bad coupling. A change in the infrastructure layer like changing some library or switching a database provider could spill changes all over your business logic. Onion Architecture is about protecting the business logic, hence the _dependency rule_. A flattened picture of the Onion Architecture would look like this:

![](http://tidyjava.com/wp-content/uploads/2017/02/obrazek_2.png)

## Implementing Onion Architecture

The Onion Architecture gives us no direct guideline on how the layers should be implemented, so we can assume that you are free to choose whatever level you want i.e. class, package, module or whatever else. However, given the heart of the architecture being a _domain model_, I would say that you should definitely avoid mixing it with those less important concerns like UI.

When it comes to the _dependency rule_, things boil down to implementing the Dependency Inversion Principle whenever an inner-layer class wants to interact with an outer-layer class. To do this, we simply put interfaces that the outer-layer classes should implement in the inner layers:

![](http://tidyjava.com/wp-content/uploads/2017/02/kolka_chmurki.png)

### Example

Jeffrey Palermo himself provided an example of the Onion Architecture, so instead of playing around with Spring Pet Clinic again, let's analyze his solution. The project is in C#, but since we will look only at the code structure and won't read the implementation, all you need to know is that C# namespaces are roughly equivalent to Java packages (more info [here](http://stackoverflow.com/questions/9249357/difference-between-namespace-in-c-sharp-and-package-in-java)).

The overall structure of the project looks like this (I cut out configuration files):

![](http://tidyjava.com/wp-content/uploads/2017/02/ss2017-02-22at06.12.44.png)

As you can see, the _application core_ is separated from the infrastructure, UI, and tests using namespaces. Let's look at the structure of the Core namespace:

![](http://tidyjava.com/wp-content/uploads/2017/02/ss2017-02-22at06.20.10.png)

The most prominent classes in the Core are Visitor and VisitorProcessor, members of _domain model_ and _application services_ layers respectively. Since the core should not depend on the Outer layer, the dependencies on VisitorBuilder and VisitorRepository are represented as interfaces, which are implemented in the UI and infrastructure layers.

If you want to take a closer look at the project, you can check it out [here](https://bitbucket.org/jeffreypalermo/onion-architecture/overview).

## Benefits of an Onion Architecture

  * **Plays well with DDD** - that should not be a surprise for an architecture that builds everything on top of a _domain model_
  * **Directed coupling** - the most important code in our application depends on nothing, everything depends on it
  * **Flexibility** - from an inner-layer perspective, you can swap out anything in any of the outer layers and things should work just fine
  * **Testability** - since your _application core_ does not depend on anything else, it can be easily and quickly tested in isolation

## Drawbacks of an Onion Architecture

  * **Learning curve** - I don't know why, but people tend to mess up splitting responsibilities between layers, especially harming the _domain model_
  * **Indirection** - interfaces everywhere!
  * **Potentially heavy** - if you look at Palermo's project, the _application core_ has no dependencies towards frameworks, even NHibernate, a cousin of Java's Hibernate. Implementing things this way in Java would not be so easy unless you want to jump into XML files (yay!)

## When to Apply Onion Architecture?

In the case of Onion Architecture, I see things pretty similarly as in the Hexagonal one. In the world of microservices that work in a request-response manner, you usually need a Repository interface and one or two Gateways, and your business code is well protected from unwanted dependencies. I'm not sure if that's an Onion Architecture already, it depends on your interpretation. On the other hand, we have the monoliths, which contain much more dependencies and services depend on one another on the code level. In this case, you'll probably find much more outward dependencies to replace with interfaces. And there's my framework dilemma, which I keep coming back to, mostly because of Uncle Bob's writings that suggest that Onion and Hexagonal Architectures avoid framework dependencies. Hence, I'd say that to some extent all of us should take from Onion Architecture, but that extent should be decided on a case-by-case basis.

One interesting thing that I found about Onion Architecture is that it's more appealing for C# programmers than Java programmers, at least judging by the blog posts I found. Of course, that's just a curiosity, I wouldn't consider that an argument in the discussion on whether to apply the architecture or not.

## Summary

Onion Architecture sets a clear _dependency rule_ between layers, making it a more restrictive variant of Layered and Hexagonal Architectures. At the very center of our application sits a _domain model_, surrounded by _domain services_ and _application services_. Those 3 layers form the _application core_ - no relevant application logic should reside outside of it and it should be independent of all peripheral concerns like UI or databases. As a close cousin of Hexagonal, Onion Architecture is certainly very powerful, but the extent to which we'll apply its principles should be carefully considered.

The Java Zone is brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered). Check out this [8-step guide](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code!
