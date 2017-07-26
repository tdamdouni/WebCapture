# Clean Architecture Is Screaming

_Captured: 2017-03-08 at 21:11 from [dzone.com](https://dzone.com/articles/clean-architecture-is-screaming?edition=276897&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-08)_

Check out this [8-step guide](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code! Brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431).

Welcome to the fifth installment of little architecture series! So far we have covered [layers](https://dzone.com/articles/layered-architecture-is-good), [hexagons](https://dzone.com/articles/hexagonal-architecture-is-powerful), [onions](https://dzone.com/articles/onion-architecture-is-interesting), and [features](https://dzone.com/articles/package-by-feature-is-demanded). Today, we'll look at a close friend of all four - Uncle Bob's Clean Architecture, initially introduced [here](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html).

## What Is Clean Architecture?

_Clean Architecture _builds upon the previously introduced four concepts and aligns the project with best practices like the _Dependency Inversion Principle_ or _Use Cases_. It also aims for a maximum independence of any frameworks or tools that might stay in the way of application's testability or their replacement.

_Clean Architecture_ divides our system into four layers, usually represented by circles:

  * **Entities, **which contain enterprise-wide business rules. You can think of them as about Domain Entities a la DDD.
  * **Use cases,** which contain application-specific business rules. These would be counterparts to _Application Services_ with the caveat that each class should focus on one particular _Use Case_.
  * **Interface adapters,** which contain adapters to peripheral technologies. Here, you can expect MVC, Gateway implementations and the like.
  * **Frameworks and drivers**, which contain tools like databases or framework. By default, you don't code too much in this layer, but it's important to clearly state the place and priority that those tools have in your architecture.

Between the circles, there is a strong _dependency rule_ - no code in the inner circle can directly reference a piece of code from the outer circle. All outward communication should happen via interfaces. It's exactly the same _dependency rule_ as we introduced in the Onion Architecture post.

![](http://tidyjava.com/wp-content/uploads/2017/03/another_productive_circle.png)

Apart from the layers, _Clean Architecture_ gives us some tips about the classes we need to implement. As you can see in the picture below, the flow of control from the _Controller_ to the _Use Case_ goes through an _Input Port _interface and flows to the _Presenter_ through an _Output Port_ interface. This ensures that the _Use Case_ and the user interface are properly decoupled. We'll see an example of this later in the implementation section.

![](http://tidyjava.com/wp-content/uploads/2017/03/rectangles_of_happiness.png)

## The Essence of Clean Architecture

I see two things that make _Clean Architecture_ distinct and potentially more effective than other architectural styles: strong adherence to the _Dependency Inversion Principle_ and _Use Case_ orientation.

### Strong Adherence to DIP

Similarly to its Onion cousin, _Clean Architecture _introduces the _Dependency Inversion Principle _at the architectural level. This way, it explicitly states the priorities between different kinds of objects in your system. In a way, _Clean Architecture_ does a better job at this, as it leaves no doubt about the tools like frameworks or databases - they have a dedicated layer outside all others.

### Use Case Orientation

Similarly to what we've seen in _Package by Feature_, _Clean Architecture _promotes vertical slicing of the code and leaving the layers mostly at the class level. The major difference between the two is that instead of focusing on a blurry concept of a _feature_, it reorients the packaging towards _Use Cases_. This is important as, ultimately, in any application that has some sort of GUI, one could identify real _Use Cases_. It's also important to note that entities sit in a different layer as in complex systems, one _Use Case_ can orchestrate several entities to cooperate and categorizing it by the type of the entity would be artificial.

## Implementing Clean Architecture

We can't be 100% sure about how Uncle Bob would implement a Clean Architecture today, as his book about it comes out in July (I preordered it already and will do a review or rehash of this post then), but we can look at the [GitHub repository](https://github.com/cleancoders/CleanCodeCaseStudy/tree/master/src/cleancoderscom) of his Clean Code Case study:

![](http://tidyjava.com/wp-content/uploads/2017/03/ss2017-03-02at07.36.08.png)

### Packaging

As you can see, the _Entities _and _Use Cases _layers have their own separate packages, while the other layers can be identified only conceptually. The `socketserver`, `http`, and `view` packages can be considered a part of the _Frameworks and Drivers_, while gateways package is a little bit ambiguous - their implementation is surely the _Interface Adapters_ layer, but their interfaces conceptually belong to _Use Cases_. My guess is that the interfaces are extracted to a separate package so they can be shared between different _Use Cases_. But it's just a guess!

By looking at the `usecases.codecastSummeries`, we can get more insight into how a complete _Use Case_ package looks like. As you can see, it accommodates all classes related to the execution of a particular _Use Case_: the view, controller, presenter, boundaries, view and response models, and the _Use Case_ class itself. This might be a lot more classes than you usually see in your projects when you execute an _Application Service_, but that's what it takes to go perfectly _Clean_.

### Internals

If you dug deeper into the implementation of the project's classes, you'd see no annotation there other than @Override. That's because of the frameworks being at the very outer layer of the architecture - the code is not allowed to reference them directly. You might ask, _how could I leverage Spring in such a project?_ Well, if you really wanted to, you'd have to do some XML configurations or do it using @Configuration and @Bean classes. No @Service, no @Autowired, sorry!

### My Extra Advice

Pulling off a _Clean Architecture_ might be a demanding task, especially if you worked with a _Package by Layer_, fat controllers kind of project before. And even if you get the idea and necessary skills to implement it, your colleagues might not. They might want to do this anyway, but simply forget to add interfaces or work around framework annotations when necessary. One way to prevent some of these issues could be to create a Maven module for each of the layers so that breaking a rule won't even compile. At the same time, if you don't have these already, introducing Pair Programming or Code Reviews will help you to prevent people from messing up with the dependency declarations (circular dependencies would not work, but adding Spring both to the _Use Cases_ and _Adapters _module would!).

## Benefits of a Clean Architecture

  * **Flexible **- you should be able to switch frameworks, databases or application servers like pairs of gloves
  * **Testable **- all the interfaces around let you setup the test scope and outside interactions in any way you want
  * **Could play well with best practices like DDD **- to be honest, I haven't seen it so far, but I also don't see anything stopping you from making an effective mix of DDD's Strategic and Tactical Patterns with _Clean Architecture_

## Drawbacks of Clean Architecture

  * **No Idiomatic Framework Usage **- the _dependency rule _is relentless in this area
  * **Learning Curve **- it's harder to grasp than the other styles, especially considering the point above
  * **Indirect **- there will be a lot more interfaces than one might expect (I don't see it as necessarily bad, but I've seen people pointing this out)
  * **Heavy **- in the sense that you might end up with a lot more classes than you currently have in your projects (again, the extra classes are not necessarily bad)

## When to Use Clean Architecture

Before I say something, let me note that I haven't tried implementing it in a professional context yet, so all of it is a gut feeling. We will probably get some more knowledgeable advice from Uncle Bob himself in his upcoming book.

If we consider _Clean Architecture_'s biggest drawbacks and its essence, I would derive the following criteria to consider:

  * **Is the team skilled and/or convinced enough? **One might consider this lame, but if people just don't get it or they don't want to do this, imposing the rigor of _Clean Architecture_ on them might be counter-productive.
  * **Will the system outlive major framework releases? **Since we're talking about heavy technology flexibility here, it's important to consider if we'll ever capitalize on this benefit. My experience so far suggests that most systems will, even if the developers won't be in the company by then.
  * **Will the system outlive the developers and stakeholders employment? **Since _Clean Architecture_ is so sound and makes _Use Cases _so clearly visible, systems that follow its principles will be much simpler to comprehend in the code, even if those who wrote it and asked for it are already gone.

## Summary

_Clean Architecture_ looks like a very carefully thought and effective architecture. It makes the big leap of recognizing the mismatch between _Use Cases _and _Entities_ and puts the former in the driving seat of our system. It also gives a clear place for _Frameworks and Drivers _in our system - a separate layer outside all other layers. This, combined with the _dependency rule_ might give us a plethora of benefits, but also might be way harder to pull off. In the end, it boils down to the question whether the system will live long enough so that the investment returns.

The Java Zone is brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered). Check out this [8-step guide](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code!
