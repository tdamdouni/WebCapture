# How to Start Your Journey in Microservices - Part 1

_Captured: 2018-02-14 at 12:10 from [dzone.com](https://dzone.com/articles/how-i-started-my-journey-in-micro-services-and-how?edition=362092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-13)_

Learn the Benefits and Principles of [Microservices Architecture for the Enterprise](https://dzone.com/go?i=274453&u=http%3A%2F%2Ftransform.ca.com%2FAPI-microservice-architecture-for-the-enterprise.html%3Fcid%3DNA-DSP-API-AEL-000195-00001674-000000492%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dmicroservices_api_acquire%26utm_content%3Dna_eb1-microservice-arch-ent-ddc-preroll%26mrm%3D)

Architecting an application using Microservices for the first timers can be very confusing. This article is very relevant if

  * You are you beginning to develop an application that can scale like Amazon, Facebook, Netflix, and Google.

  * You are doing this for the first time.

  * You have already done research and decided that microservices architecture is going to be your secret sauce.

Microservices architecture is believed to be the simplest way of scaling without limits. However, when you get started, a lot of considerations are going to confuse you. Questions arose as I spent time learning about it online or discussing it with a team:

  1. What exactly is a **microservice**? 
    1. Some said it should not exceed 1,000 lines of code.
    2. Some say it should fit one **bounded context **(if you don't know what a bounded context is, don't bother with it right now; keep reading).
  2. Even before deciding on what the "micro"service will be, what exactly is a **service**?
  3. Microservices do not allow updating multiple entities at once; how will I maintain **consistency between entities**? 
  4. Should I have a **single database cluster **for all my microservices?
  5. What is this **eventual consistency** thing everyone is talking about?
  6. How will I **collate data **which is composed of multiple entities residing in different services?
  7. What would happen if one **service goes down**? How would the **dependent services **behave?
  8. Should I make a **sync invocation **between microservices to always get **consistent data**?
  9. How will I manage **version upgrades **to a few or all microservices? Is it always possible to do it **without downtime**?
  10. And the last unavoidable question - how do I **test **the entire application as an **integrated application**?

Hmm... All of the above questions must be answered to able to be understand and deploy applications based on microservices.

## The Journey to Microservices Land

Now, I'll share my complete journey towards microservices.

We started our research by

  * Going through YouTube videos of Netflix's architecture, and

### Divide and Rule

We understand that if we are developing a big application as a single Java process (single JVM), then its scale is limited by the capacity of the underlying single hardware. We cannot keep optimizing the code infinitely. We must architect our application to be able to work on multiple machines as a single coordinated application, so we need a way to break our application into smaller components which can be deployed and scaled independently of each other.

### Domain Driven Design

While researching the methodology to break up the application into these components and also define the contract between them, we found the [Domain Driven Design](https://dzone.com/refcardz/getting-started-domain-driven) philosophy to be the most convincing. At a high level, it guided us on

  * How to break a bigger domain into smaller bounded contexts.

  * How to define contracts between them.

These smaller components are the microservices. At a finer level, domain driven design (aka DDD) provides tactical methods to help us with

  * How to write code in a single bounded context.

  * How to break up the entities.

  * How to become eventually consistent.

  * Understanding and defining aggregates.

  * Event Sourcing and CQRS.

After getting the answer to "how to break the application into microservices," we needed a framework for writing code on these guidelines. We could come up with a framework of our own, but we chose to not to reinvent the wheel. [Lagom](https://www.lagomframework.com/) provides all the functionality that we require to do microservices, like

  1. Writing services.

  2. Testing services.

  3. Integration with **Kafka**, the **messaging framework **for message passing between services.

From the experience and consultation so far, I would recommend using Lagom, as it greatly simplifies setting up the developer environment with all the right nuts and bolts and tools already in place.

This is Part 1 in a series of articles. I have explained how we got our direction on getting started with microservices. In the next article, I will talk about what exactly Domain Driven Design is and how to break up a real example domain into different microservices.

### Recommended References

Thanks to the blogs by [Vaugh Vernon](https://vaughnvernon.co/), [Udi Dahan](http://udidahan.com/), [Chris Richardson](http://www.chrisrichardson.net/), and Microsoft. A few specific references:

  1. Youtube for Event Sourcing, CQRS, Domain Driven Design, Lagom.

  2. Domain Driven Design Distilled and implementing Domain-Driven Design, by Vaugh Vernon.

Microservices for the Enterprise eBook: [Get Your Copy Here](https://dzone.com/go?i=274454&u=http%3A%2F%2Ftransform.ca.com%2FAPI-microservice-architecture-for-the-enterprise.html%3Fcid%3DNA-DSP-API-AEL-000195-00001674-000000493%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dmicroservices_api_acquire%26utm_content%3Dna_eb2-microservice-arch-ent-ddc-postroll%26mrm%3D)
