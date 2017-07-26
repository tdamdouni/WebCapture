# API Security: An Overview

_Captured: 2017-01-19 at 11:09 from [dzone.com](https://dzone.com/articles/api-security-an-overview?edition=262904&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-18)_

[Download the _Account Takeover: How Hacking Happens in 2016_ ebook](https://dzone.com/go?i=180134&u=http%3A%2F%2Fhubs.ly%2FH03SwFQ0) to learn common techniques used to hack your site and what you can do to reduce the likelihood of a breach, brought to you in partnership with [Immunio](https://dzone.com/go?i=180134&u=http%3A%2F%2Fhubs.ly%2FH03SwFQ0).

Many modern web or mobile applications use an application programming interface (API) on the back end. As a set of tools and protocols that enable developers to provide flexibility and scalability in the front end applications, APIs are an excellent way to enable connections with partners, systems, and other developers. As the back end of client facing applications, therefore, securing APIs is critical to protecting users and connected systems.

APIs can be either public or private. Private APIs are used only for specific, dedicated client applications. However, private APIs do not provide any additional security. Client applications can be reverse engineered and popular front-end technologies like JavaScript make it easy for hackers to discover and abuse APIs.

The primary security concerns for APIs are with authentication and authorization of users.

  * Authentication is what determines the identity of a user and confirms if a user is who s/he claims to be.
  * Authorization is what determines the functions, data, and/or folders a particular user is allowed access to.

Both authentication and authorization present significant security challenges. Just as one can not trust client applications with API access, one can not blindly trust the identity of users connecting with your systems. Often applications are vulnerable to brute force attacks like credential stuffing, session stealing, and other forms of impersonation of valid user. Account takeover (ATO) is often the first phase of an attack on a system. It is also a popular method of gaining access to authenticated API services, given all the data breaches in recent years and the habit of many people to reuse passwords. Thus, these two activities in particular require additional layers of protection.

In addition to attacks on user identity , APIs are also vulnerable to injection attacks like SQL injection or remote command execution attacks, which enable hackers to basically take over the entire system for their own purposes.

To secure APIs and the web applications that use them, it is critical that developers follow secure coding guidelines, use robust application security testing tools, and runtime application self-protection (RASP) to identify vulnerabilities and prevent exploitation of those vulnerabilities that do exist.

Discover how to prevent [Account Takeover Attacks](https://dzone.com/go?i=180135&u=http%3A%2F%2Fhubs.ly%2FH03SwFQ0), brought to you in partnership with [Immunio](https://dzone.com/go?i=180135&u=http%3A%2F%2Fhubs.ly%2FH03SwFQ0).
