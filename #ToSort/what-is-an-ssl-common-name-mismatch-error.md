# What Is an SSL Common Name Mismatch Error?

_Captured: 2017-06-22 at 03:05 from [dzone.com](https://dzone.com/articles/how-to-fix-ssl-common-name-mismatch-error?edition=305124&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-21)_

Address your unique [security needs at every stage](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre) of the software development life cycle. Brought to you in partnership with [Synopsys](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre).

An SSL common name mismatch error occurs when there is a mismatch between the domain name and the Subject Alternative Name (SAN) or common name of the SSL certificate. SAN allows you to list multiple domain names and subdomain names in a single certificate. This mismatch error occurs when the SSL certificate does not have the name entered in the browser address bar.

You may have observed this error if you had accidentally typed _https://uwxyz.com_ instead of _https://www.uwxyz.com/_ \- for example. However, if you had typed in the name of a website that had a multi-domain SSL that has multiple domains listed, then it would have opened even if it was _https://website.com_ or _https://www.website.com_. However, if the website did not have SSL and it had been trying to display as "https," then again, the browser would throw an error. Typical errors may display messages as listed below - depending on the browser and browser version.

**"Your connection is not private"**

Attackers might be trying to steal your information from <www.websitename.com> (for example, passwords, messages, or credit cards).

Common error messages inclucde:

  * NET::ERR_CERT_COMMON_NAME_INVALID

  * "The security certificate presented by this website was issued for a different website's address. Security certificate problems may indicate an attempt to fool you or intercept any data you send to the server."

  * "This server could not prove that it is websitename.com; its security certificate is from websitename.com. This may cause a misconfiguration or an attacker intercepting your connection"

## **Tips for Fixing a Common Name Mismatch Error**

Identify the type of SSL certificate installed for your website on the server. Then you must analyze why someone intending to visit some other domain got routed to your website. You must study the details of your SSL certificate and analyze the other domain names listed as a SAN. Analyze the common name, SAN details, IPs, and domains.

Reputed Certificate Authorities will offer SAN options that would effectively protect your domain. An SSL certificate would protect your common name. Warning messages are displayed when a typed-in web address does not match your common name because you had not included that website address in your common name.

You may get an error if your website shares an IP address with another website that has an SSL certificate. IP address sharing or shared hosting could lead to warnings. To be absolutely secure, in order to stay protected from spoofing websites, it is better to have a dedicated IP address - and some hosting companies have made it mandatory for a dedicated IP address if your website needs to have SSL.

A warning error may pop-up if Server Name Indication (SNI) is not being supported by either the hosting server or the connecting client or both. This issue is typically encountered in legacy systems. Ensure that your server supports SNI.

In case you have closed down one of your websites you must ensure that the DNS for that domain name points to your new website. Pointing to the old website can lead to an error. Also, avoid using the certificate of the hosting provider as it could lead to warnings.

Additionally, you must set up the configurations of your firewall and server correctly or else you may face issues.

Find out how [Synopsys](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3Ddzone-sig-post) can help you build security and quality into your SDLC and supply chain. We offer [application testing and remediation expertise](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsecurity-testing.html%3Fcmp%3Ddzone-sig-post), guidance for [structuring a software security initiative](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-strategy.html%3Fcmp%3Ddzone-sig-post), training, and [professional services](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-services.html%3Fcmp%3Ddzone-sig-post) for a proactive approach to application security.

Opinions expressed by DZone contributors are their own.
