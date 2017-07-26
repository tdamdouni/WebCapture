# Web Application Security: The New Way Forward

_Captured: 2017-04-23 at 10:17 from [dzone.com](https://dzone.com/articles/web-application-security-the-new-way-forward?edition=292908&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-22)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

The Web Application Firewall (WAF). It's tech that never really was. That statement might upset some people reading this -- namely those who sell web application firewalls. However, for anyone that has had to implement a web application firewall, they will probably agree that it is a fair assessment.

## Web Application Firewalls Are Not Firewalls

Out of the gate, WAFs were destined to have problems. The name just wasn't right. Sure, the web application part is true, but calling it a firewall was not the best choice. Firewalls block things. They isolate network segments. They have rules that match source and destination and allow or block based on the rules. For much of network security, firewalls were the panacea. Got a security problem? Throw more firewall at it.

The problem is that application security is a different animal than network security. Applications reside at the top of the OSI model and are meant to do all sorts of interesting things for users. While it's easy to make a rule disallowing access to a certain port by a certain network segment because it is a simple true/false decision, it is much more difficult to determine whether the application is being attacked or if it is supposed to behave that way. Classically, in application security, we bring up the example of users with single quotes in their name: Is it SQL injection? Or is it [Tim O'Reilly](https://medium.com/@timoreilly)? (Hi Tim, if you see this, I just want to say I am a big fan!) Determining good vs. bad in applications is difficult and a much grayer area than the network security space.

## Application Security Roots

Let's look back at the beginnings of the WAF. In the early days of web applications when web applications started running code on the client's browser, the rise of now commonly known problems like [cross-site scripting](https://blogs.msdn.microsoft.com/dross/2009/12/15/happy-10th-birthday-cross-site-scripting/) (XSS) began. It became clear that something had to be done. In September of 2001, the [Open Web Application Security Project (OWASP)](https://owasp.org/) was formed. It was born out of the realization that with the rise of the web app, there was also a growth in security problems (like XSS) that was not likely to slow down. The industry called this Application Security, later to be dubbed AppSec.

As the industry began to wrestle with application security problems, OWASP published guidance like the [OWASP Top Ten](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project) and other documentation to help developers and security engineers find security problems in their code. The industry also realized that an appliance or proxy sitting between the application and the client could stop some of these application security problems. Through the 90s and early 2000s, buying an appliance to solve a problem was a common occurrence. Load balancers, firewalls, and network gear were flying off the shelf and onto the racks.

It was in these early days that the WAF came on the scene. An appliance that would look at traffic before it got to the application and detect things like XSS, command execution, and SQL injection. On the surface, it all made sense, in reality, it struggled to fulfill this basic goal and promise of security. What's worse is that WAFs were being implemented in these early days for the wrong motivation: to solve development lifecycle problems.

## The Problem Statement WAFs Purportedly Solved

If you remember in the early 2000s, most people did waterfall development and long release cycles. Sure, there were some outliers, but on the whole, web development was treated in the same waterfall method as everything else. This meant development lifecycles that lasted 6 months or more. Write specs, schedule a release, write code, send to QA, release. Somewhere in there, security testing was supposed to take place, but it rarely happened.

In AppSec, new vulnerabilities were coming out daily. New encoding methodologies were discovered to hide attacks, a bespoke set of bypass techniques for new defenses, and even [completely fresh denial of service options](https://en.wikipedia.org/wiki/Slowloris_%28computer_security%29). Most of these vulnerabilities were being found in existing web applications, web servers, and development frameworks. Due to the way development worked on a 6-month horizon, this became an intractable problem.

The real fix for these vulnerabilities would have been to change the code in the application or update the development framework; however, one approach that gained headway in the industry was to use a web application firewall as a stopgap measure. It was commonly understood that even if there were no developers available to fix the vulnerability (because they were all busy on a different 6-month development effort), it could be easily assuaged with the WAF. Find XSS on your site? No problem, use a WAF until you can get a developer to fix it.

## The Ground Shifted With Agile and DevOps

While AppSec matured both in training developers on defensive measures and the security industry set out busily implementing "WAF as a stopgap" measures, the underlying structure of how code is developed and released changed dramatically.

In the mid-2000s, an uptick in the use of Agile began. Small and medium shops started shipping code weekly. Instead of the long requirements gathering phases, design, development, testing and deployment were now being done simultaneously in short iterations. The value of Agile to the business became apparent -- instead of untested ideas, lots of work in progress, and an unmanageable backlog, the business could get much quicker feedback on the expensive development and engineering resources. Around 2009, this change cascaded to operations.

In 2009, DevOps was coined by Patrick Debois and in that same year, [John Allspaw](https://medium.com/@allspaw) famously declared that [Etsy](https://medium.com/@etsy) was doing 10 deploys a day at [O'Reilly](https://medium.com/@OReillyMedia)'s Velocity Conference. [DevOps was a natural extension of Agile](https://theagileadmin.com/what-is-devops/) to the operations teams, but it has since grown into the way to describe a complete transformation of how we deliver software. [Gene Kim](https://medium.com/@RealGeneKim), [Jez Humble](https://medium.com/@jezhumble), [John Willis](https://medium.com/@johnwillis) and Patrick Debois have cataloged this in their [seminal book on the topic](https://www.amazon.com/DevOps-Handbook-World-Class-Reliability-Organizations/dp/1942788002). DevOps unlocks the IT value stream, aligns the delivery cadence, and orients software around the customer. It is completely transforming the industry.

Along the way, amidst all the cultural and process changes brought on by Agile and DevOps, we have seen an incredible change in how web applications are defined. Dynamic loading, API-first design, and the expectation of highly performant sites have fueled the growth of JavaScript frameworks, new DSLs, and the NoSQL database movement. Couple all this with cloud architecture patterns and a [microservices approach](https://martinfowler.com/articles/microservices.html) to web applications, we have a completely different landscape than when the WAF was first created.

> If applications look nothing like they did 10 years ago, why are we using the same application security approach? 

## The Way Forward Is Familiar but Different

Application Security has moved away from treating security as a black and white, binary decision. As an industry, we are now thinking in terms of attack chains and self-protection. This means the application or web server is instrumented and detects the early steps an attacker makes. From these detections, feedback loops are created back to operations, security, and developers in the ways of alerts, graphs, and defensive actions.

There is a new language to describe this new approach to application security defense: Runtime Application Self-Protection (RASP). Using a hybrid approach of Next Gen WAF and RASP might be the way to defend web applications in the modern era.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
