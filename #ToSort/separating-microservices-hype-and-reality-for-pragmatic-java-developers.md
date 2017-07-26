# Separating Microservices Hype and Reality for Pragmatic Java Developers

_Captured: 2017-07-03 at 20:05 from [dzone.com](https://dzone.com/articles/separating-microservices-hype-and-reality-for-pragmatic-java-developers?edition=306208&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-03)_

### Microservices are the next big thing, but they aren't perfect. Here's what Java developers should keep in mind when considering using microservices.

Learn how to troubleshoot and diagnose some of [the most common performance issues in Java today](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital).

_[This article is featured in the new DZone Guide to Java: Development and Evolution. Get your free copy for more insightful articles, industry statistics, and more!_](https://dzone.com/guides/java-development-and-evolution)

Microservices are everywhere, or at least so it seems. The hype has reached such a point that for a couple of conferences I am part of, attendees have asked for fewer talks unabashedly extolling microservices. As the title suggests, my aim here is to try to cut through some of the hype in favor of balance, brevity, simplicity, and pragmatism. Rest assured I plan to stay as far away as possible from anything that looks like a marketing pitch or an academic sermon. In the end, my hope is that you will be able to answer for yourself if microservices can benefit you, and know what Java tools you may need to adopt this style of developing systems.

## What's in a Name?

Microservices talks and write-ups usually start by defining microservices. The reason for this is that there still isn't any industry consensus on what microservices are. This reality makes practical adoption by blue collar IT organizations extremely difficult. Even microservices terms seem deeply  
entangled in marketing concerns.

The irony is such that "microservices" need not be so "micro" and need not be just "services." Similar problems exist for the term "monolith" to describe a system that doesn't follow the microservices style. The term has needlessly negative connotations in a computing context when a far more neutral term like a "cohesive" or "integrated" system could have done the job just as well. The reality is that there are very likely at least just as many systems  
that make sense as monoliths as there are systems that are clearly appropriate for microservices.  
The very simple core concept behind microservices is about modularizing complex systems using distributed computing.

Microservices decompose larger systems into smaller independently deployable parts using the network as a strict boundary of separation. As long as this decomposition is what you are trying to accomplish, you are doing microservices; the rest is insignificant nuance. In this sense, microservices are just a rebranding of computing concepts that have been around for a long time. These same concepts have manifested themselves many times over the years in CORBA, Jini, RMI,  
EJB 1/2, COM/DCOM, and OSGi. The last reincarnation of these concepts is SOA.

Indeed, despite what some proponents claim, microservices have far more similarities to SOA than they have differences. A plainspoken name for microservices could simply be "SOA II," "Son of SOA," or "SOA Done Right." By far the easiest path to understanding microservices is simply contrasting it with what the most ardent proponents claim are significant differences with the relatively well-established concept of SOA. Some proponents of microservices do begrudgingly admit that part of the motivation for rebranding SOA is the negative association with SOAP and ESB.

Consequently, the most significant difference between SOA and microservices is that proponents stress REST instead of SOAP. By the same token, microservices proponents also stress the purported evils of centralized orchestration via ESBs. In reality, the choice of communication protocols between distributed components is just an implementation detail. Proponents recognize, for example, that asynchronous messaging (such as using JMS) is a significant alternative to synchronous REST calls when greater reliability and resiliency is desired. The most ardent microservices proponents also tend to stress the "micro" part in an effort to differentiate from SOA. In reality, the size of a microservice only matters to a certain extent, and there is a point of diminishing returns to breaking a system down into too many services that are too small.

Microservices proponents will often cite high degrees of automated test coverage, DevOps, and Continuous Integration/Continuous Deployment (CI/CD) as strict prerequisites. In practice, these factors are just about as important as they are for monolithic systems. They only become do-or-die  
necessities to master in the case of the purist style systems broken down into a large number of fine-grained services. More infrequently, cloud solutions, Docker, and product features like  
fat-jars, dynamic discovery, circuit breakers, metrics, etc. are co-sold with microservices. The practical relationship between microservices and these product offerings is much like the  
relationship between SOA and ESBs. Just as ESBs are only needed for some SOA systems, it is possible to write perfectly fine microservices systems that do not use any of these things.

## The Promise

SOA focused on the promises of reuse and interoperability. Microservices, understandably, do not, as SOA often failed to realize the benefits of reuse in particular. Carefully evaluating the primary benefits that proponents cite is key to whether you should adopt microservices or not.

### Team Size

An ugly truth of software engineering is that code quality diminishes over time, and maintaining a code base becomes increasingly difficult. In addition, a curious observation many of us have had is that code quality suffers as the size of the code base and the number of developers working on the code base grow. With agile development in particular, scaling teams beyond a certain size is a real challenge. Just imagine what a daily standup looks like with more than about six to ten developers.

This is the most powerful and practical reason for adopting microservices for most of us. When your team and code size reaches a clear point of diminishing returns, an easy way to regain effectiveness is by breaking the system down into modules and giving them to separate smaller teams. What this also means, however, is that most blue-collar IT organizations probably won't get much out of microservices until the development team reaches a certain size. Even while adopting microservices, you are likely to get the most benefits if each team working on a given module is in the neighborhood of about six to ten developers.

### Agility

The point behind microservices and agility is simple on the surface. The smaller the module, the faster it can deploy through CI/CD, especially when including many automated integration tests and third-party libraries. Since modules are independently developed and deployed, making a single change is easier. The speed of making changes is a key reason for companies like Netflix, Google, and Amazon to adopt microservices. For the rest of us, things are not that clear cut. While there is merit to the agility argument, the issue is that microservices dogma taken too far can actually hinder productivity for most organizations by introducing complexity and overhead at the overall systems level.

### Scalability

The scalability argument cited by microservices proponents is also fairly simple on the surface. The idea is that more dedicated hardware can be allocated to each module, all the way down to a separate database. This allows for almost limitless scalability. In fact, this is the only way companies like Netflix, Google, and Amazon can reach Internet scale.

The reality for most applications is that a monolith on a horizontally scaled load-balanced set of machines with a single logical database already goes a long way. For these applications, the additional scalability that comes with microservices just isn't needed since they will never reach anything approaching Internet scale.

### Polyglot Programming

This argument is a variant of the technology interoperability point SOAP/SOA promoted. The idea is that each module can be developed using a separate technology using a common communication protocol like REST. Much like in the SOA era, this is not likely to be a compelling advantage for most blue-collar IT organizations that tend to try hard to agree on a limited technology set in order to make vendor, skill set, and personnel management easier.

## The Reality

Microservices are by no means a free lunch. They come with disadvantages that you will need to deal with if you are to adopt microservices. A key microservices paradox to notice is that the more "micro" your modules, the worse these disadvantages become.

  * Deploying a single module can be efficient on its own. The problem is that at a system level, administration, deployment, and monitoring is a lot harder for distributed systems than it is for a monolith. Imagine having to manage a single standalone application versus many applications that have complex interdependencies that only manifest themselves at runtime -- possibly in the worst ways and at the worst time. The complexity gets exponentially worse when the system is over-granularized to the point that a single enhancement results in changes across effectively interdependent but completely independently deployable modules. The reality of distributed systems is that they force higher skill, tooling, and automation requirements for both development and operations teams.

  * Distributed systems make testing, debugging, reliability, and consistency harder. When a piece of functionality depends on making a remote invocation that may result in other indeterminate remote invocations, an integration test will require that all these interdependent pieces of code be running and functioning correctly. For the same reasons, hunting down a bug is a lot harder in distributed systems. Ensuring consistency in a monolith is easy through local transactions. When a single unit of work is spread across REST invocations, it is no longer possible to use transactions to ensure consistency. Instead, you will have to write significantly more complex error handling code to try to maintain consistency yourself. The easiest way to minimize these issues is writing coarse-grained modules that are mostly independent and have few, if any, interactions with other remote modules.

  * Distributed systems result in a lot of code and data duplication. At the bare minimum, remote invocations result in virtually identical DTOs (Data Transfer Objects) on each side of the invocations. At worst, microservices can result in large parts of the domain model to be duplicated across modules, right down to the database. Besides maintenance overhead, this can easily result in bugs rooted in inconsistencies across duplicates.

  * A recent conference speaker used the term "distributed big ball of mud" to refer to a possible outcome of adopting microservices. The issue is that while adopting microservices can slow down code entropy, it can't actually stop it directly. For teams that already have difficulty maintaining reasonable code quality, microservices can make matters worse by making it easier to introduce poor quality in addition to the inherent complexities of distributed systems. Just imagine having to maintain poor quality distributed code written by an unfamiliar developer, team, and technology. The right time to think about microservices is when you are sure the team is already capable of writing reasonable monoliths.

  * Anyone considering microservices should have a solid understanding of the "fallacies of distributed computing" -- developed at Sun Microsystems in the late nineties. The fallacies remind us that it is foolish to overlook the downsides of networks. Network I/O is one of the slowest and most unreliable things you can do in computing. You can never count on infinite bandwidth, networks are often managed by different administrators, network configurations can change without your knowledge, larger networks increase the surface area for security vulnerabilities, and so on. Monolithic systems simply don't have to contend with these downsides. On the other hand, the more fine-grained microservices you have, the more obvious the fallacies of distributed computing become.

## The Bottom Line

Ultimately, only you can decide whether microservices are right for you by weighing the pros and cons in the context of your organization. That said, it is certainly possible to attempt some general observations for what they are worth.

  * A great number of systems in blue-collar IT organizations are probably fine as monoliths. Such systems may even be in the comfortable majority. The benefits of microservices do not outweigh the costs for these systems. It is wise to start systems as monoliths and grow them to microservices when necessary. If modularity is always kept in mind in a monolith, natural module boundaries are far easier to identify. Modularity can be enforced within monoliths using simple Java package names before the time becomes right for distributed modules.

  * For projects that can benefit from microservices, it is still a good idea to stay away from fine-grained services to avoid the worst disadvantages of microservices. What makes the most sense is to break these systems down into sizable sub-systems with distinct sets of business users. An example would be a larger insurance system that is broken down into point-of-sale, data capture, underwriting, policy management, payments, customer service, reporting, archival, etc. sub-systems. This is not too different from what was done in the SOA era.

  * The fine-grained services approach most microservices proponents espouse, where you would see dozens of distributed remote services comprising an application, like account service, product service, user service, or order service, is an anti-pattern for most of us. There are a small handful of companies that benefit from this level of granularity. These are companies that truly require internet scale and ultra-fast rates of change. These companies also have the manpower and resources to effectively deal with the downsides of microservices.

## Java Microservices Tools Landscape

Before considering any tools whatsoever, it is important to realize that microservices first and foremost are about architecture. For pragmatic approaches to microservices, any decent stack that supports REST, JSON, and messaging is fine. For Java developers, this certainly includes vanilla Java EE or Spring. The same can be said of the Lightbend stack: Play, Akka, and Lagom. And yes, Java EE application servers, especially the ones supporting just the Java EE Web Profile, are just fine for coarse-grained modules that look like SOA-style sub-systems.

Let's assume you've decided to go the fine-grained services route. You still have many options as a Java developer. For fine-grained services, a fat JAR solution makes more sense than an application server model. In the Spring ecosystem, Spring Boot is a popular choice for going this route (though it should be noted that Spring Boot can make general sense in terms of cutting down boilerplate Spring configuration even if writing a monolith). Dropwizard is another popular fat jar solution for  
Java developers. There are many options for Java EE developers too, including WildFly Swarm, KumuluzEE, Paraya Micro, WebSphere Liberty (yes, WebSphere Liberty supports modular fat-jars), and TomEE embedded. These Java EE centric solutions collaborate through the MicroProfile initiative.

Going down this path means that you may eventually need features like dynamic discovery, circuit breakers, metrics/healthchecks, client-side load-balancing, and so on to try to offset the downsides of distributed computing. Nearly every fat JAR solution I mentioned above supports many if not all these features.

Docker and cloud solutions (particularly PaaS) are often positioned as absolute necessities for microservices. The reality is that while Docker and cloud platforms may or may not make sense regardless of the type of architecture you have, they only become do-or-die necessities in case of very large, complex systems comprising of many fine-grained microservices.

The great news is that the tools I've mentioned work rather well with Docker and the cloud, including Java EE application servers or old school Spring framework applications.

## Summary

Microservices are the newest incarnation of valuable ideas with a long history, the last major incarnation being SOA. It is important to realize that microservices are not necessarily for everyone and not necessarily all-at-once. The great news is that the Java ecosystem has stepped up to support even the likely niche of fine-grained microservices.

_[This article is featured in the new DZone Guide to Java: Development and Evolution. Get your free copy for more insightful articles, industry statistics, and more!_](https://dzone.com/guides/java-development-and-evolution)

Understand the needs and benefits around implementing [the right monitoring solution for a growing containerized market](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics.](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital)
