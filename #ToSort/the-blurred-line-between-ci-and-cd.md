# The Blurred Line Between CI and CD

_Captured: 2017-02-14 at 19:19 from [dzone.com](https://dzone.com/articles/the-blurred-line-between-continuous-integrationci?edition=268944&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-14)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

I have the pleasure of meeting many people in a variety of European organizations in the Continuous Delivery domain. A topic that comes back repeatedly during our projects is the confusion amongst release management stakeholders on the difference between Continuous Integration (CI) and Continuous Delivery (CD).

Let's be fair -- the tools and solution vendors are not making it easy. With CI tools claiming they deploy straight into production and CD tools claiming to cut back your build cycle times, it is easy to get confused.

Let's try to clear up the confusion by taking a look at one of the core requirements for each domain.

## **Continuous Integration**

Continuous Integration is a process that should happen as soon and often as possible in the development cycle. After all, you want to know ASAP if the code changes applied by a development team member have broken the build. If so, you'll want to fix the issue right away. This is the core purpose of Continuous Integration. It can happen several times a day -- or even several times an hour. That is why there is a lot of ongoing effort involved in reducing CI cycle time and making the CI scope as focused as possible based on the code change(s) that happen.

## **Continuous Delivery**

Continuous Delivery is a process that should happen as soon and as often as it is relevant. It should pick up the release candidate components from multiple development tracks, group them together, ensure functional and technical dependencies are met, and only then push that "release candidate" through the various stages of the CD pipeline.

That blurred line between CI and CD should not be there. CI ensures you produce output (artifacts) many times an hour from many teams in parallel. CD puts the output of different CI tracks in the context of a release and orchestrates the promotion of that release package throughout the relevant stages and required tollgates.

You can align the high-cadence CI process with the lower cadence CD process to create stable, resilient, and high-performance end-to-end release pipelines.

Organizations that can successfully align their high-cadence CI process with the lower cadence CD process achieve a much more stable and resilient end-to-end process than those organizations who try to force the CD process to run at the same frequency of the CI process. That is why a CI tool is typically not a CD platform. CI and CD have different scopes, objectives, and requirements, and therefore should not be categorized together.

There is no blurred line between CI and CD. On the contrary, defining a clear demarcation point between CI and CD is one of the key success factors for implementing high-performance, scalable, and resilient end-to-end release pipelines.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
