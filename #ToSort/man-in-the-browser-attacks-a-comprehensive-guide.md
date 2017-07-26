# Man in The Browser Attacks: A Comprehensive Guide

_Captured: 2017-03-08 at 01:06 from [dzone.com](https://dzone.com/articles/man-in-the-browser-attacks-a-comprehensive-guide?edition=276883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-07)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

![man-in-the-browser-attacks](https://blog.jscrambler.com/content/images/2017/02/mitm_guide.png)

With a rapidly growing user base on the Internet, potential attackers have been coming up with new, innovative and complex ways to serve their malicious purposes. One such attack, which has gained widespread notoriety in recent times, is the Man in the Browser (MitB).

Conceptually, the MitB involves an attacker either secretly tapping into a browser to gather data, modify websites and/or manipulate requests, without the knowledge of the user.

## How Does it Work?

A MitB attack starts with a trojan affecting the OS or software. It may just be invisible to an antivirus software, and silently logs the activities of the user, with the potential of manipulating it. The most frequent modus-operandi is email phishing.

When a user downloads and executes an infected file (say, from an email attachment), it typically hooks itself to a system library called `wininet.dll`, which is used by major browsers to connect to the internet - effectively taking over all information flow to and from a browser. The malware can take full control over the user's actions -- it can detect anything a user types, read information that is displayed on the screen and modify any response originating from the browser.

You may wonder if technology such as encryption keeps you safe from MitB attacks. Encryption is designed to protect you if someone intercepts your information. In a MitB attack, the malware has access to data that has already been decrypted at your browser, thereby making encryption ineffective against such attacks. Since the attack takes place locally, other security measures like firewalls are equally ineffective in detecting such attacks.

From the point of view of a server, a MitB attack can not be detected. This happens because all the activities that are a part of this attack originate at the user's end and, thus, it is very difficult, if not impossible, for the server to differentiate any such activity.

What makes MitB so dangerous is that the process is automated with minimal, and sometimes no, human intervention. There is no upper limit on the devices that can be affected by such malware at a time since each infection uses the local resources, and the infection spreads exponentially.

## What Can a MitB Attack Potentially Affect?

With the control of detecting inputs, reading the screen, and manipulating requests, there are no limits to the consequences of MitB, although two specific use cases are discussed here.

The easiest target of a MitB attack is social engineering. It can gather a user's data (including login data) by analyzing their actions for a period of time, and use that data to impersonate the user. With user information, an attacker can obtain credit, a practice commonly known as identity theft. MitB attacks may also be orchestrated for the data leakage of sensitive, classified data.

Yet another malicious task that a MitB attack may be used for is to steal funds. The malware remains inactive when a user logs into an account using two or three-factor authentication. Thereafter, the malware redirects funds by manipulating the details of the transaction and modifying any message to fool the user into believing that the transaction was successful, thereby leading to significant financial losses.

As MitB attacks are so difficult to detect, businesses must be aware of the potential losses these attacks can cause to their systems. Financial institutions, specifically, are at high risk as they form some of the biggest bounties for potential attackers.

## How You Can Detect MitB Attacks

Although this post has continuously mentioned that detecting MitB attacks is very difficult, it must be reiterated that it is not quite impossible. There are a few emerging methods and tools to detect potential attacks and take steps to avoid transactions initiated on compromised end-user devices. The techniques that battle MitB attacks may be divided into two -- client side and server side.

As a business, one may employ many server side measures to prevent MitB attacks. A few popular methods are discussed in this post.

This process involves an extra step in the verification process by involving a separate device that is owned by the user. However, this step can also be bypassed by malware, if it has access to your phone as well, or the contact details are stored online in a platform that is accessible by the malware. The malware can also wait for the user to authenticate the transaction on the infected device, but it can be avoided by clearly mentioning the details of the transaction in the secondary device to alert the user of suspicious activity. With that said, there are difficulties in getting the transaction information on a small message and users may ignore such information to read only the verification code. Using biometrics (fingerprint or a retina scan) to verify a transaction may also be used. Although theoretically, it is possible to avoid MitB attacks through this mode, it is generally accepted that MitB bypasses this.

Behavior analysis is a process where unusual account activity is detected based on the past activity of the users. Financial institutions may use this technique to determine if a transaction under consideration fits a user profile, and accordingly validate the transaction.

On the client side, users can take extra precautions by only using browsers with stringent security measures. Browsers may come with blacklisted extensions and add-ons, which are blocked in routine security checks by the browser on startup. A good browser also performs integrity checks on any extensions that are installed to make sure malicious code is not run on the browser. Using an anti-malware software may prevent attacks, but only if they are present in the database of this software. As a part of their code, developers may also include checks to detect client side behavior of known infections.

All the measures that have been described so far require continuous monitoring and can be bypassed by attackers with relative ease. Jscrambler now offers an agentless and cross-platform solution that tackles fraud in your website, which can make your application secure by preventing tampering of the DOM and removal of known threats on the client side. Further, security to your application is provided by easy and effective monitoring through real-time updates, which enables you to tackle an issue as soon as it develops. If something suspicious is spotted, the application backend is immediately notified, allowing near real-time reaction from the application to the possible fraud attempt.

[Web Integrity Module](https://jscrambler.com/webpageintegrity) emerged as a solution that is completely plug-and-play, i.e. does not require installing anything locally. In fact, the end-user doesn't have to cooperate with anything. It's completely transparent to the client device and supports all browsers and platforms. Also, contrary to anti-virus solutions, it does not look for malware signatures, but for changes made to the untampered page, and by doing so, it is able to detect 0-day threats.

## Final Thoughts

Attackers are working round the clock on improving existing threats to find new ways of gaining access to malicious data, and traditional ways of tackling them are turning out to be insufficient, although still necessary. It is, therefore, the duty of companies to keep up with the latest threats that they may face by adopting the latest technology and securing their systems.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
