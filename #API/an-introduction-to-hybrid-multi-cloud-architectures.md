# An Introduction to Hybrid Multi-Cloud Architectures

_Captured: 2017-12-12 at 16:53 from [dzone.com](https://dzone.com/articles/an-introduction-to-hybrid-multi-cloud-architecture?edition=342132&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202017-12-12)_

Are you joining the containers revolution? Start leveraging container management using Platform9's [ultimate guide to Kubernetes deployment](https://dzone.com/go?i=243221&u=https%3A%2F%2Fget.platform9.com%2Fjzlp-kubernetes-deployment-models-the-ultimate-guide%2F).

When organizations decide to shift their workloads, data and processes across multiple on-premises, hosted, private, and public cloud services, there will be a need for a new approach. This new approach leads to hybrid multi-cloud cloud management. But this approach requires uniform solutions in terms of billing and provisioning, access control, cost control, and performance analysis and capacity management.

A hybrid multi-cloud architecture is emerging within nearly all enterprises. IT organizations are no longer limited to managing data-centers and a few hosted and managed services providers. Needy lines-of-business teams and impatient IT developers have procured SaaS, IaaS, and PaaS cloud services to overcome resource constraints. Now many enterprises' IT structures are composed of multi-clouds.

In the IT industry, the tools and technologies needed to craft and manage hybrid multi-clouds architecture are fragmented. Multi-clouds and hybrid clouds bring workload and infrastructure challenges that will drive the development of new cloud management technology. In addition to having to manage resource utilization, performance and costs of various public and private cloud services, cloud management platforms must also be aware of the integrations and processes that transcend on-premises and cloud execution venues, and interoperate (in some way) with the new multi-purpose hybrid iPaaS that connects them, to assure business continuity.

Organizations plan to migrate their on-premise systems to hybrid multi-cloud when they need a solution for the following challenges and requirements:

  * Users are widely distributed geographically where they are surrounded by multiple data centers instead of a single data center.

  * Facing regulations limit in particular countries for storing data, e.g., EU.

  * An environment where public clouds are used with on-premises resources.

  * A cloud-based application is not resilient, which can affect disaster recovery when loss of a single data center.

According to the above challenges, I've introduced two hybrid multi-cloud architectures for migrating on-premise environment to a hybrid multi-cloud environment. There are many [multi-cloud architectures](https://www.simform.com/multi-cloud-architecture/), namely re-deployment, cloudification, relocation, refactoring, rebinding, replacement, and modernization for organizations to for adopt multi-cloud environments.

## 1\. Multi-Application Rebinding

![Image title](https://dzone.com/storage/temp/7276348-mcr.png)

In the above hybrid multi-cloud architecture, a re-architected application is deployed partially on multiple cloud environments.

This architecture can be used for the systems that route users to the nearest data center when the primary or on-premise data center fails. In particular, they can be configured to monitor the status of the service to which they are directing the users. If any service is not available, all the traffic will be routed to another healthy instance.

This architecture uses an on-premise cloud adapter (e.g., service bus or elastic load balancer) to provide an integration of components in different cloud platforms.

Let's understand with an example.

Here, AC1 and AC2 are two application components hosted on-premise before migration. As both the components are independent integrity units, AC1 remains on-premise while two AC2s are deployed on AWS and Azure for disaster recovery. AC1 and two AC2 components are connected via EBS or service bus.

The main benefits of using this architecture are the application's response rate increases to the maximum level and unhealthy services become healthy again.

## 2\. Multi-Application Modernization

![Image title](https://dzone.com/storage/temp/7276364-mcm.png)

In this architecture, on-premise applications are re-architected as a portfolio and deployed on the cloud environment.

In the above example, A1, A2, and one application component, AC1, are re-architected as a portfolio and deployed on different cloud providers and on-premise. AC1 is deployed on AWS and A2 is deployed on Azure while A1 is kept on-premise.

This architecture overcomes the problem where re-architecting an on-premise application does not remove duplicated functionality and inconsistencies.

Multi-Application Modernization analyzes an application as a portfolio to identify opportunities for consolidation and sharing. The separation of workloads enables the identification of components that are shared by more than one solution.

This architecture provides a consistent performance and reduces operational tasks and maintenance costs for shared components.

## Conclusion

The introduction of hybrid multi-cloud architectures complements existing migration practices and allows for an engineering approach towards constructing and evaluating the migration plan.

Multi-cloud architectures provide an environment where businesses can build secure and powerful cloud environments outside the traditional infrastructure. Maximizing the impact of multi-cloud, however, means tackling the challenges of app sprawl, unique portals, compliance, migration, and security head-on.

Using Containers? Read our [Kubernetes Comparison eBook](https://dzone.com/go?i=243223&u=https%3A%2F%2Fget.platform9.com%2Fjzlp-kubernetes-comparison-ebook%2F) to learn the positives and negatives of Kubernetes, Mesos, Docker Swarm and EC2 Container Services.
