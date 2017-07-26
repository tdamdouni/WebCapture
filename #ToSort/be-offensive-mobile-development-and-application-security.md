# Be Offensive: Mobile Development and Application Security

_Captured: 2017-02-20 at 20:23 from [dzone.com](https://dzone.com/articles/be-offensive-mobile-development-and-application-se?edition=272881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-20)_

### Mobile devices and applications have found a foothold in our daily lives at an alarming pace. Here are some ways developers can be more offensive with their processes and procedures.

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

From 2008 to 2016, the number of mobile applications in the Apple AppStore has risen from around 20 thousand to over 2.5 million, and the Google Play store has seen similar growth. That's a jump from 40 thousand applications to over five million in less than a 10 year span, not to mention the sheer number of private and/or internal only applications. How many different, mobile developers or groups does it take to develop that many applications? And how many of those developers take a security mindset or build security processes into their development? Mobile devices and applications have found a foothold in our daily lives at an alarming pace.

Typical application security practices were used in mobile out of the gate. What I mean by this is, applications were dreamt up, they were developed, they were deployed to users, and then they were assessed for security vulnerabilities. Bugs were found, patches were applied, and the cycle continued. I would call this being defensive. It's a passive way to finding the issues and trying to put a band aid on them after the fact. Being defensive in our security practices is a traditional approach, and to an extent, has worked in a waterfall-like development environment with long development times, review cycles, and the time to fully examine programming code line by line. However, mobile, in my opinion, has moved organizations and developers away from the waterfall process and into a more agile or fast-paced development cycle. And it is here to stay. We no longer have long development life cycles, but instead, have fast paced dreams, stories, development, and delivery. The problem is, security requirements aren't less restrictive, so something has to give. I say, "Be Offensive!"

## 5 Ways to Be Offensive in Your Mobile Development

  1. Write and test security stories. Identify the logic and interfaces within your application where security issues may manifest themselves. Write stories for password complexity, authorization, storing sensitive data, transmitting sensitive data, using operating system and hardware capabilities, etc. 

  2. Mobile security testing should encompass APIs as well! Use proxy tools (such as Burp, OWASP Zap, etc) and implement them in ALL testing. This means development, quality assurance, security, and any additional layers of testing that your organization may have.

  3. Employ the use of security tools DURING development. Some examples of these include: idb, cycript, frida, MobSF, etc.

  4. Test with real devices, running multiple levels of the target Operating System. Learn how to jailbreak or root your devices and understand what that actually means. Rooting and jailbreaking are commonplace, and understanding the impacts to consumer and client devices and our applications will allow us to build more securely. 

  5. Validate production deployments to public app stores. We shouldn't blindly trust app stores for applications we install on our business-controlled mobile devices, so why should we trust them for storing and deploying our mobile apps? Deploy to the app store and then validate the authenticity of the application once downloaded.

The use of mobile applications and devices will only increase -- and at a staggering pace -- so, as a business, we should acknowledge and embrace this by becoming more offensive in developing our mobile applications.

I will be explaining all of this in more detail at MobileWebDevCon in San Francisco. Please join me there! <http://go.gsmiweb.com/devcon/dzone/davelindner>

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
