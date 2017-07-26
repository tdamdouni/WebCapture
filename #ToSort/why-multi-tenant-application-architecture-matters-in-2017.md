# Why Multi-Tenant Application Architecture Matters in 2017

_Captured: 2017-01-28 at 22:21 from [dzone.com](https://dzone.com/articles/why-multi-tenant-application-architecture-matters?edition=265887&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-28)_

[Download this eBook](https://dzone.com/go?i=177148&u=http%3A%2F%2Fgo.nuodb.com%2FIntellyxeBook-CloudGame-DZONE_IntellyxCloudGame-LPGated.html%3Futm_source%3Ddzone%26utm_medium%3Dcloudzone) outlining the critical components of success for SaaS companies - and the new rules you need to play by. Brought to you in partnership with [NuoDB](https://dzone.com/go?i=177148&u=http%3A%2F%2Fgo.nuodb.com%2FIntellyxeBook-CloudGame-DZONE_IntellyxCloudGame-LPGated.html%3Futm_source%3Ddzone%26utm_medium%3Dcloudzone).

According to this [ZDNet article](http://www.zdnet.com/article/predictions-2017-three-reasons-businesses-cant-ignore-the-rapidly-growing-cloud-market/), the global public cloud market will reach $146 billion in 2017, a $59 billion increase over 2015. A big chunk of this market is enterprises with a core product built on top of Multi-Tenant Application Architecture. For example, you may have heard of this little company going by the name of [SalesForce.com](http://www.developerforce.com/media/ForcedotcomBookLibrary/Force.com_Multitenancy_WP_101508.pdf). Yet, despite the clear indications multi-tenancy has been a game changer in the tech industry, many are uncertain of exactly what makes an application "Multi-Tenant" or why it matters.

## Multi-Tenancy Defined

To quote [TechTarget](http://whatis.techtarget.com/definition/multi-tenancy), "multi-tenancy is an architecture in which a single instance of a software application serves multiple customers." Consistent with many other ideas that have led to breakthroughs and exponential growth, at the core of multi-tenancy is the idea of resource maximization. That being said, the idea of resource maximization is not new or unique to multi-tenancy. It's a rather common objective of most business endeavors to maximize available resources. So what makes multi-tenancy special?

## The Problems Multi-Tenant Application Architectures Solve

As discussed in this [University of Wurzburg whitepaper](https://se2.informatik.uni-wuerzburg.de/pa/uploads/papers/paper-371.pdf), colocation data centers, virtualization, and middleware sharing are some examples of resource sharing with similar ambitions of reducing cost while maximizing efficiency. What differentiates multi-tenant application architecture is its effectiveness in achieving the same goal in a scalable and sustainable fashion. In a nutshell, to quote CNCCookbook CEO Bob Warfield, the benefit of multi-tenancy is "instead of 10 copies of the OS, 10 copies of the DB, and 10 copies of the app, it has 1 OS, 1 DB and 1 app on the server".

For most organizations, 10 is quite a conservative estimate, nonetheless, the takeaway is clear, Multi-Tenant Application Architecture helps optimize the use of hardware, software, and human capital. Larry Aiken makes some astute observations on this topic in this [Cloudbook article](http://www.cloudbook.net/resources/stories/why-multi-tenancy-is-key-to-successful-and-sustainable-software-as-a-service-saas).

As an alternative to a multi-tenant application, many technology vendors are tempted to enter the market with a solution that simply creates a virtual appliance from existing code, sell a software license, rinse and repeat. There are lower entry costs this way and it seems like a reasonable option for organizations looking to create a cloud offering of a software that already exists. However, as the project scales, so do the flaws in this approach.

Each upgrade of the application will require each customer to upgrade and the ability to implement tenant management tools and tenant-specific customizations is significantly limited. With multi-tenant architecture centralized updates and maintenance are possible and the level of granularity possible using tenant management tools is significantly higher. In fact, in the aforementioned Cloudbook article, OpSource CEO Treb Ryan is cited as indicating a true multi-tenant application can reduce a SaaS provider's cost of goods sold from 40 % to 10 %.

## The Challenges and Drawbacks of Implementing A Multi-Tenant Application Architecture

While Multi-Tenant Application Architecture is and will continue to be a staple of the industry for quite some time, there are alternate architectures which work better or are easier to implement for a given project. One of the more common reasons is simply that there can be quite the barrier to entry in building a multi-tenant application from scratch.

There is a knowledge gap for those without the experience, and sometimes it makes more sense to get a minimum viable product out there and learn from your users. While that approach may cost more on the back end, there are more prudent reasons to consider multi-instance applications instead as well.

This [ServiceNow blog post](https://servicematters.servicenow.com/why-cloud-architecture-matters-the-multi-instance-advantage-over-multi-tenant/) details some of the reasons they find multi-instance to be the superior architecture. Some of the common counter-arguments raised against multi-tenancy can be reconciled to the simple fact that customer data resides in the same application and or database.

These arguments center around the idea that despite the vast array of fail-safes, security measures, and encryption techniques available to mitigate risk, the reality is a shared resource does mean there will be some (at least theoretical) security and performance tradeoffs in certain circumstances. Additionally, sometimes one customer may just become big enough that their data warrants their own instance. Even SalesForce.com has somewhat acknowledged this reality by introducing [Superpod](http://www.salesforce.com/company/news-press/press-releases/2013/11/131118-2.jsp).

## Multi-Tenant vs. Multi-Instance

Making a choice between multi-tenant and multi-instance application architectures will depend almost entirely on your position and the business problems you are trying to solve. As a user, it's probably best to focus on the end product, meaning evaluating SLAs, functionality, and meeting any relevant requirements for data integrity, security, and uptime as opposed to basing a decision on the underlying architecture.

As a solution provider, your focus should be on which architecture allows your product to add the most value to the marketplace. Will there be more benefit in your team being able to leverage the extensibility of multi-tenancy or the portability of multi-instance? Taking a step back, why not both? A fairly popular approach is to implement groups of tenants across a number of instances. The focus should always be on delivery of the best product possible.

Whatever the final decision on architecture is, a key component to ensuring quality and delivery is optimized is following a DevOps philosophy that emphasizes continuous improvement, automation, and monitoring.

In conclusion, Multi-Tenant Application Architecture is an architecture that allows resources to be centralized and leads to benefits in the form of various technological economies of scale. Multi-tenancy has contributed to a disruptive change in the market over the last 10 years and continues to be at the core of many applications today. While there are alternatives and, in practice, applications may be a bit of a hybrid between multiple architectures, multi-tenancy is a core concept of cloud computing and seems likely to be so for the foreseeable future.

Learn how [moving from a traditional, on-premises delivery model to a cloud-based, software-as-a-service (SaaS) strategy is a high-stakes](https://dzone.com/go?i=177147&u=http%3A%2F%2Fgo.nuodb.com%2FIntellyxeBook-CloudGame-DZONE_IntellyxCloudGame-LPGated.html%3Futm_source%3Ddzone%26utm_medium%3Dcloudzone), bet-the-company game for independent software vendors. Brought to you in partnership with [NuoDB](https://dzone.com/go?i=177147&u=http%3A%2F%2Fgo.nuodb.com%2FIntellyxeBook-CloudGame-DZONE_IntellyxCloudGame-LPGated.html%3Futm_source%3Ddzone%26utm_medium%3Dcloudzone).
