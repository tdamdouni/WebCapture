# Global Ransomware Strikes Again

_Captured: 2017-07-05 at 21:45 from [dzone.com](https://dzone.com/articles/global-ransomware-strikes-again?edition=306229&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-05)_

Address your unique [security needs at every stage](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre) of the software development life cycle. Brought to you in partnership with [Synopsys](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre).

In May, a ransomware called [WannaCry](https://auth0.com/blog/a-massive-ransomware-attack-targets-organizations-around-the-globe/) became famous around the world for holding computers' file systems as hostages. Last week, government institutions (like [Ukraine's national bank](http://www.independent.co.uk/news/world/americas/petya-cyber-attack-us-pharma-merck-ukraine-ransomware-national-bank-power-wpp-ad-agency-wannacry-nhs-a7810906.html)) and companies from the private sector reported that another outbreak has started.

The ransomware responsible for haunting these organizations is called Petya, although this name originates from a [ransomware that attacked last year](https://blog.kaspersky.com/petya-ransomware/11715/). Similar to WannyCry, Petya ransomware starts by encrypting a computer's file systems and then it demands payment to restore access to these files.

## What Is Ransomware?

The very definition of ransomware is a malware that blocks access to the victim's data until a ransom is paid. There are some examples ransomware that lock the systems in a way that is not difficult to reverse, but the more advanced ones are using a technique called [cryptoviral extortion](https://en.wikipedia.org/wiki/Cryptoviral_extortion). This technique consists of encrypting victims' files, thus making them inaccessible. To regain access, the authors demand a ransom payment in exchange for reversing the encryption. Nowadays, most ransomware attackers are requesting [Bitcoins](https://bitcoin.org/) as payment, to [take advantage of cryptocurrency's anonymity](https://bitcoinmagazine.com/articles/is-bitcoin-anonymous-a-complete-beginner-s-guide-1447875283/).

## What Is Petya Ransomware?

The real name of the ransomware that is striking today has not been defined. But, as this ransomware is supposed to be a variant of [Petya](https://blog.kaspersky.com/petya-ransomware/11715/), the name is being reused. Petya locks a computer's hard drive as well as individual files stored on it. It's not easy to recover data from the computers affected by this malware.

One interesting fact is that cyber security experts at Kaspersky Lab have released a report that said the ransomware was not related to Petya but was, in fact, a new ransomware it called [NotPetya](https://www.forbes.com/sites/thomasbrewster/2017/06/27/petya-notpetya-ransomware-is-more-powerful-than-wannacry/#16c86cff532e). The contradictions have not yet been clarified.

![NotPetya/Petya screenshot](https://cdn.auth0.com/blog/petya-ransomware/notpetya.png)

## How Petya Started

[A Ukrainian software firm is alleged to be the source of the recent outbreak](https://www.forbes.com/sites/thomasbrewster/2017/06/27/medoc-firm-blamed-for-ransomware-outbreak/#20ca49ae73c8). Although there is no confirmation of this, and the company has denied these claims in a [Facebook post](https://www.facebook.com/medoc.ua/posts/1904044929883085), the outbreak is indeed striking Ukraine harder than any other country.

![Petya/NotPetya attacks by country](https://cdn.auth0.com/blog/petya-ransomware/by-country.png)

## How the Petya Ransomware Spreads

Researchers are saying that this new outbreak is hitting systems via the same leaked NSA vulnerabilities used by [WannaCry](https://auth0.com/blog/a-massive-ransomware-attack-targets-organizations-around-the-globe/). The analysis of some of Petya's samples confirmed that the malware author used the [EternalBlue exploits](https://en.wikipedia.org/wiki/EternalBlue), which targeted a vulnerability in Microsoft Windows. [Microsoft already created patches to solve the EternalBlue vulnerability](https://www.theverge.com/2017/4/15/15311846/microsoft-windows-shadow-brokers-nsa-hacks-patched), but many computers out there don't have this patch applied.

## How Do I Protect Myself?

Although no solutions were found for retrieving data from computers affected by Petya so far, you can review and [update your devices](https://www.theverge.com/2017/4/15/15311846/microsoft-windows-shadow-brokers-nsa-hacks-patched) and also check that your approach to security is good.

Find out how [Synopsys](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3Ddzone-sig-post) can help you build security and quality into your SDLC and supply chain. We offer [application testing and remediation expertise](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsecurity-testing.html%3Fcmp%3Ddzone-sig-post), guidance for [structuring a software security initiative](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-strategy.html%3Fcmp%3Ddzone-sig-post), training, and [professional services](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-services.html%3Fcmp%3Ddzone-sig-post) for a proactive approach to application security.
