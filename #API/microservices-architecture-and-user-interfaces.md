# Microservices Architecture and User Interfaces

_Captured: 2017-03-14 at 10:49 from [dzone.com](https://dzone.com/articles/microservices-and-user-interfaces?oid=twitter&utm_content=buffer1d076&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Build APIs from SQL and NoSQL or Salesforce data sources in seconds.[ Read the Creating REST APIs white paper](https://dzone.com/go?i=142024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714743%3B137084581%3Bk), brought to you in partnership with [CA Technologies](https://dzone.com/go?i=142024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714743%3B137084581%3Bk).

If you have been following the web development industry in the past few years, there's a good chance that you have at least heard about microservices architectures. Some would say microservices are a specialization of SOA, and others that microservices are the same as SOA or that microservices are SOA done right. In any case, you might be wondering how to take advantage of the knowledge around microservices. Is it a good architecture for your project?

In this article, I will talk about the role of Vaadin applications in microservices architectures and provide some guidelines to help you decide on when and how to use microservices with Vaadin.

## What Are Microservices Architectures?

Microservices architectures are about modularization. The key term in how modularization is done in microservices architectures is the process. Each service, or microservice, runs as a separate process that can be independently deployed. This makes it possible to use heterogeneous technologies, to horizontally scale by starting additional instances, to replace parts of a system (a microservice), and to add resiliency mechanisms than run when a part of the system doesn't work. This might sound like nothing new, but you should think of microservices architectures as a revamp of existing practices while reading this article.

Another aspect of microservices architectures is that they help in big projects. [Amazon](https://www.infoq.com/news/2015/12/microservices-amazon), [eBay](https://www.infoq.com/presentations/service-arch-scale-google-ebay), and [Netflix](http://blog.smartbear.com/microservices/why-you-cant-talk-about-microservices-without-mentioning-netflix/) are often cited as examples where microservices solved architectural problems. On the other hand, each microservice should be "small." Defining what's small and what's not depends on each project, so ask yourself whether your project "feels" too big for your team. If the answer is yes, consider microservices. If the answer is no, don't use microservices. In any case, you can benefit from the techniques frequently used in microservices architectures. Just remember not to fall into the "[nanoservices" antipattern](https://dzone.com/articles/soa-anti-pattern-nanoservices).

Where do UIs fit in the microservices model? It depends on the specific requirements. It might be that a single UI is the best approach to make your microservices available to people. This could mean that the UI is small enough to be developed by a small team of developers, for example. However, sometimes it makes sense to have separate UIs as separate microservices (deployed independently). For example, the system might serve to many business units with heterogeneous groups of users where each UI can be developed independently.

## Single UI

This is probably the best scenario for most projects. Ideally, a UI is all about view logic without any business logic at all. If you can think of the UI as a tool for the data, then providing a single microservice that acts as a human front-end for your project is a good approach to a microservices architecture.

How does a Vaadin application communicate with other microservices? Because your Vaadin code is Java running on the server side, you can consume other microservices using any Java technology to connect to them. There are a few patterns or techniques that you should at least consider when consuming microservices from a single Vaadin UI.

First, use a [service registration and discovery](http://microservices.io/patterns/service-registry.html) mechanism. This allows the clients of a service to locate services in environments where the exact location of a service might dynamically change. Usually, client microservices will consult a centralized registry for the location of a microservice.

Second, use an [API gateway](https://www.nginx.com/blog/building-microservices-using-an-api-gateway/) when a client needs to invoke calls to several microservices with probably different communication protocols. Not only might this [reduce network traffic](http://techblog.netflix.com/2013/01/optimizing-netflix-api.html) but it also might reduce the complexity of the client code. However, if your microservices are running on the same network, the API gateway might not be necessary when using the same connection protocols among them.

Could this become a big monolith? Maybe. [Not all monoliths are bad](https://8thlight.com/blog/mike-knepper/2016/01/20/hidden-costs-of-leaving-a-monolith.html), though. However, if you really think you'll have to face the typical [problems associated with big monoliths](http://microservices.io/patterns/monolithic.html#resulting-context) in your Vaadin UI, you can consider [splitting](https://www.infoq.com/articles/microservices-intro) it into several individual projects.

## Multiple Uis

Some authors and developers advocate for creating one UI per microservice. Before going this way, carefully think if this would be beneficial for your project. Software architecture should not be a goal but a tool. To fully harness the benefits of a microservices architecture, each microservice should work independently. The ideal scenario when having multiple Vaadin microservices is that each one can be visualized independently (in different browser tabs, for example). There is no need to add special configurations in the case of Vaadin microservices with this approach.

Let's say you'd like to have separate Vaadin microservices and aggregate them into a "mash-up." You have three alternatives in this scenario: [iFrames](https://developer.mozilla.org/en/docs/Web/HTML/Element/iframe), [portlets](https://vaadin.com/liferay), and [UIs](https://vaadin.com/docs/-/part/framework/advanced/advanced-embedding.html) [embedded directly to a single host page](https://vaadin.com/docs/-/part/framework/advanced/advanced-embedding.html).

The easiest way to integrate several web applications into a single one is by using HTML's _<iframe>_ tag. You can use Vaadin (_[BrowserFrame_](https://vaadin.com/docs/-/part/framework/components/components-embedded.html#components.embedded.browserframe)) or any other web technology to develop the mash-up. iFrames are not that bad. However, keep in mind there might be some [pitfalls](http://www.rwblackburn.com/iframe-evil).

A good alternative if you want to go to the route of several Vaadin microservices integrated into a single UI is [portlets](https://vaadin.com/docs/-/part/framework/portal/portal-overview.html). By using an enterprise portal framework you gain some extra features such as authentication, authorization, and portlets' inter-communication. Depending on the vendor, it might be possible to fulfill the microservices definition we used in this article, particularly regarding the ability of microservices to run in separate processes. If you are interested in using portlets, consult the documentation of portal providers regarding support for microservices architectures.

The last alternative is to create a mashup that embeds multiple external UIs hosted in different servers into a single web page. The host page can be implemented with virtually any technology and can naturally be built with Vaadin framework, as well. The easiest method is to use the [Embedded UI add-on](https://vaadin.com/directory#!addon/embedded-ui). With it, your code will look something like the following:

This approach has advantages and disadvantages, as well. You can use the Vaadin API to easily create the mash-up, but with this add-on, you'll have to use the same Vaadin theme and the same Vaadin version in all the applications.

When using this add-on, or manually [embedding UIs in HTML](https://vaadin.com/docs/-/part/framework/advanced/advanced-embedding.html), you have to enable [Cross-Origin Resource Sharing](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing) (CORS) in your microservices. The embedded UI add-on contains helpers to achieve this.

## Conclusion

Microservices architectures solve problems in big applications by dividing a system into several microservices that are implemented, deployed, and run independently. Even when the term "microservices" might be considered a buzzword, I'd suggest embracing it and taking advantage of the modernized techniques that the microservices movement is generating. Even when microservices are used in big systems, you don't have to be Amazon, Ebay, or Netflix to take advantage of this technique. I'm working on a hands-on, down-to-earth, practical guide that shows how to implement a microservices architecture. Stay tuned and be ready to get your hands dirty.

The Integration Zone is brought to you in partnership with [CA Technologies](https://dzone.com/go?i=142025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714699%3B137084580%3Bt). Use CA Live API Creator to quickly [create complete application backends, with secure APIs and robust application logic](https://dzone.com/go?i=142025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714699%3B137084580%3Bt), in an easy to use interface.
