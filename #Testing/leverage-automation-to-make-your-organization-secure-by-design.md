# Leverage Automation to Make Your Organization Secure by Design

_Captured: 2017-06-03 at 00:54 from [dzone.com](https://dzone.com/articles/leverage-automation-to-make-your-organization-secu?edition=304119&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-02)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

Recently, we co-hosted a webinar with Amazon's security strategist, Tim Sandage, and SessionM's director of technical solutions and operations, Jason LaVoie, to discuss how companies can become secure by design using automation.

With cloud providers like AWS making it easier than ever to get up and running in the cloud, the next item on the agenda for many is how to get security up to speed as well. In yesterday's webinar, Tim, Jason, and our own senior security engineer, Patrick Cable, offered practical and strategic ways for companies to do just this.

In case you missed the webinar, here's our recap.

## Why Security Needs to Be Automated

As fast as organizations are adopting security automation, our [adversaries are also taking advantage of automation](https://blog.threatstack.com/why-automated-security-threats-are-proliferating-and-how-to-fight-back) to launch attacks. Attackers can make a good living off the simple mistakes companies make in the cloud when trying to run fast. Operating on a continuous integration (CI) and continuous deployment (CD) schedule, teams can get a lot done, but they're also more prone to error. Whether it be accidentally leaked API keys or database passwords, or running a test in the wrong environment, Dev_Ops_ can quickly become Dev_Oops_, making your users the weakest link in the chain.

Case in point:

![Webinar1.png](https://blog.threatstack.com/hs-fs/hubfs/Webinar1.png?t=1495663452135&width=1920&name=Webinar1.png)

Humans will always be prone to error, so to reduce risk, security needs to be automatically deployed and monitored across your entire environment, which is where a "secure by design" approach comes in.

## Becoming Secure by Design on Amazon

Amazon has created and disseminated [Security by Design](https://aws.amazon.com/compliance/security-by-design/) (SbD) principles. They have identified the core tenets of secure infrastructure and worked to ensure that there's a feature within AWS that addresses each.

These principles of secure infrastructure include:

  * Build security into every layer.
  * Think parallel.
  * Leverage different storage options.
  * Treat infrastructure as code (modular, versioned, constrained).
  * Design for failures.
  * Implement auto-healing.
  * Plan for a breach.
  * Design for cost.
  * Don't fear constraints.

AWS users can leverage features ranging from identity access management (IAM) to access keys to multi-factor authentication to [CloudTrail](https://aws.amazon.com/cloudtrail/) to ensure they're meeting each of these key security design principles.

By automating the implementation and monitoring of these controls, organizations can become secure by design, meaning every nook and cranny of your cloud environment is secure, making it a lot harder -- if not impossible -- for hackers to get in.

Putting this into practice, here are a few ways companies can become secure by design:

### 1\. Modernize Governance

Historically, governance rules were written to cover security policies and procedures for on-premise systems. While these rules are effective at protecting legacy technology, they don't stand up to modern cloud technology. They especially don't account for a DevOps or Security by Design framework.

Many companies attempt to adapt their old governance rules to the cloud, but quickly find that they need to completely rethink their approach. To modernize your governance over security, begin with this very basic but fundamental question: what are you looking to achieve? Knowing what and who you're looking to protect, you can begin to fit security controls around your specific cloud environment. During the webinar, we walked through the following governance framework:

![TS17005_ThreatStack_SecureByDesignWebinar.jpg](https://blog.threatstack.com/hs-fs/hubfs/TS17005_ThreatStack_SecureByDesignWebinar.jpg?t=1495663452135&width=3072&name=TS17005_ThreatStack_SecureByDesignWebinar.jpg)

In short, you need to understand the stakeholders, systems, and data that you are looking to protect across the organization. When you have a bird's eye view of your security requirements, you can rewrite your governance rules to account for the nuances in the cloud. Then you can look to automation to help implement and maintain these security controls and policies for you, ensuring that, with every line of code you write and every cloud server that is spun up, security is baked in from the very beginning. Tim and Jason call this "secure by code."

### 2\. Understand the Shared Responsibility Model

In previous posts, we've written a lot about the shared responsibility model in the cloud. Understanding where your responsibilities lie is key to rewriting governance rules and adopting security best practices in the cloud.

According to this model, AWS is responsible for the security **_of_** the cloud, while you are responsible for security **_in_** the cloud. AWS has met a diverse number of compliance certifications, from SOC 1 to SOC 2 and PCI DSS to ISO, which gives organizations the ability to inherit these reports as they manage their own risk.

However, there are many pieces of the model that companies must uphold to consider themselves _fully_ secure and compliant. During the webinar, Tim stressed the importance of leveraging a virtual private network (VPN), managing secure workloads, and implementing key management, among other best practices according to the [CIS benchmarks](https://www.cisecurity.org/cis-benchmarks/).

### 3\. Adopt Continuous Risk Treatment to the Cloud

Traditionally, you have four options when evaluating your risk:

  * **Avoid** the risk.
  * **Reduce** the risk.
  * **Share** or transfer the risk.
  * **Accept** the risk.

The issue with this approach in the cloud is that changes are happening in nanoseconds, and threats are coming in larger volumes, so there's no time to decide on a case-by-case basis how you'll respond.

In the cloud, risk treatment needs to be embedded in your CI and CD frameworks so decisions can be made automatically and continuously, keeping security in front of or in lockstep with DevOps. In practice, it looks like this:

![Webinar3.png](https://blog.threatstack.com/hs-fs/hubfs/Webinar3.png?t=1495663452135&width=3072&name=Webinar3.png)

With continuous monitoring, you can always see where your security posture stands on a day-by-day basis, which can make going through an audit a lot easier as well. As a bonus, with this approach, you're not only secure by design, but also compliant by design.

## Adopting Security by Design

The cloud enables your business to run fast, which is a good thing in most regards. But when security doesn't go along with your operations and development, that can open you up to serious vulnerabilities and attacks, especially when most attacks today are automated by design. By embedding security from your infrastructure out, you can run fast and secure, keeping users, data, and systems secure and compliant.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
