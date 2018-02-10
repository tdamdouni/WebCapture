# Comparing Publish-Subscribe Messaging and Message Queuing

_Captured: 2018-02-09 at 20:20 from [dzone.com](https://dzone.com/articles/comparing-publish-subscribe-messaging-and-message?edition=355134&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202018-02-08)_

[Modernize your application architectures with microservices and APIs](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) with best practices from this free virtual summit series. Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Building the data pipelines that move data from where it is created to all of the different places that it is processed is a fundamental part of designing and implementing data-driven applications. Messaging is a critical technology for connecting data in this environment.

In the data processing domain, messaging is the transmission of data records from one system to another via an intermediate system. In contrast to direct connections, where senders know the receivers to which data will be sent and connect directly to each receiver, messaging solutions decouple the sending of data from data consumption. Senders do not know which receivers will see that data or when they will see it.

Messaging solutions help simplify application development by providing a standardized, reusable component for robustly handling the data flows, enabling developers and architects to focus on the core logic of applications. In addition to routing data, messaging systems can also provide capabilities for logging, distributed processing, flow control and resiliency to improve performance, scalability, manageability, and reliability.

Messaging is a broad term that covers several models that differ based on how data is moved from senders to recipients. There are two primary categories of messaging models: message queuing and publish-subscribe (often referred to as pub-sub) messaging.

## Message Queuing

Message queuing is designed for scenarios such as a task list or work queue. A message queue receives incoming messages and ensures that each message for a given topic or channel is delivered to and processed by exactly one consumer. An example scenario is issuing paychecks-it is critical that every paycheck is issued once and only once, but it does not matter which exact processor issues each check.

![Message queuing example scenario](https://streaml.io/img/message-queuing.png)

> _Message queuing example scenario._

Message queues can support high rates of consumption by adding multiple consumers for each topic, but only one consumer will receive each message on the topic. Which consumer receives which message is determined by the implementation of the message queue. To ensure that a message is only processed by one consumer, each message is deleted from the queue once it has been received and processed by a consumer (i.e. once a consumer has acknowledged consumption of the message to the messaging system).

Message queues support use cases where it is important that each message is processed (and only processed once), but it is not necessary to process messages in order. For example, in the case of network or consumer failures, the message queue will try resending an affected message at a later time (not necessarily to the same consumer) and as a result, that message may be processed out of order.

## Publish-Subscribe Messaging

Like message queuing, publish-subscribe (commonly referred to as "pub-sub") messaging moves information from producers to consumers. However, in contrast to message queuing, publish-subscribe messaging allows multiple consumers to receive each message in a topic. Further, pub-sub messaging ensures that each consumer receives messages in a topic in the exact order in which they were received by the messaging system.

![Publish-subscribe messaging example](https://streaml.io/img/pub-sub-messaging.png)

> _Publish-subscribe messaging example._

Publish-subscribe messaging systems can support use cases in which multiple consumers receive each message and/or that messages are received in order by each consumer. For example, a stock ticker service can be used by a large number of people and applications, all of whom want to receive all messages (e.g. prices at which stock trades occur) on their topics of choice. It is important for these users that they receive messages in order-seeing a high price followed by a low price for a stock means something very different from seeing a low price followed by a high price.

Publish-subscribe use cases are frequently associated with stateful applications. Stateful applications care about the order of messages received because the ordering of messages determines the state of the application and will, as a result, impact the correctness of whatever processing logic the application needs to apply.

## Technology Options

Not surprisingly, given how fundamental messaging is to data-driven applications, there are a number of technologies that support some form of message queuing, publish-subscribe messaging, or both.

Technologies such as [Apache ActiveMQ](https://activemq.apache.org/), [Amazon SQS](https://aws.amazon.com/sqs/), [IBM Websphere MQ](https://en.wikipedia.org/wiki/IBM_WebSphere_MQ), [RabbitMQ](https://en.wikipedia.org/wiki/RabbitMQ), and [RocketMQ](https://rocketmq.apache.org/) were initially designed primarily for message queuing use cases. Other technologies such as [Apache Kafka ](https://kafka.apache.org/)and [Google Cloud Pub/Sub](https://cloud.google.com/pubsub/) were designed primarily to support publish-subscribe use cases. Other, often newer solutions such as [Apache Pulsar](https://pulsar.apache.org/) provide support for both [message queuing and pub-sub messaging](https://streaml.io/blog/pulsar-streaming-queuing).

Determining which technology is the best fit for a particular use case requires understanding the essential requirements for that use case--for example whether ordering is important and whether multiple consumers need to process each message. Each technology brings a different set of features and optimizations that need to be evaluated based on those requirements. Also important to evaluating technology options is understanding the ease of application development, performance, resiliency, and operational demands associated with the different technologies and how they are deployed.

The Integration Zone is proudly sponsored by [CA Technologies](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Learn from expert microservices and API presentations at the [Modernizing Application Architectures Virtual Summit Series](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
