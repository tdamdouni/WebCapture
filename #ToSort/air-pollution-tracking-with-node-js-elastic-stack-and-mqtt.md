# Air Pollution Tracking With Node.js, Elastic Stack, and MQTT

_Captured: 2018-03-13 at 16:29 from [dzone.com](https://dzone.com/articles/air-pollution-tracking-with-nodejs-elastic-stack-and-mqtt?edition=366236&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-03-13)_

What can you do with a couple of IoT devices, Node.js, Elasticsearch, and MQTT? You can put together your own Internet of Things setup for measuring air pollution, like I have. In this blog post, I'll share all the details about the hardware setup, software configuration, data analytics, an IoT dashboard, and MQTT broker-based integration with other tools from the IoT ecosystem, like Node-Red and Octoblu. Of course, I'll also share a few interesting findings about air pollution IoT sensor measurements taken at a few locations in Germany. Take a look - doing this is _much_ easier than you might think when you use the right tools!

## **Motivation**

Recently, the[ Volkswagen Emission Scandal](https://en.wikipedia.org/wiki/Volkswagen_emissions_scanda) (Wikipedia) escalated again. Reasons were controversial animal experiments, as[ reported by The New York Times](https://www.nytimes.com/2018/01/30/opinion/animal-experiment-volkswagen.html). This sparked numerous debates about [banning Diesel cars from city centers in Germany](http://abcnews.go.com/Health/wireStory/german-court-issue-verdict-diesel-ban-case-53381726), where I live. People talk about global car bans, but I'm amazed nobody is really talking about smart-city concepts yet. Besides the discussion around the cheating on nitrogen oxide emissions, the EU wants to enforce lower limits of [particulates](https://en.wikipedia.org/wiki/Particulates) (measured in [PM10 and PM2.5](https://www.epa.gov/pm-pollution/particulate-matter-pm-basics)) in Germany. The impact on the health of high PM10 concentration is described in "[Health effects of particles in ambient air](https://www.sciencedirect.com/science/article/pii/S143846390470303X)".

Well, that is politics and medicine and we are computer scientists, data engineers, or DevOps specialists, so I asked myself

**"_What can we do for environmental protection_"? Living in a world where data-driven decisions are becoming more common, collecting data and visualizing facts is one way to contribute.**

As the recent scandal shows, large companies might influence scientific studies, lobbyists are influencing governments, so why not collect open source data and create independent analytics and _independent opinions_ based on open data - or your own data! We can help with recipes for device setups, software configuration or sharing data in a platform or analyzing data, help with the interpretation and we could speak about it in public, in meetups, conferences, etc.

As for me, I just wanted to see measurements in my environment because public government data lists only major cities and reports they provide typically have maps with low resolution. So I decided to start a little IoT DIY project with off-the-shelf components to measure the air pollution with a particular matter/dust sensor, tracking the PM10, PM2.5, as well as the PM2.5/PM10 ratio values. I wanted to be able to do this with a mobile device and measure in various locations where I work and live. My office is close to the main street and close to an industrial area, but I recently moved into a new house in a rural town that feels like a "climatic spa" and actually has a health resort. To make it easy for others to put together Internet of Things systems like the one described here I created "[Air Pollution Tracker"](https://github.com/megastef/AirPollutionTracker), so anyone can collect data at their locations, experiment with the setup, and share their data.

## **The Hardware**

Ok, let's get technical and first see the hardware setup of the IoT sensor device I put together:

![](https://sematext.com/wp-content/uploads/2018/02/image10.png)

So that's what our setup looks like. Let's see what each part of this IoT sensor device is and does:

  * Measuring Particulate Matter with a Nova SDS011 dust sensor
  * Logging the location of the measurement with a GPS sensor
  * Wi-Fi connection to my mobile phone to transmit measurement results via MQTT
  * A power bank provides the power for the Banana Pi device
  * [Banana Pi](https://en.wikipedia.org/wiki/Banana_Pi) (more powerful than [Raspberry Pi](https://www.raspberrypi.org/)) with Debian Linux and [Node.js](https://nodejs.org/) for data collection and shipping of the sensor data

Note that the USB power might not be sufficient for GPS, Wi-Fi, PM sensor, and an internal Ethernet interface.

## **The Software**

The software architecture is based on [MQTT](https://en.wikipedia.org/wiki/MQTT) messages, which is designed to scale to thousands of devices and supports an easy way of sharing data in real-time for any kind of processing. We created [open source plugins](https://sematext.com/docs/logagent/plugins/) for [@sematext/logagent](https://github.com/sematext/logagent-js) in Node.js to collect and correlate data from _Nova SDS011_ sensor and the GPS device. The measurements are shipped in JSON format to an MQTT broker, which can store data in Elasticsearch or, as we did, in [Sematext Cloud](https://sematext.com/cloud/). The MQTT-based architecture allows other clients to listen to the event stream and create e.g. alerts or public tweets or control traffic lights when PM10 limits are reached. In addition, the MQTT messages are recorded for historical analysis and visualization.

![](https://sematext.com/wp-content/uploads/2018/02/image11.png)

> _Architecture_

## **Sniffing Fresh Air and Collecting Data From PM Sensor**

The project started with a Google search for particulate matter sensors and availability of the device and Node.js drivers because Node.js is my favorite programming language. After some research I ordered the _Nova SDS011_ with USB to serial converter. Reading values from serial port looked easy to implement, and the USB interface works on my MacBook and the Banana Pi device. The next step was creating an input plugin for [@sematext/logagent](https://sematext.com/logagent/) to inject the sensor data in the Logagent processing pipeline. Logagent can ship data to MQTT, Elasticsearch, Apache Kafka, or simple file output.

I wanted to measure air quality in multiple locations, so I needed to collect the location of measurements. This would let me visualize air pollution on a map. The initial approach was to add a static location information to the plugin configuration, but then I changed things to get the location information from other sources, like GPS or by tracking my iPhone. The [Logagent plugin for the Nova SDS011 sensor](https://www.npmjs.com/package/logagent-novasds) is open source and published in the NPM registry. The Logagent configuration for the Nova SDS011 plugin requires the module name and the name of the serial port. Optionally, you can specify the measurement collection frequency using the workingPeriod setting in minutes:

## **Getting Accurate GPS Position**

After the setup of the serial port driver and Logagent, the first experiments started on my MacBook. To get accurate GPS position when changing places I wanted to track my location automatically. At first, I used the Logagent plugin [logagent-apple-location](https://www.npmjs.com/package/logagent-apple-location) to track the position of my iPhone. To do that I had to extend the PM sensor plugin to listen to the "_location_" events to enrich the sensor data with GPS coordinates and retrieved address. That was a good start for experiments until my new GPS device finally arrived and I switched to using [logagent-gps](https://www.npmjs.com/package/logagent-gps) plugin to get accurate GPS positions independently from internet connectivity. When the internet connection is present, the plugin queries Google Maps API to find the address of the current location and uses a cache to avoid hitting the Google API limit quickly. The downside of the cache is the loss of accuracy. With the cache in place the street numbers and addresses don't change within a few hundred meters distance. The configuration for the Logagent GPS plugin is very simple. It needs only the COM port for the serial interface and the npm module name:

## **Calculating Values From Sensor Measurements**

Smaller particles are considered more dangerous and therefore it might be interesting to see the ratio of PM10 and PM2.5 values. The Nova SDS011 provides only PM10 and PM2.5 measurements, and the ratio of PM2.5/PM10 needs to be calculated. Please note that the mass of PM2.5 particles is a subset of PM10 particles. Therefore the PM2.5 value is always smaller than the PM10 value. [Logagent supports JavaScript functions](https://sematext.com/docs/logagent/filters/#output-filter) for input and output filters in the configuration file, so that is what we used here.

The "data" variable holds the current measurement values and the callback function needs to be called to return the modified data object after the calculation. The new data object contains now PM10, PM2.5 and the calculated PM25ratio values!

## **Shipping and Consuming Sensor Data With MQTT**

The standardized MQTT protocol has a very small overhead and most IoT tools support MQTT. MQTT works with pub/sub mechanisms to distribute messages to multiple clients. In our case, the sensor device sends JSON messages to the MQTT broker using the topic called "sensor-data". We use the [Logagent MQTT output plugin](https://sematext.com/docs/logagent/output-plugin-mqtt/) and the public service mqtt://test.mosquitto.org. Please note that you should use the test.mosquitto.org server only for short tests. For a production setup you should run your own MQTT broker. For example, you could run [Mosquito MQTT broker in a Docker container](https://hub.docker.com/_/eclipse-mosquitto/) or you could use the [Logagent MQTT-broker plugin](https://sematext.com/docs/logagent/input-plugin-mqtt-broker/) and run another instance of Logagent as an MQTT broker.

Now we could use any MQTT client on another machine, connected to the same MQTT broker and subscribe to messages arriving in the "sensor-data" topic.

If you want to process measurements in some way or act on them you can use tools like[ Node-Red](https://nodered.org/) or[ Octoblu](https://octoblu.github.io/) and create IoT workflows. For example, the MQTT plugin in Node-Red takes MQTT broker address and topic as parameters, so you can use that to subscribe to that "sensor-data" topic and get measurements that were sent to the MQTT broker As soon you start Node-Red pointed to the MQTT broker you will get the air pollution data into your Node-Red workflow. Then you perform various actions on or based on received measurements. For example, you could tweet messages when conditions match or change the color of LED lights according to the sensor values, or you could control air conditioning … the possibilities are endless here! Thinking a little bigger, a smart-city might choose to control the traffic and use air pollution as one of the criteria for traffic routing decisions. The Node-Red architecture can plug devices, logic elements, or [neural network](https://flows.nodered.org/node/node-red-contrib-neuralnet) components. Node-Red is a great playground to prototype any logic based on the air pollution measurements.

![](https://sematext.com/wp-content/uploads/2018/02/image8.png)

> _Node-Red IoT workflows_

## **Storing Data in Elasticsearch or Sematext Cloud**

We stored what is effectively IoT time-series sensor data via [Logagent Elasticsearch plugin ](https://sematext.com/docs/logagent/output-elasticsearch/)directly in Sematext Cloud. Sematext Cloud provides Elasticsearch API compatible endpoints for data, dashboards, and alerts. The Elasticsearch plugin needs the Elasticsearch URL and index name. For Sematext Cloud we use the write token provided by Sematext UI as index name:

## **The Complete Device Setup for Banana Pi**

The setup for the Banana Pi device in a few steps:

  1. Create Bananian (Debian) SD card
  2. Configure Wi-Fi card for your mobile phone by setting the wpa_-_essid and the wpa_-password_ in _/etc/network/interfaces_ for the wlan0 interface. Enable the Internet tethering on your mobile phone ("Hotspot" on iPhone).
  3. Install Node.js
  1. Install @sematext/logagent and relevant plugins

Copy the working configuration to _/etc/sematext/logagent.conf_ and start the service with

## **CPU and Memory Footprint**

A lot of what I do at Sematext has to do with performance monitoring, so I couldn't help myself and had to look at the telemetry of this DIY IoT setup of mine. The low resource usage of the Node.js based Logagent with less than 1% CPU and less than 34 MB memory is impressive! Other logging tools like Logstash require 20 times more memory (600 MB+) and would use most of the resources on microcomputers like Banana Pi or Raspberry Pi and exhaust the battery in no time!

![](https://sematext.com/wp-content/uploads/2018/02/image1.png)

If you're curious about performance like I am, but also if you want to be notified when there are performance or stability issues with your setup you may want to add the [logagent-nodejs-monitor](https://github.com/megastef/logagent-nodejs-monitor) plugin as shown below. Finally, we complete the configuration with the collection of all device logs with the file input plugin. The log files in /var/log contain valuable information like Wi-Fi status or USB device information.

We restart Logagent to apply configuration changes:

After a few seconds, we will see logs and metrics in the Sematext UI. Having performance metrics and logs in one view is really valuable for any kind of troubleshooting. In my case, the USB wire had a bad contact and the lost USB connection was logged in /var/kern.log (see screenshot).

![](https://sematext.com/wp-content/uploads/2018/02/image4.png)

> _Node.js performance metrics and Banana Pi logs in Sematext Cloud_

## **Visualizing the Air Pollution**

Before we create visualisations, we need to know the data structure of messages produced by the sensor/logagent. We could easily draw numeric values as a date histogram such as _PM10, PM2_5 _and _PM25ratio_. Maps can be created with the geo-coordinates. Having the address of each measurement makes it easy to find measurements in a specific city and the hostname might help us identify the sensor device.

_Example JSON message stored in Elasticsearch / Sematext Cloud_

To visualize all data I've used Kibana, which is integrated in Sematext Cloud. Once the visualisations are created in Kibana, we can create a dashboard showing map and sensor values. At a first glance we can immediately see that air pollution is 50% lower in the north (where I live), than in the office that is close to the main street.

![](https://sematext.com/wp-content/uploads/2018/02/image13.png)

> _Kibana Dashboard in Sematext Cloud_

## **Observation of Particulate Matter concentrations in various scenarios**

The following graph was recorded while travelling from my office location to my home. The spike in graph happened when I stopped my car and took the measurement device out of the car. You can see that the PM10 value jumped for a short time up to **80 µg/m³**, which is double the EU limit of 40 µg/m³ average per year, though just for a minute. Good to know that the air in my hometown has only half of the particulate matter compared to the office location - at least as long I don't start my diesel engine … anyhow a good reason to stay in the home office.

![](https://sematext.com/wp-content/uploads/2018/02/image5.png)

![](https://sematext.com/wp-content/uploads/2018/02/image3.png)

> _ PM10 levels in Weiskirchen (orange) and Nalbach (red) _

## **Environment.on("smog", alert)**

Having dashboards is cool, but you can't really watch a dashboard all day long. So let's use alerts. The open source ELK stack has its limits - no built-in alerting - but we can use alerts in Sematext Cloud. Here a saved query, filtering only PM10 values greater than 40 (EU limit) or 50 (DE limit) is used to trigger alerts:

![](https://sematext.com/wp-content/uploads/2018/02/image14.png)

> _Setup Alert for PM10 values above 50._

![](https://sematext.com/wp-content/uploads/2018/02/image12.png)

> _Alert notification in Sematext UI_

With such an alert in place, we can add the Event stream (screenshot above) with alerts to a dashboard(screenshot below) and receive alerts via Slack channel on the mobile phone, for example.

![](https://sematext.com/wp-content/uploads/2018/02/image15.png)

> _Dashboard in Sematext UI, including Alert notifications_

![](https://sematext.com/wp-content/uploads/2018/02/image2.png)

> _Slack notification when PM10 reaches the configured threshold of PM10>40 or PM10>50_

## **Conclusion**

The costs of various sensor devices are low and assembling the gadgets and setting up the software could be done in literally a few hours. It took me much longer to find good solutions for various tiny problems and to code a few [Logagent plugins](https://sematext.com/docs/logagent/plugins/), but even scripting a plugin module takes only a few hours. Using [Sematext Cloud](https://sematext.com/cloud) instead of a local ELK stack is a big time saver for the server setup (I don't need any physical or cloud servers, just devices and Sematext SaaS). The alerting for Elasticsearch queries and forwarding of alerts to Slack made the solution complete.

The biggest source of satisfaction in this project was to make the invisible visible with the "electronic nose" - you feel like a Ghostbuster! You see PM10 values increasing when a window gets opened, or when you start to vacuum the living room or when you forget your spaghetti on the stove while programming … Outside sensors "smell" when a neighbour starts his car engine, a visitor parks his car in front of your house, a guest starts smoking a cigarette on the terrace…

An interesting fact is that PM10 values are higher close to the main street and actually reached the EU limit (PM10>40) and the German limit (PM10>50) during rush hour in front of my office! The maximum value measured was PM10=69 at my office window. The PM10 values decrease as close as a few hundred meters away from the main street. Think about how being aware of this could impact your life decisions - a move to a new flat or office could really impact your health. Knowing the time of the highest air pollution could also help to keep particles out of your flat. My measurement showed that airing the office room before 2 p.m. and after 9 p.m. would be best to keep the PM concentration low. Luckily, I recently moved to a small village and the good thing I can find here is fresh air and, as you can see, inspiration and time for fresh ideas!

The real surprise to me was that I ended up in politics by calling the city administration for an appointment with the mayor to discuss with him a traffic light, which switches to red once the PM10 limit is reached. Cars could be kept out of the town because a bypass road already exists, but is currently underutilized and should be used much more. I hope I get my appointment with the mayor scheduled soon and when I speak with him I will have data to back up my suggestions. The administration first asked for a written letter to give me an official statement - let's see if we get one more Smart-City on this planet finally making data-driven decisions applied in real-life, and not only in business Stay tuned!
