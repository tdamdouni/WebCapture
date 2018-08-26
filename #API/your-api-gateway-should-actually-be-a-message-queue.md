# Your API Gateway Should Actually Be a Message Queue

_Captured: 2018-07-11 at 19:07 from [dzone.com](https://dzone.com/articles/your-api-gateway-should-actually-be-a-message-queu?edition=386195&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-07-11)_

**[The State of API Integration 2018](https://dzone.com/go?i=285436&u=https%3A%2F%2Foffers.cloud-elements.com%2Fthe-state-of-api-integrations-report-2018%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_content%3Dpre-roll): Get Cloud Elements' report for the most comprehensive breakdown of the API integration industry's past, present, and future.**

## Or Why We Need Digital Osmosis

Conventional API Gateways handle difficult things like routing and provide a uniform layer that allows outside applications access without them having to understand what is going on in the inside.

Conventional API Gateways operate on the request/response pattern that most of the internet is based on, but this creates the problem of having to provide a relatively quick response so that the browser doesn't time out. This becomes unnatural if the internals of the architecture use an event-based architecture to allow for cleaner decoupling or otherwise trigger longer running tasks.

Instead, the gateway should be a set of message queues organized into different channels. The interior should have a set of serverless functions (or microservices) listening to specific channels waiting to process information arriving on those channels.

## Digital Osmosis

Why do I call it Digital Osmosis? In cells, nutrients are pulled through the membrane by way of a concentration gradient. A request/response, in contrast, is forcing a message into the system. Having a message queue based entry point means that the interior pulls in the message when it wants to and only the messages that it wants to. Similarly, the concentration gradient is the ratio between serverless functions listening to specific channels vs messages entering it.

Using auto-scaling based on message backup rates will often lead to more consistent and reliable performance than scaling based on memory or CPU usage. Additionally, occasional downtime will not lead to any message losses.

## Clients Need to Become Event-Based

This goes hand in hand with [Http/2 Server Push](https://en.wikipedia.org/wiki/HTTP/2_Server_Push). Instead of a client forcing a request on to the server and demanding a response, the client needs to be designed to listen to the server and process messages coming back from the server.

This is important from the perspective of modern real-time architectures. When we build platform-centric applications, the server knows more than the client -- the client often does not know what to ask for in dynamic multi-user, concurrent situations. The state will change continuously as many users interact at the same time, with the same data or process.

We need to flip the traditional request/response architecture on its head. The server should push data and pull in data. The server, in effect, becomes the facilitator.

## There is One More Change

The server has become a facilitator, which changes the fundamental client/server relationship, but the next step is that the server is completely influenced by the waves of messages coming in from many clients.

In the old architectures, the client and server acted as a singular, insulated pair. In new architectures, we can no longer have insulated pairs as many clients would want to share state. The server now becomes the facilitator or controller, always working with many clients instead of dedicating itself to a single client with each request.

This is a significant paradigm shift, but I feel it's a very necessary one.

Your API is not enough. Learn why (and how) leading SaaS providers are turning their products into platforms with API integration in the ebook, [Build Platforms, Not Products](https://dzone.com/go?i=263426&u=https%3A%2F%2Foffers.cloud-elements.com%2Fbuild-platforms-not-products-ebook%3Futm_campaign%3DPlaforms%25252C%252520Not%252520Products%252520eBook%26utm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_content%3Dtext) from Cloud Elements.
