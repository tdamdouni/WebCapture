# How to Go Zero Trust, Part 1: Why the Architecture Matters

_Captured: 2017-06-29 at 17:07 from [dzone.com](https://dzone.com/articles/how-to-go-zero-trust-part-1-why-the-architecture-m?edition=305177&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-28)_

Discover an in-depth knowledge about the different kinds of [iOS hacking tools](https://dzone.com/go?i=222228&u=https%3A%2F%2Fweb.securityinnovation.com%2Fhacking-ios-applications-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dhacking-ios-applications) and techniques with the [free](https://dzone.com/go?i=222228&u=https%3A%2F%2Fweb.securityinnovation.com%2Fhacking-ios-applications-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dhacking-ios-applications) iOS Hacking Guide from Security Innovation.

_This is part 1 in a series of blog posts dedicated to helping companies learn what it takes to achieve a Zero Trust security architecture of their own; much like Google's BeyondCorp._

When Google talks about their [BeyondCorp](https://www.beyondcorp.com) initiative, they often do so in terms of the final outcome - eliminating their need for a corporate VPN. This is a nice soundbite as it speaks to a friendlier user experience for the thousands of Googlers working across the globe, but it was really the revolutionary design of the architecture and careful implementation of the system that made it possible. Any company looking towards the Zero Trust model for their own security should approach from a similar architectural perspective, recognizing that it will take a collaborative effort across the organization that accounts for people and process as much as it does technology.

The seismic shift from traditional perimeter security measures towards that of the Zero Trust model can really be boiled down to a single key fact - the modern workforce is no longer constrained by the walls of the office. More employees are working remote from a wide range of mobile devices, and more applications are being operated as a service in the cloud. We've witnessed the impact of digital transformation over the past decade, and we're now approaching a similar era of security transformation led by the Zero Trust model.

Until now, the typical reactive response to this new environment has been to implement a VPN or some sort of software-defined perimeter. It makes sense at first glance - why not simply make the network we understand so well accessible from the outside by people who are part of the company? Well technically, VPNs do exactly what they're supposed to do in this regard, but they are failing to keep unwanted users out because they don't factor in the context surrounding the traffic, making it easier and easier to spoof a valid credential. Once on the inside, an attacker essentially has the proverbial keys to the kingdom, leaving companies vulnerable with little to no insight into what's going on.

Google recognized this fact earlier than most, and thus began their BeyondCorp initiative in 2010. Seven years later, we are fortunate to be able to look at BeyondCorp as evidence that the Zero Trust model works, it is possible to implement, and that the users will love it. In following Google's lead, companies of all kinds can pave a meaningful path forward towards their own security transformation.

Before getting into the details of the Zero Trust model, I wanted to cover a few of the benefits so we know what it is we're really getting out of the architecture itself.

### A Better Definition of Identity That Enables Smarter Decision Making

The traditional view of corporate identity has been to segment users based on their roles. This usually leaves two types of employees - privileged and non-privileged (which often means no more than SysAdmin or not). In turn, our industry has created two distinct product categories - Privileged Access Management and Identity and Access Management. Similar to the VPN, these products technically do what they're supposed to do, but they often leave organizational silos that can lead to confusion and gaps in security coverage.

What the Zero Trust model gets right in this regard is redefining Identity to a point where every request can be consistently authenticated and authorized, regardless of the user's job or the type of resource they are trying to access. In the modern workforce, the context of who we are is always changing, which a secure system needs to keep up with.

This means that a more dynamic definition of identity must go further than just an employee record in a database - it has to have the right context to enable smarter decision making. In the Zero Trust model, the definition of an identity becomes a **user** plus their **device** at a **point-in-time**. This combination of attributes and known state forms a profile that can be evaluated in real-time, laying the foundation for the entire architecture and supporting workflows.

### Centralized Access Controls Gives Better Visibility Into Employee Activity

In order to make smarter decisions in real-time, and to provide a consistent experience to the users, all traffic should flow through a central gateway service to handle the authentication and authorization processes. Google's BeyondCorp, for example, places a reverse proxy service in front of every protected resource - referred to as a Google Front End.

The gateway acts as a safety man-in-the-middle for traffic to your protected resources - assuming, of course, that all traffic is encrypted from end-to-end. This is a different behavior than with public applications because you actually want to intercept all of the traffic to company resources in order to verify each request. With a central gateway, you have an ideal processing point to place the smarts, and an ideal logging point to gain visibility into the activity. It's important to note that while logically centralized, the gateway must be a globally distributed system capable of fast auth processing to avoid interrupting the user workflow.

Taking this one step further, this architecture now supports more proactive decision making. It's one thing to be able to inspect the logs for auditing purposes, but imagine a system that could identify uncommon behavior as it's happening, and trigger additional login factors or approval workflows before granting access. I see this as the next evolution of access management, which can only be realized with a Zero Trust architecture.

### The Security Measures Encourage Better Employee Security Posture

One thing every company struggles with is maintaining and tracking their employee's personal security posture with regards to company resources. Not a week goes by without the news of another high-profile breach that originated from an insider, whether malicious or accidental. This struggle only compounds with the advent of remote employees, mobile devices, cloud services, and SaaS apps. The lack of security awareness is generally a culprit, but there's no real gain from simply pointing the finger.

As it turns out, a natural byproduct of the Zero Trust architecture itself is better employee security posture - but through encouragement. It's too easy to gloss over or ignore security procedures when presented in a forceful way. As mentioned, Zero Trust impacts people and process as much as it does technology, and personal security is ingrained into the workflows themselves. For example, a company policy may state that out-of-date devices can't access specific applications. If an out-of-date device prevents someone from doing their job - they will go run a software update!

The trick here is presenting any necessary self-remediation steps in a human readable fashion. If an employee is blocked from accessing an internal application because their device is unknown to the system, then they need to be told so in a way they can understand. A message that reads "please enroll your device to gain access" sure beats a message that reads "access denied." Over time, better security posture will just become a habit, much to the delight of security and risk teams.

### Removing Trust From the Network Eliminates Common Attack Vectors

Recognizing that the perimeter is an ineffective way to attest trust is the most fundamental concept of the Zero Trust model. There must be an alternative, of course, which centralized policy-driven access controls deliver. When the system is implemented, the outcome of the architecture then eliminates the most common source of breaches we read about every week - static credentials.

When making access decisions in real-time based on dynamic conditions, the method of trust attestation should also be dynamic and tightly scoped. Why go to all the effort of building a Zero Trust system if it's just going to be backed by a static credential? This is no easy task, however, as building your own PKI that can generate ephemeral credentials is a challenge. Google has the resources to do so, but if Zero Trust is to be a real movement, it must be achievable by companies of all kinds.

This is where a solution such as [ScaleFT](https://www.scaleft.com) can help, as our platform includes a built-in Certificate Authority that generates single-use client certificates scoped to the user, device, and resource. Every request to a protected resource flows through a central gateway that authenticates through an integration with your Identity Provider and authorizes against configurable access policies. By enrolling your employee devices and protected resources with ScaleFT, you get an end-to-end Zero Trust workflow much like Google's BeyondCorp.

## What's Next

We've just scratched the surface of the architecture here and will be getting into more detail as the series progresses. The next post will cover the various sources to collect data from to better understand how your system architecture will adapt to the Zero Trust model. I'll follow that with a post that details how to come up with the right access policy framework for your organization. Finally, I'll cover how to implement the access controls through a central gateway service. Stay tuned!

**[Leveraging](https://dzone.com/go?i=222226&u=https%3A%2F%2Fweb.securityinnovation.com%2Fwebinar%2Fleveraging-humans-and-tools-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dleveraging-humans-and-tools%252520) Humans to Get the Most Out of Tools**
