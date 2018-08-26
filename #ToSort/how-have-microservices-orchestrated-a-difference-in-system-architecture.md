# How Have Microservices Orchestrated a Difference in System Architecture?

_Captured: 2018-04-07 at 21:01 from [dzone.com](https://dzone.com/articles/how-have-microservices-orchestrated-difference-in-1?edition=371230&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-04-07)_

[Sysdig](https://dzone.com/go?i=278430&u=https%3A%2F%2Fsysdig.com%2F%3FUTM_Source%3DContent_Syndication%26UTM_SFDC_Campaign%3D701f1000001cgkm%26UTM_Offer%3DSysdig-website%26UTM_Campaign%3D%26UTM_Medium%3Dpre-roll%26UTM_Content%3DDzone-microservices-zone%26UTM_Term%3D%26UTM_Creativeid%3D) is the container intelligence company. The only unified platform for monitoring, security, and troubleshooting in a microservices-friendly architecture.

In a true sense, every architecture and code is composed of bits - just 0 and 1 - and they have the potential to manage the information in various chunks. Data used to be managed with the close efforts of various architectures that had interdependencies. Consequently, the information flow was sometimes restricted, leading to technical chaos whenever any architecture level got affected.

Considering the potential threat to the information flow, some of the big players in data management like Netflix, Amazon, and eBay decided to take a chance with a modified platform with a new concept. Microservices architecture was the next destination after saturation of monolith architecture.

Microservice architecture is comprised of elements which work independently such that upon the failure of any element, the functionalities of the other elements are not affected and the process of information flow goes on uninterrupted. These elements are primarily business capabilities, which are often HTTP resource API, designed and deployed to work independently.

## Bringing Outstanding Microservices Architecture to the System

Unlike other system architectures, microservices architecture is differently designed focusing on the uninterrupted flow of data even in the case of the failure of a component(s)/element(s).

The design of microservices architecture can be easily understood with the following hypothetical example. Consider the development of a hypothetical server-side enterprise application where the application handles requests by working on business logic, database accessing, and returning to HTML, JSON, and XML responses. The application is expected to be responsive, must also be available to third parties, and must be able to integrate its microservices components asynchronously to run even at the time of partial failure of the microservice application.

The hypothetical server-side application must contain the following components:

  * **Presentation components**: components expected to handle the user interface and consume remote services.

  * **Database access logic**: data access components to access the database.

  * **Business or domain logic**: the application's domain logic.

  * **Application integration logic**: the logic that connects different components.

## Selecting Suitable Architecture

For the selection of the perfect architecture, the administrator must split the applications into autonomous subsystems which would act as the microservices components. Each component is independent and contributes to the called queries without affecting the performance of other components.

Every microservice is complete in itself and whenever necessary consistencies between databases from various microservices are achieved using application-level integration events through a logical event bus.

## Learning Microservices Deployment

Consider this hypothetical microservice application for an e-commerce enterprise, which is comprised of different components like a product catalog, order catalog, service catalog, and buyer's basket. The application has multiple subsystems, including different UI frontends (web application and mobile application) along with backend microservices and containers for all the required server-side operations.

![Image Credit: Microsoft](https://dzone.com/storage/temp/8678012-microservices-1.png)

> _A hypothetical instance of microservices (image credit: Microsoft)._

  * **Hosting environment**: In the above figure, it is clear that the Docker host contains several containers, especially when deployed to a single Docker host with the docker-compose-up command. However, if the user is utilizing an orchestrator or cluster, then each node is expected to run in a different node, and therefore, any node could successfully run any number of containers.
  * **Communication architecture**: The e-shop uses two types of communication architecture on the basis of functionalities: 
    * **Asynchronous event-based communication** is triggered by the event bus either to distribute updates through microservices or to integrate with external applications. The event bus can be implemented with the Azure service bus, NServiceBus, Brighter, or MassTransit.
    * **Direct client-to-microservice communication** is used for dual purposes; firstly, for queries, and secondly, for accepting updates or transactional commands from the client application(s).

The application is deployed in the form of containers through microservices. The client applications can communicate with a container as well as between microservices. Each microservice has a public endpoint and, if required, each microservice can use a different TCP port.

## Verifying the Precision of Microservices

The precision of the microservices in terms of performance is verified through a series of testing methods. It is Mike Cohen's Testing Pyramid that tells the amount of testing required. The testing procedure follows a bottom-up approach such that the scope of testing gets narrower, keeping the execution time of testing elevated. With the number of tests, the execution time and scope of testing share an inverse relationship.

![Image title](https://dzone.com/storage/temp/8678024-microservices-3.png)

> _Mike Cohen's testing pyramid (image credit: Microsoft)._

Regardless of the shared inverse relationship, microservices are tested with the following testing procedures:

  * **Unit testing**: Unit testing is preferably automated, although test automation entirely depends upon the development language and framework used in the microservice.

  * **Contract testing**: Contract testing treats every service independently while verifying their responses. This saves the other service containers from being affected in case one of the services under-performs.

  * **Integration testing**: Integration testing tests every service individually for performance. Service calls are made with integration to the external services that entail error and success cases. This method validates that the system is proficiently working and all the services are perfectly integrated.

  * **End-to-end/E2E testing**: E2E testing ensures that the process flows continuously with all services and database (DB) integration. The rigorous testing of operations ensures that the system works as a whole and can remain unaffected even if a component(s) becomes defunct.

  * **UI/functional testing**: UI/functional testing tests the application as it would be tested by the end-user. It gives the feeling of the user trying to interact with the system in real time.

## Microservices as a Complete Entity

Microservices have brought an evolution in system architecture, making the standardized components independent and responsive in case of abrupt failures. System professionals are sprinting to keep themselves updated with the new tools and technologies that can make microservices better than ever to counter upcoming and existing challenges. It is suggested to implement a customer-driven contract approach to eliminate risks whenever the services are exposed to disparate data without impacting the customer.

[Download our white paper:](https://dzone.com/go?i=278431&u=https%3A%2F%2Fgo.sysdig.com%2FSysdig-Architecture%3FUTM_Source%3DContent_Syndication%26UTM_SFDC_Campaign%3D701f1000001cgkm%26UTM_Offer%3Dsysdig-architecture%26UTM_Campaign%3D%26UTM_Medium%3Dtext-link%26UTM_Content%3DDzone-microservices-zone%26UTM_Term%3D%26UTM_Creativeid%3D) The Architecture of the Sysdig Container Intelligence Platform. Built for microservices and containers for monitoring, security, troubleshooting

Opinions expressed by DZone contributors are their own.
