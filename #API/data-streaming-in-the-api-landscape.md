# Data Streaming in the API Landscape

_Captured: 2017-10-12 at 17:05 from [dzone.com](https://dzone.com/articles/data-streaming-in-the-api-landscape?edition=329562&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=big%20data%202017-10-12)_

I was taking a fresh look at [my real-time API research](http://realtime.apievangelist.com/) as part of some data streaming and event-sourcing conversations I was having last week. My research areas are never perfect, but I'd say that real-time is still the best umbrella to think about some of the shifts we are seeing in the landscape recently.

They are nothing new, but there has been renewed energy, new and interesting conversation going on, as well as some growing trends that I cannot ignore. To support my research, I took a day this week to dive in and have a conversation with my buddy Alex over at the [TheNewStack.io](https://thenewstack.io/) and the new CEO of WSO2 Tyler Jewell around what is happening.

The way I approach my research is to always step back and look at what is happening already in the space, and I wanted to take another look at some of the real-time API service providers I was already keeping eye on in the space:

  * **[Pubnub**](https://www.pubnub.com/): APIs for developers building secure real-time mobile, web, and IoT apps.
  * **[StreamData**](https://streamdata.io/): Transform any API into a real-time data stream without a single line of server code.
  * **[Fanout.io**](https://fanout.io/): Fanout's reverse proxy helps you push data to connected devices instantly.
  * **[Firebase**](https://firebase.google.com/): Store and sync data with our NoSQL cloud database. Data is synced across all clients in real-time and remains available when your app goes offline.
  * **[Pusher**](https://pusher.com/): Leaders in real-time technologies. We empower all developers to create live features for web and mobile apps with our simple hosted API.

I've been tracking on what these providers have been doing for a while. They've all been pushing to boundaries of what is streaming, and real-time APIs for some time. Another open source solution that I think is worth noting, which I believe some of the above services have leverages is Netty.io.

  * [Netty](http://netty.io/): Netty is an asynchronous event-driven network application framework for rapid development of maintainable high-performance protocol servers and clients.

I also wanted to make sure and include Google's approach to a technology that has been around a while:

  * **[Google Cloud Pub/Sub**](https://cloud.google.com/pubsub/docs/): Google Cloud Pub/Sub is a fully-managed real-time messaging service that allows you to send and receive messages between independent applications.

Next, I wanted to refresh my understanding of all the Apache projects that speak to this realm. I'm always trying to keep a handle on what they each actually offer, and how they overlap. So, seeing them side by side like this helps me think about how they fit into the big picture.

  * **[Apache Kafka**](https://kafka.apache.org/): Kafka™ is used for building real-time data pipelines and streaming apps. It is horizontally scalable, fault-tolerant, wicked fast, and runs in production in thousands of companies.
  * **[Apache Flink**](https://flink.apache.org/): Apache Flink® is an open-source stream processing framework for distributed, high-performing, always-available, and accurate data streaming applications.
  * **[Apache Spark**](https://spark.apache.org/streaming/): Spark Streaming makes it easy to build scalable fault-tolerant streaming applications. Spark Streaming is an extension of the core Spark API that enables scalable, high-throughput, fault-tolerant stream processing of live data streams.
  * **[Apache Storm**](http://storm.apache.org/) Apache Storm is a free and open-source distributed real-time computation system. Storm makes it easy to reliably process unbounded streams of data, doing for real-time processing what Hadoop did for batch processing.
  * **[Apache Apollo**](https://activemq.apache.org/apollo/): ActiveMQ Apollo is a faster, more reliable, easier to maintain messaging broker built from the foundations of the original ActiveMQ.

One thing I think is worth noting with all of these is the absence of the web when you read through their APIs. Apollo had some significant RESTful approaches and you find gateways and plugins for some of the others, but when you consider how these technologies fit into the wider API picture, I'd say they aren't about embracing the web.

On that note, I think it is worth mentioning what is going on over at Google, with their gRPC effort, which provides "bi-directional streaming and fully integrated pluggable authentication with http/2 based transport:"

  * **[gRPC**](https://grpc.io/): A high-performance, open-source universal RPC framework.

Also, I think most notably, they are continuing the tradition of APIs embracing the web and built on top of HTTP/2. For me, this is always important and trumps just being open source in my book. The more web an open source technology, and a company's service utilize, the more comfortable I'm going to feel telling my readers they should be baking this into their operations.

After these services and tooling, I don't want to forget about the good ol' fashioned protocols available out there, that help us do things in real-time. [I'm tracking on 12 real-time protocols](http://realtime.apievangelist.com/#BuildingBlocks) that I see in use across the companies, organizations, institutions, and government agencies I'm tracking on:

  * **[Simple (or Streaming) Text-Orientated Messaging Protocol (STOMP)**](https://stomp.github.io/): STOMP is the Simple (or Streaming) Text-Orientated Messaging Protocol. STOMP provides an interoperable wire format so that STOMP clients can communicate with any STOMP message broker to provide easy and widespread messaging interoperability among many languages, platforms, and brokers.
  * **[Advanced Message Queuing Protocol (AMQP)**](https://www.amqp.org/): The Advanced Message Queuing Protocol (AMQP) is an open standard for passing business messages between applications or organizations. It connects systems, feeds business processes with the information they need and reliably transmits onward the instructions that achieve their goals.
  * **[MQTT**](http://mqtt.org/): MQTT is a machine-to-machine (M2M)/Internet of Things connectivity protocol. It was designed as an extremely lightweight publish/subscribe messaging transport. It is useful for connections with remote locations where a small code footprint is required and/or network bandwidth is at a premium.
  * **[OpenWire**](http://activemq.apache.org/apollo/documentation/openwire-manual.html): OpenWire is our cross-language Wire Protocol to allow native access to ActiveMQ from a number of different languages and platforms. The Java OpenWire transport is the default transport in ActiveMQ 4.x or later.
  * [Websockets](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API): WebSocket is a protocol providing full-duplex communication channels over a single TCP connection. The WebSocket protocol was standardized by the IETF as RFC 6455 in 2011, and the WebSocket API in Web IDL is being standardized by the W3C.
  * **[Extensible Messaging and Presence Protocol (XMPP)**](https://xmpp.org/about/): XMPP is the Extensible Messaging and Presence Protocol, a set of open technologies for instant messaging, presence, multi-party chat, voice and video calls, collaboration, lightweight middleware, content syndication, and generalized routing of XML data.
  * **[SockJS**](https://github.com/sockjs): SockJS is a browser JavaScript library that provides a WebSocket-like object. SockJS gives you a coherent, cross-browser, JavaScript API that creates a low-latency, full-duplex, cross-domain communication channel between the browser and the web server.
  * **[PubSubHubbub](https://github.com/pubsubhubbub/)**: PubSubHubbub is an open protocol for distributed publish/subscribe communication on the Internet. Initially designed to extend the Atom (and RSS) protocols for data feeds, the protocol can be applied to any data type (i.e. HTML, text, pictures, audio, video) as long as it is accessible via HTTP. Its main purpose is to provide real-time notifications of changes, which improves upon the typical situation where a client periodically polls the feed server at some arbitrary interval. In this way, PubSubHubbub provides pushed HTTP notifications without requiring clients to spend resources on polling for changes.
  * **[Real-Time Streaming Protocol (RTSP)**](https://www.ietf.org/rfc/rfc2326.txt): The Real-Time Streaming Protocol (RTSP) is a network control protocol designed for use in entertainment and communications systems to control streaming media servers. The protocol is used for establishing and controlling media sessions between endpoints. Clients of media servers issue VCR-style commands, such as play and pause, to facilitate real-time control of playback of media files from the server.
  * **[Server-Sent Events**](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events): Server-sent events (SSE) is a technology in which a browser receives automatic updates from a server via HTTP connection. The Server-Sent Events EventSource API is standardized as part of HTML5 by the W3C.
  * **[HTTP Live Streaming (HLS)**](https://developer.apple.com/streaming/): HTTP Live Streaming (also known as HLS) is an HTTP-based media streaming communications protocol implemented by Apple Inc. as part of its QuickTime, Safari, OS X, and iOS software.
  * **[HTTP Long Polling**](https://www.pubnub.com/blog/2014-12-01-http-long-polling/): HTTP long polling is where the client polls the server requesting new information. The server holds the request open until new data is available. Once available, the server responds and sends the new information. When the client receives the new information, it immediately sends another request and the operation is repeated. This effectively emulates a server push feature.

These protocols are used by the majority of the service providers and tooling I list above, but in my research, I'm always trying to focus on not just the services and tooling, but the actual open standards that they support.

I have to also mention the entry-level aspect of real-time, in my opinion. Something that many API providers support but also is the 101-level approach that some companies, organizations, institutions, and agencies need to be exposed to before they get overwhelmed with other approaches.

  * **[Webhooks**](http://webhooks.apievangelist.com/): A webhook in web development is a method of augmenting or altering the behavior of a web page, or web application, with custom callbacks. These callbacks may be maintained, modified, and managed by third-party users and developers who may not necessarily be affiliated with the originating website or application.

That is [the real-time API landscape](http://realtime.apievangelist.com/). Sure, there are other services, and tooling, but this is the cream on top. I'm also struggling with the overlap with event-sourcing, evented architecture, messaging, and other layers of the API space that are being used to move bits and bytes around today. Technologists aren't always the best at using precise words or keeping things simple and easy to understand, let alone articulate. This is one of the concerns I have with streaming API approaches, is that they are often over the heads, and beyond the needs of some API providers, and may API consumers. They have their place within certain use cases, and large organizations that have the resources, but I spend a lot of time worrying about the little guy.

I think a good example of web API vs. streaming API can be found in the Twitter API community. Many folks just need simple, intuitive, RESTful endpoints to get access to data and content, while a much smaller slice of the pie will have the technology, skills, and compute capacity to do things at scale. Regardless, I see technologies like Apache Kafka being turned into plug and play, infrastructure as a service approaches, allowing anyone to quickly deploy to Heroku, and just put to work via a SaaS model. So, of course, I will still be paying attention and trying to make sense out of all of this. I don't know where it will be going, but I will keep tuning in and telling stories about how real-time and streaming API technology is being used or not being used.
