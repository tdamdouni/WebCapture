# How Secure is Your API?

_Captured: 2017-03-10 at 19:24 from [dzone.com](https://dzone.com/articles/how-secure-is-your-api?edition=278882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-10)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

You have researched the latest API design techniques. You have found the best framework to help you build it. You have all the latest tools in testing and debugging at your fingertips. Perhaps you even have an amazing developer portal setup. But, is your API protected against the common attack vectors?

Recent security breaches have involved APIs, giving anyone building out APIs to power their mobile apps, partner integrations, and SaaS products pause. By applying proper security practices and multiple layers of security, our API can be better protected.

## Recent API Security Concerns

There have been several API security breaches that demonstrate some of the key vulnerabilities that can occur when using APIs. These include:

  * The [Telegram breach](https://www.wired.com/2016/08/hack-brief-hackers-breach-ultra-secure-messaging-app-telegram-iran/) that allowed access to a user database to confirm the identities of 15 million accounts.
  * The rush-to-market by Internet of Things manufacturers has led to the introduction of security risks by developers who are proficient in their core business but not experts at managing API security ([Nissan LEAF API security flaw](http://www.wired.co.uk/article/troy-hunt-interview-pwned-security)).
  * Several instances of undocumented or private APIs that were "reverse-engineered" and used by hackers: [Tinder API used to spy on users](http://www.programmableweb.com/news/swipebuster-uses-private-tinder-api-to-let-anyone-spy-tinder-users/brief/2016/04/07), [Hacked Tesla pulls out of garage](http://newatlas.com/tesla-model-s-amazon-echo-alexa-autosummon-hack/43054/), [SnapChat hack involved undocumented API](http://www.programmableweb.com/news/snapchat-hack-involved-undocumented-api/2014/10/10).

These and other recent cases are causing API providers to pause and reassess their API security approach.

## Essential API Security Features

Let's first examine the essential security practices to protect your API:

**Rate Limiting:** Restricts API request thresholds, typically based on IP, API tokens, or more granular factors; prevents traffic spikes from negatively impacting API performance across consumers. Also prevents denial-of-service attacks, either malicious or unintentional, due to developer error.

**Protocol:** Parameter filtering to block credentials and PII information from being leaked; blocking endpoints from unsupported HTTP verbs.

**Session:** Proper cross-origin resource sharing (CORS) to allow or deny API access based on the originating client; prevents cross-site request forgery (CSRF) often used to hijack authorized sessions.

**Cryptography:** Encryption in motion and at rest to prevent unauthorized access to data.

**Messaging:** Input validation to prevent submitting invalid data or protected fields; parser attack prevention such as XML entity parser exploits; SQL and JavaScript injection attacks sent via requests to gain access to unauthorized data.

## Taking a Layered Approach to Security

As an API provider, you may look at the list above and wonder how much additional code you'll need to write to secure your APIs. Fortunately, there are some solutions that can protect your API from incoming requests across these various attack vectors - with little-to-no change to your code in most circumstances:

**API Gateway:** Externalizes internal services; transforms protocols, typically into web APIs using JSON and/or XML. May offer basic security options through token-based authentication and minimal rate limiting options. Typically does not address customer-specific, external API concerns necessary to support subscription levels and more advanced rate limiting.

**API Management:** API lifecycle management, including publishing, monitoring, protecting, analyzing, monetizing, and community engagement. Some API management solutions also include an API gateway.

**Web Application Firewall (WAF):** Protects applications and APIs from network threats, including Denial-of-Service (DoS) attacks and common scripting/injection attacks. Some API management layers include WAF capabilities but may still require a WAF to be installed to protect from specific attack vectors.

**Anti-Farming/Bot Security:** Protects data from being aggressively scraped by detecting patterns from one or more IP addresses.

**Content Delivery Network (CDN):** Distributes cached content to the edge of the Internet, reducing the load on origin servers while protecting them from Distributed Denial-of-Service (DDoS) attacks. Some CDN vendors will also act as a proxy for dynamic content, reducing the TLS overhead and unwanted layer 3 and layer 4 traffic on APIs and web applications.

**Identity Providers (IdP):** Manage identity, authentication, and authorization services, often through integration with API gateway and management layers.

**Review/Scanning:** Scan existing APIs to identify vulnerabilities before release.

When applied in a layered approach, you can protect your API more effectively:

![diagramf](https://tyk.io/wp-content/uploads/2017/01/diagramf.png)

## How Tyk Helps Secure Your API

Tyk is an open-source API management layer that offers a secure API gateway for your API and microservices. Tyk implements security such as:

  * Quotas and Rate Limiting to protect your APIs from abuse.
  * Authentication using access tokens, HMAC request signing, JSON Web tokens, OpenID Connect, basic auth, LDAP, Social OAuth (e.g. GPlus, Twitter, Github) and legacy Basic Authentication providers.
  * Policies and tiers to enforce tiered, metered access using powerful key policies.

Carl Reid, Infrastructure Architect at [Zen Internet](https://www.zen.co.uk/), found that Tyk was a good fit for their security needs:

> "Tyk complements our OpenID Connect authentication platform, allowing us to set API access/rate limiting policies at an application or user level, and to flow through access tokens to our internal APIs."

When asked why they chose Tyk instead of rolling out their own API management and security layer, Carl mentioned that it helped them to focus on delivering value quickly:

> "Zen has a heritage of purpose building these types of capabilities in house. However, after considering whether this was the correct choice for API management, and after discovering the capabilities of Tyk, we decided ultimately against it. By adopting Tyk, we enable our talent to focus their efforts on areas which add the most value and drive innovation which enhances Zen's competitive advantage"

Find out more about how Tyk can help secure your API [here](https://tyk.io/tyk-documentation/security/).

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
