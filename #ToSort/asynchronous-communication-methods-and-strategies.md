# Asynchronous Communication — Methods and Strategies

_Captured: 2018-01-19 at 13:23 from [dzone.com](https://dzone.com/articles/asynchronous-communication-methods-and-strategies?edition=355098&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-01-19)_

[Learn how _real _real-time monitoring is critical for DevOps](https://dzone.com/go?i=272435&u=https%3A%2F%2Fsignalfx.com%2Fsolutions%2Fenabling-devops%2F). Because you can't build what you can't see.

Asynchronous communication is a widely-used communication method between different processes and systems. In an asynchronous communication, the client sends a request to the server (which requires lengthy processing) and receives a delivery acknowledgment right away. Different from the synchronous communication, this response does not have the required information, yet.

After the client receives the acknowledgment, it continues to do its other tasks, assuming it will eventually be notified when the required information is ready on the server side.

The biggest benefit of asynchronous communication is the increased performance. Since the client does not block its valuable CPU cycles just for waiting, it can deliver more within the same timeframe. Increased decoupling between the client-server interaction will also lead to better scalability.

We see asynchronous communication patterns everywhere. Here are some examples:

  * A "Design and Assign" request is submitted to the Inventory Management Application, from the Order Management Application.
  * A "full dump" is requested from an Inventory Management Application.
  * Monitoring Application sends 1000 SMS's to the service impacted customers via an SMS Gateway.

Examples can be multiplied, but the principle is the same: Notify the caller when the lengthy process is finished, and the information can be consumed.

There are three methods to implement an asynchronous communication:

  * Asynchronous Callbacks
  * Using Pub-Sub messaging using a Message Broker (or MoM)
  * Polling for State Changes

In this article, we will elaborate these methods and some strategies that can make them effective.

## **Method 1: Asynchronous Callback**

In an asynchronous callback mechanism, following steps occur:

  1. The client authenticates to the server.

  2. The client calls the server operation. (Web service, RPC, Local method call, etc.)

  3. The client also subscribes with its "callback endpoint address" to the server. (explained below)

  4. The server acknowledges the receipt of the request synchronously.

  5. Client waits for the reply from another pre-defined channel (A Servlet, PHP page, Local handle, etc.)

  6. Server finishes the required work and notifies the client from the channel.

  7. The client fetches the information and processes it.

## **Method 2: Broker-based Publish/Subscribe**

In this method, a "topic" is created to enable the Client-Server communication. The steps are similar to Asynchronous Callback, but here, the medium differs. The server never notifies the client directly. It does this through a buffer, which is the Broker.

  1. The client authenticates to the server.

  2. The client calls the server operation. (Web service, RPC, Local method call, etc.)

  3. The client subscribes to the broker and starts listening to the topic from a different thread.

  4. Server finishes the required work and publishes a message to the topic.

  5. The client fetches the information and processes it.

Since we rely on a different broker component that will do the mediation between the systems, we should have a solid understanding of the inner workings of that broker. Features like message durability, TTLs, and routings need to be elaborated thoroughly.

## **Method 3: Polling**

Polling should be the least preferred method from the performance and scalability point of view as it puts extra strain on both client and server side. However, in some conditions, (especially when you have no control over the legacy server application's code or repository), you may be forced to implement it. Here are the typical steps of polling:

  1. The client authenticates to the server.

  2. The client calls the server operation. (Web service, RPC, Local method call, etc.)

  3. Server acknowledges the receipt of the request synchronously. Server puts the request in its database or exposes its state via an external service (such as web service)

  4. Every X seconds, client polls the state of the request by connecting to the repository or the exposed interface.

  5. If request's state transitions to "ready", the client fetches the information and processes it.

There are certain strategies you need to consider while designing asynchronous communication architectures.

### **Key Strategy**

The participants should be able to uniquely identify each request. That is to say, if the client asks the server to dump its database to an FTP server, the server should return its acknowledgment with a key that identifies this individual request.

The client can, then, wait for this particular key in its listening channel and correlate the incoming notification to the original request. Ideally, this key should be generated by the server. However, in some situations (cloud trailing requirement or legacy application involvement), the client provides a unique key attached to the request. It is then the server's responsibility to respond back with the same key when the callback time comes. The drawback to this second approach is key collisions. If a separate client also provides the same key at the same time, the server will need to reject the request.

Broker-based Publish/Subscribe Method normally uses one shared topic for all clients. Key Strategy becomes extremely important especially when this method is chosen.

### **Retry Strategy**

Imagine you are implementing the callback approach with an external URL. The remote client has passed the request, got its acknowledgment and waiting for the callback event to be delivered. What if the clients' endpoint is not available at that moment due to some reason? (Network outage, rebooting due to patch deployment, etc.)

If the server simply ignores this callback, when the client comes back up, it will never receive the callback. Therefore the request will never be fulfilled; client resources would be unnecessarily consumed.

To avoid this situation, Server should implement retries. It should retry the callback multiple times, waiting for fixed/increasing intervals in between. If the remote part never comes alive, then the callback message can be put in a repository that can be "re-played" manually by the support personnel.

With the broker approach, retry strategy can be even more challenging. There is a dark side of the publish/subscribe model. When you publish a message, it will be delivered to all of the subscribers. If the subscriber is not listening at that moment though, the message is lost! There are some workarounds to avoid this situation, such as durable application server topics, attached queues, or some tools like Apache Kafka. Please note that these workarounds can come with increased costs of maintainability, so feasibility studies should be performed before the rollout.

### **Subscription Strategy**

Asynchronous Callback Method requires a subscription strategy. The client should provide the server its address. For webhooks, this is a URL hosted on the client's web server. For other cases, it could even be a hostname and port number.

Rather than putting client URLs to a central database before the integration starts, we should implement a dynamic endpoint subscription methodology. The modern way to do this is to provide a Restful web service endpoint which accepts a request id, URL, and a key. "request id," comes from the initial synchronous request we made, which will be used as the correlation key. "URL" is the client's callback address. "key" is the password that should be passed to the client along with the URL callback.

Before the callback happens, the server can look up a "request id" from a lookup table (fed previously by a subscription) and find out the endpoint address to call. If this is a one-off request/response pair, the lookup row can be deleted from the repository on the spot.

### Payload Strategy

Generated response on the server side can represent any information. It can be a ten digit number or a ten terabyte file. Payload strategies depict how this information is passed to the client side.  
The payload can be directly passed inside the asynchronous notification itself. If the size is expressed in kilobytes, we can pass the information along to the callback. If this is not the case, the pointer to the file should be passed in the notification. If the information is captured in a, say, ten terabyte file, a file name, and an FTP server IP address can be passed within the notification. It would be then the client's responsibility to go ahead and fetch that file.

Designing asynchronous systems require careful design. The first question we need to ask ourselves is "Will it be more feasible to do this synchronously?". If the non-functional requirements allow, we should stick to the synchronous way of doing things. If you end up deciding the asynchronous path though, methodologies and strategies that are mentioned in this article can make your journey smoother.

[Get real-time alerts and visualizations](https://dzone.com/go?i=272432&u=https%3A%2F%2Fsignalfx.com%2F%3Fsignup%3Dtrue) across your cloud infrastructure for real real-time cloud monitoring. [Try it FREE now](https://dzone.com/go?i=272432&u=https%3A%2F%2Fsignalfx.com%2F%3Fsignup%3Dtrue)!

![](https://dz2cdn1.dzone.com/storage/rc-covers/7391100-dzone-aicover.jpg)
