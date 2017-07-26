# Why Is it so Hard to Arrest Hackers?

_Captured: 2017-03-24 at 19:42 from [dzone.com](https://dzone.com/articles/arresting-hackers-why-so-hard?edition=286910&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-24)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

So recently I was chatting with an acquaintance of mine, and he asked me about recent hacking allegations and why we never see anybody arrested for cyber crime.

Well, first, we do see arrests, though they're not usually widely publicized in mass media, and we don't see enough of them. But people do get caught.

But really, why so few? Well, honestly, because it's really hard to prove that cyber crimes are committed by specific individuals, despite all the allegations you'll see in the press, especially recently. And I mean prove - with evidence that will hold in a justice system.

There are a few reasons for this. First, it's really hard to track careful criminals down. Second, even if you have malware samples, it's pretty easy for attackers to have sanitized them. And it's easy to plant false flags if you're savvy. Finally, finding the appropriate evidence is difficult as well, not in the least because of jurisdictional problems.

Tracking determined cyberattackers down is hard, and it takes time. Many attackers use stolen infrastructure, and they will frequently camouflage access through yet other compromised systems in difficult to access countries. This leaves a trail of systems that needs to be traversed in order to find the originating system. And these trails will change frequently, or involve Tor.

Malware samples usually don't have much in them of value, unless you've been able to acquire the cyberattacker's workstation. Actually compiled payload code, or macros in MS Word documents, can be effectively sterilized, so it contains no identifying traces. Now, it's difficult to remove all stylistic traces, so it's best to use industry standard conventions in your code, not things that can be used for later sample correlation if you're an attacker. But even when engineers do use odd tricks, that really only gives analysts a way to show that selected payloads come from the same author, not that a specific author is a specific person.

False flags are easy to plant in malware as well. When do command and control systems operate? When are manual intrusions attempted? What kinds of variable names are used, and what kinds of characters? Are there characters from a specific alphabet? These kinds of tricks can all be used to lead analysts to the true authors, but it can be forged too.

Extracting evidence from computer systems is a well defined and refined field. But you need to get your hands on the system first, and the system needs to have something compelling to link malware or command and control to that particular system. Both of these can be difficult problems, especially when dealing with criminals in other countries, or countries that don't have particularly strong relationships with the one you're in if you're an analyst.

Really, like many cases in the outside world, criminals are eventually caught because they are careless. They provide a trail from cybercrime forums to domain names, then to identifying information, for example. Or they brag about a campaign. It just takes time - though sometimes it seems like too much.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.

Opinions expressed by DZone contributors are their own.
