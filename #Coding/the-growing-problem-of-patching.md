# The Growing Problem of Patching

_Captured: 2017-07-29 at 19:59 from [dzone.com](https://dzone.com/articles/the-growing-problem-of-patching?edition=311401&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-07-29)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

Bugs are part of the software lifecycle. Bugs and poorly coded software components introduce vulnerabilities waiting to be discovered and exploited. The process of running SAST and DAST tools to identify all the vulnerabilities in the software takes way more time than organizations can afford to spend. False positives are still a big problem that makes the whole process much more difficult to manage since it requires manual filtering from experienced security and software engineers.

A single SAST report could identify hundreds, if not thousands of instances, for each vulnerability. Even if organizations are willing to find and fix the vulnerabilities in their own code, applications can still be vulnerable since only **10% - 20%** of the code that runs on the system is actually written by application developers [[1](https://www.sonatype.com/2017survey)].

The rest is code for all the underlying frameworks, libraries, transient dependencies, servers, services, and even the runtime platform itself (JVM, .NET, etc). Vulnerabilities do not exist only in the application code but also in any other component of the above-mentioned software layers.

## A Vast Sea of Potentially Vulnerable Components

Some of these components are closed source, proprietary components, and some others - the vast majority in most cases - are open source. According to the latest study from Sonatype [[2](https://www.sonatype.com/ssc2017)], in 2017, **52 billion** Java open source components were downloaded from the Central Repository. That's a **68 percent increase** since 2016 which shows that the trend keeps on growing. There is no surprise here. Open source favors rapid innovation and fast deliveries and thus plays a central role in software development and lifecycle in general.

Sonatype analyzed 1.8 million Java components available in the Central Repository and identified that 5.9% of them contained a known vulnerability. Similarly, researchers from Northeastern University analyzed data from more than 133,000 websites and reported that 37% include at least one library with a known vulnerability.

The solution to fixing these vulnerabilities is usually a straightforward process. Simply patch the vulnerable component with a newer version. However, the reality is that this process can become very difficult to manage and scale since more than 10,000 new component versions are released daily, offering new features, bug fixes, and security patches [[2](https://www.sonatype.com/ssc2017)]. It is evident that Security and DevSecOps teams are overburdened and often cannot easily cope with the vast number of patches that need to be applied - especially in enterprise environments.

When a vulnerability exists in a third-party library, framework, middleware, or server you are at the mercy of the vendor. Vendors might not offer a patch. This could happen for many reasons. They may have stopped supporting older or legacy versions or because they might not accept the responsibility of the vulnerability.

Making the assumption that open source vendors offer patches for each and every identified vulnerability is a dangerous assumption. Based on Sonatype's research only **15.8%** of vendors actively fix vulnerabilities, while **84% do not actively provide patches** that remediate known security defects. Even for the projects that do actively provide patches for security vulnerabilities, the mean time to remediation (MTTR) was **233 days**.

In the base case, the absolute best suppliers, remediated known vulnerabilities in just two days. However, examining the other end of the spectrum, more than 800 vendors had MTTRs for known vulnerabilities greater than suppliers, remediated known vulnerabilities in just two days. However, examining the other end of the spectrum, more than 800 vendors had MTTRs for known vulnerabilities greater than **three years**, with 44 projects showing repair times over **seven years**.

## The Interesting Case of Apache Shiro

Apache Shiro, one of the most popular Apache projects, is an interesting example. It is a security framework for managing some of the most critical aspects of applications: authentication, authorization, and session management. A critical Java deserialization vulnerability in Shiro was reported in November 2015. Despite the criticality of the vulnerability, the fix was made available **6 months later**.

Interestingly, one cause for the delay may have been the fact that most known deserialization exploits were not working in Apache Shiro. Apache Shiro used a custom classloader that happened to be buggy and was failing to properly load arrays. This coincidental limitation may have delayed the fix since the vulnerability seemed to be, at the time, unexploitable. As a result, creating a fix was not so urgent anymore.

However, no organization can base their security on such a posture. The fact that the known payloads were failing to properly exploit the vulnerability because of the buggy classloader was entirely accidental and temporary. A workaround happened to become available recently [[3](https://bling.kapsi.fi/blog/jvm-deserialization-broken-classldr.html)], but similar working exploits could have also been available at that time, potentially being sold in the black market of 0-day exploits.

By not having available proper fixes on time, the window of exposure was unacceptably large for most critical enterprise applications. Organizations that depended on Apache Shiro had to be protected regardless of the presence of exploits in the wild or not. Since there were no fixes for such a long amount of time, organizations were forced to either accept the risk of this critical vulnerability or use workarounds that were not ideal solutions, produced false positives, and required significant manual tuning and configuration.

## The Latest Oracle CPU and the Current Climate of Patching

Despite some common misconceptions, vulnerabilities also exist in the runtime platform as well. Oracle provides quarterly fixes for the identified vulnerabilities in the Java Virtual Machine and the Java Runtime. These vulnerabilities could allow attackers to compromise the system even if the application developers write absolutely perfect and safe code in all possible ways.

To have a picture of the criticality of these vulnerabilities, let's examine the latest Critical Patch Update provided by Oracle. The latest CPU fixed 32 vulnerabilities in Java SE [[4](http://www.oracle.com/technetwork/security-advisory/cpujul2017-3236622.html)], of which 28 were remotely exploitable requiring no authentication. That's a **300% increase** of fixed vulnerabilities compared to the April 2017 CPU. Of these vulnerabilities, 66% are classified as high severity. Oracle always recommends users apply the CPU as soon as possible. This forces enterprises to plan for this update ahead of time and give it the highest priority.

However, not all organizations are able to go through this rigid and iterative process, especially since the deployment of the physical CPU requires binary changes and involves a significant amount of testing and deployment planning. Testing the patch is of paramount importance because each patch could potentially break existing application functionality. Such a break of functionality could cause catastrophic incidents [[5](https://aws.amazon.com/message/41926/)] [[6](https://www.facebook.com/notes/facebook-engineering/more-details-on-todays-outage/431441338919/)].

One significant limitation of the Critical Patch Updates offered by JVM vendors such as Oracle and IBM is that these updates are applied in an "**all or nothing**" approach. If one of the fixes breaks the functionality of an application in the environment, then the whole CPU must be rolled back. There is no way to drill down into the contents of the CPU and cherry pick specific security fixes from the CPU.

Most software projects have zero control over security patch deployment making deployment planning a complex process to manage [[10](https://cryptovillage.org/dc25/schedule.html)]. Also since deploying the CPU requires the servers to be restarted - potentially affecting the organization's SLAs - and each product could potentially have its own update schedule with different teams managing them, creating conflicting priorities, and update windows.

Patching at enterprise scale is hard, time-consuming, resource intensive, and expensive [[7](https://www.cs.columbia.edu/~smb/blog/2017-05/2017-05-12.html)]. It is common for organizations to have patch deployment windows every 90 - 120 days [[8](https://www.infosecurity-magazine.com/news/companies-average-120-days-patch/)] or even longer [[9](http://www.zdnet.com/article/financial-sector-takes-176-days-on-average-to-patch-security-vulnerabilities/)] resulting in an apparent conflict of priorities. Patching increases the risk of breaking existing functionality whereas not patching increases the exposure and the risk of attack.

Unpatched vulnerabilities are a fact of everyday life in many IT environments. Ransomware incidents, such as WannaCry, are more proof that enterprises are lagging behind patches. WannaCry managed to compromise more than 220,000 systems despite the fact that it exploited a known vulnerability. A vulnerability that should have been fixed in most infrastructures since Microsoft issued a patch more than 2 months before the WannaCry infections.

The patching problem cannot be solved by throwing more and more engineers to manually patch and test the applications. Also, asking developers to remediate all vulnerabilities is a no-win proposition since a large number of these vulnerabilities are not located in the application code that they write and control.

## Solving the Patching Problem

To solve the growing problem of patching, both of the following are needed:

### 1\. Active and accurate security controls that require minimum configuration able to completely remediate classes of common vulnerabilities (CWEs) or neutralizing attacks by mitigating known and 0-day exploits.

If such security controls are deployed in production, then the urgency to patch as soon as a patch becomes available is taken away and organizations no longer need to panic on every newly discovered vulnerability. However, no active security control can be deployed in production in unrestricted blocking mode if it generates false positives.

False positives are a major problem in production environments since they block legitimate requests. Stopping legitimate users from using the application is not an acceptable condition for most organizations. WAFs and other security controls that sit outside of the application use heuristic techniques such as signature patterns and behavioral detections are not adequate solutions to this problem since they generate large amounts of false positives and thus become noise generators.

In a traditional approach, reducing the number of false positives requires manual tuning and configuration from expert engineers. This manual process is exactly the opposite of what is sought and defeats the purpose of active and accurate security controls. Also, the security controls should not require extra configuration to be able to block 0-day exploits. The process of updating payload signatures for newly discovered 0-days is the exact opposite of what active protection means.

By moving the security controls from outside of the application to inside the runtime we achieve the visibility needed to eliminate all of these problems. Self-protecting runtime platforms using virtualization techniques have complete visibility of all the code that is executed as well as its execution context. This allows a new category of techniques to be applied that does not depend on heuristic approaches that traditionally have been the root cause of false positives.

These runtime techniques completely eliminate false positives and thus provide the highly accurate protection that is required for active security controls in production. Additional runtime techniques such as Name Space Layout Randomization (**NSLR**), Privilege De-escalation, and Runtime Compartmentalization offer the missing pieces of the puzzle for mitigating known and 0-day exploits proactively with minimum configuration.

### 2\. Automated, agile, and scalable patch deployment without breaking or restarting the application.

Enterprises will keep lagging behind patches and struggle to cope with the ever-increasing number of released patches unless the whole process becomes more automated, flexible and visible. Patch management and lifecycle software is a first good step that automates the notification of new vulnerabilities in software components. However, these are applicable only before the software reaches the production environments.

While in production, patching becomes a lot harder since applying physical patches require binary changes and even recompilation of the source code. Virtual Patching is the process of applying a patch without making binary changes to the application. Runtime protection solutions based on virtualization are able to apply virtual patches in an agile way without the need to recompile the application or restart the application or the platform. This greatly simplifies the process of patching, removes the urgency to prioritize the patching, and gives time to the DevSecOps and Security teams to deploy the physical patch according to their own update schedules. Finally, virtual patching offers fine-grained visibility of what gets patched and allows organizations to cherry pick which patches are important to their environments and lets them roll back patches of specific CVEs that are not compatible with the existing application functionality.

Cybersecurity is only as strong as its weakest link and lack of patching could be the weakest link. Fortunately, with the proper infrastructure and secure-by-default runtime platforms, patching can be streamlined and unpatched software can cease to be a problem.

## References

  1. Scott Arciszewski - The Why and How for Secure Automatic Patch Management ([Def Con 25](https://cryptovillage.org/dc25/schedule.html) \- July 2017) 

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.

Opinions expressed by DZone contributors are their own.
