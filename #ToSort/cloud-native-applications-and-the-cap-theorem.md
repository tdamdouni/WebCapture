# Cloud Native Applications and the CAP Theorem

_Captured: 2017-03-02 at 10:57 from [dzone.com](https://dzone.com/articles/cloud-native-applications-and-the-cap-theorem?oid=twitter&utm_content=buffer0987a&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Download the [Essential Cloud Buyer's Guide](https://dzone.com/go?i=123025&u=http%3A%2F%2Fpd.internap.com%2Fcloud-buyers-guide-DZ) to learn important factors to consider before selecting a provider as well as buying criteria to help you make the best decision for your infrastructure needs, brought to you in partnership with [Internap](https://dzone.com/go?i=123025&u=http%3A%2F%2Fpd.internap.com%2Fcloud-buyers-guide-DZ).

_[This article is featured in the new DZone Guide to the Cloud: Native Development and Deployment. Get your free copy for more insightful articles, industry statistics, and more!_](https://dzone.com/guides/the-cloud-native-development-and-deployment?oid=cloudarticles)

Building applications for enterprises has come a long way. To simplify a bit, we've gone from simply automating paper processes to using it as an alternative channel for our businesses to becoming the business itself. Parallel to this we've seen the evolution of Moore's law from cheaper, faster, individual hardware to fast, cheap, piles of hardware on demand. If our applications "are the business," and we have access to fleets of cheap machines and infrastructure, what does this mean for the applications and developers in this new era? It means we have to innovate by making changes quickly. We have to build resilient systems. We need to scale to deal with challenges in the world of IoT, big data, etc. Building systems and applications that fit this "cloud era" are a bit different than how we've built them in the past.

In the past, we developers had a lot of safety guarantees that made our job a lot easier. Everything ran mostly co-located. When things failed, we knew where to look and could reason about stack traces from our co-located components. We didn't have to reason much about concurrency or failure conditions with our data because the database solved a lot of that for us. When we called application or infrastructure services we did so with confidence because we were told those services were highly available (whatever that really meant). When we made changes to the data owned by our application, those changes were instantly visible to other components in our application. We could make changes to many components with a single deployment since we owned all of the application. And there are many other assumptions we've lived with, many of which will not hold up in the architectures designed for the cloud era.

When we think about designing applications in a cloud-native world, we focus on three main things:

  1. **Speed of change**: Can we make changes to the overall system without impacting other applications or services?

  2. **Elasticity**: We should be able to take advantage of additional infrastructure and scale our applications horizontally.

  3. **Failure**: Things can and do fail all the time, whether it's computers, network, storage, or just as likely: our own applications.

For this article, I'll focus mostly on the last bullet: designing for failure.

When we build cloud-native applications we are first and foremost building a distributed system. Communication between services and infrastructure happens over the network. Failure happens in all shapes and sizes. Hardware fails. Applications have bugs. Things can be working perfectly fine, but to an observer across the network, they appear to have failed. But services need to communicate and cooperate with each other to make progress. In many cases, they share similar concepts and data. For example, for an online bookstore, a book may be represented in different parts of the system differently. We may have a search service, a recommendation service, and a checkout/order service. All of these have a different understanding about what is a book and how to interpret data related to books. A problem arises when certain details of a book change. All of these services that store information related to a particular book may need to be updated with the new information. How do we deal with this?

_Read the rest of this article and a lot more in:_

![Cloud Guide](https://dz2cdn1.dzone.com/storage/rc-covers/4448764-dzone-2017cloudcover.png)

**[DZone's Guide to the Cloud:** Native Development and Deployment](https://dzone.com/guides/the-cloud-native-development-and-deployment?oid=cloudarticles)

Including:

  * Industry Research Data
  * Articles Written by Industry Experts
  * Cloud Architecture Infographic
  * Directory of the Best Tools & Solutions

The Cloud Zone is brought to you in partnership with [Internap](https://dzone.com/go?i=109853&u=http%3A%2F%2Fpd.internap.com%2Fbare-metal-101-pr). [Read Bare-Metal Cloud 101](https://dzone.com/go?i=109853&u=http%3A%2F%2Fpd.internap.com%2Fbare-metal-101-pr) to learn about bare-metal cloud and how it has emerged as a way to complement virtualized services.

Opinions expressed by DZone contributors are their own.
