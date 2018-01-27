# There Is No 80/20 Application Security Rule

_Captured: 2017-12-20 at 11:43 from [dzone.com](https://dzone.com/articles/there-is-no-8020-application-security-rule?edition=347096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-19)_

Discover how to provide [active runtime protection](https://dzone.com/go?i=255346&u=https%3A%2F%2Fwww.waratek.com%2Fruntime-application-self-protection-rasp%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Drasp) for your web applications from [known and unknown vulnerabilities](https://dzone.com/go?i=255346&u=https%3A%2F%2Fwww.waratek.com%2Fruntime-application-self-protection-rasp%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Drasp) including Remote Code Execution Attacks.

## Focusing Only on the Code You Write Leaves You Dangerously Vulnerable

Take a look at the chart below. It's the current number of software flaws in the US National Vulnerability Database (NVB) as of 09.00 GMT on 22nd November 2017. That's important because the NVB is updated every hour. The total stands at 12,537. At the end of 2016, the total was 6,446 - slightly less than half of the current number of flaws with roughly six weeks left in the year.

![Image title](https://dzone.com/storage/temp/7539072-cvss-distribution-time.jpg)

These are the known software flaws that impact applications, platforms, operating systems, libraries, and third-party components and create the gateways for malicious hackers to exploit. As is plain to see, the overall number of flaws is increasing on an absolute and a relative basis.

Focusing just on web applications shows the same trend. The latest view of how pervasive code flaws are in web applications comes from [software analysis firm CAST](http://www.castsoftware.com/news-events/press-release/press-releases/download/cast-research-on-the-state-of-software-security-reveals-riskiest-applications) which makes it clear why we continue to see an acceleration of successful attacks.

## Which Applications Are the Most Vulnerable?

Out of 278 million lines of Java and .NET code CAST reviewed in 1380 applications, there were 1.3M vulnerabilities caused by errors and poor code practices. The worst offenders with the highest ratio of flaws to lines of code were financial institutions which are among the most attacked enterprises. Looking at which applications are the most vulnerable, .NET apps (surprisingly) had a higher average number of flaws than Java-based applications, which still had an unacceptably high rate of flaws - especially those under some form of continuous development.

These stats come at the same time when there was a renewed discussion (debate is too strong a word) about where security teams should focus their efforts to protect applications: only secure the code written by company/third-party developers or protect the entire application software stack? At the risk of a poor pun, this is not a binary decision.

## ![](https://cdn.aws.waratek.com/v2/wp-content/uploads/2017/11/8020.png)

Why Should You Protect the Entire Application Stack?

The reality is, security teams can and should focus on the code they write. Reducing flaws should always be a developer's goal and there are highly effective tools to help reach that objective.

However, the business logic layer accounts for only 10-20 percent of an app stack. Focusing protection only at the top of the stack, as some experts advise, leaves applications vulnerable to a host of attacks via flaws in the remaining 80-90 percent of the application. That's where you find open source components, libraries, APIs, server operating systems, etc.

If you think these flaws can be ignored or won't impact you, take a look at the vulnerabilities recently patched by Oracle, Microsoft, IBM, and other OEMs. You'll see high severity flaws in core products like the Java Virtual Machine or Windows Server being found and fixed, sometimes after years of going unexploited. Those flaws are not in the business logic layer of apps and neither are the flaws found in the third-party components and libraries like the Struts 2 framework.

## What Is the Best Way to Secure the Entire Application Stack?

Scanning and monitoring tools can help find vulnerabilities, but they can't mitigate flaws. Traditional approaches to application security can only protect the business logic layer - and then only using heuristics to guess what is and is not an attack, often generating false positives and slowing app performance in the process.

Application security using a [secure virtual container](https://www.waratek.com/container-security/), however, offers highly accurate protection without requiring code changes or slowing an application with instruments or filters. And, your applications are [actively protected](https://www.waratek.com/runtime-application-self-protection-rasp/) against known and unknown flaws in the entire application stack - not just the code developed by your team.

That's important because there is no 80/20 rule in application security. _**Your code is 100 percent protected or it's not.**_

Find out how Waratek's award-winning [application security platform](https://dzone.com/go?i=255347&u=https%3A%2F%2Fwww.waratek.com%2Fapplication-security-platform%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappsecplatform) can improve the security of your [new and legacy applications and platforms](https://dzone.com/go?i=255347&u=https%3A%2F%2Fwww.waratek.com%2Fsolutions%2Flegacy-platforms%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dlegacy) with no false positives, code changes or slowing your application.
