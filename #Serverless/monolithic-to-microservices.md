# Monolithic to Microservices

_Captured: 2018-09-05 at 22:25 from [dzone.com](https://dzone.com/articles/monolithic-to-microservices?edition=393195&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-09-05)_

The new [Gartner Critical Capabilities report](https://dzone.com/go?i=299477&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921) explains how APIs and microservices enable digital leaders to deliver better B2B, open banking and mobile projects.

## What Are Monolithic Applications?

This kind of application is not responsible for a single task, but they need several tasks to complete a particular responsibility. In monolithic applications, all the services are bundled into one package and run as one process. The user interface, data access layer, and data store layers are tightly coupled in monolithic applications. Usually, large teams work with monolithic applications, and they are not suitable for container-based deployments.

**![Monolithic application architecture](https://lh5.googleusercontent.com/3QijRumY_34PAnvr0r_wZitVMgj1FX8RXMPK2mJCD0SYwt-F-hRUmVG3Sr0mo-jEZaGfr_XBJKqvB9Ja89lFPOaCiho0iV5QPKjWFf0Y3B-EDoTejgoGXB3QkUnWtQN2wiesSitx)**

> _Monolithic application architecture_

**Pros:**

  * Monolithic applications are very simple to develop because of all the tools and IDEs support to that kind of application by default.
  * Very easy to deploy because all components are packed into one bundle.
  * Easy to scale the whole application.

**Cons:**

  * Very difficult to understand and create the patches for monolithic applications.
  * Adapting to new technology is very challengeable.
  * Very difficult to maintain CI/CD pipeline.
  * Maintainability is very high and braking of one code line will stop the whole process.
  * Take a long time to startup because all the components need to get started.
  * One component failure will cause the whole system to fail.

## What Are the Microservices?

There is no proper definition for the microservices. We can define the microservices as a bunch of loosely coupled components working together to perform tasks. These light weighted components can be developed through various languages (Java, PHP, Python) and can use various protocols (Http/Https/JMS) to communicate between two components. Most of the microservices expose their services through the REST APIs so that other services can call those services very easier. Microservices follow the decentralized architecture.

**![Microservice application architecture](https://lh5.googleusercontent.com/kAWKAdbFfUkOXCqQaAJQoNRaPCOWE_xEn6N0aNq7eIZWglCqX_OExAMbHajwdpmFx-vLgrGd6sKYFDpRgiJQY6rQDBMrKjUuHxhHoqETzmwQql56iZE-cJbQy76909tHNmg7wpoD)**

> _Microservice application architecture_

**Pros: **

  * Can use the latest technologies to develop the microservices.
  * Composability is very high.
  * Can scale independent microservices separately. No need to scale the whole the system.
  * One component failure will not cause entire system downtimes.
  * When developing an overall solution we can parallel the microservices development task with the small teams. So it helps to decrease the development time.
  * CI/CD is very easy.

**Cons:**

  * Independent code base maintenance is very difficult.
  * Monitoring the overall system is very challenging because of decentralization. Communication needs to be very strong to communicate with independent modules.
  * Has additional performance overhead because of network latency.

## Why Do You Need to Move?

Nowadays most of the enterprise applications move into the microservice based architecture to get the maximum business value. Most people are looking for new technologies and also are looking to move out of legacy systems. People tend to use integration rather than developing whole applications like monolithic. "People like to live in green fields, not in brown fields."

## Key Points to Be Considered for the Transition

  * Identify the components which are capable of running independently.
  * What are the technologies you use to develop the microservices?
  * Need to think about the independent service code maintainability.
  * Need to consider the infrastructure and the how you are going to load balance between each component because these services are independently deployed.
  * Need to consider how many teams are going to develop the servers and number of members in one team. (Team size = two pizza)

## Strategies

### Ice Cream Scoop Strategy

**![](https://lh3.googleusercontent.com/XJrwYv1hj2uP0wgczwFJaxGR-pckZOcRet0lJQ2IDeiiR8iJu6n8xXinc59syliYFf2LRV34wEMwomsztJLsziTZOE7D-bJ3XdDnErZSkW-y-L9GxItT182famm3Tycix6-JNIfT)**

Using this kind of strategy organization can gradually move monolithic architecture to the microservices architecture. This strategy mainly focuses on the system uptime, user experiences and can run both systems in parallel. Get one component form the monolithic application and develop it as a microservice then put it into production. Likewise scooping out all components and smoothly migrate to microservices. This strategy reduces the migration risk with the transition. Using this kind of strategy will take longer to migrate whole the system into microservice architecture.

### Lego Strategy

**![](https://lh6.googleusercontent.com/_tHp219iPwgtNN_7ERzA3-68ebVnn3H3XGFmwp4WOwDhE3yp7fFAzJ5hzZKvLNs-NTllCelmRTUbvFv-ODP_G-u-ap3YJyxXINcBQtqcF7nzlEt7PAPpIlQxKEnLuJBMhd9Jxxeq)**

In this strategy, organizations are not going to completely remove the monolithic application. What architects do is to develop new features as microservices and keep the existing monolithic application as it is. This kind of architecture is called hybrid architecture. Disadvantages of this strategy are that it is required to maintain the legacy system as well as the microservices and system integration is very hard. The plus point of this strategy is that it can reduce the workload and features can be developed within short time periods.

### Nuclear Bomb Strategy

**![](https://lh6.googleusercontent.com/ddB0De8LbJWbnQGc6GL1yRlJflRQNyS3wz5yEnQyMMpUC-H7HEfqPE55skpg-rRd1yyX_vpah7jelXVqV5VKCHW_SfBGPUMSSDQfQOs8xrGEI_74FiFNurXhaFtcmyJ3Uf7b_XzZ)**

The entire monolithic application is written using the microservices form the scratch. The main advantage of this strategy is that the organization can overcome all the bugs in the monolithic application, can choose whatever technology for the new building microservices and also can engage new features than the monolithic application. For this strategy, the organization needs to put more effort and more investments.

The new [Gartner Critical Capabilities for Full Lifecycle API Management report ](https://dzone.com/go?i=299478&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921) shows how CA Technologies helps digital leaders with their B2B, open banking, and mobile initiatives. [Get your copy from CA Technologies.](https://dzone.com/go?i=299478&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921)
