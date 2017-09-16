# Web Performance 101: HTTP Headers

_Captured: 2017-09-15 at 19:39 from [dzone.com](https://dzone.com/articles/web-performance-101-http-headers?edition=326496&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-09-15)_

Hypertext Transfer Protocol, or HTTP, was first introduced by Tim Berners-Lee in 1991. The initial version HTTP/0.9 was designed to facilitate data transfers between a client and server. The protocol works on a request-response model over a TCP connection, but it's evolved over the years to include several improvements and advanced features. The latest version is HTTP/2, which has introduced major advancements that prioritize web page performance and speed.

![Image title](http://blog.catchpoint.com/wp-content/uploads/2017/09/header1.png)

This article discusses an important component of the HTTP model - headers. Before you continue, [read this detailed blog post to understand how HTTP works](http://blog.catchpoint.com/2016/08/19/revisiting-anatomy-http-part/).

### **What Are HTTP Headers?**

There are three main components that make up the request/response structure. This includes:

  * Start line
  * Headers
  * Body/Content
![Image title](http://blog.catchpoint.com/wp-content/uploads/2017/09/header6.jpg)

Based on the type of the HTTP message, the start line includes the method, path, status code, and protocol version. The HTTP headers are added next and defined as name-value pairs separated by a colon. These headers are used to send additional parameters along with the request or response. The body of the message will include the data to be sent with the request or the data received along with the response.

There are different types of headers and we can group these based on its usage into 4 broad categories:

  * General header
  * Request header
  * Response header
  * Entity header
![Image title](http://blog.catchpoint.com/wp-content/uploads/2017/09/header7.jpg)

### 1\. General Headers

Headers that can be used in both requests and response messages and that are independent of the data being exchanged. Some of the common general headers include:

#### **1.1 Cache-Control**

Cache-Control is a general header type that can be used to specify caching preference during the response-request cycle. The directives specified in the header must be strictly implemented when caching by the client and server.

For example, to cache a static file on a web page, you can define the header using the format below:

![Image title](http://blog.catchpoint.com/wp-content/uploads/2017/09/header8.jpg)

  * **max-stale:** Client accepts expired content and allows you to configure response's expire time in seconds.
  * **max-age:** Specifies the maximum time for which a resource is considered fresh.
  * **min-fresh:** Client expects a response that's fresh for at least the specified number of seconds.
  * **no-cache:** The server must validate the cache content before sending it to a client.
  * **no-store:** The cache is not allowed to store the request and response data.
  * **no-transform:** The cache should not transform the stored content. For example, changing the image format to save space.
  * **only-if-cached:** The client requires only cached content and the request does not check with the origin server for fresh content.
  * **must-revalidate:** The fetched resource must be validated to ensure it is not stale.
  * **public:** The response can be cached anywhere - private or shared cache.
  * **private:** The response must be stored in private cache; shared caching is not allowed.
  * **proxy-revalidate:** Applies to shared caches, the response must be validated for freshness.

There are a few other header directives that are not part of the HTTP caching standards. These are called Extension Cache-Control directives; immutable is an example. The immutable directive indicates that the response body will remain unchanged so the client need not validate the content again.

#### **1.2 Connection**

The Connection header specifies if the HTTP connection should remain open once the data exchange has completed. It sets up a persistent connection, which can be reused by subsequent requests.

To keep the connection open, the header is sent in the following format:

The header directives include:

  * **Keep-alive: **The connection is persistent and once established, it remains open for all subsequent requests.
  * **Close: **This value instructs the client or server to close the connection.

#### **1.3 Transfer-Encoding**

Transfer-Encoding specifies the format or encoding to be used when transferring the content in the body of the message. For example, to indicate the file should be compressed, the header is sent in the following format:

You can also specify multiple encoding formats separated by a comma. The directives for this header include:

  * **chunked: **The content is split into chunks before transferring it to the client or server.
  * **deflate:** The content is compressed using deflate compression algorithm.
  * **gzip:** This is another compression format based on the UNIX gzip program.
  * **identity:** Indicates the content doesn't need compression or modification.

### **2\. Request Header**

These headers define parameters for the data requested or parameters that give important information about the client making the request. Some of the common request headers include:

#### 2.1 Accept-Encoding

This request header specifies the encoding that the client supports. For example, to indicate the client understands multiple encoding, the header format will be:

The values accepted by the header are:

  * gzip
  * compress
  * deflate
  * br (Brotli algorithm)
  * identity
  * * (default header value)
  * ;q= (q values weighting)

#### 2.2 If-Match

The If-Match request header indicates a conditional request. The header returns the requested response only if it matches the ETag (a unique identifier for a resource) or list of ETag values specified in the header.

For example, to return a resource from the server that has any of the following ETags, the header will be in the following format (where "W/" indicates a weak ETag value that may not match byte for byte).

#### **2.3 If-Modified-Since**

The header is another conditional request. The server will return the requested resource only if it has been modified after the specified date. If-Modified-Since is used only with a GET or HEAD request. For example, to return a request that was modified after October 1, the header is sent in this format:

The request header accepts the following values in the date parameter:

#### 2.4 Range

The Range header specifies the part of the document/resource to be returned. It can be used to request partial content split into different ranges or just a single section of the content. For example, to get the data between a specific number of bytes, the header format will be:

To request from multiple parts of the same content, the header should be in the following format:

#### 2.5 User-Agent

The User-Agent request header provides details about the client application including the software version, application type, operating system, etc. The common user-agent header request will be in the following format:

Here is an example of a FireFox user agent string:

### **3\. Response Header**

These headers contain information about the incoming response. Some of the common response headers are:

#### 3.1 Accept-Ranges

This response header lets the client know that the server supports range requests. The header value specifies the unit of the range value. For example, if the range request is sent in bytes then the header format will be:

#### 3.2 ETag

ETag is a unique identifier for the requested resource. It makes it easy to identify the version of a cached resource and helps to keep track of updates made to the resource. An ETag generated for an image on the web page will be sent along with other response header format:

For example:

#### 3.3 Location

The Location response header indicates a page redirect and is sent along with a 3xx status response. It specifies a URL to which the page redirects. The header format is as follows:

#### 3.4 Vary

This response header specifies the set of request header values to determine whether the cached resource that was requested should be revalidated. For example: to serve the mobile version of a cached resource, we can use the following Vary header value so that it checks the User-Agent header before serving the resource.

### **4\. Entity Header **

The entity headers describe the content that makes up the body of the message. Some of the common entity headers are:

#### 4.1 Allow

The Allow entity header is used to list the methods that are accepted by the requested resource. For example, the following header values specify that the HTTP methods that are relevant to the resource.

#### 4.2 Content-Encoding

The entity header indicates the type of encoding that was used in the message body. The header is sent in the following format:

Multiple encoding types can be listed in the same header:

#### 4.3 Content-Length

This header specifies the size of the entity or the message body. The header format is:

For example:

Here the length is in decimals of octets.

#### 4.4 Expires

The Expires header indicated the date and time for which the resource may be considered fresh. For example, if a resource is stale after 10th October, then the header will be:
