# DDD: Part I (Introduction)

_Captured: 2017-12-15 at 20:22 from [dzone.com](https://dzone.com/articles/ddd-part-i-introduction?edition=345096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-15)_

[Learn more](https://dzone.com/go?i=250324&u=http%3A%2F%2Fblog.scalyr.com%2F2017%2F08%2Fcareerbuilder-resolves-customer-issues-5x-faster-scalyr%2F) about how CareerBuilder was able to resolve customer issues 5x faster by using Scalyr, the fastest log management tool on the market.

The first time I heard about DDD (**Domain Driven Design**, not _Deadline Driven Design,_ for sure), I was still working as a Senior Java Developer for Hewlett-Packard at its Development Center in Cyberjaya, Malaysia. I wasn't quite interested in the topic since it was difficult to get a good resource during that time. Someone told me to find Eric Evan's book ("the blue book"), and I got the book and added it to my PDF collection.

During this time, DDD was quite new (especially in Indonesia), thus only a few companies had successfully implemented this new thing. And somehow, I found that many DDD resources were too difficult to be grasped by most of the readers (i.e. they are too abstract and lack of good examples). Therefore, i'm planning to pick up this awesome topic and write it in a series, equipped with an application sample to be followed step by step.

This is the first part of another series those are still in my head as follow:

  1. _DDD Part I, Introduction -> You are here_
  2. DDD Part IV, DDD and Microservices (coming soon)
  3. DDD Part V, ES and CQRS -- DDD's best part (coming soon)
  4. DDD Part VI, Application Sample (coming soon)

In this first part of Introduction, I would like to start with some basic concepts as written below:

  1. What is DDD all about?
  2. How do we get started?
  3. What should we avoid in DDD?

Let's get started!

## 1\. What Is DDD All About?

To start this section, I'd rather take the definition from one of DDD's communities, dddcommunity.org, that describes DDD as an approach to developing software for complex needs by deeply connecting the implementation to an evolving model of the core business concepts.

As the definition implies, DDD is suitable for you if you're building software that has complexity in its business process (business domain). So, not every software is suitable for DDD (e.g. CRUD applications aren't suitable for it since they're not very complex).

Teamwork is very important within DDD since you need to keep in touch with the users/clients (a.k.a Domain Experts). Moreover, you build the software for them, not for you (you got the point right). Just like someone said: "the software can fail either in two ways, you build the things wrong or you build the wrong things." In that case, you have to ensure that you understand the business that you're going to build. This is what DDD is all about.

To summarize, DDD can be described as a technique for developing software that focuses on collaboration between technical experts and domain experts. Therefore, we must keep focus with the domain experts instead of the nitty-gritty details of the technical stuff.

## 2\. How Do We Get Started?

First things first, as mentioned earlier, the big point is to keep in touch with the **business**/**domain expert**. I will recap several points those we can use as guidance while we have a discussion with the domain expert:

  1. Learning about the _problem domain_, i.e. the specific problem the software you're working on is trying to solve. Look at the big picture of the current business process.
  2. Breaking the _domain_ into _sub-domains._
  3. Focusing on one _sub-domain_ at a time with the **domain expert**, and always use [ubiquitous language](http://martinfowler.com/bliki/UbiquitousLanguage.html) to define working out terminology.
  4. Creating a [bounded context](http://martinfowler.com/bliki/BoundedContext.html) between _sub-domain._ Again, ubiquitous language should always be used throughout the bounded context, from conversations to code, in the diagram, on the whiteboard, in the design document, team discussion, etc. The point is to use the bounded context everywhere.
  5. Ideally, there will be a different team, codebase, and database for each bounded context.
  6. Since everyone is working for their bounded context, so they are free to change anything within their _context_.
  7. For all _cross-cutting concerns_ those are shared between bounded context (we call it **shared kernel**), any changes should be known and agreed between all team in every bounded context.
  8. Always stay focused on the domain's _behaviors_ rather than domain's _state _(favor a [rich model](http://www.slideshare.net/chris.e.richardson/building-rich-domain-models) over an [anemic model](http://www.martinfowler.com/bliki/AnemicDomainModel.html)).

To summarize, always use ubiquitous language (i.e. same terminology) across the team, break the _domain_ into smaller _subdomains_ and give an isolation (i.e. bounded context) by defining the boundary and think about how the _subdomain_ within the bounded context can communicate to each other using **interfaces**/**crafted software contract**.

## 3\. What Should We Avoid in DDD?

On the other hand, during our DDD implementation, we need to be careful of certain practices those are too common among software developers. These are:

#### **1) Using a Data-Centric View When Modeling the Problem Domain**

Usually, the data model is the first thing that an architect/developer would start to design. They always consider that data is the most important thing because data is all that we need to report. If you start with DDD, you must change this mindset. Data on its own is meaningless. Only logic gives data a meaning, and the same data can have a different meaning in different contexts. Therefore, we must start with **context** and **logic** instead of data.

#### 2) Focusing on Implementation Details Like Entities, Value Objects, Services, Factories, and Repositories Instead of the Core Concepts

Entities, value objects, repositories, and so forth don't have a meaning until we defined the ubiquitous language, bounded contexts, and the interfaces/crafted software contract. If we start to early with the implementation details like entities, then it's a good chance that the result would be an anemic domain surrounded by a lot of services and business logic scattered everywhere.

#### 3) Using Generic and Developer-Specific Terms and Concepts When Implementing the Application

We should never use concepts like save, update, delete, handle, manage, etc. Those concepts are too technical- abstract concepts with no specific meaning. Instead, we must stay focused on the business concepts. Those aforementioned concepts (i.e. save, update, etc) are not related to business concepts. To understand this, I encourage myself to always imagine the client running his errands/business without computers (doing specific tasks manually). So, always think from the business/domain expert perspective, and give a clear context on it. Avoid generic terms that can lead to different meanings in different, non-specific contexts.

#### 4) Overrating DB Transactions Instead of Focusing on the Business Processes or Transactions

Within DDD, business transactions are more important than DB transactions. DB transactions are _ACID_, _strongly consistent_, and _short running_, while business transactions are not. In fact, in the real life, we don't know about DB transactions, we just know about business transactions. For example, imagine when you are sitting in a restaurant and order some foods or beverages. Within the order transaction, realize it or not, there will be a process with some asynchronous tasks with many possible inconsistent state changes; by the end, all states will be consistent (_eventually consistent_). This blackbox process works, is scalable, and is widely acceptable to everyone. Therefore, with DDD, do not ever think about DB transactions. Instead, always think about the real world processes, such as actions (behaviors) and their possible outcomes, or how to compensate for the actions if failures occurs.

You don't have to understand all the aforementioned points for now. I know that most application developers are not too familiar with the idioms and peculiarities of those concepts. Just keep reading for now, and hopefully, it will become clear when the other parts coming.

**[Find out more](https://dzone.com/go?i=250325&u=http%3A%2F%2Fblog.scalyr.com%2F2014%2F05%2Fsearching-20-gbsec-systems-engineering-before-algorithms%2F) about how Scalyr built a proprietary database that does not use text indexing for their log management tool.**

Opinions expressed by DZone contributors are their own.
