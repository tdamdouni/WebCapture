# PSA: This spoof Apple site illustrates the sophistication of today’s phishing attacks

_Captured: 2017-04-20 at 16:50 from [9to5mac.com](https://9to5mac.com/2017/04/20/how-to-spot-a-phishing-attempt-fake-apple-site/)_

![](https://9to5mac.files.wordpress.com/2017/04/phishing.jpg?quality=82&strip=all&strip=all&w=320&h=1000)

Most phishing attacks - links that send you to a fake website in the hope that you'll login with your real credentials - are usually easy to detect. Emails are often generic, rather than using your registered name. Grammar is poor or the wording is weird. The email will threaten closure of your account if you don't take urgent action, and so on.

If you did miss all these clues and click on the link, the URL would show that it's not really the site that it claims to be. But one demonstration site created by a Chinese security researcher shows how it's possible to visit a fake website that seemingly shows the correct <https://www.apple.com> URL in a browser window …

The trick employed by the site is to use Unicode characters that look the same as the appropriate ASCII characters for the site impersonated, explains researcher [Xudong Zheng](https://www.xudongz.com/blog/2017/idn-phishing/).

> It is possible to register domains such as "xn--pple-43d.com", which is equivalent to "аpple.com". It may not be obvious at first glance, but "аpple.com" uses the Cyrillic "а" (U+0430) rather than the ASCII "a" (U+0061). This is known as a homograph attack.

Safari isn't fooled by this, but Chrome, Firefox and Opera all are. You can see this for yourself by using any of them to visit <https://www.xn--80ak6aa92e.com> (this is perfectly safe, it's a site created by Zheng as a proof of concept). In Safari, you'll see this URL as it appears here - but in the other browsers it will look _exactly_ like https://www.apple.com.

Of course, to take full advantage of the exploit a phisher would have to make the email directing you there look as convincing as the site, but many people are fooled by even halfway-convincing emails.

The trick strengthens the usual advice: always visit websites from your own bookmarks or by typing the URL, never from a link in an unexpected email, even if it appears to be from someone you know. You can find [more tips here](https://9to5mac.com/2016/10/04/apple-phishing-emails/).

Phishing was [one of two methods](https://9to5mac.com/2014/09/03/opinion-after-the-celebrity-hacks-the-vulnerability-that-still-exists-and-what-needs-to-be-done/) used to obtain the iCloud logins used in the [celebrity nudes](https://9to5mac.com/guides/celebrity-hack/) attack back in 2014.

_Thanks, Fifi._
