# The Reality of Digital Twins for IoT

_Captured: 2018-09-11 at 18:34 from [dzone.com](https://dzone.com/articles/the-reality-of-digital-twins-for-iot?edition=391216&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-09-11)_

One of the key IoT trends in 2018 is the rise of 'Digital Twins.' Gartner has included digital twin as one of their [top 10 IoT technologies for 2018](https://www.gartner.com/smarterwithgartner/gartner-top-10-strategic-technology-trends-for-2018/). I also included digital twin as a key trend in [my predictions for 2018](https://ianskerrett.wordpress.com/2017/12/19/iot-trends-for-2018/).

Therefore, I thought it would be interesting to see what the IoT vendors are providing for digital twins and, more importantly, how developers can build a digital twins. Similar to my post on [Machine Learning at the Edge](https://medium.com/@iskerrett/machine-learning-at-the-iot-edge-8fed3d498bdb), this is a review of websites and online documentation; not a technical evaluation. Feel free to add comments for solutions that I might have missed.

## What Is a Digital Twin?

In simple words, a digital twin is the virtual representation of a physical asset. Some refer to a digital twin as the virtual doppelganger of a thing. I also like the analogy that a digital twin enables a [device-as-a-service](https://www.eclipse.org/ditto/).

The benefits of a digital twin is to provide an abstraction layer that allows for applications to interact with a device or devices in a consistent manner. The vision of a digital twin is that it follows the lifecycle of a device and the data associated with the device. Digital twins will enable features like device simulation during development, integration of analytics, and machine learning during deployment, and so on. This [article from IBM](https://www.ibm.com/blogs/internet-of-things/iot-digital-twin-enablers/) does a decent job to lay out the vision.

Conceptually, I can see the value of digital twins, so I am interested in seeing how vendors are implementing them in their solution and how developers might be able to build digital twins.

## Survey of Digital Twin Solutions

First up is a review of the major cloud vendors.

#### **Microsoft**

Microsoft talks a lot about [digital twins for discrete manufacturing](https://enterprise.microsoft.com/en-us/trends/microsoft-is-redefining-digital-twins-in-discrete-manufacturing/). However, they talk about it as a [concept rather than a product](https://myenvision.microsoft.com/sessions/54981?source=sessions).

Microsoft Azure IoT does have the concept of a '[device twin](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-devguide-device-twins)' that is part of their device management solution. A device twin is automatically created when a device is connected to the MS IoT Hub. The device twin is a JSON file the stores the device state information that can be used to synchronize device information with back-end processes.

#### **Amazon**

Amazon refers to a '[device shadow](https://docs.aws.amazon.com/iot/latest/developerguide/iot-device-shadows.html)' as their version of a digital twin. A device shadow is a JSON file that contains the state information, meta-data, timestamp, unique client token, and version of a device connected to the device shadow service. There are three basic REST APIs that can be used to interact with the device shadow: GET, UPDATE, DELETE. You can also interact with device shadows using MQTT messages.

#### **IBM**

IBM has a ton of marketing collateral around [digital twins](https://www.ibm.com/internet-of-things/spotlight/digital-twin), including a number of reports and videos. In fact, IBM is definitely the vendor who has invested the most in promoting the concept of a digital twin.

However, it is really hard to figure out how you would actually build a digital twin on IBM Watson IoT. Luckily, friends from Twitter provided links to this document about [data management](https://console.bluemix.net/docs/services/IoT/GA_information_management/ga_im_device_twin.html#device_twins) for Watson IoT. This document seems to take you through a fairly detailed set of steps to create a digital twin. It certainly seems a lot more complicated than other solutions from AWS and Microsoft.

### **Industrial Vendors**

The concept of digital twin is heavily discussed in Industrial IoT, specifically manufacturing. For instance, the[ Industry 4.0 reference architecture](https://www.plattform-i40.de/I40/Redaktion/EN/Downloads/Publikation/structure-of-the-administration-shell.html) has the concept of an admin shell, which is similar to the digital twin concept. For this reason, it is interesting to see what the major industrial IoT vendors are providing for digital twins.

#### **GE Predix**

[GE Predix](https://www.ge.com/digital/industrial-internet/digital-twin) also talks a lot about digital twins in their marketing material. GE has some very [compelling videos](https://youtu.be/2dCz3oL2rTw) that include AR/VR integrated with digital twins.

GE Predix talks about asset-centric digital twins. They provide a detailed tutorial on how to create a [digital twin for analytics](https://www.predix.io/resources/tutorials/tutorial-details.html?tutorial_id=2136&tag=1611&journey=Digital%20Twin%20Analytics%20Reference%20App&resources=2136,2348,2347,2138). They also have an [Asset Service ](https://www.predix.io/resources/tutorials/tutorial-details.html?tutorial_id=1736&tag=1715&journey=Exploring%20Asset%20service&resources=1710,1736,1711,1951,2456)that allows you to model your assets, which can be essential to any digital twin solution. Overall, the GE Predix digital solution looks pretty sophisticated.

#### **Bosch**

Bosch's digital twin solution is called [Bosch IoT Things](https://www.bosch-iot-suite.com/things/). Bosch has some pretty detailed [technical documentation](https://things.s-apps.de1.bosch-iot-cloud.com/dokuwiki/doku.php?id=start), including developer guides, [demo applications](https://things.s-apps.de1.bosch-iot-cloud.com/dokuwiki/doku.php?id=006_demo:006_demo), and hosted dashboard. The Bosch digital twin solution appears to be the most advanced and, more importantly, the most accessible to developers. If you are interested in exploring the concepts of digital twins, I would definitely start here.

The only open source digital twin solution I could find was [Eclipse Ditto](https://www.eclipse.org/ditto/), a project created by Bosch and contains the technology used for the Bosch IoT Things solution. The Eclipse Ditto website has extensive [documentation ](https://www.eclipse.org/ditto/intro-overview.html)and a [sandbox server](https://ditto.eclipse.org/). There is also a [detailed technical webinar](https://youtu.be/NpC4ROGqwKc) on Eclipse Ditto. If you are a developer who wants to start to incorporate digital twins into your IoT solution, you might want to take a look at Ditto.

## Summary

Right now, the term 'digital twin' is really just a concept that has a lot of marketing hype from some of the vendors. In general, the current solutions provided by some of the key IoT platforms are pretty basic. There is a lot of work needed for digital twins to become reality for developers.

The exception appears to be the Eclipse Ditto and Bosch IoT Things solution. Based on the same technology framework, they appear to have the most advanced technology for digital twins. There is still a lot of missing features, like simulation, data integration, etc., but the base building block seems to be there.

NOTE: Please feel free to add pointers to other digital twin solutions in the comments below. I am interested in understanding what other companies are doing in this space!
