# Five Questions Everyone Is Asking About Microservices (Part 1) - DZone Microservices

_Captured: 2019-08-24 at 18:59 from [dzone.com](https://dzone.com/articles/5-questions-everyones-asking-about-microservices-p?edition=520325&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202019-08-24)_

One of the joys of my role is that I’m often talking to customers (or potential customers) about their concerns, their plans, and their strategies for moving their business forward based on open source technologies.

When discussing the application development impact on existing developed applications and transitioning to microservices there are five questions that keep popping up in one form or another. They are the same regardless of the size of the organization and seem to become part of strategy discussions later in the process as organizations move towards microservice architectures.

This article touches on five questions, in no particular order, that everyone should ask about microservices. It's based on experiences from interactions with organizations in the process of conquering microservices for existing development and for delivering modern applications.

In this article, we'll take a look at the first question, one of the performance impact of microservices.

## Dealing With the Performance Impact of Microservices

The first question invariably pops up once the initial strategy planning is completed and starts made on migrating an existing (monolithic) application.

> **"How to approach the performance impact in communications when a monolith gets split up into distributed services (microservices), such as from internal calls to distributed REST APIs?"**

The basis of the question is uncertainty in what’s going to happen when decomposing existing monolithic applications into microservices (where possible). What's needed here is an understanding that the goal of splitting out services is to obtain deployment speed over API invocation speed.

Splitting microservices out of an existing monolith allows for isolation of service development within a team separate from the application development team. This service engineering team can operate at their own intervals, deploying changes weekly, daily, or even hourly if a noteworthy CVE is applicable.

The penalty for unknown network invocations is the trade-off to your monolith’s highly regimented deployment requirements, ones that caused it to move at 2-3 month deployment intervals. Dedicated microservice teams mean quicker reactions to business, competition, and security demands become possible due to faster delivery intervals. Equally critical for network invocations is to examine the granularity of network calls in this new distributed architecture.

Next time in this series of articles, a look at dealing with the state after splitting up monolithic applications.
