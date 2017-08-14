# Fast Cars, Big Data: How Streaming Data Can Help Formula 1

_Captured: 2017-07-28 at 17:47 from [dzone.com](https://dzone.com/articles/fast-cars-big-data-how-streaming-data-can-help-for?utm_source=Top%205&utm_medium=email&utm_campaign=Top%205%202017-07-283)_

A Formula 1 race is a high-speed example of the Internet of Things, where gathering, analyzing, and acting on tremendous amounts of data in real time is essential for staying competitive. The sport's use of such information is so sophisticated that some teams are exporting their expertise to other industries, even for use on [oil rigs](http://fortune.com/2015/11/12/big-data-formula-1-championship-race/). Within the industry, [automobile companies such as Daimler and Audi are leveraging deep learning on the MapR Converged Data Platform to successfully analyze the continuous data generated from car sensors](http://www.marketwired.com/press-release/norcom-selects-mapr-to-accelerate-deep-learning-in-autonomous-driving-applications-2212053.htm).

This blog discusses a proof of concept demo, which was developed as part of a pre-sales project to demonstrate an architecture to capture and distribute lots of data, really fast, for a Formula 1 team.

## What's the Point of Data in Motor Sports?

Formula 1 cars are some of the most heavily instrumented objects in the world.

![Picture1](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture1.png)

> _Read more about The Formula 1 Data Journey_

Formula 1 data engineers analyze data from ~150 sensors per car, tracking vital stats such as [tire pressure, fuel efficiency](https://www.forbes.com/sites/frankbi/2014/11/13/how-formula-one-teams-are-using-big-data-to-get-the-inside-edge/), wind force, GPS location, and brake temperature in real time. Each sensor communicates with the track, the crew in the pit, a broadcast crew on-site, and a second team of engineers back in the factory. They can transmit [2GB of data in one lap and 3TB in a full race](https://channels.theinnovationenterprise.com/articles/f1-and-data-analytics-it-s-a-numbers-game).

![Picture2](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture2.png)

> _Watch WSJ's video "The F1 Big Data Explainer"_

Data engineers can make sense of the car's speed, stability, aerodynamics, and tire degradation around a race track. The graph below shows an example of what is being [analyzed by race engineers: rpm, speed, acceleration, gear, throttle, brakes, by lap](http://f1framework.blogspot.com/2013/08/short-guide-to-f1-telemetry-spa-circuit.html).

![Picture3](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture3.png)

More analysis is also completed at the team's manufacturing base. Below is an example race strategy, analyzing whether it would be faster to do a pit stop tire change at lap 13 and lap 35 vs. lap 17 and lap 38.

![Picture4](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture4.png)

## The Challenge: How Do You Capture, Analyze, and Store This Amount of Data in Real Time at Scale?

The 2014 U.S. Grand Prix collected more than 243 terabytes of data in a race weekend, and now there is even more data. Formula 1 teams are looking for newer technologies with faster ways to move and analyze their data in the cockpits and at the factory.

Below is a proposed proof of concept architecture for a Formula 1 team:

![Picture5](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture5.png)

[MapR Edge](https://mapr.com/products/edge) in the cars provides an on-board storage system that buffers the most recent data and retries when transmission fails. MapR Edge addresses the need to capture, process, and provide backup for data transmission close to the source. A radio frequency link publishes the data from the edge to the referee _"FIA"_ topic, and from there it is published to each team's topic, where local analytics is done. The _"team engineers"_ Stream replicates to the _"trackside"_ and _"factory"_ Streams, so that the data is pushed in real time for analytics. In a sport where seconds make a difference, it's crucial that the trackside team can communicate quickly with the engineers at headquarters and team members around the world. [MapR Streams replication provides an unusually powerful way to handle data across distant data centers at large scale and low latency](https://mapr.com/blog/multi-master-replication-geo-distributed-data/).

## The Demo Architecture

The demo architecture is considerably simplified because it needs to be able to run on a single node MapR sandbox. The demo does not use real cars; it uses the [Open Racing Car Simulator (TORCS)](http://torcs.sourceforge.net/), a race car simulator often used for AI race games and as a research platform.

![Picture6](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture6.png)

The demo architecture is shown below. Sensor data from the TORCS simulator is published to a MapR Streams topic using the Kafka API. Two consumers are subscribed to the topic. One Kafka API consumer, a web application, provides a real-time dashboard using websockets and HTML5. Another Kafka API consumer stores the data in MapR-DB JSON, where analytics with SQL are performed using Apache Drill. You can download the demo code here:<https://github.com/mapr-demos/racing-time-series>.

![Picture7](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture7.png)

## How Do You Capture This Amount of Data in Real Time at Scale?

Older messaging systems track message acknowledgements on a per-message, per-listener basis. A new approach is needed to handle the volume of data for the Internet of Things.

![Picture8](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture8.png)

[MapR Streams](http://mapr.com/products/mapr-streams/) is a distributed messaging system that enables producers and consumers to exchange events in real time via the Apache Kafka 0.9 API. In MapR Streams, topics are logical collections of messages, which organize events into categories and decouple producers from consumers.

![Picture9](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture9.png)

Topics are partitioned for throughput and scalability. Producers are load balanced between partitions, and consumers can be grouped to read in parallel from multiple partitions within a topic for faster performance.

![Picture10](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture10.png)

You can think of a partition like a queue; new messages are appended to the end, and messages are delivered in the order they are received.

![Picture11](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture11.png)

Unlike a queue, events are not deleted when read; they remain on the partition, available to other consumers.

![Picture12](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture12.png)

A key to high performance at scale, in addition to partitioning, is minimizing the time spent on disk reads and writes. [With Kafka and MapR Streams, messages are persisted sequentially as produced and read sequentially when consumed. These design decisions mean that non-sequential reading or writing is rare, allowing messages to be handled at very high speeds with scale](https://mapr.com/streaming-architecture-using-apache-kafka-mapr-streams/). Not deleting messages when they are read also allows processing of the same messages by different consumers for different purposes.

![Picture13](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture13.png)

## Example Producer Using the Kafka API

Below is an example producer using the Kafka Java API. For more information, see the [MapR Streams Java applications documentation](http://maprdocs.mapr.com/home/MapR_Streams/MapRStreamsJavaApplications.html).

![Picture14](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture14.png)

## How to Store the Data

One of the challenges, when you have 243 terabytes of data every race weekend, is where do you want to store it? With a relational database and a normalized schema, related data is stored in different tables. Queries joining this data together can cause bottlenecks with lots of data. For this application, [MapR-DB JSON](http://maprdocs.mapr.com/home/MapR-DB/developing_client_applications_for_mapr_db.html) was chosen for its scalability and flexible ease of use with JSON. MapR-DB and a denormalized schema scale, because data that is read together is stored together.

![Picture15](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture15.png)

> _With MapR-DB (HBase API or JSON API), a table is automatically partitioned across a cluster by key range, providing for really fast reads and writes by row key._

![Picture16](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture16.png)

## JSON Schema Flexibility

JSON facilitates the natural evolution of your data schema during the life of your application. For example, in version 1, we have the following schema, where each JSON message group sensors values for Speed, Distance, and RPM:

For version 2, you can easily capture more data values quickly without changing the architecture of your application, by adding attributes as shown below:

As discussed before, MapR Streams allows processing of the same messages for different purposes or views. With this type of architecture and flexible schema, you can easily create new services and new APIs-for example, by adding Apache Spark Streaming or an Apache Flink Kafka Consumer for in-stream analysis, such as aggregations, filtering, alerting, anomaly detection, and/or machine learning.

![Picture17](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture17.png)

## Processing the Data With Apache Flink

[Apache Flink](https://flink.apache.org/) is an open source distributed data stream processor. Flink provides efficient, fast, consistent, and robust handling of massive streams of events as well as batch processing, a special case of stream processing. Stream processing of events is useful for filtering, creating counters and aggregations, correlating values, joining streams together, machine learning, and publishing to a different topic for pipelines.

![Picture18](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture18.png)

The code snippet below uses the `FlinkKafkaConsumer09` class to get a DataStream from the MapR Streams _"sensors"_ topic. The DataStream is a potentially unbounded distributed collection of objects. The code then calculates the average speed with a time window of 10 seconds.

![Picture19](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture19.png)

![Picture20](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture20.png)

## Querying the Data With Apache Drill

[Apache Drill](https://mapr.com/products/apache-drill/) is an open source, low-latency query engine for big data that delivers interactive SQL analytics at petabyte scale. Drill provides a [massively parallel processing execution engine](https://mapr.com/blog/apache-drill-architecture-ultimate-guide/), built to perform distributed query processing across the various nodes in a cluster.

![Picture21](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture21.png)

With Drill, you can use SQL to query and join data from files in JSON, Parquet, or CSV format, Hive, and NoSQL stores, including HBase, MapR-DB, and Mongo, without defining schemas.

Below is an example query to 'show all' from the race car's datastore :

And the results:

![Picture22](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture22.png)

> _Below is an example query to show the average speed by car and race:_

And the results:

![Picture23](https://mapr.com/blog/fast-cars-fast-data-formula1/assets/Picture23.png)

All of the components of the use case architecture that we just discussed can run on the same cluster with the MapR Converged Data Platform.

## Software

You can download the code and instructions to run this example from here: <https://github.com/mapr-demos/racing-time-series>.

## Additional Resources

[MapR Edge](https://mapr.com/products/edge) product information

Ebook: [Data Where You Want It: Geo-Distribution of Big Data and Analytics](https://mapr.com/geo-distribution-big-data-and-analytics/)

Ebook: [Streaming Architecture: New Designs Using Apache Kafka and MapR Streams](https://mapr.com/ebooks/streaming-architecture/)

Free [Apache Flink Ebook](https://mapr.com/ebooks/intro-to-apache-flink/)
