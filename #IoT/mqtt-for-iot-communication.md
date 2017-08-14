# MQTT for IoT Communication

_Captured: 2017-07-29 at 19:58 from [dzone.com](https://dzone.com/articles/mqtt-for-iot-communication?edition=311401&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-07-29)_

Cisco IoT makes digital transformation a reality in factories, transportation, and utilities. [Learn how](https://dzone.com/go?i=228254&u=https%3A%2F%2Fdeveloper.cisco.com%2Fsite%2Fdevnet%2Fhome%2F%3Futm_source%3DDZone_bumpertext%26utm_medium%3Dad%26utm_campaign%3Ddnamarketing) to start integrating with Cisco DevNet.

MQTT stands for Message Queue Telemetry Transport. As its name suggests, it's a protocol for transporting messages between two points. Sure, we've got Messenger and Skype for that; but what makes MQTT so special is its super lightweight architecture, which is ideal for scenarios where bandwidth is not optimal.

The MQTT high-level architecture is primarily divided into two parts - a broker and a client.

![](http://thinkpalm.com/wp-content/uploads/2017/03/MQTT-High-Level-Architecture-1.png)

A broker acts as the heart of the architecture with capabilities of both subscriber and publisher. It is the point of contact for all clients. A broker's primary job is to queue and transmit messages from a publisher client to the subscriber client. However, it can also possess heavier capabilities (such as SSL certification, logs, database storage, etc.) based on requirements, set-up, and the broker service used.

The client portion is further divided into publishers and subscribers. Since clients are the actual software components that go into the edge devices, they're engineered to be very, very lightweight, with a majority of processing of the already lightweight architecture handled by the broker.

Therefore, MQTT clients have very specific and simplified tasks. The publisher-client publishes MESSAGES with a TOPIC and QUALITY; the subscriber-client subscribes to MESSAGES with a TOPIC and QUALITY. And that's pretty much the gist of it.

Also, MQTT clients are very good runners! They will run on almost any OS - Mac, Windows, and Linux; as well as single-board and mobile operating systems like Raspbian and Android. They even exist as apps!

## **The Nitty-Gritties of MQTT**

Sure MQTT is simple and awesome, but it took clever engineering to make it that way. Here're some of the nitty-gritties about the critical components of MQTT.

### _**The Message**_

This is… well… the message to be sent. Typically called the "Message Payload," it is, by default, formatted as plain-text, giving users the flexibility to structure the message payload to any required format.

### _**The Topic**_

Every MQTT communication relies on the concept of "The Topic." A single unique topic defines a unique pipeline, or connection between publishers and subscribers. Essentially, if the topic of the message published matches the topic subscribed, the subscriber gets the message. As simple as that!

![](http://thinkpalm.com/wp-content/uploads/2017/03/Topic-in-MQTT.png)

It gets better. MQTT even allows hierarchies to be defined within its topics. Hierarchy levels are separated by a slash. For example, a topic for sending temperature in your living room could be "house/living-room/temperature". This basically defines the hierarchy as "temperature is the child of living-room, which is the child of house". This can be done for other rooms too, like "house/kitchen/temperature", "house/bedroom/temperature".

Moreover, you can also subscribe to multiple sensors using something called wildcards. There are two wildcards, "+" and "#". The plus sign is a single level wild card that only allows arbitrary values for one level of the hierarchy while the hash sign allows data to come in from all underlying hierarchy levels.

For instance, in the above example, house/+/temperature would give temperature value from living-room, kitchen, and bedroom. And subscribing to the topic "house/#" would mean subscribing to all topics that have house as their root parent.

## **The QoS**

The Quality of Service functionality exists to provide the flexibility to have or not have guaranteed delivery of messages. MQTT QoS can be laid out within only six bits - 0, 1, and 2.

QoS-0 is the most unreliable. Any message published with QoS 0 will be sent by the publisher, and then forgotten, not checking whether the message has been successfully delivered. It is often called "fire and forget."

QoS-1 holds the concept of delivering the message "at least" once. Any message is guaranteed to be delivered at least once, but may also be sent more than once.

QoS-2 is the most reliable - "exactly once." The broker guarantees that the message reaches its destination only once. QoS reliability is directly proportional to bandwidth consumption: higher reliability, higher bandwidth consumption.

## **The Security**

MQTT really wants to be lightweight. Implementing a protocol-exclusive full-stack security would completely upturn MQTT's diet. That being said, MQTT as a protocol does have application layer security measures. For example, each client (both publishers and subscribers) have client names and client IDs. And an MQTT broker provides the option to implement authentication so that clients will require correct usernames and passwords to connect to the broker.

However, MQTT can also be implemented with multi-layered security. Each layer prevents different kinds of attacks. Although the protocol itself specifies few security mechanisms, MQTT can use all common implementations of other state-of-the-art security standards, like VPN in the network layer and SSL/TLS in the transport layer. The idea is to not reinvent the wheel; rather, it is to build upon the accepted and easily implementable standards.

MQTT is cool! It drinks Java coffee, has a pet Python, and loves wearing Perl and Ruby. The point is, MQTT can be easily embedded in most of the popular languages - Java, Python, Perl, Ruby, C, C++, NodeJS, Swift, Go, Lua, PHP; you name it.

Although MQTT was designed with machine-to-machine in mind, it is more versatile than that. It has space for creativity. It can handle machine-to-cloud, cloud-to-machine, or even apps-to-apps communication. Even if different apps written in distinctly different languages need to communicate with each other, it's no sweat. Just set up a single broker and insert MQTT client snippets into the apps. They will happily talk to each other.

MQTT has been an immense relief to IoT projects that have many modularized components communicating with each other over a range of different environments. MQTT's simplicity and efficiency have cut down countless hours trying to get different components speaking different languages over different protocols to talk to each other.

## **Get Your Feet Wet!**

You can experience MQTT in literally four simple steps:

  * Download MQTT Box (an extension of Chrome)
  * Create a client with the details (see the following picture for details) to connect to a broker (HiveMQ Public Broker in this case)
  * Add the subscriber and publisher, both with matching topics.
  * Send a message from the publisher and watch the message magically appear (well, seemingly magical thanks to the talent and sweat of MQTT authors Andy Stanford-Clark and Arlen Nipper) on your subscriber!
  * This, of course, is to get you started. MQTT Box is an app-based MQTT client. HiveMQ is a broker service that you can download to use locally, or pay to use the cloud broker service. HiveMQ Public Broker, sponsored by HiveMQ, is a freely available trial broker service (so it might be down from time to time. It's free, not exactly faithful).
![](http://thinkpalm.com/wp-content/uploads/2017/03/MQTT-1.png)

> _Or if you want to get technical:_

  * Download a Mosquitto MQTT Broker (Mosquitto is one among many others MQTT Broker service providers like HiveMQ, RabbitMQ, EMQTT, etc.)
  * Download Mosquitto MQTT Client (mosquitto_pub and mosquitto_sub)
  * Start the broker from MQTTcommands
  * Start a subscriber from MQTT commands
  * Publish a message from MQTT commands

Here're some instrumental reference commands:

Oh, and once you have the broker running, you can actually connect any type of client (publishers and subscribers) to it: be it command-line clients, NiFi client, MQTT Box client, as well as clients existing as code snippets within your own app.

Happy coding!

Cisco is a software company. Surprised? Don't be. [Join DevNet](https://dzone.com/go?i=228255&u=https%3A%2F%2Fdeveloper.cisco.com%2Fsite%2Fdevnet%2Fhome%2F%3Futm_source%3DDZone_bumpertext%26utm_medium%3Dad%26utm_campaign%3Ddnamarketing) to explore APIs, tools, and techniques that developers are using to add collaboration, IoT, security, network priority, and more!
