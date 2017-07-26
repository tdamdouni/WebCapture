# SSO Login: Key Benefits and Implementation

_Captured: 2017-06-24 at 04:00 from [dzone.com](https://dzone.com/articles/sso-login-key-benefits-and-implementation?edition=305134&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-23)_

Discover an in-depth knowledge about the different kinds of [iOS hacking tools](https://dzone.com/go?i=222228&u=https%3A%2F%2Fweb.securityinnovation.com%2Fhacking-ios-applications-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dhacking-ios-applications) and techniques with the [free](https://dzone.com/go?i=222228&u=https%3A%2F%2Fweb.securityinnovation.com%2Fhacking-ios-applications-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dhacking-ios-applications) iOS Hacking Guide from Security Innovation.

## What Is SSO Login?

**Single Sign On (SSO) login** refers to when a user logs in to an application with a single set of credentials and is then automatically signed into multiple applications. With SSO login, a user gains access to multiple software systems without maintaining different login credentials such as usernames and passwords.

A very popular example of SSO login is Google's implementation for their software products. Once a user is logged in to Gmail, the user automatically gains access to YouTube, Google Drive, Google Photos, and other Google products.

![SSO login example - Google apps](https://cdn.auth0.com/blog/sso-google-upload.png)

> _I signed into gmail and already have access to all those products around the red marker._

## Key Benefits of SSO Login

Why should you implement **SSO login**? What are the benefits of SSO login? How does it increase your product's conversion rate? These are some of the benefits of SSO login:

  * Eliminate the time spent re-entering user credentials, thus improving productivity for users and increasing conversion rates for product owners, which means your internal employees and your external users don't have to go through the hassle of maintaining and remembering yet another set of credentials.
  * Eliminate password fatigue from having to store or remember different usernames and passwords.
  * Reduce complaints about password problems, thus reducing the costs associated with setting up several helpdesk systems for password-reset issues, invalid credentials, etc.
  * Minimize [phishing](https://en.wikipedia.org/wiki/Phishing), thus improving security.
  * Streamlines the local, desktop, and remote application workflows, thus improving users' productive capacity.

## How SSO Login Works

Let's look at an ideal scenario before going into the nitty-gritty of how SSO login works. Three apps have been developed separately: **App FOO**, **App BAR**, and **App BAZ**. They are also hosted on three different domains: **foo.com**, **bar.com** and **baz.com**, respectively.

**Challenge**: Users have to enter different usernames and passwords for the three different apps to gain access to certain resources.

**Proposed solution**: Eliminate the different login systems that are present. Users should be able to log in to **foo.com** and then be signed in to **bar.com** and **baz.com** automatically without having to re-enter their authentication credentials.

**SSO login to the rescue**: With SSO login, a _central authentication server_ needs to exist. Let's call our central authentication server **foobarbaz.com**. This is how the process flow will look in this scenario:

  1. The user accesses **foo.com**.
  2. The user is redirected to **foobarbaz.com**, where an authentication-related cookie is generated.
  3. The user navigates to **bar.com**.
  4. The user is redirected to **foobarbaz.com**.
  5. **foobarbaz.com** checks whether the user already has an authentication-related cookie and redirects the user back to **bar.com**, providing access to its features and content.
  6. The same process applies to **baz.com**.

The simple take-away concept is that there is one central domain through which authentication is performed, and then the session is shared with other domains in some secure way e.g., a signed JSON Web Token (JWT).

![A typical SSO example](https://cdn.auth0.com/blog/typical-sso.png)

> _A typical graphical SSO example._

## SSO Integrations

There are different SSO login integrations: these are external services you can use for Single Sign On logins. You can enable SSO login for your corporate applications, such as _Salesforce_, _Dropbox_, _Microsoft Azure Active Directory_, _Slack_, _SharePoint_, _New Relic_, _Zendesk_, and so on.

## Conclusion

The benefits of using SSO login to manage a large ecosystem of applications and services are numerous. Modern application development supports distributed and decentralized systems. With an efficient SSO login in place, it's easier to add more applications to the existing suite of services without having to worry about authentication every time. If Google can implement SSO login and succeed, you can do it too!

**[Leveraging](https://dzone.com/go?i=222226&u=https%3A%2F%2Fweb.securityinnovation.com%2Fwebinar%2Fleveraging-humans-and-tools-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dleveraging-humans-and-tools%252520) Humans to Get the Most Out of Tools**
