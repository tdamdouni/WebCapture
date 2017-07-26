# Top 5 REST API Security Guidelines

_Captured: 2017-01-16 at 13:12 from [dzone.com](https://dzone.com/articles/top-5-rest-api-security-guidelines)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

When developing REST API, one must pay attention to security aspects from the beginning. In this post I will review and explain top 5 security guidelines when [developing and testing REST APIs](http://www.restcase.com).

REST (or REpresentational State Transfer) is a means of expressing specific entities in a system by URL path elements. REST is not an architecture but it is an architectural style to build services on top of the Web. REST allows interaction with a web-based system via simplified URLs rather than complex request body or POST parameters to request specific items from the system.

## 1/5 - Authorization

### Protect HTTP Methods

![REST API Authorization](http://blog.restcase.com/content/images/2016/12/wall-e-sketch.jpg)

RESTful API often use GET (read), POST (create), PUT (replace/update) and DELETE (to delete a record).

Not all of these are valid choices for every single resource collection, user, or action. Make sure the incoming HTTP method is valid for the session token/API key and associated resource collection, action, and record.

For example, if you have a RESTful API for a library, it's not okay to allow anonymous users to DELETE book catalog entries, but it's fine for them to GET a book catalog entry. On the other hand, for the librarian, both of these are valid uses.

Take a look at [CORS](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing) and more if you are looking for more developers resources please check [Enable CORS](http://enable-cors.org/) website.

### Whitelist Allowable Methods

It is common with RESTful services to allow multiple methods for a given URL for different operations on that entity.

For example, a GET request might read the entity while PUT would update an existing entity, POST would create a new entity, and DELETE would delete an existing entity.

It is important for the service to properly restrict the allowable verbs such that only the allowed verbs would work, while all others would return a proper response code (**for example, a 403 Forbidden**).

### Protect Privileged Actions and Sensitive Resource Collections

Not every user has a right to every web service. This is vital, as you don't want administrative web services to be misused:

The session token or API key should be sent along as a cookie or body parameter to ensure that privileged collections or actions are properly protected from unauthorized use.

### Protect Against Cross-site Request Forgery

For resources exposed by RESTful web services, it's important to make sure any PUT, POST, and DELETE request is protected from Cross Site Request Forgery. Typically one would use a token-based approach.

CSRF is easily achieved even using random tokens if any XSS exists within your application, so please make sure you understand how to prevent XSS.

More resources on [CSRF](https://en.wikipedia.org/wiki/Cross-site_request_forgery):

### Insecure Direct Object References

It may seem obvious, but if you had a bank account REST web service, you'd have to make sure there is adequate checking of primary and foreign keys:

[https://example.com/account/325365436/transfer?amount=$100.00&toAccount=473846376](https://example.com/account/325365436/transfer?amount=$100.00&toAccount=473846376)  
In this case, it would be possible to transfer money from any account to any other account, which is clearly absurd. Not even a random token makes this safe.

<https://example.com/invoice/2362365>  
In this case, it would be possible to get a copy of all invoices.

This is essentially a data-contextual access control enforcement need. A URL or even a POSTed form should NEVER contain an access control "key" or similar that provides automatic verification. A data contextual check needs to be done, server side, with each request.

## 2/5 - Input Validation

![Input Validation](http://blog.restcase.com/content/images/2016/12/input_validation.png)

Everything you know about input validation applies to RESTful web services, but add 10% because automated tools can easily fuzz your interfaces for hours on end at high velocity. So:

Assist the user > Reject input > Sanitize (filtering) > No input validation

Assisting the user makes the most sense, as the most common scenario is "problem exists between keyboard and chair" (PEBKAC).

Help the user input high quality data into your web services, such as ensuring a Zip code makes sense for the supplied address, or the date makes sense. If not, reject that input. If they continue on, or it's a text field or some other difficult to validate field, input sanitization is a losing proposition but still better than XSS or SQL injection.

If you're already reduced to sanitization or no input validation, make sure output encoding is very strong for your application.

Log input validation failures, particularly if you assume that client-side code you wrote is going to call your web services.

The reality is that anyone can call your web services, so assume that someone who is performing hundreds of failed input validations per second is up to no good.

Consider rate limiting the API to a certain number of requests per hour or day to prevent abuse.

### URL Validations

Web applications/web services use input from HTTP requests (and occasionally files) to determine how to respond.

Attackers can tamper with any part of an HTTP request, including the URL, query string, headers, cookies, form fields, and hidden fields, to try to bypass the site's security mechanisms.

Common names for common input tampering attacks include forced browsing, command insertion, cross-site scripting, buffer overflows, format string attacks, SQL injection, cookie poisoning, and hidden field manipulation.

### Secure Parsing

Use a secure parser for parsing the incoming messages. If you are using XML, make sure to use a parser that is not vulnerable to XXE and similar attacks.

### Strong Typing

It's difficult to perform most attacks if the only allowed values are true or false, or a number, or one of a small number of acceptable values. Strongly type incoming data as quickly as possible.

### Validate Incoming Content-types

When POSTing or PUTting new data, the client will specify the Content-Type (e.g. application/xml or application/json) of the incoming data.

**The server should never assume the Content-Type, **it should always check that the Content-Type header and the content are the same type. A lack of Content-Type header or an unexpected Content-Type header should result in the server rejecting the content with a **406 Not Acceptable response**.

### Validate Response Types

It is common for REST services to allow multiple response types (e.g. application/XML or application/JSON, and the client specifies the preferred order of response types by the Accept header in the request.

Do NOT simply copy the Accept header to the Content-type header of the response. Reject the request (ideally with a 406 Not Acceptable response) if the Accept header does not specifically contain one of the allowable types.

Because there are many MIME types for the typical response types, it's important to document for clients specifically which MIME types should be used.

### XML Input Validation

XML-based services must ensure that they are protected against common XML-based attacks by using secure XML-parsing.

This typically means protecting against XML External Entity attacks, XML-signature wrapping etc.

See <http://ws-attacks.org> for examples of such attacks.

## 3/5 - Output Encoding

### Security Headers

![Output Encoding](http://blog.restcase.com/content/images/2016/12/Output-Encoding.jpg)

To make sure the content of a given resources is interpreted correctly by the browser, the server should always send the Content-Type header with the correct Content-Type, and preferably the Content-Type header should include a charset.

The server should also send an X-Content-Type-Options: nosniff to make sure the browser does not try to detect a different Content-Type than what is actually sent (can lead to XSS).

Additionally, the client should send an X-Frame-Options: deny to protect against drag'n drop clickjacking attacks in older browsers.

### JSON Encoding

A key concern with JSON encoders is preventing arbitrary JavaScript remote code execution within the browser... or, if you're using node.js, on the server. It's vital that you use a proper JSON serializer to encode user-supplied data properly to prevent the execution of user-supplied input on the browser.

When inserting values into the browser DOM, strongly consider using .value/.innerText/.textContent rather than .innerHTML updates, as this protects against simple DOM XSS attacks.

### XML Encoding

XML should never be built by string concatenation. It should always be constructed using an XML serializer. This ensures that the XML content sent to the browser is parseable and does not contain XML injection. For more information, please see the Web Service Security Cheat Sheet.

## 4/5 - Cryptography

### Data in Transit

![Cryptography](http://blog.restcase.com/content/images/2016/12/cryptography.png)

Unless the public information is completely read-only, the use of TLS should be mandated, particularly where credentials, updates, deletions, and any value transactions are performed. The overhead of TLS is negligible on modern hardware, with a minor latency increase that is more than compensated by safety for the end user.

Consider the use of mutually authenticated client-side certificates to provide additional protection for highly privileged web services.

### Data in Storage

Leading practices are recommended as per any web application when it comes to correctly handling stored sensitive or regulated data. For more information, please see OWASP Top 10 2010 - A7 Insecure Cryptographic Storage.

### Message Integrity

In addition to HTTPS/TLS, JSON Web Token (JWT) is an open standard ([RFC 7519](https://tools.ietf.org/html/rfc7519)) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object.

JWT can not only be used to ensure the message integrity but also authentication of both message sender/receiver.

The JWT includes the digital signature hash value of the message body to ensure the message integrity during the transmission. For more information, you can visit <https://jwt.io/introduction/>.

## 5/5 - HTTP Status Codes

HTTP defines status code. When design REST API, don't just use 200 for success or 404 for error.

Here are some guideline to consider for each REST API status return code. Proper error handle may help to validate the incoming requests and better identify the potential security risks.   
You will also find more information in this [REST API Error Codes 101](http://blog.restcase.com/rest-api-error-codes-101/) blog post.

  * **200 OK** \- Response to a successful REST API action. The HTTP method can be GET, POST, PUT, PATCH or DELETE.
  * **400 Bad Request** \- The request is malformed, such as message body format error.
  * **401 Unauthorized** \- Wrong or no authentication ID/password provided.
  * **403 Forbidden** \- It's used when the authentication succeeded but authenticated user doesn't have permission to the request resource.
  * **404 Not Found** \- When a non-existent resource is requested.
  * **405 Method Not Allowed** \- The error checking for unexpected HTTP method. For example, the RestAPI is expecting HTTP GET, but HTTP PUT is used.
  * **429 Too Many Requests** \- The error is used when there may be DOS attack detected or the request is rejected due to rate limiting

### 401 vs 403

**401 "Unauthorized"** really means Unauthenticated, "You need valid credentials for me to respond to this request".

**403 "Forbidden"** really means Unauthorized, "I understood your credentials, but so sorry, you're not allowed!"

## Summary

In this post, I have covered the top 5 RESTful API security issues and guidelines on how to address them. Following these guidelines will result in a more secure and quality REST API service and a more developer-friendly REST API.

Some methods (for example, HEAD, GET, OPTIONS and TRACE) are defined as safe, which means they are intended only for information retrieval and should not change the state of the server.

When designing and building REST APIs you have to pay attention to security aspects.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
