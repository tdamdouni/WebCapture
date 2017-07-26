# The Soon-to-Be-Hated Object Locator

_Captured: 2017-05-13 at 08:54 from [dzone.com](https://dzone.com/articles/the-soon-hated-object-locator?edition=298091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-12)_

What every Java engineer should know about microservices: [Reactive Microservices Architecture](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone). Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).

As more frequent readers of my blog might know, amongst my most recent interests were concepts like [DCI Architecture](https://dzone.com/articles/dci-architecture-is-visionary), [Domain-Driven Design](https://dzone.com/articles/aggregate-pattern), and the [Service Locator](https://dzone.com/articles/the-hated-service-locator-anti-pattern) pattern. I've been doing a lot of conceptual thinking about these topics and an interesting idea sprung in my head - an Object Locator! Caution: if you're among the haters of Service Locator, you might not like this one.

## A Bit of DCI

At the very roots of the [DCI Architecture](http://amzn.to/2q6mWT5) and, to some, Object Orientation lies the idea of a web of interconnected objects. You know, the objects exist somewhere in the system and work together to support end user's goals. Here lies my first conceptual problem with our current approach to working with objects.

Most of the most important objects i.e. entities don't actually exist in the system for the most part. Only when retrieved from a repository they come to existence and the access to that repository is not ubiquitous in the system. Only selected classes have the repository injected and can actually retrieve the objects.

My basic idea is that **all of the objects in the system regardless of their type and identity should exist in the system at all times, or, at least, _seem to_ exist at all times**. If my object wants to talk to the mailing class, it should be just able to say: "Hey, Mailer! Send this email to this address please." If it wants to talk to some random entity, then it should be easily able to say: "Hey, random entity! Tidy Java is the best programming blog on the planet!" All of this should be possible without injecting endless amounts of classes like repositories and similar.

## A Bit of DDD

Now, let's turn a bit into the [DDD](http://amzn.to/2q6F6nA) zone. In his [great article series](https://vaughnvernon.co/?p=838), Vaugh Vernon points out that aggregates should not directly reference each other. Instead, an aggregate should only hold an ID of the other object and use other means to get in touch with the object. It's not that big of a hassle to avoid direct references and it both reduces coupling and greatly increases scaling.

In my idea, that ID is/should be enough to talk to the other object at any time. Unfortunately, in our current way of thinking, if my object only has the ID of another object (which could semantically be considered a valid reference to the object), it still cannot talk to it unless it has access to the damn repository.

Vaugh Vernon would probably suggest the usage of the actor model at this point, but this is not a satisfying solution for me. I hate complicating things. If I'm building a simple system right now, I want it to look like a simple system. If I need the superb scaling (and extra complexity) of the actor model later, I want to be able to add it later.

## A Bit of Service Locator

As the last source of inspiration, I took the [hated Service Locator pattern](http://tidyjava.com/hated-service-locator-anti-pattern/). It caught my attention because it allows us to dynamically resolve "service" dependencies in the whole system. This big, fundamental "flaw" of the pattern actually fits the idea of objects _seeming to_ exist at all times.

I guess you guys see where I'm going with this…

## The Object Locator

We could modify our Service Locator "pattern" to allow resolving all kinds of objects, not only the so-called services. That's not really a big change. For many smaller applications, it would mean as much as exposing methods to retrieve objects by ID via the locator. A very basic implementation could look like this:

This simple trick allows me to retrieve any kind of object I need at all times without carrying a bag of repositories around. Resolving an object to collaborate with is a matter of a simple method call:

Obviously, it's not as magical as it could be. In the end, I'm calling a method, instead of somehow referring to the object by name or something. But I think it's close enough. Any object can talk to any other object. The persistence involved in resolving objects is hidden from their collaborators. It _seems _like the objects existed at all times.

If I wanted to scale my application by introducing a concurrency model like the Actor Model, I could simply extract an object's interface and implement a proxy. The object locator is then changed to return the proxy and all of the class' collaborators remain happily unconscious of the magic happening under the hood.

## Before You Deem Me Crazy

I suppose that most of you can imagine what a crazy, big, unmaintainable mess this pattern could bring to any project. I'm in this group as well. I know how bad things could go with this. At the same time, things do not necessarily have to go this way. The key to preserving maintainability is strict scope control.

**An object locator should never be global to the whole system.** It would grow way too large and make working with the code almost impossible. It should span no more than a single component or a small microservice. For anything outside of that scope, the object locator should contain a service object responsible for communicating with other parts of the system.

The mailer object from the code example above could be an example of such a service. The whole mailing component could contain a lot of sophisticated logic, which is of no interest our current component. Therefore, the mailing component should have its own object locator and expose not more than a couple of interfaces. Since our component wants to communicate with the mailing component, our object locator is able to resolve the mailer as above.

## Final Words

I don't expect any of you to fall in love with the idea and start using it immediately. Far from it. At the same time, I think that the idea is interesting and I had a lot of fun working it out in my mind. I'm pretty sure that a team with a good set of skills in dependency management would be able to pull it off in a real system. I'm also pretty sure that there's a ton of different ways to implement the concept of ever-existing objects without resorting to a locator. Maybe you can come up with one? :)

Microservices for Java, explained. Revitalize your legacy systems (and your career) with [Reactive Microservices Architecture](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone), a free O'Reilly book. Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).
