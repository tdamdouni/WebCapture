# Benefits of REST APIs With HTTP/2

_Captured: 2018-01-17 at 14:37 from [dzone.com](https://dzone.com/articles/benefits-of-rest-apis-with-http2?edition=352125&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-01-17)_

[Modernize your application architectures with microservices and APIs](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) with best practices from this free virtual summit series. Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

### HTTP/1.x vs HTTP/2

First, let's look at some of the high-level differences:

#### HTTP/2 Is Binary, Instead of Textual

Binary protocols are more efficient to parse, more compact "on the wire," and, most importantly, they are much less error-prone compared to textual protocols like HTTP/1.x, because they often have a number of affordances to "help" with things like whitespace handling, capitalization, line endings, blank lines, and so on.

For example, [HTTP/1.1](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) defines four different ways to parse a message; in [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2), there's just one code path.

#### HTTP/2 Is Fully Multiplexed, Instead of Ordered and Blocking

HTTP/1.x has a problem called "head-of-line blocking," where effectively only one request can be outstanding on a connection at a time.

HTTP/1.1 tried to fix this with pipelining, but it didn't completely address the problem (a large or slow response can still block others behind it). Additionally, pipelining has been found very difficult to deploy, because many intermediaries and servers don't process it correctly.

![](http://blog.restcase.com/content/images/2018/01/http1-vs-http2-multiplexing.png)

This forces clients to use a number of heuristics (often guessing) to determine what requests to put on which connection to the origin and when; since it's common for a page to load 10 times (or more) the number of available connections, this can severely impact performance, often resulting in a "waterfall" of blocked requests.

[Multiplexing ](https://en.wikipedia.org/wiki/Multiplexing)addresses these problems by allowing multiple request and response messages to be in flight at the same time; it's even possible to intermingle parts of one message with another on the wire.

This, in turn, allows a client to use just one connection per origin to load a page.

### HTTP/2 Can Use One Connection for Parallelism

With HTTP/1, browsers open between four and eight connections per origin. Since many sites use multiple origins, this could mean that a single page load opens more than thirty connections.

One application opening so many connections simultaneously breaks a lot of the assumptions that TCP was built upon; since each connection will start a flood of data in the response, there's a real risk that buffers in the intervening network will overflow, causing a congestion event and retransmits.

> You can see a demo of how HTTP/2 is working here: <https://http2.akamai.com/demo>

Additionally, using so many connections unfairly monopolizes network resources, "stealing" them from other, better-behaved applications (e.g., VoIP).

#### HTTP/2 Uses Header Compression to Reduce Overhead

If you assume that a page has about 80 assets (which is conservative in today's Web), and each request has 1400 bytes of headers (again, not uncommon, thanks to Cookies, Referer, etc.), it takes at least 7-8 round trips to get the headers out "on the wire." That's not counting response time - that's just to get them out of the client.

![](http://blog.restcase.com/content/images/2018/01/header_compression.jpg)

This is because of [TCP's Slow Start mechanism](https://en.wikipedia.org/wiki/TCP_congestion_control), which paces packets out on new connections based on how many packets have been acknowledged - effectively limiting the number of packets that can be sent for the first few round trips.

In comparison, even a mild compression on headers allows those requests to get onto the wire within one roundtrip - perhaps even one packet.

This overhead is considerable, especially when you consider the impact upon mobile clients, which typically see round-trip latency of several hundred milliseconds, even under good conditions.

#### HTTP/2 Allows Servers to "Push" Responses Proactively Into Client Caches

When a browser requests a page, the server sends the HTML in the response and then needs to wait for the browser to parse the HTML and issue requests for all of the embedded assets before it can start sending the JavaScript, images, and CSS.

Server Push potentially allows the server to avoid this round trip of delay by "pushing" the responses it thinks the client will need into its cache.

However, pushing responses is not "magical" \- if used incorrectly, it can harm performance. For now, many are still will continue to work with [Webhooks](https://blog.restcase.com/webhooks-role-in-the-api-world/).

### How Does This Affect the Existing REST APIs Built on HTTP/1.1?

The main semantic of HTTP has been retained in HTTP/2. This means that it still has HTTP methods such as `GET`, `POST`, `HTTP headers`, and `URIs` to identify resources.

What has changed in HTTP/2 with respect to HTTP/1.1 is the way the HTTP semantic (e.g. "I want to PUT resource /foo on host domain.com") is transported over the wire. This means that **REST APIs built on HTTP/1.1 will continue to work transparently as before, with no changes to be made to applications**.

The web container that runs the applications will take care of translating the new wire format into the usual HTTP semantic on behalf of the applications, and the application just sees the higher level HTTP semantic, no matter if it was transported via HTTP/1.1 or HTTP/2 over the wire.

Because the HTTP/2 wire format is more efficient (in particular due to multiplexing and compression), REST APIs on top of HTTP/2 will also benefit from this.

The other major improvement present in HTTP/2, HTTP/2 Push, targets the efficient downloading of correlated resources, and, as it's probably not useful in most REST API use cases, perhaps only the Object Storage like services can benefit from this (like Amazon S3).

A typical requirement of HTTP/2 is to be deployed over TLS. This requires deployers to move from `HTTP` to `HTTPS` which means buying SSL certificates from a trusted authority, etc.

### HTTP/2 Benefits Explained

Among the key improvements brought by HTTP/2 are multiplexed streams, header compression, server push, and a binary protocol instead of textual one. These and other positive changes allowed to achieve good web pages loading results, including those having lots of additional files attached to them (e.g. styles, scripts, images, fonts, etc.).

![](http://blog.restcase.com/content/images/2018/01/http2-1.jpg)

HTTP/2, the new version of the HTTP protocol, provides also a lot of new features for server-to-server communication:

#### Bidirectional Communication Using Push Requests

HTTP/2's "server push" allows a server to proactively send things to the client's cache for future use.

This helps avoid a round trip between fetching HTML and linked stylesheets and CSS, for example; the server can start sending these things right away, without waiting for the client to request them.

It's also useful for proactively updating or invalidating the client's cache, something that people have asked for.

Of course, in some situations, the client doesn't want something pushed to it - usually because it already has a copy, or knows it won't use it. In these cases, it can just say "no" with RST_STREAM.

#### **Multiplexing Within a Single TCP Connection**

HTTP/2 uses multiplexing to allow many messages to be interleaved together on a connection at the same time so that one large response (or one that takes a long time for the server to think about) doesn't block others.

Furthermore, it adds header compression, so that the normal request and response headers don't dominate your bandwidth - even if what you're requesting is very small. That's a huge win on mobile, where getting big request headers can easily blow out the load time of a page with a lot of resources by several round trips.

#### Long Running Connections

HTTP/2 is designed to use fewer connections so servers and networks will enjoy less load. This is especially important when the network is getting congested because HTTP/1's use of multiple connections for parallelism adds to the problem.

For example, if your phone opens up six TCP connections to each server to download a page's resources (remembering that most pages use multiple servers these days), it can very easily overload the mobile network's buffers, causing them to drop packets, triggering retransmits, and making the problem even worse.

HTTP/2 allows the use of a single connection per host and encourages sites to consolidate their content on one host where possible.

#### Stateful Connections

If your HTTP/1 client sends a request and then finds out it doesn't need the response, it needs to close the connection if it wants to save bandwidth; there's no safe way to recover it.

HTTP/2 adds the RST_STREAM frame to allow a client to change its mind; if the browser navigates away from a page, or the user cancels a download, it can avoid having to open a new connection without wasting all of that bandwidth.

Again, this is about improving perceived performance and network friendliness; by allowing clients to keep the connection alive in this common scenario, extra roundtrips and resource consumption are avoided.

### But...

As always, not everything is about benefits, there are some questionable downsides:

#### Using Binary Instead of Text

This is also a good and a not so good feature.

One of the nice things about HTTP/1 is the ability to open up telnet, type in a request (if the server doesn't time out!) and then look at the response. This won't be practical in HTTP/2 because it's a binary protocol. Why?

Consider how can we store short int 30000 (0x7530), both as text and as binary:

![](http://blog.restcase.com/content/images/2018/01/text_vs_binary_comp.jpg)

As you can see, instead of using 5 bytes we are using 2 bytes. It is more than 50% size reduction.

While binary protocols have lower overhead to parse, as well as a slightly lighter network footprint, the real reason for this big change is that binary protocols are simpler and therefore less error-prone.

That's because textual protocols have to cover issues like how to delimit strings (counted? double-newline?), how to handle whitespace, extra characters, and so on. This leads to a lot of implementation complexity; in HTTP/1, there are no fewer than three ways to tell when a message ends, along with a complex set of rules to determine which method is in use.

HTTP/1's textual nature has also been the source of a number of security issues; because different implementations make different decisions about how to parse a message, malicious parties can wiggle their way in (e.g., with the response splitting attack).

One more reason to move away from text is that anything that looks remotely like HTTP/1 will be processed as HTTP/1, and when you add fundamental features like multiplexing (where associating content with the wrong message can have disastrous results), you need to make a clean break.

Of course, all of this is small solace for the poor ops person who just wants to debug the protocol. That means that we'll need new tools and plenty of them to address this shortcoming; to start, Wireshark already has a plug-in.

#### More Encryption

HTTP/2 doesn't require you to use TLS (the standard form of SSL, the Web's encryption layer), but its higher performance makes using encryption easier since it reduces the impact on how fast your site seems. This means that you will probably need to buy SSL certificates, renew them, etc. This is not a small amount money to spend when you are working with many microservices using REST APIs.

In fact, many people believe that the only safe way to deploy the new protocol on the "open" Internet is to use encryption; Firefox and Chrome have said that they'll only support HTTP/2 using TLS.

They have two reasons for this. One is that deploying a new version of HTTP across the Internet is hard, because a lot of "middleboxes," like proxies and firewalls, assume that HTTP/1 won't ever change, and they can introduce interoperability and even security problems if they try to interpret an HTTP/2 connection.

The other is that the Web is an increasingly dangerous place, and using more encryption is one way to mitigate a number of threats. By using HTTP/2 as a carrot for sites to use TLS, they're hoping that the overall security of the web will improve.

### Summary

The real benefit to your existing REST APIs will be if most of your microservices that are probably REST based are working server to server communication. In today's microservices architecture, when many microservices are talking between themselves in many ways but still using REST, HTTP/2 can increase the speed of your workflows.

HTTP/2 does not define a JavaScript API nor does it help you [build your REST APIs](https://apibldr.com/) much more easily. For now, JavaScript clients running in a web browser can make only limited use of the new capabilities. However, for server-to-server communication, HTTP/2 provides a lot of ways to go beyond existing REST APIs.

Furthermore, the downside of HTTP/2's network friendliness is that it makes TCP congestion control more noticeable; now that browsers only use one connection per host, the initial window and packet losses are a lot more apparent.

Just as HTTP has undergone a period of scrutiny, experimentation, and evolution, it's becoming apparent that the community's attention is turning to TCP and its impact upon performance; there's already been early discussion about tweaking and even replacing TCP in the IETF.

The Integration Zone is proudly sponsored by [CA Technologies](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Learn from expert microservices and API presentations at the [Modernizing Application Architectures Virtual Summit Series](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
