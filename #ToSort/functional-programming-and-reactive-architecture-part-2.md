# Functional Programming and Reactive Architecture (Part 2)

_Captured: 2017-12-31 at 19:54 from [dzone.com](https://dzone.com/articles/functional-programming-and-reactive-architecture-p?edition=347147&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-31)_

Get the Edge with a Professional Java IDE. [30-day free trial](https://dzone.com/go?i=255333&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-preroll%26utm_campaign%3Didea).

As engineers, we want to build systems that are valuable for consumers; a reactive system strives to provide a correct answer in a timely manner to its users whether they are humans or other systems. For this reason, a fundamental quality of such systems is responsiveness.

## Responsiveness

A responsive system establishes the upper bounds for acceptable latency. Latency is the time that passes between a request and the response. Predictable latency and correct answers provide confidence in the system, help error handling, and enforce further system usage. To design a responsive system, we work with three main aspects: resiliency, concurrency, and elasticity.

## Resiliency

It is really frustrating when a system gets stuck in an inconsistent state caused by a failure; that system lacks a stable design with the direct consequence of not being responsive. We have to design a system that could keep working through failures by adding redundancy, isolating the components to avoid cascading effects, and (when everything else fails) restarting part of it without affecting the whole. This would free the user of the components from the handling of failures. To achieve this level of separation, we could design concurrent systems.

## Concurrency

Reactive systems achieve concurrency and isolation through asynchronous message passing. This enforces decoupling and modularization, simplifying logging and monitoring. Failures themselves could be handled through delegation using messaging. Message passing promotes a better and clearer separation of concerns where a message would specify _what_ to do and a message handler would take care of _how_ to do it. All of these properties enable elasticity using queues to mitigate spikes in system load.

## Elasticity

An elastic system provides a consistent latency by dynamically allocating resources as the need arises and optimizing their usage when the system faces less pressure. Queues and independent components enable horizontal scalability providing a more consistent and manageable latency reducing bottlenecks and allowing replication.

## The Actor Model

The actor model started as an attempt at defining an abstraction to describe efficiently and expressively the problem of _concurrently cooperative execution of desired actions_ when it became evident that the future of computing would be distributed and parallel. Actors are units of computations that communicate asynchronously through messages; their very nature is highly concurrent, enabling parallel problem-solving.

## The Big Picture

The reactive model requires good modularization so that the actors responsible for handling their messages can execute their domain behavior effectively and concurrently. This is easier to achieve when there is no shared mutable state between them.

This is the reason why functional programming is a perfect fit; referential transparency and modularization are encouraged from the very beginning and at every level. You're using pure functions and immutable data structures that decouple side effects from pure logic, enabling scalability, concurrency, and composability.

[Get the Java IDE](https://dzone.com/go?i=255334&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-postroll%26utm_campaign%3Didea) that understands code & makes developing enjoyable. Level up your code with IntelliJ IDEA. [Download the free trial](https://dzone.com/go?i=255334&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-postroll%26utm_campaign%3Didea).

![](https://dz2cdn1.dzone.com/storage/rc-covers/7391100-dzone-aicover.jpg)
