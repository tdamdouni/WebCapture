# 4 Things That Every Developer Should Know About Security

_Captured: 2017-05-14 at 17:32 from [dzone.com](https://dzone.com/articles/4-things-that-every-developer-should-know-about-se?edition=298099&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-13)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

It is of the utmost importance to focus on security from the very beginning of the software development process in order to prevent attacks and protect the users worldwide. Here are a few things every developer should know about security.

## Do Not Trust Any Input

The best way to start is to never trust any input. Securing software demands that any information and data received is thoroughly checked. The fact is, preventing malicious inputs from entering your software, as well as preventing it from ever being processed will make your software that much harder to attack or breach.

However, in most cases, developers have a tendency to check inputs against incorrect data values. This is a mistake because attackers can easily bypass the use of incorrect values and change the pattern for the correct data values that allows them to pass through unnoticed. Instead, developers should check the input against the pattern for correct data values that they know are safe and reject any input that does not match that pattern.

## Reduce the Attack Surface

When talking about software environments, the attack surface would be the sum of all points and attack vectors, where a hacker or an unauthorized user can breach the security and enter in data order to steal sensitive information. The attack vector is the method that malicious code, such as viruses or worms, use to infect and spread across a computer.

Hackers only need to find one vulnerable point for their attack to succeed and breach security. That is why organizations try to reduce the attack surface of a software or system and make it harder for hackers to find a weak spot. Organizations need to visualize the system and map out all the paths, networks, and devices in order to find as many vulnerable points and eliminate the threat of exposure.

For instance, it is important to have a secured in-house project management software, but it is also important to perform a [project management tools comparison](https://activecollab.com/best-project-management-tools-comparison) and decide which software is the best suited for an organization before implementing it. Furthermore, your organization should continue to test for vulnerabilities even after the implementation of the software.

It is important to remember that reducing the attack surface does not mitigate the damage a hacker can do if they breach security. However, it reduces the chance of security failures by reducing the attack surface of a system or piece of software. Reducing the attack surface means reducing the amount of code running, having less code available to unauthorized users, and reducing a number of entry points that hackers can exploit.

## Fail Securely

Every system is bound to fail sooner or later and that is unavoidable. In some cases, developers think that their software is special and that it can never fail - it will and the best solution is to prepare for failure and make sure it [fails securely](https://www.owasp.org/index.php/Fail_securely). The problem with failures is that once they occur, the system starts to behave insecurely and starts to show security issues.

Hackers cannot wait for such failures to happen. Sometimes they will attack the system so that they trigger a certain failure after which they can take control of the system or software. That is why it is important to have a contingency plan.

In the case of a system failure, it is important to secure defaults, which means denying access. Furthermore, return values for failure should be checked, while all changes must be undone and restored to a secure state upon failure. The privacy and the integrity of a system need to remain intact even though accessibility has been lost.

Moreover, hackers must not be permitted to gain access to restricted data that is generally inaccessible during a failure. When a system fails, it can reveal sensitive information about the failure to potential attackers and it can provide them with the additional knowledge that will help hackers create an effective attack. Failing securely means denying access by default and to allow access only once the conditions to allow have been verified.

## Use Threat Modeling

One of the best ways to improve the security of a software or application is to test them in threat modeling. Basically, threat modeling simulates how an attacker would breach security and take over control or extract valuable data from software. A developer can identify the vulnerable points in their software and eliminate the risk or a threat.

[Threat modeling](https://www.owasp.org/index.php/Threat_Risk_Modeling) should be simulated in the beginning of the development process, as well as nearing the end of the process. That way a developer can determine if any security vulnerabilities managed to slip through the initial phase of testing or if there were any oversights during the writing of the code.

Normally, threat modeling is based on identifying security objects, such as securing the identity of a user, loss of reputation due to misuse of an application, and surveying the application's data flows, components and trust boundaries.

After the assessment, an application is analyzed for security threats and security vulnerabilities. Furthermore, the application is exposed to attack trees that simulate the hacker's perspective and determine the conditions by which an attack would be successful. This is a good way to determine which security controls need to be in place in order to prevent attacks and secure the application.

## Security First

Software development is a complicated process, but without securing it, all the effort that has been put into development, can all be for naught if hackers find a way to abuse the software. Every developer should focus on building security into the software right from the beginning because dealing with security after the fact is much harder and much more expensive.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.

Opinions expressed by DZone contributors are their own.
