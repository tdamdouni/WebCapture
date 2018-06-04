# Moving to Microservices

_Captured: 2018-03-27 at 15:59 from [dzone.com](https://dzone.com/articles/moving-to-microservices?edition=367224&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-26)_

[Learn how to track microservices](https://dzone.com/go?i=274457&u=https%3A%2F%2Fwww.appdynamics.com%2Fapp-iq-platform%2Fmicroservices-iq%2F%3Futm_source%3Ddzone%26utm_medium%3Dsponsorship%26utm_campaign%3Dmicroservics%252520sponsorship%26utm_content%3Dmicroservics%252520sponsorship%26utm_term%3Ddzone%252520microservics%252520sponsorship%26utm_budget%3Ddigital) deployed in elastic infrastructure such as containers or cloud where nodes scale up and down very rapidly.

![Image title](https://dzone.com/storage/temp/8573837-microservices.png)

## Microservices Architecture

The microservices concept is similar to a "divide and conquer" type of architectural approach. This approach has been around: service-oriented architecture. Technologists are attracted to microservices mainly for the following set of predominant benefits:

  1. **Development dependencies:** Minimized code conflicts, ability to deploy partial implementation through isolated developments and deployments specific to each service.
  2. **Scalability:** Distributed horizontal scaling to overcome fault tolerance issues and performance issues with geospatial users.

## Microservices Benefits/Pitfalls

Microservices as a concept is an illusorily simple one. Ideally, they are multiple self-contained single-service applications (extracted from a centralized monolith architecture, in the case of migration) that are de-centralized/distributed and talk to each other through predefined APIs.

> "If you can't build a monolith, what makes you think microservices are the answer?" -Simon Brown 

These microservices benefits are not that easy to deliver if there are no proper architectural plans and goals predefined in the course of this movement. Microservices architectures can become complex to manage. Distributed systems have ways of failing that you've never thought of before.

Let's explore further on these benefits and how to achieve a closer effect without moving away from the monolith:

## **Development Dependencies**

A very common attraction to migrate to microservices architecture approach is to make it easy for managing development dependencies that are being faced by teams. If you have a large team all working on the same big codebase then that can cause clashes and merge conflicts and there will be a lot of code for everyone to understand.

Points to be considered:

### Code Conflicts Mostly Arise From Communication/People-Practice Issues

It would immediately seem very easy if all the services were smaller and isolated by a clear interface. That way each microservice could be owned by a small team who could all work together.

The actual problems with code conflicts and clashes are mostly related to communication problems or team management problems. Although technology approaches/tools will help to improve the situation, they cannot eradicate this completely. Revisiting this in terms of resolving people and communication issues instead will definitely improve cultural situations.

> "[With distributed teams] Face-to-face communications are rare. Hence fewer connections between modules are established. The architecture that evolves is more modular as a result of the limitations on communications between developers." -Harvard Study 

### Local Development Environment Overheads

In addition, many technologists, when deciding to move towards microservices, don't consider the local development environment-related complexities that will come along with it. In case of a monolith approach, this will be a piece of cake, whereas it will be complex to achieve if the microservices have multiple services interdependent on each other, in terms of achieving a single business workflow lifecycle. Containerized solutions also will not be that easy when it comes to local environment setup.

## Scaling Out

The self-contained nature of microservices allows an individual instance of a microservice to be decoupled not only from other microservices but also from itself. This allows running of duplicate services in parallel. This effectively brings in horizontal scaling. As an additional effect, it provides resilience and a way to achieve fault tolerant systems.

Points to be considered:

### Data Tier Isolation

Most technologists who adopted microservices still use the same data tier for all of their microservices (i.e. not isolating the data tier for each microservice to handle its own responsible data). This setup brings in the horizontal scalability only for your service and not for the entire applications. There are hurdles to achieving clean data-tier isolations when aligning with the microservices/modular separations. One example is achieving distributed database transactions. This will require re-architecting the business logic adhering to the [saga pattern](http://microservices.io/patterns/data/saga.html) or using Java DSL with Spring Integration techniques.

> "In general, application developers simply do not implement large scalable applications assuming distributed transactions." -Pat Helland 

### Resilience, Fault Tolerance, and High Availability Through Scalability

![Image title](https://dzone.com/storage/temp/8561235-microservices-02-loadbalancer-scaling.png)

If the aim for scaling out is just to achieve fault tolerance and high availability, then the easiest way to scale a monolith is to simply deploy additional copies of the subject monolithic applications behind a load balancer. This is a straightforward way to scale up if your system receives more traffic, and it involves minimal additional complexity from an operations perspective. Even in a cloud environment, this can still be achieved using something similar to Beanstalk techniques. Just optimizing CI/CD settings will be enough to manage these multiple copy deployments properly.

### Network Latencies

The multiple modules within the monolith application (with well-defined APIs) nearly have zero overhead when interacting with those APIs. This is definitely not the case with microservices, since they are often running on different host machines and require a network between the services. This can slow down your whole system considerably (if they are getting hosted on-premise microservices platform). This situation becomes even worse if you have some services which need to contact multiple other services, synchronously, in order to complete a request (i.e. response time for a particular business transaction may increase due to underlying network issues, if not established and monitored properly).

## Starting Monolith Improvements

Following rough guideline stages shall be incorporated into the context of the subject monolith application if applicable. These stages will typically solve many of the problems that cause teams to move towards microservices, and without all the associated complexity/learning curve/high amount of time & effort. And yet taking it to closer to the similar benefits that we may expect from microservices.

  * Refactor application to make sure to bring in automatic testing.
  * Refactor application into isolated modules with clear API definitions without encouraging any overlap of code pieces into the modules directly. All modules must talk through APIs only.
![](https://media.licdn.com/dms/image/C5112AQGFtslWKXN10w/article-inline_image-shrink_1500_2232/0?e=2120878800&v=alpha&t=o-AeS-vKMo1nDM2TXEwr1ewGEfG--6IK9wmDm_49dlg)

  * Choose critical module(s) and take it out of monolith application pack, split it into its own application on the same host (if capacity allows). The communication and security setting will have to be sorted out treating them as two different applications interfacing with each other through properly defined APIs. This will be a step that makes a module ready for further distributions in future if traffic for that particular increases.
![](https://media.licdn.com/dms/image/C5112AQF8ffvHpTLzJw/article-inline_image-shrink_1500_2232/0?e=2120878800&v=alpha&t=9m2sP1BoUTl9J46ZbOSQQ_GBtZ_N2WLrbW1RpPs78uM)

  * Move separated module(s) and put it on a different host system(s) (VM(s)) for the purpose of size optimization specific to the nature of these modules. (i.e. one module may require more memory allocation than others, considering the amount of data it might require in the course of processing a request). This shall be duplicated with front-ending load balancer for achieving fault tolerance and high availability.
![](https://media.licdn.com/dms/image/C5112AQEWouPdcQf6bw/article-inline_image-shrink_1500_2232/0?e=2120878800&v=alpha&t=_Mnv9Wek7qGJSLW8D9p33MC5K2jvUcJyfQW6H0V8kfw)

  * Finally refactoring the data tier for bringing in the same level of isolation that has been introduced at application modules'. If it is RDBMS, try to see for options to improvise with ORM and ORM caching techniques to improve performance. It might be started with a separate set of database tables isolated from each module within the same database as an intermediate step to assess and understand the complexity involved before isolating them into a separate database.
![](https://media.licdn.com/dms/image/C5112AQFbJ3VE2ufKPQ/article-inline_image-shrink_1000_1488/0?e=2120878800&v=alpha&t=250ALQBLJTB3cDt9w2CmCxJBs0Y1lIV1N82gar9-724)

## Conclusion

This is simply a summary of my observations and collation of other's experiences in the journey of migrating to microservices from monolith architecture approach. Hope technologists shall find these high-level concepts useful to factor-in while preparing/considering for movement towards microservices approach. If there are strong prerequisites that are in need of microservices architecture approach, they may exempt from these stages.

[Understand and immediately diagnose](https://dzone.com/go?i=278422&u=https%3A%2F%2Fwww.appdynamics.com%2Fdocker%2F%3Futm_source%3Ddzone%26utm_medium%3Dsponsorship%26utm_campaign%3Dmicroservices%2525252520sponsorship%2525252520docker%2525252520%26utm_content%3Dmicroservices%2525252520sponsorship%2525252520docker%2525252520%26utm_term%3Ddzone%2525252520microservices%2525252520sponsorship%2525252520docker%2525252520%26utm_budget%3Ddigital) the performance issues within your microservices architecture with Docker Monitoring
