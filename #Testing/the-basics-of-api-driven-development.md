# The Basics of API-Driven Development

_Captured: 2017-01-15 at 20:54 from [dzone.com](https://dzone.com/articles/abcs-of-api-driven-development)_

Build APIs from SQL and NoSQL or Salesforce data sources in seconds.[ Read the Creating REST APIs white paper](https://dzone.com/go?i=142024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714743%3B137084581%3Bk), brought to you in partnership with [CA Technologies](https://dzone.com/go?i=142024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714743%3B137084581%3Bk).

With the ubiquitous question of, "What are APIs?" has been answered in multiple forums. Let's start with a more interesting and relevant question: "Why APIs?"

## Why APIs?

The most important aspect of "Why APIs?" is that it brings in the standardization of interfaces in the development process. Developers get to work on structured and standardized APIs that are bound to not change their underlying behavior, irrespective of the technology or components used underneath.

APIs also take care of hiding the complexity of underlying implementation, bringing in modularity and [separation of concerns](http://en.wikipedia.org/wiki/Separation_of_concerns), which lets independent decoupled services to be implemented and tested.

The proliferation of [SaaS](http://en.wikipedia.org/wiki/Software_as_a_service) applications with exposed web APIs gives a new dimension to application development in which the developer has to focus on coding just the application business logic. Other subsidiary services (such as user management, logging, dashboards, deployment, etc.) are made available by calling these services (third-party or in-house services) through APIs. This speeds up the app development time manifold.

## What Is the API Economy?

The business answer to "Why APIs?" is even more intriguing because APIs act as gateways to enterprise digital assets. Organizations treat APIs as an important revenue channel. In fact, in some organizations like Salesforce.com, APIs contribute to more than 50% of total revenue. The ability of APIs to generate revenue by monetizing digital assets has ushered in a new way of shoring up enterprise revenues. This phenomenon needed some new jargon, so the world called it the API economy.

## What Is API-Driven Development (ADD)?

An API-first design is where the API is the first artifact that is created during the app development process. API contracts (API specification and signature, including the name, parameters, types, etc.) are either created by dedicated API architects or by front-end developers who are responsible for creating the end user experience. API contracts are finalized in collaboration with front-end and back-end developers.

Once the API contracts are finalized, the front-end developers build mocks around APIs and create and refine the end-user experience. In parallel, the back-end developers implement the underlying logic of the APIs. Dedicated test suites are created around these APIs and, in a way, they foster the idea of [test-driven development](http://en.wikipedia.org/wiki/Test-driven_development). Finally, the implementations of the front-end and back-end developers are brought together. This is bound not to fail as long as the developers have coded honoring the API contracts as established in the first step.

At a code implementation level, APIs these days are typically designed using the REST architecture with JSON payloads. SOAP, XML, and other standards are found to be heavy and heading towards oblivion.

## Benefits of ADD

In addition to the benefits of APIs listed under the "Why APIs?" section, API-driven development adds its own set of benefits to make the life of a developer easier and the process of app development simpler.

## **Faster App Development**

ADD allows the developer to focus only on the business logic. In ADD, it is expected that all subsidiary services will be accessed through APIs. Also, the initial agreement of the API contracts, parallel implementation by the front- and back-end teams, and hassle-free merging of the front and back-end code bring about huge time savings in app development.

## **Focus on Only Your Business Logic**

It is expected that the developers will use APIs (third-party or internal) for all the subsidiary services like user management, logging, etc. Hence, the focus of development is purely on the implementation of business logic and not on spending time implementing the skeletal technical structures of the app. In fact, in the thriving API ecosystem, API marketplaces (like ProgrammableWeb and Mashape) have come up to make the process of discovering and consuming the required APIs much easier.

## **Better Documentation**

One thing you will observe in all the enterprises who have made it big in API economy (i.e., Twitter, Expedia, etc.) is that their APIs are easy to use. Their APIs are easy to find and they have great documentation. An effective API is defined by an effective documentation around it. In fact, there are API tools like [Swagger](http://en.wikipedia.org/wiki/Swagger_%28computer_science%29) that have sprung up to aid in the process of describing and visualizing web APIs. In summary, a positive side effect of ADD is great API documentation, which typically is a neglected aspect of the traditional product development process

## **Inherently Microservice Architecture-Based Applications**

One of the aspects we discussed in the "Why APIs" section was modularity. Apps developed using ADD tend to be modular in nature, with every module representing a service (third-party or own). The main application itself seems to be a collection of micro apps talking to each other using APIs. This app architecture is called [microservices](http://en.wikipedia.org/wiki/Microservices) and has its own set of benefits. For example, If there is a load on the user management service of a microservice-architected app, we can scale that user management service by adding more hardware resources. Compare this with traditional monolith app architecture, where the entire app has to be scaled, though only a part of the app needs scaling.

## **Your App Is Ready for the Connected World**

With the proliferation of smart devices and the evolution of the API economy, we are heading towards a digital world (i.e., Internet of Things) where everything is connected through APIs. With API-driven development having API as the fulcrum, your app is will not just survive but also thrive in this connected world.

## What Next?

ADD is a powerful development process and is gaining prominence among IT teams in various organizations. What are the typical lifecycle phases of an API? What can be done to make ADD as the default development approach in organizations? Let's discuss those questions and more in later posts, where I will talk about API life cycle and the next-gen ADD.

The Integration Zone is brought to you in partnership with [CA Technologies](https://dzone.com/go?i=142025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714699%3B137084580%3Bt). Use CA Live API Creator to quickly [create complete application backends, with secure APIs and robust application logic](https://dzone.com/go?i=142025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714699%3B137084580%3Bt), in an easy to use interface.

### Like This Article? Read More From DZone
