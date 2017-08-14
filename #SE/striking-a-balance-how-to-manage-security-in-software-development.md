# Striking a Balance: How to Manage Security in Software Development

_Captured: 2017-08-03 at 18:06 from [dzone.com](https://dzone.com/articles/striking-a-balance-how-to-manage-security-in-code?oid=twitter&utm_content=buffera590b&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Discover an in-depth knowledge about the different kinds of [iOS hacking tools](https://dzone.com/go?i=222228&u=https%3A%2F%2Fweb.securityinnovation.com%2Fhacking-ios-applications-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dhacking-ios-applications) and techniques with the [free](https://dzone.com/go?i=222228&u=https%3A%2F%2Fweb.securityinnovation.com%2Fhacking-ios-applications-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dhacking-ios-applications) iOS Hacking Guide from Security Innovation.

Look, software development is hard.

Developers don't get enough credit for that. Too many people who oversee or otherwise manage or fund development efforts don't usually spend any time really thinking about how difficult it really is and how amazing the things we can do with computers are.

It's difficult enough to develop software that does what it's supposed to do. Getting the needed functionality, appearance, and performance into a quality app of any scale is tough. Making the system secure is even harder.

I spent many years as a software engineer, prior to my cybersecurity career. And I still develop software, it just does different things. Believe me, I get it. I know it's a tough job. That's why I've been working as a security advisor on a few projects over the last few years. This way, the development team can work on developing software, while I deal with ensuring the software we develop is appropriately secure. While doing this, I've learned a few things about how you need to balance more traditional requirements with security needs within a development process.

**Look to Risk. **First and foremost, you need to use actual risk as your guiding principle when determining where to spend your time. You're not going to develop perfectly secure software, just as you're not going to develop bug-free software (after all, they're pretty much synonymous). But you don't want to deliver insecure software, just as you don't want to deliver buggy code. So where to draw the line?

Try to understand where your real risk lies. You'll find security flaws, but can they be exploited, are they accessible from your attack surface (if not, they should be a low priority)? Frequently, when fuzzing software, I'll find a fair number of flaws that crash a program. But most of those are not exploitable. Does that mean you, as a developer, should ignore these kinds of flaws? Of course not. But it does mean that they should be a much lower priority than something that's exploitable. You should certainly fix these kinds of problems, as you never know when you might make them visible via some new feature, but they are not immediately exploitable and should be treated as such.

Just as there's risk to shipping with any flaw, there's risk to not shipping at all. You need to take a holistic approach to project risk and include security as another aspect of that risk calculation.

**Adversarial Mindset, but with more resources.** You should adopt an adversarial mindset when examining your team's code. You should look to the system in the same way an attacker would, and you should try to find flaws accordingly. But keep in mind - you have more resources. Don't spend tons of time fuzzing when you have access to the code base. You don't need to.

If you're working as a development team member, you won't be able to focus all your time on security review either. I find it's best if you separate the two perspectives - look over the code as an attacker would for a security review, and then as a developer would when looking to style, format, and function.

This is also a perfect time to try new tools against your app. As always, automate as much as possible. If you find a tool that really works for you on your project from a security review perspective, try to automate its use as much as possible. These kinds of tools are no silver bullet, but they can help with some of the more obvious issues. Most bugs are more involved today than they used to be, but a simple problem that a tool (like, say, a static analyzer) points out can very well be the beginning of a larger, exploitable problem.

**Where to look.** There are two places where you'll find most of your problems. Areas with high complexity, or areas with low use. Bugs are always associated with highly complex code - run an analyzer that measures cyclomatic complexity over your code base to find the areas of highest complexity and start there.

Likewise, areas in your app that are rarely used will not have been exercised under as many different conditions as more popular functions. This is a surprisingly frequent problem. Old subsystems that are rarely used are gold mines for exploitable issues in operating systems. The same type of thing happens in apps too.

You don't have endless time to review your app. Focus your time on the most impactful areas, as efficiently as possible to maximize your security ROI.

Learn about the importance of a strong culture of cybersecurity, and [examine](https://dzone.com/go?i=232227&u=https%3A%2F%2Fweb.securityinnovation.com%2Fbuilding-a-culture-of-cybersecurity-adv%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dbuilding-a-culture-of-cybersecurity) key activities for building - or improving - that culture within your organization.

### Like This Article? Read More From DZone

Opinions expressed by DZone contributors are their own.
