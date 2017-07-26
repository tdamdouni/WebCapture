# Full Speed Ahead with HTTP/2 on Google Cloud Platform

_Captured: 2015-10-08 at 22:13 from [googlecloudplatform.blogspot.de](http://googlecloudplatform.blogspot.de/2015/10/Full-Speed-Ahead-with-HTTP2-on-Google-Cloud-Platform.html?m=1)_

Performance is a feature. For many Google applications it is the featurethat makes everything else possible--instant text and voice search, directions, translations, and more. The platforms and infrastructure teams at Google are always on the leading edge of development and deployment of new performance best practices. These best practices, in turn, benefit your applications running on Google Cloud Platform.

One great example of Cloud Platform leveraging technology improvements in the Google infrastructure is support for SPDY and HTTP/2. The Google Chrome team began [experimenting with SPDY](https://www.chromium.org/spdy/spdy-whitepaper) back in 2009 and Google servers were the first to support it. SPDY proved to deliver [significant performance benefits](http://blog.chromium.org/2013/11/making-web-faster-with-spdy-and-http2.html) and helped shape the development of the HTTP/2 protocol. Now, with HTTP/2 finalized ([RFC 7540](https://httpwg.github.io/specs/rfc7540.html), [RFC 7541](https://httpwg.github.io/specs/rfc7541.html)) and [rapidly gaining client adoption](http://caniuse.com/#feat=http2), Google servers are, once again, leading the way by being among the first to offer full HTTP/2 support.

**HTTP/2 on Google Cloud Platform**

We're not breaking any news here, because Google Cloud Platform support for SPDY has been enabled for many years, and support for its successor (HTTP/2) was enabled earlier this year. Many performance-conscious developers are already leveraging the performance benefits of the HTTP/2 protocol in their applications, and so should you! Here's what you need to know:

  1. Your application must run over HTTPS. Support for the HTTP/2 protocol is automatically negotiated as part of the TLS handshake [via ALPN](http://chimera.labs.oreilly.com/books/1230000000545/ch04.html#ALPN). 
  2. The server terminating the secure HTTPS connection must support ALPN and HTTP/2 protocols. If either side does not support the new HTTP/2 protocol then they fallback to HTTP/1.1. 

If your application is already running over HTTPS, and the secure session is terminated by one of Google servers, then--good news--you're already HTTP/2 enabled! Let's take a peek under the hood to see how this works.

![HTTP-2 Flowchart - Remove Server Push \(v3\).png](https://lh6.googleusercontent.com/_MqiZGNZEwlbAHydUOtMDvbe7IDYD6C5XmxDPZY1G9pEMgWOijoNlvs74KEPUmKmbWL2od3enQ36lSFgI_OD_JAmMdXN1iy_vXDVEskkjVSZljENzYEduaK9CQ9T3Mzk=s1600)

Google Cloud Storage

Consider a scenario in which you upload a file into [Google Cloud Storage](https://cloud.google.com/storage/) and get an HTTPS link for the resource, which you then reference or share with others. When the resource is fetched, the client and Google server negotiate the TLS session and HTTP/2 protocol support. If the client supports HTTP/2 then the Google servers automatically selects it; otherwise the Google servers fallback to HTTP/1.1. In short, just upload a file and provide an HTTPS link to it and your job is done.

Google App Engine

Both in its original incarnation and Managed VM configurations, [Google App Engine](https://cloud.google.com/appengine/docs) servers are responsible for negotiating and terminating the TLS tunnel. As long as your application is being served over HTTPS, the Google servers automatically negotiate HTTP/2 on your behalf.

Each HTTP/2 stream is then translated into an HTTP/1.1 request and routed to your application. As a result, no modifications are required within your application to enable HTTP/2. Simply direct your traffic through HTTPS and all capable visitors will be automatically served over HTTP/2.

If you're running a virtual machine, or an entire cluster, via [Google Compute Engine](https://cloud.google.com/compute/) or [Google Container Engine](https://cloud.google.com/container-engine/), then you have multiple options for where and how the inbound connections are routed:

  1. You can expose the virtual instance directly, in which case you must set up and manage the necessary infrastructure to terminate the TLS tunnel, negotiate HTTP/2, and process the HTTP/2 session--see the [HTTP/2 wiki for a list of open source servers](https://github.com/http2/http2-spec/wiki/Implementations). 
  2. You can use a [network load balancer](https://cloud.google.com/compute/docs/load-balancing/network/) to distribute inbound TCP connections to one of multiple servers, which then have to terminate the TLS tunnel and negotiate HTTP/2--the same as with exposing the virtual instance directly. 
  3. You can use an [HTTPS load balancer](https://cloud.google.com/compute/docs/load-balancing/http/), which terminates the TLS tunnel and negotiate HTTP/2 on your behalf. The load balancer translates inbound HTTP/2 streams into HTTP/1.1 requests and forwards them to one of your servers--same as Google App Engine. This is the quickest and easiest way to enable HTTP/2 for your Compute/Container-powered application. 

There shouldn't be any surprises with any of the above. To enable HTTP/2, you need to enable HTTPS, and then either let one of the Google servers terminate it and do all the heavy lifting on your behalf, or route the connection to one of your HTTP/2 capable servers.

Note: There is much more to be said about the benefits and optimization strategies for HTTP/2--it's a big and important upgrade--but that's outside of scope of this post. If you're curious, however, check out the free chapters on [HTTP/2](http://chimera.labs.oreilly.com/books/1230000000545/ch12.html) and [HTTP/2 optimization strategies](http://chimera.labs.oreilly.com/books/1230000000545/ch13.html) in High Performance Browser Networking (O'Reilly).

##  A QUIC peek into the future

##  The Google Chrome and platform teams continue to innovate by experimenting with QUIC, a [UDP-based transport for HTTP/2](http://blog.chromium.org/2015/04/a-quic-update-on-googles-experimental.html), which enables faster 0-RTT secure handshakes, improved congestion control, loss recovery, and other mechanisms that promise to further improve performance:

The data shows that 75% percent of connections can take advantage of QUIC's zero-round-trip feature. QUIC outshines TCP under poor network conditions, shaving a full second off the Google Search page load time for the slowest 1% of connections. These benefits are even more apparent for video services like YouTube. Users report 30% fewer rebuffers when watching videos over QUIC. This means less time spent staring at the spinner and more time watching videos. - from [A QUIC update on Google's experimental transport](http://blog.chromium.org/2015/04/a-quic-update-on-googles-experimental.html)

And speaking of being on the leading edge of performance--Many applications powered by App Engine are already speaking QUIC to capable Chrome clients, and we're hard at work to bring QUIC to all other products as well. As with HTTP/2, the Google servers terminate the UDP flow and translate the QUIC protocol to HTTP/1.1 requests, enabling a transparent performance upgrade to millions of existing applications running on Google Cloud Platform.

Tip: To quickly and easily see what protocol is negotiated, install the [HTTP/2 indicator extension](https://chrome.google.com/webstore/detail/http2-and-spdy-indicator/mpbpobfflnpcgagjijhmgnchggcjblin?hl=en) for Google Chrome. A blue bolt indicates HTTP/2; a red bolt indicates QUIC.
