# Microservices Design Patterns - API Gateway

_Captured: 2017-12-05 at 13:46 from [dzone.com](https://dzone.com/articles/7-important-microservices-design-patterns-every-de?edition=343093&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-04)_

Share, secure, distribute, control, and monetize your APIs with the platform built with performance, time-to-value, and growth in mind. [Free 90 day trial](https://dzone.com/go?i=257321&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Ftechnologies%2Fjboss-middleware%2F3scale%2Fget-started%3Fsc_cid%3D701f2000000tnttAAA) 3Scale by Red Hat

Design patterns…a valuable tool in the life of an architect or a savvy developer. We have hundreds of them. Many ways to solve common problems, in many areas. Since the GoF (Gang of Four) pattern catalog, we gave the proper attention to and started to use them in our complex projects, with great success.

The design patterns are here to help you, no matter which the complexity of the problem is. The microservices world is no exception.

Due to many challenges brought by the complexities of the Microservices Architecture Style, we looked back and saw many approaches that did succeed so far. Now we have a Design Pattern consensus in the format of a catalog for this type of architectural solutions, being constantly updated and reviewed by the community.

In this article series, we'll highlight the most popular and important design patterns that you should care about in microservices architecture and which tools or approaches you can use in order to apply it in a correct and easy way.

In this post, we'll give you an intro of the overall topic and pick one of the most popular design pattern used in microservices solutions - **The API Gateway pattern**.

So, let's get started.

## Pattern #1 - API Gateway

### Context

Systems need many pieces of information that are spread across several services within the service catalog. In addition, many types of clients consume the system's services, adding more complexity to the final solutions when we start thinking about the evolution of those services, respecting the communication and data size/format tradeoffs for each of those clients.

This way, the services must be able to "talk" to each of this clients (and to be easily discovered) without losing non-functional requirements of performance, maintenance, scalability, security, and availability needed to support these distributed solutions.

To respond to the ever-increasing need for information and velocity, more and more service instances should be provided to support the right scalability- adding, of course, more complexity.

So, the API Gateway pattern should be handy in this scenario…

### Main Objective

The purpose of the API Gateway is to represent a single point of entry to all those clients, and at the same time, to abstract the complexities of communication issues such as protocol transactions and data conversions.

The picture below highlights the API Gateway pattern in microservices architecture:

![Image title](https://dzone.com/storage/temp/7270038-untitled-page.png)

### Direct Benefits

The API gateway is a protocol-agnostic solution that serves distinct clients across several communication channels. It exposes each API for each consumer, according to the communication and client types, and embraces security once it is the main entry point. It abstracts any refactoring or break-down structures on existing systems (the so-called monoliths) to its clients, and abstracts underlying microservices topology and technologies involved to final consumers.

### Drawbacks

The API gateway also adds a new layer of complexity to the final microservices solution, both in implementing (or maintaining) the API gateway with a new or existing technology/product, and governing the evolution of the API's contract, so it's important to distributed solutions.

As we should expect, adding a new layer to the overall architecture decreases the response time due to conversational costs to request all microservices involved in a specific transaction in a particular business context.

### How to Implement It

Today the most popular available implementations to realize an API gateway solution are:

In the next posts, we'll explore in detail some of these solutions.

## Summary

Essential to every microservices solution, the API gateway pattern helps improve service messaging, and at the same time, abstract some of the complexity and details that exist in every microservice call. At the same time, it serves as the main entry point to every kind of client.

Thanks for reading.

Discover how you can [achielve enterpriese agility](https://dzone.com/go?i=257322&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Fresources%2F3scale-enterprise-agility-with-microservices-api-management-whitepaper%3Fsc_cid%3D701f2000000tntUAAQ) with microservices and API management
