# HTTPS From HTTP: How And Why You Need To Migrate

_Captured: 2017-03-01 at 12:59 from [dzone.com](https://dzone.com/articles/safer-web-practices-with-https-website-https-from?oid=twitter&utm_content=buffera98ff&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

## Why HTTPS?

We don't hang out on the internet anymore. We live on the internet. Just like our physical world, the internet is a funny place - at times quirky, at times it's random, and at times it's safe. Well, we think it's safe. As developers and website owners,** we are responsible** for providing a safe web experience to all of our users.

As users ourselves, we have seen it all:

  * Malware injections
  * Popups triggering software installs
  * Trojan horse viruses
  * etc.

Luckily, most of that is over. The modern age browsers take care of these issues by default. But browsers are just a container that renders whatever the server throws at it. There is only so much it can do. Users (and by extension, websites) are still vulnerable to javascript injections (read more [here](http://www.medianama.com/2015/06/223-mtnl-isp-advertising-airtel/) and [here](http://gadgets.ndtv.com/india/news/airtel-javascript-code-injection-discussed-in-parliament-727576)).

Building trust and credibility with users goes a long way. And it is because of this, global leaders such as Mozilla and Google are putting their weight behind _**making the web a more secure place. **_This is contributing to the major reason for a gradual shift from HTTP websites to HTTPS websites.

## **Understanding the Major Difference?**

![This is how a HTTPS website looks like](https://blog.izooto.com/wp-content/uploads/2016/09/term-https.jpg)

> _Source: https://websitesdepot.com/google-announces-new-security-measure-website-owners-https/_

Before we dive deeper, let's get a quick understanding of HTTP and HTTPS. These are the most frequently used protocols on the web.

  * **HTTP**: HyperText Transfer Protocol - a simple protocol for sending and receiving text based messages.
  * **HTTPS**: HyperText Transfer Protocol Secure - the same protocol as HTTP, but the text is encrypted.

[Read this detailed overview to develop a better understanding of HTTP and HTTPS](https://blog.izooto.com/https-http-web-protocols/).

## **How HTTPS Bridges the Gap**

![Difference between http and https](https://blog.izooto.com/wp-content/uploads/2016/09/http-vs-https.png)

> _[Source](https://www.instantssl.com/ssl-certificate-products/https.html)_

Google_ (and many others)_ are committed to making the web more secure for all the users. In 2014, Google had their [HTTPS everywhere campaign](https://www.youtube.com/watch?v=cBhZ6S0PFCY) when they announced [HTTPS as a ranking signal](http://searchengineland.com/google-starts-giving-ranking-boost-secure-httpsssl-sites-199446) and [started indexing secure pages over unsecured pages](http://searchengineland.com/google-to-begin-to-index-https-pages-first-before-http-pages-when-possible-238811).

Google's indexing conditions:

  1. _It shouldn't contain insecure dependencies._
  2. It isn't blocked from crawling by robots.txt.
  3. It shouldn't redirect users to or through an insecure HTTP page.
  4. It shouldn't have a rel="canonical" link to the HTTP page.
  5. It shouldn't contain a noindex robots meta tag.
  6. It shouldn't have on-host outlinks to HTTP URLs.
  7. The sitemap lists the HTTPS URL or doesn't list the HTTP version of the URL.
  8. The server has a valid TLS certificate.

**The first condition is a critical requirement. **The page should not include "insecure dependencies." Many pages **include insecure images, embeds, videos, and so on.**

  * Google has even created their own guide, "[Securing Your Website With HTTPS](https://support.google.com/webmasters/answer/6073543)"**.**
![People opting for https with ssl certificate](https://blog.izooto.com/wp-content/uploads/2016/09/Screenshot-413.png)

> _Source: https://www.keycdn.com/blog/http-to-https/_

According to the data from BuiltWith, around only [6.3% of the top 100,000 websites are using SSL](http://trends.builtwith.com/ssl/SSL-by-Default).

![Secure websites with https protocol](https://blog.izooto.com/wp-content/uploads/2016/09/less_than_1.png)

> _Some additional benefits:_

  1. **More Security**- A major reason why it is important to be running over HTTPS is of course _**because of security!** _The reason you need an SSL certificate for e-commerce and other transactional sites is because they are _**processing sensitive information.**_For other sites, a big reason for going to HTTPS is the _**WordPress login page.**_ If you aren't running over an HTTPS connection, your username and password are sent in clear text over the internet. Anyone can [sniff and capture WordPress logins over unsecured connections using a variety of free tools](http://www.wpwhitesecurity.com/wordpress-security/hacking-wordpress-login-capturing-usernames-passwords/).
  2. **Better Referral Data**- Another good reason to migrate is that the _**referral data is blocked in Google Analytics.** _If your website is on HTTP and you go viral on any HTTPS website, the referrer data will be completely lost and the traffic from the HTTPS website could end up under "direct traffic" _(which is not very helpful)._ If someone is going from HTTPS to HTTPS, the referrer will still be passed.
  3. **SSL Builds Trust and Credibility**- To move to this secure protocol you need an SSL certificate. An SSL certificate builds trust and credibility with your visitors. Visitors tend to look for the _**green padlock**_ on a website. This gives it "[SSL trust](https://www.keycdn.com/blog/ssl-trust/)"._** It is important to let your visitors know you are a secure site and that their information will be safe.**_

## **Common Myths Around the Migration**

![Common myths around migrating to https](https://blog.izooto.com/wp-content/uploads/2016/09/Screenshot-387.png)

> _Let's go ahead and bust these myths._

  1. **My site's not important enough.**

More than often, publishers maintain that their properties don't handle sensitive user data (login info, payments, etc.) so they can do away with HTTPS.

It is important to note that **Javascript-based ad injections** _**are well known to kill user experience.**_

  * Read here about how ISPs [including Airtel and MTNL have indulged in such activities](http://www.medianama.com/2015/06/223-mtnl-isp-advertising-airtel/).

Moreover, running on HTTP _**restricts web developers**_ from using key APIs including:

  * **GeoLocation:** You can no longer seek a user's location if you are on HTTP.
  * **Web Push Notification:** Push notifications are only available on HTTPS.
  * **GetUserMedia:** You can no longer trigger permissions of using a user's camera/microphone if you are on HTTP.
  * **HTTP/2:** All major browsers support HTTP/2 for HTTPS.
  * **EME and App Cache:** To be removed soon.
  2. **HTTPS will slow down my site.**

Quite a few developers have witnessed negative results post migration to HTTPS. Having said that, when Gmail was migrated to HTTP in 2010, there was **no noticeable performance impact.**

Here are the stats from the Gmail's migration:

![Myths around migrating to https](https://blog.izooto.com/wp-content/uploads/2016/09/Screenshot-389.png)

Negative results are often because of a **lack of optimization** such as moving to HTTP/2. We have to update the way that we talk about HTTPS and performance.

  3. **I can move my site to HTTPS, but what about the 3rd parties I depend on?**

Another major concern for publishers is with reference to the third party content on their website - primarily ads _[most often the only source of monetization]._

A key constraint with this is, if you move to HTTPS, **all of your content (including third party content) also has to be served over HTTPS.**

**Note**: [Google AdSense](http://www.shoutmeloud.com/how-to-adsense) and Ad Exchange requests are_** already**_ being served over HTTPS.

There is also the concern about partnerships wherein 3rd party service providers depend on the HTTP referrer header. When a user follows a link from an HTTPS site to an HTTP partner site, browsers will _**strip their referrer header**_ for privacy reasons. There's a web platform feature called **"**[Referrer Policy](https://www.w3.org/TR/referrer-policy/)**"** that helps with this.

Publishers can set a referrer policy to allow their partners to see which traffic is coming from their site, but they won't see the full URL that the user was visiting, so user privacy is maintained.

Then there is a kind of general problem called mixed content. Mixed content is the problem of _loading non-secure HTTP content on HTTPS. _This is important because non-secure sub-resources can actually compromise the security of a secure HTTPS site. Browsers will actually block this content and completely wipe out all of the security of that HTTPS site.

Publisher websites (i.e. blogs) contain a lot of old news articles that link to third party images which aren't available over HTTPS. These images are called _passive content_ and browsers will still allow them to load.

The HTTPS site won't be completely broken, but that green lock will go away.

![Content security policy related to https](https://blog.izooto.com/wp-content/uploads/2016/09/Screenshot-401.png)

_Complete video:_

This header is basically a way for publishers to assert to the browser that all content should be loaded over HTTPS and that the publishers want to receive reports about any content that isn't. [Content Security Policy](https://content-security-policy.com/) allows publishers to find and fix mixed content across their properties. Chrome also has a _DevTools security panel_ to make it as easy as possible to find and fix problems with HTTPS configurations such mixed content issues. Essentially, third party providers must support HTTPS in order for you to fully move your site.

## **Frequently Asked Questions**

  * **How does this whole communication take place?**
![Communication flow over https server](https://blog.izooto.com/wp-content/uploads/2016/09/ssl1.png)

_**When a client/browser requests for a secure session over HTTPS, the server responds with the SSL certificate.**_

A request is made from the client end and the server responds with the certificate and the server's public key. The client/browser then checks the validity of the SSL certificate signed by CA. Then the client/browser sends an _encrypted session key_ with the server's public key. Now the server de-crypts the session key with its private key.

With this, _**a secure session is created for a secure data transfer.**_

  * **How is the data sent over HTTPS secured?**

Data sent using HTTPS is secured via Transport Layer Security protocol (TLS), which provides **three key layers** of protection for your information:

  1. **Encryption - **Encrypting the exchanged data to keep it secure from eavesdroppers. The encryption ensures that while browsing, no one can intrude into conversations, track activities across pages, or get access to any information.
  2. **Data integrity -** This means data cannot be compromised during transfer and any alteration made to the data cannot be easily detected.
  3. **Authentication - **This ensures that users are on the correct website. HTTPS authentication protects against [man-in-the-middle](https://blog.izooto.com/https-http-web-protocols/) attacks and builds user trust.

[Here is the full list of frequently asked questions](https://www.seroundtable.com/google-faq-on-http-to-https-migration-21568.html).

## **Getting Your SSL Certificate**

There are numerous options that can be availed to get an [SSL certificate](https://www.sslshopper.com/) while moving from HTTP to HTTPS.

Here are three great options:

**[Let's Encryp****t**](http://www.shoutmeloud.com/recommended/Letsencrypt/)- Get your **absolutely FREE **SSL certificate from Let's Encrypt! You can choose a number of options from their available certificates. Domain Validation: Single domain or subdomain, no paperwork (just email validation), cheap, issued within minutes. 

**Business/Organization **Requires business verification and provides a high level of security, issued within 1-3 days.

**Extended Validation**: Requires business verification which provides a higher level of security, issued within 2-7 days.

You can check the [Full Documentation](https://certbot.eff.org/docs/intro.html) and get your SSL certificate from[https://letsencrypt.org/](http://www.shoutmeloud.com/recommended/Letsencrypt/)

**[AWS Certificate Manager**](https://aws.amazon.com/certificate-manager/) (ACM). These certificates are free and issued directly by Amazon and last a little over a year. However, they currently require manual issuance through email validation, and do not support[Certificate Transparency](https://www.certificate-transparency.org/). Here's a [good ACM guide for Jekyll](https://olivermak.es/2016/01/aws-tls-certificate-with-jekyll/).

## Things to Do While Making the Switch

![migrating from http to https](https://blog.izooto.com/wp-content/uploads/2016/09/http-to-https-cropped-507x1024.png)

First of all, **buy and activate an SSL certificate** if you haven't already. During the migration, there could be some hurdles stalling the process. Errors may occur when Google starts crawling the HTTP version of your website and generating content duplication issues, with both HTTPS and HTTP versions of the pages shown and different versions of the page showing on HTTP and HTTPS.

![pitfalls-in-using-HTTPS](https://blog.izooto.com/wp-content/uploads/2016/09/pitfalls-in-using-HTTPS.png)

Check out these other [common pitfalls in using HTTPS/TLS](https://support.google.com/webmasters/answer/6073543?hl=en).

## Best Practices When Migrating to HTTPS:

![https protocol](https://blog.izooto.com/wp-content/uploads/2016/09/HTTPS_Fig1.png)

  1. **Using robust security certificates. **As part of enabling HTTPS for your website, you must obtain a security certificate (SSL certificate). The certificate is issued by a [certificate authority](http://en.wikipedia.org/wiki/Certificate_Authority) (CA) which takes steps to verify that your web address actually belongs to your organization. While setting up your certificate, ensure a high level of security by choosing a 2048-bit key. If you already have a certificate with a weaker key (1024-bit), _**an upgrade would be a great way to go.**_
  2. **Redirect your users and search engines** to the HTTPS page or resource with server-side 301 HTTP redirects.
  3. **Use a web server that supports HTTP** Strict Transport Security (HSTS) and make sure that it's enabled.

The idea behind the whole migration is to provide a safer web experience, ensuring your personal information _**stays private**_ and does not get misused.

**Anything and everything** could be personal to you or your end users.

Even if you are searching for _"Nexus 5 cost in India",_ that search could be private to you. Whether you are browsing or looking for a product or reading an article, you generally do not want what you're doing to be public information. Particularly for personal information, banks, and transaction information, HTTPS has become a necessity and an industry standard.

Though the migration is _highly recommended_ and being followed by most website developers, the final decision depends on you. For those who are ready to follow this safer web practice, get started by grabbing your SSL certificate and be delighted to have that green padlock on your website.

Have you made the switch yet? Let me know in the comments.
