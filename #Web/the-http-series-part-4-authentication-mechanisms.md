# The HTTP Series (Part 4): Authentication Mechanisms

_Captured: 2017-08-15 at 19:31 from [dzone.com](https://dzone.com/articles/the-http-series-part-4-authentication-mechanisms)_

In the [previous post](https://dzone.com/articles/the-http-series-part-3-client-identification), we've talked about the different ways that websites can use to identify the visiting user.

But identification itself represents **just a claim**. When you identify yourself, you are **claiming** that you are someone. But there is no proof of that.

Authentication, on the other hand, is **showing a proof** that you are what you claim to be, like showing your personal id or typing in your password.

More often than not, websites need some sort of proof to serve you sensitive resources.

HTTP has its own authentication mechanisms that allow the servers to issue challenges and get the proof they need. You will learn about what they are and how they work. We'll also cover the pros and cons of each one and find out if they are really good enough to be used on their own (spoiler: they are not).

This is what we have learned so far:

In this article, you will learn more about:

  * How HTTP authentication works.
  * Basic authentication.
  * Digest authentication.

Before venturing deeper into the concrete HTTP authentication mechanisms, let's explore what HTTP authentication is.

## How Does HTTP Authentication Work?

Authentication is a way to identify yourself to the web server. You need to show proof that you have the right to access the requested resources. Usually, this is done by using a combination of a username and a password (key and secret) which the server validates and then decides if you can access the resource.

HTTP offers two authentication protocols:

  * **Basic authentication**
  * **Digest authentication**

Before learning more about each one, let's go through some of the basic concepts.

**1\. HTTP uses a challenge/response authentication framework**

What does this mean?

It means that when someone sends a request, instead of responding to it immediately, the server sends an **authentication challenge**. It challenges the user to provide the proof of identity by entering the secret information (username and password).

After that, the request is repeated using the provided credentials, and if they are correct, the user gets the expected response. In case the credentials are wrong, the server can reissue the challenge or just send the error message.

**2\. Authentication related [request/response headers](https://www.code-maze.com/the-http-reference/#headers)**

The server issues the challenge by utilizing the **WWW-Authenticate response header. **It contains the information about the authentication protocol and the security realm.

After the client inputs the credentials, the request is sent again. This time with the **Authorization header **containing the authentication algorithm and the username/password combination.

If the credentials are correct, the server returns the response and additional info in an optional **Authentication-Info response header**.

**3\. Security realms**

Security realms provide a **way to associate different access rights to different resource groups** on the server. These are called protection spaces.

What this means, effectively, is that depending on the resource you want to access, you might need to enter different credentials.

The server can have multiple realms. For example, one would be for website statistics information that only website admins can access, and another for website images that other users can access and upload images to.

`/admin/statistics/financials.txt -> Realm="Admin Statistics"`

`/images/img1.jpg -> Realm = "Images"`

When you try to access the financials.txt you will be challenged by the server and the response would look like this:

You can find out more about security realms [here](https://tools.ietf.org/html/rfc7235#section-2.2).

### **Simple HTTP Authentication Example**

Now let's connect the dots by looking at the simplest HTTP authentication **example** (Basic authentication, explained below):

1\. User Agent -> Server

The user requests access to some image on the server.
    
    
    GET /gallery/personal/images/image1.jpg HTTP/1.1

2\. Server -> User Agent

The server sends the authentication challenge to the user.

3\. User Agent -> Server

The user identifies itself via form input.
    
    
    GET /gallery/personal/images/image1.jpg HTTP/1.1

4\. Server -> User Agent

The server checks the credentials and sends the [200 OK status code](https://www.code-maze.com/the-http-reference/#statuscodes) and the image data.

Not that complicated, right?

Now let's drill down and look into basic authentication.

## Basic Authentication

Basic Authentication is the most prevalent and supported authentication protocol out there. It has been around since HTTP/1.0 and every major client implements it.

The example above depicts how to authenticate by using Basic Authentication. It's [rather simple to implement and use](https://www.rdegges.com/2015/why-i-love-basic-auth/), but it has some security flaws.

Before going into the security issues, let's see how Basic Authentication deals with usernames and passwords.

Basic authentication packs the username and password into one string and separates them using the colon (:). After that, it encodes them using [Base64 encoding](https://en.wikipedia.org/wiki/Base64). Despite what it looks like, the scrambled sequence of characters is **not secure** and it's **easily decoded**. The purpose of Base64 encoding is not to encrypt, but to make the username and password HTTP compatible because international characters are not allowed in HTTP headers.

The "Zm9vOmJhcg==" from this example is nothing more than a Base64 encoded "foo:bar" string.

So anyone listening to the requests can easily decode and use the credentials.

Even worse than that, encoding the username and password wouldn't help. A malicious third party **could still send the scrambled sequence to achieve the same effect**.

There is also **no protection against proxies** or any other type of attack that changes the request body and leaves the request headers intact.

So, as you can see, Basic Authentication is a less than perfect mechanism.

Still, despite that, it can be used to prevent accidental access to protected resources and offers a degree of personalization.

To make it more secure and useable, Basic Authentication can be implemented by using HTTPS over SSL which we talk about in part 5 of the series.

Some would argue it's only [as secure as your transport mechanism](http://www.skorks.com/2009/08/is-basic-authentication-really-insecure).

## Digest Authentication

Digest Authentication was made as a more secure and reliable alternative to simple but insecure Basic Authentication.

So, how does it work?

Digest Authentication uses **MD5 cryptographic hashing **combined with the usage of **nonces** to hide the password information and prevent different kinds of malicious attacks.

This might sound a bit complicated, but it will get clearer when you see how it works in a simple example.

#### **Example:**

1\. User Agent -> Server

The client sends a unauthenticated request.

2\. Server -> User Agent

The server challenges the client to authenticate using Digest Authentication and sends the required information to the client.

3\. User Agent -> Server

The client calculates the response value and sends it together with a username, realm, URI, nonce, opaque, qop, nc and cnonce. A lot of stuff.

Let's define these:

  * **nonce** and **opaque** - the server defined strings that should be returned by the client as they were received.
  * **qop (quality of protection) **- one or more of the predefined values ("auth" | "auth-int" | token). These values affect the computation of the digest.
  * **cnonce** - client nonce, must be generated if qop is set. It is used to avoid [chosen plaintext attacks](https://en.wikipedia.org/wiki/Chosen-plaintext_attack) and to provide message integrity protection.
  * **nc **- nonce count, must be sent if qop is set. The purpose of this directive is to allow the server to detect request replays by maintaining its own copy of this count - if the same nc-value is seen twice, then the request is a replay.

The response attribute is calculated in the following way:

If you are interested in learning how to compute the response depending on qop, you can find it in the [RFC 2617](https://www.ietf.org/rfc/rfc2617.txt).

4\. Server -> User Agent

The server computes the hash on its own and compares the two. If they match, it serves the client with the requested data.

As you can see, Digest Authentication is more complicated to understand and implement.

It is also more secure than Basic Authentication, but still vulnerable to [man-in-the-middle attacks](https://en.wikipedia.org/wiki/Man-in-the-middle_attack). [RFC 2617](https://www.ietf.org/rfc/rfc2617.txt) recommends that **Digest Authentication is used instead of the Basic   
Authentication** since it remedies some of its weaknesses. It also doesn't hide the fact that **Digest Authentication is still weak by modern cryptographic standards **and that its strength largely depends on the implementation.

So, in summary, Digest Authentication:

  * Does not send plain text passwords over the network.
  * Prevents replay attacks.
  * Guards against message tampering.

Some of the weaknesses:

  * Vulnerability to the man-in-the-middle attacks.
  * Many of the security options are not required and thus make Digest Authentication functions in a less secure manner if not set.
  * Prevents the use of strong password hashing algorithms when storing passwords.

Due to these facts, Digest Authentication still hasn't gained major traction. Basic Authentication is much simpler, and, when combined with SSL, still more secure than Digest Authentication.

## Conclusion

That's it for this part of the HTTP series.

We've gone through different authentication mechanisms that HTTP offers by default and talked about their advantages and disadvantages.

These concepts are hopefully not just the letters on the screen anymore, and the next time you hear about them you will know precisely what they are and when to apply them.

You are also aware that there are security risks that haven't been solved by these mechanisms and that's why the concepts like HTTPS and SSL/TLS exist. We talk more about security risks and how to solve them in the next part of the series.

If you found some of the concepts in this part unclear, refer to the [part 1,](https://www.code-maze.com/http-series-part-1/) [part 2](https://www.code-maze.com/http-series-part-2/), and [part 3](https://www.code-maze.com/http-series-part-3/) of the [HTTP series](https://www.code-maze.com/http-series/).

If you reached this far I guess you liked the article Even if you didn't, please do leave a comment in the comments section below and let me know how you feel about it.
