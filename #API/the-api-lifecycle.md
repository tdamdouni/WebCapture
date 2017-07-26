# The API Lifecycle

_Captured: 2017-01-15 at 20:52 from [dzone.com](https://dzone.com/articles/the-api-life-cycle?edition=263882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-15)_

Learn how API management supports better integration in [Achieving Enterprise Agility with Microservices and API Management](https://dzone.com/go?i=126027&u=http%3A%2F%2Fpages.3scale.net%2Fmicroservices-api-management-dzinteg.html), brought to you in partnership with [3scale](https://dzone.com/go?i=126027&u=https%3A%2F%2Fwww.3scale.net%2F%3Futm_campaign%3Ddzintegration%26utm_source%3Ddzoneint%26utm_content%3Dbumper)

This article is a continuation of my [first post](https://dzone.com/articles/abcs-of-api-driven-development), where I had introduced the basics of API-driven development (ADD). In this post, I will discuss a very relevant concept called the API lifecycle, explain the different phases in the life of an API, and discuss different personas who will be a part of that cycle.

In the API lifecycle, there are three primary personas:

  1. **API publisher: **Creates and deploys the API.
  2. **API manager:** Manages and monetizes the API.
  3. **API consumer:** Discovers and integrates with the APIs.

Each of these API personas has multiple tasks associated with them, and those tasks define the characteristics of the API (see Figure 1).

![Fig-1: API life-cycle, personas and tasks](https://dzone.com/storage/temp/3967325-build-manage-consume-design-touched.jpg)

> _Figure 1: API lifecycle, personas, and tasks._

Let's take a look at the API lifecycle in another dimension (see Figure 2) and understand the different stages of the lifecycle. Here, you can see how the various personas deal with APIs in different stages.

![FIG-2:  API life-cycle and personas](https://dzone.com/storage/temp/3967479-api-lifecycle.jpg)

> _Figure 2: API lifecycle and personas._

The API manager, API publisher, and API consumer are personas who may be represented by people with various designations in an organization.

For the sections below, the numbers represent the steps as given in Figure 2.

## 1\. Plan and Strategy

The API manager (a persona who could be represented by people with designations such as API product manager or API architect) prepares an overall plan on how to expose an enterprise's digital assets using APIs. The plan can include identifying the list of APIs, their design (including parameters and types), visibility scope, etc. Last but not least, the API manager also makes sure that the documentation of the API is comprehensive. There is a popular saying in the API world: "An API is as good as its documentation." Hence, API documentation is one of the tasks that should be done with utmost clarity.

## 2\. Create, Design, Test, and Publish

Once the API plan is ready, the API publisher (who can be represented by people with designations such as software developer or software architect) gives birth to APIs by creating APIs as a part of the core app development process. Note that a lot of times, you find the responsibilities of API manager and API publisher being delivered by someone like an enterprise architect or similarly designated persons.

## 3\. Versions

API undergoes further tweaking to its design configuration (i.e., path or query parameter) as per the requirements. It's tested, versioned, and published to a private enterprise DevPortal. Whether an API is private or public is defined by the API's visibility settings and the governance semantics around it. You normally see vendors using API frameworks such as Swagger and tooling around it to do the above tasks easily.

## 4\. Features

The API manager can apply more management configurations based on requirements. For instance, the API manager may configure the free API invocations limit to a finite number and make the consumer to pay for any invocations beyond the configured limit. He or she can also configure analytic reports on various APIs and can create plans that can be subscribed to by the consumer. At this point, all APIs are assumed to be published and available for consumption, through an API DevPortal (check out [Paypal's API dev portal](https://developer.paypal.com/webapps/developer/docs/api/)). APIs can be [internal or external](http://www.wavemaker.com/api-management/internal-vs-external-apis/), and similarly, API DevPortal can be a public portal like PayPal's or can be private portal accessible only withing an enterprise network.

The above four steps (as seen in Figure 2), explored the API lifecycle from the perspective of an API publisher and an API manager.

Now, we will explore the API lifecycle from an API consumer perspective. The API consumer persona is usually an app developer or an app architect who consumes or integrates the APIs as a part of the app development process.

## 5, 6, and 7. Discovery, Authentication, and Creation

In the API DevPortal, the consumer has the ability to search for the desired APIs and subscribe to a particular API or an API plan associated with a group of APIs as defined by the API manager. The API consumer creates a DevPortal account and registers his or her app to consume the needed APIs. Usually, an API key is generated per app and is used during the runtime to authenticate the app accessing the API. Consuming the API is the last step in the lifecycle of the API. When you are able to successfully integrate the API into your app and get the desired results, the cycle is complete.

Note: A few API management vendors use another lifecycle step of engage and promote where the APIs are promoted in various forums to the end consumers (who are developers). I have not touched that aspect of the lifecycle, since it may not be that relevant from the ADD perspective.

In the next post of this series, I will talk about how ADD has become a part of some modern app development platforms.

Unleash the power of your APIs with future-proof API management - [Create your account](https://dzone.com/go?i=126028&u=http%3A%2F%2Fpages.3scale.net%2Ffuture-proof-api-management-dzinteg.html) and start your free trial today, brought to you in partnership with [3scale](https://dzone.com/go?i=126028&u=https%3A%2F%2Fwww.3scale.net%2F%3Futm_campaign%3Ddzintegration%26utm_source%3Ddzoneint%26utm_content%3Dbumper).
