# Microservices Solution Patterns

_Captured: 2017-12-14 at 23:35 from [dzone.com](https://dzone.com/articles/microservices-solution-patterns-1?edition=342136&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202017-12-14)_

[Modernize your application architectures with microservices and APIs](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) with best practices from this free virtual summit series. Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Microservices Architecture (MSA) is reshaping the enterprise IT ecosystem. It started as a mechanism to break the large monolithic applications into a set of independent, functionality focused applications which can be designed, developed, tested and deployed independently. The early adopters of MSA have used this pattern to implement their back-end systems or the business logic. Once they have implemented these so-called back-end systems, then came the idea of implementing the same pattern across the board. The idea of this article is to discuss the possible solution patterns which can be used in an MSA driven enterprise.

At 33,000 feet, enterprise IT system looks like the picture shown below.

![](https://lh6.googleusercontent.com/lEH3eRICZivv7ng1peyvm8z_8pH6tbmLQ-RxDKKQ0ZQGLI793spfoWCY-L2cwjV_w-Gbmo4pQd8hFnSm4hR39hKg658h5FhICAyStfBCMrDuq6Nxr3DhSZNFzRhCvuw7uEbUVaMH)

> _Figure 1: Enterprise IT system at 33000 feet._

As depicted in the above figure 1, the system is comprised of multiple layers horizontally and vertically. The business logic will be implemented in back-end systems as monolithic applications and there will be third-party systems like ERP, CRM, etc. On top of the back-end systems, there is the integration layer which interconnects heterogeneous back-end systems. Once these services are integrated, they need to be exposed as APIs to internal and external users as managed APIs through API management layer. Security and analytics will be used across all those 3 layers. With the introduction of the MSA, this entire ecosystem is opened up with new solution patterns which can serve the purpose of different enterprises based on their needs.

## Pattern 1: MSA BE + Monolithic ESB + Monolithic APIM

This is the most common and the starting pattern of microservices implementations where back-end systems (business logic) are developed as microservices while keeping the other layers as is.

![](https://lh6.googleusercontent.com/vwDkmjYckkPxH_m6gg0KjwdAsDd0qE7MhxCIfhFghqSae74PiXmbX5I3RzSR9Dvd0a9WT7uhalgjPWJr9Kmi4ySRvpWVxq7KG7sWJ8Ha4aeT62AA7GQHHdcnhnzI3hk4gOBxOvMn)

> _Figure 2: Pattern 1 - MSA BE + Monolithic ESB + Monolithic APIM._

The above-mentioned pattern is a good starting point for any organization to bring in the MSA and evaluate the pros and cons of the approach. Based on the results of this approach, a wider adoption can be done by moving into the patterns mentioned below.

## Pattern 2: Monolithic APIM + Service Mesh + Message Broker

The latest development of the MSA is the concept of a "service mesh," which provides the additional functionalities which are required for communication between microservices. The message broker is used as the communication channel (dumb pipe) for message exchange across microservices. This will reduce the requirement of an integration layer in some use cases.

![](https://lh5.googleusercontent.com/FisbZFvyKO8DLqud2SENH-YAIM6nP2C18dzfkmRMo3criNX5weJW5jb9C4-Q6o_Hd7fTulwUWNAcYQG8i3SbgYaZYSHpy7NxSLAJRmMSKr1hQyM1IbFmmZn9xa5Tjg413VY3LQMr)

> _Figure 3: Pattern 2 - MSA BE + Service Mesh + Message Broker._

As depicted in the above figure 3, in this solution pattern, MSA has extended to the integration layer and removes the need for a separate integration layer. Even though this pattern can be implemented for a green field IT organization, it will be harder for larger enterprises with so many additional systems.

## Pattern 3: Monolithic APIM + Micro Integration + Service Mesh

One of the challenges of the Pattern 2 is to integrate CRM, ERP kind of systems to the microservices layer. Instead of doing the integration at microservices layer or through message broker, it is possible to bring in a micro integration layer to fulfill this requirement. With that, Message Broker functionalities (messaging channel) can also be moved into the micro integration layer.

![](https://lh4.googleusercontent.com/VgrXifNqsWaGPLac9LvXo_74zrGLo1JU4d1RZUWgC5E-YqkrOqIMgPNDv7VSp2P8-O0iSajvh_kCbPQJoBEH0tZBeyaCQoQsm7br07nabEztk1wFuQU6kmE0yFV3Jk4JwnNZ8lkl)

> _Figure 4: Pattern 3 - Monolithic APIM + Service Mesh + Micro Integration._

As depicted in the above figure 4, microservices, database systems, and COTS systems (ERP, CRM) are integrated using the micro integration layer.

## Pattern 4: Service Mesh + Micro Integration + Edge Gateway

With the widespread adoption of microservices architecture within the enterprise, the monolithic API gateway can also be replaced with a micro-API gateway or an edge gateway. This is the next solution pattern which can be implemented.

![](https://lh5.googleusercontent.com/7CqFfxsGKR7XfAhx50gHwBGOCk8FHYTfJxUcf_2DGSASVz2DEKHa1xd2fQ2KWXnprDLjVbNtX4vXc8oxtMSfcQAzUm9UydEkM4EIcYlbmZEs9NPYcViMpi6NoR8DhSOG7TeMyyip)

> _Figure 5: Pattern 4 - Edge gateway + Service Mesh + Micro Integration._

In this pattern, monolithic API management layer is replaced with a set of edge gateways which are deployed based on the APIs which are exposed to the users. These edge gateways behave similarly to microservices when it comes to design, develop, test and deployment while providing the API management functionalities.

## Pattern 5: All MSA

Once the microservices wave is in full swing, security, analytics and database layers can also be implemented as microservices, except the COTS systems, entire enterprise IT ecosystem is implemented as microservices in this solutions pattern.

![](https://lh5.googleusercontent.com/9ENgAVNf5XIaUFdDp51dcKgwWyXYSyHE_z-9aFLYh2IFOSwq4wNnKkiL0COvie4DNbJGDAqPfjwBmGYiJGvwsDMVFNNDIQaphRybKVk5S8tmDj62dwwo1D-fzsFV8KgRgApUauri)

> _Figure 6: Pattern 5 - All MSA._

As depicted in the above figure 6, all the component within the enterprise are implemented as microservices except third-party systems. This pattern can be extended so that service mesh is extended across micro integration, analytics, security, and database microservices.

The Integration Zone is proudly sponsored by [CA Technologies](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Learn from expert microservices and API presentations at the [Modernizing Application Architectures Virtual Summit Series](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
