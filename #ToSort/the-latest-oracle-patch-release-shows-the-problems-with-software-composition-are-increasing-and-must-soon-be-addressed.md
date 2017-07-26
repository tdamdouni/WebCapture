# The Latest Oracle Patch Release Shows the Problems With Software Composition Are Increasing and Must Soon Be Addressed

_Captured: 2017-04-20 at 00:00 from [dzone.com](https://dzone.com/articles/the-latest-oracle-patch-release-shows-the-problems?edition=292898&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-19)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

![Image title](https://dzone.com/storage/temp/5018623-banner2.jpg)

## **Summary**

The April 2017 Oracle Critical Patch Update contains more than 30 Java-related CVEs, including:

  * Eight (8) CVEs that directly affect the core Java Platform.
  * Nearly 70% of the Java-related CVEs, including 87% of the Java Platform CVEs, are remotely exploitable without authentication.
  * Belated remediation for more than one dozen high-profile software composition vulnerabilities which, in some cases, date back as far as 5 years.
  * Included in these belated remediations are the "celebrity superstar" vulnerabilities, Apache Struts v1 _and_ v2 as well as Apache Commons.
  * Users should not just rely on the installation of this CPU to mitigate all the identified vulnerabilities. In some cases, manual profiling and extra configuration are required.

With the latest Oracle patch release, we have one of the largest software vendors in the world, with expert security resources and dedicated testing and remediation teams, belatedly discovering and responding to the presence of major, known-vulnerable components buried deep in the software stacks of their core software platforms.

The April CPU shows the scale of the challenge that the information technology industry as, a whole, faces in securing modern modular enterprise applications which are composed of dozens or sometimes hundreds of third-party libraries and modules. If a best-of-breed software vendor like Oracle struggles to account for and secure their third-party library dependencies in a major software platform like Oracle Fusion, then how can an "ordinary" enterprise, which is not a sophisticated IT vendor, be expected to do any better?

The pace of the discovery of software composition vulnerabilities is accelerating quarter-by-quarter and year-by-year. As a result, the IT industry faces an impending crisis point if it does not rapidly begin adopting and embracing automated remediation solutions to detect and protect software composition vulnerabilities at runtime in any application, at any layer of the software stack, without human intervention or manual testing.

## **Recommended Actions**

If you are using a Runtime Application Self-Protection solution that uses virtualization, and therefore is non-heuristic, you will already be protected against a number of the vulnerabilities included in the Oracle patch, such as the Apache Struts 1, 2 and Commons CVEs.

Virtual patches are available that address the remaining appropriate April CPU vulnerabilities which should be applied to receive immediate protection without restarting your applications.

Alternatively, you should apply the appropriate binary patches from Oracle as quickly as possible, as nearly three-quarters of the CVEs addressed in the April 2017 CPU can be remotely exploited without credentials.

However, installing the new CPU may not be enough. Manual profiling and configuration are also required in some cases. For example, the fix for CVE-2017-3509 requires users to:

  * Install the new CPU.
  * Profile their applications and environments to determine if caching for HTTP NTLM connections is required.
  * Change the JVM launcher system properties and set the new `jdk.ntlm.cache` property to false.

This change must be done with caution because disabling NTLM connection caching could cause severe performance and usability side effects in some cases.

## **Final Thoughts**

The sheer number of software vulnerabilities and the ubiquitous nature of software flaws simply mean that the protective measures we've relied on for decades are now unable to provide the level of protection required. Automated runtime application security solutions are the only way that end-users - even the most sophisticated ones - will ever be able to get ahead of the crashing vulnerability wave.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.

Opinions expressed by DZone contributors are their own.
