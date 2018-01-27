# Tail-Tolerance by Google

_Captured: 2017-10-27 at 17:11 from [dzone.com](https://dzone.com/articles/tail-tolerance-by-google?edition=334741&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202017-10-27)_

Recently, I read an interesting paper entitled "The Tail at Scale" written by two experts from Google, Jeff Dean and Luiz Barroso. The authors defined what the latency tail-tolerant system is and how to implement it.

## What Is Tail Latency?

In the paper, the authors provide an example of the system where each server typically responds in 10 ms, but 1% of the requests (99th percentile) will take 1 second to complete. It doesn't sound like a big deal because we still respond to 99% of the requests in 10 ms. But let's imagine a scenario when we have 100 of microservices which we need to call in parallel in order to build the final response for the client. Each microservice has the previously mentioned latency characteristics (10 ms for 99% of the requests and 1 second for the remaining 1%).

Let's calculate the probability of 10 ms response time for the main request:

`(1/99) ^ 100 = 0.3660323412732289`

Which means that more than 63% of the requests will take at least 1 second to respond! That's not what you might expect from a system where each service responds in 10 ms 99% of time.

## Root Causes

There are plenty of factors which might lead to variability in response time. To name a few:

  * Shared resources (memory, CPU cores, CPU caches, shared file system)
  * Background tasks running on the server
  * Maintenance activities (GC, log compactions)
  * Queues in general
  * CPU throttling

It might be a good idea to reduce a response time variability by for instance synchronizing some background tasks in a way that all of them are triggered at the same time on all servers. It might sound counterintuitive to increase the latency of all the services at once, but at the same time, it limits the amount of time the background tasks affects the performance of the whole system.

## Solutions

Sometimes, it might be nearly impossible to reduce all the response time variability, so the authors suggest a bit different approach and show how you can get by with all these spikes.

### Hedged Requests

This is a fairly simple solution. When you need to call the particular service, you just send the requests to multiple instances of it and use the response which comes first. That might highly increase the load in your systems so the authors suggest deferring sending the secondary requests. For example, if the initial request takes more than the 95th-percentile expected latency, then it's a good time to send the requests to other instances.

### Tied Requests

Instead of deferring the secondary requests, here you send the requests to all the instances which have the incoming requests queues and you allow them to communicate with each other. When one of the instances starts processing the request, it sends the cancellation message to other instances, so they can drop it from their queues. If you are familiar with how invalidation queues in modern CPU work, this is conceptually similar.

### Latency-Induced Probation

One slow service can drastically slow down the entire combined response as described earlier. Having multiple instances allow us to temporarily exclude the slow ones from the system, so we can improve the response time.

### Good Enough Responses

The authors give an example of Google's large information-retrieval (IR) systems where speed is more than just a performance metric, it's a key quality metric. In that kind of system, it is usually better to return _good_ results quickly, than to return the _best_ possible results slowly (think of Google search engine). So if an IR system calls multiple services to combine the best possible response, it's better to give up some slow queries and server the "good enough" content faster.

### Canary Requests

Another interesting concept is called Canary Requests. Similarly to Canary Release, the name of this technique also comes from [coal mining industry](https://en.wikipedia.org/wiki/Sentinel_species#Historical_examples). Imagine the following scenario: your system combines the response from thousands of servers which all execute the similar code. If there is a programming bug in the code (or just a malicious request), it will cause crashes or very long delays on thousands of servers simultaneously. To prevent this scenario, you can initially send a _canary request _to one or two servers and only if they respond successfully, then you call all the remaining servers.
