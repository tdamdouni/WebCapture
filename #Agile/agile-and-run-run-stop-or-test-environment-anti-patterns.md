# Agile and Run-Run-Stop, or Test Environment Anti-Patterns

_Captured: 2018-03-06 at 18:29 from [dzone.com](https://dzone.com/articles/agile-and-run-run-stop-or-test-environments-anti-p?edition=366207&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202018-03-06)_

**The Agile Zone is brought to you in partnership with [Techtown Training](https://dzone.com/go?i=275424&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddzone%26utm_medium%3Dfooter). Learn how DevOps and SAFe® can be used either separately or in unison as a way to make your organization more efficient, more effective, and more successful in our [SAFe® vs DevOps eBook](https://dzone.com/go?i=275424&u=http%3A%2F%2Fpages.aspeinc.com%2FSAFe-vs-DevOps.html%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_campaign%3Dsafe_vs_devops%26utm_content%3Debook).**

Ever noticed how organizational goals (or project goals) of being Agile often fall apart due to the unexpected stuff on the periphery? Yes, we have the "Post-It" Notes, we do the morning "Stand-ups" and the build guys have created a "CICD Framework". Then it all falls "off the rails," and suddenly there is a realization that the upstream, downstream, and instream IT & Test Environments (including Infra, Apps, Interfaces & Data) are not fit for the purpose, the supporting teams are not ready and, we enter a costly and painful remediation cycle. Bang goes Agile.

![Image title](https://dzone.com/storage/temp/8214165-long-run-run-stop-agile-anti-patterns-2018.png)

As someone who has spent many years watching the "repeating chaos," and someone who has an intrinsic interest in IT & Test Environments, I thought It might be fun to perhaps recognise this "phenomena" through discussing it as an "Anti-Pattern," and providing alternative patterns that would lead to simplification, better control, and ultimately less disruption.

> _An Anti-Pattern is a commonly occurring approach to a problem or task that generates decidedly negative consequences. Examples of Anti-Patterns in the software development might be: (1) spaghetti code, i.e. code that becomes unmaintainable and difficult to extend; or (2) duplicate code, i.e. code that has been cut and paste and now must be changed in two places._

## **The Top 8 Anti-Patterns of IT & Test Environments Management**

### **1\. Death by Spreadsheet**

Anti-Pattern: The organisation is heavily reliant on spreadsheets to identify current systems under management, their components, versions, and the projects using them. These spreadsheets often get out of date, are non-integrated across teams, and regularly become unusable.

Pattern: A centralised CMDB or Knowledge Portal that all teams can use for visualisation, modelling and ongoing-management of systems, components, relationships, versions, and, of course, relationships.

### **2\. System Contention Hell**

Anti-Pattern: Different teams "reactively" compete for the same system resources and components, causing test disruption & outages due to continual changes and re-configurations. Collaboration across projects is typically low and often results in finger pointing and arguments.

Pattern: Project requirements are identified early in the lifecycle and the correct system resources are shared with the most compatible teams. In areas of high contention, the organisation has time to provision new environments and/or re-prioritise to meet the spike in demand.

### **3\. Ninja Changes**

Anti-Pattern: Developers deploy changes during operational hours, without prior notice and re-configure applications on the fly. The test teams are blind-sided, experience unusual disruption and defects arise that are difficult to recreate or track.

Pattern: All environment activity is collaborated through group calendars that highlight scheduled events and statuses. Effected teams are notified of changes, via alerts or dashboarding, that may impact their project or team.

### **4\. The Email Support Vortex**

Anti-Pattern: Members across the project use email as a method to request test environment support and coordinate operational fulfilment. High volumes of emails go across different teams and fail to convey ownership, accountability, or correct operational procedures. Thus, requests become overwhelming, uncoordinated and are often ignored & orphaned.

Pattern: All environments, whether production or test, need a basic level of service management to prevent operational chaos. Although not necessarily as "heavy" as production, the organisation needs "just enough" service management to ensure all requirements are captured, tracked & closed.

### **5\. Superhero Provisioning**

Anti-Pattern: Deployment (data, application & infrastructure) operations are unrepeatable, manual, slow and error prone. They typically involve heroics from one or more subject matter experts and the use of "black magic." This chaotic approach consequently results in disruption to the end users, i.e. project and test teams.

Pattern: Organisations need to establish consistent tasks that are clearly documented and understood. Ideally these operations should evolve to become fully automated, "single command line" tasks that can be exposed through "self service" forms.

### **6\. Manual Health Checks**

Anti-Pattern: Every morning the test team will get in early to run various functional tests that ensure the application and the end-to-end business processes are working. Results are then emailed to the test teams. Process is typically time consuming and typically can only be done once a day.

Pattern: Implementation of Test Synthetics that can automatically run at any time of the day, (scheduled or in real time) to provide immediate insight into whether the end-to-end environments are healthy. Results can be communicated via real time dashboards and automated alerts.

### **7\. Stopping the Clock**

Anti-Patterns: Testing and projects are often delayed due to the various engineering/provisioning teams not being available to service them. For example, the infrastructure team are too busy to provide more virtual test environments, the deployment team are too busy to release the latest code version and the data team don't have time to provide more test data.

Pattern: Establishment of Self Service orchestration gateways (portals where provisioning automation is exposed & shared) will ultimately mean much of the "busy" work previously done by the Infrastructure, Application, or Data team can be completed by the testers or project team themselves.

### **8\. Creative Reporting**

Anti-Pattern: The test environment & release management teams spend many days (potentially weeks) per month collating and analysing non-integrated environment & release information with the intent of creating reports. Typically resulting in reports which are invariably inaccurate & untimely.

Pattern: Establish automated environment information aggregation that brings together all your IT environment & release information and generates real-time reports and dashboards that support analytics and decision making.

### **Learn More or Share Ideas**

If you'd like to learn more about IT & Test Environment Management anti-patterns, or perhaps just share your own ideas then then feel free to contact myself or the enov8 team. [Enov8](https://www.enov8.com) provides a complete platform for addressing organisations "DevOps at Scale" requirements. Providing advanced "out of the box" [IT & Test Environment Management](https://www.enov8.com/it-test-environment-management/), [Release Management](https://www.enov8.com/enterprise-release-management/) and [Holistic Data Management](https://www.enov8.com/dataview-holistic-test-data-management/) capabilities.

**Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=266427&u=http%3A%2F%2Fpages.techtowntraining.com%2FDevOpsRoadmapDzone_DevOpsTransformationRoadmap.html%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_campaign%3Ddevops-transformation), brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266427&u=http%3A%2F%2Fwww.techtowntraining.com%2F). **

Opinions expressed by DZone contributors are their own.
