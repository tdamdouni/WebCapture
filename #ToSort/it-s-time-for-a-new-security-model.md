# It's Time for a New Security Model

_Captured: 2018-07-30 at 07:47 from [dzone.com](https://dzone.com/articles/its-time-for-a-new-security-model?edition=385303&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-30)_

Discover how to provide [active runtime protection](https://dzone.com/go?i=255346&u=https%3A%2F%2Fwww.waratek.com%2Fruntime-application-self-protection-rasp%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Drasp) for your web applications from [known and unknown vulnerabilities](https://dzone.com/go?i=255346&u=https%3A%2F%2Fwww.waratek.com%2Fruntime-application-self-protection-rasp%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Drasp) including Remote Code Execution Attacks.

![blog security apis](https://blogs.mulesoft.com/wp-content/uploads/blog-security-apis.jpg)

> _blog security apis_

Traditional security models -- such as firewalls and DMZs -- were designed to protect the perimeter. The thinking was that if the four walls of a company were protected, then threats would be neutralized before they come anywhere near core IT infrastructure. However, when bad actors inevitably made their way inside, they were often left undetected and free to move about as they extracted sensitive business data.

Fast forward to 2018, and the IT environment is very different. Rather than being walled gardens, IT infrastructure now consists of large-scale mashups of on-premises systems, cloud platforms, SaaS applications, mobile devices, and hundreds of APIs connecting it all together. Businesses today do not have a clear perimeter; they live everywhere that their customers, partners, and employees do.

In a business landscape where perimeters no longer exist, IT teams need a new security model that orients around securing the connectivity fabric itself -- APIs. [According to Gartner](https://www.gartner.com/doc/3834704/build-effective-api-security-strategy), API abuses will be the most-frequent attack vector, resulting in data breaches for enterprise web applications by 2022. It's time businesses toss aside the traditional security model and, instead, adopt a zero trust model, where security lies in the APIs themselves.

## **The Power of Zero Trust Security**

Moving away from trying to secure entire perimeters, zero trust architectures provide verifiable identities to APIs and consumers (e.g., devices and applications), allowing them to exchange data without the risk of loss or unauthorized access.

With verifiable identities, each API can perform authentication, authorization, and access control in a distributed fashion. Therefore, access to APIs and the sensitive data they share is granted based on what we know about the caller and its context, in terms of device, location, and more. Zero trust architectures also build on top of well-known and proven cryptographic technologies, such as encryption, public/private keys, and blockchain. These technologies are combined in a decentralized, distributed, self-service, and automated model, effectively making security a de-facto and embedded capability for every API.

The shift to zero trust comes at a time when APIs are becoming increasingly important for organizations. According to MuleSoft's[ Connectivity Benchmark Report 2018](https://www.mulesoft.com/lp/reports/connectivity-benchmark), organizations generate 25 percent of revenue through APIs and API-related implementations. Security teams must, therefore, find a balance between making their APIs easy to use and having them tightly controlled to prevent misuse. They must ensure security is built in at the design stage by embracing zero trust.

## **Building a Zero Trust Architecture**

Achieving a robust, secure, API-based infrastructure using zero trust principles requires a four-step process:

  1. _Asset discovery:_ Compile an exhaustive summary of all APIs currently in use within the organization. You can't secure things that you don't know about, and so, having a definitive list of all elements is critical.
  2. _Take a capabilities-led view:_ Since APIs are designed for a known purpose, this provides them with the ability to target protections in design time based on the capability of the API. This further complements the API gateway protections during runtime to provide targeted and focused protections.
  3. _Adopt a continuous approach:_ API security is not a one-off exercise. Constantly discover, monitor, and secure the infrastructure to ensure that it remains secure while also delivering the performance required by users.
  4. _Deploy a distributed enforcement model:_ The approach needs to protect the front-end of the API, in addition to the back-end of the API connecting to the data source. Both protections are important and need to be thought through when exposing APIs.

Above all, when it comes to creating an effective zero-trust environment, security must always be treated as a design-time concern with targeted and focused runtime capabilities. All communications between APIs, and with data consumers, must be mutually authenticated, authorized, encrypted, and governed by policy - this policy-based access control should be governed centrally but handled in a distributed way.

Also, the identity of someone seeking access to an API should not be assumed simply because the call is coming from a particular network. Multi-factor authentication and digital signatures should be made a key part of the security infrastructure, not only to authenticate a login but to also authorize actions.

In this way, access to APIs and services can be granted based on what is known about the caller, and there is no need for implicit trust to be involved in the process. Instead, the organization ends up with an effective system; whereby, API callers need to prove that they are legitimate before they can gain access to core data or applications.

Find out how Waratek's award-winning [application security platform](https://dzone.com/go?i=255347&u=https%3A%2F%2Fwww.waratek.com%2Fapplication-security-platform%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappsecplatform) can improve the security of your [new and legacy applications and platforms](https://dzone.com/go?i=255347&u=https%3A%2F%2Fwww.waratek.com%2Fsolutions%2Flegacy-platforms%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dlegacy) with no false positives, code changes or slowing your application.

Topics:

security ,zero trust ,model ,architechture ,api ,infrastructure
