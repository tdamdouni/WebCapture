# A Beginner's Guide to SSL: What It Is & Why It Makes Your Website More Secure 

_Captured: 2015-09-16 at 23:37 from [blog.hubspot.com](http://blog.hubspot.com/marketing/what-is-ssl?utm_campaign=Inbound%2015%20Product%20Launch%20Webinar&utm_content=20236952&utm_medium=social&utm_source=twitter)_

![](http://cdn2.hubspot.net/hub/53/hubfs/what-is-ssl-1.jpg?t=1442439385868&width=669&height=278)

Have you ever noticed that some URLs start with "http://" while others start with "https://"? Perhaps you noticed that extra "s" when you were browsing websites that require giving over sensitive information, like when you were paying bills online.

But where'd that extra "s" come from, and what does it mean?

To put it simply, the extra "s" means your connection to that website is encrypted so hackers can't intercept any of your data. The technology that powers that little "s" is called SSL, which stands for Secure Sockets Layer.

In this post, I'm going to break down what SSL is and how it works. Then, I'll show you how to tell whether a website has SSL and how to get it on your own website.

## What is SSL?

First, let's start with a definition from [SSL.com](http://info.ssl.com/article.aspx?id=10241):

> _SSL is the standard security technology for establishing an encrypted link between a web server and a browser. This link ensures that all data passed between the web server and browser remain private."_

Let's break that down for a second.

Imagine you're watching American football. Your team is only down by a few points to win, and the receiver needs to catch the ball in the end zone to put your team ahead. The quarterback drops back in the pocket, throws, and ... it's intercepted! Bummer, man.

Similarly, when you enter information into a webpage without SSL, it can be intercepted by a prying hacker and your information can be stolen.

This information could be anything from details on a bank transaction, to high-level information you enter to register for an offer. In hacker lingo, this "interception" often referred to as a "man-in-the-middle attack." The actual attack can happen in a number of ways, but one of the most common is this: A hacker places a small, undetected listening program on the server hosting a website. That program waits in the background until a visitor starts typing information on the website, and it will activate to start capturing the information and then send it back to the hacker.

But when you visit a website that's encrypted with SSL, your browser will form a connection with the webserver, look at the SSL certificate, and then bind together your browser and the server. This binding connection is secure so that no one besides you and the website you're submitting the information to can see or access what you type into your browser.

This connection happens instantly and doesn't require you to do anything. You simply have to visit a website with SSL, and voila: Your connection will automatically be secured.

## Is SSL good for SEO?

Yes. While the primary purpose of SSL is securing information between the visitor and your website, there are benefits for SEO as well. [According to Google Webmaster Trends Analysts Zineb Ait Bahajji](http://googlewebmastercentral.blogspot.com/2014/08/https-as-ranking-signal.html), SSL is now part of Google's search ranking algorithm:

> _Over the past few months we've been running tests taking into account whether sites use secure, encrypted connections as a signal in our search ranking algorithms. We've seen positive results, so we're starting to use HTTPS as a ranking signal."_

## How can I tell if a website has SSL?

When you visit a website with SSL, there are a few distinct differences that display within the browser.

### 1) The URL says "https://" and not "http://". 

It looks like this:

###   
2) You'll see a little padlock icon in the URL bar.

It'll show up either on the left- or right-hand size of the URL bar, depending on your browser. You can click on the padlock to read more information about the website and the company that provided the certificate.

![](http://cdn2.hubspot.net/hubfs/53/GeoTrust-SSL-Details.png?t=1442439385868)

### 3) The certificate is valid.

Even if a website has the "https://" and a padlock, the certificate could still be expired -- meaning your connection wouldn't be secure.

To find out whether the certificate is valid, click on the padlock and choose "Certificate Information." That'll take you to a certification authority page, which'll show you the time frame of the certificate. Notice the two fields toward the bottom of the screenshot below: "Not Valid Before" and "Not Valid After." If the "Not Valid After" date is in the past, then the certificate has expired.

## How can I get an SSL certificate for my website?

If you're looking to get an SSL certificate for your website, you'll need to figure out which type of certificate fits your needs.

First, consider how many certificates you need and which domains you need to secure. For example, you may want to secure your blog, your website, and your landing pages. In that case, depending on how each is configured, you may need to purchase a specific type of certificate from SSL certificate authorities like [GeoTrust](https://www.geotrust.com/) or [Globalsign](https://www.globalsign.com/en/).

(**HubSpot customers:** If you're using the Website Platform, you can get a standard SSL certificate for free. If you're a customer but don't have the HubSpot Website Platform, SSL is available for purchase. To find out more, contact your Customer Success Manager, or [visit our pricing page](http://hubspot.com/pricing-comparison).)

One of the other key considerations is the validity period of a certification. Most standard SSL certificates are available for one to two years by default, but if you're looking for longer-term options, then look into more advanced certificates that offer longer time periods.
