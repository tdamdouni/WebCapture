# Top 5+ Microservices Architecture and Design Best Practices

_Captured: 2018-03-28 at 20:30 from [dzone.com](https://dzone.com/articles/top-5-microservices-architecture-and-design-best-p?edition=369206&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-28)_

[Sysdig](https://dzone.com/go?i=278430&u=https%3A%2F%2Fsysdig.com%2F%3FUTM_Source%3DContent_Syndication%26UTM_SFDC_Campaign%3D701f1000001cgkm%26UTM_Offer%3DSysdig-website%26UTM_Campaign%3D%26UTM_Medium%3Dpre-roll%26UTM_Content%3DDzone-microservices-zone%26UTM_Term%3D%26UTM_Creativeid%3D) is the container intelligence company. The only unified platform for monitoring, security, and troubleshooting in a microservices-friendly architecture.

Microservices-based application architecture represents a collection of small, autonomous, and self-contained services which are built to serve a single business functionality/capability. The following is a sample microservices-styled application landscape representing a set of microservices. Pay attention to different microservices accessed through the API gateway.

![Image title](https://dzone.com/storage/temp/8625488-screen-shot-2018-03-27-at-43830-pm.png)

> _Microservices architecture (Image courtesy: Cloud Application Architecture Guide)._

In this post, you will learn about some of the best practices related to microservices-styled architecture (MSA) which can be adopted when creating the microservices-based application. The following are some of the best practices related to microservices which you may consider following while doing application implementation based on microservices-styled architecture:

  * **Model Services based on Domain-driven Design (DDD)**: Services should be modeled around the business domain. Check out some of the following great reads in relation to **domain-driven design**. 

  * **Consider separating data storage**: Data should be made private to each of the microservices. Microservice becomes the **owner of its data**. **Any access to data** owned by a specific service should **only happen through APIs**. Failing to do so would allow multiple services to access the database owned by a specific service leading to **coupling between services**. The architecture pattern such as CQRS (Command and Query Responsibility Segregation) comes handy in taking care of data which required to be read by different kinds of users.
  * **Build separate teams for different microservices**: Teams should be divided based on microservices with one team working on one microservice. This consists of product manager, and DevOps staff (development, QA, and Ops staff). Recall that microservices shine when they could help organizations in building cloud-native applications which could be released to cloud frequently with very less lead time.
  * **Design domain-driven APIs**: APIs should be designed keeping the business domain in mind. Also, implementation details should not be made part of API design.
  * **Design cohesive services**: Consider grouping the functions requiring to change together as a single unit rather than separate services. Not doing so would lead to a lot of inter-service communications representing the hard-coupling.
  * **Consider separating services for cross-cutting concerns**: One should consider designing separate services for cross-cutting concerns such as authentication and authorization.
  * **Automate enough for independent deployment**: Nicely designed micro-services should be able to be deployed independently. And, build and release automation would enhance the deployment process thereby leading to quicker releases and shorter overall lead time. This would help build microservices truly cloud-native in nature with microservices wrapped in containers and deployed to any environment including cloud in an easy manner. Good **DevOps** practice followed organization-wide would help achieve this objective.
  * **Failure isolation**: Microservices-based architecture should consider adopting isolation of failure with independent microservices. Architecture principles and design patterns such as some of the following would help achieve the same: 
    * **Circuit-breaker** design pattern
    * Asynchronous communication
    * Loose coupling
    * Event-driven architecture
    * Stateless design
    * Self-contained services
    * Timeouts

## Related Interview Questions

The following are some of the related questions which can be asked in microservices related interviews.

  * How is domain-driven design related to microservices design?
  * How is CQRS design pattern related to microservices?
  * What are some of the best practices related to microservices design and development?
  * Name some design patterns for isolating failures when working with microservices?

## Summary

In this post, you learned about **microservices design best practices**. Did you find this article useful? Do you have any questions or suggestions about this article? Leave a comment and ask your questions and I shall do my best to address your queries.

[Download our white paper:](https://dzone.com/go?i=278431&u=https%3A%2F%2Fgo.sysdig.com%2FSysdig-Architecture%3FUTM_Source%3DContent_Syndication%26UTM_SFDC_Campaign%3D701f1000001cgkm%26UTM_Offer%3Dsysdig-architecture%26UTM_Campaign%3D%26UTM_Medium%3Dtext-link%26UTM_Content%3DDzone-microservices-zone%26UTM_Term%3D%26UTM_Creativeid%3D) The Architecture of the Sysdig Container Intelligence Platform. Built for microservices and containers for monitoring, security, troubleshooting
