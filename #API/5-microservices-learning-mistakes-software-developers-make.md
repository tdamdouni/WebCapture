# 5 Microservices Learning Mistakes Software Developers Make

_Captured: 2017-10-19 at 14:31 from [dzone.com](https://dzone.com/articles/05-microservices-learning-mistakes-software-develo?edition=334696&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202017-10-19)_

When we are learning a new technology or tool, we always rely on what we already know or experienced in our past projects. However, we end up assuming too many things (mostly wrong ones), especially when we are learning one of the most important and recent topics of our industry: **Microservices**.

In this article, we'll discuss the five main mistakes professionals make when they are learning the microservices subject. Let's get started.

## Mistake #1 - Confusing SOA and Microservices As the Same or Similar Things

Although both SOA and microservices are architecture styles (an architectural style is a formal notation to explain how a software application is assembled and its implications), these two variations have a lot of differences:

### Soa

  * Its approach is to connect existing applications via a single instance, the ESB, via disparate protocols.
  * The connection and message delivery between the endpoints must be orchestrated within the ESB.
  * The service that is exposed in the ESB should be written in a specific language and follow mostly SOAP protocol (with or without WS* stack) or REST, via HTTP protocol.
  * Costly when you have a huge payload to exchange between the parties, due to the phases of marshaling and unmarshaling.
  * Vertically scalable.
  * ESB as a single point of failure.
  * Harder to deploy in comparison to MSA (microservices style architecture) due to dependencies of the application endpoint and ESB mediation itself.
  * Services are registered in advance of the execution and consumption of their contract by other services.

### Microservices

  * Its approach is to create a single, self-sufficient application that can run in an isolated environment with its own database.
  * The connections between the services are choreographed_ \- _this way the microservice can respond to a specific event received.
  * The microservice can be written in any programming language available for the creation of services (Java, Python, JavaScript, .NET, etc).
  * Follows only REST conventions. Can use binary protocols such as [Google Protobuf](https://github.com/google/protobuf) and [Twitter Finagle](https://twitter.github.io/finagle/).
  * Corresponds to a functional feature of our current monolith system.
  * Fault-tolerant.
  * Horizontally scalable.
  * Easy to deploy with CD/CI in place.
  * Microservices register themselves in an entity called an API Gateway and are automatically discovered by other microservices.

## Mistake #2 - "if I Use REST, I Already Have Microservices"

In microservice architecture, the REST approach is only one of the main attributes. For an application to be labeled as a microservice solution, one should have all characteristics described by the [12-factor](https://12factor.net/) methodology.

Besides that, any level of maturity with REST should suffice. For more information on RMM with REST, [read our post about it](https://microservicesradar.wordpress.com/2017/09/19/what-is-the-richardson-maturity-model/).

## Mistake #3 - Microservices Can Run on the Same Container. No Problem, Right?

Yes. Unfortunately, it's a problem.

Microservices should

  * Run totally isolated in their environment with all needed resources in hand (loosely coupled).
  * Be able to be scaled independently.
  * Be able to be deployed independently, in their own CD/CI, to accelerate the answer for changes in a specific functional feature.
  * Be able to be traced,
  * Be able to be discovered by other microservices automatically,

These are necessary to maintain the right scalability, fault-tolerance, and time to market.

## Mistake #4 - All Microservices Should Be Written in the Same Programming Language

Once the microservices run on different containers and expose known contracts that abstract their underlying technology, there's no need to implement all microservices in one specific programming language.

With this in mind, you could have smaller teams, each one with a specific expertise of business functionality and programming languages, to ease the evolution of the business solution as a whole, independently.

## Mistake #5 - Microservices, As the Name Implies, Should Be Small

The _micro_ in microservices represents the business functionality that exists today in the monolith application,as are called all solutions that have several functional concerns of a huge business problem to solve.

The _micro _is not about the size, but about the minimum business context it addresses in comparison to the _monolith _as a whole.

This business problem then is split into smaller pieces (the microservices themselves) to easily compose and respond effectively to all request and business demands that may arise on the way, in all business transactions.

Thanks for reading.

Best regards.
