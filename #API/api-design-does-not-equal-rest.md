# API Design Does Not Equal REST

_Captured: 2017-07-29 at 08:53 from [dzone.com](https://dzone.com/articles/api-design-does-not-equal-rest?oid=twitter&utm_content=buffer6a378&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Migrating from On-Prem to Cloud Middleware?](https://dzone.com/go?i=228224&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fgreat-middleware-transition-managed-services-address-key-needs%2F%3Futm_campaign%3DDZONE%26utm_source%3DDZONE%26utm_medium%3DMarket%252520Report%252520-%252520The%252520Great%252520Middleware%252520Transition) Here's what Aberdeen Group says leading companies should be considering. Brought to you in partnershp with [Liaison Technologies](https://dzone.com/go?i=228224&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fgreat-middleware-transition-managed-services-address-key-needs%2F%3Futm_campaign%3DDZONE%26utm_source%3DDZONE%26utm_medium%3DMarket%252520Report%252520-%252520The%252520Great%252520Middleware%252520Transition).

[This article is featured in the new DZone Guide to Integration: API Design and Management. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/integration-api-design-and-management)

In the early days of web APIs (2000-2010), the concept of API design was very much associated  
with Roy Fielding's dissertation on Architectural Styles and the Design of Network-  
based Software Architectures. If you were talking about API design, all conversations quickly  
became about using HTTP, crafting your URIs, and using your HTTP verbs -- early RESTafarians made sure of this.

## Hypermedia Design Patterns

Alongside this discussion that put HTTP at the center the API design conversation, a small band of API architects was pushing forward how we craft the requests and responses of our APIs, something that was modeled after the web and was called hypermedia. This new breed of API craftsperson focused on applying RESTful design principles while also deeply considering the structure and relationships between the resources they were making available and heavily considering how these resources would be consumed at the client level.

Even with these strong opinions regarding the technical details of an API and the careful crafting of your API requests and responses, the conversations were primarily within an exclusive group of developers. The wider business and enterprise developer groups were often unaware of the nuances of design and would need more documentation to be able to understand and put API design practices to work in their world. A new breed of API documentation tool called Swagger would soon emerge, which would help introduce developers to the world of API design through their need for up-to-date API documentation.

## Defining Common Design Patterns

In 2012, as the API space was picking up steam, the API definition format, formerly Swagger (now OpenAPI), was helping to standardize how we communicate around APIs. But another API service provider emerged with a new approach to defining APIs that was focused on design over just producing documentation. Apiary came onto the scene with their new way of defining APIs called API Blueprint, which emphasized design over mocking, testing, documentation, or even the deployment of your API. This new approach to designing APIs before you ever got dirty with the hard work of development would set into motion a new age of API design where it was becoming more than just REST or hypermedia but was also quickly becoming about communicating, collaborating, and sharing your API design throughout the API lifecycle.

Swagger and API Blueprint cracked open a new world of API design, enabling a much more standardized and shared conversation to occur amongst developers about what API design is beyond just REST and hypermedia. Honestly, I don't feel that most developers are even ready for hypermedia, and API definition formats are allowing for some critical web literacy to be taught to large groups of developers, preparing everyone for a hypermedia engineered future. We now had a common language for defining, collaborating, and sharing around common API design practices, setting the stage for growth beyond just the number of APIs, including what we expected of our APIs and ultimately the design constraints we were applying (or not).

## Serving the Full API Lifecycle

API definitions were being used to design APIs, potentially considering other existing API design patterns, all captured in a way that could be shared with other stakeholders, evolving the API design process into a group effort. The resulting API definition could then be used as a central truth to mock, deploy, manage, test, monitor, discover, and generate code. This new approach to developing software is not just driving web and mobile applications but also a growing number of   
devices across our personal and professional lives. API design was no longer about a single set of design patterns and could now encompass a wider practice and discipline, opening up the door to new ways of thinking.

## Runtime Design Solutions

Many APIs are just a façade for backend databases, so that as APIs are driving more web and mobile applications, it is natural for front-end developers to demand more access and control over backend resources. Modern approaches to designing web APIs do well when it comes to providing access to query, filter, and send instructions to backend databases, but a new way to access large, very complex data and content backends has emerged and seen adoption. GraphQL was developed by Facebook and is now used by GitHub and others, giving developers more control over what data they accessed, allowing them to design the exact API responses they needed for any application at runtime -- offloading API design to front-end developers, sharing the load with backend developers.

## Designing for Performance

Alongside GraphQL, as it was providing API solutions for big data problems, Google had been cooking up their own approach to delivering APIs, but this time with a focus on performance and the delivery of high-volume APIs. Google's approach to delivering high-volume, high-performance APIs using gRPC has been growing, allowing developers to design a new breed of APIs using a description format called Protobuf. At Google, RESTful APIs and gRPC live side by side, sharing a common API definition that set a coordinated set of API design goals, allowing for the deployment of two distinct design patterns to achieve shifting goals.

## A Diverse API Design Toolbox

The API design toolbox has expanded. RESTful approaches are still the preferred design pattern to follow across the majority of APIs we see out there. However, there is an increasing number of hypermedia APIs emerging, helping deliver more experience-based APIs that behave much like the web within client applications. GraphQL is growing amongst single-page application usage, as well as applications that service big data and complex content applications. Then adding to the professional API design toolset, gRPC is getting more attention within the data center and larger enterprises, and is driving a new generation of tooling like the Spanner database platform. A truly robust API design toolbox has emerged, helping API designers and architects deliver exactly the solution they need for a variety of use cases.

## Designing the Internet of Things

There are signs of leading API design patterns spreading beyond web and mobile and being applied to the growing world of the Internet of Things (IoT). We are beginning to see REST and hypermedia patterns applied to device APIs as part of the engineering of IoT platforms and services. API design has moved out of its dogmatic RESTful roots and is becoming more about finding exactly the design blueprint you need for the job. Mobile devices, equipped with API design patterns, has opened the door pretty wide when it comes to delivering and consuming digital resources made available on consumer, commercial, and industrial IoT implementations.

## Communication Is Essential to Design

API design has proven to be much more than just the technical details, and one of the essential ingredients needed to set all this in motion was the ability to communicate around common API design patterns -- if we can't share, communicate, and collaborate around a common set of design rules, the concept will never gain traction and see adoption. This is why API definitions like OpenAPI are playing an important role in the API design conversation because they allow us to communicate around a common set of design patterns. This communication is key to the growth in the number of APIs out there, as well as the number of developers who are aware and literate when it comes to common API design patterns.

## API Design Is the API Contract

In the last five years, API design has quickly become the contract that defines the technical, business, and political aspects of API operations, which in turn are driving web, mobile, and device applications. API design is quantified using API definition formats, which have evolved from XML, to JSON, to a more human-readable YAML -- making API design a much more accessible discipline. Business stakeholders could now play a role in helping hammer out the details of the API contract, what data is available, and how it is accessed and made available within APIs.

API design is not just REST anymore. It is not just the domain of the developer. API design is about all stakeholders sitting at the table, having a conversation about what is needed to drive web, mobile, network, and device applications. In this environment, the API contract can be hammered out in plain English, defining the technical, business, and legal aspects of making data, content, and algorithms available for use across distributed applications. API design has become about following a common, well defined set of best practices, while being able to communicate, collaborate, share, and ultimately implement design strategies. Most importantly, API design has matured beyond a single approach, allowing for a robust toolbox to emerge, with a diverse set of blueprints to apply across almost any situation.

[This article is featured in the new DZone Guide to Integration: API Design and Management. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/integration-api-design-and-management)

[Is iPaaS solving the right problems?](https://dzone.com/go?i=171134&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-ipaas-plus-e-guide%2F%3Futm_campaign%3DDZONE%26utm_source%3DDZONE%26utm_medium%3DeGuide%252520-%252520iPaaS%252520vs%252520iPaaS%252520%252520) Not knowing the fundamental difference between iPaaS and iPaaS+ could cost you down the road. Brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=171134&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-ipaas-plus-e-guide%2F%3Futm_campaign%3DDZONE%26utm_source%3DDZONE%26utm_medium%3DeGuide%252520-%252520iPaaS%252520vs%252520iPaaS%252520%252520)

### Like This Article? Read More From DZone
