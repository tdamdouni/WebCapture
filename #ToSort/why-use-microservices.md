# Why Use Microservices?

_Captured: 2018-08-24 at 08:12 from [dzone.com](https://dzone.com/articles/why-microservices?edition=387225&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-23)_

Containerized Microservices require new monitoring. See why a new APM approach is needed to even [see containerized applications](https://dzone.com/go?i=279427&u=https%3A%2F%2Fwww.instana.com%2Flibrary%2Febook-application-monitoring-in-containerized-world%2F%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dcontainer_apm_ebook%26utm_content%3Deverything_changed).

Microservices are very trendy these days. Almost everybody is into it. It is not just Netflix, Amazon, or Google -- it appears that almost everyone has adopted this architecture style. Although microservices have been here for quite some time now and a lot has already been written about them, I thought of writing yet another piece today, so please bear with me.

To understand the need for microservices, we need to understand problems with our typical 3-tier monolithic architecture.

## **What Is Monolithic Architecture?**

Monolithic means composed all in one piece. A monolithic application is one which is self-contained. All components of the application must be present in order for the code to work.

Take the case of a typical 3-tier traditional web application built in three parts: a user interface, a database, and a server-side application. This server-side application is called a monolith, which is further divided into 3 layers -- presentation, business layer, and data layer. The entire code is maintained in the same codebase. In order for the code to work, it is deployed as a single unit. Any small change requires the entire application to be built and deployed.

![A Typical Monolithic Application](https://dzone.com/storage/temp/10016993-monolithic.jpg)

> _A typical monolithic application._

## **What Is Microservices Architecture?**

Microservices architecture is an architectural style where the entire application is divided and designed as loosely-coupled, independent services modeled around a business domain. The "micro" in microservices is very deceiving. It has been debated a lot, but in my humble opinion, it does not dictate how small or big a service has to be. Again, this is another discussion we should have another day. Let's move forward.

The important point at this stage is that each independent service has a business boundary which can be independently developed, tested, deployed, monitored, and scaled. These can be even developed in different programming languages.

![Image title](https://dzone.com/storage/temp/10017015-microservices.jpg)

> _A typical microservices application._

In microservices-based architecture, each component or service has its own database. There is no centralized database, as in the case of a monolith. You can even use NoSQL, RDBMS, or any other database as needed for each of the individual microservices. This makes microservices truly independent.

Let's now see what concerns microservices address.

## **Concerns With the Monolith**

### ** Difficult to Scale**

These applications can only be horizontally scaled by having multiple instances of entire application behind a load balancer. If a specific service within the application requires scaling, there is no simple option. You need to scale the application in its entirety, which is an unnecessary waste of resources.

In contrast, a microservices-based application allows you to scale individual services independently as per your requirements. In the above diagram, if service B needs to be scaled, you can have maybe 10 instances of it while keeping the others as is. This can be changed on the fly, as needed.

### Long Time to Ship

The entire codebase is deployed rather than just the impacted code. Any change made in any portion/layer of a monolithic application requires building and deploying the entire application. The individual developer is also required to download the entire application code and not just his/her impacted module for fixing and testing. This also impacts continuous deployments.

On the other hand, in microservices architecture, if a change is only needed in one of the hundred microservices, only the changed microservice is built and deployed. There is no need to deploy everything. In fact, a microservice can even be deployed several times during the day, if needed.

### Complexities of Growing Applications

As a monolithic application grows (features, functionality, etc) so does the team, and soon, the application becomes complex and intertwined. As different teams keep modifying the code, it slowly becomes more and more difficult to maintain a modular structure and slowly results in spaghetti code. This not only impacts code quality, but also impacts the organization as a whole.

In a microservices-based application, each team works on separate microservices, which makes it less difficult to make intertwined code.

### No Clear Ownership

In monolithic applications, teams that look independent are not actually independent. They simultaneously work on the same codebase but are heavily dependent on each other.

In microservices-based applications, the independent teams work on separate microservices. A team will own an entire microservice. There is clear ownership of work with clear control of everything about the service, including development, deployment, and monitoring.

### Failure Cascade

The failure of one part of a monolithic application can cascade and result in bringing down the entire system, if not properly designed.

In the case of microservices-based architecture, we can make use of a circuit breaker to avoid such failures.

### Wall Between Dev and Ops

Dev teams normally do the development, test, and once deployed simply toss the ownership of maintenance and support to the operations team. The dev team is disbanded and the ops team takes ownership and struggles to support the monolithic application in production.

In microservices-based applications, teams are organized with the understanding that "you build it, you run it." The dev team continues to own the application in production.

### Stuck in a Technology/Language

With a monolith, one gets locked into the implemented technology/language. The entire application must be rewritten if a technology/language change is needed.

With microservices, each service can be implemented in a different technology or language as per the requirements and the business. Any decision to change the technology/language of a service will only require rewriting of that particular service since all microservices are independent of each other.

### Availability of the Right Tools/Technologies to Support Microservices

A few years back, the appropriate tools and technologies were not available to support microservices. Ever since Docker containers and Cloud Infra (especially PaaS) became available to the masses, microservices are being adopted at such a large scale due to the freedom these provide without going through the traditional provisioning procedures.

## Conclusion

We have talked in detail about both monolithic and microservices architecture styles. We also discussed the various key problems of monolithic applications and how microservices come forward to solve them in the new world. In a nutshell, choose microservices architecture for the following benefits:

  * Independently develop and deploy services
  * Speed and agility
  * Better code quality
  * Code created/organized around business functionality
  * Increased productivity
  * Easier to scale
  * Freedom (in a way) to choose the implementation technology/language

Even with all the benefits offered by microservices architecture, it is not a silver bullet. It has complexities of its own. Think of multiple instances of hundreds of services in a big project. How will you monitor these? In case of any service failures, how will an error be tracked, traced, and debugged?

All these are overheads which need to be addressed for an efficient application.

[Automatically manage containers and microservices](https://dzone.com/go?i=290421&u=https%3A%2F%2Fwww.instana.com%2Ftrial%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dinstana_trial%26utm_content%3Dgot_cloud_get_instana) with better control and performance using [Instana APM](https://dzone.com/go?i=290421&u=https%3A%2F%2Fwww.instana.com%2Ftrial%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dinstana_trial%26utm_content%3Dgot_cloud_get_instana). Try it for yourself [today](https://dzone.com/go?i=290421&u=https%3A%2F%2Fwww.instana.com%2Ftrial%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dinstana_trial%26utm_content%3Dgot_cloud_get_instana).
