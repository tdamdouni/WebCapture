# The Three HTTP Routing Patterns You Should Know

_Captured: 2018-05-30 at 18:18 from [dzone.com](https://dzone.com/articles/the-three-http-routing-patterns-you-should-know?edition=379204&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-05-29)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

HTTP is the de-facto application transport layer. The majority of applications and APIs today are delivered via HTTP, regardless of their content (HTML, JSON, XML).

![app stats](https://devcentral.f5.com/Portals/0/Users/038/38/38/app_stats_thumb.jpg?ver=2018-04-06-080322-110)

> _app stats_

That means most of the scaling going on is focused on scaling HTTP-based apps. In fact, when I peek at our latest data from nearly 4 million virtual servers, 63% of them are HTTP/S. In [MuleSoft's latest Connectivity Benchmark,](https://www.mulesoft.com/lp/reports/connectivity-benchmark) respondents reported an average of 1020 applications in their enterprise environments. Even if only 63% are HTTP/S, that's still a lot of HTTP -- with not a lot of IP space to give it.

Most organizations aren't lucky enough to own significant ranges of publicly accessible IP addresses. That's one of the reasons why "virtual servers" exist in the realm of web serving, so that a single IP address can service multiple servers (or applications).

Host-based (virtual) routing has been a go-to for the Internet for years. And though it's the most commonly used (and best known) type of HTTP routing, there are actually three types of HTTP routing NetOps should get familiar with. That's because increasingly the world of applications is clashing with that of the network, and many of the deployment patterns being used by DevOps rely on HTTP-based routing capabilities.

### **1\. Host-Based**

The old standard. Host-based routing is what enables virtual servers on web servers. It's also used by application services like load balancing and ingress controllers to achieve the same thing. One IP address, many hosts.

Host-based routing allows you to send a request for **api.example.com **and for **web.example.com **to the same endpoint with the certainty it will be delivered to the correct back-end application.

### **2\. Path-Based**

Increasingly common - particularly in the realm of scaling containers using ingress controllers - is path-based routing. Path-based routing requires visibility into the URI portion of an HTTP request.

![http path](https://devcentral.f5.com/Portals/0/Users/038/38/38/http_path_thumb.jpg?ver=2018-04-06-080326-047)

> _http path_

You can route based on the entire path (not advisable) or a portion of the path. For example, you could search for** /getprofile** in this path and route it to one application while routing all others to a different application. You can also search for **/v1** in the path and use it to implement a type of API versioning.

Because of the focus on API-only communication in modern apps (like mobile) and architectures (like microservices), the use of path-based routing is increasingly important to enabling not only scale but simple delivery. When everything you need to know is found in the URI (in the path), it becomes imperative that you can dissect that path into its composite pieces and make decisions on where that request needs to go.

### **3\. Header-Based**

Header-based is a broad category that includes some familiar routing patterns such as persistence (sticky sessions). Header-based routing simply means that you use an arbitrary HTTP header as the basis for determining how to route a request. This might be a standard header, like _content-type or cookie, _or it might be a custom header, like _x-custom-header-for-my-app._

The use of HTTP headers to route requests is a long-standing tradition of sorts. The concept of [sticky sessions (persistence)](https://f5.com/resources/white-papers/cookies-sessions-and-persistence) is based on the use of Cookies to aid in scaling stateful applications. It's also instrumental in maintaining secure sessions (SSL/TLS).

Note that Header-based is usually separated from host-based routing even though the host is technically one of the many HTTP headers. Many systems were able to perform host-based routing but not general header-based routing, though today it is hard to find a load balancer/proxy that cannot support routing based on any header.

Despite the apparent simplicity of these routing patterns, their importance should not be underestimated. API Gateways, web application firewalls ([particularly inspection capabilities](https://f5.com/about-us/blog/articles/how-does-a-waf-mitigate-vulnerabilities-28915)), [ingress controllers](https://f5.com/about-us/blog/articles/ingress-controllers-new-name-familiar-function-27388), and a robust set of other application services rely on being able to route based on this information.

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

Topics:

http ,routing ,traffic ,patterns ,host ,path ,headers ,api gateway ,firewalls ,cloud
