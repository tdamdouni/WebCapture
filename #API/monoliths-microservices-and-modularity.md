# Monoliths, Microservices and Modularity

_Captured: 2018-06-06 at 21:36 from [dzone.com](https://dzone.com/articles/monoliths-microservices-and-modularity-1?edition=376267&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=microservices%202018-05-09)_

One of the biggest problems when working in IT business is for sure, that in contrast to disciplines like biology, we are lacking a common vocabulary. There is also no clear definition of what the term "Microservice" stands for. In November 2017 I ran a survey on Twitter, asking the community if building microservices is all about the size of the particular services or not. The result was close to a draw (I know it should be: "too monolithic"):

![Image title](https://dzone.com/storage/temp/8981699-screen-shot-2018-04-30-at-25628-pm.png)

> _See this poll on Twitter_

So when even this is not clear, how can we ever come to a conclusion when discussing the pros and cons of an architectural style like this? No wonder so many discussions are getting us nowhere. But what actually most people agree upon are the following points:

  * They are usually modeled around a business domain (or capability). They do one of these things well, and usually rather nothing else.
  * They can be deployed independently.
  * They can run on separated processes, communicating with each other over the network.
  * Communication usually using REST APIs and lightweight messaging.
  * They can be easily replaced, and are not designed for reuse like in times of SOA.

All these aspects of microservice architectures should result in gaining the following advantages:

  1. The independent deployments enable independent development of the particular services.
  2. The given separation of microservices will isolate their failures from each other during operation.
  3. The network separation will also enable total flexibility on the technologies being used per microservice.
  4. All this will naturally enforce a modular structure, which will make maintaining the software platform easy.
  5. They scale individually.

In this post, I want to have a look at this expected advantages, and if the microservice architectural style does live up to its expectations. Especially when compared to monolithic architectures. To do so, we are still lacking the definition of the term "Monolith." Some use that term for software, that grew to a total mess, completely lacking any structure. For this, I will rather use the term "Big Ball of Mud" (BBoM). A monolith according to my definition is rather a software, built with one technology and based on modules that interact using the mechanisms of the particular technology they are built with. So the difference between microservices and monoliths is, that in a microservice architecture the modules are distributed, whereas in a monolith they are not. A BBoM can be distributed too, so this is certainly not a unique selling point of monolithic architectures.

## 1\. Independent Development

The problem: In a monolithic architecture different projects will be working on different features concurrently on the same codebase. This is, without any doubt, a clear advantage of microservice architectures. It is actually very hard, in a big monolithic codebase, to separate the ongoing development efforts of the employees from each other. If you have ever tried to feature-branch the code in the SCM, then you are most likely aware, that this is a pretty bad idea. It will just move the problem to the merge at the end of the project.

But actually, there is an alternative option for monoliths, even when it will not work as smooth as it would in a microservice architecture. A developer can "hide" her/his new features behind a feature switch, that can be activated or not. First, the automated testing will cover the old featureset, as well as the new one. As soon as the tests for the new features are fine, the switch can be activated in production stage as well. If any troubles occur there, it can be switched off again easily. Here a sample code snippet, implemented using the [togglz](https://www.togglz.org/) library for Java:

## 2\. Failure Isolation

Failure isolation is another big advantage of microservice architectures, or rather of any kind of distributed system. In case a service instance runs short of memory or CPU due to a bug in one of the services, this will not affect the rest of the system as easily as it would in a code monolith. If you managed to separate the features and functionality implemented by the particular (micro)services, it is possible that the rest of the system remains available for the user. To achieve such a kind of graceful degradation it makes sense to utilize patterns like Circuit Breaker or Bulkhead. But this only comes with a downside: The lot of communication over the network between your microservices will add another possible "point of failure" to your system.

But what are the alternatives for monolithic architectures? The question is: How can you make a monolith as robust against breakdown as possible? An underestimated option is constant long-running automated load testing. If you just record your load tests with a tool like [JMeter](http://jmeter.apache.org/), it will actually be hard to react to changes of the API of your monolith, as the recorded test case will be very hard to maintain. Usually resulting in the recorded load test being thrown away. This is why I recommend using a tool like [Gatling](https://gatling.io/) where you can actually script your load test. [Flood IO](https://flood.io/) is an interesting opportunity from Thoughtworks 2017 techradar to run Gatling test cases in the cloud.

So just like independent development, failure isolation is another advantage of microservice architectures. But overall robustness is not a distinctive feature of microservices exclusively.

## 3\. Totally Independent Choice of Technology

When you utilize microservices, you can actually choose the technology, that one of them is running upon, per service. That is true, and not so easily done with a monolith. To some extent, you can also do it with a monolith. Imagine a situation where you are using an RDBMS underneath your monolith, and you want to offer a decent full-text search for the user, this will not be much of a problem, as even a monolith can use an additional instance of an [ElasticSearch DB](https://www.elastic.co/de/) that the data is replicated to. Why not? But you cannot choose the whole technical platform per module as you can with a microservice architecture. That is certainly true.

But: I do believe that this feature of microservice architectures is highly overrated. Many of the big famous platforms in the web are actually built on boring PHP technology stacks with a boring MySQL underneath. They do just well, serving billions of requests per month quickly and flawlessly. I usually even recommend using the most boring technology that is still sufficient for the particular use case. Boring old technologies are mostly stable, well established and it is easy to find employees with appropriate skills on the market. For example, there is a huge advantage in using a classical RDBMS instead of one of the new NoSQL DBs if appropriate. SQL is a very well defined standard, and if you use an RDBMS, it should be fairly easy to switch the concrete database technology (the SQL dialect and some other specialties will create some effort though).

## 4\. Modularity

I think one of the main reasons why microservices are hyping so much currently is, that with microservices the developers will be forced to apply some kind of modularity to the solution. When you try to achieve a fine-grained distribution of components, you will not likely be able to forget about the modularization of the codebase. But actually we will later also talk about the [disadvantages](http://improve-it.solutions/20171219_Monoliths-Microservices-and-Modularity.html#MicroservicesDisadvantages) of building distributed systems, so the question arises if all the effort is worth it?

Actually, I do not think so. There are other options to enforce modularity, even if you agree with me that the buzzword "governance" is not a simple solution. I think it is all about using the right tool, like [Sonargraph from hello2morrow](https://www.hello2morrow.com/products/sonargraph), and constantly reporting some structural metrics and the technical debt of the solution to the management and all employees. If you want a very simple solution, that will make it impossible to have an accidental package structure in Java you can simply run the following code snippet in a Unit-Test. If the structure is free of cycles, developers and/or architects will not be able to do anything anymore, they will just have to think about their structure!

![Image title](https://dzone.com/storage/temp/8981700-screen-shot-2018-04-30-at-25735-pm.png)

Does all this seem familiar? To me, it does, as I do believe that we actually had all this before. It was called Test Driven Design back then (TDD). At some point, software architects realized that it was indeed very hard, or even impossible, to create unit-tests for an unstructured codebase (a BBoM). So they recommended starting with the development of Unit Tests before coding the solution so that this cannot happen anymore. But this also brought us unnecessary abstractions like interfaces, just to be able to create a test-stub to make sure you can unit-test the particular feature. Or methods that should be private but were made public to be able to test them, clearly violating the information hiding principle. These are the reasons why I was never a huge fan of TDD.

## 5\. Scalability

Monoliths don't scale, at least according to the microservice community. But they also claim that a duel between Godzilla and King-Kong would be won by microservices. So we will have to ask ourselves if that is true. Scaling can mean increasing CPU and memory (vertical scaling), but that does have only limited potential. The interesting question is, if it is possible to horizontally scale a monolith, which means if we could add instances of a monolith in parallel, and increase its load-bearing capacity by that. There are usually 2 factors that limit the scalability of a monolith. The first one is application state. But some technologies offer the possibility to replicate it between the instances, and if not you can still move it to the client (like the browser) or to the database of the monolith. Which then makes the database the only limiting factor of horizontal scalability that is left.

If you manage to separate the data that needs writing atomic transactions in your database somehow, you can actually achieve horizontal scaling as well. Just as the runtime instances of the monolith you could also separate the data into different shards of the database underneath. This is also possible with an RDBMS like MySQL (yes, the boring old technology). Every DB instance bears customers within a certain immutable hash key range. The DB instances replicate the data between them for reading purposes:

![Sharded DB with Instances of a Monolith](http://improve-it.solutions/img/MasterMasterSharding.svg)

Every instance of the monolith would have one of the DB switches as proxies, so this will not become a single point of failure. If it seems hard to find the boundaries to separate the writing transactions at first, you can use the patterns of eventual consistency even for your monolith, and off you go!

This does even have a huge advantage over a microservice architecture: If it is not just one of the features that needs to endure a higher user load, but all of the functionality, than it will be a lot more effort in a microservice architecture to achieve higher scalability. This is why I do not see an advantage for microservice architectures here, and I would call this a draw.

## Microservices Disadvantages

Conclusion after discussing the advantages of microservices? There are a few, but not as many as the community is arguing. So let us now have a look at disadvantages that distributed systems, and especially microservice architectures, have:

  * Refactoring can be a lot harder. In a monolithic codebase, you can easily move functionality with a few clicks in your IDE. In a distributed system you might need a whole project to do so.
  * In a distributed system you will be forced to have some kind of eventual consistency. In a monolith, you can do so, but you don´t have to.
  * Tracking down production issues is usually harder.
  * All kinds of cross-cutting concerns are a lot harder to implement.
  * Network communication can affect stability and performance of the system.
  * Changing Interfaces can result in a whole cascade of changes in other services, that are maybe even hard to find. In a monolith, you will see instantly what other modules are affected.
  * You can easily analyze the module dependencies and visualize the architecture of a monolith with a static code analysis tool like [Sonargraph](https://www.hello2morrow.com/products/sonargraph). Microservice architectures will need things like trace-IDs in log-statements that you can analyze with tooling, which means more effort leading to results that are not as precise.
  * In a microservice architecture, you might need to invest efforts in order to manage the technology portfolio.

That said, the discussion between microservices and monoliths is now a question of pros and cons, that you will have to evaluate for your particular use case. A few other things are worth noticing, which are typical microservice fallacies and myths that need to be busted:

## Microservice Fallacy #1 - Network Separation Means Loose Coupling

Some claim that applying the microservice architectural style will automatically lead to good modularity, and especially to loose coupling between the modules/microservices. What microservice do, like any other kind of distributed system architecture, is to reduce the technical coupling between the services. Services are nothing else than modules that are distributed over the network. This will enable us to use different kinds of technologies for every particular service. This is especially helpful once one of the technologies reaches its end. It will be easy to get rid of the legacy technology, by replacing it service by service.

But: loose coupling means more than that. A distributed system is loosely coupled regarding the technology, but there are mainly 2 other factors that you need to reduce in order to achieve loose coupling, that microservices will not automatically guarantee for you:

  * If one feature/service needs to call another service in order to get its own request done, it has a time dependency. A lot of these dependencies will result in deep calling cascades. Having boundaries in the right places and utilize an asynchronous messaging technology can help.
  * The provider APIs data format of the service that a consumer calls will result in having a dependency to this kind of model in the consumer. If you want to change the API of the provider, you will have subsequent changes in all the consumers that are using this particular API.

Modularity is a lot more than just distribution over the network enabling technical flexibility. A well-designed module hides it´s implementation details from the other modules, and that includes its models and data formats (Domain Driven Design!). Loose coupling also means separating the completion of requests from each other as much as possible in as few microservices as possible.

## Microservice Fallacy #2 - It's Either Microservices or Monolith

It´s not a question between black and white if you consider using microservices or a building a monolith. Actually designing a fine-grained distributed system only maximizes the troubles you will certainly have in all distributed systems. So why not design a distributed system of (small) monoliths? You can call it a system of systems, or an [SOA 2.0](https://www.amazon.de/Grundlagen-modularen-Softwareentwurfs-Makro-Architekturen-Microservices/dp/3446455094). The trick is to have a combination of the benefits you get from building monoliths and distributed systems. You can just design multiple smaller monoliths (aka "thinliths"), that decompose further to well-designed code modules (aka "modulith"). These multiple monoliths interact with each other following the rules of microservice architectures, without overemphasizing the small size of the services. One question will remain: What should be a healthy upper limit for the size of one of this "thinliths." Because one problem will remain when building a monolith: The technology platform it is built upon, will reach the end of its lifespan at some point in time, and you will have to replace that technology. I would say try not to make one of the distributed thinliths so big, that one team (max. 10 to 12 people) is not able to replace it anymore within one year. If that is ensured, your overall system architecture is very unlikely to run into fundamental troubles any time. Good luck!
