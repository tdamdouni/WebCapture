# How IoT Big Data is Going to the Dogs

_Captured: 2017-03-22 at 21:58 from [mapr.com](https://mapr.com/blog/how-iot-big-data-going-dogs/)_

![](https://mapr.com/en/blog/how-iot-big-data-going-dogs/assets/thinkstockphotos-497617058.jpg)

## Send Your Data Streams to the "Dogs"

The [Internet of Things (IoT)](https://mapr.com/solutions/enterprise/internet-of-things), with its ubiquitous sensors and streams of big data for big insights, has an estimated market valuation of $1.7 trillion. Apparently, the "sensoring" of the world is a seriously big deal, generating insights into people, processes, and products on a scale that is almost incomprehensible. Certainly, $1.7 trillion is almost an incomprehensible figure. The corresponding forecasts for data-driven insights that lead to such a valuation are expected to be on a similarly large scale to justify those astronomical projections.

But insights are not hardcoded within Raspberry Pi or Arduino kits, though IFTTT (If-This-Then-That) kits might be a satisfactory solution (more about that later). Insights begin with ubiquitous data collection (via the tens of billions of connected devices that will be measuring, monitoring, and tracking nearly everything). Those vast streams of data represent the very essence of big data: "[everything being quantified and tracked](https://mapr.com/blog/big-data-everything-quantified-and-tracked-what-means-you)." But that is not the same thing as insights. So how do we transition from petascale data collection to massive-scale value and insights?

The answer to this question is simple: **send your big data to the dogs!**

Why dogs? Because dogs are perfect sensors, sorters, and sentries.

For example, a dog's sense of hearing is sensitive to frequencies beyond the range of human hearing. Consequently, they can detect signals that humans miss, even identifying specific signals amidst all of the noise that fills the air.

Second, dogs have an incisive sense of sorting out (disambiguating and classifying) different smells. They can be trained to sniff out bombs, illegal drugs, and even specific people based only on a fragment of their clothing, despite the vast mix of smells, odors, and scents that permeate the world. There are stories of dogs that have identified their prior owners after many years of separation simply by sniffing them. Dogs have even found their way back to their owners across hundreds of miles of separation.

Third, dogs make great sentries (also called sentinels). They are able to sound the alarm and alert us when something unusual, unexpected, and/or undesirable is happening around us. They can be trained to know when to sound an alarm ("danger approaching") and when not to sound an alarm ("friends approaching").

Well, of course, I do not actually mean that you should give your IoT data to real dogs. But I do mean that you should send your data streams to analytics sentinels that have those same special characteristics of dogs: keen sensing of different types of signals in "noisy" environments, sharp sorting out (disambiguation and classification) capabilities, and intelligently trainable to learn different rules (classifiers) in response to different inputs and thereby to emit actionable alerts to humans (or other devices). The sentinels that I am referring to are [machine learning algorithms](https://mapr.com/blog/some-important-streaming-algorithms-you-should-know-about) that intercept and analyze the data streaming from IoT devices: "digitally and analytically sniffing your IoT data streams."

What are some of the things that we expect our machine learning sentinels to do, particularly in IOT applications? We expect them to detect events in the data streams, to learn what classes of events can occur, to classify new events, and to alert us appropriately. That last step involves triage based on a set of business rules that define which events are informational only, which events are important (actionable) but not urgent, and which events need an urgent response. This is where [IFTTT architectures and recipes](https://ifttt.com/recipes/collections/32-recipes-for-the-internet-of-things) can be very helpful--they can be "wired" to respond to specific events, signals, or conditions, and then to take specific actions (update a database, send an alert, store the information for later distribution, collect more data from this event, or move on to the next thing).

## The Four Fundamental Unsupervised Learning Techniques

But there is more. The above business scenarios focus on known events that involve the application of basic supervised machine learning (classification) techniques. There may also be previously unseen behaviors in your data streams, which therefore require unsupervised machine learning techniques. The four fundamental unsupervised learning techniques are:

  1. **Class discovery** - find the classes, partitions, and clusters of events and behaviors that are represented in your data streams, and then learn the defining boundaries (in the feature parameter space) that separate and distinguish the different classes (so that future instances of such events can be classified according to those rules).
  2. **Correlation discovery** (or predictive power discovery) - find the trends, correlations, and patterns of behavior in your data streams that enable the deployment of predictive and prescriptive analytics models.
  3. [Association (link) discovery](https://mapr.com/blog/association-rule-mining-%E2%80%93-not-your-typical-data-science-algorithm) - find the unusual (non-random) co-occurring associations and linkages among different objects, events, and behaviors in your data streams that become explanatory and predictive for future events in your domain.
  4. [Novelty (surprise) discovery](https://mapr.com/blog/n-novelty-detection-and-news-few-my-favorite-data-science-things) (sometimes called outlier detection) - find the rare (one-of-kind) unexpected "unknown unknowns" in your data streams that may indicate sensor (hardware) problems, data quality (software) issues, or totally new discoveries (the real valuable surprises in your domain).

**_IF_** your sentinels detect an interesting signal, and if **_THIS_** signal represents an actionable insight, **_THEN_** you can program your analytics system to take the appropriate action **_THAT_** is best for your organization (based on the business rules coded into the algorithm)--that is the essence of **_IFTTT_** (If-This-Then-That) for discovering and extracting fast business value from your streaming IoT big data.

These sentinels (machine learning algorithms and their accompanying business rules) will be most effective if they are located at the edge of the network, at the point of data collection (or near thereto), and therefore not relegated to high-latency batch processing. Low-latency is a key requirement for IOT analytics. Embedding the sentinel (analytics algorithm) within the sensor or data collector enables faster sense-making, insights, response, and value, which is essential when data is being acquired at an enormous rate.

## Key Takeaways

So, before we panic at the impending explosion of data streaming from our billions of ubiquitous devices in the [Internet of Everything era](https://mapr.com/cito-internet-everything-era), let us put some sentinels on duty. Put these machine learning "dogs" (analytics algorithms) to the task of taking us from data collection through data analytics to data understanding (insight and value). Only then can we hope to realize the promised trillion-dollar market value of the IoT.

To help you get there, MapR offers a variety of solutions and platforms that you can bring to the data, including:

  * [MapR Streams](https://mapr.com/products/mapr-streams) in a [converged data platform](https://mapr.com/products/mapr-converged-data-platform), designed for speedy data integration and machine learning
  * Distributed data clusters with [Apache Hadoop](https://mapr.com/products/apache-hadoop) to manage the rich variety of data, and time-series databases
  * Low-latency schema-on-read query and exploration across many data sets with [Apache Drill](https://mapr.com/products/apache-drill)
