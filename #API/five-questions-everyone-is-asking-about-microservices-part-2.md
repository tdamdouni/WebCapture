# Five Questions Everyone is Asking About Microservices (Part 2) - DZone Microservices

_Captured: 2019-08-25 at 19:45 from [dzone.com](https://dzone.com/articles/five-questions-everyone-is-asking-about-microservi?edition=520326&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202019-08-25)_

When discussing the development impact on existing applications while transitioning to microservices, there are five questions that keep popping up in one form or another. They are the same regardless of the size of the organization and seem to become part of strategy discussions later in the process as organizations move towards microservice architectures. 

These articles cover questions that everyone should ask about microservices. They're based on experiences from interactions with organizations in the process of conquering microservices for existing development and for delivering modern applications.

 Previously I covered the first question around [the performance impact of microservices](http://www.schabell.org/2019/08/5-questions-everyones-asking-about-microservices-question1.html). In this second article, I'll take a look at dealing with the state after splitting up monolithic applications.

##  State and Monoliths

After the initial discussion around the first question, it’s usually followed by issues of how to deal with the state in a monolithic application.

> **"How to deal with services that get split off from their monolith usage and are stateful, where we want to use the benefits of a container platform like OpenShift?"**

There are two types of _stateful_ in relation to applications:

  1. Building a business application that uses either in-memory state or database state.
  2. Building a specific database engine and need highly performant, even low-level, access to the underlying disk. 

The first option is the mainstream way of developing and deploying cloud-native applications with their _stateful_ components, while still spitting out microservices, using a container platform like OpenShift based on Kubernetes. 

Option two is another story and is often best left to specialized vendors. This is because these types of solutions can go deep enough to involve maintaining extensions to operating system kernels themselves. It makes more sense to focus on your domain-specific business value and delivering that to your customers. 

Next time in this series of articles, a look at dealing with data across a distributed microservices architecture.
