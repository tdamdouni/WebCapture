# Understanding and Monitoring Dependencies in Cloud Applications

_Captured: 2017-04-02 at 18:48 from [dzone.com](https://dzone.com/articles/understanding-and-monitoring-dependencies-in-cloud?oid=twitter&utm_content=buffere3f00&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

_[This article is featured in the new DZone Guide to Performance: Optimization & Monitoring. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/performance-optimization-and-monitoring)_

It's been a nerve-wracking few months for teams managing cloud applications. In October 2016, a DDoS impaired Dyn's DNS services for hours, rendering unavailable myriad sites and services across the Internet. And in an unrelated, but similarly impactful event, the outage of AWS S3 at the end of February 2017 caused widespread and unpredictable collateral damage. With more applications leveraging more services hosted in just a few infrastructure environments, how can we make sense of application dependencies? How can we adopt a monitoring strategy that clearly accounts for the risks of improbable but hugely catastrophic service disruptions?

We'll dig into how you can identify and manage cloud dependencies by:

  * Understanding underlying cloud architectures and failure scenarios.
  * Getting a handle on the API connections in your app and in customer interactions.
  * Developing a comprehensive monitoring strategy based on these requirements.

## Making Sense of IaaS Architectures

Public cloud environments are a popular and powerful way to gain access to advanced services that would be costly to build or maintain on your own. But these services, from firewalls to [DDoS mitigation](https://aws.amazon.com/shield/) to [globe-spanning databases](https://cloud.google.com/spanner/) to data streaming platforms, are themselves composed of many other services. Like a digital matryoshka doll, it can be hard to know just how many layers and dependencies are bound up inside. In the case of the AWS S3 outage, many operations teams were surprised at how many different AWS offerings failed. They had not appreciated, and AWS had not communicated, just how interdependent various services were.

In your own data center, the failure of your entire file storage system would have a dramatic impact. In the cloud, it is the same story. The oldest services are building blocks from which other services are built (as represented in the AWS logo), and are foundational and critical to almost all other services. Basic compute (AWS EC2), storage (AWS S3), and networking (underpinning it all) are critical services that you should be monitoring and evaluating for failure scenarios. The same goes for Microsoft Azure (VMs, Blob Storage) and Google Cloud (Compute Engine, Cloud Storage). If you use cloud services that depend on these foundational elements, make sure they are part of your monitoring strategy.

Developing for the cloud also requires an understanding of failure isolation. AWS is built around the concept of regions, with previous outages typically corresponding to a single region. Unfortunately, many developers don't invest (sometimes wisely, sometimes naively) in cross-region failover strategies. So when US-East-1, the first and largest of the AWS regions has an issue, the impact is unmistakable. Some services, like Google Spanner, have different isolation mechanisms that need to be evaluated.

When it comes to architecture planning, performance monitoring, and optimization, you'll want to monitor each potential failure domain. So if you are using cloud services in 4 different regions, make sure that you are collecting metrics on each.

## Identifying API Usage in Applications

Your applications depend on the specialized functionality of third-party applications, typically accessed via APIs. Don't think you rely on APIs for critical capabilities? Think again. APIs are very common in modern applications, hiding in plain view a complex set of dependencies. Some of these external services are important for just small portions of functionality. But many impact customer experience and revenue generation in fundamental ways.

What kind of APIs should you be monitoring? The specific APIs will be unique to your application, but some examples include:

  * User authentication is accomplished with single sign-on APIs and services to detect fraud or abuse.
  * Pricing and merchandising require the complex integration of many back-end applications to show an accurate price to a customer.
  * Supply chain and logistics APIs ensure shipping is fulfilled.
  * Payment gateways and billing systems are necessary to transact with your customers.
  * Advertising is the lifeblood of many media sites and relies on APIs to display targeted products, images, descriptions, and reviews in real time.
  * Customer chat, phone, and CRM systems use APIs to seamlessly integrate with sites, and typically are the difference between successfully communicating with your users and being dead in the water.

There are myriad APIs that make up your overall customer experience. Getting a handle on performance dependencies requires a clear appreciation for the APIs used by your application. You enumerate your APIs in various ways: observing domains of objects on web pages, looking at connection logs from your application servers, and using documentation (well hopefully it exists!) of embedded services.

![Performance Guide](https://dzone.com/storage/temp/2579425-performanceguide.jpg)

> _Performance Guide_

_Find this article and much more in..._

Including:

  * Survey findings from over 500 developer responses

  * Articles written by top Performance experts

  * "What Ails Your Application" Infographic

  * Directory of performance optimization and monitoring tools

## Monitoring External Services, Infrastructure, and APIs

Once you've figured out what to monitor, the next step to operational awareness is collecting data. There are several key elements you'll want as part of your monitoring toolkit:

  1. **Log errors** of failed API connections and requests. Track trends over time to understand services that fail under your application load.
  2. **Actively monitor** API servers and infrastructure services. Regularly test the reachability, response time, and response codes of these services with preconfigured tests. Don't know what targets to test? Your cloud provider typically has canary servers or endpoints ([here is the list for AWS](http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region)) they can point you to.

Taken together, these two approaches will give you an understanding of baseline performance and specific issues as they occur. As a bonus, tying both of these methods together with a correlation engine such as Splunk can be an effective way to make sense of seemingly disparate events that are actually all related.

## Four Steps to Tackling Dependencies

Cloud-based applications, and the business models that they support, rely on an increasingly diverse set of underlying services, tied together through APIs. The availability and efficacy of APIs and infrastructure services has, therefore, become a key element in monitoring and optimizing cloud applications.

As you are building out your next cloud application or rethinking ways to meet your SLAs, follow these four steps:

  1. **Map** key cloud infrastructure and application APIs. It can be a monster task but you can't optimize or mitigate services you don't know about.
  2. **Test** each of the critical service dependencies with a combination of logging and active monitoring. Logs will give you forensic evidence while active monitoring will provide a heads up to impending trouble.
  3. **Validate** functionality and performance with event correlation, alerting, and baselining. With interdependent services, you may not know likely failure scenarios until you correlate your data.
  4. **Optimize** performance over the long run to influence vendor or architectural decisions. From choosing vendors to investing in redundancy, it all starts with having clear insights from your monitoring data.

The next time a major cloud outage or service disruption hits, you'll be well aware of what is wrong, and with the proper planning, well positioned to ride out the storm.

_[This article is featured in the new DZone Guide to Performance: Optimization & Monitoring. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/performance-optimization-and-monitoring)_
