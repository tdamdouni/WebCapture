# 3 Best IoT Frameworks for Beginners

_Captured: 2018-01-13 at 19:09 from [dzone.com](https://dzone.com/articles/3-best-iot-frameworks-for-beginners?edition=352117&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-13)_

![](https://d1xzrcop0305fv.cloudfront.net/wp-content/uploads/2018/01/02105803/zymr-3-best-iot-frameworks-for-beginners.jpg)

As of 2016, there were over 300 IoT platforms to choose from, and the cost of integrating IoT solutions is skyrocketing, as is the growing network of devices with IP addresses that enables our connectivity to the great data cloud in the sky. [According to IoT analysts](https://www.slideshare.net/KaiWaehner/iot-open-source-integration-comparison-kura-nodered-flogo-apache-nifi-streamsets), the number of networked electronics is projected to exceed 20-50 billion devices by 2020.

So, how do you choose which IoT platform is best for you--especially when you're just getting started? First, understand that IoT frameworks complement cloud platforms, analytics, micro-services, APIs, and function as part of a hybrid integration architecture. The tricky bit is that not all devices are connected to the cloud all the time, nor do they always have sufficient bandwidth to stay updated in high-latency conditions.

Unfortunately, there is no standard or one-size-fits-all IoT framework that fits everyone's needs, so below we've compared several frameworks such as Eclipse Kura, Node-RED, and Flogo to help point you in the right direction. A few commonalities that all of these share is that they are open source, designed for integration developers, and work well with MQTT, CoaP, REST, and others. They are all deployable 'at the edge' and their extendable APIs offer customization.

### **Eclipse Kura**

Kura is one of the most popular IoT frameworks, but it isn't for the faint of heart. It's designed for integration specialists familiar with Apache Camel and uses the Eclipse 1.0 public license. Kura is also a mature framework established in 2013, so it's relatively bug-free and has an impressive track record focusing on IoT Gateways powered by Java or OSGi. Despite its popularity, it has a number of drawbacks (or features, depending on how you look at it), including the following:

  * Kura requires developers to create their own source code without a visual designer, so you'll get more customization but also a significantly higher learning curve.
  * Kura does have a web UI for configuration of the protocols and devices connected to your network, and this also includes options for data and cloud services, and other I/O integration.
  * Uses a multi-service gateway with an online/offline mode and can manage applications and network connectivity.
  * Runs on a wide range of edge, container, cloud, or premise platforms.

### **Node-RED**

Unlike Kura, Node-RED is a visual tool for wiring IoT connections and integrating them simply. It's built on JavaScript and Node.js so you can expect easy installation and integration flowcharts as well as an Apache 2.0 license. Like Kura, it has also been around the block and is reliable. There are also numerous online examples and documentation available. Node-RED key features include:

  * Easy, beginner-friendly installation.
  * Uses color-coded boxes and wiring connections to visualize your web of networked devices.
  * Leverages IBM Bluemix cloud with native integration.
  * Runs on a wide range of edge, container, cloud, or premise platforms.

### **Flogo**

The biggest difference between Flogo and its aforementioned competition is that it has extremely lightweight edge applications, which can make a big difference if your hardware and/or bandwidth is bogged down by queries. Flogo is powered by Golang and is also a visual tool that's easy to install and get the hang of, and uses a BSD-style license. While it's not as old as Node-RED, Flogo's zero dependency model allows for shared lightweight binaries on devices. A few other features include:

  * Easy installation and integration workflow.
  * Color-coded visual designer equally suited to specialists and non-specialists.
  * Flows are shareable as JSON files or strings.
  * Also runs on a wide range of edge, container, cloud, or premise platforms.
