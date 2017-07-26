# Solving The Persistent Security Threats For The Internet Of Things

_Captured: 2015-11-28 at 20:19 from [techcrunch.com](http://techcrunch.com/2015/11/28/solving-the-persistent-security-threats-for-the-internet-of-things/?ncid=rss)_

![](https://tctechcrunch2011.files.wordpress.com/2015/11/23390123_b6caaefc16_b.jpg?w=738)

Ben Dickson is a software engineer and freelance writer. He writes regularly on business, technology and politics.

[How to join the network](http://techcrunch.com/tc-network-submission-guidelines/)

The rapid expansion of the Internet of Things (IoT) and the security issues created in its wake have quickly captured the attention of [governmental and regional bodies](http://www.scmagazineuk.com/enisa-puts-smart-devices-and-iot-on-top-of-european-security-agenda/article/450047/) and consumers.

According to a [survey by Auth0](https://auth0.com/blog/2015/11/06/surprised-turns-out-consumers-dont-trust-iot-security/), more than 50 percent of consumers and 90 percent of developers are skeptical about IoT security.

The security problem -- and, just as important, the security risks that consumers perceive in internet-connected devices -- represents a real threat to the [hundreds of millions of dollars ](http://tech.co/trends-iot-investing-2015-2015-09)companies are pouring into connected devices of all stripes.

And with the technology still in its infancy, defining a finite framework for its security is a challenging task.

"The Internet of Things is a complex idea and organism, constantly evolving to both its own needs and the needs of consumers. As such, to provide hard and fast security rules would be similar to knowing the workings of a biological creature," wrote Jen Martinson, editor-in-chief of [Secure Thoughts.](http://securethoughts.com/)

Taking lessons from past experiences, the tech community is scrambling to plug the leaks before the situation spins out of control, and many startups and established companies in the tech industry are using this window of opportunity to mitigate the threats and decide the fate of this [fast-growing](http://www.intel.com/content/www/us/en/internet-of-things/infographics/guide-to-iot.html) [phenomenon](https://www.abiresearch.com/press/the-internet-of-things-will-drive-wireless-connect/).

From solutions for connectivity threats to data protection and the quarantine of potentially compromised devices, startups and tech giants are developing solutions for the problem [areas in IoT security](https://bendeetech.wordpress.com/2015/11/04/5-domains-where-iot-security-needs-to-be-addressed/).

**Dealing with network connectivity threats**

![security](https://tctechcrunch2011.files.wordpress.com/2014/12/security.jpg?w=680&h=455)

The always-connected nature of IoT devices makes them especially vulnerable to breaches from outside attackers or from compromised devices sharing the same network.

Surveys show that there's a general negligence when it comes to securing communications protocols and many IoT devices are [still suffering from the famous HeartBleed vulnerability](https://grahamcluley.com/2015/09/heartbleed-200000-vulnerable-devices-internet/?utm_source=Cluley&utm_campaign=a22a46e1d1-Graham_Cluley&utm_medium=email&utm_term=0_8106850f4a-a22a46e1d1-55416989) -- which could allow hackers to stage man-in-the-middle attacks and steal sensitive information such as passwords.

Since engineers who build IoT devices aren't necessarily network security experts, it's only natural that they leave security gaps behind.

Patrick Foxhoven, CTO of Emerging Technologies at [ZScaler](https://www.zscaler.com/), explains, "More often than not, IoT devices are developed by companies with a different mindset - they think about user experience before security or compliance. These devices increase the attack surface of a network, and IT needs to put a plan in place to secure them."

The results from the [Auth0 survey](https://auth0.com/blog/2015/11/06/surprised-turns-out-consumers-dont-trust-iot-security/) indicate that many developers ship their products while feeling pressured to rush an application to the market. Under such circumstances, they normally overlook security concerns and stick to being feature complete on their products.

Therefore if there was some way to abstract and outsource IoT device connection into readymade packages, a lot of the security issues that are being faced by this fledgling technology could be overcome.

This is the idea behind [GENBAND's](http://www.genband.com/) new product, [Kandy](https://www.kandy.io/) Communications Platform-as-a-Service (CPaaS).

According to Paul Pluschkell, who runs the project, Kandy "provides multiple layers of security that are important to IoT applications." As Pluschkell explains, Kandy uses a combination of secure protocols and encryption technologies, including HTTPS and Secure Real-Time Protocol (SRTP), to provide data privacy, end-to-end encryption, and advance authentication mechanisms in order to ensure device integrity.

GENBAND offers its Kandy platform through simple and flexible APIs and wrappers, which allows systems to communicate without compromising or accessing each other's underlying data and structure.

**On-device data protection**

![security-breach](https://tctechcrunch2011.files.wordpress.com/2014/11/security-breach.png?w=680&h=383)

Physical and on-board security is something that is generally neglected in respect with IoT devices. This can become the source of serious security headaches given that a wide range of these devices are often left unguarded in the open and attackers can gain direct access to data stored on devices.

But sensitivity varies for different devices. "A lot of innovation and development comes down to context," says Martinson "Weather data doesn't need to be protected, but someone's GPS coordinates should be." And device data context changes over time. "When our toasters eventually adapt to take biometric readings for optimal toasting efficiency," she says, "security measures will form to protect that information."

The most obvious solution to on-device protection is the encryption of data, an approach that is being endorsed by more and more vendors, including [Apple](https://nakedsecurity.sophos.com/2015/10/21/apple-tells-judge-its-impossible-to-unlock-a-device-running-ios-8-or-higher/) and [Microsoft](http://www.pcworld.com/article/2986346/internet-of-things/microsofts-enterprise-grade-security-is-coming-to-windows-10-iot.html), which are implementing default disk encryption on their new mobile operating systems.

Smaller vendors are also grasping on the idea of on-device encryption and including it as an out-of-box feature of their products. [Sports Performance Tracking](https://www.sportsperformancetracking.com/), a manufacturer of GPS performance trackers for contact sports, employs heavy encryption on all data kept on its devices.

Other companies such as Finnish VPN company [Tosibox](http://www.tosibox.com/) are providing versatile encryption solutions that add an encrypted control layer to remote data access mechanisms in order to improve file access security on devices that are lacking such features.

**Device isolation**

![identity-security](https://tctechcrunch2011.files.wordpress.com/2015/10/identity-security.png?w=680&h=383)

Without isolation, IoT devices allow attackers to move laterally across a network after they gain an entry point. This way, hackers infiltrate one device and start probing the entire system until they find the real prize, e.g. a database or repository that contains sensitive customer or business data.

"If one 'thing' is attacked," says Foxhoven, "it can bring down the network and compromise the business."

This issue is being tackled by companies like [Luma](https://getluma.com/about/), a WiFi home router shipped earlier this month by a tech startup with the same name. Aside from being a normal WiFi router, Luma is equipped with an Intrusion Detection System (IDS) that monitors traffic in your home IoT networks and looks for signs of infection or communications with a command-and-control (C&C) server. This can help in identifying and isolating compromised devices before they become conduits to breach other devices.

Describing Luma, Paul Judge, who cofounded the company, [says](http://www.darkreading.com/endpoint/startup-builds-secure-router-for-iot-laden-home-wifi-/d/d-id/1323019), "We look at outbound traffic and do vulnerability scanning of all devices on the network: is the connected fridge talking to your cameras? The [networked] doorknob to your new light bulbs?"

F-Secure is taking a different approach by introducing the [Sense security monitor](https://sense.f-secure.com/), a device that sits between the home router and connected devices and scans all incoming and outgoing traffic for abnormal behavioral patterns, malware and phishing attacks.

[According to Samu Konttinen](http://www.scmagazineuk.com/slush-helsinki-iot-security-on-the-rise-physical-security-becoming-more-prevalent/article/453164/), the company's executive vice president, both the device and its cloud infrastructure "are not hackable." F-Secure hopes that with Sense, consumers will never have to buy another security solution again, a goal the company wishes to achieve with the backing of 27 years of experience in the security industry.

F-Secure has many other IoT security items on its agenda is an idea called "device reputation," a system that is supposed to scan all devices within a network and give owners indication of where they are lacking in security.

**What else needs to be done?**

![security-insight](https://tctechcrunch2011.files.wordpress.com/2014/10/security-insight.png?w=680&h=383)

> _Great strides have been taken, but we're still very far from saying that we have the IoT security dilemma under control._

For one thing, updating mechanisms on IoT devices have become a sort of Rubik's cube problem. Too many IoT device vendors have intentionally forgone including a means to patch and update their firmware, fearing that doing so will open up security holes to be exploited by hackers.

Others that do bake updating interfaces and features into their devices fail in implementing a secure delivery mechanism, effectively leaving openings for hackers to install and execute arbitrary code on IoT devices. Combined with poor network security, this kind of vulnerability can lead to remote hijacking of connected devices.

Another complicated issue is the huge amount of data being collected by manufacturers and stored on cloud servers. These servers are very attractive targets for hackers, and failure to secure these repositories can lead to the theft of company secrets and consumer information.

Martinson suggests user-end encryption, a method that is fast becoming popular as big data storages are increasingly being attacked by large-scale hacks. This way, even if the data vault is breached, the user data will remain safe and unusable. "The best way to not worry about cloud security breaches," Martinson says, "is to make a server breach irrelevant." But since vendors are one of the main beneficiaries of cloud-stored data, and they use the data for ad and sales-improvement purposes, whether they will actually opt for such a procedure remains in a "cloud" of doubt.

**What the future of IoT withholds**

At the [chaotic pace that it is growing](http://www.informationweek.com/mobile/mobile-devices/gartner-21-billion-iot-devices-to-invade-by-2020/d/d-id/1323081), the IoT industry will surely reveal great many surprises in the future months and years. The combined efforts and determination of the tech community can help us to enjoy the good surprises and avoid the bad ones.

Featured Image: [Kris Krug](https://www.flickr.com/photos/kk/)/[Flickr](https://www.flickr.com/) UNDER A [CC BY-SA 2.0](http://creativecommons.org/licenses/by-sa/2.0/) LICENSE
