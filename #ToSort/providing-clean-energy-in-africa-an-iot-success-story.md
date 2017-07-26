# Providing Clean Energy in Africa: An IoT Success Story

_Captured: 2017-05-07 at 18:07 from [dzone.com](https://dzone.com/articles/providing-clean-energy-in-africa-an-iot-success-story?oid=twitter&utm_content=buffer9440d&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

I am always amazed at how technology is transforming the energy industry, but this IoT use case was particularly inspiring because we are making a profound difference in the lives of hundreds of thousands of children in Africa. InfluxDB is part of the solution at BBOXX (pronounced "BeeBox") as it provides affordable, clean solar energy to off-grid communities in the developing world.

![Clear Energy BBOXX and InfluxData](https://dzone.com/storage/temp/5186714-20150318103609-lighting-africa.jpg)

Consider life in one of these communities where the dominant source of light is from burning kerosene, creating soot and toxic fumes that permeate the home as the family sits together and the children try to study. Clearly, there is a better way, and BBOXX created an elegant solution -- a solar powered "Battery Box" that sits in an individual's home to power lights and appliances like TVs, lights, and mobile phones. the name is short for "Battery Box." [Read the case study for more details. ](https://marketing.influxdb.com/acton/attachment/16929/f-009b/1/-/-/-/-/CustomerCaseStudyBBOXX.pdf?utm_campaign=dzone&utm_medium=partner&utm_source=dzone&utm_content=&utm_term=)Now families can spend quality time together in a smoke-free environment.

This solution would not be possible just a few years ago:

  * The price of solar cells would have made this cost prohibitive.

  * Battery technology was not as energy efficient as today.

  * Sensors were not widely available and databases didn't exist that could handle the volume of time series data needed to monitor and control millions of data points per second.

  * Cellular technology for remote connectivity was sparsely deployed.

## Sensor Monitoring Key to the IoT Platform

Technology has evolved and BBOXX has been able to overcome these limitations. In particular, let's drill down into one part of their IoT Platform: the need for a storage, visualization, and analytics engine that can handle the volume of the metrics and events that were generated. They chose InfluxData's platform including InfluxDB as their sensor monitoring engine for its ability store, visualize, and perhaps, more importantly, analyze the millions of sensor reading in real-time. The goal is to use this data to improve the customer experience, expand their product offerings, and become a data-driven enterprise.

For instance, when looking at Battery performance one might be tempted to just stop at a simple graph showing power consumption over time.

![Time Series Data - InfluxData](https://dzone.com/storage/temp/5186735-screen-shot-2017-05-04-at-84224-am.png)

> _Time Series Data - InfluxData_

## Turning Sensor Monitoring into Action with Predictive Analytics

But what BBOXX really wanted to do was use the data to predict battery failures (predictive maintenance), before the failure occurred.

> "There is a strong correlation between a working system and a paying customer!" \-- David McLean, a senior developer at BBoxx 

![Predictive Maintenance with InfluxData](https://dzone.com/storage/temp/5186738-screen-shot-2017-05-04-at-85917-am.png)

> _Predictive Maintenance with InfluxData_

The system creates a proactive alert to the customer service team to dispatch a new battery before the system fails. This whole move from monitoring to alerting and eventually to control, where the system can automatically ship the battery, for instance, is a trend we see across our IoT monitoring customer base.

### Data-Driven Business

The goal at BBOXX was to become a data-driven business. Not that all this sensor and metric data is in InfluxDB, but they can analyze all data across their customer base. This analysis has proven some unexpected insights: Take this graph that shows the massive BBOXX usage during soccer match (AFCON qualifying match)

![Image title](https://dzone.com/storage/temp/5186737-screen-shot-2017-05-04-at-94530-am.png)

### Business Implication

Increase sales by creating compelling incentives for customers to get their products before major events and increase battery capacity on units to handle peak demand. InfluxData has allowed BBOXX to become more of a data-driven business, something that will provide competitive differentiation for years to come.

## Socio-Economic Results

While BBOXX's business results are impressive, the socio-economic results are also awe-inspiring:

  * Offset 40,000 tons of CO2.

  * $2.4 million in savings.

  * Generated 4 GW-hrs of energy.

  * And most importantly, more than 63,000 school aged children can now study comfortably without straining their eyes or destroying their lungs

We at [InfluxData](https://www.influxdata.com/) could not be happier that we play an important part in the work BBOXX is doing to change the world and we would love to hear how you are using our technology to make a difference.
