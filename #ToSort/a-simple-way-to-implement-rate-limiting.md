# A Simple Way to Implement Rate Limiting

_Captured: 2017-03-15 at 22:10 from [dzone.com](https://dzone.com/articles/a-simple-way-to-implement-rate-limiting?edition=283883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-15)_

With the advent of APIs and its growth inside organizations, rate limiting has become an important functionality.

Let's start this article with a question: Why do enterprises need to implement rate limiting in their applications?

Before we heard about API (Application Programming Interface) and before its growth inside organizations, one of the main reasons to implement rate limiting was to defend applications against DoS (Denial of Service) attacks. These applications could apply policies to limit traffic coming from specific sources, specific customers, IP addresses, and so forth.

Nowadays, with the advent of API and its increasing popularity, API management has emerged. Thereby, rate limiting has been replaced by throttling.

According to Wikipedia:

> API management is the process of creating and publishing APIs, enforcing their usage policies, controlling access, nurturing the subscriber community, and collecting and analyzing usage statistics. 

API management allows enterprises to monetize their APIs through throttling (rate limiting) by controlling API usage. For example, a specific customer has the right to access the API (its resources) only 100 times or requests per day. If the customer wants more accesses, he or she must pay more for that.

There are a lot of companies providing API management in the market. This API management usually has a throttling functionality embedded among others. The idea in this article is not to reinvent the wheel, but to show you a simple way to implement rate limiting (or, if you prefer, throttling) and to see how things work in the background.

To do so, we will use the following technologies:

  * Java.
  * Memcached (server and client).

## **The Example**

Imagine that DZone releases an API that allows its customers to retrieve articles. They will register into the DZone API. However, the DZone API allows them to retrieve just five articles per day per customer, limiting their access.

Get the Memcached connection:
    
    
    MemcachedClient memcacheClient = new MemcachedClient(new InetSocketAddress("localhost", 11211));

Get the counter information into Memcached. Set it if it is not stored yet:
    
    
          memcacheClient.set(customerLogin, EXPIRED_SECONDS, String.valueOf(ALLOW_ARTICLE -1));

If the counter information is zero, throw an exception:

Decrement the counter information into Memcached:

## **Summary**

Memcached has many commands -- but it has one, called `decr`, that is the core of this solution. Probably, this simple solution could meet most of the enterprises' applications or APIs needs. There are two points to observe. First, parallel requests in applications or APIs could grant exceeded access. Second, as Memcached is an in-memory key-value store, the counter information could be lost when the Memcached server restarts, and it could grant exceeded access, too. Depending on the business's flexibility, some exceeded access is not a problem.
