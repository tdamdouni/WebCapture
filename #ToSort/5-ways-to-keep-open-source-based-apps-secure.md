# 5 ways to keep open source-based apps secure

_Captured: 2017-04-23 at 23:33 from [techbeacon.com](https://techbeacon.com/5-ways-keep-open-source-based-apps-secure?utm_campaign=Black%20Duck%20Press&utm_content=51826910&utm_medium=social&utm_source=twitter)_

![Lock with city lights in background](https://techbeacon.com/sites/default/files/styles/article_hero_image/public/field/image/secure-open-source-apps.jpg?itok=mqOY7tcc)

> _Lock with city lights in background_

The use of open source for application development continues to grow. A recent Forrester Research report called attention to [open source's pre-eminence ](https://www.blackducksoftware.com/2016-future-of-open-source)in application development, citing that custom code now often constitutes only 10 to 20 percent of many applications.

Open source is used in numerous applications in all industries by organizations of all sizes. The reasons are straightforward: Using open source lowers development costs, speeds time to market, and accelerates innovation.

More than 80 percent of all cyberattacks specifically target applications. Application attacks are both harder to detect and more difficult to contain than network attacks. The combination of these two facts--applications are the No. 1 target of cyberattacks and open source is the foundation of most of today's application code--leads to the inevitable conclusion that open-source vulnerabilities are one of the biggest risks to application security.

Open source is neither more nor less secure than custom, proprietary code. However, there are certain characteristics of open source that make vulnerabilities in popular open-source components attractive to attackers: Open source is target-rich, traditional testing tools are ineffective in identifying open source, and few companies understand the breadth of open source being used in their applications (more on these points below).

This lack of knowledge translates into a lack of awareness about vulnerable components, leaving organizations exposed to attack. Here are five steps you can take now to manage open-source risks.

### 1\. Inventory your open source

You can't secure what you're not tracking, so your first step needs to be an inventory of all open-source components your teams use to develop software. A complete open-source inventory must include all open-source components, the version(s) in use, and the download locations for each project in use or in development. You'll also need to include all dependencies--the libraries your code is calling to and/or the libraries that your dependencies are linked to--in your inventory.

### 2\. Map your open source to known security vulnerabilities

Sources such as the National Vulnerability Database (NVD) can provide information on publicly disclosed vulnerabilities in open-source software. But be aware that not all vulnerabilities are reported to the NVD in a timely fashion and that the format of NVD records often makes it difficult to determine which versions of a given open-source component are affected by a vulnerability. You should not rely on the NVD as your sole source of vulnerability information.

### 3\. Identify other open-source risks you may face

Failure to comply with open-source licenses can put organizations at significant risk of litigation and compromise of intellectual property. Similarly, the use of outdated or poor-quality components can compromise the quality of applications that use them. Are you using a current version of the open-source component? Is it the most stable? Is the component actively maintained by a robust community?

### 4\. Create and enforce open-source use policies

Many organizations lack even basic documentation of open-source policies that would help them mitigate risks. You should have a single responsible entity--either a person or a committee--overseeing open-source usage, documented policies, and developers' awareness of their responsibilities when it comes to open-source use.

### 5\. Continuously monitor for new open-source risks

With more than 3,600 new open-source vulnerabilities discovered every year, the job of tracking vulnerabilities doesn't end when applications leave development. Organizations need to continuously monitor for new threats as long as their applications remain in service.

### Understand the risk of open source

As I previously noted, open source is ubiquitous in applications. Hackers take the easiest path when determining exploits and choose applications that offer the best attack surface opportunities. Those opportunities are generally created by unpatched or outdated software.

Open-source vulnerabilities and exploits are usually publicly disclosed, a dual-edged sword for both open-source and proprietary code that is a matter of much debate in the security community. If discoverers disclose vulnerabilities with exploitation details, "black hats" can use the information to launch attacks. But if discoverers do not disclose vulnerabilities publicly, the affected software may remain unpatched and vulnerable.

Finally, open source has a "pull" support model--users are responsible for keeping track of vulnerabilities as well as fixes and updates for the open source they use rather than having those fixes "pushed" out to them.

#### Traditional testing not effective at identifying open source in apps

According to the National Security Agency (NSA), the average SAST tool can only find 14 percent of the problems in any given application. Most open-source vulnerabilities are reported by security researchers and not found by application development teams using DAST and SAST application security tools.

#### Most companies ill-informed about open source in use

With over 3,600 new open-source component vulnerabilities reported in 2016--almost 10 per day on average and a 10 percent increase from 2015--the need for effective open-source security and management is clear. However, Black Duck audits of client code consistently reveal that many organizations are blind to the security and license compliance risk that their use of open source may expose them to.

### The most important step you can take

At this point, readers may have concluded that manually managing their open-source use will entail significant investments of time, resources, and budget, impacting both developer productivity and the overall software development lifecycle. That's why many organizations turn to an automated solution to simplify open-source risk management, enabling them to inventory open source in their code, protect against security and other open-source risks, and enforce open-source use policies effectively and cost-efficiently.

Whatever your choice, while it may seem easier to just keep doing what you're doing and hope for the best, the most important step you can take is to put some type of open-source security management process in place. Application vulnerabilities are the No. 1 security threat to your organization. Without inventorying, managing, and securing the open-source components used in those applications, you're providing attackers with an easy target.
