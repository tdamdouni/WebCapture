# Azure IoT in the Industrial World: A Reference Architecture

_Captured: 2018-05-22 at 21:18 from [dzone.com](https://dzone.com/articles/azure-iot-in-the-industrial-world?edition=376341&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-05-22)_

With over 200,000 attendees, [Hannover Messe 2018](http://www.hannovermesse.de/en/exhibition/facts-figures/after-show-report/end-of-show-report/), provided an amazing venue for sharing our latest release - an industrial reference architecture for genset optimization, monitoring, and control. Dr. Jochen Kockler, Chairman of the Managing Board at Deutsche Messe closed this year's event in Hannover, Germany by stating "Technology is not about competing with us humans; it's about assisting us. The interaction of humans with machines and IT adds up to a huge competitive gain across manufacturing, logistics and the energy industry." We couldn't agree more. For digital transformation to succeed inside traditionally hardware-focused organizations, industrial IoT, and connected product solutions must deliver actionable insights in a transparent fashion that increases the value of humans in the system rather than attempting to replace them. With this outcome in mind, let's look at how genset optimization presents an opportunity for bringing about exactly this sort of positive change in the industrial space.

## Azure IoT Reference System

Our reference design for an Azure IoT industrial genset optimization application is aimed at the following primary use cases:

  1. Remote monitoring and dashboards providing at-a-glance operational status of power generation assets across multiple organizations and site locations
  2. Management and configuration of individual assets for peak performance, including secure, IT policy-driven user access controls on the basis of organization, site, and user role
  3. Enable the building, training, and deployment of predictive models at the edge and in the cloud
  4. Create and operationalize continuous learning loops for maximizing energy output and minimizing energy costs

The first two use cases are shown in the main dashboard panels below - temperatures, pressures, location, etc. The more predictive aspects of scenarios three and four are made possible by the architecture and underlying services.

![azure iot genset asset dashboard](http://brightwolf.com/wp-content/uploads/2018/05/azure_genset_dash1.png)

![azure iot genset fleet dashboard](http://brightwolf.com/wp-content/uploads/2018/05/azure_genset_dash2.png)

## Industrial Data Management and Gateway Independence

At the heart of this reference architecture is an extremely flexible data management layer for orchestrating the collection, cleaning, normalization, and contextualization of information from machines, 3rd party sources, and integrated enterprise systems. At the edge, the system provides local filtering and storage, device connectivity and protocol translation, and grants independence from any particular gateway hardware vendor.

## Machine Learning at the Edge and in the Cloud

The system provides the capacity for [Microsoft Azure IoT Edge](https://azure.microsoft.com/en-us/services/iot-edge/) integration to run trained models locally and execute custom logic with or without direct connectivity to the cloud. This can also include on-premises AI and image recognition, reducing latency and bandwidth constraints and bringing intelligence more directly to your equipment in the field.

This cloud architecture features [Azure IoT Hub](https://azure.microsoft.com/en-us/services/iot-hub/) for the secure ingestion of machine data from the edge. The reference system ensures a source of clean, trusted, and completely auditable data is made available to [Azure Machine Learning Studio](https://azure.microsoft.com/en-us/services/machine-learning-studio/) for building and sharing predictive models, which the system is designed to rapidly operationalize. [Azure Time Series Insights](https://azure.microsoft.com/en-us/services/time-series-insights/) lets you view and explore correlations across real-time and historical data to spot hidden trends and anomalies.

![azure iot reference genset](http://brightwolf.com/wp-content/uploads/2018/05/bw_azure_genset.png)

## Optimize Performance, Maximize Profits

A real-world scenario envisioned by this design is the automation of decision making for when to run each generator based on local conditions such as weather, production schedules, and fuel and electricity prices (both historic and predicted). For each generator, there are times where it is more cost effective to consume stored fuel and generate power to run your facilities than buying electricity from the grid, depending on utility rates. Under certain conditions, additional revenue can be produced by generating electricity for sale directly to the utility company at a profit - but only if you can accurately monitor and correlate these conditions and take immediate action.

A successful connected solution gives human operators access to data and insights for making decisions that were previously too complex or resource intensive to be viable aspects of enterprise business strategy. As a result, with each new tactic brought into the realm of the possible through automation, the achievable boundaries of executive aspirations are expanded ever further to propel the business ahead of competitors moving at a slower pace on their digital transformation journey.

## Start Faster, Go Further

This design empowers equipment makers to deliver connected customer pilots in a fraction of the time, expense, and risk of traditional methods without sacrificing the agility and control you require for long-term success. All code runs entirely inside your own Azure subscription so you remain in control of your data and feature roadmap.

The solution at the edge leverages Bright Wolf's GearBox suite, providing a flexible approach to local storage and secure data management so you remain free to choose your gateway hardware and software tools as your requirements and goals change over time. Also included are protocol clients and drivers for translating Modbus, OPC-UA, J1939, Ethernet/IP, and other industrial protocols to MQTT for ingestion via Azure IoT Hub, enabling the rapid connection of PLCs from Allen-Bradley, Siemens, and others to the cloud.

![azure iot gearbox edge](http://brightwolf.com/wp-content/uploads/2018/05/bw_azure_edge.png)

In the cloud, Bright Wolf's [SpringBoard reference system](http://brightwolf.com/2018/03/27/microsoft-azure-support-springboard-industrial-iot-system/) rests on top of our Strandz data management infrastructure in conjunction with Azure's secure data ingest, storage, compute, and other platform services. It includes customizable code blocks for solving the complexities associated with user management, asset modeling, reporting engines, notifications, and other challenges that are common to all connected product systems.

![bright wolf azure iot stack](http://brightwolf.com/wp-content/uploads/2018/05/bw_azure_stack.png)

> _Topics: azure iot , iiot , industrial internet , iot_
