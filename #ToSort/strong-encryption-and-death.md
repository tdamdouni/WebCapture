# Strong Encryption and Death

_Captured: 2017-01-29 at 19:59 from [dzone.com](https://dzone.com/articles/strong-encryption-and-death?edition=265888&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-29)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

I try to use strong encryption wherever I can. While I doubt it will keep my thoughts from prying eyes forever, at least it should make peeking a little harder.

But it dawned on me: what happens when I die? I want to let my business partners see what is on my encrypted desktop and I know my wife will need access to the files on my systems at home. I could share them with her now, but my passphrases are complex and she isn't very familiar with the operating systems I use.

Now I'm not planning on dying any time soon, in fact I want to live until I am at least 95 and a half. Why that age? Because that is when [Halley's Comet](https://en.wikipedia.org/wiki/Halley's_Comet) will return. I saw the comet when I was living in California in 1986 and I could care less about seeing it again, but I do want to be the old guy they interview:

"Back in '86, now that's 1986 for you young folks, I was livin' in Los Angeles. The comet was too dim to see in the city, so we drove out to [Joshua Tree](https://en.wikipedia.org/wiki/Joshua_Tree_National_Park)…"

![Image title](https://www.adventuresinoss.com/wp-content/uploads/sites/2/2017/01/halley.jpg)

So, how do I safely pass on my important passphrases? This is the solution I chose.

I created a file called "deathnote.txt" which I then encrypted using GPG:

This will encrypt the file so that both Bob and Alice can read it (and I can too). I then sent it to several friends unrelated to them with instructions that, upon my death (but not before), please send this file to Bob and Alice. I also remembered to include a copy of my GPG private key:

Just in case they can't find it on my systems.

This does require a certain level of trust in my friends, but I am blessed with having several I can count on. As long as I remember to keep it updated this should provide a secure way to pass on this important information, although I hope no one has to use it any time soon.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
