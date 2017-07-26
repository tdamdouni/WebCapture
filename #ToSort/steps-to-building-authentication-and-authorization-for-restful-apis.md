# Steps to Building Authentication and Authorization for RESTful APIs

_Captured: 2017-02-07 at 19:40 from [dzone.com](https://dzone.com/articles/steps-to-building-authentication-and-authorization?edition=267885&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-07)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

One of the challenges to building any RESTful API is having a well thought out authentication and authorization strategy. Concerns like authentication, security, and logging are always challenging and involve many stakeholders.

To be clear on definitions, there are two separate actions usually discussed together:

## **Authentication**

Authentication involves verifying who the person says he/she is. This may involve checking a username/password or checking that a token is signed and not expired. Authentication does _not_ mean this person can access a particular resource.

## **Authorization**

Authorization involves checking resources that the user is authorized to access or modify via defined roles or claims. For example, the authenticated user is authorized for read access to a database but not allowed to modify it. The same can be applied to your API. Maybe most users can access certain resources or endpoints, but special admin users have privileged access.

Of course, these definitions are usually implemented together and interdependent, so when we refer to auth, we are referring to the overall system.

## **Defining the Actual Token**

One of the first things to give thought to when creating an auth strategy is what type of token you will use. There are a variety of methods, but two of the most common are:

### **1\. JWT Tokens (JSON Web Tokens)**

A [JWT Token](https://en.wikipedia.org/wiki/JSON_Web_Token) is actually a full JSON Object that has been base64 encoded and then signed with either a symmetric shared key or using a [public/private key](https://en.wikipedia.org/wiki/Public-key_cryptography) pair. The difference is if you have a consumer that needs to verify the token is signed, but that consumer shouldn't be allowed to create tokens, you can give the consumer the public key, which can't create tokens but still verify them. I'll save the details for a separate post, but if you remember from your cryptography courses, asymmetric encryption and signature algorithms create a pair of keys that are mathematically related.

The JWT can contain such information include the subject or user_id, when the token was issued, and when it expires. By signing with a secret, you ensure that only you can generate a token and thus was not tampered with (such as modifying the user_id or when it expires). One thing to keep in mind though, while the JWT is signed, JWTs are usually not encrypted (although you can encrypt it optionally). This means any data that is in the token can be read by anyone who has access to the token. It is good practice to place identifiers in the token such as a user_id, but not personally identifiable information like an email or social security number. You can use a tool like [JWT.io](https://jwt.io/) to easily base64 decode and view the JSON data.

#### **Why Are JWTs So Great?**

One of the benefits of JWTs is they can be used without a backing store. All the information required to authenticate the user is contained within the token itself. In a distributed microservice world, it makes it easy to not rely on centralized authentication servers and databases. The individual microservice only needs some middleware to handle verifying the token (JWT libs are openly available for everything from Express to JVM MVC Frameworks) and the secret key needed for verification. Verifying consists of checking signature and a few parameters such as the claims and when the token expires. JWTs are usually medium life tokens with an expiration date that may set anywhere from a few weeks to longer.

Verifying that a token is correctly signed only takes CPU Cycles and requires no IO or network access and very easy to scale on modern web server hardware.

#### **If Jwts Are So Great Why Doesn't Everyone Use Them?**

One of the downsides with JWTs is that banning users or adding/removing roles is a little harder if you need the action to be immediate. Remember, the JWT has a predefined expiration date which may be set a week into the future. Since the token is stored client side, there is no way to directly invalidate the token even if you mark the user as disabled in your database. Rather, you must wait until it expires. This can influence your architecture especially if designing a public API that could be starved by one power user or an e-commerce app where fraudulent users need to be banned. There are workarounds, for example, if all you care is banning compromised tokens or users, you can have a blacklist of tokens or user_ids, but this may reintroduce a database back into your auth framework. A recommended way to blacklist is to ensure each token has a _jti_ claim (or a JWT Id which can be stored in the DB) Assuming that the number of tokens you would like to invalidate is much smaller than the number of users in your application, this may scale pretty easily. You may even locally cache it in the same process as your API code removing some dependency on a database server being multiple 9's of reliability.

On the other hand, if you have an enterprise app with many roles such as admin, project owner, service account manager and you want the effect to have immediate effect, then development can be tricky. Especially, think of the case where an admin is modifying someone else's authorized roles such as his/her immediate reports. Thus, the modified user doesn't even know his/her roles have changed without refreshing the JWT.

A second downside is the token can grow as more fields are added. In stateless apps, the token is sent for pretty much every request, thus there can be an impact on data traffic size. For example, the enterprise app we referred to earlier may have many roles, which may add bloat and complications for what to store in a token. Think of designing the APIs that back AWS or Azure's Web Portal. You have targeted permissions on each resource for each user. For example, thus one user is allowed to view S3 accounts, but not modify EC2 instances. The sheer complexity of this may be beyond what a JWT can handle.

In mobile apps where smartphone owners are concerned for client side latency and data usage, JWTs may add too much payload to each request.

### **2\. Opaque Tokens**

Now that we discussed the benefits and drawbacks of JWTs, let's explore a secondary option, Opaque Tokens. Opaque tokens are literally what they sounds like. Instead of storing user identity and claims in the token, the opaque token is simply a primary key that references a database entry which has the data. Fast key value stores like Redis are perfect for leveraging in memory hash tables for O(1) lookup of the payload. Since the roles are read from a database directly, roles can be changed and the user will see the new roles as soon as the changes propagate through your backend.

Of course, there is the added complexity of maintaining the K/V store and the auth server. Depending on your architecture, each service has to handshake with the auth server to get the claims or roles.

### **3\. A Blend**

One thing not talked about yet is a blend of both options. You can handle authentication via JWT such as checking that the user is who they say they are. On the other hand, authorization for specific resources are not part of the JWT. In other words, the JWT only handles the authentication side but not the authorization side.

## **Cookies vs. Headers vs. URL Parameter**

### **URL Parameters**

First of all, we never recommend placing a token in the URL. URLs are bookmarked, shared with friends, posted online, etc. It is too easy for a user to copy a URL of a page they like and forward to a friend. Now, the friend has all the authentication requirements needed to sign in on behalf of that user. In addition, there are a variety of other concerns such as most loggers will log the URL in plain text at a minimum. It's much less likely for someone to open developer tools in Chrome and copy their cookie or HTTP headers. ;)

So this narrows us down to Cookies vs. HTTP Headers. If you are focused on creating RESTful APIs, really the Cookie is just another header just like the Authorization Header. You could in fact take the same JWT that would be sent via an Authorization Header and wrap it in a cookie. In reality, many pure RESTful APIs designed for consumption by others just use a standard or custom authorization header as it is more explicit. There can also be a blend, for example a web app may talk to a RESTful API behind a proxy using Cookies. The proxy will extract the Cookie and add the appropriate headers when relaying the request. The real reasons come in the next section:

### **The Real Debate: Cookie vs. Local Storage:**

While the cookie may in fact just wrap the JWT or opaque token, a client web app still has to store the token somewhere. The two choices that most people think of is Cookies and HTML5 Local Storage. So sometimes when people refer to Cookie vs HTTP Header, they are actually asking "Cookie vs. Local Storage" There are benefits and security risks for each.

### **Cookies**

Cookies can be nice as they have certain flags that can be set to enforce security checks such as HTTP Only and Secure. By setting HTTP Only and Secure flags, the cookie cannot be read by any Javascript code nor be sent in plain text over HTTP. Thus the Cookie can be immune to [XSS](https://en.wikipedia.org/wiki/Cross-site_scripting) attacks as described in the local storage Section. Cookies can be vulnerable to a different type of attack called [cross site request forgery (XSRF or CSRF)](https://en.wikipedia.org/wiki/Cross-site_request_forgery). XSRF means a hacker on a different site can replicate some input form on your own site and POST form data to our own site. While the hacker doesn't have access to the cookie itself, cookies are transferred with every HTTP request to your real domain that the cookie is valid for. Thus, the hacker doesn't need to read the cookie, it just needs to successfully POST form data to your real site. This is one of the dangers with cookies. They are sent for every request, static, AJAX, etc. There are ways around this, but the fundamental principal is that your web server needs to recognize whether the request came from your real website running in a browser or someone else. One way to do this is with a hidden anti-forgery token. One way is to generate and store a special random key in the cookie that also needs to be sent with the POSTed form data. Remember, only your real site can _access_ the cookie but the hacker site cannot due to same origin policy. Your server can then verify that the cookie's token matches the token in form data. There are other options for protection on XSRF.

### **Local Storage**

A security risk for [local storage](https://en.wikipedia.org/wiki/Web_storage) is Javascript can be subject to Cross-Scripting attacks (XSS). In the early days, XSS was a result of not escaping user input, but now your modern web app probably imports numerous JS libs from analytics and attribution tracking to ads and small UI elements. Local storage is global to your website domain. Thus, any javascript on your website, 3rd party lib or not, can access the same local storage. There is no sandboxing within your app. For example, your analytics lib reads and writes from the same local storage as your own application code. While GA is probably fine, did you audit that quick UI element you added? In the past, there was also concern if javascript made AJAX calls in plain text even though the website itself was secured via HTTPS. This concern is less than it used to now that browsers are starting to enforce checks for mixed content. Something to still be aware of incase a browser is older or launched without enforcement.

A second downside for local storage is you can't access it across multiple subdomains. If you have a separate blog subdomain or email subdomain, these sites cannot read the local storage. This might be fine if you don't plan on logging in across multiple domains (Think mail.google.com and google.com).

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.

Topics:

authentication ,authorization ,jwt ,rest api ,cross-site scripting ,api best practices ,ajax
