# The IoT Data Platform: Architectural Approaches

_Captured: 2017-08-08 at 20:21 from [dzone.com](https://dzone.com/articles/the-iot-data-platform-architectural-approaches?edition=310395&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-23)_

Cisco IoT makes digital transformation a reality in factories, transportation, and utilities. [Learn how](https://dzone.com/go?i=228254&u=https%3A%2F%2Fdeveloper.cisco.com%2Fsite%2Fdevnet%2Fhome%2F%3Futm_source%3DDZone_bumpertext%26utm_medium%3Dad%26utm_campaign%3Ddnamarketing) to start integrating with Cisco DevNet.

The main purpose of IoT projects is to gather data from sensors or devices in order to gain real-time insights, accelerate decision-making, perform automated tasks, and create value by enabling organizations to become data-driven. Being data-driven allows organizations to have a significant competitive advantage, allows them to focus on the strategic and not the urgent, and builds a revenue generation stream by building applications that were unthinkable just a few years ago.

Creating applications and systems optimized for dealing with the intricacies of IoT demands a new architectural approach. In this article, I will look at three of our customers, and how they approached their IoT projects and then try to look at what the common design pattern is between these use cases. In doing so, I hope to inspire your development and successful deployment of your IoT projects.

## BBOXX

[BBOXX](http://www.bboxx.co.uk/) develops solutions to provide affordable, clean energy to off-grid communities in the developing world. BBOXX created an elegant solution -- a solar-powered "Battery Box" that sits in an individual's home to power lights and appliances like TVs, lights, and mobile phones. The name is short for "Battery Box."

### Business Opportunity

BBOXX's business is to sell energy to rural Africa. In order to grow this business, they wanted to become a data-driven company to:

  * **Drive business value:** Proactively monitor and analyze battery health, creating alerts  
based on historical trends that can predict battery failure before it happens. Their  
customers buy a service not a battery!

  * **Increase customer satisfaction and retention:** Gain insight into the day and life of a customer, uncover interesting usage scenarios that drive product development. For  
example, knowing that customers leave their lights on all night for security purposes helps  
BBOXX deliver additional security offerings.

  * **Upsell opportunities: **Correlate and aggregate usage data and upsell additional power  
capacity based on upcoming events; for example, the Kenya and Zambia football match  
increased demand for more energy to support extended viewing times.

### Technical Architecture

I have described their use case in more detail in my article on [Providing Clean Energy in Africa: An IoT Success Story](https://dzone.com/articles/providing-clean-energy-in-africa-an-iot-success-story), and [the case study on our website has more details](https://marketing.influxdb.com/acton/attachment/16929/f-009b/1/-/-/-/-/CustomerCaseStudyBBOXX.pdf?utm_campaign=dzone&utm_medium=partner&utm_source=dzone&utm_content=&utm_term=), but the overall technical infrastructure looks like this:

**![](https://lh4.googleusercontent.com/XwcWz7jA4JgF5znojfE_NgmcwqaxTacOx_eQzOErM30eQfmDIEUX7TeMzmErR6z6uR-lKWAGvy5z2EcyBOh5e-UclwrJ2LOQUoiN9oO_2q2OkD_4gpIryEEB1FzTIib7SRSAj_CAAVo)**

Data is sent from the sensors via a 2G network and through the Amazon Web Services infrastructure into the cloud. Once the raw sensor data is in AWS, it is then stored in [InfluxDB](https://www.influxdata.com/time-series-platform/influxdb/) -- a database designed for metrics and events. Once in InfluxDB, they are able to analyze the data, provide interesting business dashboards, generate predictive maintenance alerts and notifications, and use this data to predict and find interesting business trends like energy consumption spikes during soccer events.

### Business Outcome

BBOXX provides hundreds of thousands of people access to clean energy across 35 countries. They are scaling their business from 85,000 units to over 1 million and have become a data-driven organization able to enter new markets and create new solutions based on data that they analyze in real-time.

## tado°

[tado°](https://www.tado.com/us/) is a company focused on home climate control. Driven by its mission of smart energy management without sacrificing comfort, tado° believes it is possible to live comfortably and still act responsibly. Tado needed an IoT solution as it created and rolled out its Smart AC Control which enables consumers to intelligently control air conditioners based on location and temperature.

### Business Opportunity

Tado's business is about using IoT to deliver an experience to the consumer that other AC controls can't do:

  * **Drive business value:** Bring to market a Smart AC Control device and the consumer-driven web and mobile applications to make any air conditioner smart by making it controllable from anywhere. Automate temperature control using a variety of collected data (geolocation of the user, temperature, user settings, current device functional state) and let users know when the device may need maintenance. 
  * **Educate customers on energy usage:** Consumers are becoming more interested in their carbon footprint and their impact on the environment. Consumers want to reduce their energy consumption from an environmental and budgetary impact. Tado needed to deliver an application that could graphically show consumption, predict trends, and automate the whole system allowing for unattended smart operation. 
  * **Predict new trends:** Tado wants to collect all this data and use it to get insight into energy consumption to deliver interesting and innovative solutions that will reduce energy consumption by creating a smarter home and office. 

### Technical Architecture

There are more [details in the webinar and case study](https://www.influxdata.com/project/iot-monitoring-with-tado/), but the overall technical infrastructure is:

**![tado architecture.png](https://lh3.googleusercontent.com/AxXGbR19my6wtu5xahNK-oLDB1BA6vnOVWmNR91qH3dxfHumVbzoRat4MLdpSf55othRINEqWB__6JvzHTS10Ly4tJva6vtGYB3pX5p4V5uDFu_AvHF6-gR5HbXoDthgSzOt7ts5)**

Using the 6LoWPAN low-energy protocol, tado° devices communicate wirelessly with the company's Internet bridge which is connected to the home router. Devices report temperature changes to the server of 0.1 degrees or more. This measurement is wrapped in a message and sent through a secure WebSocket to tado°'s cloud infrastructure which consists of EC2 instances at Amazon Web Services; from there, tado° writes the data collected to its InfluxDB Time Series Data Store. Writing to InfluxDB is done through a hosted instance in InfluxCloud, and there are 5-10 application instances writing in parallel at a total write rate of 5000 points/s. Batch writing is used, and write time for batches is observed. Netflix Hystrix adds resilience and fault tolerance, providing backup if batch write requests fail. The web applications and mobile applications query InfluxDB to provide real-time graphs, statistical analysis, and control of the AC unit.

### Business Outcome

Tado has already delivered this functionality to the market, so it provides: instant access to daily insights and a full year's view of users' home temperature. Unprecedented convenience and efficiency are now only a click or swipe away. Functionality gained includes easy setup (Smart AC Control connects to the home Wi-Fi -- no additional device or wiring is needed); location awareness (using residents' location, the AC self-regulates automatically to detect the first person returning, cools before they get home, and saves when residents are away); control from anywhere (tado° mobile app allows users to check and change settings remotely while on the move); cost savings (users can save up to 40% on AC costs, and tado° can pay for itself in less than a year); and much more.

## Spiio

[Spiio](https://spiio.com/) uses its sensor-based Spiio Cloud Platform -- featuring wireless systems, smart irrigation, and plant data analytics -- to give clients a full view of green wall installations anytime, anywhere. Using Spiio's real-time analytics, clients can understand their plants' condition, share insights across their organization, and make data-driven decisions to boost maintenance efficiency and improve green wall design.

### Business Opportunity

Recognizing the greenery industry's need to maintain installations, extract insights on plant performance, and improve green wall design based on data-driven decisions, Spiio knew from the beginning that they had to build a plant monitoring system. They needed a solution that was easy to scale, provided the ability to ingest high volumes of data from distributed sensors, and could provide real-time control and notifications. In a nutshell, they needed a platform that could map to their business processes and allow them to simply track how the plants were doing, detect anomalies, and support predictions to correct poor performance overall.

### Technical Architecture

There are more [details in the webinar and case study](https://www.influxdata.com/project/customer_case_study_spiio/), but the overall technical infrastructure can be depicted as follows:

**![../../../../Desktop/Screen%20Shot%202017-05-02%20at%203.11.54%20PM.p](https://lh6.googleusercontent.com/C79EmD4I4adHuVCfENsx6o_6lL3ncb-CkIOpzKhZXWj9fTmpcFp_JasCleWK3h70K47BBkIYyFnBi6b1oi3cdQRfAEUEH-YOArCcWXeF1aCCnVphAgfIWvnPviIVdBwO08dcam5qi5h4U66KRA)**

Spiio uses ElectricImp at the Spiio sensor to safely and securely send sensor data to their gateways. ElectricImp fulfilled the requirements of device security and connectivity. They used the InfluxData platform hosted on an AWS instance to fulfill the requirements of data processing analytics, presentation, and integration. As part of Spiio's architecture, InfluxData performs streaming analytics and scopes event detection by tags, it visualizes data and creates client-defined alerts, and InfluxData is used for metric collection from their gateways.

Data is sent hourly per sensor, then sent in 5-hour batches from their gateway to InfluxDB. As green walls need to be monitored over the long run, the data tracks "slow" trends of irrigation and performance over seasonal changes to view long-term impact and is retained indefinitely for historical purposes.

To enable high-precision sensor-based monitoring, a green wall is approached as a grid divided into zones, with each zone divided into sections and each section divided into spots.   
A sensor swarm aggregates the overall green wall condition while enabling data drilldowns into the zone, section, and spot levels to detect overall performance patterns, identify problem areas, and optimize irrigation timing.

## The Distributed IoT Platform

Looking at these three use cases, it is possible to define a generic architecture for every IoT project, a basic IoT Platform Architecture:

**![IoT Data Platform.png](https://lh3.googleusercontent.com/WtzpraSmfEzD6tqiSoxlix7Q3PiYuS82ZcjAG-s7VXloiJEfNXmgI2zNNvq_CcxLYFKt9sdPDwDRC861bg0PhqzRHqOZK9SRVokRPwBHFz8o94X4TJrjCv31AepP4rURfkwogyFA)**

**Devices**: Sometimes referred to as "Things" or "end points," these can be software or hardware devices that generate data or measurements from the object they are monitoring and/or controlling. Some examples are temperature sensors, voltage sensors, humidity sensors, and machine rotation sensors. Sensors can be co-located together as in the case of a wind turbine or a car, others form part of another device (like the Smart Watch with biometric data), while some have control features like industrial valves. From the use cases above, examples are: plant sensors, thermostat/AC sensors, and solar sensors.

**Edge/Gateways:** Optional in most IoT use cases (and not in the use cases above) but growing in popularity, gateways are usually deployed closer to the edge (some might actually be part of a sensor collection and are deployed with the sensor) and allow for the collection of data and the selective transfer of data to the Hub, and they provide some command-and-control functionality back to an automated device, for example. This area is further expanding into what is called edge computing. This allows for critical decisions to be made closer to where the data is created without it having to always go back to the Hub.

**Hub: **The Hub is conceptually the IoT solution's central processing area. Hubs may be deployed in a distributed fashion but conceptually provide the ability to process data streams from the gateways (or directly from the sensors), to store, monitor, and analyze data, and provide the basis for new applications to enable competitive differentiation.

To support this architecture, an IoT platform needs to provide a variety of services:

**Communication services: **The necessary services that provide device connectivity, message/event queuing and transportation services across Wi-Fi, cellular and fixed connections. In the use cases above, these were provided by Kafka, ElectricImp, and Amazon IoT.

**Security services:** A set of security services that provide encryption and authentication services to ensure that devices (and software on the devices) are secure and tamper-proof; also usually required are additional services that provide security to the communication services. In the use cases above these were provided by ElectricImp, and Amazon IoT.

**Device management services:** Services that support devices' provisioning and lifecycle management. In the use cases above these were provided by ElectricImp and some custom code.

**Data services:** The key set of data services that support collection, aggregation, storage, visualization and analytics of the sensor data. In the use cases above, these were provided by InfluxData.

## IoT Data Platform Services

The new IoT workloads and IoT data characteristics -- more data points, more data sources, more monitoring, more controls -- demand a paradigmatic shift in how we approach building systems that can support these unique characteristics. There is the need for a modern IoT Data Platform which provides a comprehensive set of tools and services that are optimized for IoT data. InfluxData provides a Modern IoT Data platform that provides:

**Data aggregation services: **Lightweight services that can be deployed in a distributed manner to collect, normalize, correlate, and aggregate metrics and events from sensors and other important data sources.

**Data storage services: **Data storage services that support high write loads, the storage and real-time retrieval of large sets of time series data. In addition, the database needs to provide time series functions that support query and analytics.

**Streaming analytics and visualization services:** A set of services that provide visualization and dashboarding services, real-time pattern detection services, a set of notification, control and action services to automate the entire system.

I encourage you to read more in the white paper on [IoT Data Platform Services ](https://www.influxdata.com/resources/iot-architecture/?ao_campid=70137000000Mph2)on our website.

Cisco is a software company. Surprised? Don't be. [Join DevNet](https://dzone.com/go?i=228255&u=https%3A%2F%2Fdeveloper.cisco.com%2Fsite%2Fdevnet%2Fhome%2F%3Futm_source%3DDZone_bumpertext%26utm_medium%3Dad%26utm_campaign%3Ddnamarketing) to explore APIs, tools, and techniques that developers are using to add collaboration, IoT, security, network priority, and more!
