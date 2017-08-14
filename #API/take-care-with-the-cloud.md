# Take Care With the Cloud

_Captured: 2017-08-06 at 01:17 from [dzone.com](https://dzone.com/articles/take-care-with-the-cloud?edition=313394&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-05)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

Cloud computing is so common today it should just be called "computing." Everybody is using cloud resources to some degree today. There are significant advantages to using the cloud after all - scalability, better cost distributions for startups, and yes, security. Security can be a problem too, but not necessarily in the way you might think.

There's a large number of arguments used against cloud computing that just don't hold water. We've heard most of them - things like you can't trust who's working in the data center, you don't know where your data is stored (this one does have some potential issues actually), or that you really can't trust the security posture of these kinds of companies.

For the most part, these are just not true. Cloud computing companies are very serious about physically securing their facilities, and they have much more resources with which to do this as a result of their large scale. They carefully vet employees and closely monitor systems for a potential intrusion. And they're better at it than your company is. They have more experience and more money on their side.

Of course, physical data location has become more of an issue in the past few years, but cloud providers have provided ways to ensure that your data is physically stored where you'd like it to be stored. That way you can keep it out of countries that may have more unpredictable information collection laws.

Cloud computing providers are a very secure, performant alternative to in-house computing, no doubt about it.

This, however, can introduce new problems.

### **Attacking You via Anti-Virus in the Cloud**

At Blackhat this year, two researchers from SafeBreak Labs (Itzik Kotler and Amit Klein) successfully demonstrated an attack that uses Cloud anti-virus to exfiltrate data. Essentially, the attack exploits sample collection practices to send a payload from the attacked system to the Cloud AV Sandbox from which the payload can then send captured data.

In this case, the target system may be hardened and only allow very specific, known, predictable communication channels. One of these channels is the Cloud AV Sandbox channel.

The payload is a program that is installed and injected with data for exfiltration on the target. The payload then triggers an event on that target system, triggering a transfer of that payload to a cloud AV sandbox system. This sandbox is heavily instrumented to closely monitor malware activity for later forensics, but frequently will allow very specific communication through to the internet (e.g. things like DNS lookups or queries to known endpoints for additional payload collection).

Once the payload hits the sandbox, it's executed. The payload then transmits the previously captured data via a variety of possible mechanisms (the authors used HTTP/HTTPS and DNS).

This is a new extension of the system attack surface via a supply chain. The supply chain, in this case, is the AV provider and that provider's cloud computing infrastructure. Another lesson in being aware of your real attack surface, and that you need to clearly understand your supply chain. Especially if that supply chain is automated.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.

Opinions expressed by DZone contributors are their own.
