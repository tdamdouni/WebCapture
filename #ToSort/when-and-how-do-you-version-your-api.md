# When and How Do You Version Your API?

_Captured: 2017-04-01 at 21:10 from [dzone.com](https://dzone.com/articles/when-and-how-do-you-version-your-api?edition=286969&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-01)_

Today's data climate is fast-paced and it's not slowing down. [Here's why your current integration solution is not enough.](https://dzone.com/go?i=188126&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fdata-inspired-future-e-guide%2F%3Futm_campaign%3DDZONE%26utm_medium%3DE-guide%25252520-%25252520Data-Inspired%25252520Future%26utm_source%3DDZONE) Brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=188126&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fdata-inspired-future-e-guide%2F%3Futm_campaign%3DDZONE%26utm_medium%3DE-guide%25252520-%25252520Data-Inspired%25252520Future%26utm_source%3DDZONE)

One of the most frequent questions I receive during API training and coaching engagements involves versioning -- when to version, how to version, and whether to version at all. While not all APIs are exactly the same, I have found that there are certain patterns and practices that work for most teams. I have pulled these together to provide a recommendation for a versioning strategy that will help most API providers whether they are deploying internal, private APIs or public APIs outside the organization.

## Do You Really Need to Version Your API?

APIs are contracts established between you and your API consumers. Ideally, you will never have to break this contract. This includes URI patterns, payload structures, field and parameter names, expected behavior, and everything else in between. The biggest benefit of this approach is obvious: an API consumer's understanding never expires. Applications continue to work, making your consumers happy.

However, that may not be reality. There may be times when you need to make a breaking change. When this happens, you need to ensure that you never do anything that will cause your API consumers to fix the code.

## Breaking vs. Non-Breaking Changes

Non-breaking changes tend to be additive -- adding new fields or nested resources to your resource representations or adding new endpoints such as a `PUT` or `PATCH` that was previously unavailable. API consumers should build client code that is resilient to these kinds of non-breaking changes.

Breaking changes include:

  * **Renaming fields and/or resource paths** -- often for clarity after your API is released.
  * **Changing payload structures** to accommodate the following: 
    1. Renaming or removing fields (even if they are considered optional -- contracts!).
    2. Changing fields from a single value to a one-to-many relationship (i.e., moving from one email address per account to a list of email addresses for an account).
  * **Fixing poor choices of HTTP verbs, response codes, or inconsistent design** across your API endpoints.

In short, once you release your API into the wild, you have to live with it. If you encounter one or more of the items above, it may be time to version your API to prevent breaking your existing API consumers.

## Defining Your API Versioning Strategy

Any evolving, growing API will require an API versioning strategy. When and how you version may vary based on the expectations of your API consumers. I generally recommend the following API versioning strategy as part of an overall API governance model.

  * If your API is in an early preview release, perhaps to gain feedback from consumers, **establish proper expectations that your API may change**. At this stage, you will remain at Version 1 for some time, but your API design may change. Things are volatile as a consumer, so they should expect that changes may occur.
  * Once released, **your API should be considered a contract and cannot be broken without a new version release**. If you follow this general rule, you won't need to version your API.
  * **API versions are major.minor**, following the general principles of [semantic versioning](http://semver.org/).
  * **Non-breaking changes result in a bump in the minor version**; clients are automatically migrated to the latest version and should not experience any negative side-effects.
  * **Breaking changes result in a new major version**; clients must specifically migrate to this new version as it contains one or more breaking changes. You must establish an appropriate timeline and regular communication with your API consumers to ensure that they migrate to the new version. In some cases, this may not be possible and your team will be required to support the previous API version indefinitely.

## When You Must Implement API Versioning

Once you determine that you need a new version of your API, you need to decide how to handle it. Preferably, you have decided ahead of time and encouraged API consumers to request Version 1 of your API. There are three common approaches to implementing API versioning.

### **1\. Resource Versioning**

The version is part of the Accept header in the HTTP request -- for example, `Accept: application/vnd.github.v3+json` is sent to `GET /customers`. This considered the preferred form of versioning by many, as the resource representations are versioned while keeping resource URIs the same. Some APIs choose to provide the latest version as the default, if not provided in the Accept header

### **2\. URI Versioning**

The version is part of the URI, either as a prefix or suffix -- for example, `/v1/customers` or `/customers/v1`. While URI versioning isn't as pure as content-based versioning, it tends to be the most common as it works across a variety of tools that may not support customized headers. The downside is that resource URIs change with each new version, which some consider counter to the intent of having a URI that never changes.

### **3\. Hostname Versioning**

The version is part of the hostname rather than the URI -- for example, `https://v2.api.myapp.com/customers`. This approach is used when technology limitations prevent routing to the proper backend version of the API based on the URI or Accept header.

No matter which option you choose, API versions should only include the major number. Minor numbers should not be required (i.e., `/v1/customers`, not `/v1.1/customers`).

## Final Thoughts

Remember, APIs are contracts with your consumers. Break your contract and a new version is required. Choose a strategy, have a plan, and communicate that plan with your API consumers. They will thank you for it.

[Is iPaaS solving the right problems?](https://dzone.com/go?i=171134&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-ipaas-plus-e-guide%2F%3Futm_campaign%3DDZONE%26utm_source%3DDZONE%26utm_medium%3DeGuide%252520-%252520iPaaS%252520vs%252520iPaaS%252520%252520) Not knowing the fundamental difference between iPaaS and iPaaS+ could cost you down the road. Brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=171134&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-ipaas-plus-e-guide%2F%3Futm_campaign%3DDZONE%26utm_source%3DDZONE%26utm_medium%3DeGuide%252520-%252520iPaaS%252520vs%252520iPaaS%252520%252520)
