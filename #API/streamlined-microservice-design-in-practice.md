# Streamlined Microservice Design in Practice

_Captured: 2017-12-15 at 20:22 from [dzone.com](https://dzone.com/articles/streamlined-microservice-design-in-practice?edition=345096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-15)_

The Integration Zone is brought to you in partnership with [Cloud Elements](https://dzone.com/go?i=263425&u=https%3A%2F%2Fresources.cloud-elements.com%2Febooks-private%2Fguide-to-api-integrations-ebook%3Futm_campaign%3DAPI%2BIntegration%2BeBook%26utm_medium%3Ddisplay%26utm_source%3Ddzone). What's below the surface of an API integration? Download [The Definitive Guide to API Integrations](https://dzone.com/go?i=263425&u=https%3A%2F%2Fresources.cloud-elements.com%2Febooks-private%2Fguide-to-api-integrations-ebook%3Futm_campaign%3DAPI%2BIntegration%2BeBook%26utm_medium%3Ddisplay%26utm_source%3Ddzone) to start building an API strategy.

[This article is featured in the new DZone Guide to Microservices. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/orchestrating-and-deploying-containers)

As more organizations implement microservices, the practices of microservice architecture become more mature. Whereas much of the early microservices literature focused on companies decomposing a monolithic web application into microservices, larger and more diverse organizations are now tackling how to migrate their existing software ecosystems into domains of services in order to improve their software delivery speed and scalability. This problem space is significantly more complex than breaking down the single monolith, and comes with higher-order challenges.

Modularization is fundamental to dealing with the complexity of distributed software systems. This is both the reason microservice architecture is gaining popularity, and an important reminder of how to approach it. Finding the right boundaries between services is understandably one of the main focus areas for organizations adoptingmicroservices in order to [reduce coordination between teams](http://www.freshblurbs.com/blog/2016/09/27/microservices-coordination-removal.html), and there is a [growing body](http://www.apiacademy.co/designing-a-system-of-microservices/) of [information](http://blog.christianposta.com/microservices/the-hardest-part-about-microservices-data/) on [techniques](https://www.infoq.com/articles/Microservices-Architectural-Fitness) to draw those boundaries. This technology-agnostic design work deals with the [essential complexity](http://www.apiacademy.co/visualizing-microservice-architecture/) of the software system, helping to improve its evolvability and sustainability over time. Once the boundaries are drawn, there is still design work that needs to be done.

## The Microservice Design Canvas

The microservices movement has been driven by developers, is closely aligned with the rise of [Agile methods and DevOps](https://www.infoworld.com/article/3075880/application-development/microservice-architecture-is-agile-software-architecture.html), and has been motivated by a desire for faster software delivery. Consequently, developers often start coding quickly and rely on emergent design to guide their work, which can result in sub-optimal service disposition over the long haul. On the other hand, an overly-involved service design process can bog down development efforts and undermine the intended benefits of microservice architecture. How can appropriate design thinking be injected into the process in a streamlined way?

With a hat tip to Simon Brown's "[just enough up front design](http://www.codingthearchitecture.com/presentations/sa2011-just-enough-up-front-design)" concept, the [Microservice Design Canvas](http://www.apiacademy.co/the-microservice-design-canvas/) intends to capture the essential service attributes that can help guide development of the service itself as well as its consuming applications.

![Image title](https://dzone.com/storage/temp/7525113-screen-shot-2017-12-13-at-95434-am.png)

> _Figure 1 - The Microservice Design Canvas._

In addition to the name and description of the service, the canvas includes the following sections:

![Image title](https://dzone.com/storage/temp/7525148-screen-shot-2017-12-13-at-100052-am.png)

Ideally, a service designer can complete sections in the table's order and capture the essence of the service using the canvas. Here is an example of a completed canvas fora Transaction Search Service:

![Image title](https://dzone.com/storage/temp/7525149-screen-shot-2017-12-13-at-100121-am.png)

> _Figure 2 - a sample microservice design canvas for "Transaction Search."_

## Microservices at Capital One

Capital One has been an early adopter of microservice architecture, with several hundred now running in production across the company. Capital One's technology is large and heterogeneous, not all of which is built using microservices. The initial rise of microservices adoption happened organically, by different teams experimenting with and adopting its concepts as they saw fit in their daily work.In 2017, the Capital One executive team declared maturation of microservices capabilities an important priority, and a team was put together to provide a microservices adoption strategy, implementation guidelines, and training workshops for development teams.

To align their microservices efforts across the organization, Capital One first needed to identify a common goal. When analyzing the success of the organic microservices efforts, the Capital One microservices team recognized that the power of the new architecture was that it allowed developers to move fast without compromising the safety and quality of their solutions. Irakli Nadareishvili, one of the leaders of the team, explains:

> For the longest time, there has been a belief in software engineering that you have to compromise between speed and safety: either you go fast or you build with high quality. Such a compromise makes intuitive sense. Complex systems are built by many teams, working on different parts of an application. Every now and then those teams need to coordinate their work with others, and at that point you have one of two choices: you either ignore coordination need and keep going fast, which may break some things along the way, or you acknowledge the need to coordinate and slow down. But what if we had a system architected in a way that minimized the need for coordination? Then we wouldn't need to choose between speed and safety as often. It turns out you can have such a design if you have autonomous teams working on small batches of isolated work. For us, that is the essence of microservice architecture. 

## Designing Microservices at Capital One

Many organizations get stuck when trying to find the size for the microservices. In Capital One's analysis of microservice design, they found that the optimal microservice size varies over time, as illustrated by microservice pioneers like Netflix:

![Image title](https://dzone.com/storage/temp/7525255-screen-shot-2017-12-13-at-100812-am.png)

At Capital One, development teams start with coarse-grained design and split microservices when they find need to eliminate emerging instances of coordination.Teams are not expected to get service boundaries "right" out of the gate. Instead, boundaries evolve over time to allow autonomous, high-performance teams to develop systems quickly and safely.

When examining how to design greenfield or brownfield system of microservices, the Capital One microservices team used Domain Driven Design (DDD) as a starting point. They found the concept of bounded contexts to be extremely useful for representing autonomous capabilities in a complex system. Overall, however, they felt that applying DDD in depth across the organization would require expertise and experience that most software teams were not equipped with, and trying to make it work would be costly and difficult to implement consistently.

Capital One found a viable shortcut to DDD in AlbertoBrandolini's [Event Storming methodology](http://eventstorming.com/). This new approach that is rapidly gaining popularity in the software industry allows teams to explore a complex domain--including the identification of bounded contexts--in just a handful of 4-hour sessions. In addition to its work products, Capital One has found Event Storming to be a collaborative and inclusive exercise that helps quickly develop a shared understanding of a product between engineering, product teams, design teams, as well as other key stakeholders.

## The Microservice Design Canvas at Capital One

One issue the Capital One team encountered withEvent Storming is that, while the process is very useful, its final artifact--a wall full of sticky notes--is difficult to digitize or document. Since they wanted something more than just a list of bounded contexts and hotspots as a takeaway, they decided to codify the resulting microservice designs using a variant of the Microservices Design Canvas. Team member [James Higginbotham](https://twitter.com/launchany) reordered the boxes on the canvas to align more closely with the [Business Model Canvas](https://strategyzer.com/canvas/business-model-canvas), resulting in the following:

![Image title](https://dzone.com/storage/temp/7525273-screen-shot-2017-12-13-at-100922-am.png)

_Figure 3 - A sample microservice design canvas for "Payments Management Service" using the Capital One variant (information purely for demonstration purposes)._

So far, the Capital One team has found the canvas to be a useful way of documenting the design of their microservices. Importantly, they are able to use the canvas in a non-intrusive way that helps them reduce coordination between teams in order to improve their overall delivery speed without compromising the safety and stability of their systems.

## Design Thinking in Microservice Architecture

Just as Capital One recognized that microservice boundaries evolve over time, the structure of the Microservice Design Canvas will also change as it is applied and adapted by individuals and organizations. Its value should be measured by how effectively it meets its goal: to provide a simple tool for capturing just enough design thinking at the right time in order to help deal with the complexity of distributed software ecosystems.Experimentation and iteration are hallmarks of the microservices way, so please let the authors know about your own experiences working with the canvas and the other tools discussed in this article.

[This article is featured in the new DZone Guide to Microservices. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/orchestrating-and-deploying-containers)

Your API is not enough. Learn why (and how) leading SaaS providers are turning their products into platforms with API integration in the ebook, [Build Platforms, Not Products](https://dzone.com/go?i=263426&u=https%3A%2F%2Foffers.cloud-elements.com%2Fbuild-platforms-not-products-ebook%3Futm_campaign%3DPlaforms%25252C%252520Not%252520Products%252520eBook%26utm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_content%3Dtext) from Cloud Elements.
