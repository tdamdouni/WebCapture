# The HTTP Series (Part 1): Overview of the Basic Concepts

_Captured: 2017-08-15 at 19:29 from [dzone.com](https://dzone.com/articles/the-http-series-part-1-overview-of-the-basic-conce)_

In this article, I will present you the basics of HTTP.

## But Why HTTP?

You may be asking yourself, why should I read about HTTP?

Well, if you are a software developer, you will understand how to write better applications by learning how they communicate. If you are system architect or network admin, you will get deeper knowledge on designing complicated network architectures.

REST, which is very important architectural style nowadays, completely relies upon utilizing HTTP features, so that makes HTTP even more important to understand. If you want to make great [RESTful applications](https://www.vegaitsourcing.rs/media-center/blog/2015/04/hypermedia-driven-restful-web-apis/), you must understand HTTP first.

So are you willing to pass on the chance to understand and learn the fundamental concepts behind the World Wide Web and network communications?

I hope not!

The focus of the article will be on explaining the most important parts of HTTP as simply as humanly possible. The idea is to organize all the useful information about HTTP in one place, to save you the time of going through books and RFCs to find the information you need.

This is the first article of the [HTTP series](https://www.code-maze.com/http-series/). It will give you a short introduction of the most important concepts of the HTTP.

  * **The HTTP series (Part 1): Overview of the basic concepts **
  * The HTTP series (Part 5): Security

Without further ado, let's dive in.

## HTTP Definition

The founder of HTTP is [Tim Berners-Lee](https://en.wikipedia.org/wiki/Tim_Berners-Lee) (the guy also considered to be the inventor of the World Wide Web). Among other names important to the development of the HTTP is [Roy Fielding](https://en.wikipedia.org/wiki/Roy_Fielding), who is also the originator of the REST architectural style.

**The Hypertext Transfer Protocol** is the protocol that applications use to communicate with each other. In essence, HTTP is in charge of delegating all of the internet's media files between clients and servers. That includes HTML, images, text files, movies, and everything in between. And it does this quickly and reliably.

HTTP is the **application protocol** and not the transport protocol because it is used for the communication in the application layer. To jog your memory here is what the Network Stack looks like.

![Network stack](http://www.code-maze.com/wp-content/uploads/2017/06/Network-stack.png)

From this image, you can clearly see the that the HTTP is the application protocol and that TCP works on the transport layer.

## Resources

## ![resource](http://www.code-maze.com/wp-content/uploads/2017/06/resource-1024x475.jpg)

Everything on the internet is a resource, and HTTP works with resources. That includes files, streams, services, and everything else. An HTML page is a resource, a Youtube video is a resource, your spreadsheet of daily tasks on a web application is a resource… you get the point.

And how do you differentiate one resource from another?

By giving them URLs (Uniform resource locators).

A URL points to the unique location where your browser can find the resource.

## How the Messages Are Exchanged Between Web Client and Web Server

Every piece of content, every resource lives on some web server (HTTP server). These servers are expecting an HTTP request to provide those resources.

But how do you request a resource from a web server?

You need an HTTP client, of course!

You are using an HTTP client right now to read this article. Web browsers are HTTP clients. They communicate with HTTP servers to retrieve the resources to your computer. Some of the most popular clients are Google's Chrome, Mozilla's Firefox, Opera, Apple's Safari, and, unfortunately, the still infamous Internet Explorer.

## Messages and Some Message Examples

So what does the HTTP message look like?

Without talking too much about it, here are some examples of HTTP messages:

**GET Request**

**POST Request**

Here is the example of one GET and one POST request. Let's go quickly through the different parts of these requests.

The first line of the request is reserved for the **request line.** It consists of a **[request method**](http://www.code-maze.com/the-http-reference/#requestmethods) name**, request URI, **and** HTTP version.**

The next few lines represent the [request headers](http://www.code-maze.com/the-http-reference#headers). Request headers provide additional info to the requests, like the content types the request expects in response, authorization information, etc.

For the GET request, the story ends right there. A POST request can also have a body and carry additional info in the form of a body message. In this case, it is a JSON message with additional info on how the GitHub webhook should be created for the given repo specified in the URI. That message is required for the webhook creation so we are using a POST request to provide that information to the GitHub API.

The request line and request headers must be followed by <CR><LF> (carriage return and line feed \r\n), and there is a single empty line between message headers and message body that contains only CRLF.

[Reference](https://www.w3.org/Protocols/rfc2616/rfc2616-sec5.html) for HTTP requests.

And what do we get as a response to these requests?

**Response Message**

The response message is pretty much structured the same as the request, except the first line that is called is the **status line,** which surprising as it is, carries information about the [response status](http://www.code-maze.com/the-http-reference#statuscodes).

The status line is followed by the **response headers** and **response body**.

[Reference](https://www.w3.org/Protocols/rfc2616/rfc2616-sec6.html) for HTTP response.

## MIME Types

MIME types are used as a standardized way to describe the file types on the internet. Your browser has a list of MIME types and the same goes for web servers. That way files can be transferred the same way regardless of the operating system.

A fun fact is that MIME stands for Multipurpose Internet Mail Extension because they were originally developed for multimedia emails. They have been since adapted to be used for HTTP and several other protocols.

Every MIME type consists of a **type**,** subtype**, and a list of **optional parameters **in the following format: **type/subtype; optional parameters.**

Here are a few examples:

You can find the list of commonly used MIME types and subtypes in the [HTTP reference](http://www.code-maze.com/the-http-reference/#mimetypes).

## Request Methods

HTTP request methods (also referred to as "verbs") define the action that will be performed on the resource. [HTTP defines several request methods](http://www.code-maze.com/the-http-reference#requestmethods) of which the most commonly known/used are **GET** and **POST** methods.

A request method can be idempotent or not idempotent. This is just a fancy term for explaining whether the method is safe/unsafe to be called several times from the same resources. In other words, that means that the GET method, that has the sole purpose of retrieving information, should by default be idempotent. Calling GET on the same resource over and over should not result with a different response. On the other hand, the POST method is not an idempotent method.

Prior to HTTP/1.1, there were just three methods: GET, POST, and HEAD, and the specification of the HTTP/1.1 brought a few more in the play: OPTIONS, PUT, DELETE, TRACE, and CONNECT.

Find out more about each one of these methods does in the [HTTP Reference](http://www.code-maze.com/the-http-reference#requestmethods).

## Headers

Header fields are colon-separated name-value fields that you can find just after the first line of a request or response message. They provide more context to the HTTP messages and ensure clients and servers are appropriately informed about the nature of the request or response.

There are five types of headers in total:

  * **General Headers: **These headers are useful to both server and client. One good example is the Date header field which provides the information about the time of the message creation.
  * **Request Headers: **Specific to the request messages. They provide the server with additional information. For example, Accept: */* header field informs the server that the client is willing to receive any media type.
  * **Response Headers: **Specific to the response messages. They provide the client with additional information. For example, the Allow: GET, HEAD, PUT header field informs the client which methods are allowed for the requested resource.
  * **Entity Headers: **These headers deal with entity body. For example, Content-Type: text/html header lets the application know that the data is an HTML document.
  * **Extension Headers: **These are nonstandard headers constructed by application developers. They are not the part of HTTP but need to be tolerated.

You can find the list of commonly used request and response headers in the [HTTP Reference](http://www.code-maze.com/the-http-reference#headers).

## Status Codes

![404batman](http://www.code-maze.com/wp-content/uploads/2017/06/tumblr_ntqxdoCovo1udik9co2_1280-1024x683.jpg)

The **status code** is a three digit number that denotes the result of a request. It is followed by the **reason phrase** which is a humanly readable status code explanation.

Some examples include:

  * 200 OK
  * 404 Not Found
  * 500 Internal Server Error

The status codes are classified into five different groups.

Both status code classification and the entire list of status codes and their meanings can be found in the [HTTP Reference](http://www.code-maze.com/the-http-reference#statuscodes).

## Conclusion

Phew, that was a lot of information.

The knowledge you gain by learning HTTP is not the kind that helps you to solve some problem directly. But it gives you the understanding the underlying principles of internet communication which you can apply to almost every other problem on a higher level than HTTP. Whether it is REST, APIs, web application development, or networks, you can now be at least a bit more confident while solving these kinds of problems.

Of course, HTTP is a pretty large topic to talk about and there is still a lot more to it than the basic concepts.

Read about the architectural aspects of HTTP in the [part 2](https://www.code-maze.com/http-series-part-2/) of the [HTTP series](https://www.code-maze.com/http-series/).

Was this article helpful to you? Please leave the comment and let me know.
