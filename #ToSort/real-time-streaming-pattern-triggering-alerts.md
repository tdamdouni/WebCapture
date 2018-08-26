# Real-Time Streaming Pattern: Triggering Alerts

_Captured: 2018-07-14 at 14:24 from [dzone.com](https://dzone.com/articles/real-time-streaming-pattern-triggering-alerts?edition=385238&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=big%20data%202018-07-14)_

[Hortonworks Sandbox](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) for HDP and HDF is your chance to get started on learning, developing, testing and trying out new features. Each [download](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) comes preconfigured with interactive tutorials, sample data and developments from the Apache community.

## Introduction

This week, I will continue to look at data processing patterns used to build event triggered stream processing applications, the use cases that the patterns relate to, and how you would go about implementing this within Wallaroo.

This purpose of these posts is to help you understand the data processing use cases that Wallaroo is best designed to handle and how you can go about building them right away.

I will be looking at the Wallaroo application builder, the part of your application that hooks into the Wallaroo framework, and some the business logic of the pattern.

You should also check out my previous post, [Real-time Streaming Pattern: Preprocessing for Sentiment Analysis](https://dzone.com/articles/real-time-streaming-pattern-preprocessing-for-sent), which describes how to use Wallaroo to clean up data so that it ready for later processing stages.

## Pattern: Triggering Alerts

When you think about event triggered applications, sending an alert based on an event is one of the first things to come to mind.

The triggering alerts pattern involves monitoring a stream of even data and triggering some action when a threshold is reached.

You see this pattern implemented in a variety of applications. Some examples include:

  * Monitoring server infrastructure CPU utilization and sending an alert if a particular server's utilization goes above 90%.
  * Monitoring an IoT device that tracks temperature for a zone in an office building and sending an alert if it is too warm or too cold.
  * Monitoring a credit card transaction and sending an alert if the transaction appears fraudulent.

You might want to trigger an alert when:

  * A raw threshold is reached (alert if over 100 degrees).
  * A threshold based on a time window is reached (if latest reading is > average of the last 5 minutes)
  * A particular rate of increase or decrease is noticed (previous reading is up 10% compared to 5 minutes ago).

Part of the power of Wallaroo is that we allow you to implement any logic you need to accomplish your business objectives; there is no new API or programming model to learn, you implement your business logic in Python or Golang.

## Use Cases

A good example is triggering an alert when an odd temperature reading is received from a thermostat located in an office building.

In this example, I will be looking at a series of events that represent the temperature of a particular room and trigger an alert if the temperature exceeds some threshold.

For this example, we will assume that our Wallaroo cluster is receiving a data stream of temperature readings via Kafka and that the data contains a device_id, zone_id, and temperature reading for each message received.

For any given zone, we will keep the last 500 readings in Wallaroo's in-memory state and trigger an alert if the latest temperature reading is outside of three standard deviations or if the latest temperature is above 89 degrees.

## Wallaroo Application Builder

### Overview

![](https://d33wubrfki0l68.cloudfront.net/430fce20335009c2767b007f207d2cfc900cdce0/31c7b/images/post/real-time-streaming-pattern-triggering-alerts/image1.png)

The above defines the Wallaroo pipeline including the pipeline name, "Temperature Alerts," and the source of the data. In this example, we are receiving messages from a Kafka topic.

The only processing step in this example is a stateful partition that calls a function,`check_tempature`. Since this is a partitioning step, the data for Zone A would be routed automatically by Wallaroo to where the state for Zone A resized, the same for Zones B...Z, etc. The partition routing is defined in `zone_partitions` and executed via `partition`.

When the message is routed to the correct partition, the state object `ZoneTotals` would be updated with the latest temperature reading, then the `check_tempature` function would run to execute our business logic.

If an alert was triggered in the previous step, a message would be generated and passed along to the Kafka sink.

## Conclusion

Triggering alerts is one of the most common patterns you will see when thinking about and building event-triggered applications.

As you can see, Wallaroo's lightweight API gives you the ability to construct your data processing pipeline and run whatever application logic you need to power your application.

## Give Wallaroo a Try

We hope that this post has piqued your interest in Wallaroo!

If you are just getting started, we recommend you try our [Docker image](https://docs.wallaroolabs.com/book/getting-started/docker-setup.html), which allows you to get Wallaroo up and running in only a few minutes.

[Hortonworks Community Connection (HCC)](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295) is an online collaboration destination for developers, DevOps, customers and partners to get answers to questions, collaborate on technical articles and share code examples from GitHub. [Join the discussion.](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295)
