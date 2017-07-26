# Devops, Security, or Both: Who Holds the Reins to Container Deployment and Management?

_Captured: 2017-05-10 at 00:40 from [dzone.com](https://dzone.com/articles/devops-security-or-both-who-holds-the-reins-to-con?edition=298034&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-09)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

The DevOps-Security hybrid model is not a new thing. [Gartner first introduced this model nearly five years ago](https://www.gartner.com/doc/1896617/devopssec-creating-agile-triangle). It was driven by the need to define where DevOps' responsibility for security starts and ends, and how security teams can facilitate a streamlined process for building and deploying software in a secure manner.

Since then we've come a long way and today this model is often referred to as [DevSecOps](http://info.aquasec.com/gartner-devsecops-devops-security-report). The beauty of this hybrid model is that it integrates the best of both worlds - delivering value that is greater than the sum of its individual parts.

In the container space, DevSecOps becomes even more relevant and actionable. Until recently, DevSecOps wasn't so easy to achieve due to the lack of standardized, usable technology and tools. But now, the path to DevSecOps is open.

## **Security Is Not Traditionally a DevOps Thing - and Vice-Versa**

Let's take a look at the "traditional" roles of DevOps and security.

### **DevOps**

The DevOps movement sprung up as a push to get developers (the dev part) and operations (ops, the people who manage servers) a little closer. In the container space, rapid development cycles mean that DevOps tend to perceive traditional security processes and controls as impediments - stumbling blocks that they need to address but don't necessarily have the time or mindset to handle.

In container environments, images are assembled by developers from self-sourced and/or open source components. This places tremendous power in the developers' hands, and as Spiderman has taught us: with great power comes great responsibility. For reasons of preferring expediency over security, developers may choose to use unvetted code. Or they may inadvertently include code with known (or unknown) vulnerabilities. Either way, this can represent a serious security risk.

At the same time, developers can't be expected to know and address all security risks. Security is not their main responsibility; creating and running applications is. This means that they can't afford to dedicate a large portion of their time to security checks.

### **Security Professionals**

Security teams are traditionally responsible for creating and enforcing the procedures and policies that determine what constitutes acceptable vs. unacceptable risk. They may not be the ones fixing the vulnerabilities, but they do decide which vulnerabilities must be fixed. In order to accomplish this, Security requires visibility and enforcement capabilities over the process and outcome. They need to know which containers are running where, and be able to establish a clear container security checklist.

This is good in theory. The problem is that rapid container development cycles strain traditional security processes and controls. They truly can't keep up with the pace of change. In some organizations, we see that they have tried to cope with this by periodically shifting security experts into their DevOps team. This is great for the short-run but what about the long-run? That's why we see a steady shift towards the combination of both DevOps and Security.

By collaboratively and transparently integrating security at multiple points in DevOps workflows, the new DevSecOps model minimizes the impact on agility and speed while maximizing the security of the build and ship process.

This process is often referred to as "[shifting security left](https://www.safaribooksonline.com/library/view/devopssec/9781491971413/ch03.html)" - moving security practices into the early phases of design and coding, instead of applying them haphazardly at the last minute before release. The DevSecOps model offers a security schema that fits the way container developers think and work - incremental, automatic, efficient, and repeatable.

### **How to Start Talking DevSecOps?**

To facilitate implementation of the DevSecOps model, security controls must be automated within DevOps toolchains. From a process standpoint, security needs to start "[talking DevOps](http://blog.aquasec.com/devops-terms-security-pros-need-to-know)", not the other way around. The tools used need to be transparent to DevOps teams, and shouldn't impede DevOps agility - yet at the same time fulfill legal and regulatory compliance requirements, with full control over policy and visibility given to security teams.

Container technology is probably the great enabler of DevSecOps. Not only does it make for rapid, repeatable application development and deployment cycles, but it also makes it possible for them to be more secure. Containers are immutable and therefore are never patched in runtime, but simply replaced with new versions. This shifts much of the security controls to the "left", i.e., upstream into the development cycle.

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
