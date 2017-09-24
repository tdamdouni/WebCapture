# Introduction to Web Application Performance

_Captured: 2017-09-21 at 11:08 from [dzone.com](https://dzone.com/articles/introduction-to-web-applications-performance?edition=326502&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-09-20)_

[Transform incident management with machine learning and analytics](https://dzone.com/go?i=239227&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2Fanalytics-machine-learning-incident-management-ebook.html%3Fcid%3Dpt-PA_STA_All_FC_PT_Five_Strategies_Dzone_eBook-AB-03-f-08162017%26cc%3Dpt%26elqcid%3D4046%26sfcid%3D7011O0000027vq2) to help you maintain optimal performance and availability while keeping pace with the growing demands of digital business with this [eBook](https://dzone.com/go?i=239227&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2Fanalytics-machine-learning-incident-management-ebook.html%3Fcid%3Dpt-PA_STA_All_FC_PT_Five_Strategies_Dzone_eBook-AB-03-f-08162017%26cc%3Dpt%26elqcid%3D4046%26sfcid%3D7011O0000027vq2), brought to you in partnership with BMC.

## Introduction

The field of web application performance is huge and cannot be covered in a single article, especially when we talk about practical techniques to build fast applications. Thus, I will just scratch the surface of the topic to cover important concepts around performance like performance metrics, the difference between performance and scalability, and perceived performance.

Let's go…

## Basic Concepts

### Performance Metrics

  * Response time: This is the most widely used metric of performance and it is simply a direct measure of how long it takes to process a request.
  * Throughput: A straightforward count of the number of requests that the application can process within a defined time interval. For web applications, a count of page impressions or requests per second is often used as a measure of throughput.
  * System availability: Usually expressed as a percentage of the application's run time minus the time the application can't be accessed by users. This is an indispensable metric because both response time and throughput are zero when the system is unavailable. Most companies use this as a way to measure uptime for service level agreements (SLA).
  * Responsiveness: How quickly the system acknowledges a request as opposed to processing it. This is important in many systems because users may become frustrated if a system has low responsiveness, even if its response time is good. If your system waits during the whole request, then your responsiveness and response time are the same. However, if you indicate that you've received the request before its done processing, then your responsiveness is better. Providing a progress bar during a file copy improves the responsiveness of your user interface, even though it doesn't improve response time.
  * Requests Rate: Understanding how much traffic your application receives can be useful to correlate to other application performance metrics to understand the dynamics of how your application scales. The more requests users send to the application, the higher the load. As load increases, performance decreases. A similar but slightly different metric to track is the number of concurrent users.
  * Resources Consumption: Measuring resources (CPU, Memory, and disk space) in correlation to other metrics -- like response time or throughput -- is very important in resource planning for scalability.
  * Efficiency is performance divided by resources. A system that gets 30 transactions per second (TPS) on two CPUs is more efficient than a system that gets 40 TPS on four identical CPUs.
  * Latency is the minimum time required to get any form of response, even if the work to be done is nonexistent. It's usually the big issue in remote systems. If I ask a program to do nothing but to tell me when it's done doing nothing, then I should get an almost instantaneous response if the program runs on my laptop. However, if the program runs on a remote computer, I may get a few seconds just because of the time it takes for the request and response to make their way across the wire. As an application developer, I can usually do nothing to improve latency. Latency is also the reason why you should minimize remote calls.
  * Server response time measures how long it takes to load the necessary HTML to begin rendering the page from your server, subtracting out the network latency between the browser and your server.

### What Is Performance?

Performance is either throughput or response time -- whichever matters more to you (in web applications, response time is more popular). It can sometimes be difficult to talk about performance when a technique improves throughput but decreases response time, so it's best to use the more precise term. From a user's perspective, responsiveness may be more important than response time, so improving responsiveness at a cost of response time or throughput will increase performance.

### What Is Scalability?

Application performance will always be affected by resource constraints. Scalability is the ability to overcome performance limits by adding resources. No matter how much hardware we have, at a certain point, we will see decreasing performance. This means increasing response times or a limit in throughput. Will adding additional hardware solve the problem? If yes, then we can scale. If not, we have a scalability problem. In other words, Scalability is a measure of how adding resources (usually hardware) affects performance. A scalable system is one that allows you to add hardware and get a commensurate performance improvement, such as doubling how many servers you have to double your throughput. Vertical scalability, or scaling up, means adding more power to a single server, such as more memory. Horizontal scalability, or scaling out, means adding more servers.

### Will Scaling Solve Performance Problems?

Ideally yes, but practically resources constraints may not be the issue! For example, if resources are not overloaded then adding more resources will not solve performance problems because they are not the bottleneck. If you add resources and didn't get a commensurate performance improvement, you have a performance issue.

The rules here:

  1. If adding more resources can solve performance issue, go for it.
  2. When adding resources becomes expensive, or does not help in the issue, enhance performance and efficiency.

### How to Define an Application Performance?

It is common to define application performance like "Response time is 2 seconds."

But this is not descriptive enough, especially in scalability planning context. It is better to say: "System response time is 2 seconds at 500 concurrent requests, with a CPU load of 50%, and a memory utilization of 92%."

## Performance Tests

To make an accurate performance definition, we should do some performance tests:

### Load Test

Load testing is the simplest form of performance testing. A load test is usually conducted to understand the behavior of the system under a specific expected load. This load can be the expected concurrent number of users on the application performing a specific number of transactions within the set duration. This test will give out the response times of all the important business-critical transactions. The database, application server, etc. are also monitored during the test, this will assist in identifying bottlenecks in the application software and the hardware that the software is installed on.

### Stress Test

Stress testing is normally used to understand the upper limits of capacity within the system. This kind of test is done to determine the system's robustness in terms of extreme load and helps application administrators to determine if the system will perform sufficiently if the current load goes well above the expected maximum.

### Responsiveness As Perceived Performance

While response time -- for example -- is important to measure performance, it's important as well to remember that users are the ultimate judge of performance. As users are not clocks, their time perception may be different from what we measure empirically.

In judging system responsiveness, we must first know how fast users expect a system to be. Research shows that there are four main categories of response times:

  * We expect an instantaneous response, 0.1 to 0.2 milliseconds, for any action similar to a physical interaction. Pressing a button, for example. We expect this button to indicate that it is pressed within this time.
  * We expect an immediate response, within a half to one second, indicating our information is received. Even in the case of a simple interaction, we expect an actual response to our request. This is especially true for information we assume is already available, as when paging or scrolling content.
  * We expect a reply within 2 to 5 [or better 3] seconds for any other interactive request. If the response takes longer, we begin to feel that the interaction is cumbersome. The more complex we perceive a task to be, the longer we are willing to wait for the response.

Simple UI tricks, such as progress bars, redirecting users' attention using animation, or placing slower loading sections at the bottom of a page or offscreen, can often 'fix' a performance problem without the need to tune the underlying code. These UI tricks are an important tool to have in your performance tuning toolbox and can be much quicker and easier than addressing the underlying issue. They can act as a holdover until you have the time to devote to the core problem.

### How Can We Measure Perceived Performance?

As with performance, human perception for faster or slower is not as precise as technical measurements. This is very important when judging whether a performance optimization is worth the effort.

In essence, our limited perception of application responsiveness can't detect performance changes of much less than 20%. We can use this as a rule of thumb when deciding which improvements will impact users most noticeably. If we optimize 300 milliseconds a request that took 4 seconds, we can assume that many users will not perceive any difference in response time. It might still make sense to optimize the application, but if our goal is to make things faster for the users, we have to make it faster by at least 0.8 seconds.

### References

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).
