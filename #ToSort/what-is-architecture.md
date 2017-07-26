# What Is Architecture?

_Captured: 2017-01-23 at 00:52 from [dzone.com](https://dzone.com/articles/what-is-architecture?edition=263911&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-22)_

Learn how API management supports better integration in [Achieving Enterprise Agility with Microservices and API Management](https://dzone.com/go?i=126027&u=http%3A%2F%2Fpages.3scale.net%2Fmicroservices-api-management-dzinteg.html), brought to you in partnership with [3scale](https://dzone.com/go?i=126027&u=https%3A%2F%2Fwww.3scale.net%2F%3Futm_campaign%3Ddzintegration%26utm_source%3Ddzoneint%26utm_content%3Dbumper)

On a regular basis, we hear people speak of good and bad architecture. However, what _is _architecture?

Before I describe software architecture, let's see if we can come to an agreement of what architecture is. What are the components of architecture and value does architecture have?

Architecture provides the structural and connective framework required for a system of components to function. Architecture is specific to a context. Good architecture for a software system is different from that of a car or a building.

Architecture, in general, is not visible. It is present in the system, but only under other visible design components. Before a discussion of software architecture, it would be best to describe architecture using physical objects.

## Architectural Elements

Architecture involves two elements:

  1. Structural elements.
  2. Connective elements.

Let's look at these two elements with respect to a building.

Structure for a building involves the foundation and the pieces that provide support to the entire building; it is the skeleton of the building. If a building has an interesting shape it is because underneath the framework of rebar and concrete support the shape.

Connective elements can be structural, but they provide a way of linking different structural components for the purposes of transporting something. Connective elements in a building transport air, water, and electricity.

The structural capability of the framework will dictate how high a building can go. Generally speaking, architecture determines size. If the building has a framework of rebar and concrete that will support a 10-story structure, it will be difficult to add additional floors over 10 easily. Adding additional floors will require effort expended to reinforce the existing structural strength of the building

If a connective element is missing, adding it will be expensive. For example, old brick buildings often didn't plan for plumbing or electricity. If this element is added afterward, then it will be much more expensive to put in.

If plumbing is added afterward, then you will see the plumbing running outside the walls. This can lead to problems if the building experiences sub-zero weather.

It is similarly inconvenient to add electricity or air-conditioning to a building that did not have these connective elements designed into the building when it was built.

For comparison purposes, let's look at architecture in a couple of contexts:

**Object**
**Structural Component**
**Connective Element**

**Building**

  * Steel frame.
  * Concrete.
  * Bricks.

  * Plumbing.
  * Electrical system.
  * HVAC system.
  * Elevator.
  * Emergency stairwell.

**Car**

  * .Chasis
  * Tires.

  * Drive train.
  * Steering column.
  * Gas conduits.
  * Electrical system.
  * HVAC system.

## Architecture and Visibility

In the two examples above, several things about architecture stand out:

  * Structural components are generally hidden unless they are functional.
  * Connective elements are covered up in the final object.

So, for a building, the structural element of the steel frame is invisible hidden under finishing elements. However, there are cases where we see concrete or brick walls exposed. Structural elements are generally not attractive and so we put in extra effort (i.e., cost) to hide the structural elements. Sometimes, in the case of concrete or brick walls, we will leave them exposed because the visual need to hide these elements are not there, i.e., a warehouse.

Connective elements are almost always hidden. The sight of electrical wires, plumbing, or HVAC tubes is not aesthetically pleasing and we generally hide these elements. If we are hiding a connective element, they are cheapest to put in when an object is being created the first time.

## Cost of Fixing Hidden Connective Elements

Repairing a hidden connective element is expensive. For example, fixing plumbing and electrical wires in a house are expensive depending on how hard it is to access the connective element.

Adding a connective element after the fact is much more expensive and much less attractive. There are brick buildings that were built prior to indoor plumbing and electricity being available. A good example of these buildings are the residences at Harvard or old brick warehouses that are now office space. In the case of the Harvard residences the plumbing runs outside the residences and due to the winter weather in Boston, is subject to freezing. Adding electricity to a brick warehouse involves running metal conduits inside the walls; since they are exposed, they are subject to water accidents.

## Visible Structural Elements

In the case of a car, the tires are a structural element, but they are exposed to view. This is why effort goes into making the tires as attractive as possible, i.e., white wall tires, decorative hubcaps, etc.

## Purpose of Architecture

Once the architecture is set it determines two things:

  * The size of an object.
  * The functional capabilities of the object.

As previously mentioned, the structural architecture of a building will dictate its maximum size and the connective elements will outline its capabilities. Connective elements are always about functional capabilities.

The purpose of structural architecture is to partition an object into sub-components that are independent and can be designed separately. For example, in a building, the structural architecture allows you to subsequently design each of the apartments separately without worrying about how the design of one room affects another.

For a car, the main structural element of the chassis allows you to design the following sub-components separately:

  * Engine.
  * Doors.
  * Lights.
  * Seats.

By allowing sub-components to be designed separately we subdivide a problem (i.e., divide and conquer), which reduces the complexity of the overall design. It allows separate teams to work on the sub-components. Good architecture facilitates strong polymorphism in the sub-components.

In the case of apartments, each apartment can be designed differently and by different people. In a car, the engine can be designed by one group of people different from that designing the doors, lights, or the other part of the car.

The connective components in each object either provides a shared service that is accessible to multiple components or provides a coordination of sub-components to achieve a higher level function.

Electricity, plumbing, and HVAC are all examples of shared services that are available to an entire building. The usage of electricity in one room does not dictate the usage of electricity in another room, however, aggregate usage of electricity is sized by the architecture.

![Image title](http://nitoautogas.com/upload/system_lpi.png)

Elevators for a building and steering columns and the gas system of a car are examples of components that are coordinated across multiple levels of the object. They provide an overall functionality when all of the sub-components coordinated are functioning.

In general, if one of the sub-components is not functioning then the entire set of coordinating objects will fail to function. For a car, if any component in the diagram fails then the engine itself will fail.

## Summary

In any object composed of multiple subobjects, there is architecture. Architecture provides two different but related functions:

  1. Structural components.
  2. Connective elements.

The architecture of an object dictates how large it can be and determines how separately each sub-component can be designed.

Unleash the power of your APIs with future-proof API management - [Create your account](https://dzone.com/go?i=126028&u=http%3A%2F%2Fpages.3scale.net%2Ffuture-proof-api-management-dzinteg.html) and start your free trial today, brought to you in partnership with [3scale](https://dzone.com/go?i=126028&u=https%3A%2F%2Fwww.3scale.net%2F%3Futm_campaign%3Ddzintegration%26utm_source%3Ddzoneint%26utm_content%3Dbumper).
