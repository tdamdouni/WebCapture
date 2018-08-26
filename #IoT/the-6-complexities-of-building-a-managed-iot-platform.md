# The 6 Complexities of Building a Managed IoT Platform

_Captured: 2018-03-13 at 16:27 from [dzone.com](https://dzone.com/articles/the-6-complexities-of-hosting-a-managed-iotnbspser?edition=366236&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-03-13)_

The IoT (Internet of Things) industry is in an era of rapid proliferation, with[ industry experts](http://www.gartner.com/newsroom/id/3598917) projecting the number of connected devices to grow from 8 billion (2017) to 20 billion (2020). As more and more companies are looking to enter the IoT arena, they are facing unparalleled challenges when building and deploying IoT projects.

According to a [Cisco survey (2017)](https://www.slideshare.net/CiscoBusinessInsights/journey-to-iot-value-76163389), over 60% of respondents admitted that they substantially underestimated the complexities of managing their own IoT initiatives. Even more alarming, the same survey also found that 75% of self-initiated IoT projects were considered a failure.

![](https://cdn-images-1.medium.com/max/800/0*KFDg5EOLcYCvfAJ_.)

What makes these IoT initiatives so complex? Well, when it comes to managing your own IoT service, you are basically constructing a software and hardware ecosystem that is exponentially more complex than a standard web application. This ecosystem demands the expertise of multiple engineering disciplines: computer, electrical, hardware, network, DevOps… and the list goes on.

In order to launch a successful IoT system, you must first understand the inherent complexities of designing, building, and maintaining such a system -- and decide whether it is better to build a custom platform or purchase a managed IoT solution.

## **What Is a Managed IoT Platform?**

Fundamentally, it is a fully integrated service that offers everything you need to connect and deploy an IoT device. It needs to be capable of supporting millions of simultaneous device connections and easily allow consumers to configure their devices for machine-to-machine communication. This means a managed IoT service has to establish bidirectional communication protocols through real-time event streams (like a [pub/sub](https://realtimeapi.io/hub/publishsubscribe-pattern/) messaging pattern).

![](https://cdn-images-1.medium.com/max/800/0*-Ul6riLJ6NCtrGj_.)

Although, many companies often overlook the complexities of remotely managing thousand of simultaneous devices, establishing connections between them, and the basics of building a cloud infrastructure that can handle all of this and more.

## **What Are Some of the Complexities of Creating and Hosting a Managed IoT Platform?**

### **1\. Designing, Building, and Testing Software and Hardware**

Just like any self-managed service, you must spend ample time (weeks or months) scoping the hardware, software, network, and server requirements to run such a service. This often means you will need to hire new resources and/or repurpose current resources just to get into the development phase. Additionally, you will need to build development, deployment, and testing infrastructure geared specifically for IoT systems and hardware management. This includes configuring a network, and planning connectivity and redundancy strategies so other devices can easily connect to this network.

### 2\. **Infrastructure Setup and Costs**

According to [Gartner](http://www.gartner.com/newsroom/id/3598917), total spending on endpoint infrastructure and services will reach almost $2 trillion in 2017. For a managed IoT service, there are even more significant upfront costs that go beyond the normal server architecture needed for a pure web application. A company needs to set up their own hosted cloud service, evented API infrastructure, and fault-tolerant real-time communication channels. Most of these services will need to be purchased from multiple third-party vendors, which creates a lot of unknown expenditures and resources as the project develops further.

### **3\. Domain Expertise**

Developing an IoT service requires a wide range of specialty expertise: embedded technologies, electrical engineering, DevOps practices, server infrastructure, manufacturing, security, and many more. In fact, [Cisco (2017)](https://newsroom.cisco.com/press-release-content?articleId=1847422) found that most companies that consult IoT domain experts throughout the project's lifecycle finish on time. Companies that go it alone often exceed their initial timelines and find that they lack the internal expertise to keep the project up and running. Unfortunately, by the time companies realize that they need additional expertise, they are usually deep into the development process, making pivoting exponentially more costly.

### **4\. Flexibility/Scalability**

Every project faces scalability issues, but imagine scaling up from 100 to 10,000 or a million connected devices. If you don't scale correctly, your costs will skyrocket and your system will fail. When scaling IoT, you are not scaling a single technology or product, you are scaling an entire process. You have to scale business operations, data processes, product infrastructure, and API infrastructure.

It's difficult to adapt to ever-evolving customer and market needs, and even more difficult to add new IoT device offerings. Even when creating a self-hosted solution, network architects need to depend on a number of vendors for sensor hardware, radio technologies, and cloud platforms. If you choose the wrong vendor, you might find yourself stuck with an incompatible piece of hardware or software.

### **5\. IoT Sensors and Networking Complexity**

According to [Intel (2016)](http://r-stylelab.com/company/blog/iot/internet-of-things-how-much-does-it-cost-to-build-iot-solution), 85% of gadgets were not configured to communicate with one another or connect to the internet. This means a managed IoT service requires middleware that opens gateway connections between device sensors and their application layer. Not only do you have to integrate this type of middleware, but network engineers will need to measure and maintain them as well. When you integrate IoT sensors and data streams, you are now concurrently processing terabytes of data. Your organization has suddenly turned into a big data company that has to process massive data sets that could include sensitive information.

### **6\. The Security/Privacy Issue**

With IoT, there is no shortage of security concerns. On a fundamental level, you need to create a service that secures the device connection, the cloud connection, the API connection, and anything else that connects to the managed service. It's not a one-time setup either -- a managed IoT service requires a dynamic streaming mechanism that can keep pace with requirements in monitoring, detection, access control, and other security needs. This not only requires top-notch encryption expertise, but specific firmware written by domain experts. Many projects will need to comply with HIPPA and other industry-specific federal guidelines. These statutes continually evolve and require that you make both software and firmware updates.

## **The Bottom Line**

Together, these 6 complexities make it difficult to host your own IoT solution while maintaining the infrastructure of your current product. The purpose of this isn't to make you feel discouraged though. In fact, there are many solutions and steps you can take to successfully complete your own IoT initiative.

## **Overcoming These Complexities**

There are two options companies can take: build a custom IoT platform or buy a managed IoT platform. For the build route, it is imperative that you research, plan, and consult domain experts to help you scope your IoT project. For starters, here are some IoT [white papers](https://www.particle.io/white-papers/all) to help you learn more about basic IoT infrastructure, security, supply chain management, and power management. Remember to thoroughly address each of the six complexities in your planning and resource estimates.

The second option is to build with a managed IoT platform that provides the hardware, software, and connectivity needed for deploying an IoT product. When you build with a pre-built platform, you also have access to IoT experts, support services, and engineering services to assist you through every stage of the IoT development cycle.

## **All in all**

The purpose of the article is to introduce you to the complexities of building a managed IoT service. By addressing these complexities upfront, you can substantially increase your chances of launching a successful IoT solution. All in all, you must decide whether building your own IoT system is worth the time, costs, and risks, or purchasing a pre-built solution that can help mitigate these complexities.

Opinions expressed by DZone contributors are their own.
