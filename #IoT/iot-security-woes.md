# IoT Security Woes?

_Captured: 2017-03-12 at 00:11 from [dzone.com](https://dzone.com/articles/iot-security-woes-cool-to-talk-about-a-problem-but?edition=281881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-11)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

**Problem solved: AWS IoT + Mongoose OS + crypto chip = IoT Security**

We have all witnessed the media outcry about IoT security breaches and all the possible consequences of them. However, what has not been addressed is how to actually avoid or prevent such breaches.

The general public and the media has a really vague understanding of what goes into IoT security and usually uses words like 'device' and 'cloud.' Start speaking about SSL/TLS, crypto chips, 2 ways MQTT SSL authorization and you will completely lose their attention.

What is the key reason IoT Security is being compromised? It's as simple as this: _vendors are price cautious and time sensitive, wanting to launch their connected products to the markets at the lowest cost possible, all too often overlooking the basic security precautions._

**What you need to know, though, are the key points where a connected device can be compromised:**

  1. On the device itself (when the device is being tampered with) as SSL certificates are not protected and can be easily accessed.

  2. In the way a device communicates with the cloud when the traffic is not encrypted.

  3. On the cloud side, where the unprotected or less well-protected authorization process with the cloud can be compromised. This can occur with cloud providers who do not enforce security requirements on their side.

End price of the product and good P&L costs are among the key priorities for businesses. However, now security comes into the equation as the key pillar to protect brand identity and perception.

**So, how do you have a well-rounded and secure connected product and at the same time achieve this in a cost-effective way?**

Many heads were scratched recently going over these dilemmas, looking for the best answer.

Look no further, we have an answer for you - a fully secure solution with a hardware part (MCU + crypto chip) costs below $3.00!

Unbelievable? Almost, but it is definitely real.

As a matter of fact, there are several strong key players who have come together to put out a solution which is fairly inexpensive, but provides the highest level of security available now:

  1. [AWS IoT](https://aws.amazon.com/iot/) is the only cloud provider insisting on secure 2-way TLS authentication for any device connecting to it.

  2. [Microchip](http://www.microchip.com/) (Atmel) and their [ECC508A](http://www.atmel.com/products/security-ics/cryptoauthentication/ecc-256.aspx) crypto chip, which stores SSL certificates securely on the devices, which is literally impossible to hack. The best point here is it is priced at under $1.00.

  3. [Espressif Systems](http://espressif.com/) and their ESP8266 chip, which is probably the most popular Wi-Fi-enabled MCU with a price point of below $2.00 as well.

Now you've got the components to make your connected device secure and in a very cost-effective way. So, what do you need to do and how do you get to bundle them?

Here comes Cesanta, a company behind the very popular [Mongoose Web Server](https://www.cesanta.com/), with their [Mongoose OS](https://mongoose-iot.com/) which not only bundles all three components outlined above but which has been developed in a way where you can literally plug-and-play the solution into your product and have secure IoT connectivity from the get-go, with actual implementation being so seamless you won't even notice it has happened.

You are probably asking, how is that all possible? Is this another ad pushing something into my head? Fear not, this is not an advertisement, but an overview of an open-source product you can actually try out immediately after you have finished reading this article. Now, who else can do this for you?

**So let's have a closer look at the solution:**

  1. [Mongoose OS](https://mongoose-iot.com/) is the only industrial-grade firmware available for ESP8266. Proven, stable, tested over time.

  2. It is seamlessly integrated with AWS IoT providing secure 2 way MQTT authentication.

  3. It supports an ECC508A crypto chip and makes the security and certificate storage on the end device bulletproof.

  4. Security is enforced by a mbedTLS library - the most trusted and stable on the market. It has been tuned by Cesanta so it can fit constrained resources available on the ESP8266.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
