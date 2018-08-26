# Practicality of Observability

_Captured: 2018-06-22 at 14:58 from [dzone.com](https://dzone.com/articles/practicality-of-observability?edition=383245&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-06-22)_

xMatters delivers integration-driven collaboration that relays data between systems, while engaging the right people to proactively resolve issues. Read the [Monitoring in a Connected Enterprise whitepaper](https://dzone.com/go?i=283436&u=https%3A%2F%2Fwww.xmatters.com%2Fresources%2Freports%2Fmonitoring-connected-enterprise%3Futm_campaign%3D70138000001C2pDAAS%26utm_source%3Ddzon%26utm_medium%3Dweb%26utm_content%3D3-steps-to-monitoring-in-a-connected-enterprise-wp) and learn about 3 tools for resolving incidents quickly.

Technology teams are not immune to hype and trends. Today, one of the hottest topics is observability. Everyone seems to be jumping on the observability bandwagon. Companies are building observability teams and looking to purchase observability tools.

Observability isn't necessarily a new thing. Having spent two decades building, monitoring, and observing a large distributed internet service, I have had the pleasure to see the concept of observability evolve. Observability and monitoring are [closely related](http://blog.catchpoint.com/2017/12/14/monitoring-and-observability/). For me, observability is about the ability to see. To find the needle in the haystack. To learn and to make things better.

A long time ago in a galaxy far away, I set up a Quality of Services group. Our job was to buy, build and deploy solutions to improve the quality of the service we delivered to customers. We spent the majority of our time looking at monitoring data, telemetry, and signals trying to make sense of all it. Our objectives were to ensure our service level objectives (SLO) were met, to prevent service level agreement (SLA) breaches, and to drive decisions across the company regarding capacity planning, release management, and new product launches.

We didn't always know why things were broken, we had to examine the data to reveal the answers. We couldn't rely only on alerts for known issues as sometimes performance issues were new and unusual. We were doing observability in a way, although we didn't call it that. The language we use to describe things changes over time. As technology evolves the words we use to describe them also evolve to help us differentiate.

It isn't about what you call it or what tools you use. It is about defining a strategy to help you identify what is broken and why things are broken. The ultimate goal is to quickly identify and resolve issues.

Start with the strategy and desired outcomes then look for tools and solutions to support your strategy and goals.

The tools you choose must support your strategy and help you execute on your goals. For example:

  * If your goal is to be the most reliable application, you need tools that can tell you what elements and third parties are impacting reliability.
  * If your goal is to be the fastest application, you need tools that can tell you when response times increase and how your competitors are performing.
  * If your goal is to be the most available application, then your tools should notify you when outages occur.

Goals and objectives won't be met overnight or in a couple of months, it may take multiple iterations before your strategy is fully implemented.

If the tools you are using today are not able to tell you what is broken and why then it's time to look for alternatives. It isn't easy to cut your losses on a tool you have invested millions of dollars on, spent thousands of hours implementing, and bet your career on. But if it isn't answering the critical questions it is the best thing to do. I myself, have had to do just this in 2000 when an APM solution we purchased was not meeting our needs after spending millions on the purchase and trying to get it deployed.

I was recently speaking with a CTO whose company had implemented an APM solution to address all of their IT monitoring needs. They weren't convinced it was meeting all their needs and told me "I spend my time in this tool but still do not know why things are not working."

I set up some tests to see if Catchpoint would be able to provide some insights.

The first thing that jumped out at me was how their Wait time (time to first byte) was very high. At times during the day, it spiked above anything I have ever seen:

![](http://blog.catchpoint.com/wp-content/uploads/2018/06/apm1.png)

> _What I observed looking at trends over a month:_

  * The spikes only occur during certain days of the week.
  * The spikes occur during specific times (see chart below).

Standard Deviation by Hour:

![](http://blog.catchpoint.com/wp-content/uploads/2018/06/apm2.png)

> _Standard Deviation by Day of the Week:_

![](http://blog.catchpoint.com/wp-content/uploads/2018/06/apm7-1024x420.png)

At this point, the data reveals what is occurring - a long time to first byte at certain hours of the day. But we still don't know why so, I decided to call [my friend, robots.txt](http://blog.catchpoint.com/2012/01/19/best_friend_robots/) for some additional insights. The robots.txt file is served using only the HTTP layer, not the application layer. This provides an easy way to identify whether slowness is due to the HTTP layer or application/backend layer.

Comparing the TTFB of the homepage to the robots.txt file we see the homepage is much higher than the robots.txt file. This indicates the issue is with the application layer and not the HTTP layer.

![](http://blog.catchpoint.com/wp-content/uploads/2018/06/apm3.png)

Now, this particular company is pretty cool they are passing some of their internal metrics in the HTML response. We were able to capture and report on these using our Insight capabilities.

In this case, we grabbed Application, Backend, and Front End time which is highly correlated to TTFB.

![](http://blog.catchpoint.com/wp-content/uploads/2018/06/apm5-809x1024.png)

> _Using some of our custom visualization here is another way to look at the same data:_

![](http://blog.catchpoint.com/wp-content/uploads/2018/06/apm6-1024x505.png)

> _Within days we were able to draw the following conclusions:_

  * Something on the back-end causes high TTFB during certain hours of the day, but not every day.
  * The HTTP layer is not responsible for the slowness.
  * The Application time is the one driving the TTFB.
  * The Backend time is fairly stable and does not seem to induce other latency.
  * The Front-End time is responsible for driving end-user slowness and is highly correlated to document complete.
  * The TTFB is very high no matter what, confirmed by comparing the main site to competitors.
![](http://blog.catchpoint.com/wp-content/uploads/2018/06/amp8-1024x443.png)

> _The questions the team should focus on answering:_

  * What is happening with the infrastructure at 3 am during those days?
  * Why are we 3 times slower than our competition?
  * What other telemetry do we have access to that can help answer why the application time is so high?
  * Can we take one of those Catchpoint requests and trace it throughout the system to answer the above questions?

The trend towards observability tools reminds me of the craze around web performance optimization of a few years ago. People would implement automated solutions sold by vendors to optimize their sites and then realize the automatic algorithms broke more things than they solved.

There is no easy fix or [magic pixie dust](http://blog.catchpoint.com/2012/08/03/web-performance-pixie-dust/) for ensuring high availability, high reliability, and optimal performance. Building and revising a monitoring strategy takes time, and sometimes you have to start over. Take the time, observe the data, and ensure it is telling you what is broken and why. Installing a tool does not solve the problem, it helps you discover the source, eliminate the various layers... but it starts with having a team of people that care. Successful companies have a mature customer-centric technology team driven by results, accountability, and responsibility.

[3 Steps to Monitoring in a Connected Enterprise](https://dzone.com/go?i=283437&u=https%3A%2F%2Fwww.xmatters.com%2Fresources%2Freports%2Fmonitoring-connected-enterprise%3Futm_campaign%3D70138000001C2pDAAS%26utm_source%3Ddzon%26utm_medium%3Dweb%26utm_content%3D3-steps-to-monitoring-in-a-connected-enterprise-wp). Check out [xMatters](https://dzone.com/go?i=283437&u=https%3A%2F%2Fwww.xmatters.com%2Fsolutions%2Fmanagement%3Futm_campaign%3D70138000001C2tKAAS%26utm_source%3Ddzon%26utm_medium%3Dweb%26utm_content%3Dxmatters-website).
