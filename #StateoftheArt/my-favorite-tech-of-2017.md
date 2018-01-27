# My Favorite Tech of 2017

_Captured: 2017-12-15 at 09:51 from [dzone.com](https://dzone.com/articles/favorite-tech-of-the-year-early-edition?edition=342156&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-14)_

[Find out how AI-Fueled APIs from Neura](https://dzone.com/go?i=244221&u=https%3A%2F%2Fhubs.ly%2FH08wTJ10) can make interesting products more exciting and engaging.

This has been a pretty awesome year for technology in the big data, streaming, IoT, deep learning, machine learning, AI, and device space.

I am going to give you my list of the top technology for 2017 and then give you a rundown on why I chose these technologies.

## **The List (Not in Order)**

  * SnappyData
  * DL4J
  * Apache NiFi 1.4 (especially QueryRecord)
  * Hortonworks Streaming Analytics Manager
  * Hortonworks Schema Registry
  * Movidius
  * Apache MXNet
  * Apache Spark 2.2
  * Matrix Creator
  * NVidia Jetson TX1 Developer Kit
  * Raspberry Pi (because of price, HATS, and community)
  * Apache MiniFi Java Agent
  * Apache SuperSet
  * Python
  * Apache Livy
  * Apache Hive LLAP
  * Druid
  * Apache Tika
  * spaCy
  * Apache OrC
  * NLTK
  * MQTT
  * GPS Sensors
  * OpenCV
  * MobileNets

## **Streaming**

For streaming, 2017 was an amazing year -- from updates on Apache Spark Streaming, Apache Flink, and Apache Storm to the introduction of Hortonworks Streaming Analytics Manager (on top of Apache Storm) to in-memory advances with SnappyData.

If you aren't running streaming code, now's the time to start. The on-ramp is simple; [Apache NiFi](https://nifi.apache.org/download.html) can be downloaded and run anywhere, including your laptop, easily and quickly. If you have the Java 8 JDK installed, you just have to run a command or shell and go to port 8080 and you can easily drag-and-drop your way to basic open-source Apache streaming.

One the things that is often forgotten in streaming is that for maximum speed, usability, versioning, 12-factor separation, messaging, Apache Kafka usage, Apache NiFi usage, and more -- you _need_ a schema. You need an open-source extensible registry with a slick web UI and REST API. Hortonworks Schema Registry fits the bill; it's part of the HDF install and available on GitHub and I hope it will be in the Apache Incubator next year. MQTT, Apache Kafka, and Apache NiFi S2S have been my go-to protocols for messaging. Assisting with streaming, Livy is now Apache and is working great for securely [integrating calls to Apache Spark from Apache NiFi and Apache Zeppelin](https://community.hortonworks.com/articles/73828/submitting-spark-jobs-from-apache-nifi-using-livy.html).

## **Analytics**

This has been the year of Apache SuperSet, which joined Apache and has wowed me with its easy and fast analytics and dashboards. Now that it's Apache and a full member of Hortonworks Data Platform with Druid, it's really powering up some cool streaming analytics. If you haven't tried this powerful combination yet, it's a must.

Apache Hive LLAP, with its super fast queries on huge data, combined with Druid, is a killer query environment. This will be _the_ way to query in 2018. The only way to store data this year is Apache ORC (Parquet is a close second but doesn't give you that superb Hive LLAP performance).

## **Devices/IoT**

This has been the year of devices. The edge is getting AI power. Movidius pumps up your Pi with VPU power. Matrix Creator adds a ton of sensors in one Pi Hat. And Google released a really cool cheap voice kit (another kit for vision before year-end). You add AndroidThings, and Google is really enabling devices and -- on the cheap.

Microsoft, NVidia and Amazon are doing similar things. Movidius is part of Intel, so you now have interesting chips coming out from ARM, Intel, and NVidia. The NVidia Jetson TX series has been amazing, with a developer-only super deal on the Jetson TX1 camera. I have been loving my TX1 with its big RAM (4GB), 256 Cuda cores, and fast Ubuntu. Bolt came out and looks like a cool little inexpensive platform. Having cameras, GPS, GPU, hundreds of sensors, big RAM, and MobileNets available in makers' hands is great.

And it was another great year for Raspberry Pi, with some OS updates and lots of sensors, HATS, and libraries. RPI is the standard others have to think about. I did like the Nano Pi Duo, Bolt, Libre Computer, and others -- but the size factor and community around RPI are unbeatable. My hope is that they can come out with a higher-end RPI for more enterprise use with 4GB RAM, a GPU, and more storage.

## **Deep Learning/Machine Learning/AI**

The updates to deep learning have been legion! Almost every day, there's been an update, a new library, a new example, or a new combined approach. All the major players -- Amazon, Microsoft, Google, Apple, Facebook -- are in the game. Some are coming to Apache like the excellent and now 1.0 Apache MXNet, while the enterprise-solid DL4J went to the Eclipse foundation (which also got some goodness around Java 9).

If you are not investigating deep learning, start now -- we have many articles here at [DZone](https://dzone.com/users/297029/bunkertor.html). My [TensorFlow Refcard](https://dzone.com/refcardz/introduction-to-tensorflow) came out this year, so check that out, too. If you haven't yet added object detection and image recognition to your suite of applications running on your corporate distributed YARN cluster, now is the time to start!

OpenCV is awesome and is being combined with machine learning and deep learning for awesome computer vision applications. This is a must-install that utilizes utility on devices, desktops, and distributed clusters.

SpaCY is a really cool library for Python that is quickly evolving. I had a lot of fun with it this year. Also, NLTK got some updates and again proved to be great.

Apache Tika has been very useful in many projects and for helping out some DL and ML apps.

In the drone space, I liked the Kudrone that I got this year, though there have been some growing pains with that.

On every single device, I install Apache MiniFi Java Agentunless it is really tiny -- then, it's Apache MiniFi C++ agent. The ability to control how I send and orchestrate data securely makes this the only tool I use with devices. It's so much easier than MQTT, plus you get logging, standard processors, flows, data provenance, security, updates, and a lot more. It's a no-brainer.

## **Wrapping Up**

The one common thread between these technologies lies in community, projects available on GitHub, and fun things to do with them.

I really wish Apache Avro supported more naming types. Not having dots, spaces, and dashes is causing me some headaches.

![Image title](https://dzone.com/storage/temp/7449701-samsetup.png)

In fact, because of the lack of naming options, I created a [custom Apache NiFi processor](https://github.com/tspannhw/nifi-attributecleaner-processor) to handle that.

This was the year of Apache, open-source, big data, and cool projects working together.

![Image title](https://dzone.com/storage/temp/7449700-samrunning.png)

## ***The* Technology of the Year**

Drumroll... Apache NiFi 1.4 is my choice. I use it everywhere. It's my Swiss Army Knife for everything from mobile apps to web apps to REST APIs to streaming to messaging to exporting data to reading RDBMS to backups to running ML to running DL to ingesting data to Hadoop. This is my everyday tool, and it got even better this year with records and schemas.

Thanks to Joe Witt and the Apache NiFi team for making this the project to use for everything, everywhere. It even powers my little Christmas Trees!

![Image title](https://dzone.com/storage/temp/7489841-trees3.jpg)

![Image title](https://dzone.com/storage/temp/7489847-matrixcreator1.jpg)

Where is Apache NiFi? It's on my OSX laptop, my Ubuntu Dell Inspiron, my eight raspberry Pis, my odd devices, my Jetson TX1, every enterprise app, my phone, my truck... it is everywhere. I am even powering my DJ gear and Fortune 50 Enterprise applications with it.

Thanks, Apache! And Happy Holidays, friends! See you at a [meetup](https://www.meetup.com/futureofdata-princeton/)

To find out how AI-Fueled APIs can increase engagement and retention, [download Six Ways to Boost Engagement for Your IoT Device or App with AI](https://dzone.com/go?i=244222&u=https%3A%2F%2Fhubs.ly%2FH08wTJ50) today.

Topics:

machine learning ,deep learning ,drones ,data streaming ,ai ,apache nifi ,iot devices ,big data analytics

Opinions expressed by DZone contributors are their own.
