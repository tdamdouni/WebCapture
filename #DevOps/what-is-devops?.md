# What Is DevOps?

_Captured: 2017-02-21 at 15:17 from [dzone.com](https://dzone.com/articles/what-is-devops-3?oid=twitter&utm_content=buffer8b943&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

#  What Is DevOps? 

### The role of DevOps is not limited to CI, CD, and automating releases. It's much more than that. Long story short — automate everything.

[ ![](https://secure.gravatar.com/avatar/2c6be0823cb6db1c3eb981dc3efa86c3?d=identicon&r=PG) ](/users/2952633/kanawade.html) by 

[ Nilesh Kanawade](/users/2952633/kanawade.html)

Jan. 24, 17 * [DevOps Zone](/devops-tutorials-tools-news)

[Discover how to optimize your DevOps workflows](http://info.saucelabs.com/paper-the-devops-journey.html?utm_campaign=devopsjourney+wp&utm_medium=textlink&utm_source=dzone-devops&utm_content=article) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](http://info.saucelabs.com/paper-the-devops-journey.html?utm_campaign=devopsjourney+wp&utm_medium=textlink&utm_source=dzone-devops&utm_content=article). 

I started working as a DevOps engineer couple of years back. My initial impression was that it optimized release management activities, which was not completely true. When I dived into it, I found that this was just a tip of the iceberg. The role of a DevOps engineer is not just limited to CI/CD and automating releases. It's much more than that. Long story short — automate everything.

The below diagram depicts that DevOps is the collaboration between development, QA, and operations teams.

![](https://media.licdn.com/mpr/mpr/AAEAAQAAAAAAAAgxAAAAJDkxZTg1YTViLTI3NzYtNDQzNi1iOGFhLTkzMTZiNmNjYmY5NA.png)

_[Source](https://en.wikipedia.org/wiki/DevOps#/media/File:Devops.svg)._

## **What Is DevOps?**

DevOps is a term emerged from the combination of Development and Operations. The role of a DevOps engineer is to automate all the operational work in the way that a developer would do. The idea is to encourage frequent releases to increase quality and get early feedback.

Hence, according to me, the main two objectives of DevOps are increasing the speed and quality the deliveries.

## **Where Did DevOps Come From?**

> "DevOps is the offspring of Agile software development.” — [Dennis Ehle](http://www.versionone.com/devops-101/what-is-devops/). 

Nowadays, Agile is an overloaded buzzword. Everybody has gone or is going Agile. Not only development but also other departments such as BA, QA, build-and-release engineers, etc. should keep up to speed. A DevOps engineer helps all of these stakeholders adopt Agile gracefully. They automate everything right from the planning phase to the release phase. They help the team move faster while maintaining high quality.

## **What Problem Does DevOps Solve?**

> “Ideas are cheap. Ideas are easy. Ideas are common. Everybody has ideas. Ideas are highly, highly overvalued. Execution is all that matters.” — Casey Neistat. 

Agile software development is one of the revolutionary changes that have happened to software development practices in recent decades. It advocates adaptive planning, evolutionary development, early delivery, and continuous improvement, and it encourages rapid and flexible responses to change. To make this happen, the entire development life cycle should be optimized. As for optimization, wherever it's possible, automation the key — that should be a no-brainer!

## **What Should Be Automated?**

Each and every phase of software development should be automated!

Some people may argue that automating everything is very ambitious or even impossible. However, I think that we should consider that stage as our final stage and work towards it. After all, we are implementing Agile, which is a continuous improvement process.

The main idea behind Agile is rapid and frequent delivery. Whatever is repetitive should be automated, or try to reduce the time spent on it. This should be applicable everywhere in the project.

## **DevOps Toolchain**

I have defined some categories for each phase of the SDLC involving DevOps tools. We should try to adopt at least one tool for each category to address the solution.

### **Planning and Analysis**

  * Capturing and tracking ([JIRA](http://www.atlassian.com/software/jira), [ServiceNow](http://www.servicenow.com/)).
  * Documentation or Wiki page ([Confluence](http://www.atlassian.com/software/confluence)).
  * Collaboration ([Slack](http://slack.com/), [HipChat](http://www.hipchat.com/)).

### **Design and Implementation**

  * SCM ([Subversion](http://subversion.apache.org/), [Git](http://git-scm.com/), [Mercurial](http://www.mercurial-scm.org/)).
  * IDE ([Eclipse](http://eclipse.org/), [IntelliJ](http://www.jetbrains.com/idea/), [Visual Studio](http://www.visualstudio.com/)).

### **Build and Release (CI/CD)**

  * Repository management ([Artifactory](http://www.jfrog.com/artifactory/), [Nexus](http://www.sonatype.org/nexus/)).
  * Build tools ([Jenkins](http://jenkins.io/), [Bamboo](http://www.atlassian.com/software/bamboo)).
  * Configuration management ([Chef](http://www.chef.io/chef/), [Puppet](http://puppet.com/), [Ansible](http://www.ansible.com/)).
  * Cloud ([AWS](http://aws.amazon.com/), [Azure](http://azure.microsoft.com/en-us/), [OpenStack](http://www.openstack.org/)).
  * Containers ([Docker](http://www.docker.com/)).

### **Integration and Testing**

  * Source code verification ([SonarQube](http://www.sonarqube.org/)).
  * Security testing ([HP Fortify](http://www8.hp.com/sg/en/software-solutions/static-code-analysis-sast/)).
  * Functional testing ([JUnit](http://junit.org/junit4/), [Cucumber](http://cucumber.io/), [Selenium](http://www.seleniumhq.org/)).
  * Performance testing ([SOASTA](http://www.soasta.com/)).

### **Operations**

  * Monitoring ([Splunk](http://www.splunk.com/)).
  * Analytics ([Adobe Analytics](http://www.adobe.com/sea/marketing-cloud/web-analytics.html), [Flurry](http://developer.yahoo.com/analytics/), [TeaLeaf](http://www-01.ibm.com/software/info/tealeaf/)).
  * BI ([Kibana](http://www.elastic.co/products/kibana), [Tableau](http://www.tableau.com/)).

## **Final Thoughts**

Although the terminology is somewhat new, the core concept of DevOps has always been there. Still, it brings a lot to the table. Hence, everybody has started to adopt DevOps. The implementation may differ from organization to organization, as it is highly dependent on management's priorities. It surely helps move things more quickly and maintain high quality.

[Download “The DevOps Journey - From Waterfall to Continuous Delivery”](http://info.saucelabs.com/paper-the-devops-journey.html?utm_campaign=devopsjourney+wp&utm_medium=textlink&utm_source=dzone-devops&utm_content=article) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](http://info.saucelabs.com/paper-the-devops-journey.html?utm_campaign=devopsjourney+wp&utm_medium=textlink&utm_source=dzone-devops&utm_content=article).

