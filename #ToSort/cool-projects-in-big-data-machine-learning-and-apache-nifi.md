# Cool Projects in Big Data, Machine Learning, and Apache NiFi

_Captured: 2017-01-30 at 23:00 from [dzone.com](https://dzone.com/articles/cool-projects-big-data-machine-learning-apache-nifi?edition=266885&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-30)_

This week, data is becoming knowledge as all streams of data are converging and leading me to the conclusion that every business is in need of the same types of data, tools, and results. From payment processing to media to rentals to retail to finance to big pharma, the same problems are coming up of "How do I ingest all kinds of data (variety), constantly changing (agile), often broken (flexible, schemaless or schema flexible), do some transformations in stream and land it in my big data environment (Hadoop with some flavors of NoSQL or data warehouse (SAP HANA or SQL Server+ or Oracle X) on the side)?"

Oh and it's got to be fast, scalable, easy to use, and have a UI that can be used by my intern/data engineers. Some of the data is coming from IoT devices, cameras, beacons, web logs, Twitter, Facebook, 3rd party paid feeds, free feeds from NOAA, government and partner data sources, and legacy systems.

So what can support text files, JSON, JMS, MQTT, REST, XML, MongoDB, S3 and a host of sources and formats? Only Apache NiFi comes to mind. Think Big Analytics has given us a preview of February's amazing [Kylo](https://github.com/ThinkBigAnalytics/kylo-docs-test), an open source tool that works with Apache NiFi to add data wrangling and discovery features on-top. [Kylo](https://www.thinkbiganalytics.com/kylo2/) will be open source and the GitHub directory is built and ready for the first release. I will announce here on DZone when that comes out, as it will be a major boost for enterprises.

Getting started with Hortonworks [HDF](http://docs.hortonworks.com/HDPDocuments/HDF2/HDF-2.1.1/index.html) (Apache NiFi + Storm + Kafka) to ingest these formats is really easy, as I have shown in previous articles. If you are in the New Jersey area, come by our meetup and we'll be doing [hands-on training ](https://www.meetup.com/futureofdata-princeton/events/236924547/)with Apache NiFi. It's 100% open source and open for extension. I am working on a NiFi Processor for doing NLP tasks like Name recognition and Sentiment Analysis. For my current flows, I call Python scripts for NLTK, but in the processor I will be doing that with Apache [OpenNLP](http://opennlp.apache.org/) and Java 8.

Preview header from that open source processor:

![Image title](https://dzone.com/storage/temp/4124789-hdf.png)

[Sentiment](http://irds.usc.edu/SentimentAnalysisParser/index.html)[Analysis Parser for USC Data Science](https://github.com/USCDataScience/SentimentAnalysisParser), combines Apache Tika and Apache OpenNLP, a really powerful combination, be warned that the maven build will take some serious power to run and will take a while. Perhaps hours depending on your machine, so run this before heading out to a long lunch.

Oliver Meyn has written a pretty amazing [article](https://elephant.tech/spark-2-0-streaming-from-ssl-kafka-with-hdp-2-4/) on using Spark 2.0 Streaming with SSL, Kerberos, Kafka and hosted on HDP 2.4 YARN. It includes all the build scripts, configuration and source code for you to be able to do this. Code can easily be adapted to HDP 2.5 and Spark 2.1, very nice.

## **Great Links of the Week**

  * 52 Technologies from 2016, great documenation and code in this [GitHub](https://github.com/shekhargulati/52-technologies-in-2016/blob/master/README.md) including Sentiment Analysis.

  * [Huge Open Data](https://deeplearning4j.org/opendata) resources from Deep Learning 4 J.

  * You can never have enough data for testing and for a constant stream of data, Twitter is usually your only option. But what if you want a different schema of data? Try [ACES, Inc.'s JSON Data Generator](https://github.com/acesinc/json-data-generator), well documented with full source code, run it locally and get a nice stream of JSON data.

  * A cool class going on right now [CS224n](http://web.stanford.edu/class/cs224n/): Natural Language Processing with Deep Learning, course materials will be provided online for free as they are available.

  * Another Stanford class I will be watching closely is [CS20SI](https://web.stanford.edu/class/cs20si/): Tensorflow for Deep Learning Research ([GitHub](https://github.com/chiphuyen/tf-stanford-tutorials)).

## **Deep Learning Presentations of Note**
