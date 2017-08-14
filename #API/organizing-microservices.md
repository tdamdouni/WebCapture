# Organizing Microservices

_Captured: 2017-08-05 at 23:10 from [dzone.com](https://dzone.com/articles/organizing-microservices?edition=313394&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-05)_

[Modernize your application architectures with microservices and APIs](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) with best practices from this free virtual summit series. Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Microservices is probably one of the most popular buzzes among my fellow developer friends, and I do like the concept of being flexible, agile, and having simply having more choices. But as a person that worked in the software integration space for years, I started to see some resemblance to the old ESB days.

Looking at the problem from ten thousand feet up: A decade ago, we had to come up with a better way of organizing the spaghetti connections in between systems and stop duplicating effort on the same piece of business logic. That is when service oriented architecture (SOA) became popular. By modularizing services, sharing them among others systems, and organize ways of communication, routing of data. And ESB is one implementation of that, maybe not necessarily how it should be done.

### ![](https://lh4.googleusercontent.com/iLy8J5--BzZA8uCoP-oYddYILQ5iYI4XmsmfNUOHOhMaDWFv6c3cgpBE1yKPxqn2eoSzaNObGTXeClyGwCyUjNEWEc-e3PLYfko_vescnQMs8_aQJnhEqp7hxCCDbuQLU0MbmpGV)

I was very fortunate to participate in many of these kinds of integration projects, and lead some myself. We worked with various middleware vendors; at the time the solutions were all about ESB. By removing the complex interconnecting logic between systems into ESB, negotiating data models among teams (with application/services leaders), setting up WSDL contracts for web services, and adding BPEL processes if needed between calls. And I had seen a fair share of these ESBs myself- outside of the ESB, everything seems very organized. But lift up the ESB "box" you will find many of them end up with even worse tangled spaghetti code (or diagrams, depends on your tooling). And that giant bundle of chaos then becomes the bottleneck in delivering changes in enterprise.

### ![](https://4.bp.blogspot.com/-QWD-mwjaP5Y/WX9sPj486AI/AAAAAAAAFTg/rgPlHFf77yUxzjkOWgCdVKuhD2GzasnTgCK4BGAYYCw/s320/esb.png)

(On a side note: this is when I started on the lightweight ESB idea, and how I was introduced to Camel, Karaf, and servicemix because it solves my problem of independently bundling my integration code and breaking that ESB box into a smaller distribution..and so on..) When the idea of independently deployable microservices came along, this giant monolithic monster with idea of a smart pipe where it tries to do too much, like data model definition, process flow, interconnect protocols and data format transform, and dumb endpoints where services just wait to be activated by events, was soon cast aside by developers. The relationships between each service are still messy and the monolithic nature makes the cycle of development long and cumbersome. The microservice allows developers to be more agile, who needs that piece of "Integration." So this is the resemblance to a problem I was once trying to solve.

![](https://lh3.googleusercontent.com/cUSxRio5nBYmDSR7FlPxf4tksy3JKue-LIGOFK4NwWKsHu-35lcnXbGjg_pIPoRlHDd9QNbXEQdP4XgwztFq-kFuTGzGiiy_ZZmcGJGNfq0enFhGeC8BBCt8C5wT6ymc4s0Ge2Ws)

We still need to interact with other services (systems/applications) outside microservices. So, learning from the past, here are the things we know what NOT to do:

  * No more large monolithic bundle applications, to speed up the dev cycle.
  * Stop doing complex business processes inside system integration code.
  * The data model shouldn't be defined in the integration layer; it only leads to extra negotiation between teams.
  * The state should not be kept in the integration layer, to allow maximum scalability
  * Create fixed complex contracts between services.

And still, there are things we liked about the old "integration" way:

  * Organized, visualized, interconnected view of systems.
  * Patterns that are already defined for integrating applications such as aggregations, separation, and normalization of data.
  * An event-based approach. A more reactive way and less coupled ways to integrate systems.

And that is why I came up with the layered architecture for microservices. The main goal that I wanted to achieve in the new integration architecture in the modern integration/application development is flexibility. Not only in the scalable way, but also allowing the developer to make any architectural change with ease. So first things first, in the new modern agile integration, the integration code itself should be sorted into different small services that make sense in the business world, and are decoupled and made to be independently deployable microservices units. Then we can start to apply true CI/CD to the integration code. This will avoid becoming a large monolithic ESB.

![](https://lh6.googleusercontent.com/wZqqX4rjeK8odspg2lAKLs3w2Abd8LzJCG7iqTP_XbNTOYv_YKRda5nTVr7qD-3_4AmmKkUXU8-h2J6ZbAHVFyj0HkWJRR52jGW23UO4XOa2g8vzorjVMb-lfDuG_NZ5iQS2dtCM)

In order to bring some logical sense to my microservice spaghetti, and avoiding repeating the mistake of taking on too much in one single integration bundle, I have defined four layers for my microservice, so each will have its own responsibility, making it easier to adopt changes.

  * Gateway layer: provides simple gateway routing capability such as versioning and dealing with different platforms of devices. ![](https://1.bp.blogspot.com/-xnO352Kf5DA/WX9soBJ_t-I/AAAAAAAAFTo/_4uvqWfUhZA7xobMxzQE-QFq6i2ihSU2QCK4BGAYYCw/s640/Reference%2BArchitecture%2B-%2BGateway%2Blayer.png)

Originally, I wanted to divide this layer into two, but decided not to because of the gateway pattern has become so popular now; people have the perception that the gateway should achieve certain abilities (that is a whole other story I want to talk some other time). That is why I have two separate forms of the gateway in my diagram- one represents as green, the other blue.

It's all about the separation of concerns. This layer is all about putting together what is needed for external API consumption. This is where and when separate application domains try to integrate with each other and route to the correct versions of services. And clearly, the major concerns were:

  * Accessing policy rules, versioning of endpoints (APIs).
  * Setting traffic throttle, applying limits and policies.
  * Security of APIs.
  * Routing to the correct versions.
* Combine, transform, and return result to client.

  * Citizen developers are the main creators here, they use the capability provided by each microservice team to put together meaningful services for external clients.
  * Collect, split, or normalize a canonical data format to external users.
  * Translate data output depending on the clients.
  * Routing between application domains.
  * Composite layer: the important middle tier that handles composition of multiple microservices. They do more complex routing from processing the content data and aggregates/split data and populate the split/aggregated result to other microservices by triggering events, or simply passing it. This layer hides the complexity of microservices away from clients.
![](https://1.bp.blogspot.com/-MF3-LQz1_Cc/WX9ssB8DleI/AAAAAAAAFTw/E40WZicPeggJhM-p5e4sjj3jNsCIrASFgCK4BGAYYCw/s640/Reference%2BArchitecture%2B-%2BComposite%2BLayer.png)

> _This layer is probably the layer that does most of the old time integration logic where it is responsible for_

  * Composing microservices.
    * By calling the API available from microservices, transforming data as needed between them, and routing data to the corresponding microservices based on its content.
  * Triggers events within the domain.
    * I believe strongly that event base does best at decoupling stickiness between each service, and allowing performance at its best because of its asynchronous nature. The event bus here doesn't necessarily have to be a message broker, but any form of Bus. 
  * Enrich contents.
    * The content enrichment here should be specific to the format and avoid any business side enrichment when possible.
  * Applying integration patterns.
    * The old integration problem will not just go away in the microservices world. By applying proven patterns, we can avoid making mistakes.
  * Caching.
    * The REST architecture specifically talks about a caching layer. It makes sense for the composite layer to try to apply a caching mechanism because it's non-business related, but does make a significant impact on the performance and fault tolerance ability of the system. 

The composite services should also be included in the application domain, which I will talk about in the basic layer.

  * Base layer: like the name, which most likely represents the basic components of the system. Handles data retrieval or business logic processing. Each should be independent and self-contained.
![](https://3.bp.blogspot.com/-txwlmM6EA60/WX9sxctg6uI/AAAAAAAAFT4/wU2oK2911B4qOKoT395e6knWtUKizoOdwCK4BGAYYCw/s640/Reference%2BArchitecture%2B-%2BBase%2BLayer.png)

Borrowing from the idea of Bounded Context, in this case, a logically organized group of microservices into what is called application domain where each domain represents separate entities of business functions that shares the same data model, eliminates the need to do too much transformation in the code.

  * Anti-corruption layer: this layer handles the interface to legacy applications or anything that works against microservices' quick and flexible principle. This layer is a built in protection wall to your system, by doing the transforming job and translating between two very distinct implementations of the system. 

Until next time!

The Integration Zone is proudly sponsored by [CA Technologies](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Learn from expert microservices and API presentations at the [Modernizing Application Architectures Virtual Summit Series](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
