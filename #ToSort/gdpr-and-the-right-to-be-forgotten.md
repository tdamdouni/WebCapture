# GDPR and the Right to Be Forgotten

_Captured: 2018-01-23 at 20:30 from [dzone.com](https://dzone.com/articles/gdpr-and-the-right-to-be-forgotten?edition=357100&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-23)_

### Implementing the GDPR regulation will undoubtedly have its challenges. In this post, we take a look at those challenges and what a potential solution might be.

Discover how to provide [active runtime protection](https://dzone.com/go?i=255346&u=https%3A%2F%2Fwww.waratek.com%2Fruntime-application-self-protection-rasp%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Drasp) for your web applications from [known and unknown vulnerabilities](https://dzone.com/go?i=255346&u=https%3A%2F%2Fwww.waratek.com%2Fruntime-application-self-protection-rasp%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Drasp) including Remote Code Execution Attacks.

![George Bailey on the Bedford Falls bridge](https://www.johndcook.com/georgebailey2.jpg)

The European GDPR (General Data Protection Regulation) was adopted in 2016 and becomes enforceable in May of this year. Article 17 mandates a **right to erasure**, more commonly called the **right to be forgotten**.

A right to be forgotten is tricky. It's not immediately clear what this means or to what extent it's even possible. That's for lawyers and courts to work out. I can't comment on the legal interpretation of the regulation. There are laws that require companies to delete information and laws that require them to retain information, and no doubt there are debates on how to reconcile these.

Here I want to look at some of the logical and statistical issues that come out of privacy laws, not necessarily the GDPR in particular, that mandate that information be forgotten.

## Challenges With a Right to Be Forgotten

Suppose John Smith had participated in some database and a report showed that there were 5,000 diabetics in Smith's geographic region. Smith asks to be removed from the database, and now a revised report shows that there are 4,999 diabetics in the region. What does that tell you about Smith? (For an elaboration on this example, see [Big aggregate queries can still violate privacy](https://www.johndcook.com/blog/2017/11/11/aggregate-queries-and-privacy/).)

You might object that removing Smith from the database doesn't really cause him to be forgotten if we retain the fact that he was removed from the database. We have to forget that he was forgotten, maybe like George Bailey in It's a Wonderful Life. While the fictional George Bailey was able to see what life would have been like if he had never been born, our real-world John Smith doesn't have that option. Truly forgetting anything in a world of ubiquitous databases may not be possible. It may require a cascade of changes that are illegal, impractical, or impossible.

## Differential Privacy

One way to address the challenges of erasure is through **differential privacy**. A report constructed via a differentially private system would not have released the exact number of diabetics in Smith's region but rather some randomized version of the exact result. Ideally, the amount of noise added to the true result is large enough to protect Smith's privacy, but small enough that the result is useful to the person who wants to know the approximate number of diabetics in Smith's region.

Differential privacy is both powerful and subtle. It gives a theoretically grounded way to quantify the privacy implications of someone's participation or lack of participation in a database. But it comes with restrictions that may be hard to live with. For example, we cannot let someone ask the same question many times, or if we do, we must give the same answer each time. If the answers were generated afresh each time, one could average the results to remove the effect of the random noise.

But what if you want to let someone rerun reports, not because they're trying to evade privacy protections, but because the world is changing and they periodically want to get an updated view of the world? That can be done, but it requires forethought. Before you release the first report, you must have a system in place that is intended to allow multiple queries over time.

Differential privacy applies to a process, not to a result. You can't say "This is a differentially private report" but rather "This report is the result of a differentially private mechanism." That mechanism has to be designed up front. You can design a mechanism to support a wide variety of queries, but this comes at a cost. You have to anticipate what these queries will be (maybe not specifically but at least some class that they fall in) and add sufficient randomness to support them all. In general, the more flexible you want your query system to be, the more randomness you will need to add, and so you face a privacy-utility trade-off.

Find out how Waratek's award-winning [application security platform](https://dzone.com/go?i=255347&u=https%3A%2F%2Fwww.waratek.com%2Fapplication-security-platform%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappsecplatform) can improve the security of your [new and legacy applications and platforms](https://dzone.com/go?i=255347&u=https%3A%2F%2Fwww.waratek.com%2Fsolutions%2Flegacy-platforms%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dlegacy) with no false positives, code changes or slowing your application.
