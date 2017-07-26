# Technical Solutions for IoT

_Captured: 2017-03-01 at 21:06 from [dzone.com](https://dzone.com/articles/technical-solutions-for-iot?edition=273881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-01)_

To gather insights on the evolution of IoT to this point in 2017, we spoke to 19 executives who are familiar with the current state of the Internet of Things.

We asked them, "What are the technical solutions being used to implement IoT?" Here's what they told us:

  * Most are dropping data into their **existing architecture whether its PostgreSQL, SQL**, **MongoDB, or Cassandra** because it's what they have. Others are looking at **AWS Green Grass, Dynamo DB, Kafka, Spark, and MQTT**. There are bigger opportunities in time series with data from sensors. Able to summarize, extrapolate, and predict.
  * **Start with a data queue at the edge.** Have an actor pulling data from the queue. Have streaming work transformation with real-time queries and a data lake for storage. Realize data has gravity and a life cycle - begin in the cloud, end in the lake.
  * **How to mix product lifecycle management (PLM) and asset lifecycle management (ALM)**. You need continuous improvement. Wi-Fi routers provide awful updating experiences. We need to be servicing in the field with automatic updates like Nest and Tesla.
  * Typically using **AWS or Azure**. AWS has a better application infrastructure. It takes more work to develop an Azure platform. Everyone needs sensors for measuring defects, consumption, et.al. Build from the ground up to provide the data of value to the manufacturer.
  * **Using different databases to hold data**. Afraid of personally identifiable information (PII) glitches.
  * **Private clouds.**
  * **No single platform is emerging because there are a series of vertical markets with different problems to solve**. These require different platforms and architectures to deliver business value. Medical devices are different than connected cars are different from controllers on an industrial factory floor. All do involve connectivity and need to focus on security. As you go through the maturity model with a fleet of connected devices, the challenge of managing business solutions becomes greater.
  * **Tying consumers to devices** with extension core open ID and other existing protocols on the identification side.
  * Move from batch to real-time processing. **Use JSON self-describing data types**. Deal with exploration and manipulation natively. Apache Drill to query directly.
  * We have very tech savvy clients. They are integrating IoT devices with web applications. Given the concern around security, they are doing this themselves to **maintain control at a granular level.**
  * Standards like **Wi-Fi, ZigBee and Bluetooth** have been around for many years and are excellent ways of wirelessly connecting devices. Wi-Fi works fine for high-data rate, wide-bandwidth devices that have a good source of power. If you can plug them in or can easily recharge the batteries, Wi-Fi works fine for streaming video, gaming, high-quality audio, speech, etc. Bluetooth is already in most phones and is an excellent way of connecting devices that don't need networking and can operate on batteries--it is ideal for wearables. ZigBee is a proven technology for connecting a houseful of devices that can utilize networking to talk to each other and to a central hub or gateway. ZigBee connected sentrollers (sensors, controllers, and actuators) can provide a robust and reliable network that can be powered by batteries or even by energy harvesting.
  * Varies by client. Want to see ROI. Most common is the use of **Alexa**. All the systems are disparate and integration is an issue.
  * Our customers typically use a big data store for data injection and storage, e.g. MongoDB or Hadoop. Our solutions sits on top of those solutions to transform the data collected into business applications (e.g., turning time stamp data into time, day, shift (AM/PM)), or classifying with business terms (e.g., mobile transactions by location, storefront,or zip code, based on latitude and longitude data). Our analytics and visualizations are designed for business users. For example, we have insurance agents that using our solutions to gauge car use and frequency for quoting insurance premiums. We also offers machine learning and predictive analytics to make recommendations about what action the customer should take next.

What technical solutions are you using to implement your IoT strategy?

And in case you're curious, here's who we talked to:

  * Scott Hanson, Founder, and CTO, [Ambiq Micro](http://ambiqmicro.com/)
  * Adam Wray, CEO and Peter Coppola, SVP, Product Marketing, [Basho](http://basho.com/)
  * Farnaz Erfan, Senior Director, Product Marketing, [Birst](https://www.birst.com/)
  * Shahin Pirooz, CTO, [Data Endure](https://www.dataendure.com/)
  * Anders Wallgren, CTO, [Electric Cloud](http://electric-cloud.com/)
  * Eric Free, SVP Strategic Growth, [Flexera](https://www.flexerasoftware.com/)
  * Brad Bush, Partner, [Fortium Partners](https://www.fortiumpartners.com/#about)
  * Marisa Sires Wang, Vice President of Product, [Gigya](http://www.gigya.com/?gclid=CPGnjMm5n9ICFREdgQod6b0P1w)
  * Tony Paine, Kepware Platform President at PTC, [Kepware](https://www.kepware.com/en-us/?gclid=CM3Ho9m5n9ICFQwZgQodYEMLng)
  * Eric Mizell, Vice President Global Engineering, [Kinetica](http://www.kinetica.com/)
  * Crystal Valentine, PhD, V.P. Technology Strategy and Jack Norris, S.V.P., Database Strategy and Applications, [MapR](https://www.mapr.com/)
  * Pratibha Salwan, V.P. Digital Services Americas, [NIIT Technologies](https://www.niit-tech.com/)
  * Guy Yehaiv, CEO, [Profitect](http://www.profitect.com/)
  * Cees Links, general manager Wireless Connectivity, [Qorvo](http://www.qorvo.com/)
  * Paul Turner, CMO, [Scality](http://www.scality.com/)
  * Harsh Upreti, Product Marketing Manager, API, [SmartBear](https://smartbear.com/)
  * Rajeev Kozhikkuttuthodi, Vice President of Product Management, [TIBCO](http://spotfire.tibco.com/)

Opinions expressed by DZone contributors are their own.
