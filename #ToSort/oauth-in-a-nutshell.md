# OAuth 2.0 in a Nutshell

_Captured: 2018-01-24 at 22:21 from [dzone.com](https://dzone.com/articles/oauth-20-in-a-nutshell?edition=357095&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-01-24)_

Address your unique [security needs at every stage](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre) of the software development life cycle. Brought to you in partnership with [Synopsys](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre).

OAuth 2.0 is an industry-standard protocol for authorization. It provides a wide range of authorization flows to support various uses cases for web applications, desktop applications, mobile phones, and IoT devices.

It is important to stress that OAuth is solely responsible for coarse-grained authorization, that is whether the application/device is authorized to make the request. However, the service still needs to make a decision on whether the specific request that has been made is actually allowed based on multiple factors such as time, region, delegation rules, etc. This is where fine-grained authorization models (PDP, PAP, PIP, PEP) come in. Visit [my blog post](https://gitanjali548936168.wordpress.com/2018/01/03/externalizing-fine-grained-security/) for more details on fine-grained authorization.

## **OAuth 2: Grant Types**

### Authorization Code Grant Type

This flow is also called a three-legged OAuth flow or web service flow. This flow involves three parties:

    * The OAuth client application (web server).
    * The resource owner.
    * The Authorization server.

#### **Used by:**

  * Web applications that have a server-side component.

### **Authorization Flow**

  1. The OAuth client has signed up to the server and receives its client credentials (also known as "consumer key and secret") ahead of time.
  2. The OAuth client sends the resource owner a redirection to the authorization server.
  3. The authorization server presents a form to the resource owner to log in and to grant access.
  4. The resource owner logs in to the authorization server and provides either a grant or deny flag.
  5. Based on the response from the resource owner, the following processing occurs: 
    * The OAuth client is redirected with the authorization grant code.
    * If the resource owner denies access, the request is redirected to the OAuth client but no grant is provided.
  6. The OAuth client sends the following information to the token endpoint (authorization server). 
    * Authorization grant code.
    * Client ID.
    * Client secret or client certificate. 
  7. The authorization server authenticates the OAuth client with the client id and client secret, validates the authorization grant code, and, if the grant code is indeed validated, then the authorization server sends the OAuth client an access token (JWT token) signed with the authorization server's private key and, optionally, a refresh token. The token type value is "Bearer."
  8. The OAuth client sends the access token to the resource server to request protected resources.
  9. The protected resource validates the access token (validating the signature of the authorization server). If valid, it allows access. 

**Figure 1. Authorization code grant (happy flow)**

![Screen Shot 2018-01-08 at 5.41.36 PM](https://gitanjali548936168.files.wordpress.com/2018/01/screen-shot-2018-01-08-at-5-41-36-pm.png)

**Security Consideration** - This flow provides a high level of security. Use short-lived access tokens and long-lived refresh tokens for maximum security.

### Authorization Code Implicit

This flow is also called a three-legged OAuth flow. The three major differences with "authorization code flow" are:

  * Instead of the authorization server returning an authorization code on the exchange of the resource owner's approval, it returns the access token itself.
  * The authorization server does not authenticate the OAuth client.
  * It is intended to be used by user-agent-based clients such as browsers.

#### **Used by:**

  * This variant was specifically designed for JavaScript-based applications running in a web browser. Use this flow in highly trusted environments as the access token is available with the browser.
  * Client applications running on the server-side that call another server application by handing out client credentials (or client secrets).

#### **Authorization Flow:**

  1. The OAuth client (user agent browser) sends the resource owner a redirection to the authorization server.
  2. The authorization server presents a form to the resource owner to log in and to grant access.
  3. The resource owner logs in and either grants or denies access.
  4. Based on the response from the resource owner, the following processing occurs: 
    * If the resource owner allows access, the authorization server sends the OAuth client an access token (JWT token) signed with the authorization server's private key. The token type's value is, "Bearer."
    * If the resource owner denies access, the request is redirected to the OAuth client but access is not granted.
  5. The OAuth client sends the access token to the resource server to request protected resources.
  6. The protected resource validates the access token (validating the signature of the authorization server). If valid, it allows access.

**Figure 2. Authorization code implicit (happy flow)**

![Screen Shot 2018-01-08 at 5.43.51 PM](https://gitanjali548936168.files.wordpress.com/2018/01/screen-shot-2018-01-08-at-5-43-51-pm.png)

**Security Consideration** - The implicit grant flow does not issue refresh tokens, mostly for security reasons. A refresh token isn't as narrowly scoped as access tokens, granting far more power, hence, inflicting far more damage in case it is leaked out. Upon the expiration of the access token, the client has to run the reauthorization process again to get a new access token.

### Resource Owner Password Credentials

This flow is called a two-legged OAuth flow with password credentials. This flow involves two parties:

    * The OAuth client application.
    * The authorizations server.

This flow describes a scenario where a client application collects the user's (resource owner's) credentials and hands that to the authorization server to get an access token from the authorization server. The client uses this access token to access the resource.

#### **Use by:**

This flow should only be used where there is a high degree of trust between the client application (highly privileged application) and the resource owner. Note that the login credential is collected by the client application (NOT the authorization server). Usually, it is used for migration purposes and mostly the client application and authorization server are controlled by the same party.

#### **Authorization Flow:**

  1. The OAuth client has signed up to the server and received it's client credentials (also known as "consumer key and secret") ahead of time.
  2. The OAuth client presents a form to the resource owner to log in and collects the user's credentials.
  3. The user logs into the OAuth client login form.
  4. The OAuth client sends the following to the authorization server: 
    * User's credentials
    * Client Id
    * Client Credentials
  5. The authorization server validates the OAuth client credentials, accepts the resource owner's credentials, and sends the OAuth client an access token (JWT token) signed with the authorization server's private key. The token type value is, "Bearer." It also sends a refresh token.
  6. The OAuth client sends the access token to the resource server to request protected resources.
  7. The protected resource validates the access token (validating the signature of the authorization server). If valid, it allows access.

**Figure 3. Resource owner password credential (happy flow)**

![Screen Shot 2018-01-08 at 5.53.16 PM](https://gitanjali548936168.files.wordpress.com/2018/01/screen-shot-2018-01-08-at-5-53-16-pm.png)

**Security Consideration - **In this scenario, the client application is impersonating a resource owner which opens your application up to a higher risk of a phishing attack. The password could be unintentionally disclosed to a malicious attacker. This scenario must not be used with external applications where the client application is not controlled by the party that controls the authorization server.

Since, in this scenario, the resource owner is not authenticated by the authorization server, there is no user identity managed by the authorization server and, hence, there is no Single Sign-On possible for this scenario.

### Client Credentials

This flow is also called a two-legged OAuth flow with password credentials. This flow involves two parties:

    * The OAuth client application.
    * The authorization server.

#### **Use by:**

This flow is mostly used in application-to-application access. The application does not need the user's permission to get access to a resource.

#### **Authorization Flow:**

  1. The OAuth client has signed up to the server and received its client credentials (also known as "consumer key and secret") ahead of time.
  2. The OAuth client sends the following to the authorization server: 
    * Client Id
    * Client Credential
  3. The authorization server validates the OAuth client's credentials and then sends the OAuth client an access token (JWT token) signed with the authorization server's private key. The token type value is "Bearer."
  4. The OAuth client sends the access token to the resource server to request protected resources.
  5. The protected resource validates the access token (validating the signature of the authorization server). If valid, it allows access.

**Figure 4. Client credential (happy flow)**

![Screen Shot 2018-01-08 at 5.05.41 PM](https://gitanjali548936168.files.wordpress.com/2018/01/screen-shot-2018-01-08-at-5-05-41-pm.png)

**Security Consideration - **In this scenario, it does not send any refresh token, as this is not needed in this scenario. The client can get another token just by sending its credentials again. In this scenario, the resource is not owned by any user.

Besides the above Grant type of flow, OAuth supports a few other forms of authorization flow that are provided below.

### OAuth Device Flow

This authorization flow enables OAuth clients to request user authorization from browser-less and input-constrained devices. This authorization flow instructs the user to perform the authorization request on a secondary device, such as a smartphone. There is no requirement for communication between the constrained device and the user's secondary device.

#### **Used by:**

Browser-less and input-constrained devices that have an Internet connection, but don't have an easy input method (such as a smart TV, media console, picture frame, or printer), or lack a suitable browser for a more traditional OAuth flow.

#### **Authorization Flow:**

  1. The OAuth client (for example, the YouTube app) makes a request to the authorization server.
  2. The authorization server responds with a verification URL, user code, and device code.
  3. The OAuth client device polls the token endpoint every few seconds.
  4. Meanwhile, the user navigates to the verification URL, accesses the browser in another device, and enters the user code.
  5. The browser-based device forwards the user's response to the authorization server.
  6. If the user grants access, then the authorization server sends an access token to the OAuth client. 
  7. The OAuth client device accesses to the protected resource with this access token.
  8. The protected resource validates the access token (validating the signature of the authorization server). If valid, it allows access.

**Figure 5. Device flow (happy flow)**

![Screen Shot 2018-01-08 at 5.59.35 PM.png](https://gitanjali548936168.files.wordpress.com/2018/01/screen-shot-2018-01-08-at-5-59-35-pm.png)

**Security Consideration** - Since the user code is hand-entered by the user into an interface that does not yet know about the device being authorized, precautions should be taken to avoid the possibility of a **brute force attack **against the user code.

### SAML Bearer Assertion Flow

This flow defines how a SAML bearer token can be exchanged to get an OAuth token.

#### **Used by:**

This flow is mostly used if the identity provider generates a SAML token for a valid user, where a resource is protected by OAuth security.

#### **Authorization Flow:**

  1. The client application is registered to the OAuth authorization server ahead of time.
  2. IdP has issued a SAML token, signed by itself, to the client application ahead of time.
  3. The client application sends a SAML token to the OAuth authorization server.
  4. The authorization server validates the signature given by the IdP and, based on the SAML assertion claims, it generates an OAuth access token.
  5. The client application sends an access token to the protected resource.
  6. The protected resource validates the access token (validating the signature of the authorization server). If valid, it allows access.

**Figure 5. SAML Bearer assertion flow (happy flow)**

![Screen Shot 2018-01-08 at 7.00.18 PM.png](https://gitanjali548936168.files.wordpress.com/2018/01/screen-shot-2018-01-08-at-7-00-18-pm.png)

**Security Consideration** - The client application must be an OAuth client registered with the authorization server. And the IdP that generates the SAML assertion is trusted by the OAuth authorization server.

## **Token Type Consideration**

OAuth specification talks about MAC tokens and bearer tokens. Mac tokens strengthen bearer tokens in the absence of SSL/TLS protocols by providing encryption using a symmetric key. However, since it is symmetric key encryption, it is also vulnerable to MiTM attacks. You still need an SSL/TLS protocol. If you use an SSL/TLS protocol, it would be better to use bearer tokens, as they are easier to implement than Mac tokens.

## References

<https://oauth.net/2/>

Find out how [Synopsys](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3Ddzone-sig-post) can help you build security and quality into your SDLC and supply chain. We offer [application testing and remediation expertise](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsecurity-testing.html%3Fcmp%3Ddzone-sig-post), guidance for [structuring a software security initiative](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-strategy.html%3Fcmp%3Ddzone-sig-post), training, and [professional services](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-services.html%3Fcmp%3Ddzone-sig-post) for a proactive approach to application security.
