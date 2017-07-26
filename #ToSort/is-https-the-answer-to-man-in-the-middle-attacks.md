# Is HTTPS the Answer to Man in the Middle Attacks?

_Captured: 2017-05-07 at 19:18 from [dzone.com](https://dzone.com/articles/is-https-the-answer-to-man-in-the-middle-attacks)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

A Man in the Middle attack, or MITM, is a situation wherein a malicious entity can read/write data that is being transmitted between two or more systems (in most cases, between you and the website that you are surfing). MITMs are common in China, thanks to the "Great Cannon."

The "Great Cannon" is slightly different from the "The Great Firewall." The firewall monitors web traffic moving in and out of China and blocks prohibited content.

The Great Cannon, on the other hand, acts as a man in the middle and is not just able to eavesdrop on the conversation taking place between two or more systems, but is also capable of altering the content or redirecting the users to a different property on the Internet without the user even realizing that he/she is not communicating with the intended machine.

In an MITM attack, the attacker may use one of the many possible ways to split the TCP connection into two separate connections. One connection will be used between the client and the attacker, whereas the second connection will be used between the attacker and the web server, making the eavesdropper act like a proxy who is able to intercept data being sent between the client and the server.

Such attacks are common when it comes to HTTP because of the way HTTP as a protocol is designed. HTTP works as a request/response protocol where a web browser, for example, will be the client, and an application or a website hosted on the web will be the server. It's easy for an Internet Service Provider or a network administrator to run a packet sniffer (Wireshark, Fiddler, HTTP Analyzer) on the Network and capture the traffic moving between the client and the server.

## **Why Should the Internet Start Using HTTPS More?**

HTTPS, otherwise known as HTTP over TLS/SSL or HTTP Secure, is a protocol that is used for communication that needs to be secure; it's designed to transfer information in an encrypted form. The data is transferred over HTTP using the Secured Socket Layer (SSL). HTTPS connections were initially used to secure transactions that involved money and sensitive content.

Lately, HTTPS is being used on websites that are not necessarily financial sites or sites that handle sensitive content. This is a welcomed trend, as it extends data encryption beyond payment gateways and banking websites, making the Internet a little more secure.

Starting with the release of Chrome version 56, any website that is not running HTTPS will have the following message appear in the location bar that says "Not Secure" on pages that collect passwords or credit cards. Per Google's "Transparency Report":

> Secure web browsing through HTTPS is becoming the norm. Desktop users load more than half of the pages they view over HTTPS and spend two-thirds of their time on HTTPS pages. HTTPS is less prevalent on mobile devices, but an upward trend can be seen there too. 

HTTPS is vital in preventing MITM attacks as it makes it difficult for an attacker to obtain a valid certificate for a domain that is not controlled by him, thus preventing eavesdropping.

## **Analysis of a Use Case**

Recently, a customer who was using our web testing functionality to monitor their performance complained that they were seeing a lot of performance issues from some of their locations in China.

![](http://blog.catchpoint.com/wp-content/uploads/2017/04/Screen-Shot-2017-04-26-at-9.27.38-AM.png)

We observed the following when investigating further:

1\. The number of items downloaded was highly inconsistent.

2\. The waterfall view showed us that the HTTP version of the website was getting redirected to random websites using an HTTP 302 (Temporary Redirect), suggesting that this was an MITM attack in China.

3\. The HTTPS version of the same website did not show this behavior and was not getting redirected.

4\. In this case, a permanent redirect (HTTP 301) existed from http:// to https://. However, since HTTP was not secure, the MITM attack was happening between the URL redirect from HTTP to HTTP Secure.

## **Important Takeaways**

  * The objective of end-user monitoring should not be limited to monitoring uptime but should take into consideration real user scenarios and determine whether the user is able to access the intended website.
  * Security plays a very important role in today's world where people are concerned about privacy and online identity.
  * It is highly recommended for businesses to move to HTTPS and to ensure that they have their servers patched and TLS correctly implemented.
  * In scenarios like these, our recommendation would be to use the HTTPS version of websites for newsletters, search engine optimization rules, and advertising campaigns. This will ensure that the traffic is being directed to the HTTPS version of the website and not the HTTP version.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.

### Like This Article? Read More From DZone
