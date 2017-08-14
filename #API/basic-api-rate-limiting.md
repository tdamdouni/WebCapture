# Basic API Rate-Limiting

_Captured: 2017-08-08 at 20:32 from [dzone.com](https://dzone.com/articles/basic-api-rate-limiting?edition=310393&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-21)_

It is likely that you are developing some form of web or RESTful API, and in case it is public-facing (or even when it's internal), you normally want to rate-limit it somehow. That is, to limit the number of requests performed over a period of time, in order to save resources and protect it from abuse.

This can probably be achieved on the web-server/load balancer level with some clever configurations, but usually, you want the rate limiter to be client-specific (i.e. each client of your API should have a separate rate limit), and the way the client is identified varies. It's probably still possible to do it on the load balancer, but I think it makes sense to have it on the application level.

I'll use spring-mvc for the example, but any web framework has a good way to plug an interceptor.

So, here's an example of a spring-mvc interceptor:

This sounds simple. But there are a few catches. You may wonder where the `SimpleRateLimiter` above is defined. We'll get there, but first, let's see what options we have for rate limiter implementations.

The most recommended one seems to be the Guava [RateLimiter](https://google.github.io/guava/releases/22.0/api/docs/index.html?com/google/common/util/concurrent/RateLimiter.html). It has a straightforward factory method that gives you a rate limiter for a specified rate (permits per second). However, it doesn't accomodate web APIs very well, as you can't initialize the RateLimiter with a pre-existing number of permits. That means a period of time should elapse before the limiter would allow requests. There's another issue - if you have less than one permit per second (e.g. if your desired rate limit is "200 requests per hour"), you can pass a fraction (hourlyLimit/secondsInHour), but it still won't work the way you expect it to, as internally there's a "maxPermits" field that would cap the number of permits at much less than you want it to. Also, the rate limiter doesn't allow bursts - you have exactly X permits per second, but you cannot spread them over a long period of time, e.g. have 5 requests in one second, and then no requests for the next few seconds. In fact, all of the above can be solved, but sadly, through hidden fields that you don't have access to. Multiple feature requests have existed for years now, but Guava just doesn't update the rate limiter, making it much less applicable to API rate-limiting.

Using reflection, you can tweak the parameters and make the limiter work. However, it's ugly, and it's not guaranteed it will work as expected. [I have shown here](https://gist.github.com/Glamdring/287844346374297bc0880b06df9dd492) how to initialize a Guava rate limiter with X permits per hour, with burstability and full initial permits. When I thought that would do, I saw that `tryAcquire()` has a `synchronized(..)` block. Will that mean all requests will wait for each other when simply checking whether allowed to make a request? That would be horrible.

So, in fact, the Guava RateLimiter is not meant for (web) API rate-limiting. Maybe keeping it feature-poor is Guava's way of discouraging people from misusing it?

That's why I decided to implement something simple myself, based on a Java Semaphore. [Here's the native implementation](https://gist.github.com/Glamdring/06be638d3913c6a23ecf820852ede60b):

Are there alternatives? Well, yes - there are libraries like [RateLimitJ](https://github.com/mokies/ratelimitj), which uses Redis to implement rate-limiting. That would mean, however, that you need to setup and run Redis. Which seems like an overhead for "simply" having rate-limiting.

On the other hand, how would rate-limiting work properly in a cluster of application nodes? Application nodes probably need some database or gossip protocol to share data about the per-client permits (requests) remaining? Not necessarily. A very simple approach to this issue would be to assume that the load balancer distributes the load equally among your nodes. That way you would just have to set the limit on each node to be equal to the total limit divided by the number of nodes. It won't be exact, but you rarely need it to be - allowing 5-10 more requests won't kill your application, allowing 5-10 less won't be dramatic for the users.

That, however, would mean that you have to know the number of application nodes. If you employ auto-scaling (e.g. in AWS), the number of nodes may change depending on the load. If that is the case, instead of configuring a hard-coded number of permits, the replenishing scheduled job can calculate the "maxPermits" on the fly, by calling an AWS (or other cloud-provider) API to obtain the number of nodes in the current auto-scaling group. That would still be simpler than supporting a Redis deployment just for that.

Overall, I'm surprised there isn't a "canonical" way to implement rate-limiting (in Java). Maybe the need for rate-limiting is not as common as it may seem. Or it's implemented manually - by temporarily banning API clients that use "too much resources."
