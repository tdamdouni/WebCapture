# Promise Theory and DevOps

_Captured: 2017-04-30 at 23:35 from [dzone.com](https://dzone.com/articles/promise-theory-and-devops?oid=twitter&utm_content=buffer7c637&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Mark Burgess ([@markburgess_osl](https://twitter.com/markburgess_osl?lang=en)) is a theoretical physicist, but in his keynote at the EMEA Conference, he talked more about economics and human interaction than physics. What does either have to do as the keynote for a conference on DevOps?

Well, for a little more background, Mark Burgess is also the founder and former CTO of [CFEngine](https://cfengine.com/), a configuration management and automation framework, and is the author of _Promise Theory_. While at CFEngine, Mark worked to apply a theory of how the autonomous agents in software interact with each other. Promise Theory was born.

Promise Theory sits counter to obligation theories. Obligation theories view human interactions and behavior under the assumption that people (or agents, in the case of software) choose behavior based on their obligation to follow the rules. Agents are obligated to take a certain action. Promise theory contends the desire to follow the rules is voluntary and that agents can only be responsible for their own behavior, not the behavior of other agents.

In his presentation, Mark started out looking at human behavior and trends in our society. For instance, with technological advances, our need for one another is decreasing, even as our interdependence through communication is increasing. For example, our smartphones enable us to do almost anything without the direct interaction of someone else.

![Image title](https://dzone.com/storage/temp/5106052-burgess1.jpg)

Looking at interactions in society, trust is the basis for our exchanges, working communities, and function as a society. He contends, "The promise is the source of intent by which all promises and observers may calibrate their expectations." Money is an example of this. Money does not have intrinsic value, but we use it because we trust the backer will stand behind its value and it is more convenient than bartering goods. He explains that in the old monetary economy, banks and governments were the provider of trust; in the new service/IT economy, the service provider is the basis of trust.

How do you model this trust? Enter Promise Theory, which describes how agents make promises with each other and how this leads to trust between them. Mark outlines the "ingredients" of Promise Theory:

  1. Agents and super agents make promises in a scaling hierarchy.
  2. An agent can never make a promise about another agent's behaviour (only its own).
  3. An agent's promise need not be accepted or used by its intended or unintended recipient!
  4. An agent makes its own valuations: what you have is only worth what another is willing to give you for it.
  5. Dependency invalidates promises.

At the core of understanding this, you have to understand that collaboration is made up of semantics, what words means, and dynamics: all how things work. And that our ever-increasing service economy is driving us to an explosion of semantics- because words matter so much more than the mechanics. As an example, Mark sketched the hierarchy of promise dependencies in the old and new economies. Looking at the old economy, where we have more dynamic money, the hierarchy is:

Retail-> Money-> Banks-> Central Banks-> Government.

In the new economy, where we have more semantic services, the hierarchy is:

Client-> Network Availability-> Provider-> Internet Authorities-> Company/Service Organization.

None of these systems could work without cooperation at the bottom of it all. So, production is a cognitive process between the producer and the consumer, but also between the agents inside those organizations that have to interact. Often we create pipelines to describe these interactions, but the interdependencies within the systems are often much more complex than the pipeline can model.

![Image title](https://dzone.com/storage/temp/5106126-burgess2.jpg)

This is all just the tip of the iceberg. Mark has three books that dive into it in detail: _Thinking in Promises, In Search of Certainty, _and _Promise Theory._

In the end, Mark made the point that technology does an excellent job of both binding us together and pulling us apart. We need to be careful that we don't take ourselves out of the systems we create, or we could scale ourselves out of existence.

If this piqued your interest, you can watch Mark's [full All Day DevOps conference session](https://youtu.be/R56rNrr2ydw) (just 40 minutes). When you do, you can view the other 56 presentations from the 2016 conference online and free-of-charge.

This blog series is reviewing sessions from the 2016 All Day DevOps, which hosted over 13,500 registered attendees. Next week, look for "Breaking Bad Equilibrium" \-- new perspectives from John Willis of Docker.

Finally, be sure to register you and the rest of your team for the 2017 All Day DevOps conference. This year's event will offer 96 practitioner-led sessions (no vendor pitches allowed). It's all free, online on October 24th.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
