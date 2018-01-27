# How to Use Varnish to Make Your Cache Infrastructure GDPR Compliant

_Captured: 2018-01-21 at 19:43 from [dzone.com](https://dzone.com/articles/how-to-use-varnish-to-make-your-cache-infrastructu?edition=355113&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-21)_

Address your unique [security needs at every stage](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre) of the software development life cycle. Brought to you in partnership with [Synopsys](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre).

All European businesses (and in fact all companies that do business with Europe) have at least one thing in common until May 25, 2018. They are all hustling to comply with the new General Data Protection Regulation (GDPR). The reason? The consequence of non-compliance can result in a hefty fine worth 4% of the company's annual revenue. For most businesses, getting such a fine is not a risk worth taking.

## **What Is the GDPR?**

The GDPR is considered to be the most significant piece of European data protection legislation to be introduced in Europe for decades. It replaces the European Data Protection Directive from 1995 and seeks to unify data protection laws across Europe. Its purpose is to give back control of their own personal data to private citizens. Not only do companies need to be able to show evidence that they handle personal data with respect and care, they are also strongly encouraged to encrypt that data to protect it from getting into the hands of the wrong people, for example via malicious cyber attacks.

## **Encryption Is the Key**

It is a well-known fact that cybercrime is on the rise and the damages it causes are predicted to reach $6 trillion annually by 2021. Out of more than 9 billion data records that have been stolen since 2013 only 4% were encrypted. The lucky few who had encrypted their data records rendered the stolen data useless. This means that out of 9 billion data records, only 360 million were encrypted while the remaining 8.6 billion got used by cybercriminals.

## **How Can Varnish Help You Encrypt and Protect Your Data?**

Varnish offers integrated SSL/TLS support with both a client-facing TLS and a backend TLS, which in combination form one modern, minimalistic, and fast TLS proxy.

### **Client-Side SSL/TLS**

Hitch is a scalable, open-source network proxy that terminates SSL/TLS connections and forwards the unencrypted traffic to one of the available backends. It can handle up to 3,000 TLS protocol negotiations per second. Its process-per-core model architecture lets it manage tens of thousands of connections on multicore machines.

In addition to supporting TLS 1.0, 1.1, and 1.2, it also offers:

  * SNI, with and without wildcard certificates.
  * Support for HAproxy's PROXY protocol.

### **Backend SSL/TLS**

Varnish Plus offers SSL/TLS connections for the backend side of your architecture to safeguard it from possible attacks/leaks. This means that any request handled by Varnish will be encrypted before it's sent to the backend server(s).

Many companies require their inter-machine connections to be TLS connections. Thus, when caches are distributed around the world to serve different regions it is of the utmost importance to encrypt data exchange between the caching nodes and the backend servers. For example, when using Varnish within a CDN the long-haul connections that are transferred through the public internet will benefit from encryption. With the upcoming GDPR adoption, this type of encryption is strongly recommended and may become crucial to protect the data your web server produces and analyzes from cyber attacks.

### **Total Encryption**

Varnish engineers are currently working on a brand new feature, which is designed to encrypt all your caches across Varnish instances at all times. This _Total Encryption_ feature will help prevent bugs like [Cloudbleed](https://en.wikipedia.org/wiki/Cloudbleed) from causing leaks of sensitive data from your caches. You can read more details about the _Total Encryption_ feature in an upcoming blog post. And you can learn all there is to know about total encryption as well as Varnish and SSL/TLS during our upcoming webinar "[How to make your cache infrastructure GDPR compliant."](https://info.varnish-software.com/webinar-gdpr-cache-infrastructure)

## **Minimizing Your GDPR-Related Vulnerabilities**

Among the several new rules that make up the GDPR, there is one which states that businesses must notify their local data protection authority if they experience a security incident that affects the integrity, confidentiality, or security of the personal data that they hold. Said breach must be reported if and only if the leaked data can result in identity theft, fraud, or any other type of damages for the data subjects (the people whose personal information has been leaked).

Businesses who have implemented appropriate security measures, protecting both the leaked data and the data subjects, will not need to notify authorities about such breaches as the stolen data will be useless to the perpetrators. Thus, if the leaked data is encrypted and therefore can't be used, then no reports of such leaks must be made.

That's yet another good reason to lock down your data and connections to deliver a safe and performant experience for your users.

Find out how [Synopsys](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3Ddzone-sig-post) can help you build security and quality into your SDLC and supply chain. We offer [application testing and remediation expertise](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsecurity-testing.html%3Fcmp%3Ddzone-sig-post), guidance for [structuring a software security initiative](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-strategy.html%3Fcmp%3Ddzone-sig-post), training, and [professional services](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-services.html%3Fcmp%3Ddzone-sig-post) for a proactive approach to application security.
