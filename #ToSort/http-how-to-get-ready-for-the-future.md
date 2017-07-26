# HTTP/2: How to Get Ready for the Future

_Captured: 2017-05-14 at 17:30 from [dzone.com](https://dzone.com/articles/http2-how-to-get-ready-for-the-future?edition=298099&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-13)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190137&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190137&u=https%3A%2F%2Fwww.wakanda.io%2F).

HTTP/2 is the future of browser communication, and as such, it offers many opportunities to users, developers, and DevOps. Read this blog post to learn how HTTP/2 works, what makes it better than HTTP/1.1 (or maybe not) and where it still needs to improve.

## A Brief History of HTTP, HTTP/1.1, SPDY, and HTTP/2

[HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol), or Hypertext Transfer Protocol, is the method of communication used by browsers to communicate to web servers. The most commonly used version of HTTP is HTTP/1.1, which was introduced in 1997. However, its last major release was in 1999, when browsers were a different animal, not to mention the concept of the Internet as a whole. Today's websites contain more data and resources than before, sometimes hundreds of them, and they are generally larger in size because they are much more interactive and contain more components and elements. HTTP/1.1 isn't able to deal with all of these improvements, and communication is slower and more complex than necessary.

Google created its own protocol as an improvement to HTTP/1.1. This protocol was called SPDY and it was originally introduced to improve web page load time, latency, and web security. After it was released, a few of SPDY's core developers contributed to the HTTP/2 project as well, which became more and more prominent, which eventually led Google to deprecate their SPDY.

HTTP/2 is the latest HTTP version. It aims to improve many of HTTP/1.1's old behaviors and to work ideally with websites as they are built today. For example, HTTP/1.1 allows only one request per connection. While there might be a few connections open enabling the client to make multiple concurrent requests, this still is a very limited way of retrieving resources from the server side. This makes HTTP/1.1 latency sensitive, and generally slower.

## How HTTP/2 Makes Browser Communication More Efficient, Or: What's All the Fuss About?

The actual structure of HTTP/2 requests and responses is [the same as HTTP/1.1](https://tools.ietf.org/html/rfc7231#section-4). The headers, cookies, and methods are all the same. The only thing that has really changed is the way the web server sends information down the wire to the web browser. This is because HTTP/2 is binary, as opposed to HTTP/1.1 which is textual. This means that it's lighter, easier, and more efficient to parse with a smaller chance of errors.

### HTTP/2 Multiplexing

As mentioned above, HTTP/1.1 allows only one request per connection, which means the next request in line must wait for the first one to finish its trip back to the client. HTTP/1.1 works around this problem by enabling Pipelining, which means browsers can open several connections simultaneously, but this doesn't fully resolve the issue.

This led webmasters to combine CSS and JS files, which has several down sides such as breaking caching, because any small change to a CSS will lead the browser to download the entire big CSS file. It also slows down the resources' downloads as each file is obviously bigger than several smaller ones.

HTTP/2 introduces Multiplexing. This means that it allows you to serve/retrieve multiple requests in parallel, thus it avoids having requests wait in a queue. Practically, this means the client will now be able to retrieve multiple small files at the same time, and the server will no longer have to concatenate many files to one large file, i.e. Spriting, which is a process of combining several small images into one large sprite set.

Specifically, CSS and JS files will no longer have to be grouped into 1 large file, thus the client will no longer have to retrieve redundant code. The fact that with HTTP/2, developers will no longer have to concatenate JS and CSS files is already making it lucrative to use.

### HTTP/2 Introduces 'Server Push'

Another major feature of HTTP/2 is 'Server Push'. 'Server Push' makes resources retrieval much faster. With HTTP/1.1 after the browser requests a page, the server will respond with the HTML file, but the browser will know which resources it needs to request only after parsing it. After the requests are sent, the server will send the embedded resources, e.g JavaScript files, CSS files, and images. With Server Push, the server is more proactive and responds to the initial request with the HTML and with all the embedded resources it believes are relevant. These resources will be cached and will be used by the browser when needed.

![HTTP/2 server push diagram](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/HTTP%20diagram%20\(2\).png)

### HTTP/2 Enables File Prioritization

HTTP/2 also allows prioritization of files. The client may set priorities per resources by "weight" and dependencies, in order to retrieve responses for high priority requests before the less prioritized requests. Since bandwidth is limited by nature, and latency is almost never ideal, it's important to avoid a scenario of low priority resources competing for bandwidth with high priority resources, causing a web page to load slower than it should.

For example, HTML, CSS, and JS files should probably be retrieved before images and icons, in order for the browser to be able to render the structure of the page before the actual media gets there.

### HTTP/2 Introduces HPACK Header Compression

One of the most important efficiency boosters in HTTP/2 is the Header compression in HPACK format, specially designed for HTTP/2. HTTP is a stateless protocol, which means that it will not necessarily retain each communication's status. This means the server does not keep a state in the protocol level that will inform the server of the client's requirements, even if they previously requested something. As a result, all requests must include all the information about the client's requirements, while the server won't store it, which leads to a huge overhead.

In HTTP/2, when a connection is established, all headers are compressed into a large block that is sent in its entirety. After a short trip, the header block is decompressed. An example for such a compression would be that if the 'name:value' pairing or just the 'name' are commonly used, they would only be referenced with just one or two bytes in most cases instead of specifying the actual name and value.

## HTTP/2's Weak Points

### HTTP/2 Requires HTTPS

HTTP/2 websites must support HTTPS and specifically TLS. While HTTPS improves security, it is also slower than HTTP, e.g the SSL/TLS protocol requires one more redirection to be made. Therefore, this condition is a downside for websites that are not currently using HTTPS.

That said, in order to waste as little time as possible when opening a secured connection, HTTP/2 introduced an extension for the TLS protocol in the Application layer called ALPN (Application-Layer Protocol Negotiation). This layer allows for an efficient negotiation with the server over the exact protocol to be used for a connection. Instead of the classic 2-handshake "client-server hello" procedure, ALPN requires only 1 handshake, hence less time to establish the connection, and a shorter latency.

### HTTP/2 'Server Push' Might Disturb Performance

One more weak point is the 'Server Push' feature, which can actually harm performance. Ideally, HTTP/2 should greatly improve page load times. However, it has to be used wisely and requires research, expertise, and a great understanding of the website as well as the website's users' behavior to do so. Otherwise, it might actually slow down the process rather than speed it up. For example, it might send resources that the browser already has in its cache. With HTTP/1.1 the browser knew what he had in its cache, and only then it requested the rest from the server.

By it's nature, HTTP/2 is not meant to be groundbreaking but merely an improvement for the obsolete HTTP/1.1. HTTP/2 must be backward compatible with HTTP/1.1 which makes it not as modern and innovative as it could be. For example, HTTP/1.1 introduced Cookies as the solution for storing user details in order to customize and improve the UX for them. However, cookies are a great vulnerability as hackers can get a lot of information about users just from the data stored in them. HTTP/2 still uses Cookies as HTTP/1.1's successor.

While HTTP/2 is still relatively young and not yet commonly used, support for it continues to grow. Most major browsers support HTTP/2 including Chrome, Chrome for Android, Firefox, Safari, and Edge. The prominent web servers support HTTP/2, including Apache Server, NGINX, and Tomcat.

There's plenty of debate around HTTP/2 about whether it's actually faster than HTTP/1.1 or not, and whether it suits smaller websites as well as the larger ones, however as there is no better alternative at the moment, or even in the near future, it seems that the more HTTP/2 will be supported by software and webmasters, the more its popularity will continue to grow.

As a result, developers will need to learn how to adjust to the HTTP/2 ways and lose old habits they gained while trying to workaround HTTP/1.1's weaknesses. Practices like merging multiple images into one large file, aka Spriting, resources concatenation, and Domain Sharding for increasing the number of multiple parallel downloads will no longer be needed. In addition, load testing tools like [Apache JMeter](http://jmeter.apache.org/)™ will need to develop plugins for performance testing websites that communicate over HTTP/2. The future will be interesting.

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190138&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190138&u=https%3A%2F%2Fwww.wakanda.io%2F).
