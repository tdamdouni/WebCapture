# Is Your Stream Processor Obese?

_Captured: 2018-06-27 at 19:06 from [dzone.com](https://dzone.com/articles/is-your-stream-processor-obese?edition=383268&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-27)_

While selecting tools for our systems, we often look up to Google, which runs an impressive system with scale and availability we can only dream of. Google's use cases are, however, different from ours. As Ozan Onay starts his article "[You are not Google](https://blog.bradfieldcs.com/you-are-not-google-84912cf44afb)," the designs used by large digital businesses, such as Google, are pleasing to the eye and look impressive to fellow architects, but they have a higher total cost of ownership and are filled with [YAGNI (you aren't gonna need it) features](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it). There is "[scale-envy](https://en.wikipedia.org/wiki/Physics_envy)" at work.

Consequently, development teams sometimes select tools and deployments that scale too well. Unfortunately, those systems provide much less performance per unit than some less scalable systems. For example, assume your system needs 5K TPS (transactions per second). You might choose to build a system that can scale to 50K TPS even if such a load is unlikely, leading to over-engineering. The truth is that a 10X load is a good problem to have if it ever happens since it will likely bring in 10X more revenue as well. However, at that point, you can afford to replace everything. There's no need to waste resources upfront on an unlikely scenario.

As more companies turn to stream processing, the tendency to over-engineer is once again rearing its head. Even a simple deployment tends to incorporate six or more servers. This article discusses the factors that typically lead to larger deployments, effective lower-footprint alternatives, and decision criteria on how to choose the right approach.

## High Availability Drives Stream Processing Bloat

A primary factor driving stream processing deployments is the fact that high availability (HA) and recoverability from failures are indispensable features for most stream processing use cases. Since stream processing applications run forever without stopping, they must fail eventually when the inevitable system crash happens. When they do fail, the application's state (e.g. data in a window) will be lost unless the application is highly-available and recoverable.

The best-known approach for achieving HA is to use a Zookeeper distributed coordinator service. The system keeps a consistent view across all nodes and takes snapshots. If one node fails, other nodes can continue the processing. This approach is used in most well-known stream processors, such as Apache Storm, Apache Flink, and Apache Samza. However, because a minimal, highly available, and recoverable deployment with the Zookeeper approach requires a minimum of five nodes, these systems present a weakness in anything less than a large deployment.

Let's get into the details for Flink, Storm, and Samza. The main culprit is Zookeeper, where a setup needs 3-5 nodes [1] and the minimal HA setup is 3 nodes.

Apache Flink: A minimal setup, as per their docs [[2]](https://ci.apache.org/projects/flink/flink-docs-release-1.3/setup/jobmanager_high_availability.html#standalone-cluster-high-availability), will require 6 or more nodes, including:

  * 3 Zookeeper nodes.
  * 2 job managers without Apache Hadoop YARN and 1 job manager with YARN.
  * Worker nodes.

Apache Storm: HA is possible with Nimbus and as per its docs [[3]](http://storm.apache.org/releases/current/nimbus-ha-design.html), a minimal deployment needs at least 7 nodes, including the following:

  * 3 Zookeeper nodes.
  * 2 Leaders.
  * Nimbus supervisor.
  * Worker nodes.

Apache Samza: Samza depends on Kafka, which depends on Zookeeper. As per the docs [[5]](https://www.cloudera.com/documentation/kafka/latest/topics/kafka_ha.html), Kafka needs three nodes. Hence, a Samza minimal deployment needs 5-8 nodes total, including:

  * 2 Samza nodes.
  * 3 Kafka nodes.
  * 3 Zookeeper nodes.

With these stream processors, even very small loads will require a 5- to 8-node deployment. Is it a big deal? Ask your DevOps team. After 3 nodes, the complexity of deployment and monitoring increases significantly. Managing such systems often demands dedicated resources that monitor those systems.

Unfortunately, many teams will only realize this at the last stage of their evaluation when they consider HA and recoverability. A single node version that they try in the quick start of each product does not have this problem. But it does not have HA or recoverability either. Unfortunately, by the time many users come to this realization, they have already invested both time and identity into the technology. So they rarely back out.

## A Lighter Approach to High Availability

A lesser-known approach to HA is to run two stream processors side by side as shown in the picture below. Both processors consume the same events. The master produces outputs and the slave discards its outputs. If the master fails, the slave already has all the information to continue and takes over as the master. With this approach, two servers can produce more than 50-100k events per second. The reason this is not well known is that it is not scalable beyond two nodes.

![HA with Hot-Warm Deployment](https://lh3.googleusercontent.com/JI_ATqmMK61pjU8KifJxGB-UiMGqnntSh-olTcg6DsNTB7z2zfR3ZbujoWhCGTzbj25R9IKNBTSbtVyIVDPe9-eJkJOqy7DP3r6MBh_pWhY8p9Dz5yVr84kzarrOoxytSp1-BNGP)

> _HA with Hot-Warm Deployment_

## A Rational Way to Make the Choice

Some organizations may require the scalability provided by the Zookeeper approach. However, many more enterprises will have use cases that are well served by running two stream processors in parallel.

To determine the right approach and size for your organization, first, approximate the load you are anticipating. In my years of working with Fortune 500 companies, I have rarely seen them handling a load that exceeds 5,000 TPS (assuming 157.68 billion messages per year with 1KB messages and 157TB of data).

Then think of a reasonable limit over which you can justify redoing the deployment. Often 3X more traffic means 3X new revenue, providing the necessary validation to update the deployment.

If you can handle the load and a reasonable multiple against the limit with two nodes, go for the side-by-side approach. Later, if you want to scale, a stream processor that supports the side-by-side HA approach can run on top of Kafka and scale just like other stream processors. You can start small and later switch to Kafka without changing any code. Chances are that you will save some serious money and have some peace of mind.

That said, there will be some cases where the high degree of scalability required will justify investing in the Zookeeper approach. The important thing is to look before you leap into a complex deployment with five-plus nodes.

I hope this was useful. I am a contributor to [WSO2 Stream Processor](https://wso2.com/analytics), which is an Apache-licensed, open source, stream processor. It can [process 100K+ events using two nodes with HA](https://docs.wso2.com/display/SP410/Performance+Analysis+Results). It's tuned for small and medium size use cases. Please check it out if you are interested. Notably, this is not the only stream processor that can do the same. See [this Quora Question](https://www.quora.com/How-is-stream-processing-and-complex-event-processing-CEP-different) for a list of other stream processing servers.

Dave Ramsey [notes](https://www.goodreads.com/quotes/25775-we-buy-things-we-don-t-need-with-money-we-don-t), "We buy things we don't need with money we don't have to impress people we don't like." But we don't have to keep feeding into that reality when a robust, lean alternative for high availability stream processing is readily available.

## References

  1. Deploying ZooKeeper, <https://hadoop.apache.org/docs/stable/hadoop-project-dist/hadoop-hdfs/HDFSHighAvailabilityWithNFS.html#Deploying_ZooKeeper>
  2. Flink: Standalone Cluster High Availability, <https://ci.apache.org/projects/flink/flink-docs-release-1.3/setup/jobmanager_high_availability.html#standalone-cluster-high-availability>
  3. Highly Available Nimbus Design, <http://storm.apache.org/releases/current/nimbus-ha-design.html>
  4. Apache Storm: Highly Available Nimbus Design, <https://scalr-wiki.atlassian.net/wiki/spaces/docs/pages/75071490/Deploying+a+Kafka+cluster>
  5. Configuring High Availability and Consistency for Apache Kafka, <https://www.cloudera.com/documentation/kafka/latest/topics/kafka_ha.html>
