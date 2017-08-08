# Open-Source Software Security

_Captured: 2017-07-30 at 16:01 from [dzone.com](https://dzone.com/articles/open-source-software-security-the-nerd-is-no-longe?edition=310400&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-26)_

Discover an in-depth knowledge about the different kinds of [iOS hacking tools](https://dzone.com/go?i=222228&u=https%3A%2F%2Fweb.securityinnovation.com%2Fhacking-ios-applications-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dhacking-ios-applications) and techniques with the [free](https://dzone.com/go?i=222228&u=https%3A%2F%2Fweb.securityinnovation.com%2Fhacking-ios-applications-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dhacking-ios-applications) iOS Hacking Guide from Security Innovation.

Open-Source Software (OSS) has become increasingly popular in the enterprise these days. The GitHub Open-Source Survey [1] indicates that 84% the respondents said their employers accept or encourage the use of open-source dependencies in their code base. There are many reasons for the popularity of OSS:

  * Not having to pay onerous licensing fees.
  * No need to re-invent the wheel when there is so much excellent OSS already written to do what is needed. This allows faster application development.
  * The ability to easily customize code to meet the needs of the developer.
  * Not being locked into a particular vendor.
  * Developers use OSS components to form the bulk of an application and just write "glue" code to hold everything together.

### OSS vs COTS and Custom Software

OSS has many of the same types of problems that commercial software does. Although there aren't fees for licensing, maintaining licensing compliance can be complicated, particularly if an application is using many different OSS components and libraries from different sources - each with different licensing requirements.

The security of OSS is very similar to the security of commercial software - it varies and is often just as bad as commercial software can be. The primary reason is simple: people write software, and writing **secure** software is hard to do. Just like many commercial software developers, OSS developers may not have strong secure coding skills or security testing expertise, and if the application is working, it's ready for prime time.

There is a tendency for people to think that since OSS is available for anyone to review, and that many/most/all of the bugs have been found and fixed. This is the fallacy of Linus's Law [2] which states, "given enough eyeballs, all bugs are shallow." The infamous Heartbleed vulnerability in OpenSSL is a well-known example of such a failure. Most likely, people's mental model of OSS is "since the code is available for review, we assume that others have looked at it, so there is less of a need for us to do so." As a result, OSS code may get less security scrutiny than if the code is closed source.

### Managing OSS

The first step in managing OSS risk is knowing what OSS components are being used in all of your applications. It's common that organizations don't have a full inventory of their OSS. As a result, it's difficult to know what software is vulnerable or has already been patched. Getting a full inventory is a non-trivial problem, particularly with containerized applications and with applications on mobile, web, desktop, cloud, and embedded platforms.

Maintaining licensing compliance for a variety of OSS components throughout the organization can be challenging for both internally and externally developed applications. Additionally, component warehouses are immutable sources of components, including those with known security defects. Development teams may rely on such vulnerable components to build their applications.

Lastly, the lack of organizational standards around the use of OSS often gives development teams the freedom to use whatever OSS components best meets their current needs. This results in many different kinds of OSS being incorporated into applications, making it harder to monitor and update as issues are found.

### Securing OSS

OSS is often incorporated into a project without a security code review or any other security assessment. In an analysis of over 1,000 commercial applications, Black Duck [3] found 67% of the applications with open-source components contained known vulnerabilities. Using libraries or components with known vulnerabilities is tantamount to professional negligence.

OSS components age and can become vulnerable if not actively maintained. Sonatype [4] found that older components had 3 times the rate of vulnerabilities. Some OSS developers do a better job of keeping the software patched against known vulnerabilities, but it is not easy to stay current when there are so many different OSS components on so many different platforms.

Another factor is developers often use a library or component with a known vulnerability either because they are unaware that the component is vulnerable or they are not able/not permitted to upgrade to the newer, more secure component. The result is an application that gets shipped with a vulnerable component.

Fixing applications with known vulnerable components is surprisingly challenging. In theory, it might be possible to just rebuild the application with a newer version of the vulnerable component. In reality, however, APIs and functionality change, so the application needs to be fully re-tested to ensure the fixes work and didn't introduce any new vulnerabilities. This is a time- and cost-consuming effort, often getting skipped in exchange for a timely product release.

## Improving Open-Source Software Security at Your Organization

There are a number of approaches to improve the security of OSS.

  * **Implement and Enforce Open-Source Software Organizational Policy: **An organizational policy that covers the use of OSS is important to minimize the out-of-control use of unauthorized OSS components. It is also important to enforce this policy. Automated tools can help with compliance.  

  * **Use Local Component Repositories: **Local component repositories ensure that approved and secure OSS components are used to build applications. This provides a way of gaining visibility into these components and provides some level of control. Components in a local repository tend to have fewer vulnerabilities because they are kept current.  

  * **Use Automated Tools to Manage OSS: **Automated tools can help by inventorying applications and handling licensing compliance. These tools are also helpful by notifying the organization of vulnerable components and components that need to be updated.  

  * **Validate and Verify OSS: **Just as you would validate and verify software written by your development teams, any OSS software used in your applications should be given the same level of security scrutiny. This means doing code reviews (manual and automated), as well as dynamic and static code analysis, as appropriate.

Open-source software is popular for many good reasons, but it must be treated as other software is, including evaluating the security of every OSS component used in all applications.

Learn about the importance of a strong culture of cybersecurity, and [examine](https://dzone.com/go?i=232227&u=https%3A%2F%2Fweb.securityinnovation.com%2Fbuilding-a-culture-of-cybersecurity-adv%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dbuilding-a-culture-of-cybersecurity) key activities for building - or improving - that culture within your organization.
