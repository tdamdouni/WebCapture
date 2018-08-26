# Microservices — Future Applications

_Captured: 2018-08-09 at 06:08 from [dzone.com](https://dzone.com/articles/technology-and-innovation-microservices-the-future?edition=387204&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-08)_

[Learn how modern cloud architectures use of microservices has many advantages and enables developers](https://dzone.com/go?i=300448&u=https%3A%2F%2Fwww.cloudentity.com%2Fwhite-paper-microservice-devsecops-zone%2F) to deliver business software in a CI/CD way.

Being able to build, evolve, and scale large applications is critical for organizations, but the challenges involved make it a difficult task. Because of this, microservices has emerged as a dominant pattern for building modern cloud applications by breaking apart individual components as independent services that are centered around specific business capabilities.

Microservice architecture is an approach to distributed systems that promotes the use of finely-grained services with their own lifecycles. As microservices are primarily modeled around individual business processes/functionality, they avoid the problems of traditional tiered (multi-tier/n-tier) architectures like monolith applications. Microservices also integrate new technologies and techniques that have emerged over the last decade, which helps them avoid the drawbacks of many service-oriented architecture implementations.

While using microservices comes with a myriad of benefits in making large applications more manageable, building a reliable distributed system at scale is incredibly challenging in any scenario, as there are numerous considerations for dealing with failure, consistency, and performance, among others.

This article details the path to the microservices architecture and examines the benefits and drawbacks of the pattern. It also discussed best practices that will help developers and application architects achieve their application goals.

## About the Domain

### **SOA**

Service Oriented Architecture is an approach to have software resources in an enterprise available and discoverable on a network as well as defined services. Each service would achieve a predefined business objective and perform discrete units of work. The services are independent and do not depend on the context or state of the other services. They work within distributed system architecture.

In some ways, SOA is an evolution of distributed technologies like COM and CORBA. Similar to these, SOA stresses on strict contracts between the services and consumers (WSDL) and specific service discovery (UDDI), transport (SOAP), mediation (WS-mediation), routing (WS- addressing), security (WS-security, WS-trust, WS- secure conversation etc) and other aspect of distributed computing. Additionally, it lays a lot of emphasis on the design, development and operational governance of services through enterprise repository, service lifecycle management, and service level monitoring tools.

## 1\. Introduction

Microservices is an architectural style. It is an approach to develop a single application as a suite of small services, each running its own process and communicating with lightweight mechanisms often an HTTP API. These services are built around business capabilities and independently deployable.

The microservice pattern has significant benefits, especially when it comes to enabling the agile development and delivery of complex enterprise applications.

The microservice architecture pattern breaks an application into manageable chunks thus enforcing a level of modularity that in practice is extremely difficult to achieve with a monolithic code base. Consequently, individual services are much faster to develop and much easier to understand and maintain.

Alternatively, the approach favors a lightweight message bus. In layman's terms, the applications built from microservices aim to be a decoupled and a cohesive as possible. They own their individual domain logic and act more as filters - receiving a request, applying logic as appropriate, and producing a response.

The essence of microservice architecture is not new. The concept of distributed system is very old. The microservice architecture also resembles SOA. The idea behind microservices is to architect large, complex and long-lived applications a set of unified (organized or interconnected) services that evolve over time. The term "microservices" strongly suggests that the services should be small.

However, while it's desirable to have small services, that should not be the main goal. Instead, you should aim to decompose your system into services to solve the kind of development and deployment problems. Some services might indeed be tiny, whereas others might be quite large.

## Application Development Evolution

![](https://dzone.com/storage/temp/9907365-singletier-ntier-applications.jpg)

### **Single Tier Applications**

In the early times of evolution, the applications were developed and deployed as a single entity. These single tiers of applications are easy to deploy since they only have one codebase and deployment configuration.

Scalability for such applications was big challenges as it can only be done by replicating the entire application. This directly increases the cost to a business as well as a waste of resources as traffic and load grow.

#### **Multi-Tier (or n-Tier)**

The drawbacks of Single-Tier/monolithic applications lead to the origin of multi-tier architecture. This new architecture breaks the application into logical distributed tiers causing efficient scalability. This approach generally separates the presentation layer, data layer, and business logic layer. So scaling approach applied to these respective layers individually instead of the application as a whole.

Now, when the applications built with the pattern grow, it causes strain on the business logic layer and leads to many of the drawbacks of the monolith. Again, as a single entity, scalability is challenging and expensive.

#### **Service Oriented Architecture (SOA) **

The thinking behind SOA (evolution of SOA) is the vision to see the applications as business capabilities.

As more and more organizations are moving towards automation/digitization, IT has evolved as the backbone of business by serving rapidly changing business requirements. These rapidly changing business needs, lead developers began to envision their applications as a collection of business capabilities, thereby isolating components more around their purpose than their place in the stack. For example, the developer would create a user service that handles user authentication, an order service that handles billing, or a notification service that handles sending emails. Doing so provide more effective scalability, as each service is smaller and more focused.

While this pattern provided a framework for building effective application architecture, its practice has generally been ineffective due to unnecessary complex abstractions and legacy protocols. The developer would attempt to use SOA to connect a wide range of applications that all spoke a different language, requiring an extra layer for an Enterprise Service Bus.

This leads to archaic and costly configurations that cannot keep up as the technology and business landscape evolved.

## 2\. Microservices - Artefacts

### Why Microservices - the New Pattern?

The evolution of IT has drastically changed the perspective of business globally. In the early days, IT was supposed to be a helping hand to business/organizations. Initially, IT was used to reduce the manual work for a business function/unit.

Nowadays, IT is being used to transform the business, generate more revenue. So now it's not just a support function/liability but the main function line of business.

In its Top 10 Strategic Technology Trends for 2015, Gartner stated, "To deal with the rapidly changing demand of digital business and scale systems up - or down - rapidly, computing has to move away from static to dynamic models. Rules, models and code that can dynamically assemble and configure all of the elements needed from the network through the application are needed."

This shift in thinking around application architecture has also introduced a shift in practice. Further predictions from Gartner state that, "The first step toward the web-scale IT future for many organizations should be DevOps (Development Operations) - bringing development and operations together in a coordinated way to drive rapid, continuous incremental development of applications services."

Using web-scale IT makes it easier for organizations to build applications and infrastructure similar to those offered by Amazon, Google, and Facebook. It puts them in position to further embrace the cloud in an enterprise IT setting, delivering capabilities of large services providers to internal users.

### Differentiation From SOA

The microservices pattern is clearer than SOA in its defining characteristics, providing a real-world framework that satisfies modern application architecture requirements. Microservices is often referred to as "SOA done right:"

_SOA focused on independent technical systems, microservices focuses on independent business systems._

Instead of connecting various applications together, the microservices pattern aims to create a single, cohesive application comprised of independently developed and deployed services that each follows the single responsibilities principle. The term micro can be deceiving as to the characteristics of microservice, however, since size is not the defining trait of microservices. While generally small, what is important is that each service is its own encapsulated process that can be developed and deployed independently. By limiting the scope of what a service can do, the developer can ensure they do not unintentionally end up with many decoupled monoliths.

In line with the modern cloud, communication between services is done over HTTP via RESTful APIs, passing JSON data, often through a message queue to ensure reliability. The individual microservices are generally processed asynchronously, triggered by an event such as an API call, push queue, schedule or a webhook. A lightweight and efficient framework around communication and processing further distinguishes microservices from SOA.

### Decomposing Applications Into Services

There are other architectural styles that do scale. The book, "The Art of Scalability," describe a really useful, three-dimension scalability model; the scale cube, which is shown in below figure.

![](https://dzone.com/storage/temp/9907370-scaling.jpg)

In this model, the commonly used approach for scaling an application by running multiple identical copies of the application behind a loader balance is known as X-axis scaling. That's a great way of improving the capacity and the availability of an application.

When using Z-axis scaling each server runs an identical copy of the code. In this respect, it is similar to X-axis scaling. The big difference is that each server is responsible for only a subset of the data. Z-axis scaling, like X-axis scaling, improve the application's capacity and availability.

However, neither approach solves the problem of increasing development and application complexity.

**To solve those problems, we need to apply Y-axis scaling.**

Whereas Z-axis scaling splits things that are similar, Y-axis scaling splits things that are different. At the application tier, Y-axis scaling splits a monolithic application into a set of services.

Each service implements a set of related functionalities such as order management, customer management etc.

**As a pattern, microservices promote Y-Axis scalability by decomposing functional elements as individual services, as opposed to traditional replication. **

Ideally, each service should have only a small set of responsibilities. The SRP (Single Responsible Principle) defines a responsibility of class as a reason to change, and that a class should only have one reason to change. It makes sense to apply the SRP to service design as well.

##  Microservice Architecture - Communication Mechanism

In microservice architecture, the pattern of communication between clients and the applications, as well as between application components, are different than in a monolithic application. Let's first look at the issue of how the application's clients interact with the microservices. After that, we will look at communication mechanisms within the application.

### **Direct Service Calls**

An application client such as a native mobile application could make a RESTful HTTP request to the individual services, as shown in the figure below.

![](https://dzone.com/storage/temp/9907371-directservicecall.jpg)

There is likely to be a significant mismatch in granularity between the APIs of the individual services and data required by the clients.

For example, displaying one web page could potentially require calls to a large number of services. Amazon.com, for example, describes how some pages require calls to 100+ services. Making that many requests, even over a high-speed internet connection, let alone a lower-bandwidth, higher-latency mobile network would be very inefficient and result in poor user experience.

### **API Gateway Pattern**

This is a better approach, as the client will make a small number of requests per page, perhaps as few as one, over the internet to a front-end server known as an API gateway

![](https://dzone.com/storage/temp/9907373-apigatewaypattern.jpg)

The API gateway sits between the application's client and the microservices. It provides APIs that are tailored to the client. The API gateway provides a coarse-grained API to mobile clients and a finer-grained API to desktop clients that use a high -performance network. In this example, the desktop clients make multiple requests to retrieve information about a product, whereas a mobile client makes a single request.

The API gateway handles incoming requests by making requests to some number of microservices over the high-performance LAN. In this example, fine-grained requests from a desktop client are simply proxied to the corresponding services, whereas each coarse-grained request from a mobile client in handled by aggregating the results of calling multiple services.

## 3\. Advantages of Microservices

This separation of components creates a more effective environment for building and maintaining highly scalable supplications. Smaller services that are developed and deployed independently are easier to maintain, fix and update, leading to more agile capabilities for responding to today's changing environments.

### Modularity

Microservices use the service as the unit; every service has its boundary and you cannot simply bypass the boundary so you can develop, deploy, and scale the service independently.

#### Service-Specific Database

Microservices are loosely coupled and own their database so services do not block other services by holding a database lock.

#### Fault Isolation

Microservice architecture has better fault isolation; an issue with one service will not affect other service and other services will continue to work normally.

#### Scalability

Scaling at the individual service level become more cost effective and is on demand. Individual tasks can be processed concurrently without affecting the rest of the application.

Separating components of an application makes it less likely that an individual bug or hardware failure will take down an entire system (eliminate a single point of failure). Failed processes can be isolated, and down endpoints can be retired until reached.

### Technology/Language Flexibility

Each individual service can be in a different language based on a developer's preference, task suitability, or to match a certain library.

Apart from these, the below points are also the major advantages of microservices:

  * Microservice architecture gives developers the freedom to independently develop and deploy services.
  * Small teams can develop a microservice.
  * Code for different services can be written in different languages.
  * Easy integration and automatic deployment (using open -source continuous integration tools such as Jenkins, Hudson, etc)
  * Easy to understand and modify for developers, thus can help a new team become productive quickly.
  * APIs can be versioned more effectively since individual services can follow their own scheme. Major releases can be done at the application level, while services can be updated on demand.
  * Separating components of an application makes it less likely that an individual bug or hardware failure will take down an entire system. Failed processes can be isolated, and down endpoints can be retired until reached (eliminate a single point of failure).
  * The developers can make use of the latest technologies.
  * The code is organized around business capabilities.
  * Starts the web container more quickly, so the deployment is also faster.
  * When change is required in a certain part of the application, only the related service can be modified and redeployed - no need to modify and redeploy the entire application.
  * Better fault isolation: if one microservice fails, the other will continue to work (although one problematic area of a monolith application can jeopardize the entire system.
  * Easy to scale and integrate with third-party services.
  * No long-term commitment to a technology stack.

## 4\. Drawbacks of Microservices

Decoupling an application into independent services means that there are now more moving parts to maintain. This lead to certain challenges, as well.

### Complex Orchestration

While a key benefit of microservices is its streamlined orchestration capabilities, more services mean maintaining more deployment flows. DevOps takes an even more important role with this pattern, as each service must be configured properly across its entire lifecycle.

### Inter-Service Communication

Decoupled services need a reliable, effective way to communicate while not slowing down the whole application. Delivering data over the network introduces latency and potential failure, which can interfere with the user experience. A common approach is to introduce a message queue as a reliable transport layer.

### Testing

While keeping code and dependencies tight means a simpler development environment for specific services, it does introduce challenges with testing as it relates to the entire application. Services will often need to communicate with each other or rely on a data source or API.

Testing one service independently would then require a complete test environment to be effective.

  * Microservice architecture brings a lot of operational overhead.
  * A distributed system is complicated to manage.
  * Default to trace problem because of distributed deployment.
  * Complicated to manage whole products when the number of services increases.

## 5\. Conclusion

The monolithic architecture pattern is a commonly used pattern for building enterprise applications. It works reasonably well for small applications: developing, testing and deploying small monolithic applications are relatively simple.

However, for large, complex applications, the monolithic architecture becomes an obstacle to development and deployment. Continuous delivery is difficult to do and you are often permanently locked into your initial technology choices. For large applications, it makes more sense to use a microservices architecture that decomposes the application into s set of services.

The microservice architecture has a number of advantages. For example, individual services are easier to understand and can be developed and deployed independently of other services. It is also a lot easier to use new languages and frameworks because you can try out new technologies one service at a time.

Microservice architecture also has some significant drawbacks. In particular, applications are much more complex and have many more moving parts. You need a high level of automation, such as a PaaS, to use microservices effectively.

You also need to deal with some complex distributed data management issues when developing microservices. Despite the drawbacks, the microservice architecture makes sense for large, complex applications that are evolving rapidly, especially for SaaS-style applications.

There are various strategies for incrementally evolving an existing monolithic application to microservice architecture. Develops should implement new functionality as a standalone service and write glue code to integrate the service with the monolith.

It also makes sense to iteratively identify components to extract from the monolith and turn into services. While the evolution is not easy, it's better than trying to develop and maintain an unwieldy monolithic application.

## References

  1. Fowler, Martin, and Lewis, James [25 March 2014] Microservice Architecture.

Discover how to [deploy pre-built sample microservices OR create simple microservices from scratch.](https://dzone.com/go?i=300428&u=https%3A%2F%2Fwww.cloudentity.com%2Fdemo-reward-zone%2F)
