# Tips on Building a Complete IoT Solution for Your Business

_Captured: 2017-03-23 at 15:25 from [dzone.com](https://dzone.com/articles/tips-on-building-a-complete-iot-solution-for-your?utm_medium=twitter&utm_source=dlvr.it&utm_campaign=Feed:%20dzone%2Fiot)_

![Image title](http://bridgera.com/wp-content/uploads/2017/03/blog_post_IOT_banner2_revised_final-768x384.jpg)

Building an enterprise IoT solution, is far more challenging than building yet another business application. And since the [IoT tsunami](http://bridgera.com/the-iot-tsunami-are-your-apps-ready/) is still in its formative stage, it is no less challenging to put together a business case driven by a clear ROI.

For a start, an IoT solution is not just software, it is a combination of:

  * A physical thing (device), which is hardware with built-in firmware that controls device behavior and capabilities
  * Network communication channels, which are dependent on the transmission protocols that the device can support
  * A multi-tiered IoT application software that is comprised of:
  * Listener service that provides data ingestion capabilities
  * Business logic layer that encapsulates data processing capabilities (validates user inputs and translates to messages to/from the device)
  * Integration service that connects the IoT system with other business applications
  * User interface that allows the end user to use the IoT solution
  * Database for data storage
  * Business Intelligence layer providing analytics and visualization

I like to compare an IoT solution to the human body. The IoT application software is the heart and brain of the system, pumping blood (data) and control commands through the communication channels (blood vessels and nerves). And the things, or devices, are our hands, legs, fingers, and toes.

So how do we build a great IoT solution from these ingredients? Here are a few key factors to consider during your selection process.

## **Device Selection**

Device selection is its own can of worms. There are many options in the market to choose from. There are several key device characteristics that should drive your decision-making; for instance, your device should:

  * Have the capabilities you need (GPS, geofence, alerts, alarms, audio, video, waterproof, etc.)
  * Meet your functional needs: 
    * Environment (temperature, humidity, altitude, indoor, outdoor, underwater, etc.)
    * Battery life (access to power sources)
    * Built-in security features to deter hackers and allow the device to function in a predictable manner
  * Be easy to provision, deploy, and administer (configure and diagnose)
  * Support over the air (OTA) firmware updates, eliminating the inconvenience of buying new devices if business needs change or if system enhancements are needed
  * Support communication channels that are best suited to your use case
  * Be certified by regulatory organizations relevant to your business

One of the challenges involved with device selection/validation is that you will need access to the IoT application software before you can complete an end-to-end proof of concept (POC).

## **Communication Channels**

This is a complex part of any IoT solution and requires a general understanding of the wireless communication options supported by your device. Your options range from Bluetooth and Wi-Fi (NFC) to LAN and WAN, using cellular and satellite communication.

Key characteristics to consider when evaluating communication channels include:

  * The range, or distance, of the communication - determined by frequency of the radio signal
  * Real-time performance criteria - determined by bandwidth (data rate) and latency (delay)
  * Signal strength variations that your device must function under
  * Likelihood of signal interference
  * Security considerations (encryption levels)

## **IoT Application Software**

IoT application software is often referred to commercially as an IoT platform. There are many IoT platforms to choose from along with the option to build your own. It is important to understand the capabilities and limits when evaluating a platform. Some platforms, for example, will only enable communication between devices that are certified for the platform. This limits your device selection. Other platforms may limit capabilities to data ingestion with the expectation that you will consume data through an API. Bridgera's built-to-spec IoT software solutions are tailored to your needs, offering custom user interfaces, custom device integration, [and more.](http://bridgera.com/services/internet-of-things/)

It is also important to understand the skills you need if you plan to customize the platform to meet the requirements of your use case. Below is a description of a comprehensive IoT application software solution:

![Image title](http://bridgera.com/wp-content/uploads/2017/03/blog_post_IOT_banner2_revised_final750x400.jpg)

## **Listener Service for Data Ingestion**

This is generally a network program that is connected to the internet. The listener should "always be on" and capable of substantial scaling. It should guarantee secure messaging between the device and the rest of the application software services. High availability requires complex distributed processing logic that ensures backup mechanisms are in place when servers fail or overload.

A good listener service as architecture is a highly configurable solution, so that it may be configured to talk to various devices quickly. It should also support multiple communication channels and protocols.

The data ingestion service must be compatible with the communication protocol used by the device. Apache NiFi coupled with a message broker like Kafka or RabbitMQ can work well as an effective IoT data ingestion engine.

## **Business Logic Layer for Data Processing**

This is where the business functions occur. Account setup, user registration, access control, payment processing, device interactions, data validation, error handling, and logging are all part of this layer. The design should facilitate multi-threading to support large user volumes.

## **Integration Service**

This layer is responsible for communication with existing business applications. Just because you have a new IoT solution does not mean you can do away with the rest of your application portfolio! This is often underestimated and overlooked when deciding on a new IoT solution. A strong integration service allows two-way communication: Expose RESTful APIs to provide IoT data to external systems and consuming external APIs to bring relevant data into the IoT solution. External interfaces may be SOAP or RESTful.

## **User Interface (UI)**

The level of personalization and usability of the user interface is highly dependent on the IoT use case. IoT UI's can range from very unique user experiences to dashboard graphs and widgets. User interfaces should provide easy access to deployed devices. All device commands are formatted based on user actions that are permitted through the UI. In general, a good UI will provide:

  * Customer portal for user registration and account management
  * Dashboards
  * Search capability
  * Device management console (for Admin users)

## **Data Storage**

Considering the proliferation of IoT devices, it is highly recommended that your data storage mechanism is architected using big data technologies. NoSQL databases (MongoDB, Cloudant, DynamoDB, etc.) are excellent choices and allow clustering and unlimited horizontal scaling. They are also flexible because they are typically 'schema-less' and designed for high performance

## **Analytics and Visualization**

Finally, to realize the full potential of an IoT solution, it is important to drive business value through insights gained from the mass amount of data collected from your devices. There are several powerful proprietary and open source technologies that can be plugged into your IoT solution to derive business insights through analytics and visualization.

Ideally, analytics is custom-built within the IoT solution using technologies within the Hadoop stack. HortonWorks, Cloudera, and MapR are the most popular Hadoop distributions in the market that have leveraged Spark's analytics capabilities. Splunk is a proprietary solution option for log analytics. While Tableau, Qlikview, and PowerBI are popular for visualization; however, D3 is a powerful, open source alternative.
