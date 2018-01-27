# RESTful API Technology Overview

_Captured: 2018-01-24 at 22:21 from [dzone.com](https://dzone.com/articles/restful-api-technology-overview?edition=357095&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-01-24)_

### What Technology Goes Into an API?

APIs are driven by a set of specific technologies, making them easily understood by a wide variety of developers.

A focus on simplicity means that APIs can work with any common programming language and be understood by any programmer, even one with little or no training in API technology.

### REST

Application Programming Interface ([API](https://en.wikipedia.org/wiki/Application_programming_interface)) is a set of clearly defined methods of communication between various software components. A good API makes it easier to develop a computer program by providing all the building blocks. While the specifications vary between various APIs, the end goal is to provide value to the programmer through utilization of the services gained from using an API.

The most popular approach to delivering web APIs is Representational State Transfer ([REST](https://en.wikipedia.org/wiki/Representational_state_transfer)). This approach to API design takes advantage of the same internet mechanisms (based on the HTTP protocol) used to view regular web pages, so it has the advantage of faster implementations and is easier for developers to understand and put to use.

![](http://blog.restcase.com/content/images/2017/11/RiseOfApis.png)

REST APIs allow you to take information and functionality that is already available on your website and then quickly make it available through a programmatic API, so that both web and mobile applications can reuse it, dramatically extending your company's reach over new channels, all without much additional work.

### JSON

JavaScript Object Notation ([JSON](https://en.wikipedia.org/wiki/JSON)) is a way for programs to exchange information. APIs are a way for programs to communicate, but since they don't have voices, they need a way to describe the data and information they that is being exchanged. JSON uses brackets, quotes, colons, and commas to separate data, giving the information meaningful structure so that computers can differentiate between a first name and last name or any other information that potentially describes data.

JSON has become one of the preferred ways for programmers to enable API communication. It provides a lightweight, simple way to exchange data across the internet while maintaining the structure and meaning of that data.

### Security

API security is the single biggest challenge organizations want to see solved in the years ahead, and solving the security challenge is expected to be a catalyst for growth in the API world.

According to research by SmartBear presented in their State of APIs Report 2016:

  * Security is the #1 technology challenge teams want to see solved; 41.2% of respondents say security is the biggest API technology challenge they hope to see solved.
  * Security is the #4 technology area expected to drive the most API growth in the next two years; 24% of API providers say digital security will drive the most API growth in the next two years.
  * 40.4% of API providers are currently utilizing a tool for testing API security.
![](http://blog.restcase.com/content/images/2017/11/securityState.JPG)

This is not any kind of formal standard, but something like a common practice by API providers, and supported by API management providers - the usage of one or two keys that accompany every API call. API keys are really more about identifying the application and user rather than a true security protocol, but it is perceived as secure by many.

Public REST services without access control run the risk of being farmed, leading to excessive bills for bandwidth or compute cycles. API keys can be used to mitigate this risk. They are also often used by an organization to monetize APIs; instead of blocking high-frequency calls, clients are given access in accordance with a purchased access plan.

Typically, an API key gives full access to every operation an API can perform, including writing new data or deleting existing data. If you use the same API key in multiple apps, a broken app could destroy your users' data without an easy way to stop just that one app. Some apps let users generate new API keys, or even have multiple API keys with the option to revoke one that may have gone into the wrong hands. The ability to change an API key limits the security downsides.

#### Basic Auth

HTTP Basic authentication implementation is the simplest technique for enforcing access controls to web resources because it doesn't require cookies, session identifiers, or login pages; rather, HTTP Basic authentication uses standard fields in the HTTP header, removing the need for handshakes.

To receive authorization, the client sends the userid and password, separated by a single colon (":") character, within a base64 encoded string in the credentials.

If the user agent wishes to send the userid "Aladdin" and password "open sesame," it would use the following header field:

The Basic authentication scheme is not a secure method of user authentication, nor does it in any way protect the entity, which is transmitted in cleartext across the physical network used as the carrier.

The most serious flaw in Basic authentication is that it results in the essential cleartext transmission of the user's password over the physical network.

Because Basic authentication involves the cleartext transmission of passwords it SHOULD be used over TLS or SSL protocols (HTTPS) in order to protect sensitive or valuable information.

#### Open Authorization (OAuth 2)

Created in 2006, OAuth 2 is an open standard for authentication protocols that provides authorization workflow over HTTP and authorizes devices, servers, applications, and APIs with access tokens instead of credentials. OAuth gained popularity from usage by Facebook, Google, Microsoft, and Twitter, who allow usage of their accounts to be shared with third-party applications or websites.

OAuth 2.0 can be used to read data of a user from another application without compromising the user's personal and sensitive data, like user credentials. It also supplies the authorization workflow for web and desktop applications and mobile devices.

The previous versions of this spec, OAuth 1.0 and 1.0a, were much more complicated than OAuth 2.0. The biggest change in the latest version is that it's no longer required to sign each call with a keyed hash. The most common implementations of OAuth use one or both of these tokens instead:

  * **access token**: sent like an API key, it allows the application to access a user's data; optionally, access tokens can expire.
  * **refresh token**: optionally part of an OAuth flow, refresh tokens retrieve a new access token if they have expired.

Since an access token is a special type of API key, the most likely place to put it is the authorization header, like so:

#### JSON Web Token (JWT)

JSON Web Token ([JWT](https://jwt.io/)) is an open standard, an extension of the OAuth 2.0, for creating access tokens that assert some number of claims.

Whereas API keys and OAuth tokens are always used to access APIs, JSON Web Tokens (JWT) can be used in many different scenarios. In fact, JWT can store any type of data, which is where it excels in combination with OAuth.

Like OAuth access tokens, JWT tokens should be passed in the Authorization header:

### Webhooks

Webhooks are a form of push notifications that can be triggered by a specific action. When triggered, they push information to an external website address. Webhooks allow developers to choose the action, URL, and fields associated with the webhook push. Once a webhook is triggered, it passes all associated information to the location where a developer can process it.

Webhooks became very popular, and, even in [OpenAPI 3](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.0.md), you can define the format of the "subscription" operation as well as the format of callback messages and expected responses to these messages. This description will simplify communication between different servers and will help you standardize the use of webhooks in your API. Today, many tools help you create webhooks based on the OpenAPI spec and even helps you [build your API definitions WYSIWYG](https://apibldr.com).

Webhooks are a great way to reduce constant polling on an API because they push data to API developers only when the required action is triggered. Webhooks make the API a two-way street, allowing developers to not only pull data from API platforms but also receive data in real time as events occur.

### Summary

REST, JSON, OAuth, JWT, and [Webhooks](http://www.restcase.com) have become the preferred technology for both API providers and API consumers, because they stick with the core principles of simplicity, security, making data and resources accessible, and easily integrating into web and mobile applications.

This suite of web API technologies was not designated by a single standards body or by a single company. It has been established over the past 13 years through the best practices of existing, successful API providers that are meeting the demands of developers.
