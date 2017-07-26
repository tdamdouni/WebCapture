# SOAP vs. REST: Differences in Performance, APIs, and More

_Captured: 2017-03-31 at 20:14 from [dzone.com](https://dzone.com/articles/differences-in-performance-apis-amp-more?edition=286955&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-31)_

Build APIs from SQL and NoSQL or Salesforce data sources in seconds.[ Read the Creating REST APIs white paper](https://dzone.com/go?i=142024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714743%3B137084581%3Bk), brought to you in partnership with [CA Technologies](https://dzone.com/go?i=142024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714743%3B137084581%3Bk).

SOAP (Simple Object Access Protocol) and REST (Representational State Transfer) are both web service communication protocols. SOAP was long the standard approach to web service interfaces, although it's been dominated by REST in recent years, with REST now representing more than 70% of public APIs according to [Stormpath](https://stormpath.com/blog/rest-vs-soap). Understand the primary differences between SOAP vs. REST and how each can benefit your organization's goals.

## SOAP vs. REST: Primary Differences

REST operates through a solitary, consistent interface to access named resources. It's most commonly used when you're exposing a public API over the Internet. SOAP, on the other hand, exposes components of application logic as services rather than data. Additionally, it operates through different interfaces. To put it simply, REST accesses data while SOAP performs operations through a more [standardized set](http://blog.smartbear.com/apis/understanding-soap-and-rest-basics/) of messaging patterns. Still, in most cases, either REST or SOAP could be used to achieve the same outcome (and both are infinitely scalable), with some differences in how you'd configure it.

SOAP was originally created by Microsoft, and it's been around a lot longer than REST. This gives it the advantage of being an established, legacy protocol. But REST has been around for a good time now, as well. Plus, it entered the scene as a way to access web services in a much simpler way than possible with SOAP by using HTTP.

## Benefits of REST Over SOAP

In addition to using HTTP for simplicity, REST offers a number of other benefits over SOAP:

  * **REST allows a greater variety of data formats**, whereas SOAP only allows XML.
  * Coupled with JSON (which typically works better with data and offers faster parsing), **REST is generally considered easier to work with**.
  * Thanks to JSON, **REST offers better support for browser clients**.
  * **REST provides superior performance**, particularly through caching for information that's not altered and not dynamic.
  * **REST is the protocol used most often for major services** such as Yahoo, Ebay, Amazon, and even Google.
  * **REST is generally faster and uses less bandwidth**. It's also easier to integrate with existing websites with no need to refactor site infrastructure. This enables developers to work faster rather than spend time rewriting a site from scratch. Instead, they can simply add additional functionality.

Still, SOAP remains the preferred protocol for certain use cases. The general consensus among experts these days is that REST is the typically preferred protocol unless there's a compelling reason to use SOAP (and there are some cases in which SOAP is preferred).

## Benefits of SOAP Over REST

Because you can achieve most outcomes using either protocol, it's sometimes a matter of personal preference. However, there are some use cases for which SOAP tends to be better-suited. For instance, if you need more robust security, SOAP's support for WS-Security can come in handy. It offers some additional assurances for data privacy and integrity. It also provides support for identity verification through intermediaries rather than just point-to-point, as provided by SSL (which is supported by both SOAP and REST).

Another advantage of SOAP is that it offers built-in retry logic to compensate for failed communications. REST, on the other hand, doesn't have a built-in messaging system. If a communication fails, the client has to deal with it by retrying. There's also no standard set of rules for REST. This means that both parties (the service and the consumer) need to understand both content and context.

Other benefits of SOAP include:

  * **SOAP's standard HTTP protocol makes it easier for it to operate across firewalls and proxies** [without modifications](http://searchmicroservices.techtarget.com/tip/REST-vs-SOAP-Choosing-the-best-web-service) to the SOAP protocol itself. But because it uses the complex XML format, it tends to be slower compared to middleware such as ICE and COBRA.
  * Additionally, while it's rarely needed, some use cases require greater transactional reliability than what can be achieved with HTTP (which limits REST in this capacity). **If you need ACID-compliant transactions, SOAP is the way to go**.
  * In some cases, **designing SOAP services can actually be less complex** compared to REST. For web services that support complex operations, requiring content and context to be maintained, designing a SOAP service requires less coding in the application layer for transactions, security, trust, and other elements.
  * **SOAP is highly extensible** through other protocols and technologies. In addition to WS-Security, SOAP supports WS-Addressing, WS-Coordination, WS-ReliableMessaging, and a host of other web services standards, a full list of which you can find on [W3C](https://www.w3.org/Submission/).

At the end of the day, the best protocol is the one that makes the most sense for the organization, the types of clients that you need to support, and what you need in terms of flexibility. Most new APIs are built using REST and JSON simply because it typically consumes less bandwidth and is easier to understand both for developers implementing initial APIs as well as other developers who may write other services against it. Because it's more easily consumed by most of today's web browsers, REST+JSON has become the defacto technology for the majority of public APIs. However, SOAP remains a valuable protocol in some circumstances. Plus, you don't have to look far to find die-hard fans advocating for SOAP for certain use cases.

The Integration Zone is brought to you in partnership with [CA Technologies](https://dzone.com/go?i=142025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714699%3B137084580%3Bt). Use CA Live API Creator to quickly [create complete application backends, with secure APIs and robust application logic](https://dzone.com/go?i=142025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714699%3B137084580%3Bt), in an easy to use interface.
