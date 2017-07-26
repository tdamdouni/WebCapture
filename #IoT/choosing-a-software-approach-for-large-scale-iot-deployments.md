# Choosing a Software Approach for Large-Scale IoT Deployments

_Captured: 2017-03-11 at 01:45 from [dzone.com](https://dzone.com/articles/choosing-a-software-approach-for-large-scale-iot-deployments?oid=twitter&utm_content=bufferad51c&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The Internet of Things is still in its infancy. IoT solutions are presently architected, designed, and implemented with a focus limited to a vertical use case only. But over the next several years, as IoT begins to mature, the various IoT solutions will need to interact not only with each other but also with enterprise systems.

For example, smart thermostat data and smart meter data will need to be combined with smart grid data and customer data to allow utility companies to dynamically optimize power generation and distribution.The APIs for combined data will be available to a broad set of partners that can provide added services.

Although IoT deployments on massive scale remain a few years away, the design and tool decisions made now will have a direct impact on future capabilities. Consider a solution that works well with a limited set of sensors streaming data to a public cloud, but now needs to integrate with the company's existing IT infrastructure, applications, supplier systems, and business processes. And the data stream now includes data from sensors, mobile devices, weather, social media, and other sources. After all, the real value of IoT lies in combining the IoT-generated data with other data to derive greater value than each data set can deliver on its own.

![Image title](https://dzone.com/storage/temp/4413539-rtinsights-blog.jpg)

Using monolithic IoT solutions that use custom tooling without integrating with the rest of the IT infrastructure, processes, and resource pool is a recipe for major pain down the road when IoT deployments reach critical mass.

## **Best Practices for IoT Project Development**

IoT solutions have to be architected with a broader context right at the beginning. The best practices learned from enterprise IT and cloud deployments could solve these challenges for IoT without the need to reinvent the wheel. Using current development methodologies for IoT will also ensure the optimal use of existing resources and processes.

Let's look at two examples of how these best practices can help with an IoT deployed at scale.

## **Application Management**

Compared to traditional embedded systems, the key advantages of IoT projects include modern apps and a general plug-and-play ecosystem. These new IoT applications will make use of data from the multiple sources and interact through standard APIs.

When thinking of these IoT apps, most of the discussion is around programming languages, packaging format, and update mechanisms. These are important concerns, but one needs to look beyond the basics and think about how these apps will be developed, installed, and configured, shared across various teams (dev, architecture, security, operations) and deployed quickly at scale. These apps would also need to be deployed across various tiers (cloud, local datacenter, gateways, end devices). (**See**: "[Why Gateways and Controllers Are Critical to IoT Architecture](https://www.rtinsights.com/why-gateways-and-controllers-are-critical-for-iot-architecture/).").

In this regard, IoT apps are similar to other enterprise apps, so one could consider using existing application management platforms to manage IoT apps. For traditional enterprise multi-platform applications, this could mean [JBOSS WildFly Application Server](http://wildfly.org/), [Drools business rules engine,](https://www.drools.org/) and other tools.

For mobile applications across Android and iOS platforms, [FeedHenry](http://feedhenry.org/) is a popular choice among enterprises. In case of containerized applications, one may want to look at [OpenShift Origin ](https://www.openshift.org/)which is gaining popularity across many industries, with customers like KeyBank, Amadeus, Cisco, FICO etc.

## **Container Deployment Automation**

Container adoption by DevOps teams is accelerating in the enterprise and cloud. Containers solve the complexity of application installation and integration. Using the standardized container format methodology (aka docker) allows applications to be easily shared and deployed. IoT could also gain the same benefits from container adoption along with enhanced security capabilities. There are several container-based operating system offerings (e.g. [Red Hat Atomic Host](https://access.redhat.com/documentation/en/red-hat-enterprise-linux-atomic-host/7/single/installation-and-configuration-guide/), [Ubuntu Core](https://www.ubuntu.com/core), [Resin.io](https://resin.io/)) that can be used for IoT. When deployed to scale (millions of instances of containers deployed across various classes of systems across the globe), one needs to look beyond container basics. These production-class systems present unique problems for developers, sys admins, and ops.

For a large-scale container deployment, you will need to worry about the following:

  * **Scheduling:** Where should the various containers run?
  * **Lifecycle and health**: Keep the various containers running despite failures.
  * **Discovery:** Where are the containers now?
  * **Monitoring**: What's the status of various containers?
  * **Auth(n,z)**: Control who can do what to various containers.
  * **Aggregates**: Compose sets of containers into jobs.
  * **Scaling**: Make jobs bigger or smaller.

Automation is a must have for production-class deployments. A tool like [Kubernetes](https://kubernetes.io/) (widely used for container deployment automation) could also be applied to IoT use cases. Kubernetes automates deployment, operation, and scaling of containerized applications across multiple hosts. It provides Scheduling, Lifecycle and health, Discovery, Monitoring, Authorization, (Auto)Scaling, and Self-healing. Once again, standardized tooling that's already in use in enterprise IT/cloud could be used to handle IoT workloads as they reach the massive scale.

## **Conclusion**

Instead of adopting monolithic IoT solutions, companies should be looking at how to leverage their existing tools to manage IoT deployments. For example, consider using tooling used to manage, provision, and configure your enterprise systems (e.g. [SpaceWalk](http://spacewalk.redhat.com/)[)](https://access.redhat.com/products/red-hat-satellite) for IoT systems as well. This approach provides a consistent approach for managing all the systems, including IoT systems.

Also, IoT can benefit from IT best practices on how to deliver standards-based solutions that can be securely deployed at scale. For example, when a container-based approach is chosen for IoT systems, consider how they are being used for the rest of the enterprise. If your company is using industry standard container formats (e.g. docker) for enterprise apps then you should consider using this for IoT apps as well (rather than a custom format like [Ubuntu Snap](https://www.ubuntu.com/desktop/snappy)). In addition, you should also consider how these containers can be deployed to scale (millions of containers deployed across various systems around the globe). Once again, take a look at what container deployment automation tools (e.g. Kubernetes) are being used by your company so you can use these for production-class IoT deployments as well.

Treating IoT as a silo, and not using the same tools that are being used by existing systems, risks splitting resources, management focus, and budgets among competing priorities. Using standardized tools across the various use cases (including IoT) will spare you potential problems ahead.

### Like This Article? Read More From DZone

Opinions expressed by DZone contributors are their own.
