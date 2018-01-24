# DDD: Part IV (DDD and Microservices)

_Captured: 2018-01-12 at 19:53 from [dzone.com](https://dzone.com/articles/ddd-part-iv-ddd-amp-microservices?edition=352108&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-01-12)_

**Best practices for [getting to continuous deployment](https://dzone.com/go?i=268427&u=https%3A%2F%2Finfo.rainforestqa.com%2Febook-getting-to-continuous-deployment%3Futm_campaign%3Dgetting-to-continuous-deployment%26utm_medium%3Ddisplay%26utm_source%3Ddzone) faster and with dramatic results in reduced outage minutes, development costs, and QA testing cycles. Brought to you by [Rainforest QA](https://dzone.com/go?i=268427&u=https%3A%2F%2Fwww.rainforestqa.com%3Futm_campaign%3Dhome-page%26utm_medium%3Ddisplay%26utm_source%3Ddzone).**

Finally, I got a chance to write the fourth part! For those of you who didn't get the chance to read the previous parts, you can read them starting with Part 1 [here](https://dzone.com/articles/ddd-part-i-introduction).

In this fourth part, I will try to elaborate on the **microservices architecture** and its relationship with **Domain Driven Design** (DDD).

## **Microservices Architecture**

First things first: let's describe what **microservices architecture** is all about.

**Microservices architecture** is a kind of an architectural pattern that focuses on developing/building small, reusable, and scalable services. Microservices allow us to break our large system into a number of independent collaborating processes, thus it can help to avoid a big monolith application, which is difficult to maintain, especially if you have big projects with a big team.

Microservices also can be very useful when you have to create services for polyglot devices such as wearables, Internet of Things (IoT), mobile, desktop, and web.

Microservices itself is not a new term. It was coined in 2005 by Dr. Peter Rodgers, who mentioned micro web services based on SOAP. It has become more popular since 2010.

The keys to **microservices architecture** are:

  1. It is independently deployable in terms of stack, framework, and/or languages used.
  2. It is deployed as a small service that keeps focusing on doing one thing well, i.e. domain-driven services.
  3. Well-defined interfaces and minimal functionality.
  4. Avoiding cascading failures and synchronous calls -- reactive designing for failure.
  5. Every service has its own data and uses events/messages to communicate with other services. 
  6. Every service is deployed independently and isolated from other services (usually running in its own container) and automatically scalable.

The main goal is to provide you with a small set of independent services which run independently in different environments, but can communicate with each other (_tight cohesion_). As we know, coupling is a two-headed beast. On one side, tightly-coupled code is difficult to test, difficult to maintain/reuse, and typically exhibits "whack-a-mole" bug behavior (i.e. fixing one bug most likely will produce one or more new bugs). On the other side, a certain amount of coupling is also necessary since completely uncoupled code doesn't do anything; thus, coupling is necessary but should be carefully managed. This is what we call "Loosely Coupled, Highly/Tightly Cohesive."

## **Microservices Benefits**

  1. Easy to scale as individual components.
  2. Easy to deploy and reduce time deployment, i.e. you can deploy each module without interrupting any other module.
  3. Easy to maintain due to its smaller code size, and you can have a small, focused team. 

## **Microservices Challenges**

  1. It's difficult to achieve strong consistency in distributed services.
  2. It's harder to debug and trace issues compared to monolithic applications.

There are many other challenges that you will know yourself later, once you implement **microservices**. Nevertheless, it will depend on how you design and manage your **microservices** by following some _well-known_ best practices, like API Management, Traffic Management, Services Monitoring, etc. I'll try to encapsulate them later in another series, if I get the chance.

## **How Does DDD Relate to Microservices?**

As mentioned earlier, in **microservices**, we build each service to serve only one thing and do one thing well. Each service is also isolated from the others. On this matter, DDD principles can help us to keep the scope of the service small through what it calls "bounded context."

Subsequently, DDD is going to help you investigate and know your _domain_ and all _subdomains_ well through the communication you build with the _domain experts_. By knowing your _domain _and_ subdomains_ well, you will know the _map contexts_ and how all _subdomains_ interact with each other, which will help you in designing and choosing the type of your **microservices architecture** and what kind of approaches you use to implement them, whether a _reactive approach_, _orchestration approach_, or _hybrid_... it will depend on your knowledge about the _domain_ you're working on. There are _pros_ and _cons_ for each approach that need to be evaluated based on the project and your domain knowledge. DDD will help you make a decision on this matter.

That's all for now... please let me know if you have any more insight into how DDD relates to **microservices**!

**Discover how to [optimize your DevOps workflows](https://dzone.com/go?i=268430&u=https%3A%2F%2Finfo.rainforestqa.com%2Febook-getting-to-continuous-deployment%3Futm_campaign%3Dgetting-to-continuous-deployment%26utm_medium%3Ddisplay%26utm_source%3Ddzone) with our on-demand QA solution, brought to you in partnership with [Rainforest QA](https://dzone.com/go?i=268430&u=https%3A%2F%2Fwww.rainforestqa.com%3Futm_campaign%3Dhome-page%26utm_medium%3Ddisplay%26utm_source%3Ddzone). **

Opinions expressed by DZone contributors are their own.
