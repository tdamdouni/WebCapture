# What Are Microservices, Actually?

_Captured: 2017-05-19 at 08:29 from [dzone.com](https://dzone.com/articles/what-are-microservices-actually?edition=298126&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-18)_

Today's data climate is fast-paced and it's not slowing down. [Here's why your current integration solution is not enough.](https://dzone.com/go?i=188126&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fdata-inspired-future-e-guide%2F%3Futm_campaign%3DDZONE%26utm_medium%3DE-guide%25252520-%25252520Data-Inspired%25252520Future%26utm_source%3DDZONE) Brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=188126&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fdata-inspired-future-e-guide%2F%3Futm_campaign%3DDZONE%26utm_medium%3DE-guide%25252520-%25252520Data-Inspired%25252520Future%26utm_source%3DDZONE)

Over the past few years, a lot of people have used the term "microservices" either to try to explain their system's or application's setup or just to brag about how trendy they are in the tech world. I believe everyone from the tech industry should know at least the fundamentals, because microservices are the future of development. And if you don't believe me, I have the word of [the President of SAP](http://www.geekwire.com/2017/sap-president-steve-singh-says-cloud-computing-yesterdays-news-microservices-future/) to back me up. But what are _microservices,_ actually?

## Microservices Architecture![Monolithic vs. SOA vs. Microservices](https://dzone.com/storage/temp/5302646-microservices-food-infographic1.png)

> _Monolithic vs. SOA vs. Microservices_

First, to be precise, when talking about microservices, we are actually referring to a _microservice architecture_. This architecture type is a particular way of developing software, web or mobile applications as suites of independent services - a.k.a microservices. These services are created to serve only one specific business function, such as: user management, user roles, e-commerce cart, search engine, social media logins, etc. Furthermore, they are independent of each other, meaning they can be written in different programming languages and use different data storages. The centralized management is almost non-existent and the microservices use lightweight HTTP, REST or Thrift APIs for communicating between themselves.

Naturally, some people will ask: Hey, isn't that same as [SOA](https://en.wikipedia.org/wiki/Service-oriented_architecture)? In a way, you could say that microservices finally achieved what Service Oriented Architecture wanted to in the first place. However, there are still differences between the two types of architectures. Classic SOA is often implemented inside deployment monoliths and is more platform driven, while microservices must be independently deployable and therefore offer more flexibility in all dimensions. The key difference of course is the size, the word micro says it all - they tend to be significantly smaller than regular SOA is. As Martin Fowler says, we should [think about SOA as a superset of microservices](https://martinfowler.com/articles/microservices.html).

![Monolithic Architecture vs. Microservices Architecture](https://dzone.com/storage/temp/5302608-1.png)

> _Monolithic Architecture vs. Microservices Architecture_

That being said, we do not look at microservices as revolutionary breakthrough, but more like a natural next step in the evolution of software development.

## Advantages of Microservices

Following the trend of modularity in the physical world (PC's hardware, IKEA furniture, automobiles, etc.), the idea behind microservices is to allow developers to build their applications from various independent components which can easily be changed, removed or upgraded without affecting the whole application - as is not the case with monoliths. This can be considered one of the major benefits of this new type of architecture. On top of that, after creating a certain microservices (e.g., File Uploading service), a developer can reuse the code for many other projects that have the need for the same function.

Another important characteristic of microservices, is that unlike monolithic applications where teams are defined by the different layers of the app: user interface, server-side logic, database logic and so on - it allows companies to construct teams around specific business capabilities. This in turn makes teams cross-functional and with a larger set of skills: user experience, database management, project management etc. This brings us closer to the era of DevOps.

The decentralized governance of the services, enables developers to use different programming language, depending on what they believe is the best one for the specific business function the microservice is built around. This also means that they can use separate data storages, bringing us to [the biggest advantage of this architecture](http://www.microtica.com/2017/01/why-migrate-to-microservices/) - the practically unlimited scalability. Having hosted each microservice at a different location allows you to scale only the function you have a need to, instead of creating double instances of the whole application every time. This in turn saves you both time and resources.

![The Building Blocks of Microservices](https://dzone.com/storage/temp/5302743-2.png)

> _The Building Blocks of Microservices_

When talking about microservices, it is inevitable to mention [containers](https://medium.com/aws-activate-startup-blog/using-containers-to-build-a-microservices-architecture-6e1b8bacb7d1#.hcaxtzyay). Containers are designed to be pared down to the minimal viable pieces needed to run what they were meant to, rather than packing multiple functions in the same physical or virtual machine. That being said, containers are just tools that might ease deployment, so it is not impossible to build an application following the microservice architecture without containerization.

To sum up, the goal of microservices is to ease the building, maintaining and managing of an application by breaking it down into smaller, composeable pieces which work together and can be independently deployed, upgraded, removed or scaled whenever the need arises.

[Is iPaaS solving the right problems?](https://dzone.com/go?i=171134&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-ipaas-plus-e-guide%2F%3Futm_campaign%3DDZONE%26utm_source%3DDZONE%26utm_medium%3DeGuide%252520-%252520iPaaS%252520vs%252520iPaaS%252520%252520) Not knowing the fundamental difference between iPaaS and iPaaS+ could cost you down the road. Brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=171134&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-ipaas-plus-e-guide%2F%3Futm_campaign%3DDZONE%26utm_source%3DDZONE%26utm_medium%3DeGuide%252520-%252520iPaaS%252520vs%252520iPaaS%252520%252520)

Topics:

microservice architecture ,microservices ,app development ,backend ,integration ,software development
