# Where Does Deep API Monitoring Fit Into APM?

_Captured: 2017-03-29 at 01:56 from [dzone.com](https://dzone.com/articles/where-does-deep-api-monitoring-fit-into-apm?oid=twitter&utm_content=buffer0ff3c&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

_[This article is featured in the new DZone Guide to Performance: Optimization & Monitoring. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/performance-optimization-and-monitoring)_

APIs are the backbone of modern applications -- web and mobile alike. Even though end users may be oblivious to underlying APIs when they are using web and mobile applications, API issues can affect them directly. When APIs fail, one or more critical functions in the application become unavailable. It's even worse when APIs seem to be working but are functionally incorrect. That means end users can use the application but the actions return unexpected results. That's where sophisticated API monitoring comes into play. Just checking an API endpoint for 200 OK is not enough when you are dealing with chained API transactions, where each call depends on the results from previous API calls. It's about time we revise the definition of APM to include advanced API monitoring functionality.

APIs are taking the world by a storm. As you strive to deliver world class web, mobile, and SaaS applications, make sure the APIs that power them are running smoothly.

![Image title](https://dzone.com/storage/temp/4782212-screen-shot-2017-03-27-at-31750-pm.png)

SmartBear's The State of API 2016 survey queried both API consumers and producers on a variety of topics impacting the API space. The survey had more than 2,000 respondents from more than 50 industries and 100 countries. While the focus of this survey was not API monitoring, it became clear to me from the results that many of the concerns of both API consumers and producers can be addressed through deep API monitoring. High quality delivery of APIs is critical to ensuring that the web and mobile applications that depend on them are meeting the increasingly high expectations of users. Some highlights of that survey include the following:

The top three concerns of API Consumers are:

  * Ease of use

  * Performance

  * Service reliability/uptime

The top two measures of success identified by API producers are:

  * Performance

  * Uptime/availability

The top two barriers to solving API issues are:

  * Determining root cause

  * Isolating the API as the cause of the issue

![Performance Guide](https://dzone.com/storage/temp/2579425-performanceguide.jpg)

> _Performance Guide_

_Find this article and much more in..._

**[DZone's Guide to Performance: Optimization and Monitoring](https://dzone.com/guides/performance-optimization-and-monitoring?oid=performanceplug)**

Including:

  * Survey findings from over 500 developer responses

  * Articles written by top Performance experts

  * "What Ails Your Application" Infographic

  * Directory of performance optimization and monitoring tools

Looking at the results from these three questions, it is clear that performance and uptime/reliability are paramount to both producers and consumers. Adding to the clear need for performant and reliable APIs, ease of issue diagnosis also emerged as a key trend. Knowing exactly which APIendpoint is failing within a chain of successive calls is a clear operational need.

Another key takeaway of the survey is that both API consumers and producers are in alignment on the key measures of success for API delivery. Since it appears that all involved agree that the need for deep API monitoring is obvious, what are the key attributes of a successful API monitoring approach?

![Image title](https://dzone.com/storage/temp/4782207-screen-shot-2017-03-27-at-31355-pm.png)

  * Just checking if a single API endpoint is available is not enough when your applications depend on APIs. It's essential that any monitoring tool also be able to measure and monitor performance and functional correctness. Deep API monitoring provides three lenses of API monitoring -- availability, performance, and functional correctness. Knowing with certainty that the API is available, fast, and fully functional must be the standard going forward.

  * API endpoints are not called in isolation by web and mobile applications -- so your monitoring shouldn't rely on simple endpoint availability checks. A monitoring platform must be able to execute and monitor chained API transactions, where API endpoints are invoked in sequence with contextual data passed from one call to the next. This is how your critical web and mobile applications consume those APIs and that is how you must monitor them.

  * API monitors should be able to be easily created by reusing your existing test cases as the foundation for your monitors. In addition to freeing up development and operational resources from monitor creation duties, leveraging existing test cases provides the added benefit of allowing monitoring to become a key part of each version of the application as it progresses through the development lifecycle. With increased use of agile development, continuous integration, and delivery methodologies, pre-production monitoring makes more sense than ever.

  * In addition to the above-mentioned API-specific attributes, a monitoring solution will not be successful without robust scheduling, playback, and alerting capabilities. You will only reap the benefits of proactive monitoring if you are getting accurate alerts and results in real time.

  * Another important consideration when monitor in your APIs is location. Whether around the globe or behind your firewall, it is important to monitor where your users or API consumers are. Increasingly, more customers are concerned about users spread across both a mix of physical geographic locations and internal points of presence inside your infrastructure. These internal locations can be physical data centers, private cloud deployments, various office locations, or even vendor and customer locations.

You may be a producer or a consumer of APIs. You may be both -- and we are increasingly seeing this scenario in our customer base. In either case, proactive deep API monitoring is critical to ensuring you are delivering and receiving excellent performance and reliability from the APIs that you depend on to run your business. The same holds true for the operations teams tasked with supporting the APIs and applications that use them. They need to know the health of those applications in real time, and they need to be able to quickly resolve issues when they occur. Deep API monitoring provides the foundation to do this.

Without deep API monitoring, your customers and users are the canary in the coal mine, informing you far too late of service delivery failures.

_[This article is featured in the new DZone Guide to Performance: Optimization & Monitoring. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/performance-optimization-and-monitoring)_
