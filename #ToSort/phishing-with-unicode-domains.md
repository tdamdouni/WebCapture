# Phishing with Unicode Domains

_Captured: 2017-04-20 at 23:15 from [www.xudongz.com](https://www.xudongz.com/blog/2017/idn-phishing/)_

![URL Bar](https://www.xudongz.com/cache/daea1fdcd6a324778f3274a64b6dfc24e6073874067835efefe5e26870baa383.png)

> _Before I explain the details of the vulnerability, you should take a look at the proof-of-concept._

[Punycode](https://goo.gl/sWKaLz) makes it possible to register domains with foreign characters. It works by converting individual domain label to an alternative format using only ASCII characters. For example, the domain "xn--s7y.co" is equivalent to "短.co".

From a security perspective, Unicode domains can be problematic because many Unicode characters are difficult to distinguish from common ASCII characters. It is possible to register domains such as "xn--pple-43d.com", which is equivalent to "аpple.com". It may not be obvious at first glance, but "аpple.com" uses the Cyrillic "а" (U+0430) rather than the ASCII "a" (U+0061). This is known as a [homograph attack](https://goo.gl/l8qDjk).

Fortunately modern browsers have mechanisms in place to limit IDN homograph attacks. The page [IDN in Google Chrome](https://goo.gl/94iEWc) highlights the conditions under which an IDN is displayed in its native Unicode form. Generally speaking, the Unicode form will be hidden if a domain label contains characters from multiple different languages. The "аpple.com" domain as described above will appear in its Punycode form as "xn--pple-43d.com" to limit confusion with the real "apple.com".

The homograph protection mechanism in Chrome, Firefox, and Opera unfortunately fails if every characters is replaced with a similar character from a single foreign language. The domain "аррӏе.com", registered as "xn--80ak6aa92e.com", bypasses the filter by only using Cyrillic characters. You can check this out yourself in the [proof-of-concept](https://www.xn--80ak6aa92e.com/) using Chrome, Firefox, or Opera.

Visually, the two domains are indistinguishable due to the font used by Chrome and Firefox. As a result, it becomes impossible to identify the site as fraudulent without carefully inspecting the site's URL or SSL certificate. [This Go program](https://goo.gl/kFjYJV) nicely demonstrates the difference between the two sets of characters. Safari, along with several less mainstream browsers are fortunately not vulnerable.

Internet Explorer does not display native characters in domains unless it belongs to one of the computer's system languages. As a result, it suffers from the same vulnerability if the system has Russian (and other Cyrillic languages) enabled. Internet Explorer's [documentation](https://goo.gl/0PRdXx) acknowledges that users are "increasing the risk of spoofing attack" when their system supports additional languages.

This bug was [reported to Chrome](https://goo.gl/Q17h3U) and Firefox on January 20, 2017 and was fixed in the Chrome trunk on March 24. The fix is included in Chrome 58 which is currently rolling out to users. The existence of the bug in Opera was brought to my attention only after the initial publication of this post. The problem remains in Firefox as they decided that it is a problem for domain registrars to deal with. You can find the detailed discussion in [the Bugzilla issue](https://goo.gl/eg3wvN).

> Our IDN threat model specifically excludes whole-script homographs, because they can't be detected programmatically and our "TLD whitelist" approach didn't scale in the face of a large number of new TLDs. If you are buying a domain in a registry which does not have proper anti-spoofing protections (like .com), it is sadly the responsibility of domain owners to check for whole-script homographs and register them. 

Firefox users can limit their exposure to this bug by going to `about:config` and setting `network.IDN_show_punycode` to `true`. This will force Firefox to always display IDN domains in its Punycode form, making it possible to identify malicious domains. Thanks to user MARKZILLA from reddit for this temporary solution. Chrome 58+ users and Firefox users who apply this fix will see the Punycode domain rather than "apple.com".

![Firefox Fix](https://www.xudongz.com/cache/a502b06561524ec740ec6e8cb11fbd931f6fb219f42a0be6de275f97d44a514a.png)

A simple way to limit the damage from bugs such as this is to always use a password manager. In general, users must be very careful and pay attention to the URL when entering personal information. Until this is fixed, concerned users should manually type the URL or navigate to sites via a search engine when in doubt. This is a serious vulnerability because it can even fool those who are extremely mindful of phishing.

_ Enjoyed this? Follow me on Twitter [@Xudong_Zheng](https://goo.gl/5ZtdWP) _
