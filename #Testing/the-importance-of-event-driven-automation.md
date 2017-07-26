# The Importance of Event-Driven Automation

_Captured: 2017-03-25 at 14:58 from [dzone.com](https://dzone.com/articles/the-importance-of-event-driven-automation)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

As the adoption of automation techniques and tools start to move more into the mainstream, more progressive organizations are looking at how smaller units of automation can be invoked in a more efficient and responsive way. One of the ways they are looking to achieve this is through event-driven automation.

Event-driven automation has emerged as a response to organizations' ongoing conflict between developers who want to use and implement new technology, and Ops and security teams who want to prevent deployments that have security or operational risks.

With changes to networks and systems being introduced at a rapid pace, it is likely that security and ops teams (who generally prefer to review changes introduced into an environment before deployment) will become a bottleneck in this innovation pipeline.

For this reason, enterprises are increasingly looking to event driven automation to replace manual review, both removing the bottleneck and improving security. The Verizon [Data Breach Investigations Report](http://www.verizonenterprise.com/verizon-insights-lab/dbir/) found that manual attempts to block security breaches were not preventing attacks.

## **What Is Event-Driven Automation?**

Event-driven automation tries to manage known security and ops chokepoints. For instance, automated blocking before deployment will prevent a "known bad" security vulnerability from executing in the environment. Automating the blocking of non-blocking actions requires a mechanism for tracking deployment events and injecting security responses into the deployment process - another reason to break with fragile deployment infrastructure!

Alternatively, an organization might focus on auditing and responding to what has been deployed, automatically rolling back changes that were not approved or compliant. This reduces the amount of time that the problem exist in the environment. The problem with this approach is that there is still a window of time when the non-compliant changes exist in the environment, an amount of time which can be used to exploit systems. It's better to prohibit a "known bad" from entering the environment in the first place.

Netflix has also introduced event-driven automation in order to ensure high availability and resiliency. Netflix built the Winston framework (based on Stackstorm) to avoid having to page engineers in the middle of the night to fix a problem and to ensure that developers do not have to build and maintain new microservices just to host and execute scripts that encapsulate business logic. Winston is an event driven runbook automation platform for Netflix engineers that allows them to host and execute run books in responses to alerts.

With applications becoming ever more complex, techniques that may have worked well on a single monolithic app, such as pair programming, become less effective. No engineer has access to every known security vulnerability, and no review process will create such bullet-proof code that a service never fails in the middle of the night.

Of course, Event Driven Automation need not be merely a reactive procedure. Event Driven Automation is also emerging as the vehicle in which small units of automation are exposed for up stream consumers to use them. The provision of an application or infrastructure can trigger events. For example, the provision of an AWS cluster may trigger some Lambda code to create it's dependencies, such as a storage layer. In Kubernetes this is done using handlers, which can trigger events to provide capability from smaller discrete units of automation.

## **Requirements for Event-Driven Automation**

In order for a security or Ops team to implement event-driven automation, it's necessary for teams to have access to data concerning events in the environment that warrant a response. This data will often be in the form of server logs (often via tools like LogShash, ElasticSearch, and Splunk), monitoring and alerting systems, or other sources. Quite simply, though, if a team can't track or doesn't have access to data which shows that events are occurring, it's impossible to automate responses to those events.

Implementing event-driven automation around security requires automation to be embedded into processes that could introduce threats into the environment, such as build and deployment. Companies like Netflix and AWS have embedded automated security into their build and deployment systems. Security teams need to be able to audit the environment in a secure way and trigger events if data patterns indicate a security risk or intrusion. System logs themselves need to be trusted, secure and immutable.

It's also critical that build systems that are responsible for deploying automated systems are secure. Automated systems that are not designed with appropriate controls on build and deployment might increase security problems. For example, there is some evidence that the Target breach may have been caused by a build system being used to deploy malware to one of the POS systems, leading to a massive data breach with far reaching consequences.

## **Benefits of Event-Driven Applications**

By using event-driven or rules based applications, enterprises are able to analyze data that is being produced and make necessary changes to improve performance and security. They can also use this information to model and deploy automatic responses to events, enabling them to make the organization more efficient and responsive.

There are numerous ways to implement event-driven automation. Amazon's AWS platform, for instance, offers many of the requirements for event-driven security and automation. While of course, a security team can automate compliance, intrusion detection, and response to on-prem systems, AWS provides a platform where much of the heavy lifting has already been done. This allows security teams to focus on implementing security rules rather than providing generic system and platform components.

This is, in no small part because almost any kind of resource that can be created on AWS can be instantiated using web service calls, instead of humans taking an action. For instance, you can record every API call with CloudTrail, use VPC Flow Logs to track if network traffic was allowed or denied by security groups, and track every call made to services by the public using S3, CloudFront, and ELB Access Logs. This data can be analyzed in near-real time using Lambda.

Overall, the key to unlocking the power of big data starts with applications and the IT infrastructure that is supporting them. Without event-driven architecture, businesses are less able to make use of the performance data they have at their disposal. In this dynamic and distributed world, organizations cannot afford to stick to the static, reactive IT approaches of the past.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
