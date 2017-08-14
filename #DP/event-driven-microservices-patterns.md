# Event Driven Microservices Patterns

_Captured: 2017-08-05 at 23:10 from [dzone.com](https://dzone.com/articles/event-driven-microservices-patterns?edition=313394&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-05)_

Share, secure, distribute, control, and monetize your APIs with the platform built with performance, time-to-value, and growth in mind. [Free 90-day trial](https://dzone.com/go?i=231226&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Ftechnologies%2Fjboss-middleware%2F3scale%2Fget-started%3Fsc_cid%3D701f2000000h30LAAQ) of 3Scale by Red Hat

In this blog, we will discuss some patterns which are often used in microservices applications which need to scale:

  * Event Stream
  * Event Sourcing
  * Polyglot Persistence
  * Memory Image
  * Command Query Responsibility Separation

## The Motivation

[Uber](https://eng.uber.com/soa/), [Gilt](https://www.infoq.com/presentations/scale-gilt), and others have moved from a monolithic to a microservices architecture because they needed to scale. A monolithic application puts all of its functionality into a single process, scaling requires replicating the whole application, which has limitations.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture1.png)

Sharing normalized tables in a clustered RDBMS does not scale well because distributed transactions and joins can cause concurrency bottlenecks.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture2.png)

The [microservice architectural style](https://martinfowler.com/articles/microservices.html) is an approach to developing an application as a suite of small independently deployable services built around specific business capabilities. [A microservices approach is well aligned to a typical big data deployment](http://ostatic.com/blog/q-a-maprs-jack-norris-on-the-impact-of-microservices). You can gain modularity, extensive parallelism and cost-effective scaling by deploying services across many commodity hardware servers. Microservices modularity facilitates independent updates/deployments, and helps to avoid single points of failure, which can help prevent large-scale outages.

## Event Stream

When moving from a monolithic to a microservices architecture a common architecture pattern is event sourcing using an append only event stream such as Kafka or MapR Streams (which provides a Kafka 0.9 API) . With MapR Streams (or Kafka) events are grouped into logical collections of events called Topics. Topics are partitioned for parallel processing. You can think of a partitioned Topic like a queue, events are delivered in the order they are received.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture3.png)

Unlike a queue, events are persisted, even after they are delivered they remain on the partition, available to other consumers.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture4.png)

Older messages are automatically deleted based on the Stream's time-to-live setting, if the setting is 0 then they will never be deleted.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture5.png)

Messages are not deleted from Topics when read, and topics can have multiple different consumers, this allows processing of the same messages by different consumers for different purposes. Pipelining is also possible where a consumer enriches an event and publishes it to another topic.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture6.png)

## Event Sourcing

[Event Sourcing](https://martinfowler.com/eaaDev/EventSourcing.html) is an architectural pattern in which the state of the application is determined by a sequence of events each of which is recorded in an append-only Event store or Stream. As an example, imagine that each "event" is an incremental update to an entry in a database. In this case, the state of a particular entry is simply the accumulation of events pertaining to that entry. In the example below the Stream persists the queue of all deposit and withdrawal events, and the database table persists the current account balances.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture7.png)

Which one of these, the Stream or the Database, makes a better system of record? The events in the Stream can be used to reconstruct the current account balances in the Database, but not the other way around. Database replication actually works by suppliers writing changes to a change log, and consumers applying the changes locally. Another well-known example of this is a source code version control system.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture8.png)

With a Stream, events can be re-played to create a new view, index, cache, [memory image](https://martinfowler.com/bliki/MemoryImage.html), or materialized view of the data.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture9.png)

The Consumer simply reads the messages from the oldest to the latest to create a new View of the data.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture10.png)

> _There are several advantages for modeling application state with streams:_

  * **Lineage**: to ask how did BradA's balance get so low?
  * **Auditing**: it gives an audit trail, who deposited/withdrew from account id BradA? This is how accounting transactions work.
  * **Rewind**: to see what the status of the accounts was last year.
  * **Integrity**: can I trust the data hasn't been tampered with? 
    * yes because Streams are immutable.

[The Replication of MapR Streams](https://mapr.com/documentation/v5.1.0/MapR_Streams/replicating_streams.html) gives a powerful testing and debugging technique. A replica of a Stream can be used to replay a version of events for testing or debugging purposes.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture11.png)

## Different Databases and Schemas for Different Needs

There are lots of databases out there, and each [uses different technologies depending on how the data is used](http://martinfowler.com/bliki/PolyglotPersistence.html), optimized for a type of write or read pattern: graph query, search, document... What if you need to have the same set of data for different databases, for different types of queries coming in? The Stream can act as the distribution point for multiple databases, each one providing a different read pattern. All changes to application state are persisted to an event store which is the system of record. The event store provides rebuilding state by re-running the events in the stream.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture12.png)

Events funnel out to databases which are consumers of the stream. [Polyglot persistence](https://mapr.com/products/polyglot-persistence) provides different specialized materialized views.

## CQRS

[Command and Query Responsibility Segregation (CQRS)](https://martinfowler.com/bliki/CQRS.html) is a pattern that separates the read model and Queries from the write model and Commands often using event sourcing. Let's look at how an online shopping application's item rating functionality could be separated using the CQRS pattern. The functionality, shown below in a monolithic application, consists of users rating items they have bought, and browsing item ratings while shopping.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture13.png)

In the CQRS design shown below, we isolate and separate the Rate Item write "command" from the Get Item Ratings read "query" using event sourcing. Rate Item events are published to a Stream. A handler process reads from the stream and persists a materialized view of the ratings for an item in a NoSQL document-style database.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture14.png)

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture15.png)

## NoSQL and De-Normalization

With [MapR-DB](https://mapr.com/products/mapr-db-in-hadoop-nosql) a table is automatically partitioned across a cluster by key range, and each server is the source for a subset of a table. Grouping the data by key range provides for really fast read and writes by row key. With MapR-DB you [design your schema so that the data that is read together is stored together](https://mapr.com/blog/guidelines-hbase-schema-design).

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture16.png)

Often with MapR-DB, you de-normalize or store in one table what would be multiple tables in a normalized relational database. If your entities exist in a one-to-many relationship, it's possible to model it in MapR-DB HBase as a single row or MapR-DB JSON as a single document. In the example below, the item and related ratings are stored together and can be read together with a single get on the indexed row key. This makes the reads a lot faster than joining tables together.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/17b.png)

## Event Sourcing: New Uses of Data

An advantage of using an Event Stream for the rate item and other shopping related events is shown here. This design lets us use this data more broadly. Raw or enriched events can be stored in inexpensive storage such as [MapR-FS](https://mapr.com/products/mapr-fs). Historical ratings data can be used to build a machine learning model for [recommendations](https://mapr.com/blog/inside-look-at-components-of-recommendation-engine). Having a long retention time for data in the queue is also very useful. For example, that data could be processed to build a collection of shopping transaction histories stored in a data format such as Parquet that allows very efficient querying. Other processes might use historical data and streaming shopping related events with machine learning to [predict shopping trends](http://www.forbes.com/sites/bernardmarr/2015/11/10/big-data-a-game-changer-in-the-retail-sector/#3bae52a1678a), to [detect fraud](https://mapr.com/blog/real-time-credit-card-fraud-detection-apache-spark-and-event-streaming), or to build a real-time display of where transactions are happening.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture18.png)

## Fashion Retailer's Event Driven Architecture

A major fashion retailer wanted to increase in-season agility and inventory discipline in order to react to demand changes and reduce markdowns. The Event driven solution architecture is shown below:

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture19.png)

  * Weather, world events, and logistical data is collected in real time via [MapR Streams](https://mapr.com/products/mapr-streams), allowing for real time analysis of potential logistical impacts, and rerouting of inventory.
  * [Apache Spark](https://mapr.com/products/apache-spark) is used for batch and streaming analytics processing, and machine learning for predicting supply chain disruptions, and product recommendations.
  * Data is stored in [MapR-DB](https://mapr.com/products/mapr-db-in-hadoop-nosql) providing scalable, fast reads and writes. [Apache Drill](https://mapr.com/products/apache-drill) is used for interactive exploration and preprocessing of the data with a schema-free SQL query engine.
  * ODBC with Drill provides support for existing BI tools.
  * MapR's Enterprise capabilities provide for global data center replication.

## Summary

In this blog post, we discussed event driven microservice architecture using the following design patterns: [Event Sourcing,](http://martinfowler.com/eaaDev/EventSourcing.html)[ Command Query Responsibility Separation](http://martinfowler.com/bliki/CQRS.html), and [Polyglot Persistence](http://martinfowler.com/bliki/PolyglotPersistence.html). All of the components of the architectures we discussed can run on the same cluster with the MapR Converged Data Platform.

![](https://mapr.com/blog/event-driven-microservices-patterns/assets/otherpageimages/2817blog/picture20.png)

## References and More Information

Explore the core elements of owning an API strategy and best practices for effective API programs. [Download](https://dzone.com/go?i=231227&u=https%3A%2F%2Fengage.redhat.com%2F3scale-api-owners-s-201706160312%3Fsc_cid%3D701f2000000h30LAAQ) the API Owner's Manual, brought to you by 3Scale by Red Hat
