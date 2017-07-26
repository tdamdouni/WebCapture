# The Anatomy of an IoT Solution

_Captured: 2017-05-21 at 12:43 from [dzone.com](https://dzone.com/articles/the-anatomy-of-an-iot-solution?edition=299092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-20)_

The Internet of Things (IoT) is a powerful, transformative force and the cornerstone for digital businesses taking advantage of the convergence of the physical and digital worlds.

McKinsey estimates that IoT could generate $11.1 trillion a year in economic value by 2025. Understandably, IT leaders face growing pressure from the business to deliver new IoT solutions that improve operational efficiency and grow revenue via connected products and services.

I've been involved in quite a few discussions with customers lately on what it takes to develop IoT solutions and how to establish the right architecture. When diving into the subject, I hardly found materials online that would give me an end-to-end overview of IoT solutions architecture, or best practices for getting started with IoT application development.

![](https://www.mendix.com/wp-content/uploads/AnatomyIoT-inpost-1.png)

So, I've started to paint the picture, relate it to projects that Mendix customers are doing in this domain, and distil some best practices.

I'll cover the story in three blog posts, starting with describing the anatomy of IoT Solutions, followed by one about the role of platforms in simplifying IoT Solution Development. The last post will cover recommendations on architecture and best practices for defining an incremental IoT strategy.

What does it take to develop IoT solutions, and how do you establish the right architecture? IoT solution design is quite different from typical IT solutions in that it bridges the physical world of Operations Technology (OT) with sensors, actuators and communication devices, and the digital world of Information Technology (IT) with data, analytics, workflows, and applications.

The diversity of use cases and operational requirements creates an array of IoT Endpoints, communication protocols, data management, and analytics technologies, as well as corresponding deployment topologies.

And that's just for establishing the foundation. The real value of IoT comes from turning data into insight, and making it actionable to drive smarter operations or launch new products and services. This fuels the need for IoT apps that empower users to act upon insight, by combining sensor data, data residing in enterprise systems such as ERP, CRM, and PLM, and even third-party services such as weather and traffic data.

## **What an IoT Solution Looks Like**

Despite the diversity, there is a level of commonality across use cases that can illustrate the anatomy of IoT solutions. Taking a layered approach in describing the anatomy helps identify relevant services and technologies from the things-level all the way up to IoT apps.

![](https://www.mendix.com/wp-content/uploads/Artboard-1SAP.png)

### **IoT Endpoints**

This layer covers the physical world and operational technology required to connect things and communicate:

  * **Things:** The real endpoint for IoT is obviously the thing that should be connected, whether physical products like cars, jet engines, and lighting systems, or other 'things' like livestock, crops, human beings, or spatial areas like rooms or outdoor space.
  * **Sensors:** collect and report data on the actual status of things to which they're connected. Sensors could be mounted on, or embedded in, things to monitor temperature, pressure, light, motion, location, etc.
  * **Actuators:** control the physical or logical state of a product through signals they get from IoT apps or other systems, like opening a valve, or turning a camera, motor or light on/off. This includes commands sent to embedded software e.g. to reboot or update configurations.
  * **Agents**: components that mediate between a set of IoT devices and act as a bridge between the sensors/actuators and the cloud, deciding what data to send and when. In reverse, they also process commands and updates coming from the cloud.
  * **Edge computing device**: a distributed architecture in which IoT data is processed at the edge of the network. Transmitting massive amounts of raw data over a network puts tremendous load on network resources. In some cases, it is much more efficient to process data near its source and send only the data that has value over the network to the cloud.
  * **Communication**: For IoT device communication, the physical layer and communication protocols are distinguished. As far as the physical layer is concerned, gateways, mobile devices, mesh networks, and direct- or broadcast device communication are alternatives that may or may not be suitable depending on the use case. The choice for the physical layer will determine which communication protocols are most suitable (e.g. MQTT, COAP, HPPT(S), AMQP, ZigBee, Z-Wave, etc.)

## **IoT Software**

The next layer is the (cloud) platform that brings essential IoT software services together to manage the IoT endpoints securely, represent the 'digital twin' of connected things, process and analyze data, and provide APIs to consume and expose services:

  * **Device management:** simplifies the process of configuring, provisioning, and operating the endpoint devices. It supports monitoring, testing, updating software, and troubleshooting connected devices.
  * **Digital twin management:** For many IoT use cases, particularly in industrial IoT, it's valuable to define a digital twin of the connected thing. This could be as simple as a 1:1 mapping of the physical things to logical identifiers in the IoT Platform, or as sophisticated as mapping an engineering view of an asset with a hierarchical structure of components/systems to the physical devices representing that asset on an instance and class level.
  * **Event and data processing**: Event Processing deals with event streams coming from connected devices, filtering, and monitoring. In addition, services for data aggregation, data storage, and management are required.
  * **Analytics/machine learning:** Analytics services perform statistical analysis and apply machine learning to detect patterns on a device instance or class level for predictive maintenance, making recommendations, triggering engineering changes, etc.
  * **API management**: provides openness on all layers in the IoT platform for device communication, data-, service-, and backend integration, and application development.
  * **Security management**: ensures that IoT endpoints do not expose security threats due to the increased attack surface IoT creates. IoT devices generate sensitive information about operations transmitted over the internet. Also, devices themselves are vulnerable to hacks that could cause serious business damage. Security services should include (certificate-based) device attestation, network connectivity, software upgrades, authentication, identity and access management, and data loss prevention.

## **IoT Apps**

The Apps layer is where IoT solutions are brought to life, turning data into actionable insight, putting it in the hands of business users, customers and partners. This is the layer where integrations with existing back-ends and 3rd party services are established and workflows are defined to act upon insight. Core services in the apps layer include:

  * **Integrated development environment (IDE):** A design time environment is required to develop IoT apps. This could be a traditional IDE for coding in a specific language or a model-driven environment for collaborative, visual development of IoT apps. In addition, core services for software configuration management and branching & merging are needed for development teams to commit their work, and create builds and application packages. Finally, the IDE should guide developers to apply the right patterns and best practices for IoT app development.
  * **Multi-channel apps:** In today's world of web and mobile apps, the IDE ideally supports development of cross-platform, responsive and multi-channel apps, optimized for specific form factors, using device features and supporting gestures with minimal overhead.
  * **Integration**: The lifeblood of IoT apps. Apps should have access to IoT endpoints (via the digital twin) for reading the full history of a 'thing' after receiving an alert, or triggering an actuator. They should be able to leverage various IoT software services (e.g. time series data and machine learning algorithms) and weave these services into IoT apps. Last but not least, integration with enterprise back-ends and 3rd party services is needed for managing workflows and making IoT apps contextual e.g. by creating a dashboard for a service engineer, enhanced with engineering and customer support data.
  * **Testing**: Testing & quality assurance are essential disciplines in IoT app development projects. Test automation on various levels (unit test, integration, functional test) helps minimize the test burden relative to (iterative) development cycles.
  * **Deployment**: Staged deployment to target environments and automated provisioning of application resources (web server, OS, database, file storage) helps DevOps engineers to efficiently manage IoT apps. Ideally, there's flexibility to deploy on a cloud of choice--for instance, close to where core IoT services that the application uses are running.
  * **Management**: User management, application management, monitoring, and self-service options for horizontal/vertical scaling and configuring high-availability are important to manage IoT apps. Specifically, support for elasticity backed by a stateless application architecture is essential to deal with variable load and volume.
  * **Security**: Like for the IoT platform layer, security on an app level is vital. This concerns both the application runtime environment and the security settings for the apps themselves (e.g. access and authentication).

The elements that define the anatomy of an IoT solution may come across as overwhelming. As mentioned before, the type and level of sophistication of the IoT solution will determine how many of the elements and services described are needed to create an end-to-end solution.

Nevertheless, it's clear that the diverse set of endpoints, network technologies, protocols, IoT software, and application development services pose a challenge for enterprises planning to adopt IoT to transform their business operations. The question is: How do you make IoT solution development manageable? The answer lies in adopting a platform approach.
