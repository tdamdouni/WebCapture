# A Platform for Intelligent Environments

_Captured: 2017-03-29 at 20:11 from [dzone.com](https://dzone.com/articles/a-platform-for-intelligent-environments?edition=286927&utm_source=weekly%20digest&utm_medium=email&utm_campaign=wd%202017-03-29)_

In this post, I'll explain the architecture of Current by GE's intelligent environment platform. The key differentiator is that it's open at the top and at the bottom so we can integrate with best-of-breed hardware and software to provide the most innovative solutions to our customers.

The bottom layer of the architecture consists of three types of data sources:

  1. Intelligent lights
  2. Other building subsystems
  3. External data.
![Image title](https://cdn2.geready.com/digital/sites/default/files/Intelligent%20Environments.jpeg)

## Intelligent Lights

The intelligent lighting network underpins this platform strategy. It comprises scalable and cost-effective ZigBee-based sensors, actuators and controls to collect temperature, humidity, occupancy, ambient light, CO2, and many other types of data. These devices communicate wirelessly with a gateway that streams data into the Predix cloud.

Lighting is the largest network in a commercial or industrial building and offers the following benefits:

  1. Provides power to sensors so there's no need for separate cabling or batteries
  2. Sits at a vantage point providing a line of sight
  3. Negligible labor costs to install sensors when combined with LEDs
  4. Future proof and vendor neutral thanks to the open ZigBee standard

The lighting network doesn't just provide illumination, sensing, and control. Current embeds codes in the light emitted by LED fixtures to support indoor positioning. An app running on a smart phone receives these codes using the phone's camera to determine its position with 10 cm accuracy. We also embed BLE (Bluetooth Low Energy) beacons in lights to support proximity-based indoor positioning. The positioning data is delivered to the platform for further analysis like the number of visitors in a retail store, frequency of visits, etc.

## Subsystem Integration and Data Gathering

A building has many subsystems like HVAC, solar, refrigeration, access control etc. Typically, these are siloed. Current unlocks these silos to provide one view of the data and access to boilers, chillers, pumps, refrigerators, thermostats, and many other data control elements using the Niagara framework gateway (aka JACE box).

A plethora of useful data is accessible over the Internet such as weather, smart meter, utility tariff, billing, etc. We gather them using the provider's APIs. This makes our platform "open at the bottom" meaning that it leverages data from any system.

## Predix, the Operating System for the Industrial IoT

Current's intelligent environment platform is built on Predix, a cloud-based operating system for developing and deploying industrial Internet applications designed for the challenges and opportunities at the intersection of people, machines, Big Data, and analytics. Predix provides state-of-the-art hosting, connectivity, data aggregation, analytics, security, and visualization capabilities. We leverage these capabilities to store, process, analyze, benchmark and visualize datasets from a portfolio of assets to support data-driven decisions at extraordinary speed and scale.

## Data Normalization

The data normalization layer of the architecture frees applications from hardware and regional dependencies. For example, a European thermostat provides temperature data in Celsius and a U.S. thermostat provides it in Fahrenheit. The application that consumes temperature data should work seamlessly wherever it is deployed, which necessitates data normalization (e.g. normalizing temperature data in Kelvin). We normalize all the data and expose it in the form of standardized, well-documented APIs. You can review the APIs [here](https://www.predix.io/catalog/services/). Each API includes documentation for integration and access as well as sample data sets to assist with development.

## Project Haystack Support

The platform supports Project Haystack, the data tagging methodology adopted by the building automation industry. It's an open-source initiative to standardize semantic data models and web services.

## Apps

The top layer comprises apps that consume data to drive outcomes. Current has developed apps such as an energy management app that lets facility managers monitor, analyze and optimize every aspect of their building's energy consumption and generation.

Beyond energy, many other apps can benefit from the data our platform provides. To explore possible next generation apps, we crowd-sourced ideas and received 300+ ideas in a week! No single company has the time and resources to develop all the ideas. Our strategy is to partner with companies that leverage our open platform to develop and offer differentiated value propositions in the market. Since the normalized data is available in a standardized format, the incremental efforts in developing and deploying new applications is minimal-- saving time and money. No wonder we already have 60+ ecosystem partners!

In summary, the building automation industry is undergoing a massive transformation and Current has built a platform to help it leapfrog forward. I am excited to be a part of this technology movement and look forward to continuing to share our process.
