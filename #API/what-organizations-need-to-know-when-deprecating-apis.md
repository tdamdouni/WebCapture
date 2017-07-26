# What Organizations Need to Know When Deprecating APIs

_Captured: 2017-04-14 at 20:40 from [dzone.com](https://dzone.com/articles/what-organizations-need-to-know-when-deprecating-a?edition=290908&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-14)_

Learn how API management supports better integration in [Achieving Enterprise Agility with Microservices and API Management](https://dzone.com/go?i=126027&u=http%3A%2F%2Fpages.3scale.net%2Fmicroservices-api-management-dzinteg.html), brought to you in partnership with [3scale](https://dzone.com/go?i=126027&u=https%3A%2F%2Fwww.3scale.net%2F%3Futm_campaign%3Ddzintegration%26utm_source%3Ddzoneint%26utm_content%3Dbumper)

One topic that comes up a lot in the API space is the decision of companies to deprecate an API's version or to fully shut down support for a popular API.

Take the most recent example of Google, which silently announced that it would [shut down support for its Hangouts API](https://www.xda-developers.com/most-of-the-google-hangouts-api-is-being-killed-on-april-25th/) in January 2017. It is speculated that this was a move to focus on its consumer [video chat app, Duo](https://techcrunch.com/2016/08/15/google-duo/), which resulted in the decision to make Hangouts an enterprise-grade solution. This has caused a lot of uncertainty for applications built on the API, like Roll20 and PingPong.

Public APIs are best thought of as a contract provided by one business unit to another, defined by the company providing the service. Various third-party developers and partner units can work with such APIs to build their own services.

This concept of open APIs has been a driving force of innovation for application developers, but it also comes with certain risk. One of the biggest risks of building apps or services with public APIs is this very nature of unreliability. As an organization that provides APIs to the public, it's important to have a plan for how you will manage the deprecation and retirement of the different versions of your API. So how best do organizations deprecate APIs?

Let's understand the reasoning behind API deprecation first, and then highlight some recommended practices to efficiently deprecate.

## When to Deprecate APIs

The decision to deprecate and disable APIs is a hard one. There's no right way to do so, but there certainly are wrong ways. Remember that if deprecating APIs is not done correctly, it can damage a company's brand reputation and trust.

There are quite a few reasons for doing API deprecation. Deprecating an API's version could be because:

  * The API is insecure.
  * The API has too many bugs.
  * The API does not support important use cases.
  * The API is inefficient.

Deprecating an API's version is more or less a given in today's fast past tech landscape, where new and updated improvements are constantly added to APIs to keep them relevant. This form of deprivation does not have a big impact on the consumer's applications if a good and stable alternative with the right resources is quickly provided.

Then there's the more permanent form of deprecation -- deleting or disabling an API entirely. Here, the API is completely disposed of, with no updated version provided. This is a more risky option, and organizations need to have a solid understanding of the implications of doing so if they want to go through it.

Some of the reasons APIs get disposed of are:

  * The service can no longer be supported due to costs.
  * The company's decision to invest resources in a different variant of the product.
  * The service no longer serves a business objective.

These decisions usually boil down to business strategy and the alignment of the APIs with the company's revenue or user acquisition objectives. While this decision is hard, a lot of organizations will have to go through with it at some point.

## How to Efficiently Deprecate an API

Deprecation is the final stage for an API and should be done with care and empathy. It can cause a lot of frustration for your end consumers, and in some cases, it can lead to the shutdown of an entire product. Here are a few guidelines to do this better.

### Communicate Honestly

Be open and honest with the API's consumers when you decide to deprecate an API. Send an initial message announcing the intended deprecation with the proposed deprecation time frame, next version release schedule (if any), additional information like support, contact information, etc. This is where an API Management tool could come in handy, providing quick access to the list of users who have consumed your API. If this information is not readily available, looking at the API logs for frequent users could be a good place to start.

Communication can also be done in the API developer portal, and in its documentation. The Swagger framework, for example, supports a deprecated tag for operations, which will update the interactive Swagger documentation, informing users of a deprecated operation.

![Swagger UI](https://i1.wp.com/swaggerhub.com/wp-content/uploads/2017/01/Deprecated-swagger.png?resize=1457%2C796)

> _Provide a Long Enough Sunset Period_

This is the period after the initial announcement to deprecate APIs, that gives API consumers time to reconfigure their apps. This could be in the form of code updates to fit the new version of the API into their software architecture, or a program to accommodate alternative solutions in case the API has been disabled. A good sunset period is important as it gives API-dependent companies time to work on changing their business and technological strategy. Depending on the deprecated API's reach, user base, and service offering, this period could be anywhere between three to eight months.

### Version Effectively

Deprecating a particular version of an API can be easier with effective versioning. With good versioning, it's also possible for different versions of the APIs to live simultaneously. Build and release the next version of the API before fully deprecating the API. This ties into the sunset period, providing developers and engineers enough time to rework their existing architecture to support the new API.

### Provide Alternatives

There may be many applications and full-scale software solutions that depend on the API to function smoothly. A good migration plan for your API consumers to transition smoothly, either to your the API's newest version or to other alternatives in case of full API deletion, can help ease frustration and maintain trust among your end consumers.

It is always a good idea to honor any promises and commitments made in the service level agreement of the API before its full depreciation. The reason for this is to sustain trust and keep your organization's reputation among your API consumers intact. People talk, and bad word-of-mouth press can cause irreparable harm to brand identity. [Twitter is a prominent example](https://www.fastcompany.com/3043716/sxsw/twitter-only-gave-meerkat-2-hours-notice-before-cutting-access-to-the-social-graph), which has born the brunt of poor developer relations in the past and is [actively working towards rebuilding this](http://www.theverge.com/2015/10/21/9586084/jack-dorsey-twitter-ceo-apology-developers).

To summarize, organizations should put considerable thought into why, when, and how they disable support for an API -- be it a version or the entire service itself. Organizations should take time and effort to help their end consumers recoup by providing the right information, the right resources, and the right time. And finally, organizations should invest in the right tools and infrastructure needed to manage, version, and eventually retire the different versions of their API.

Unleash the power of your APIs with future-proof API management - [Create your account](https://dzone.com/go?i=126028&u=http%3A%2F%2Fpages.3scale.net%2Ffuture-proof-api-management-dzinteg.html) and start your free trial today, brought to you in partnership with [3scale](https://dzone.com/go?i=126028&u=https%3A%2F%2Fwww.3scale.net%2F%3Futm_campaign%3Ddzintegration%26utm_source%3Ddzoneint%26utm_content%3Dbumper).
