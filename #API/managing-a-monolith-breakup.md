# Managing a Monolith Breakup

_Captured: 2018-02-02 at 16:51 from [dzone.com](https://dzone.com/articles/managing-a-monolith-breakup?edition=359106&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-01)_

Planning to extract out a few microservices from your monolith? Read this [free guide](https://dzone.com/go?i=265421&u=https%3A%2F%2Ftry.split.io%2Fmonolith-breakup-stateful-services-ebook%3Futm_campaign%3D2018%252520DZone%252520DevOps%26utm_source%3Ddzone%26utm_medium%3Dpre%252520roll) to learn the best practice before you get started.

Moving from a monolithic system to a set of services is a common architectural transition, particularly prevalent at the moment as microservices continue to gain mindshare. Like any large architectural shift, a monolith breakup is best tackled as a series of small steps which incrementally move the system towards the desired state. These incremental steps might seem less effective than making changes in large leaps, but small steps are safe. They also enable a team to evolve their system's design while continuing to deliver features and functionality in parallel. This makes it a lot more likely that the architectural work will continue to completion.

In this blog post, I'll describe the sequence of changes a team can use to extract a chunk of functionality out from a monolith. We'll pick a fairly easy example to get started with - a stateless email notification service. In future posts, we'll look at some more complex scenarios, such as extracting functionality which depends on persistent state. We'll also see how we can use the capabilities of a feature flagging framework to make this a safe, controlled transition.

## The Plan

Imagine that we're working on a relatively large e-commerce application currently implemented as a large monolithic system. Our architectural vision is to move towards a set of fine-grained services.

We will move towards this goal slowly but surely, tackling one chunk of functionality at a time. Each chunk will be either extracted from the monolith into a _new_ service or moved into an _existing_ service, extending its scope of functionality.

Each of these extractions will take a while, and we want to avoid the [perils](https://trunkbaseddevelopment.com/5-min-overview/) of a long-lived feature branch. Instead, we will use [Branch by Abstraction](https://trunkbaseddevelopment.com/branch-by-abstraction/) techniques to perform the extraction on our shared master branch using the following plan of attack:

  1. Choose a candidate piece of functionality within the monolith
  2. Gather our internal implementation of the functionality within our monolith
  3. Introduce an internal facade for the functionality
  4. Create a new externalized version of the functionality
  5. Create a second facade for the externalized functionality
  6. Introduce a Toggler which can switch between the internal and external facade
  7. Migrate traffic from the internal to the external
  8. Remove the internal functionality, remove Toggler

## Choosing Functionality

We know that the best way to slice a system into independent services is by focusing on core business capabilities. In our domain that might mean services responsible for things like Order Fulfillment and Product Catalog. This is the best way to ensure that each service is highly cohesive and that the coupling between services is loose.

We've decided to start by extracting a Customer Notifications service, which will eventually be responsible for sending emails, text messages and in-app notifications to our customers to inform them of events like an order being shipping.

![Image title](https://dzone.com/storage/temp/7978239-pete-1.png)

## Gathering the Functionality

Our system is relatively mature and has been worked on by various teams over its lifetime. Different aspects of customer notification functionality are implemented in different areas of the codebase, based mostly on which team added the functionality and when it was done. We now spend some time refactoring these existing implementations to gather them into a single module without our codebase.

![Image title](https://dzone.com/storage/temp/7978240-pete-2.png)

## Introduce an Internal Facade

Next, we create a [Facade](https://sourcemaking.com/design_patterns/facade) which provides a high-level abstraction over the notification functionality and refactor all consumers of that functionality to use the facade. This provides us with a single choke point from which we will [strangle out](https://www.martinfowler.com/bliki/StranglerApplication.html) the functionality.

![Image title](https://dzone.com/storage/temp/7978244-pete-3.png)

## Create an Externalized Implementation

Now it's time for us to do the fun part - create the new implementation. Sometimes it's possible to do this by reusing the existing internal implementation, but quite often the best path is to simply re-implement the same functionality from scratch in an external service. In some cases, it will make sense to add the functionality to an existing externalized service, but in this instance, we decide to create a brand new Customer Notification service. When creating the new functionality, we are careful to use the same abstractions that we used when building our facade.

![Image title](https://dzone.com/storage/temp/7978253-pete-4.png)

## Create an External Facade

Now we add a second implementation of the customer notification facade within the monolith, which simply proxies requests over to the external service.

![Image title](https://dzone.com/storage/temp/7978262-pete-5.png)

## Introduce a Toggler

We now create a Toggler - a third implementation of the facade which acts as sort of traffic router, forwarding requests to either the internal facade or the external facade. This routing decision is typically configured via a [feature flag](https://martinfowler.com/articles/feature-toggles.html) of some sort.

![Image title](https://dzone.com/storage/temp/7978263-pete-6.png)

## Migrate

We're now ready to start moving over to the next external implementation. We start off with a Canary Launch, configuring the Toggler's feature flag such that 2% of requests to the customer notification Toggler is routed to the external facade while the remaining 98% is routed to the existing internal implementation. Assuming things go well we can slowly ramp up traffic to the new implementation until eventually 100% of customer notifications are being delivered via our next external service.

![Image title](https://dzone.com/storage/temp/7978274-pete-7.png)

## Cleanup

Once we are comfortable that our new external implementation is performing as hoped we get to another fun part - deleting code! At this point, we can remove the now-deprecated internal implementation of the customer notification functionality. We can now also remove the Toggler and hard-wire the consumers of the functionality to the external facade. After those two operations are done we may want to also do some refactoring of the interface exposed by the facade. It's quite likely that we had to add some non-optimal usage patterns to accommodate our 'crufty' legacy implementation. Now that we're free from that constraint, we can take the opportunity to improve the abstraction provided by the facade.

![Image title](https://dzone.com/storage/temp/7978280-pete-8.png)

## Gotchas

There are two common mistakes which teams make when performing this sort of incremental architectural improvement. The first is to succumb to the [fallacies of distributed computing](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) and design the interface of the initial, internal facade as if the facade will always be implemented locally within the same process. Consumers of the functionality behind the facade will eventually be talking to an external implementation, and we cannot abstract that behind the facade. The facade's interface should reflect that fact that it will eventually be implemented as a distributed system. This means things like not creating synchronous request/reply interactions, and expecting a broad range of failure modes.

The second mistake which I often see is for teams to take this opportunity to "fix" how the functionality has been modeled. Perhaps previously we had email, SMS and in-app modeled as 4 distinct interactions but we now realize that they're really 3 different variants of the same action. We will be tempted to re-model the notification functionality in this way when we create our new external implementation. The problem with this approach is the new model almost invariably cannot be perfectly mapped back to the existing implementation. This leads to no end of pain when trying to make both the internal and external facades speak the same interface. It's much better to take this as a two-step process. First, perform an architectural refactoring to extract functionality without changing its externally observable behavior. Once that has been done and your internal implementation has been removed it will be much easier to "upgrade" the new implementation to reflect your newer model of the problem space.

## Standing on the Shoulders of Giants

Almost all the concepts and ideas presented here are Branch by Abstraction techniques which have long been championed by folks like Paul Hammant, Jez Humble, Martin Fowler, Chris Stephenson, Steve Smith and many others. What we've seen in this blog post is an application of these techniques in the specific context of a monolith breakup, with our branching decisions powered by feature flags.

## That Was an Easy One

We've seen that it's possible to perform relatively large-scale architectural work as a series of small, safe steps. Using techniques like feature flagging also allows us to perform this evolution in parallel with other work happening within the same codebase, and while continuing to deploy our codebase to production whenever we'd like.

I did intentionally pick a relatively easy example for this discussion. Our email notification functionality is stateless, so we don't have to figure out how to move existing internal state to a new external store, or how to manage state in both places while we are in the middle of the migration phase. We also picked an example where it makes sense to do a simple canary launch to cut over to our new implementation. In other more risky scenarios, we might instead choose a dark deploy, where we send duplicate requests to both our existing internal implementation and our new external implementation and monitor for differences in functionality or performance.

In [part 2](https://www.split.io/blog/managing-monolith-breakup-stateful-services/) of this series, learn how to extract a service which is backed by persistent state that initially lives in a monolithic shared data store.

Measure the impact of feature releases, and of your DevOps program more broadly with full stack experimentation. [Learn how](https://dzone.com/go?i=265422&u=https%3A%2F%2Ftry.split.io%2Fmonolith-breakup-stateful-services-ebook%3Futm_campaign%3D2018%252520DZone%252520DevOps%26utm_source%3Ddzone%26utm_medium%3Dpre%252520roll) with this free article from CITO Research, provided by Split Software.
