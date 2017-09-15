# The HTTP Series (Part 3): Client Identification

_Captured: 2017-08-15 at 19:30 from [dzone.com](https://dzone.com/articles/the-http-series-part-3-client-identification)_

Up until now, you learned about the basic concepts and some of the architectural aspects of HTTP. This leads us to the next important subject to the HTTP: client identification.

In this article, you'll learn why client identification is important and how can Web servers identify you (your Web client). You will also get to see how that information is used and stored.

This is what we have learned so far, and where we are now:

  * **The HTTP series (Part 3): Client Identification**
  * The HTTP series (Part 4): Authentication mechanisms
  * The HTTP series (Part 5): Security

First, let's see why websites need to identify you.

## Client Identification and Why It's Extremely Important

As you are most definitely aware, every website, or at least those that care enough about you and your actions, include some form of content personalization.

What do I mean by that?

Well, that includes suggested items if you visit an e-commerce website, or "the people you might know/want to connect with" on social networks, recommended videos, ads that almost spookily know what you need, news articles that are relevant to you, and so on.

This effect feels like a double edged sword. On the one hand, it's pretty nifty having personalized, custom content delivered to you. On the other hand, it can lead to [Confirmation bias](https://en.wikipedia.org/wiki/Confirmation_bias) that can result in all kinds stereotypes and prejudice. There is an [excellent Dilbert comic](http://dilbert.com/strip/2011-07-02) that touches upon Confirmation bias.

Yet, how can we live without knowing how our favorite team scored last night, or what celebrities did last night?

Either way, content personalization has become part of our daily lives we can't, and we probably don't even want to, do anything about it.

Let's see how web servers can identify you to achieve this effect.

## Different Ways to Identify the Client

There are several ways that a web server can identify you:

  * **HTTP request headers**
  * **IP address**
  * **Long URLs**
  * **Cookies**
  * **Login information (authentication)**

## HTTP Request Headers Used for Identification

Web servers have a few ways to extract information about you directly from the [HTTP request headers](https://www.code-maze.com/the-http-reference/#headers).

Those headers are:

  * **From - **contains user's email address if provided.
  * **User-Agent - **contains information about the web client.
  * **Referer - **contains the source the user came from.
  * **Authorization - **contains username and password.
  * **Client-ip - **contains user's IP address.
  * **X-Forwarded-For - **contains user's IP address (when going through the [proxy server](https://www.code-maze.com/http-series-part-2/#proxyservers)).
  * **Cookie - **contains server-generated ID label.

In theory, the **From header** would be ideal to uniquely identify the user, but in practice, this header is rarely used due to the security concerns of email collection.

The** user-agent header** contains the information like the browser version or operating system. While this is important for customizing content, it doesn't identify the user in a more relevant way.

The **Referer header** tells the server where the user is coming from. This information is used to improve the understanding of user behavior, but less so to identify it.

While these headers provide some useful information about the client, it is not enough to personalize content in a meaningful way.

The remaining headers offer more precise mechanisms of identification.

## IP Address

The method of client identification by IP address has been used more in the past when IP addresses weren't so easily faked/swapped. Although it can be used as an additional security check, it just isn't reliable enough to be used on its own.

Here are some of the reasons why:

  * It **describes the machine**, not the user.
  * **NAT firewalls - **many ISPs (Internet service providers) use NAT firewalls to enhance security and deal with IP address shortage
  * **Dynamic IP addresses - **users often get the dynamic IP address from the ISP
  * **HTTP [proxies](https://www.code-maze.com/http-series-part-2/#proxyservers) and [gateways](https://www.code-maze.com/http-series-part-2/#gateways) - **these can hide the original IP address. Some proxies use Client-ip or X-Forwarded-For to preserve the original IP address

## Long (fat) URLs

It is not that uncommon to see websites utilize URLs to improve the user experience. They add more information as the user browses the website until URLs look complicated and illegible.

You can see what the long URL looks like by browsing Amazon store.

There are several problems when using this approach.

  * It's ugly.
  * Not shareable.
  * Breaks caching.
  * It's limited to that session.
  * Increases the load on the server.

## Cookies

The best client identification method up to date excluding authentication. Developed by Netscape, but now every browser supports them.

There are two types of cookies: **session cookies** and **persistent cookies**. A session cookie is deleted upon leaving the browser, and persistent cookies are saved on disk and can last longer. For the session cookie to be treated as the persistent cookie, Max-Age or Expiry property needs to be set.

Modern browsers like Chrome and Firefox can keep background processes working when you shut them down so you can resume where you left off. This can result in the [preservation of the session cookies](https://bugs.chromium.org/p/chromium/issues/detail?id=128513), so be careful.

So how do the cookies work?

Cookies contain a list of name=value pairs that the server sets using [Set-Cookie or Set-Cookie2 response header](https://www.code-maze.com/the-http-reference/#headers). Usually, the information stored in a cookie is some kind of client id, but some websites store other information as well.

The browser stores this information in its cookie database and returns it when the user visits the page/website again. The browser can handle thousands of different cookies and it knows when to serve each one.

Here is an **example flow**.

1\. User Agent -> Server

The user agent identifies itself via the form input.

2\. Server -> User Agent
    
    
    Set-Cookie2: Customer="WILE_E_COYOTE"; Version="1"; Path="/acme"

The server sends the Set-Cookie2 response header to instruct the user agent (browser) to set the information about the user in a cookie.

3\. User Agent -> Server

The user selects the item to put the shop basket.

4\. Server -> User Agent

Shopping basket contains an item.

5\. User Agent -> Server

The user selects the shipping method.

6\. Server -> User Agent

New cookie reflects the shipping method.

7\. User Agent -> Server

That's it.

There is one more thing I want you to be aware of. Cookies are not perfect either. Besides security concerns, there is also a problem with [cookies colliding with the REST architectural style](https://www.infoq.com/articles/rest-anti-patterns) (the section about misusing cookies).

You can learn more about cookies in the [RFC 2965](https://www.ietf.org/rfc/rfc2965.txt).

## Conclusion

This wraps it up for this part of the [HTTP series](https://www.code-maze.com/http-series/).

You have learned about the strengths of content personalization as well as its potential pitfalls. You are also aware of the different ways that servers can use to identify you. In [part 4](https://www.code-maze.com/http-series-part-4/) of the series, we will talk about the most important type of client identification: authentication.

Thank you for reading and feel free to leave the comment below.

## References
