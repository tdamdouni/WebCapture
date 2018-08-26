# RESTful Architecture 101

_Captured: 2018-08-04 at 10:39 from [dzone.com](https://dzone.com/articles/restful-architecture-101?edition=388195&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-03)_

**[The State of API Integration 2018](https://dzone.com/go?i=285436&u=https%3A%2F%2Foffers.cloud-elements.com%2Fthe-state-of-api-integrations-report-2018%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_content%3Dpre-roll): Get Cloud Elements' report for the most comprehensive breakdown of the API integration industry's past, present, and future.**

The Representational State Transfer (REST) architectural style is not a technology you can purchase or a library you can add to your software development project. [REST](https://blog.cloud-elements.com/the-beauty-of-rest-apis) is a worldview that elevates information into a first-class element of the architectures we build.

The ideas and terms used to describe "RESTful" systems were introduced and collated in Dr. Roy Fielding's thesis, "Architectural Styles and the Design of Network-based Software Architectures." This an [academic document](https://www.ics.uci.edu/~fielding/pubs/dissertation/fielding_dissertation.pdf), but is comprehensible and convenient by providing the basis of RESTful architecture.

The summary of the approach is that by making specific architectural choices, we can obtain desirable properties from the systems we create. The constraints detailed in this architectural style are widely applicable, however, they are not intended to be used universally.

## **Great, but What Is It?**

![](https://blog.cloud-elements.com/hubfs/Rest-101-GEN-1.png?t=1532984102890)

What does Representational State Transfer mean? Transferring, accessing and manipulating textual data representations, in a stateless manner. When deployed correctly, it provides a uniform, interoperability, between different applications on the internet. The term stateless is a crucial piece to this as it allows applications to communicate agnostically.

A RESTful API service is exposed through a Uniform Resource Locator (URL). This logical name separates the identity of the resource from what is accepted or returned. The URL scheme is defined in RFC 1738, [which can be found here](https://www.ietf.org/rfc/rfc1738.txt).

A RESTful URL must have the capability of being created, requested, updated, or deleted. This sequence of actions is commonly referred to as CRUD. To request and retrieve the resource, a client would issue a Hypertext Transfer Protocol (HTTP) GET request. This is the most common request and is executed every time you type a URL into a browser and hit return, select a bookmark, or click through an anchor reference link.

For programmatic interaction with a RESTful API, any of a dozen or more client-side APIs or tools can be used. To use the curl command line tool, you could type something similar to:

$ curl <http://cloud-elements.com/elements-catalog/>

This will return the default representation on the command line, however, you may not want the information in this form. Fortunately, HTTP has a built-in mechanism to filter and return information in a different format. If the server supports an "Accept" representation, you are able to specify this in the header and the information in this format. This is known as content negotiation and is one of the more underused aspects of HTTP. This ability to ask for information in different forms is possible because of the separation of the name of the resource from its form. Although the 'R' in REST is 'representation', not 'resource', this should be kept in mind when building systems that allow clients to ask for information in the forms they want.

An important aspect of a RESTful request is that each request contains enough state to answer the request. This allows for visibility and statelessness on the server, desirable properties for scaling systems up, and identifying what requests are being made. This state also enables the caching of specific results. The combination of a server's address and the state of the request, combine to form a computational hash key into a result set.

The GET request allows a client to make very specific requests, but only when necessary. The client can cache a result locally, the server can cache a result remotely or some intermediate architectural element can cache a result in the middle. This is an application-independent property that can be designed into our systems.

Just because it is possible to manipulate a resource, doesn't mean everyone has the capability to do so. By putting a protection model in place that requires users to authenticate and prove that they are allowed to do something, before we give them permission.

## **What About SOAP?**

Plain and simple, [they are not the same thing](https://blog.cloud-elements.com/how-to-convert-soap-apis-to-rest-apis). Even though you can solve many architectural problems with either approach, they are not intended to be used interchangeably.

The confusion largely stems from the misunderstood idea that REST "is about invoking Web Services through URLs." This idea is far from the point of the functionalities of RESTful architecture. Without a deeper understanding of the larger picture that RESTful architecture achieves, it is easy to lose the intent of the practices.

REST is best used to manage systems by decoupling the information that is produced and consumed by the technologies that produce and consume it. We can achieve the architectural properties of:

  * Performance
  * Scalability
  * Generality
  * Simplicity
  * Modifiability
  * Extensibility

This is not to say SOAP-based systems cannot be built demonstrating some of these properties. SOAP is best leveraged when the lifecycle of a request cannot be maintained in the scope of a single transaction because of technological, organizational, or procedural complications.

## **Verbs**

![](https://blog.cloud-elements.com/hs-fs/hubfs/Rest-101-verbs-1.png?t=1532984102890&width=949&name=Rest-101-verbs-1.png)

[Verbs](https://blog.cloud-elements.com/http-verbs-demystified-patch-put-and-post) are the methods or actions that are available to interact with the resources on the server. The limited number of verbs in RESTful systems confuses and frustrates people new to the approach. What seems like arbitrary and unnecessary constraints, are in fact intended to encourage predictable behavior in non-application-specific ways. By explicitly and clearly defining the behavior of these verbs, clients can be self-empowered to make decisions in the face of network interruptions and failures.

There are four main HTTP verbs which are used by well-designed RESTful systems.

### GET

A GET request is the most common verb on the Web. A GET request transfers representations of named resources from a server to a client. Although the client does not necessarily know anything about the resource it is requesting, the request returns a byte stream tagged with metadata, indicating how the client should interpret the resource. This is typically represented on the web by "text/html" or "application/xhtml+xml". As we indicated above, the client can use content negotiation to be proactive about what is requested as long as the server supports it.

One of the key points about the GET request is that it should not modify anything on the server side. It is fundamentally a safe request.GET requests are also intended to be idempotent. This means that issuing a request more than once will have no consequences. This is a critical property in a distributed, network-based infrastructure. If a client is interrupted while it is making a GET request, it should be empowered to issue it again because of the idempotency of the verb.

In well-designed infrastructures, it doesn't matter what the client is requesting from which application. There will always be application-specific behavior, but the more we can push into non-application-specific behavior, the more resilient, accessible, and easier to maintain our systems will be.

### POST

A POST is used when the client cannot predict the identity of the resource that is requested to be created. When we hire people, place orders, submit forms, etc., we cannot predict how the server will name the resources we create. This is why we POST a representation of the resource to a handler (e.g. servlet). The server will accept the input, validate it, verify the user's credentials, etc. Upon successful processing, the server will return a 201 HTTP response code with a "Location" header indicating the location of the newly created resource.

Note: Some people treat POST like a conversational GET on creation requests. Instead of returning a 201, they return a 200 with the body of the resource created. This seems like a shortcut to avoid a second request, but it combines POST and GET functions while complicating the potential for caching the resource. Avoid the urge to take shortcuts at the expense of the larger picture. It seems worth it in the short-term, but over time, these shortcuts will add up and work against you.

### PUT

A client can issue a PUT request to a known URL as a means of passing the representation back to the server, in order to do an overwrite action. This distinction allows a PUT request to be idempotent in a way that POST updates are not.

If a client is in the process of issuing a PUT overwrite and it is interrupted, the client can issue a PUT again because an overwrite action can be reissued with no consequences; the client is attempting to control the state, so it can simply reissue the command.

Note: This protocol-level handling does not necessarily preclude the need for higher (application-level) transactional handling, it's an architecturally desirable property to bake in below the application level.

### DELETE

The DELETE verb is not widely used on the public Web (thankfully!), but for information spaces you control, it is a useful part of a resource's lifecycle.

DELETE requests are intended to be idempotent. A DELETE request may be interrupted by a network failure. Whether the request was successfully handled on the first request or not, the resource should respond with a 204 (No Content) response code. It may take some extra handling to keep track of previously deleted resources and resources that never existed (which should return a 404 response code). Some security policies may require you to return a 404 response code for non-existent and deleted resources to prevent leaking information about the presence of resources.

### HEAD

The HEAD verb is used to issue a request for a resource without actually retrieving the resource. It is a way for a client to check for the existence of a resource and possibly discover metadata about it.

### OPTIONS

The OPTIONS verb is also used to interrogate a server about a resource by asking what other verbs are applicable to the resource. This allows for developers to better understand how to interact and develop against resources.

### PATCH

The newest of the verbs, PATCH was only officially adopted as part of HTTP in 2010. The goal is to provide a standardized way to express partial updates. A PATCH request in a standard format allows an interaction to be more explicit about the intent.

If the client issues a PATCH request with an If-Match header, it is possible for this partial update to become idempotent. An interrupted request can be retried because, if it succeeded the first time, the If-Match header will differ from the new state. If they are the same, the original request was not handled and the PATCH can be applied.

## **Response Codes**

![](https://blog.cloud-elements.com/hubfs/Rest-101-Error.png?t=1532984102890)

[HTTP response codes](https://blog.cloud-elements.com/error-handling-restful-api-design-part-iii) give us a rich dialogue between clients and servers about the status of a request. Most people are only familiar with 200, 403, 404 and maybe 500 in a general sense, but there are many more useful codes to use. Each set of numbers can be categorized as the following:

1XX: Informational

2XX: Success

3XX: Redirection

4XX: Client Error

5XX: Server Error

There is more to learn in your RESTful journey, but hopefully, this REST 101 has illustrated some of the foundational aspects. Also, a better understanding when encountering other RESTful architectures in the wild.

Your API is not enough. Learn why (and how) leading SaaS providers are turning their products into platforms with API integration in the ebook, [Build Platforms, Not Products](https://dzone.com/go?i=263426&u=https%3A%2F%2Foffers.cloud-elements.com%2Fbuild-platforms-not-products-ebook%3Futm_campaign%3DPlaforms%25252C%252520Not%252520Products%252520eBook%26utm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_content%3Dtext) from Cloud Elements.

Topics:

integration ,rest ,soap ,api ,restful api ,get ,post ,put ,delete ,response codes
