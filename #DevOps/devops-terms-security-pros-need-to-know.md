# DevOps Terms Security Pros Need to Know

_Captured: 2017-04-28 at 22:11 from [dzone.com](https://dzone.com/articles/devops-terms-security-pros-need-to-know?oid=twitter&utm_content=buffer277aa&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

Take one of the growing IT areas today, combine it with skyrocketing [demand](https://www.indeed.com/jobtrends/q-Devops.html), and there you have it: DevOps is here to stay. And the sooner security teams grasp the DevOps methodology, the better. There are many different ways in which security teams can adopt DevOps practices and embed themselves into the process, but one thing is becoming very clear - the old security methods and tools will not work in the long run, with some requiring slight adaptation while others will need to be completely replaced.

In my recent blog, I offered a primer on key security concepts that DevOps should become familiar with. Now I'd like to mirror this for security professionals. Hopefully, this will help your organization take its first steps in the meshing of security and DevOps, and eventually understand what it means to ensure efficient container security while maintaining a fast development environment. In other words: what it means to practice an effective [DevSecOps](http://info.aquasec.com/gartner-devsecops-devops-security-report).

## **1\. Continuous Integration (CI)**

This technique continuously merges source code updates from all the developers on a team into a shared mainline, in order to prevent merge conflicts by integrating code from different developers as soon as it's available. CI offers a real-time window into the actual state of the software system and quality measurements, which allows immediate and constant engagement of all DevOps team members. CI also creates an opportunity for security teams to enforce secure coding practices and vulnerability assessment early in the SDLC.

## **2\. Continuous Delivery (CD)**

A series of practices that enable code to be pushed rapidly to QA/testing, and sometimes production environments. Continuous delivery means shipping every change to a production-type environment so applications and services will always be in a deployed-ready state. Due to this verifiable automated environment, DevOps know that applications and services can be confidently delivered whenever they're needed. Generally, the same automated security tests that are built into the CI process can be built into the CD process. The difference is of course that CD is "the last frontier" before an application goes into production, so enforcement should be sharply defined.

## **3\. Build Automation**

Automated builds allow DevOps to compile source files, package compiled files into compressed formats, and produce installers - all with no human involvement. When the build steps are repeatable and can be done with no information other than stored source code, then it is automated. To be able to integrate security services, the implemented functions that control the building automation services have to be protected against unauthorized access and malicious interference.

####  **4\. Feature Teams**

Feature Teams consist of members from every department that deal with feature development; developers, quality assurance (QA), production engineers, and program or product managers. Ideally, they work in a big room together or close by, in order to shorten communication paths and speed up information exchange. From the idea stage to operations, each team is fully responsible for the feature it's tasked with. Any challenges that arise within their specific feature is to be solved by the team. Becoming part of a feature team can be a great way for security professionals to ensure that no downstream security risks are created.

## **5\. Site Reliability Engineer (SRE) **

SRE teams combine software development, networking, and system engineering expertise. These teams are mostly tasked with building and running large-scale, massively distributed software systems and infrastructure. Often, SRE teams are part of the development of automation systems to enable the scale and speed necessary for enterprises. Since SRE teams make many architectural decisions that affect security, it makes sense for security to be represented within those teams, or risk facing a "secure this after the fact" scenario.

## **6\. Canary Rollouts **

Also known a canary deployment or canary launch, canary rollouts are intended to reduce the risk when introducing a new software version in production. Named after the canaries historically used in coal mines to detect poison gas, this is essentially a rollout of a new version to a small group of users, which allows these users to assess the overall system before rolling it out to everybody. It is especially useful for Web applications (SaaS). Canary releases are a best practice for Agile development organizations practicing continuous delivery to move faster. Security teams can also use this technique to monitor applications in a lower risk environment before they become widely accessible.

## **7\. Failing Forward **

In the event of a problem in a new release, the natural tendency is to roll back to the last good version - but sometimes it's not possible, or smart, to restore the system to its previous state. In a fail-forward mode, a new production environment is set up alongside the existing production system. Using a canary process, traffic is gradually sent to the new system. If there's a problem, the new environment is pulled out, and original environment continues as normal. This "no going back" method encourages teams to quickly fix issues rather than fall back on old versions that stymie progress.

## **8\. ChatOps **

ChatOps is the automation of operations using an automated chat "bot". The Chatbot is configured to execute commands, through custom scripts and plugins, issued by DevOps team members. These commands range from code deployments to security event responses and team notifications. Security professionals themselves are moving to automated practices using ChatBots, such as the one from [Demisto, ](https://www.demisto.com/product/)which can help a security team move at DevOps speed.

## **9\. Application Release Automation (ARA)**

ARA is the consistent, repeatable, and auditable process of packaging and deploying an application from development to production. When done right, ARA eliminates the need to build and maintain custom scripts for application deployments. It also cuts down on configuration errors and downtime. From a security standpoint, ARA can be used to enforce application security policies that would otherwise require manual vetting, for example, around allowed server configurations, data protection, and other aspects.

## **10\. Minimum Viable Product**

The idea is to create a prototype of the intended product with the minimum amount of effort in order to determine if the idea is a good one. So that if significant changes are needed, less time and effort has already been spent. At times, this means cutting down on features or advanced settings in order to focus on the core concept, or on features rather than design or performance. MVPs allow organizations to improve more quickly while reducing cost and waste. Security teams can use MVPs to vet new systems for structural security risks, however, when the MVP is fleshed out the results of the early tests will need to be re-validated.

## Time to Move From Security to DevSecOps

These 10 terms are only a partial list, but in today's rapidly converging environments, it is imperative that security teams understand the DevOps mentality and ethos better. Security can't be applied as an afterthought or without understanding how applications are developed and delivered. Nor can they use the security tools of yesterday to gate speedy DevOps deployments. Learning to speak each other's lingo is a good start.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
