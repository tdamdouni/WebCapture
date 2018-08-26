# Dear Open Source Developers, Please Protect Your Users

_Captured: 2018-03-11 at 18:39 from [dzone.com](https://dzone.com/articles/dear-open-source-developers-please-protect-your-us?edition=365237&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-11)_

The Nexus Suite is uniquely architected for a DevOps native world and creates value early in the development pipeline, provides precise contextual controls at every phase, and accelerates DevOps innovation with automation you can trust. [Read how in this ebook](https://dzone.com/go?i=222229&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

For the second time in as many weeks, we're seeing the fallout of missteps taken by publishers of open source components. It was just last week that I [wrote](https://blog.sonatype.com/hijacking-of-a-known-github-id-go-bindata) about the GitHub ID of go-bindata being highjacked. We don't know for certain if the intentions were malicious but the risk was obvious.

Today we are finding that credentials were compromised for an npm component called conventional-changelog and a [malicious version was uploaded](https://github.com/conventional-changelog/conventional-changelog/issues/282#issuecomment-365367804) that allegedly included a Monero cyptocurrency miner. Anyone who built or installed an npm package depending on the malicious package yesterday is now potentially running a miner and worse, potentially distributing it to their downstream users or customers.

A few months ago, people were laughing at a [parody of a similar situation](https://hackernoon.com/im-harvesting-credit-card-numbers-and-passwords-from-your-site-here-s-how-9a8cb347c5b5) describing credit card harvesting via a compromised package. It's not so funny anymore, is it?

Open source developers typically thrive in creating something used by millions or billions of other people. This is the fuel that drives us and knowing that you've contributed, even in some small part, to the lives of millions of users is amazing.

Conversely, knowing that you've accidentally inflicted harm on those users through careless practices is probably devastating… yet seemingly not enough people are thinking about this beforehand, while it's preventable.

We open source developers and package maintainers are finding ourselves at the front line of the new battle. Attackers have recognized the power of open source in terms of broad distribution and are seeking to use that against us.

**We must not let them ruin the reputation of the things we've built.** Or worse, the entire open source ecosystem.

If you're an open source contributor or package maintainer: Pay attention to your own digital security as you would if you were protecting millions of others. _Because you are._

The DevOps Zone is brought to you in partnership with Sonatype Nexus. See how the Nexus platform infuses precise open source component intelligence into the DevOps pipeline early, everywhere, and at scale. [Read how in this ebook](https://dzone.com/go?i=222230&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

Opinions expressed by DZone contributors are their own.
