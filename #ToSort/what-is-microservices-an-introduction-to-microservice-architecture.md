# What Is Microservices? An Introduction to Microservice Architecture

_Captured: 2018-05-30 at 18:14 from [dzone.com](https://dzone.com/articles/what-is-microservices-an-introduction-to-microserv?edition=376338&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-05-30)_

Containerized Microservices require new monitoring. See why a new APM approach is needed to even [see containerized applications](https://dzone.com/go?i=279427&u=https%3A%2F%2Fwww.instana.com%2Flibrary%2Febook-application-monitoring-in-containerized-world%2F%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dcontainer_apm_ebook%26utm_content%3Deverything_changed).

Have you ever wondered, "What is microservices and how the scaling industries integrate with them while building applications to keep up with their client expectations?"

To get an idea of "**What is Microservices**," you have to understand how a monolithic application is decomposed into small tiny micro applications which are packaged and deployed independently. This blog will clear your understanding of how developers use microservices to scale their applications according to their need.

**In this blog, you will learn about the following: **

  * Features of microservice architecture
  * Advantages of microservice architecture
  * Best practices to design microservices
  * Companies using microservices

Now, before I tell you about microservices, let's see the architecture that prevailed before microservices, i.e. the **monolithic architecture. **In layman's terms, you can say that it's similar to a big container wherein all the software components of an application are assembled together and tightly packaged.

**Listed here are the challenges of monolithic architecture:**

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/02/challenges-of-monolithic-architecture-What-are-microservices-edureka.png)

    * **Inflexible -** Monolithic applications cannot be built using different technologies.
    * **Unreliable -** If even one feature of the system does not work, then the entire system does not work.
    * **Unscalable -** Applications cannot be scaled easily since each time the application needs to be updated, the complete system has to be rebuilt.
    * **Blocks Continuous Development -** Many features of an application cannot be built and deployed at the same time.
    * **Slow Development -** Development in monolithic applications takes a lot of time to be built since each and every feature has to be built one after the other.
    * **Not Fit for Complex Applications - **Features of complex applications have tightly coupled dependencies.

The above challenges were the main reasons that led to the evolution of microservices.

**Microservices**, aka [Microservice Architecture](https://www.edureka.co/blog/microservice-architecture/), is an architectural style that structures an application as a collection of small autonomous services, modeled around a **business domain.**

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/02/microservices-What-Are-Microservices-edureka-2.png)

> _Microservices Representation._

In microservice architecture, each service is **self-contained** and implements a **single business capability.**

Consider an e-commerce application as a use case to understand the difference between both of them.

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/02/Differences-Between-Monolithic-Architecture-And-Microservices-What-Is-Microservices-edureka-3.png)

> _Differences Between Monolithic Architecture and Microservices._

The main difference we observe in the above diagram is that all the features were initially under a single instance sharing a single database, but then, with microservices, each feature was allotted a different microservice, handling their own data, and performing different functionalities.

Now, let us understand more about microservices by looking at its architecture. Refer to the diagram below:

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/02/microservice-architecture-What-Are-Microservices-edureka-1.png)

> _Different clients from different devices try to use different services like search, build, configure, and other management capabilities._

  * All the services are separated based on their domains and functionalities and are further allotted to individual microservices.
  * These microservices have their own **load balancer** and **execution environment** to execute their functionalities, and at the same time, captures data in their own databases.
  * All the microservices communicate with each other through a stateless server which is either **REST** or a **Message Bus**.
  * Microservices know their path of communication with the help of **Service Discovery **and perform operational capabilities such as automation and monitoring.
  * All the functionalities performed by microservices are communicated to clients via an **API Gateway**.
  * All the internal points are connected from the API Gateway so anybody who connects to the API Gateway is automatically connected to the complete system.

Now, let us learn more about microservices by looking at its features.

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/02/Microservices-Features-What-Is-Microservices-edureka.png)

> _Features of Microservices._

  * **Decoupling** \- Services within a system are largely decoupled, so the application as a whole can be easily built, altered, and scaled.
  * **Componentization** \- Microservices are treated as independent components that can be easily replaced and upgraded.
  * **Business Capabilities** \- Microservices are very simple and focus on a single capability.
  * **Autonomy** \- Developers and teams can work independently of each other, thus increasing speed.
  * **Continous Delivery** \- Allows frequent releases of software through systematic automation of software creation, testing, and approval.
  * **Responsibility** \- Microservices do not focus on applications as projects. Instead, they treat applications as products for which they are responsible.
  * **Decentralized Governance** \- The focus is on using the right tool for the right job. That means there is no standardized pattern or any technology pattern. Developers have the freedom to choose the best useful tools to solve their problems.
  * **Agility** \- Microservices support agile development. Any new feature can be quickly developed and discarded again.
![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/02/advantages-of-microservices-What-Are-Microservices-edureka.png)

> _Advantages of microservices._

  * **Independent Development** \- All microservices can be easily developed based on their individual functionality.
  * **Independent Deployment** \- Based on their services, they can be individually deployed in any application.
  * **Fault Isolation** \- Even if one service of the application does not work, the system still continues to function.
  * **Mixed Technology Stack** \- Different languages and technologies can be used to build different services of the same application.
  * **Granular Scaling** \- Individual components can scale as per need, there is no need to scale all components together.

In today's world, complexity has managed to creep into products. Microservice architecture promises to keep teams scaling and function better.

The following are the best practices to design microservices:

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/02/Best-practices-to-design-microservices-What-Are-Microservices-edureka-2.png)

> _Best practices to design microservices._

Now, let us look at a use-case to get a better understanding of microservices.

Let's take a classic use case of a shopping cart application. When you open a shopping cart application, all you see is just a website. But, behind the scenes, the shopping cart application has a service for accepting payments, a service for customer services and so on.

Assume that developers of this application have created it in a monolithic framework. Refer to the diagram below:

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/02/Monolithic-Framework-Usecase-What-Is-Microservices-Edureka.png)

> _Monolithic Framework of a Shopping Cart Application._

So, all the features are put together in a single code base and are under a single underlying database.

Now, let's suppose that there is a new brand coming up in the market and developers want to put all the details of the upcoming brand in this application. Then, they not only have to rework the service for new labels, but they also have to reframe the complete system and deploy it accordingly.

To avoid such challenges developers of this application decided to shift their application from a monolithic architecture to microservices. Refer to the diagram below to understand the microservices architecture of shopping cart application:

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/02/Microservices-Framework-Usecase-What-Is-Microservices-Edureka.png)

> _Microservice Architecture of a Shopping Cart Application._

This means that developers don't create a web microservice, a logic microservice, or a database microservice. Instead, they create separate microservices for search, recommendations, customer services and so on.

This type of architecture for the application not only helps the developers to overcome all the challenges faced with the previous architecture but also helps the shopping cart application to be built, deployed, and scale up easily.

## **Companies Using Microservices**

There is a long list of companies using microservices to build applications, these are just to name a few:

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/02/companies-using-microservices-What-Are-Microservices-edureka.png)

[Automatically manage containers and microservices](https://dzone.com/go?i=290421&u=https%3A%2F%2Fwww.instana.com%2Ftrial%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dinstana_trial%26utm_content%3Dgot_cloud_get_instana) with better control and performance using [Instana APM](https://dzone.com/go?i=290421&u=https%3A%2F%2Fwww.instana.com%2Ftrial%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dinstana_trial%26utm_content%3Dgot_cloud_get_instana). Try it for yourself [today](https://dzone.com/go?i=290421&u=https%3A%2F%2Fwww.instana.com%2Ftrial%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dinstana_trial%26utm_content%3Dgot_cloud_get_instana).
