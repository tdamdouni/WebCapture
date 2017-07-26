# Frontcache: Cache for Dynamic Pages

_Captured: 2017-05-08 at 10:44 from [dzone.com](https://dzone.com/articles/frontcache-cache-for-dynamic-pages?edition=298008&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-07)_

A lot of applications use Content Delivery Network [CDN] for static content (images, CSS, JS, etc). It really makes your site faster and reduces the load on your servers a lot.

A similar approach can work for dynamic pages as well: static parts of the page are cached, so dynamic parts of the page hit servers only. It can speed up your website a lot and reduce backend load times! It's something [Frontcache](http://www.frontcache.io/) is designed for.

![Page structure example](https://dzone.com/storage/temp/5122380-page-parts-2.png)

> _Page structure example_

For example for 'Product details' page cart and recommendation parts are dynamic only, so the rest part of the page can be cached.

Another good catch is that Frontcache returns a single response for the browser. No need to handle multiple RESTful calls with fancy JavaScript and debug it for different browsers' versions.

Frontcache differentiates between HTTP requests from users versus those from bots (Googlebot, Bingbot, Baiduspider, etc). So, the same 'Product details' page can be handled entirely from the cache for bots but has dynamic data for customers.

And it's really easy to integrate, regardless of the programming language you use (Java, PHP, .Net, etc). It can be used as a standalone edge in a corporate network or as servlet filter (for Java-based websites) or as a distributed cluster of edges similar to CDN networks.

## **Some Use Cases**

**Scale legacy systems for larger traffic load** (including loads from bots). Legacy systems are very sensitive to the amount of concurrent traffic. A little bit higher traffic rate during hot hours can slow down the whole system a lot (even move it out of service). With Frontcache, legacy systems can be scaled up by a dozen times with minimal code change.

**Cache 'heavy' backend requests** (e.g. report generation). For example, the system generates documents in PDF format and it takes a couple seconds to complete the request. Impatient operators want to get the page faster and refresh it a couple more times - but this will slow down the whole system a lot (even move it out of service). Frontcache is designed to shield such sensitive components with fault tolerance tuning and short time caching.

**Increase website performance without frontend development overhead.** Nowadays, to speed up page download times, the following approach is used: after the page is loaded, multiple JavaScript/RESTtful calls make up a page's content. The downside of such an approach is that it support multiple browsers with different versions which leads to bugs and extra development/support. With Frontcache, the same dynamic page can be loaded fast in a single response (without extra complexity with JavaScript/RESTful calls).

Sounds like your case? There are '[Getting Started](https://github.com/eternita/frontcache/wiki/Getting-Started)' article and [code samples](https://github.com/eternita/frontcache/tree/master/examples) on Github.

## **How it Works**

General request processing overview:  
A request is checked in the cache. If no data is in the cache - hit the origin.  
The response is checked for SSI (server side includes). When a response has been included - they are resolved from the cache/origin.  
Completed response is sent back to the client.

![Frontcache overview](https://dzone.com/storage/temp/5122381-how-it-works-overview.png)

> _Frontcache overview_

**Pages for the example above have the following markup:**

![Page includes](https://dzone.com/storage/temp/5122383-how-it-works-pages-urls.png)

> _Page includes_

## **Fun Demo**

[www.coinshome.net](http://www.coinshome.net) uses Frontcache and posts [real-time statistics online](http://www.frontcache.io/coinshome.net-real-time-demo).   
It's fun to create load and check how it's handled in real time:

1\. Download the sitemap from <https://www.coinshome.net/export/sitemap.txt>

2\. Create a crawler - as an example, I've included the following bash script (crawler.sh):

3\. Run the crawler.

[Check how it works online](http://www.frontcache.io/coinshome.net-real-time-demo).

Notice:

\- Pages have a 'recent updates' section with frequently changed content.  
\- The 'logs to headers' feature is enabled and response headers have to trace how the page was assembled.

![page assemble logs](https://dzone.com/storage/temp/5142703-screen-shot-2017-05-01-at-114707-am.png)

> _page assemble logs_

### **Cheat Sheet With Features/Key Points**

  * Page fragment cache.

  * User agent specific caching (user vs bot).

  * Written in Java, and works with any language (Java, PHP, .Net, etc).

  * Fault tolerance management (based on Netflix Hystrix).

  * Advanced error handling with fallback configurations for URL patterns.

  * Advanced web based console for configs and real-time monitoring.
