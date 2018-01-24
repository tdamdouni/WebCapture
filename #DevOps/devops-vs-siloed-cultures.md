# DevOps vs. Siloed Cultures

_Captured: 2018-01-23 at 00:12 from [dzone.com](https://dzone.com/articles/devops-vs-siloed-cultures?edition=357094&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-22)_

[Learn more](https://dzone.com/go?i=250324&u=http%3A%2F%2Fblog.scalyr.com%2F2017%2F08%2Fcareerbuilder-resolves-customer-issues-5x-faster-scalyr%2F) about how CareerBuilder was able to resolve customer issues 5x faster by using Scalyr, the fastest log management tool on the market.

[This article is featured in the new DZone Guide to DevOps. Get your free copy for more insightful articles, industry statistics, and more! ](https://dzone.com/guides/devops-culture-and-process)

The emergence of DevOps philosophy has introduced a welcomed manner in the way Information Technology (IT) professionals view the gap between development and deployment. Coupled with Continuous Integration/Continuous Deployment (CI/CD), implementations of a DevOps mentality can streamline efforts which were tedious at best for teams which utilized legacy deployment routines.As DevOps gains momentum, it is important to understand the DevOps culture and how it differs from alternative strategies.

## The Siloed Culture

In order to gain an appreciation of the DevOps model, providing a backdrop of a common deployment approach can help illustrate the issues that were faced for years -- as application development teams built applications and interacted with application server administrators (or web administrators) to deploy the result of their development efforts.

[Consider this comic](https://static.dzone.com/static/guide/2018/vester2.jpg). Under the model illustrated above, there was a clearly defined separation between the role of the application developer and the responsibilities of the application administrator. The development team would finish their development and unit testing, then toss the resulting application over to the application administrator, who was responsible for deploying the application properly in order to pave the way for testing and final validation.

On one side, the development team wore metaphorical blinders to limit their focus to the application functionality, with the underlying mechanics of the application server foreign or out-of-sight to them. In contrast, the application administrator was focused on getting the application deployed and available, wearing a similar set of metaphorical blinders to deflect any issues or bugs with the underlying program code.

To the development team, their primary objective was getting their application deployed -- unaware of all the other applications application administrator had to maintain. In fact, the expectation of the application administrator was that they almost had a photographic memory -- remembering everything they did last time to make the deployment successful, plus keeping track of additional requirements based upon drive-by conversations which occurred days (if not weeks) earlier.

As one might imagine, this model didn't seem to work out well, especially as the ratio of applications/development teams increased for a given application administrator. Not only were bottlenecks commonplace, but the ability to understand every supported application became problematic...if not impossible.

## Introducing DevOps

Adoption of the Agile software development introduced improvements to the way applications were designed and built. While focusing on shorter iterations, or sprints, smaller teams could work directly with a business representative to deliver a series of features and functionality. This process alone delivered value to the business faster, in contrast to other development lifecycles which provided a larger delivery over a longer time period.

The concept of Continuous Integration/Continuous Deployment (CI/CD) introduced the desire to release updates or features on a continual basis. With the Agile teams delivering features on a two- or three-week basis, the aspect that was initially missed was the deployment of the unit of code that was ready for use. Application administrators had worked in a model where a large release would happen on a quarterly (or longer) basis, allowing the ability to support multiple teams. With the adoption of Agile and CI/CD, the workload for the application administrator was increasing, since each team had something new to deploy on a monthly basis -- if not sooner.

DevOps became this new idea that broke down the walls between the application developers and the application administrators. The realization of CI/CD demanded a new model. As a result, DevOps became the union of Development (Dev) and Operations (Ops). Instead of being outside the Agile process, the DevOps team would become part of the Agile process, participating in the planning stage, procuring tools and technologies to make CI/CD a reality and providing a level of monitoring for the applications under their support.

## * as Code Is Born

In the days of the comic illustration (above), the process to prepare a release for deployment often required a series of manual steps.These steps would range from validating dependencies, creating some type of archive that could be deployed, making configuration changes to match the current environment, and validating the application deployed as expected. Since a majority of these tasks were manually driven, the potential for an issue to occur during deployment was higher than desired, with challenges centered around debugging scenarios where an unexpected error or failure occurred.

As a part of the CI/CD implementation, the idea of "* as Code" was born. The notion behind this concept is to rid the deployment of manual steps and embed those steps into a script that can be automated and executed when desired. In fact, with application container technologies, a CI/CD pipeline can be established that executes on code check-in and will accomplish all the manual steps noted above -- including starting and validating the application is running. With a successful CI/CD pipeline in place, the same steps that are executed on the developer's workstation are ultimately executed in production, largely removing the challenges with a deployment model based upon a series of manual tasks.

## The Culture of DevOps

With this understanding of DevOps and how this role fits into an Agile lifecycle, it is important to understand the culture behind DevOps. Unlike the Siloed Culture represented in the comic(above), DevOps teams are simply another Agile team. They work in small groups, tightly coupled with the applications they support, moving fast to support the needs of not only the developers introducing features, but the customers utilizing the applications being deployed.

The DevOps team is an extension of the Agile team, focusing on continuous improvement of the process and walking away from the previous "us vs. them" mentality. In fact, in the Agile world, the metaphorical blinders must be removed. Those same metaphorical blinders are removed from the DevOps team as well.

The culture of DevOps also bridges the gap between the application code and the deployment code. Since the "* as Code" concept is in place, everyone on the team has the ability to view the underlying application code and the deployment code, which is called via an established CI/CD pipeline (that is also stored in a human-readable format). As a result of DevOps, a culture is born where silos no longer exist.

## Conclusion

For years, if not decades, a siloed culture had success within IT. Often paired with long-running Waterfall development projects, the application administrators were able to maintain the workload to manually deploy application code -- since releases were quarterly, yearly, or even longer. However, as development teams began to utilize Agile practices, the ensuing workload on the application administrator became unmanageable and problematic.

These deployment teams soon realized a culture shift was required to meet the new demand for their skills. With the idea of CI/CDgaining momentum, the concept of DevOps was born, changing the way in which teams worked together to deliver applications ina code-driven, standardized manner that could be reproduced in every aspect of the development lifecycle.

The change which complements a successful DevOps implementation provides teams who work together (thus avoiding the blame game) and participate in Agile ceremonies with the side benefit of continuous improvement across the IT landscape.

[This article is featured in the new DZone Guide to DevOps. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/devops-culture-and-process)

**[Find out more](https://dzone.com/go?i=250325&u=http%3A%2F%2Fblog.scalyr.com%2F2014%2F05%2Fsearching-20-gbsec-systems-engineering-before-algorithms%2F) about how Scalyr built a proprietary database that does not use text indexing for their log management tool.**
