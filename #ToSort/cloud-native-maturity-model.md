# Cloud-Native Maturity Model

_Captured: 2018-08-07 at 19:12 from [dzone.com](https://dzone.com/articles/a-maturity-model-for-cloud-native-software-develop?edition=385338&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-08-07)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

## Introduction

Running applications on the cloud is not a binary decision. You don't just move to the cloud and call it a day. The journey to cloud-native starts with establishing business decisions that mandate that applications in your organization need to deploy faster, scale easier, and break less frequently.

Throughout the cloud journey, companies can find themselves in one of several stages, progressing further into a cloud-native environment. I've highlighted these stages below, including the major benefits of each.

## The Cloud-Native Maturity Model

![](https://cdn.mojotech.com/2018/1/28/cloud-native-infographic.jpg)

## Stage 0: On-Premise

![](https://cdn.mojotech.com/2017/11/5/on-premise_cloud_native.jpg)

Throughout the years, companies have housed their applications internally or in off-site co-locations. Before high-speed internet and fiber connections were readily available and affordable, software accessibility outside a company's local network proved troublesome.

Now, with service providers offering bandwidth that meets or exceeds internal networks, organizations can leverage cloud platforms like Amazon, Google, Pivotal, and Microsoft to run their data-centers more efficiently.

## Stage 1: Cloud-Enabled

![](https://cdn.mojotech.com/2017/11/5/01_cloud-enabled.jpg)

Cloud-Enabled Applications are the simplistic form of cloud-based applications. They are applications that were built with requirements to run on a specific operating system, within a particular environment. These applications moved to the cloud as the first step in this journey which allows them to integrate with basic cloud features.

Imagine if you dug up your house, put it on a giant flatbed truck, and moved it to the beach. You would get the benefits of being beachside, but your bedrooms, bathrooms, and kitchen would be the same. It's a comparable concept with a Cloud-Enabled App. It can take advantage of certain amenities of the cloud, while still being an application that is built for an on-premise environment.

**Some of the highlights of a cloud-enabled application include:**

### Density

![](https://cdn.mojotech.com/2017/11/5/01_cloud-enabled_density.jpg)

While leveraging a Cloud-Enabled environment, each application no longer requires its own set of hardware. Cloud platforms allow applications to be built on different stacks while living on the same set of underlying hardware.

### Cost Reduction

![](https://cdn.mojotech.com/2017/11/5/01_cloud-enabled_cost.jpg)

Once applications migrate to the cloud, businesses can reduce their capital expenses. The need for expensive hardware, local support, and building and maintenance costs shrink.

## Stage 2: Cloud-Optimized

![](https://cdn.mojotech.com/2017/11/5/02_cloud-optimized.jpg)

Cloud-Optimized Applications take Cloud Applications one step further, optimizing them for access to more cloud features without having to be re-developed as cloud-native applications. The applications are best described as a hybrid between applications that were moved to the cloud and applications that were built for the cloud.

Most organizations live in a Cloud-Optimized environment. They take advantage of additional benefits and stop there. While it surely a step in the right direction, organizations need to look deeper into their business needs to understand if and how fully cloud-native applications can further reduce cost and increase performance.

**Some of the highlights of a Cloud-Optimized Application include:**

### Continuous Delivery

![](https://cdn.mojotech.com/2017/11/5/02_Cloud-Optimization_ContinuousDelivery.jpg)

Applications can easily be replicated to create a more efficient deployment workflow. While code can be updated through a code repository, the environment and configuration can just as easily be re-created by just cloning existing applications, and publishing them as needed.

From here, developers can use their individual workstations to write code, push to staging/development servers, and then ultimately have the code from development pushed to production.

### Scaling

![](https://cdn.mojotech.com/2017/11/5/02_cloud-optimized_scaling.jpg)

The ability to easily scale is one of the main reasons the Cloud stands out as a preferred platform. Scaling in cloud-based applications usually takes place in one of two formats. They either scale up vertically or out horizontally.

Applications that require more power such as compute or memory resources will scale up, while applications requiring additional servers to handle load will scale out.

### Redundancy

![](https://cdn.mojotech.com/2017/11/5/02_cloud-optimized_redundancy-2.jpg)

Virtual Load Balancers make a great and easy way to create redundant access to your applications. At this stage, applications are usually separated from key web and database services, allowing redundancy to be introduced independently.

## Stage 3: Cloud-Native

![](https://cdn.mojotech.com/2017/11/5/03_cloud-native.jpg)

Cloud-native Applications are the end goal for modern software development. These applications are built from the ground up to incorporate best practices for efficiency, delivery, and availability. Utilizing features of the cloud allow these applications to operate consistently across devices, platforms, and providers.

**Some of the highlights of a cloud-native application are:**

### Microservices

![](https://cdn.mojotech.com/2017/11/5/03_cloud-native_microservices.jpg)

Microservices in cloud-native Applications are services separated out to address a specific task. Since these services are loosely coupled with the underlying application, they can be updated or repaired without impacting other services.

This distinction allows microservices to be deployed and maintained more efficiently than traditional applications.

### Containerization

![](https://cdn.mojotech.com/2017/11/5/03_cloud-native_containerization.jpg)

Just as virtual machines allow multiple operating systems to live on one machine, containers allow multiple apps to live on one virtual machine.

With containerization, applications are bundled with dependencies like libraries, configuration files, and binaries to expedite the process of deploying new applications and deploying updates to existing ones.

### Orchestration

![](https://cdn.mojotech.com/2017/11/5/03_cloud-native_orchestration.jpg)

Orchestration was introduced to the software development process to streamline the process of manually provisioning and configuring applications.

With DevOps time being constrained by setting up new web servers, databases, and load balancers, orchestration creates efficiency by automating DevOps processes.

### Fault Tolerance

![](https://cdn.mojotech.com/2017/11/5/03_cloud-native_faulttolerance.jpg)

Cloud-native Applications reduce the risk for single points of failure. Unexplained performance issue? Applications can automatically relocate to different compute and memory resources.

Worried about disk failure? Cloud providers can hot swap out startup disks in the event of a failure. All of these safety features increase business continuity while decreasing the need for IT staff to intervene.

## Conclusion

So there you have it. The goal is not to focus on moving to the cloud, but to understand the pillars of the cloud, and see what makes the most sense for your business. Getting to the cloud is just the first step in the journey. When businesses consider the development of new applications, it's critical to not only understand the cloud maturity model but to ensure applications are being built as cloud-native.

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)
