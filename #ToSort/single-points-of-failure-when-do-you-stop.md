# Single Points of Failure: When Do You Stop?

_Captured: 2018-08-17 at 17:28 from [dzone.com](https://dzone.com/articles/single-points-of-failure-when-do-you-stop?edition=385389&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-08-17)_

Maintain Application Performance with real-time monitoring and instrumentation for any application. [Learn More!](https://dzone.com/go?i=281422&u=https%3A%2F%2Fwww.nastel.com%2Fapplication-performance-monitoring%2F%3Futm_source%3DDZone%26utm_medium%3DPrePostRoll%26utm_campaign%3DDZone2018%2520for%2520all%2520pre%2Fpost-roll%2520text%2520ads%3A)

Understanding that you have Single Points of Failure in your system is half the battle, knowing when to stop going down the rabbit hole is the other half.

I've had discussions with teammates who argued that my managed Redis cluster was a SPOF because most of my services actually needed it for some task. It can definitely be a chokepoint if it's not properly optimized, but given our use case and business needs, it made no sense to even start thinking about contingencies if that cluster were to fail, because if it did, a lot of other things would also fail and honestly, our SLAs did not cover that much availability.

So, when do you stop and say "This is good enough"? In my opinion, a good tool for that is the SLA you sign with your users or clients regarding the performance, availability, and overall quality of your service. It usually boils down to a number, a percentage that is between 90% and 100% (i.e 99% also known as "two nines" or 99.99% which is known as "four nines") and is in the context of a period of time (the most common ones are a week, a month or even a year).

You basically take that percentage from the number of minutes in the time period defined, and you have how much uptime your system is expected to have in that timeframe. But reaching that number is not an act of magic or just pure guesstimation work, it's a process that if done correctly, requires a lot of analysis and discussions.

To give you a quick overview (you should dig deeper into this subject if you're not familiar with the concepts that are coming), the tools you'll need to properly find that number are called SLI and SLOs.

## SLI, or System Level Indicator

These are metrics you'll develop and measure constantly to understand how your system is performing. These are not strictly hardware or performance related, they're business related. In some cases, they might be obvious such as counting how many web pages load within an acceptable timeframe (I.e 100ms) on web apps. But in others, they might not be, such as comparing the number of billing requests in your web-server log files against your database records at the end of the day and making sure the percentage of correlation is close to 100%. These indicators should be set based off of conversations between developers, DevOps/sysadmins or whatever flavor of them you have on your team and the business.

All three parts of the equation must be present and must give their opinion as to what makes an indicator relevant and measurable. Each SLI should have a basic description regarding what it's meant to measure from a business perspective and then a detail description on how it needs to be measured from a technical perspective. Basically the more documentation you can write about them, the easier it'll be to both maintain them and review them in future iterations.

In order to properly define your SLIs you have to remember to keep them user-centric (it might be a good idea to define them based off of the user journeys for your application) and to think on metrics that can be measured in the form of "good events" divided by the "total number of events" times 100. This will provide scenarios like: "proportion of homepage requests loading in under 100 ms."

There are some pre-defined SLIs types that might come in handy to guide you while thinking them up, they are related to the type of sub-system you're trying to analyze, for example:

  * If you have a **user-facing** section of your application, you might want to think of going for SLIs of type availability, latency, and throughput. Or, put another way, "Can my system provide a response to a request?", "How long does it take to do it?", and "How many requests can it handle?"

  * If on the other hand, you have a **storage system** you want to keep track of, you might want to consider going with latency, availability, and durability. Also known as "How long does it take to read and write?" or "Can we actually request data from it?" and "Is the data there if we need it?"

  * Finally, ** Big Data** projects have specific types as well, such as throughput and end-to-end latency. For instance, you can ask things like "How much data are we processing?" and "How much time does data need to go from ingestion to final storage?"

## SLO or System Level Objective

These are the objectives you want to aim for on each of your indicators. They're percentage numbers in a timeframe, just like the SLAs, but internal. They're not shared with your users and customers, since they usually act as the upper limit of what you expect your system to do, not exactly what you want to state that your system _can _do to the outside world (in other words, try not to shoot yourself in the foot by sharing these values).

You should arrive at them based on your understanding of your user's needs, which is why having your business in these meetings is great. Sometimes techies like the developers or the sysadmins will only think from their technical expert positions and they will forget about what the user actually feels like and wants from the application they're building. This is not to say they shouldn't help define the objectives, this must be a group effort to avoid leaving something out.

These are crucial because, in the context of rooting out SPOFs, you need them to understand when to stop working on that and when to start shipping.

When it comes to the amount of SLIs and SLOs to write, as a rule, you can probably assume one SLO per SLI and up to 3 SLIs per user journey. If you start seeing a lot of relevant SLIs being defined as a result of these meetings, you should consider grouping them into more generic topics, for instance if you happen to have 3 or 4 different SLIs that talk about loading time of web pages, you can probably collapse them all into a generic one that's not related to a single user journey but to several (or maybe all of them).

### What Happens When We Don't Meet Our SLOs?

Finally, and although not entirely related to SPOFs, if we're talking about SLIs and SLOs, we need to understand what to do when those numbers aren't met. Because let's be honest for a second here, you can identify your key user journeys and create all the SLIs you want for them. You can sit down for weeks with the business, your DevOps and your developers and come up with realistic and reachable SLOs for those indicators. But you also have to expect the system to fail and some point and not meet those numbers.

When that happens, you should already have a plan for it in your deployment and development policies. You should be keeping track of the failures and count the time your system is not conforming as expected. If this time exceeds a given pre-set amount (some people call it "Error Budget"), then you need to already have defined what to do. For example, holding back work on new features until major bugs get fixed, or canceling new deployments until bugs causing the issues are found and fixed. These are all strategies you need to think of while working on your indicators and objectives.

## Agreeing on Your SLAs

The final step in this process is going to be agreeing on your SLAs, which obviously will depend on your business case and use cases, but should be kept under the objectives, with the intent of preventing your user from expecting excellence in a scenario where it might not be 100% up to you and your team (service providers might fail to deliver, and even if you don't, your users will fault you and see your services as the one not fulfilling the pre-defined agreement.

Collect, analyze, and visualize performance data from mobile to mainframe with AutoPilot APM. [Learn More!](https://dzone.com/go?i=281423&u=https%3A%2F%2Fwww.nastel.com%2Fapplication-performance-monitoring%2F%3Futm_source%3DDZone%26utm_medium%3DPrePostRoll%26utm_campaign%3DDZone2018%252520for%252520all%252520pre%2Fpost-roll%252520text%252520ads%3A)
