# Event Sourcing: The Pains of Wrongly Designed Aggregates

_Captured: 2017-03-29 at 20:30 from [dzone.com](https://dzone.com/articles/event-sourcing-the-pains-of-wrongly-designed-aggre?edition=286946&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-29)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Event sourcing is a brilliant solution for high-performance or complex business systems, but you need to be aware that this also introduces challenges that most people don't tell you about. In [June](http://www.continuousimprover.com/2016/06/event-sourcing-from-trenches-mixed.html), I blogged about the things I would do differently next time. But after attending another introduction to event sourcing recently, I realized it is time to talk about some real experiences.

In this multi-part post, I will share the good, the bad, and the ugliness to prepare you for the road ahead. After having dedicated the [two last posts](http://www.continuousimprover.com/2017/02/the-good-of-event-sourcing-projections.html) on the good of event sourcing, let's talk about some of the pains we went through.

![](http://d35brb9zkkbdsd.cloudfront.net/wp-content/uploads/2013/12/The-Good-The-Bad-And-The-Ugly-Clint-Eastwood-e1387471759294-638x279.jpg)

## Designing Your Domain Based on Ownership

When I started practicing domain-driven design almost nine years ago, I thought I knew all about aggregates, value objects, repositories, domain services, and bounded contexts. I read Eric Evans' [blue book](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215), Jimmy Nilsson's [white book](https://books.google.nl/books/about/Applying_Domain_Driven_Design_and_Patter.html?id=8RueQPUOPssC&source=kp_cover&redir_esc=y&hl=nl), and various papers such as InfoQ's _[DDD Quickly_](https://www.infoq.com/minibooks/domain-driven-design-quickly). Our main driver for designing our aggregates was based on who owns what property or relationship.

We designed for optimistic concurrency, which meant that we needed to use the version of the aggregate to detect concurrent updates. The same applied to relationships (or association properties on a technical level). If it was important to protect the number of children a parent has, you needed to add the child through the parent. Since we were using an OR/M, we could use its built-in versioning mechanism to detect such violations.

Surely, I had not heard of eventual consistency or consistency boundaries yet, and Vaughn Vernon had not published his brilliant [three-parts series](https://vaughnvernon.co/?p=838) yet. In short, I was approaching DDD as a bunch of technical design patterns rather than the business development experience it is supposed to be.

## **Relying on Eventual Consistent Projections**

Because we didn't consider the business rules (or invariants) enough while designing our aggregates, we often needed to use projections to verify certain functional scenarios. We knew that those projections were not transactional consistent with the transactions, and that other web requests could affect those projections while we were using it.

But the functional requirements allowed us to work around this for the most part -- until the point that we wanted to make a projection run asynchronously, of course. That's the point where we either had to stick to an (expensive) synchronous projector or accept the fact that we couldn't entirely protect a business rule.

Next time, I'll make sure to consider the consistency of a business rule. In other words, if the system must protect a rule at all costs, design the aggregates for it. If not, assume the rule is not consistent and provide functional compensation for it.

## **Bad Choice in Aggregate Keys**

As many information management systems do, we had an aggregate to represent users. Each user was uniquely identified by his or her username and all was fine and dandy. All the other aggregates would refer to those users by their username. Then, at a later point in time, we introduced support for importing users from Active Directory. That sounded pretty trivial until we discovered that Active Directory allows you to change somebody's username.

So, we based our aggregate key on something that can change (and may not even be unique), including the domain events that such an aggregate emits. And since a big part of the system is using users to determine authorization policies, this affected the system in many painful ways. We managed to apply some magic to convert the usernames to a deterministic Guid (ping me for the algorithm), but it still was a lot of work.

Next time, I will just need to accept that no functional key is stable enough to be the aggregate key and start from a Guid instead.

## **Using Domain Events as a Way to Externalize Business Rules**

The system that I worked on is highly customizable and has a domain with many extension points to influence the functional behavior. At that time, before we converted the system to event sourcing, we used Udi Dahan's [domain event](http://udidahan.com/2009/06/14/domain-events-salvation/) implementation to have the domain raise events from inside the aggregates. We could then introduce domain event handlers that hook into these and which provide the customized behavior without altering the core domain. This worked pretty well for a while -- in particular because those events were essentially well-defined contracts. With some specialized plumbing we made sure all that code would run under the same unit of work and therefore behaved transactionally.

But when we switched to event sourcing, this mechanism became a whole lot less useful. We had to make decisions on many aspects. Are the events the aggregates emit the same as domain events? Should we still raise them from inside the aggregate? Or wait until the aggregate changes have been persisted to the event store? It took a while until we completely embraced the notion that an event is something that has already happened and should never be used to protect other invariants. Those cases that did misuse them have been converted into domain services or by redesigning the aggregate boundaries. You can still use the events as a way to communicate from one aggregate to another, but then you either need to keep the changes into the same database transaction or use sagas or process managers to handle compensation or retries.

## **Domain-Specific Value Types in Events**

Remember the story about how we choose the wrong functional key for a user and had to touch a large part of the code base to fix that? As with any bad situation, people will try to come up with measures that will prevent this in the first place. Consequently, we decided to not directly use primitive types in our code-base anymore and introduced domain-specific types for almost everything.

For instance, a user was now identified by a UserId object with value semantics. So, whether it contained a Guid or a simple string was no longer of concern for anything but that type itself.

But as often happens with a lot of new practices, we applied it way too dogmatic. We used them everywhere; in commands, aggregates, projections, and even events. Naive as we were, we didn't realize that this would cause a tremendous amount of coupling between the entire code-base. And I didn't even mention the horror of somebody changing the internal constraints of a value type causing crashes caused by an old event that couldn't be deserialized because its old value didn't meet the new constraints.

Having learned our lessons, nowadays, we make sure we consider the boundaries of such value types. You may still use them in the aggregates, domain services and value objects within the same bounded contexts, but never in commands, projections, and events.

## **Event Granularity**

Consider a permit-to-work process in which the risk assessment level can be determined to be 1 or 2. If the level is 2, the process requires a risk assessment team to be formed that will identify the real-world risks involved in the work. However, if the risk level is reduced to 1, then the team can be disbanded. To model the intent of this event, we have two options. Either we capture this situation by first emitting a couple of fine-grained MemberRemovedFromRiskAssessmentTeam domain events, followed by a RiskAssessmentLevelChanged domain event. Or we decide to capture this as a single RiskAssessmentLevelDemoted event.

So, which is better?

Considering the fact that we're practicing Domain-Driven Design, I guess most people will go for the coarse-grained RiskAssessmentLevelDemoted event. And indeed, it does properly capture the actual thing that happened.

But it has a drawback, as well. Both the domain as well as the projection logic must know to interpret that event as a demotion in the actual level and the disbandment of the risk assessment team. But what happens if the expected behavior changes in a later version of the software? Maybe the rules change in such a way that team will need to be kept intact, even if the level changes. If you take the coarse-grained event path, you will need to duplicate that logic. We don't share code between the command and query sides in a CQRS architecture style. And what happens when you rebuild domain aggregates from the event store that existed before the software update was completed?

There's no ultimate answer here, but considering the relatively high rate of change and configurability in our system's business rules, we choose for fine-grained events.

## **Event Versioning**

Much [has been written](https://docs.google.com/forms/d/e/1FAIpQLSeavyr_ZbW18l-H_g1T8M_GRX3PQrlddZmWSHzEDD2-2wChNg/viewform?c=0&w=1) about event versioning and there are plenty of examples how to convert one or more older events into a couple of new events. We use NEventStore, which provides a simple event upconversion hook out of the box. That library uses Newtonsoft's [Json.NET](http://www.newtonsoft.com/json) to serialize the events into its underlying storage, which, by default, includes the .NET runtime type of the event in the JSON payload.

This has caused us some pain. What if the .NET namespace of the event type changes because somebody refactored some of the code? Or what if the event is moved from one DLL to another because we decide to split one project in two or two projects in one? We had to tweak the JSON serializer considerably to ensure it would ignore most of the run-time type info and find a reasonably stable mechanism to match a JSON-serialized event with its run-time .NET type. Maybe there's an event store implementation that solves this for you, but we have not come across one yet.

## **Bugs**

"Great developers don't write bugs," I often hear some of my colleagues say -- but somehow, I keep running into apparent less-than-great-developers. So, bugs are inevitable. We didn't have too many problems with bugs affecting the domain. Either we could handle them by changing the way the existing events were used to rebuild the domain, or by repairing flawed events using smart upconverters. However, I do remember a particular painful bug that was really hard to fix. One of our background processes was responsible for importing information about a back office system into the domain. It would collect the changes from that system and translate them into a couple of commands that were handled by the domain.

All was well for a while -- until we got some reports about some weird timeouts in the system. After some investigation, we discovered that a particular single aggregate had more than a million events associated with it. Considering the average of a handful of events per aggregate instance, this was a serious problem. Apparently, the aggregate root contained a bug that caused it to be not so idempotent as it should be, injecting new events for things that didn't even change. We finally managed to fix this by marking the stream as archivable, a concept we build ourselves. But it most definitely wasn't fun.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
