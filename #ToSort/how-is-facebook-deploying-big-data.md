# How is Facebook Deploying Big Data?

_Captured: 2017-02-07 at 20:41 from [dzone.com](https://dzone.com/articles/how-is-facebook-deploying-big-data?edition=267885&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-07)_

### How Facebook harnessed Big Data by mastering open source tools, and in some cases developing their own.

Learn how you can [maximize big data in the cloud](https://dzone.com/go?i=177153&u=http%3A%2F%2Fhortonworks.com%2Finfo%2Fmaximize-big-data-cloud-aws-ebook%2F%3Futm_medium%3Dsponsored-content%26utm_source%3Ddzone%26utm_campaign%3Daws) with Apache Hadoop. Download this eBook now. Brought to you in partnership with [Hortonworks.](https://dzone.com/go?i=177153&u=http%3A%2F%2Fhortonworks.com%2Finfo%2Fmaximize-big-data-cloud-aws-ebook%2F%3Futm_medium%3Dsponsored-content%26utm_source%3Ddzone%26utm_campaign%3Daws)

If Facebook were a country, it would be the most populous nation on earth. Running in its 11th year of success, Facebook stands today as one of the most popular social networking sites, comprising of 1.59 billion accounts, which is approximately the 1/5th of the world's total population. Launched in the year 2004, it has grown tremendously since then. With a sudden obsession in social media, the number of people on Facebook has increased enormously, producing a massive amount of data every minute.

Every time you open your Facebook account, on an average you notice more than 10 new news feed items, 5 notifications, 10 messages, and two friend requests. Surprised, right? Then this is what you need to know that what Facebook does with this data.

## Growing Big With Big Data

There is no doubt that Facebook is one of the largest Big Data specialists, dealing with petabytes of data, including historical and real-time, and will keep growing in the same horizon. While the world is coming closer together on this platform, Facebook develops algorithms to track those connections and their presence on or outside its walls to fetch the most suitable posts for its users. Whether it is your wall post, your favorite books, movies, or your workplace, Facebook analyzes each and every bit of your data and offers you better services each time you log in.

## Star Performers Working Behind Facebook's Big Data

There is a combined workforce of people and technology constantly working behind the successful implementation of this platform. Though the platform is continuously being enriched, below are the prime technological aspects:

### Hadoop

"Facebook runs the world's largest Hadoop cluster" says Jay Parikh, Vice President Infrastructure Engineering, Facebook.

Basically, Facebook runs the biggest Hadoop cluster that goes beyond 4,000 machines and storing more than hundreds of millions of gigabytes. This extensive cluster provides some key abilities to developers:

  * The developers can freely write map-reduce programs in any language.
  * SQL has been integrated to process extensive data sets, as most of the data in Hadoop's file system are in table format. Hence, it becomes easily accessible to the developers with small subsets of SQL.

Hadoop provides a common infrastructure for Facebook with efficiency and reliability. Beginning with searching, log processing, recommendation system, and data warehousing, to video and image analysis, Hadoop is empowering this social networking platform in each and every way possible. Facebook developed its first user-facing application, Facebook Messenger, based on Hadoop database, i.e., Apache HBase, which has a layered architecture that supports plethora of messages in a single day.

### Scuba

With a huge amount of unstructured data coming across each day, Facebook slowly realized that it needs a platform to speed up the entire analysis part. That's when it developed **Scuba**, which could help the Hadoop developers dive into the massive data sets and carry on ad-hoc analyses in real-time.

Facebook was not initially prepared to run across multiple data centers and a single break-down could cause the entire platform to crash. Scuba, another Big data platform, allows the developers to store bulk in-memory data, which speeds up the informational analysis. It implements small software agents that collect the data from multiple data centers and compresses it into the log data format. Now this compressed log data gets compressed by Scuba into the memory systems which are instantly accessible.

According to Jay Parikh, "Scuba gives us this very dynamic view into how our infrastructure is doing -- how our servers are doing, how our network is doing, how the different software systems are interacting."

### Cassandra

> "The amount of data to be stored, the rate of growth of the data, and the requirement to serve it within strict SLAs made it very apparent that a new storage solution was absolutely essential."   
\- Avinash Lakshman, Search Team, Facebook 

The traditional data storage started lagging behind when Facebook's search team discovered an Inbox Search problem. The developers were facing issues in storing the reverse indices of messages sent and received by the users. The challenge was to develop a new storage solution that could solve the Inbox Search Problem and similar problems in the future. That is when Prashant Malik and Avinash Lakshman started developing **Cassandra**.

The objective was to develop a distributed storage system dedicated to managing a large amount of structured data across multiple commodity servers without failing once.

### Hive

After Yahoo implemented Hadoop for its search engine, Facebook thought about empowering the data scientists so that they could store a larger amount of data in the Oracle data warehouse. Hence, Hive came into existence. This tool improved the query capability of Hadoop by using a subset of SQL and soon gained popularity in the unstructured world. Today almost thousands of jobs are run using this system to process a range of applications quickly.

### Prism

Hadoop wasn't designed to run across multiple facilities. Typically, because it requires such heavy communication between servers, clusters are limited to a single data center.

Initially when Facebook implemented Hadoop, it was not designed to run across multiple data centers. And that's when the requirement to develop Prism was felt by the team of Facebook. Prism is a platform which brings out many namespaces instead of the single one governed by the Hadoop. This in turn helps to develop many logical clusters.

This system is now expandable to as many servers as possible without worrying about increasing the number of data centers.

### Corona

Developed by an ex-Yahoo man Avery Ching and his team, Corona allows multiple jobs to be processed at a time on a single Hadoop cluster without crashing the system. This concept of Corona sprouted in the minds of developers, when they started facing issues with Hadoop's framework. It was getting tougher to manage the cluster resources and task trackers. MapReduce was designed on the basis of a pull-based scheduling model, which was causing a delay in processing the small jobs. Hadoop was limited by its slot-based resource management model, which was wasting the slots each time the cluster size could not fit the configuration.

Developing and implementing Corona helped in forming a new scheduling framework that could separate the cluster resource management from job coordination.

### Peregrine

Another technological tool that is developed by Murthy was Peregrine, which is dedicated to addressing the issues of querying data as quickly as possible. Since Hadoop was developed as a batch system that used to take time in running different jobs, Peregrine brought the entire process close to real-time.

Apart from the above prime implementations, Facebook uses many other small and big sized pieces of technology to support its Big Data infrastructure, such as Memcached, Hiphop for PHP, Haystack, Bigpipe, Scribe, Thrift, Varnish, etc.

Today Facebook is one of the biggest corporations on earth thanks to its extensive data on over one and a half billion people on earth. This has given it enough clout to negotiate with over 3 million advertisers on its platform in order to clock staggering revenues that is north of 17 Billion US Dollars. But the privacy and security concerns still loom large regarding whether Facebook will utilize all that gargantuan volumes of data to server humanity's greater good or just use it to make more money.

But one thing is for sure, it is Big Data indeed that has propelled Facebook, a small-time Harvard dorm startup into the constellation of some of the biggest corporations on earth of all times!

Hortonworks DataFlow is an integrated platform that makes data ingestion fast, easy, and secure. [Download the white paper now](https://dzone.com/go?i=133024&u=http%3A%2F%2Fhortonworks.com%2Finfo%2Fdata-ingestion%2F%3Futm_medium%3Dsponsored-content%26utm_source%3Ddzone%26utm_campaign%3Ddata-ingestion). Brought to you in partnership with [Hortonworks](https://dzone.com/go?i=133024&u=http%3A%2F%2Fhortonworks.com%2Finfo%2Fdata-ingestion%2F%3Futm_medium%3Dsponsored-content%26utm_source%3Ddzone%26utm_campaign%3Ddata-ingestion).
