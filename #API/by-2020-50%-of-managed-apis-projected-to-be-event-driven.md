# By 2020, 50% of Managed APIs Projected to be Event-Driven

_Captured: 2017-10-19 at 14:34 from [dzone.com](https://dzone.com/articles/by-2020-50-of-managed-apis-projected-to-be-event-d?edition=334696&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202017-10-19)_

[Modernize your application architectures with microservices and APIs](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) with best practices from this free virtual summit series. Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

According to Mark O'Neill and Paolo Malinverno of Gartner, 50% of managed APIs will support event-driven IT by 2020 ([2017 Report](https://www.gartner.com/doc/3660318)). These event-driven APIs will not necessarily replace RESTful request-response architectures, but will become necessary supplements to expand an organization's functional offerings and overall performance.

In another [2017 IoT report](http://www.gartner.com/newsroom/id/3598917), Gartner projects "8.4 billion connected devices, up 31% from 2016, and will reach 20.4 billion by 2020. Total spending on endpoint infrastructure and services will reach almost $2 trillion in 2017."

So, what's driving this evolution? "Realtime" is becoming an omnipresent force in the modern tech stack. As consumers demand faster experiences and more instantaneous data transactions, companies are increasingly investing in product infrastructure that accelerates these transactions. Though we've seen APIs become an economic and technological imperative, they are typically based on request-response style interactions, which limits their scope and effectiveness in the realtime arena.

## Request-Response vs. Event-Driven APIs

At its core, request-response is a message exchange pattern in which a requestor sends a request message to a replier system. The replier system receives and processes the request, and if all goes well, it returns a message in response. While this exchange format works well for more structured requests, it limits integrations to those where the expectant system has a clear idea what it wants from the other. These request-response style APIs, therefore, must follow the interaction script from the calling service.

![Request-Response vs Event-Driven Realtime APIs](https://realtimeapi.io/wp-content/uploads/2017/10/requestresponsevseventdrivenapi.jpg)

In an event-driven architecture, applications integrate multiple services and products as equals based on event-driven interactions. These interactions are driven by event emitters, event consumers, and event channels, whereby the events, themselves, are typically significant 'changes in state' that are produced, published, propagated, detected, or consumed. This architectural pattern supports loose coupling amongst software components and services. The advantage is that an event emitter does not need to know the state of the consumer, who the consumer is, or how the event will be processed (if at all). It is a mechanism of pushing data through a persistent stream.

## The $195 Billion IoT Market

The proliferation and "smartening" of IoT-driven devices is projected to reach a market cap exceeding $195 billion in 2023, according to analysts at [ReportsnReports](http://www.reportsnreports.com/reports/944711-internet-of-things-iot-market-shares-strategies-and-forecasts-worldwide-2017-to-2023.html). From a market of $16 billion in 2016, this growth is mainly fueled by the increasingly ubiquitous manufacturing of smarter in-home, mobile, and transportation devices -- and the need to capture that data and enhance communication infrastructure.

The smarter devices become, the more data they need to make complex, realtime decisions. Sensors and external data gathering implements are becoming an essential catalyst for IoT industry growth. The accuracy of sensors and actuators that measure geospatial proximity, acceleration, temperature, and motion will separate the industry leaders from the laggards.

![IoT_realtime API](https://realtimeapi.io/wp-content/uploads/2017/10/IoT_realtime.jpg)

Taking a deeper dive into the actual core components, like semiconductors, [Gartner](http://www.gartner.com/newsroom/id/3598917) forecasts a $45 billion IoT-driven semiconductor market by 2020, with consumer IoT taking the lion's share and the automotive industry (including self-driving vehicles) taking second.

![](https://realtimeapi.io/wp-content/uploads/2017/10/IoTgrowth.png)

## Data & Business Intelligence

The goal of a truly interconnected tech ecosystem will also mirror equal growth in data and business intelligence. The more things are interconnected, the more companies will need to gather data, push remote updates, and control devices in the field. Hence, remote communication needs to be reliable, data needs to be accurate, and the ability to extract meaningful information from big data becomes paramount.

In a [2015 report](http://www.seagate.com/files/www-content/our-story/trends/files/Seagate-WP-DataAge2025-March-2017.pdf) by Seagate, 25% of all data will need to be processed and generated in realtime by 2025 out of a total of 160 Zettabytes.

![rise of realtime data](https://realtimeapi.io/wp-content/uploads/2017/10/SW-V1.png)

## Event-Driven API Mechanisms

If you're looking to understand the web infrastructure behind realtime, then let's explore some of its basic components. A more thorough analysis can be found in [Getting Started with Realtime API Infrastructure](https://realtimeapi.io/getting-started-with-building-realtime-api-infrastructure/).

Realtime is all about pushing data. In a [data push](https://techterms.com/definition/push) model, data is pushed to a user's device rather than pulled (requested) by the user. For example, modern push email allows users to receive email messages without having to check manually. Similarly, we can examine data push in a more continuous sense, whereby data is continuously broadcasted. Anyone who has access to a particular channel or frequency can receive that data and decide what to do with it.

### **HTTP Streaming**

[HTTP streaming](https://realtimeapi.io/hub/http-streaming/) provides a long-lived connection for instant and continuous data push. You get the familiarity of HTTP with the performance of WebSockets. The client sends a request to the server and the server holds the response open for an indefinite length. This connection will stay open until a client closes it or a server side-side event occurs. If there is no new data to push, the application will send a series of keep-alive ticks so the connection doesn't close.

### **Websockets**

[WebSockets](https://realtimeapi.io/hub/websockets/) provide a long-lived connection for exchanging messages between client and server. Messages may flow in either direction for full-duplex communication. This bi-directional connection is established through a WebSocket handshake. Just like in HTTP Streaming and HTTP Long-Polling, the client sends a regular HTTP request to the server first. If the server agrees to the connection, the HTTP connection is replaced with a WebSocket connection.

### **Webhooks**

[Webhooks](https://realtimeapi.io/hub/webhooks/) are a simple way of sending data between servers. No long-lived connections are needed. The sender makes an HTTP request to the receiver when there is data to push. A WebHook registers or "hooks" to a callback URL and will notify you anytime an event has occurred. You register this URL in advance and when an event happens, the server sends an HTTP POST request with an Event Object to the callback URL. This event object contains the new data that will be pushed to the callback URL. You might use a WebHook if you want to receive notifications about certain topics. It could also be used to notify you whenever a user changes or updates their profile.

### **HTTP Long-Polling**

[HTTP long-polling](https://realtimeapi.io/hub/http-long-polling/) provides a long-lived connection for instant data push. It is the easiest mechanism to consume and also the easiest to make reliable. This technique provides a long-lived connection for instant data push. The server holds the request open until new data or a timeout occurs. Most send a timeout after 30 to 120 seconds, it depends on how the API was setup. After the client receives a response (whether that be from new data or a timeout), the client will send another request and this is repeated continuously.

And, of course, there is the infrastructure behind it all.

**[Realtime API Infrastructure -](https://realtimeapi.io/hub/realtime-api-iaas-overview/)** Realtime API infrastructure specifically allows developers to build realtime data push into their existing APIs. Typically, you would not need to modify your existing API contracts, as the streaming server would serve as a proxy. The proxy design allows these services to fit nicely within an API stack. This means it can inherit other facilities from your REST API, such as authentication, logging, throttling, etc. It can be combined with an API management system. In the case of WebSocket messages being proxied out as HTTP requests, the messages may be handled statelessly by the backend. Messages from a single connection can even be load balanced across a set of backend instances.

**[Realtime Application Infrastructure -](https://realtimeapi.io/hub/realtime-app-iaas-overview/)** Realtime app infrastructure sends data to browsers and clients. It typically uses [pub/sub ](https://realtimeapi.io/hub/publishsubscribe-pattern/)messaging, [webhooks](https://realtimeapi.io/hub/webhooks/), and/or [websockets](https://realtimeapi.io/faq/what-is-a-websocket/) -- and is separate from an application or service's main API.

## Main Take-Aways

IoT, big data, and consumer expectations are fueling the proliferation of event-driven/realtime APIs. One of the greatest challenges facing engineers over the next few years will be constructing scalable, fault-tolerant event-driven architectures at scale. This is why we are seeing companies spend more than $2 trillion in 2017 to support event-driven endpoints and infrastructure.

While RESTful architectures will remain a necessity, it is important for organizations to understand and plan for event-driven systems -- which add a new dimension of realtime API infrastructure complexity.

The Integration Zone is proudly sponsored by [CA Technologies](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Learn from expert microservices and API presentations at the [Modernizing Application Architectures Virtual Summit Series](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
