# Getting Started Writing Secure Code

_Captured: 2017-08-03 at 18:05 from [dzone.com](https://dzone.com/articles/getting-started-writing-secure-code?oid=twitter&utm_content=buffera590b&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Discover an in-depth knowledge about the different kinds of [iOS hacking tools](https://dzone.com/go?i=222228&u=https%3A%2F%2Fweb.securityinnovation.com%2Fhacking-ios-applications-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dhacking-ios-applications) and techniques with the [free](https://dzone.com/go?i=222228&u=https%3A%2F%2Fweb.securityinnovation.com%2Fhacking-ios-applications-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dhacking-ios-applications) iOS Hacking Guide from Security Innovation.

Cybersecurity means different things from different perspectives. A penetration tester thinks about tools, exploits, and attack surfaces. A network engineer thinks about firewalls, proxies, and intrusion detection. System administrators think about anti-virus and application whitelisting.

Software engineers should have a different perspective, too.

When coding, there are things you have control over and things you don't. While you do have control over the code you write, and some control over the code others on your team may write, you don't have control over the code in the libraries you use. That said, you can and should practice due diligence when selecting those libraries. You don't have control over the underlying operating system (in most cases). You do have control over your update process if you use one.

As a team, you have control over things like your application architecture, the use of encryption, certificate management, things like that. As an individual engineer, you may not.

Here, I'm going to focus specifically on what you, as an engineer, can do to create more secure products.

### **Learn Your Language and Runtime**

What language are you using? C? C++? Something else?

Many languages have secure coding standards that various bodies have already published. SEI CERT, for example, has published secure coding standards for C, C++, Java, and Perl. Other languages have similar resources (more esoteric languages won't, but that's part of the territory when you start using niche languages).

All systems have ways you can create insecure software, and these kinds of standards are designed to help you avoid these kinds of problems.

### **Understand Encryption, but Don't Implement Any of It**

Encryption is hard. No, not the encryption itself - that's pretty well documented, and honestly you could implement these algorithms with a bit of time invested. But using encryption techniques to build a secure system is much more difficult.

Heartbleed is an example of this - SSL is secure if implemented correctly. In Heartbleed's case, attackers were able to downgrade the encryption to a known insecure algorithm, allowing for a possible compromise. Was SSL broken? Well, no. Was the system itself broken? Arguably yes. The recommended algorithms were still very strong, but if the system was misconfigured, weaker algorithms would take the place of the stronger ones. Seeing these kinds of edge cases is difficult, and best left to specialists.

### **Keep Things Simple**

The simpler something is, the easier it is to understand, and the easier it is to secure. Try to keep your code as simple and understandable as you can. It'll be easier for you to get right the first time, and easier for you to review later.

### **Know the Common Vulnerabilities**

Every language and runtime have specific, common flaws. There are also more general problems that you can run into. You should familiarize yourself will all of these. For example, in C, buffer management is always a potential problem, as is using non-limited string management functions. You should be aware of things like this so you can avoid them.

Likewise, there's a large number of more general problems you can run into. OWASP maintains a top 10 list of web security issues, updating the list each year. IEEE has released a similar report on the top 10 security design flaws seen in software today. These kinds of resources can really help you avoid potential problems.

If you follow these guidelines, you'll find you'll start developing much more secure code. You'll understand how to write secure code to begin with, know what kinds of flaws to look for in your own code, and you'll have an easier time finding any bugs that sneak in.

Good luck!

Learn about the importance of a strong culture of cybersecurity, and [examine](https://dzone.com/go?i=232227&u=https%3A%2F%2Fweb.securityinnovation.com%2Fbuilding-a-culture-of-cybersecurity-adv%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dbuilding-a-culture-of-cybersecurity) key activities for building - or improving - that culture within your organization.

### Like This Article? Read More From DZone

Opinions expressed by DZone contributors are their own.
