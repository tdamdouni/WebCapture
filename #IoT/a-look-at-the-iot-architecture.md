# A Look at the IoT Architecture

_Captured: 2018-08-28 at 17:31 from [dzone.com](https://dzone.com/articles/iot-architecture-2?edition=385426&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-08-28)_

## **Introduction**

Internet of Things (IoT) is one of the most disruptive IT technologies that exists today. It can be classified as a collection of devices equipped with sensors, actuators, and processors that communicate with each other to serve a meaningful purpose. It is also defined as an interaction between the physical and digital planes; this interaction takes place with the help of various sensors attached to all conceivable objects.

IoT has the power to change the way we interact with our belongings, and in an industry or enterprise, it can change the way the businesses run. Energy companies across the world are already using IoT to optimize usage. Sensors are attached to electrical units to measure consumption and patterns, and accordingly, switch on or switch off when required. IoT sensors are also being used for traffic management, water management, and various other smart city components because of the technology's ability to be remotely manageable.

![IoT Architecture](https://dzone.com/storage/temp/9983998-iot-architecture.jpg)

> _IoT Architecture_

However, there is a certain obscurity to **[IoT](https://www.esds.co.in/iot)** that makes one hesitant to fully employ it on their systems. However, don't let this lack of knowledge refrain you from implementing this technology or reaping the benefits for your business. This is why it is essential for you to invest in a simple architecture that can integrate the networked 'things' and transfer valuable data to your IT system that can be processed into actionable business insights.

## **Sensors and Actuators**

The first layer is the physical layer that is comprised of sensors that can sense and collect data from the environment. Its work includes the pick up of physical parameters or identifying other smart objects. Then, we come to the actuators that can affect a change in the environment. For example, a sensor will sense that the temperatures have changed and the light is low, and thus, at is dusk, an actuator will then automatically switch on the street lights.

* Then comes the **Internet Gateway Layer**. The data that comes from the sensors needs to be prepped before it enters the eventual processing stage. Basically, the data that is received in the analog form needs to be aggregated and converted to digital form, and this layer does exactly that with the help of an Internet gateway that routes it over WLANs or other networks for further processing. Both of the above layers are situated closely with each other so that collection pre-processing can be done in real time. These gateways can be built with additional functionalities like analytics, protection against malware, and data management.
* The pre-processed data then enters the **edge computing IT systems** to perform further analysis of the data. While the above two layers will be located at an actual site of the device, an edge IT processing system will be situated in remote offices or other edge locations but not as far as the DC. Usually, the IoT data is so enormous that, if directly sent to the data center or server, it can eat up crazy amounts of network bandwidth, swamping your resources. Thus, systems at the edge perform analytics to lessen the burden on core IT infrastructure.
* The last stage is where data is analyzed, managed, and stored on strong IT systems. This data is the one that needs more processing, and the feedback need not be immediate. A data center or a cloud-based system suits this purpose perfectly. Here, the results take some time, but what is available is more in-depth and can be combined with other data for deeper insights.

The first two parts of the architecture or the first two stages are all about Operations Technology (OT), while the next two are about Information Technology (IT). While the two are not mutually exclusive, the lines are definitely blurring. A higher level of collaboration is required between the two as the functions start to converge to execute more value for IoT via data processing and domain expertise.

The above architecture can also be defined in layers like:

  * **The perception layer**, which is essentially the physical layer of sensors.

  * The transport or **network layer,** which connects the 'smart things' to network devices and servers or basically transfers the sensor data from perception to the processing layer through networks.

  * **The processing layer** stores, analyzes, and processes the humongous data and employs various technologies, like big data, etc.

  * The **application layer,** which delivers application-specific services to the user

Besides, a cloud-based systems architecture can also deploy a fog-based architecture. In the former, data processing is done in a largely centralized fashion by cloud computers where the cloud is at the center of the system with applications above and the network of smart things below it. This type of a system provides excellent flexibility and scalability, like core infrastructure, platform, software, and storage. In fog computing, the architecture comprises of monitoring, preprocessing, storage, and security layers between the physical and transport layers.

Topics:

iot ,sensors ,internet gateway layer ,actuators ,data storage ,cloud ,edge computing

Opinions expressed by DZone contributors are their own.
