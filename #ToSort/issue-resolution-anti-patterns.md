# Issue Resolution Anti-Patterns

_Captured: 2018-01-26 at 18:24 from [dzone.com](https://dzone.com/articles/issue-resolution-anti-patterns?edition=355142&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-01-26)_

The DevOps Zone is brought to you in partnership with xMatters. xMatters delivers integration-driven collaboration that relays data between systems, while engaging the right people to proactively resolve issues. [Read this best practices guide and learn 4 steps that are critical to DevSecOps success](https://dzone.com/go?i=273425&u=https%3A%2F%2Fwww.xmatters.com%2Fresources%2Freports%2Fdevsecops-best-practices-guide%3Futm_campaign%3D70138000001F6XsAAK%26utm_source%3Ddzon%26utm_medium%3Dbanner%26utm_content%3Ddevsecops-best-practices-guide).

[This article is featured in the new DZone Guide to DevOps. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/devops-culture-and-process)

In the battle between software delivery speed and infrastructure stability, speed is winning. Organizations are releasing software faster than ever before to keep up with market demand. But when speed comes at the expense of software quality and incident response, organizations suffer, along with their customers and partners.

The benefits of DevOps are well documented, and companies continue to prove them. According to the 2017 Puppet State of DevOps Survey, top performers deploy 200 times more frequently, have change failure rates that are three times lower, and recover from failure 24 times faster.

When xMatters worked with Atlassian on a survey of more than 1,000organizations about their DevOps environments, more than 60% said they were enjoying the benefits of DevOps that they expected. Lost in the details, however, another 1,000 organizations didn't even make the cut in the survey report because they didn't have a well-defined DevOps plan.

For top performers and luddites alike, there are barriers to ideal development and operations processes, and there are solutions. We're all spoiled for systems that work perfectly every time from anywhere, so near perfection is about the only way to keep our customers happy.

## Barriers to Perfecting DevOps

Sometimes people outside the DevOps realm think DevOps is a prescriptive set of guidelines like ITIL, but it's really a philosophy of working together and sharing the load to produce faster deployments and releases. How that philosophy manifests itself in the real world is up to each organization based on their use cases, personnel, and appetite for risk.

So, organizations have had nearly a decade to replace their separate development and operations teams with a more collaborative culture, and they have been pretty successful overall. In fact, according to the xMatters-Atlassian survey, more than 80% of organizations share tools between development and operations. The breakdown is in the knowledge sharing.

When teams have to request access to information, or access timeouts, or their access is limited to certain areas, delays build up and trust is reduced.

According to the xMatters-Atlassian survey, more than 90% of organizations share knowledge in at least some way. However, three-quarters of those organizations have restrictions on what knowledge is shared.

Part of the problem is that organizations still have to look at other systems to get the information they want. If companies automated the way data moves between systems, they wouldn't have to stop and give explicit consent every time they wanted to share information.

For instance, if an APM tool catches an error in an application running in a dev environment, an IT ops manager might open a Slack or HipChat channel, and an incident manager might open an incident in Jira. If they pull in additional engineers and they have to search both Slack for the conversation thread and Jira for incident details, they waste valuable time. If the Slack channel is available in Jira, everyone can collaborate easily in one place.

## Problems With DevOps and Incident Management

As you can see in the Puppet survey, leading DevOps organizations are limiting errors and resolving incidents faster than their less DevOps-ish counterparts. But the number of errors that reach production after companies release software is still alarmingly high.

Nearly half of organizations say they have to fix errors in production. One in every 15 organizations has major issues with new application releases, forcing rollbacks.

Why is the error rate so high? With so many quality monitoring tools available, organizations are recording virtually everything that happens in their systems, so it's not a data collection issue. In fact, more than 60% say their monitoring solutions predict potential issues before users are affected. Instead, it goes back to the knowledge sharing we talked about earlier.

When an incident occurs, incident managers are in a race against time to resolve it before it can affect customers, employees, or even a wider swath of people out there. So, every element that delays discovery and action puts the company more at risk.

Are such elements showing themselves during incident management situations? According to the xMatters-Atlassian survey, they certainly are:

> "DevOps has a clear call for more individual autonomy, yet 50% say they have to wait for the operations center to declare a major incident before taking appropriate action. DevOps relies heavily on automation, but 43% still use a manual process to keep customers and internal stakeholders up to date. DevOps is supposed to empower individuals to have an impact on the organization, yet 34% say waiting for subject matter experts delays incident resolution. DevOps is supposed to improve communication across teams and systems, but 29% say duplicate tickets are created while the incident is being resolved. DevOps is supposed to streamline processes, yet 23% say tickets are routed without proper assignments and must often be rerouted."

## Incident Management Solutions

There are a few methodologies and technologies to mitigate these issues, including:

  * **Targeted messaging:** Developers love themselves some code, and when they don't have a ready solution, they are apt to build it themselves. When it comes to CI tools like Jenkins or TeamCity, developers on large teams are likely to build their own instances until the cluster gets too confusing. So, when a message from Slack or HipChat comes in, exactly who should respond can be contentious. As a best practice, document instances of your CI tools and target messages to the developers who need to receive them. An error in your CI processes might just be some discomfort at first, but unaddressed discomfort becomes pain.

  * **Culture and process:** Surprisingly, more than half of organizations practicing DevOps do not have documented incident management procedures they can follow and repeat. ITSM organizations live and die by their incident response processes. For some reason, that culture of repeatability has not moved over to DevOps yet. Virtually every DevOps organization has monitoring tools in place and processes for testing. When things go wrong, most organizations have the tools in place to implement similar processes during development cycles or for more major incident situations in production.

  * **Data and information: **When a product test fails in production, QA or testing teams log it so the errors can be fixed. Advanced APM tools can even uncover the root cause of the errors. But that information can get locked up in siloes, and the engineers who have to do the work have to ask for it or discover it for themselves by poring over code. Automated routing can pass along not only the test results but detailed analysis from monitoring tools and MOM systems.

## Conclusion

DevOps environments can be chaotic enough when everything goes right, especially if you're releasing code multiple times per day. Automation can help replace chaos with repeatable process…until it breaks. And it will break.

And when it does, be prepared to resolve incidents and get your development and software delivery cycles back on track quickly. In today's world of daily (or more) releases, waiting until morning can be a disaster.

[This article is featured in the new DZone Guide to DevOps. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/devops-culture-and-process)

[4 Steps to an Effective DevSecOps Infrastructure](https://dzone.com/go?i=273426&u=https%3A%2F%2Fwww.xmatters.com%2Fresources%2Freports%2Fdevsecops-best-practices-guide%3Futm_campaign%3D70138000001F6XsAAK%26utm_source%3Ddzon%26utm_medium%3Dbanner%26utm_content%3Ddevsecops-best-practices-guide). Check out [xMatters](https://dzone.com/go?i=273426&u=https%3A%2F%2Fwww.xmatters.com%2Fsolutions%2Fdevops%2F%3Futm_campaign%3D70138000000quUrAAI%26utm_source%3Ddzon%26utm_medium%3Dbanner%26utm_content%3Dxmatters-website).
