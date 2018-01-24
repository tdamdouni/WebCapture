# Product Owners and Reactive Microservices

_Captured: 2017-11-26 at 20:06 from [dzone.com](https://dzone.com/articles/product-owner-and-reactive-microservices?edition=337909&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-26)_

"[Automated Testing: The Glue That Holds DevOps Together"](https://dzone.com/go?i=236222&u=http%3A%2F%2Finfo.saucelabs.com%2FAutomated_Testing_Glue_LP-DZone.html%3Futm_medium%3Dpre-roll_textlink%26utm_content%3Darticle) to learn about the key role automated testing plays in a DevOps workflow, brought to you in partnership with Sauce Labs.

## What Is a DevOps Product Owner?

A [product owner](https://www.scrum.org/resources/what-is-a-product-owner) is someone who is,

  1. Accountable for maximizing the value of a product,

  2. Incrementally managing and expressing business and functional expectations for the product, and

  3. Doing so by the means of a prioritized product backlog.

With DevOps, it has now become extremely important for product owners to use _"[Systems Thinking"_ (DevOps - Three Ways).](https://itrevolution.com/the-three-ways-principles-underpinning-devops/) They should look at the bigger picture and ensure that the importance of operability of a product is understood. A modern product backlog should describe the scalability, deployability, security, and performance, besides the functionality of a feature.

## Microservices

Recently there is a lot of buzz around [microservices](https://martinfowler.com/articles/microservices.html). I would say microservices support DevOps by enabling development and release of loosely coupled applications, but also the agile development idea of keeping things very small and iterative.

Microservices decompose an application into different smaller services to improve modularity and makes the application easier to understand, develop and test. It also parallelizes development by enabling small autonomous teams to develop, deploy and scale their respective services independently. It also allows the architecture of an individual service to emerge through continuous refactoring. Microservices-based architectures enable continuous delivery and deployment.

## The Reactive Manifesto for a Product Owner

To get the most out of microservices-based systems, we should embrace the four principles outlined in the [Reactive Manifesto.](https://www.reactivemanifesto.org/)

![Image title](https://dzone.com/storage/temp/7238898-reactive-manifesto.png)

Let us apply the Product owners lens on the Reactive Manifesto to include the Operability aspect in the Product Backlog

**Responsive: **A responsive system responds in a timely manner. Responsiveness is the cornerstone of usability to gain end-user confidence.

**_PO Lens: _**Cleary specifies the performance parameters for the feature or user story being developed. Include details about the logging, monitoring, or an alert mechanism for the piece of functionality to ensure consistent behavior and rapid error handling.

**Resilient: **The system stays responsive in the face of failure.

**_PO Lens: _**Think about the scalability of the product/service considering the responsiveness expected. Do we scale up or scale out (add or replicate)? How should the service react in event of failure or delay in response, should there be an alternate flow?

**Elastic: **The system stays responsive under varying workloads. Reactive Systems can react to changes in the input rate by increasing or decreasing the resources allocated to service these inputs.

**_PO Lens:_** Include Replication, Location and Access transparency wherever possible. The solution should not be affected if the system resources are replicated, scaled down or up to handle the varying load.

**Message Driven: **Reactive Systems rely on asynchronous message-passing to establish a boundary between components that ensures loose coupling and isolation.

**_PO Lens:_** Use asynchronous communication wherever applicable, as it fosters Elasticity and Resilience to achieve higher responsiveness. It supports parallel execution and effective error handling.

![Image title](https://dzone.com/storage/temp/7238899-po-lens.png)

> _So, in summary, a DevOps Product Owner needs to:_

  1. Embrace "System Thinking" and focus on the complete lifecycle from conceptualizing to maintenance of a new feature.

  2. Understand the "Operational Requirements."

  3. Ensure that the "OR's" or the "NFR's" are seen as important as the "Functional and Business Requirements" in the Product roadmap and champion their implementation.

[Learn about the importance of automated testing](https://dzone.com/go?i=236223&u=http%3A%2F%2Finfo.saucelabs.com%2FAutomated_Testing_Glue_LP-DZone.html%3Futm_medium%3Dpost-roll_textlink%26utm_content%3Darticle) as part of a healthy DevOps practice, brought to you in partnership with Sauce Labs.

Opinions expressed by DZone contributors are their own.
