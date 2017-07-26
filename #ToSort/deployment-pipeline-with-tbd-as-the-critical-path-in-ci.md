# Deployment Pipeline With TBD as the Critical Path in CI

_Captured: 2017-03-22 at 22:08 from [dzone.com](https://dzone.com/articles/deployment-pipeline-with-trunk-based-development-t?oid=twitter&utm_content=buffer6de05&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

The focus of all organizations historically is to strive to deliver software in the shortest possible time with the best quality and at optimal cost. As a means to achieve this goal, organizations have been trying out various techniques, tools, methodologies, and frameworks. The organization that is able to do this and that meets all the critical parameters is able to meet the customer expectations and move ahead in the marketplace. Many organizations thus focus on time to market (TTM), quality, and cost as key KPIs as part of their yearly goals.

As per the _[2016 State of DevOps Report](https://puppet.com/resources/whitepaper/2016-state-of-devops-report)_ published by Puppet Labs and DORA (DevOps Research and Assessment), high performers are deploying 200 times more frequently than low performers with 2,555 times faster lead times. They also have the fastest recovery time and the lowest change failure rate.

Various techniques and practices cumulatively grouped under the broad umbrella of Continuous Delivery (CD) can help organizations to deliver software faster with improved quality and optimal cost.

It is observed that software is notoriously difficult to ship. In order to address this aspect, one important conceptual Continuous Delivery (CD) practice that helps in facilitating this requirement is Continuous Integration (CI), which is more effective when it is also implemented along with Trunk Based Development (TBD).

CI can also be undertaken without TBD, but the full effects of CI will be felt when we use TBD. TBD is the norm in high-performing organizations such as Google. The focus on TBD is being observed more recently, though some teams have done it earlier. The connection between TBD and CI may not be readily apparent, but when we delve a bit deeper, we can intuitively observe that Continuous Integration at the high level is consolidated incrementally through TBD.

Additionally, when all the members are working on the same branch, this increases visibility into what every member is doing, reduces duplicate effort, and increases collaboration. Visual Management Indicators are a key concept in Lean and Agile, and TBD provides a means to achieve these goals.

Critical Path is a term from the field of project management that describes a set of tools, methodologies, and methods. Critical Path is the path with the least amount of slack in a sequence of linked work packages. Thus, borrowing the analogy and tweaking it and applying it in software development, if we meet the critical path requirements and we know the time taken for the critical path, we can take steps to minimize the critical path through automation and other techniques and it thereby brings down our time to market.

In the case of software development, the critical path is the deployment pipeline. The deployment pipeline facilitates effective workflows with TBD and the deployment pipeline is the critical path from build to production. Any delay on the critical path will affect the time to market of the application.

If the application delivery is modeled along this pipeline starting from build (trunk to mainline) until production, the visibility is available to the members to deploy continuously to production. Additionally, this visibility also translates into reliability as things that are visible can be managed appropriately and it increases reliability. The pipeline is generally modeled as a series of stages, as this is again linked to the high visibility that stages provide into the pipeline.

If there is any failure in any stage of the deployment pipeline, we can isolate it easily as compared to one monolithic single stage pipeline where it takes too much time to identify where the problem is in the pipeline. This also takes into account the concept of modularity to bring visibility to the entire deployment process.

Forks with very short lifetimes (less than a day) before being merged into the trunk and having two active branches at maximum, merging code into trunk or branch are important aspects that need to be managed, and these type of guidelines helps to contribute toward higher performance. Additionally, teams that don't have code freeze periods (when people can't merge code or pull requests) also achieve higher performance.

Similarly, just as we have Infrastructure as Code (IaC), we also have Pipeline as Code (PaC), which describes a set of features that allow Jenkins or other CI users to define pipelined job processes with code, stored and versioned in a source repository. These features allow Jenkins/other CI tool to discover, manage, and run jobs for multiple source repositories and branches thereby eliminating the need for manual job creation and management.

This automatically shortens the time for the critical path which would not have been possible if it was done manually. As we can observe, all the activities that are done to automate or shorten the critical path lead to improved time to market for the application. One of the techniques to achieve maximum reduction in the duration of the critical path is the PAC concept, which helps to automate all the activities and thereby lead to reduced TTM for the application.

Thus, CD tools that use the deployment pipeline can enable workflows with TBD. This, in turn, leads to a reduction in time to market. The organization benefits from this time reduction through improved customer relationships and customer satisfaction and the ability to meet the changing market requirements.

Hence, the deployment pipeline with trunk-based development (TBD) as the critical path in CI is an important area of focus during the implementation of Continuous Delivery practices.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).

### Like This Article? Read More From DZone

Topics:

devops ,continuous deployment ,deployment pipeline ,continuous integration ,critical path ,trunk based development
