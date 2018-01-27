# 40 Tips You Must Know About Secure iOS App Development

_Captured: 2015-11-13 at 23:59 from [www.checkmarx.com](https://www.checkmarx.com/2015/11/10/40-tips-you-must-know-about-secure-ios-app-development/)_

**The iPhone is arguably the most desired smartphone on the planet today, thanks to its shiny metallic hardware and user-friendly iOS 9 mobile platform. Despite Google leading the numbers-game with its open-source Android mobile platform, iOS is often considered to be the safer of the two due to Apple's stricter security policy and its willingness to sacrifice customizability for the cause. But even this platform has its fair share of vulnerabilities and potential security loopholes that need to be addressed by the developers.**

The following developer's guide is loosely based on the [OWASP Mobile Top-10](https://www.owasp.org/index.php/OWASP_Mobile_Security_Project), considered by many InfoSec experts to be the most comprehensive mobile vulnerability list out there today. Secure iOS app development is no longer an option and must be taken seriously. These 40 development pointers will help you create robust iOS apps with minimal flaws.

### M1 - Insecure Data Storage

**_The Risk - _**This is considered the biggest risk that that iPhone and other mobile phone users face after losing their devices or when they get stolen. Apple offers a good choice of security mechanisms to protect sensitive data. But to provide more comprehensive protection, developers should build security right into the iOS applications.

**_The Fix - _**The iron rule all developers must follow is simple - data should be stored locally only when it's needed by the application to work properly. This means that:

1 - Data in plain text should not be stored in the application's sandbox.  
2 - Sensitive credentials can be stored securely in the device's Keychain.  
3 - Apple's _File Protection Mechanism_ can protect consumer-grade data.  
4 - NSUserDefaults should not be used to store sensitive data and it should be noted that NSManagedObects are stored in an unencrypted DB file - plan accordingly.

### M2 - Weak Server Side Controls

**_The Risk_** - Hackers are constantly looking to exploit weaknesses in the application to gain access to the server side, where large amounts of sensitive data are stored.

**_The Fix_** - In a nutshell, iOS developers should make sure that user input is properly checked, filtered and regulated. This can be achieved by adopting coding habits that include:

5 - Input validation must be built in to detect/block unauthorized malicious access.  
6 - Canonicalization can be used to simplify data input and optimize processing.  
7 - Whitelisting is also a common way to neutralize illegal user input.  
8 - Encoding the output also helps prevent XSS and format string attacks.

### M3 - Insufficient Transport Layer Protection

**_The Risk_** - Most modern mobile applications are networked, regardless of the platform (OS) they are working on. Sensitive data is often exposed to eavesdropping attacks.

**_The Fix_** - Secure iOS app development should involve the following practices to enhance transport layer protection. A few key steps that should be taken during development are:

9 - Authentication/session tokens and app data should be SSL/TLS encrypted.  
10 - The application should accept only properly validated SSL certificates. This can be done by using the setAllowsAnyHTTPSCertificate parameter.  
11 - Use the CFNetwork API that uses NSStreamSocketSecurityLevelSSLv3/TLSv1.2.  
12 - Always assume the application will be used in public unsafe WiFi networks.

### M4 - Client Side Injection

**_The Risk_** - These attacks are well known and documented in web apps, but more and more injection attacks are being executed today against vulnerable mobile apps.

**_The Fix_** - The following steps should be taken to deal with injection based attacks:

13 - Parameterized queries should be used as much as possible.  
14 - Injection vulnerable functions such as _strcat_ and _strcpy_ should be avoided.  
15 - Extra validating should be implemented while using URL schemes.  
16 - The local capabilities of the app should be minimized while developing hybrid (web and mobile) apps. This means full control of the UIWebView content/pages should be maintained.

**TrustKit Code Injection on iOS 8. Courtesy: _Network Security_**

### M5 - Poor Authorization and Authentication

**_The Risk_** - These vulnerabilities are exploited by poor server side programming standards. iOS developers are advised to follow the same steps taken with web apps.

**_The Fix_** - Some of the common practices that secure iOS app development should involve include:

17 - Device identifiers should be used as less as possible (UDID, IMEI, etc).  
18 - Avoid sending "out-of-band" authentication tokens to the same device. Many hackers make use of the sending of texts to the same iPhone/iPad.  
19 - All API calls should be authenticated to paid resources (control 8.4).  
20 - Strong server-side authentication, authorization and session management should be implemented at all times (control # 4.1-4.6).

### M6 - Improper Session Handling

**_The Risk_** - Unlike web applications, mobile applications have trouble handling sessions properly. For example, security issues may arise when sessions are left open infinitely.

**_The Fix_** - Every iOS developer should take session handling seriously and made the right decisions from the early stages of development. This involves:

21 - Session identifiers should use a key space of at least XXXX bits and also must utilize the largest character set available to it.  
22 - iOS developers should also randomize all session identifiers to bolster security.  
23 - "_Remember Me_" functionality should not be used in sensitive iOS applications.  
24 - The iOS application should not be able to make automated requests to prevent session timeouts. Session timeouts are important security tools.

### M7 - Security Decisions via Untrusted Inputs

**_The Risk_** - iOS is much safer than the Android mobile platform when it comes to allocating applications channels for communicating between themselves. But some communication channels still exist in Apple's operating system, which require the developers to take the right steps to make sure the iPhone stays safe to use.

**_The Fix_** - iOS developers should take the aforementioned risks into consideration and work accordingly:

25 - Canonicalize and positively validate all input data especially in app boundaries.  
26 - Take extra care before validating and accepting URL schemes.  
27 - Untrusted data output should be contextually escaped to make sure it can't change the actual intent of the output for malicious purposes.  
28 - Prompt the user to allow/disallow access to the requested resource.

### M8 - Side Channel Data Leakage

**_The Risk_** - Modern mobile applications perform all kinds of data exchange processes that enhance performance and improve the user-end experience. Common actions that iOS applications perform include keystroke logging, which is used by keyboard applications for spell checking. There is also web caching for enhancing browser speeds.

**_The Fix_** - All iOS applications should be developed under the assumption that the device can be stolen or lost. Side channel data should be identified.

29 - Identify and enumerate all side channels and third party libraries to be prepared for instances of data leakage and deal with them effectively.  
30 - Disable screenshots along with cut-and-paste buffers.  
31 - iOS developers can also disable keystroke logging from within sensitive apps.  
32 - Dynamically test the application's data stores and communication channels to make sure that no sensitive data is being unknowingly stored or transmitted.

### M9 - Broken Cryptography

**_The Risk_** - Mobile security is often compromised by a wide range of cryptographic weaknesses. These flaws typically are a result of poor key management.

**_The Fix_** - iOS application developers should carefully design and implement the various aspects of the crypto systems. The following steps should be taken to bolster security:

33 - Cryptographic keys should not be "hard coded" or stored.  
34 - Secure containers should be to store cryptographic keys.  
35 - A secure key exchange system should be created, where the key is controlled by a secure server. It should never be saved on the mobile device locally.  
36 - Authentication credentials and session tokens can be stored securely in the device's Keychain. Third party encryption APIs (i.e - SQLcipher) are also recommended to safeguard more general types of data.

### M10 - Sensitive Information Disclosure

**_The Risk_** - The modern iOS application is full of private information inputted by the end-user. If not programmed safely, apps can be reverse-engineered to harvest data.

**_The Fix_** - The solutions to these kinds of risks is simple. iOS developers should simply not let private and sensitive information reside on the mobile device. They should also:

37 - Ensure that the private information is always in the process memory and not stored on the iPhone or the iPad. If necessary this should be done securely.  
38 - Never hard cord passwords or session tokens.  
39 - Trip binaries prior to shipping.  
40 - Make sure no sensitive information is written to the log files. This is because they can be monitored by malicious attackers and commercial hackers.

### Secure iOS App Development with Static Code Analysis (SCA)

These ten aforementioned security issues are only the most commonly exploited ones. There are dozens of coding flaws and vulnerabilities that need to be eliminated before the application is released to the market. Most of them can be mitigated by creating a [secure Software Development Life Cycle (sSDLC)](https://www.checkmarx.com/solutions-2/secure-sdlc/) with integrated [SAST](https://www.owasp.org/index.php/Source_Code_Analysis_Tools) security.

For example, [Static Code Analysis (SCA)](https://www.checkmarx.com/technology/static-code-analysis-sca/) can help automate the security process while developing iOS applications. Developers then don't have to deal with complex solutions that require long installation times and tiring maintenance procedures. The scanner sits as a plugin within the developer IDE, making vulnerability remediation a breeze.

With more and more people taking a bite of the apple and purchasing "iDevices", iOS application developers have to start taking security seriously and produce robust code.

**To read Checkmarx's "The State of Mobile Application Security 2014-2015 Report" - ****[Click Here**](https://www.checkmarx.com/white_papers/the-state-of-mobile-application-security-2014-2015/)
