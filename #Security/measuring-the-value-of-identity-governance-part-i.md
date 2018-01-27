# Measuring the Value of Identity Governance (Part I)

_Captured: 2017-10-19 at 19:38 from [dzone.com](https://dzone.com/articles/measuring-the-value-of-identity-governance-part-i?edition=334792&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-19)_

### When it comes to minimizing risk and securing your data and network, identity governance can be a powerful tool for companies and other organizations.

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

Identity governance is important, right? Everyone agrees, but how can you measure its value?

It looks daunting, but all you need is to have a framework to understand identity governance and a very simple equation: Risk (R$) = likelihood (%) x Impact ($).

I'll break this down into two parts - the first part is the framework that we'll use to quantify the value and the second will cover how to calculate the value within that framework.

#### Identity Governance Framework

I see identity governance as much more than user access reviews (UAR) and I break Identity Governance into the following four domains:

  * Entitlement Governance
  * Fulfilment Governance
  * Activity Governance
  * Authentication Governance

#### Entitlement Governance

Entitlement governance is tasked with the important duty of ensuring that people only have appropriate (needful) access to permissions and resources. It is also tasked with ensuring that all resources and permissions (including accounts) are owned with a clearly understood impact ($) should they be abused.

Entitlement governance asks the following questions:

  * Is every "account" owned? (orphaned accounts)
  * Does each permission or resource have a dollarized impact should it be abused/compromised? (Risk)
  * Do we have a methodology or practice to determine the likelihood (%)? (Risk)
  * Do we understand the direct cost of each permission? (Decision analytics)
  * Does each person actually need each permission they currently hold? (access creep)

These look like intimidating questions, but there are practices (User Access Reviews) and tools to readily answer these questions.

#### Fulfilment Governance

Fulfilment governance is tasked with ensuring that fulfillment actions are completed and done within the approved framework. This is critical to identify rogue administration actions. Not all rogue fulfillment (provisioning/deprovisioning) actions are malicious, but they are all important; e.g. are people avoiding the use of the provisioning system because of poor training, or a bad UI? Each time an ungoverned fulfillment action occurs, it either costs the business extra money or opens a large risk.

Fulfillment governance asks the following questions:

  * Was the fulfillment request correctly executed? (rework/risk)
  * How many governed fulfillment requests were not done through the approved process or tool?
    * What was the cost of this?
    * Should this fulfillment be rolled back?
    * Why were these happening? (process improvement)

This can be delivered in a "batch" fashion, but the greatest value is derived from an event-driven (near real-time) system; less latency equals less risk exposure and time to correct.

#### Activity Governance

Activity Governance looks at what is and what has happened in an environment. Identity, be it for users, applications or other assets, is critical to link all of the disparate data sources into a coherent story. Being able to map actions or events through time back to a given entity is critically important if there is the desire to answer the following questions:

  * When was this entitlement last used and by whom? (Is it "stale"?) 
    * Entitlement: asset, application, account or permission.
    * If stale, then trigger entitlement governance processes.
  * Is the pattern of usage (asset or application) "normal" behavior? (behavioral analytics)
  * How do I provide a full activity history (report) about a user, application, or asset?

Typically this is the domain of a SIEM and it requires that it be fed maps to provide appropriate contexts for analysis and action. Typical contexts are time, identity, service, and risk.

#### Authentication Governance

The purpose of Authentication Governance is to ensure that the authentication controls for a user or application are appropriate for the agreed dollarized risk (R$). Good examples of where this is done intuitively - often forced by legislation - is health; e.g. it is common for the prescription of "controlled substances" to require step-up authentication (usually biometric) to minimize the risk of abuse. Some of the questions authentication governance tries to answer are:

  * Given the risk (R$) of an application, what are the appropriate authentication controls required?
  * Given the risk (R$) of a user, what authentication controls are required?
  * How do the connection attributes impact the risk rating of a user or application?
  * What is the "friction" of these controls?

We have tools to do this - attribute based access control (ABAC) and multifactor authentication (MFA) technologies - and I hope to show a way to calculate when we should use these in part II of Measuring the Value of Identity Governance.

#### Conclusion

I hope I've demonstrated that there is a lot more to identity governance than user access reviews (UAR). This also has a significant impact on what you should expect from your identity governance processes and tools:

  * Do they allow you to define entitlement risk (and OpEx)? Can you map these to users?
  * Do they allow you to address each of the four governance types or do they just do one piece? e.g. UAR

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
