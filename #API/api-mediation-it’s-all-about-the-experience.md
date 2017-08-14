# API Mediation: It’s All About the Experience

_Captured: 2017-07-29 at 20:02 from [dzone.com](https://dzone.com/articles/api-mediation-its-all-about-the-experience?edition=311401&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-07-29)_

The Integration Zone is brought to you in partnership with [Cloud Elements](https://dzone.com/go?i=109831&u=http%3A%2F%2Fresources.cloud-elements.com%2Fh%2Fi%2F232813135-the-definitive-guide-to-api-integrations-ebook%3Futm_campaign%3DAPI%2520Integration%2520eBook%26utm_medium%3Ddisplay%26utm_source%3Ddzone). What's below the surface of an API integration? Download [The Definitive Guide to API Integrations](https://dzone.com/go?i=109831&u=http%3A%2F%2Fresources.cloud-elements.com%2Fh%2Fi%2F232813135-the-definitive-guide-to-api-integrations-ebook%3Futm_campaign%3DAPI%2520Integration%2520eBook%26utm_medium%3Ddisplay%26utm_source%3Ddzone) to start building an API strategy.

[This article is featured in the new DZone Guide to Integration: API Design and Management. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/integration-api-design-and-management)

The world of application and data integration has undergone a sea change in recent years. Web APIs have turned the once debilitating task of integration into a competitive advantage -- enabling new channels to market, providing a platform on which new web, mobile, and IoT applications can be built, and offering far greater engagement and interaction with customers, partners, or employees. But integration still isn't as easy as it could be -- in fact, even with the broad landscape of tooling and best practices on hand, it can still be incredibly hard.

## One Size Does Not Fit All

As API-centric integration evolves and matures, it has become very clear that not all API consumers are created equal: Data objects may need to be modified based on the device type; orchestration or composition may be needed depending on the sophistication of the client; security might need to be adapted to fit mobile, web, or IoT scenarios. The list goes on.

A great example of this diversity comes from Netflix, where their API development team learned quickly that a "one-size-fits-all" approach to API integration wasn't going to work. The team found that different client applications (such as a desktop browser, a mobile application, or a smart television) required different functionality as they accessed the Netflix API, thus forcing the API team to build an increasing number of features to address the demands. Once continuously updating this single interface became unmanageable, they introduced an API experience, or mediation, layer on top of their existing API platform that allowed each UI team and even partners to optimize the API experience for their specific app or device.

With each new innovation in connected devices, and each new user and application experience that accompanies these devices, organizations must consider an application architecture and integration strategy that embodies flexibility and agility. API mediation (in other words: API experience management) is becoming a more familiar concept as many organizations begin to evolve their first foray into the API Economy.

## What Is API Mediation?

API mediation is a solution for enriching or personalizing interactions between distributed application and service components. We like to call this API Experience Management. The key to the API experience model is placing a new mediation or abstraction layer between API consumers (apps, services, and "things") and API providers (services and applications). This layer wraps the backend API (the inner API) and exposes a personalized and managed API (the outer API) to each defined constituency of consumers, simplifying the developer experience while also ensuring loose coupling. The new outer API may also aim to offer more advanced features to your developers, providing a façade on top of the inner API to enhance its functionality or simply keep pace with changes across API technologies and best practices

![Image title](https://dzone.com/storage/temp/6071087-screen-shot-2017-07-27-at-44402-pm.png)

Three functional areas you might want to consider adding as part of your API experience management include:

**1\. Eventing: **There is increasing demand for event-driven integration patterns amongst web APIs, yet support amongst public and private APIs is still very limited. There is strong preference for WebHooks to handle this asynchronous eventing between application services, so offering this functionality can be a valuable addition for your developers. WebHooksare even gaining a place within API documentation languages such as OpenAPI Specification v3.0.

**2\. Bulk Data Operations:** Bulk upload and download operations are useful for many data-centric services and applications -- and where available developers are often keen to leverage this functionality. If your backend doesn't support bulk operations today, your API experience layer can be used to enable this.

**3\. API Discovery:** To help relieve some of the pain of integration, API providers are increasingly offering a capability known as metadata discovery, so that data models and resource structures can be accessed and understood programmatically. Linked data can also enhance the usability and experience of your APIs, and again within OAS v3.0 there are new basic linking capabilities being described -- a definite nod toward Hypermedia.

## The Need for Mediation

Perhaps the simplest form of mediation is transforming legacy SOAP interfaces into more developer-friendly RESTful APIs. But in today's complex world of integration, this isn't enough to solve the challenges front-end developers are experiencing.

Rather than thoughts of divorce or separation that the term mediation may conjure up, this evolution is actually about providing a more positive experience for each of your API consumers. We've learned that quite often a one-size-fits-all approach to API design and exposure doesn't work, and different types of users, developers, and devices have different expectations and requirements when it comes to API consumption.

## API Experience Management in Practice

There are at least six fundamental reasons why your organization will derive value from an API experience layer in your integration architecture:

**1\. Integration requirements have changed:** When you built out your APIs, they needed to serve a single use case, product, or business line, but now you have lots of constituencies -- each with different use cases and integration requirements.

_Example:_ I have created an API designed to allow B2B partners to resell my products and services via their channels. When a new product owner wants to build a mobile application, this API is likely not optimized for the mobile web.

**2\. Customer needs and expectations evolve:** Your existing API layer has been in product for several years and needs to be enhanced with new functionality your developers are asking for.

_Example: _My API is a basic RESTful interface that customers today must poll the endpoint when checking for updated data. They would prefer a WebHooks implementation that alerts their app   
when new data is available.

**3\. Integration is about data, not interfaces: **You need to synchronize data across a variety of services -- even if they are in different domains. With many departments within an organization making their own purchasing decisions for the products they use, central control and data governance can be lost.

_Example:_ If the sales organization selects Salesforce as their CRM platform and the support organization is using JIRA, are these two organizations and products sharing data effectively? Don't think about master data management, but rather a lightweight way to share and synchronize common data fields in each environment.

**4\. Reducing vendor lock-in:** You are integrating to a particular service now, but in the future need to swap this for a new product or connect to multiple products.

_Example:_ If I'm storing files in Box, and using Box's raw API to do that, and then I add in SharePoint or Google Drive down the road, or swap them out, I have broken everything else, unless I mediate those APIs.

**5\. Hiding backend complexity:** You have objects or resources that exist in multiple underlying applications, databases, or other sources and want to provide consistent access to these as API resources to shield the consumer of the resource from complexity.

_Example:_ Accessing a data object representing an "order" spans a number of systems -- pulling data from stock management and eCommerce platforms. Developers should be abstracted from this complexity, only integrating with a single API that orchestrates the integration flows in the background to construct the data object.

**6\. Shifting the burden of integration: **You are bringing a digital business application to market, and customers of this application will expect built-in integration to the SaaS apps they use within their organization rather than managing this burden themselves.

_Example:_ You have built a new digital payments application and customers of this product need to be able to integrate this with their accounting applications (like NetSuite).

## Final Thoughts

Quite often across each of the use cases or scenarios described above, when starting with a small number of integration points (one or two), there is no need to worry about API experience   
management, since each API consumer can navigate any limitations. But keep in mind that once you start integrating more and more services, products, or serve different types of API consumers and an increasing number of developers, you'll find that one-size-fits-all APIs become a barrier, rather than an enabler.

[This article is featured in the new DZone Guide to Integration: API Design and Management. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/integration-api-design-and-management)

The [State of API Integration Report](https://dzone.com/go?i=201150&u=http%3A%2F%2Foffers.cloud-elements.com%2Fthe-state-of-api-integrations-report-2017%3Futm_campaign%3DState%252520of%252520API%252520Integrations%252520Report%26utm_source%3Ddzone%26utm_medium%3Ddisplay) provides data from the [Cloud Elements](https://dzone.com/go?i=201150&u=http%3A%2F%2Foffers.cloud-elements.com%2Fthe-state-of-api-integrations-report-2017%3Futm_campaign%3DState%252520of%252520API%252520Integrations%252520Report%26utm_source%3Ddzone%26utm_medium%3Ddisplay) platform and will help all developers navigate the recent explosion of APIs and the implications of API integrations to [work more efficiently in 2017 and beyond.](https://dzone.com/go?i=201150&u=http%3A%2F%2Foffers.cloud-elements.com%2Fthe-state-of-api-integrations-report-2017%3Futm_campaign%3DState%252520of%252520API%252520Integrations%252520Report%26utm_source%3Ddzone%26utm_medium%3Ddisplay)
