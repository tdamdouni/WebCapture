# MQTT: The Nerve System of IoT

_Captured: 2017-06-04 at 01:16 from [dzone.com](https://dzone.com/articles/mqtt-the-nerve-system-of-iot?edition=304120&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-03)_

There are billions of smart devices in our world today, but what if these devices were interconnected? What if these devices can interact with each other just like how their owners do and form a kind of global nervous system? This essentially describes what people call the Internet of Things or IoT. IoT has revolutionized the IT world and the way in which we innovate. Everything from performance to security must be considered when delving into IoT.

## **Message Queueing Telemetry Transport Protocol (MQTT)**

MQTT is a publish/subscribe-based lightweight messaging protocol for Machine to Machine (M2M) communication, on top of the TCP/IP protocol. The protocol provides telemetry technology, and MQTT developers are working to connect the evolving internet world, which is expected to produce even more diverse smart devices. The first version of the MQTT protocol was authored by Stanford-Clark, IBM, and Arlen Nipper.

## **Why MQTT?**

MQTT has been used by [Facebook for their messenger application](https://www.messenger.com/), which needed a persistent connection to their servers without killing battery life. It requires a low network bandwidth and has a small code footprint. It transmits data over widely distributed and sometimes intermittent networks. These features translate as advantages for remote devices with little memory and processing power.

Other notable features of MQTT are:

  * It's open source, royalty free and therefore easy to adopt and adapt
  * It follows a publish/subscribe model for one-to-many distribution
  * Small message headers
  * Multiple Quality of Service levels
  * Simple command messages
  * Data type agnostic
  * Retained messages
  * Clean sessions and durable connections
  * Last Will and Testament (LWT)

## **MQTT vs. HTTP**

  

**MQTT**
**HTTP**

Design
Data-centric
Document-centric

Model
Publish/Subscribe
Request/Response

Complexity
Simple commands
Complex

Message Size
Small headers with a compact binary header size of 2 bytes
Larger because headers are in text format

Service Levels
3 QoS Levels
Same service level for all messages

Distribution
One-to-many
One-to-one

An example of an MQTT topology:

![Image title](http://blog.catchpoint.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-30-at-11.55.30-AM.png)

## **Quality of Service Levels**

QoS value decides on how each message will be delivered, and it is a mandatory value to be set for every message sent.

### **QoS 0 (At Most One Message Delivery)**

When a QoS value of 0 is set for a message, a response is not expected, and there are no retry rules defined. A message arrives at the broker either once or not at all. A QoS 0 message is lost if the client is disconnected or if the server fails. A retry is not attempted by the MQTT layer. From a performance point of view, this is the fastest way to send a message using MQTT. Only the MQTT command PUBLISH is used here, and no other commands flow for a QoS 0 message.

![Image title](http://blog.catchpoint.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-30-at-11.58.21-AM.png)

> _QoS 1 (At Least One Message Delivery)_

The MQTT client or server would attempt delivering the message at least once, but there are possibilities of duplicate messages. When the broker receives the message, acknowledgment PUBACK is sent. In the event of no PUBACK received, the sender sends the message again with a DUP (duplicate) bit set. On receiving a message with the DUP bit set, the broker republishes the message to all its subscribers and sends another PUBACK message. This way MQTT persistence can be achieved. When a PUBLISH happens, the message is stored in the persistence layer such as a disk and removed when a PUBACK is received. A message with QoS 1 has a message ID in the message header.

![Image title](http://blog.catchpoint.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-30-at-11.59.18-AM.png)

> _QoS 2 (Exactly One Message Delivery)_

Additional flows to QoS 1 ensure that the message is delivered exactly once. The message is sent in the PUBLISH flow and the message is stored in the persistence layer by the client. A PUBREC message is sent as the response to PUBLISH. Meanwhile, the message is locked on the server. On receiving PUBREC, a PUBREL is sent to the server. On receiving PUBREL, the broker sends the messages, sends back a PUBCOMP and discards the stored state. A message with QoS 2 will have a message ID in the message header.

![Image title](http://blog.catchpoint.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-30-at-12.01.31-PM.png)

## **Security in MQTT**

MQTT aims at a lightweight communication for the internet of things, but security comes at a cost regarding processor utilization and communication overhead. This is a reason as to why in the protocol there are only a few security mechanisms available. But many MQTT implementations have security standards like SSL/TLS is used.

Security in MQTT is divided into multiple layers.

**Network Level:** Using a physically secure network or VPN for communication provides a secure connection.

**Transport Level:** TLS/SSL can be used for transport encryption that ensures communication is encrypted and identity is authenticated.

**Application Level:** The protocol has Client ID, Username/Password credentials which can bring about device authentication. Another way is to have payload encryption without having an extensive transport encryption.

## MQTT in Action: Home Monitoring Solution

A classic example for an MQTT-based application would be a home monitoring system. For example, the current temperature of a room heater is sent to a device on request.

![Image title](http://blog.catchpoint.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-30-at-1.22.22-PM.png)

Like any other application when there is communication between two applications/devices there is room for failures, and it is very important to monitor the applications to ensure efficient functioning of the application and good user experience.

Catchpoint can now monitor the performance and availability of IoT devices using the MQTT protocol. The MQTT test can be used to publish/subscribe communications over MQTT by publishing and subscribing to message for a specified topic and measuring how long it takes.

![Image title](http://blog.catchpoint.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-30-at-1.23.50-PM.png)

In an upcoming blog, we will look under the hood of MQTT protocol as seen by [Wireshark](http://blog.catchpoint.com/2017/05/12/dissecting-tls-using-wireshark/). This will help us understand the communication between an MQTT client and MQTT broker.
