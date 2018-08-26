# API Authentication: Size Small

_Captured: 2018-07-16 at 23:43 from [dzone.com](https://dzone.com/articles/api-authentication-size-small?edition=386203&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-16)_

I consider myself an API expert -- well, in my own mind anyway. I've seen so many different API specifications in my tenure here at Cloud Elements that I can review the API documentation for a cloud service, and within a few minutes, categorize it by our grading style of choice - t-shirt size: S, M, L or XL. Some are really great, easy to understand, quick to realize - size S. Others not so much, screaming out, "XL!" from the moment I first review its docs.

Others are so strange (mainly due to the fact the documentation is terrible), that after about 10 minutes of looking at it, I proceed directly to happy hour to drown my confusion with a margarita (or two). Cheers!

But, with API integrations, my real nemesis is authentication.

Why? Because even though nearly all modern API authentication specifications can be categorized into a few different types, every single one of them has nuances. Even authentication standards, like OAuth 2.0, have different grant types and have components of each that are implementation dependent. Thus, nearly every OAuth 2.0 implementation that I've seen requires custom code or a nuance workaround to implement. Worse, in some cases, you have to invite auth's evil cousin "session timeout" to the party, and that can escalate quickly into trouble.

As a developer who is realizing an integration to a given service, you will need to research and understand these nuances in order to compensate in your code - and estimate its t-shirt size.

Let's step back a bit (#powerphrase) and review the major categories of authentication.

When it comes to authenticating, most mainstream cloud services (e.g. Box, Salesforce, Hubspot, Quickbooks, etc.) use one of: Basic, API Keys, Token, or OAuth -- with all the other outliers falling into a catch-all category type of Custom (e.g. AWS Signature).

  1. **Basic Auth:** Username and password are passed in the authorization header. The user's information, <username>:<password> is encoded to a base64 string and transmitted in the request. Thus, to auth as david:p@55w0rd the client would send:_ Authorization: Basic ZGF2aWQ6cEA1NXcwcmQ=_. To ensure security, HTTPS/SSL is required across the entire authentication data cycle as base64 is easily decoded.![image \(9\)](https://blog.cloud-elements.com/hs-fs/hubfs/image%20\(9\).png?t=1531412550947&width=5892&name=image%20\(9\).png)

  2. **API Keys:** An API Key is passed in a request header, a cookie, or a query string (e.g. _GET /contacts?api_key=abcd1234_). API key-based auth uses one or more keys that the client and server have agreed upon. Often they are automatically/randomly generated based on the client's specific information (e.g. IP address) or they can be provided from the endpoint service directly. They are only considered secure if used along with HTTPS/SSL encryption.  

  3. **Token/Bearer:** Authentication is provided to the "bearer" using a cryptic token (string). The token is provided by the server and the client sends it in the authorization header, ie. _Authorization: Bearer <token>_. This, once again, is only secure if used over HTTPS/SSL encryption.![image \(8\)](https://blog.cloud-elements.com/hs-fs/hubfs/image%20\(8\).png?t=1531412550947&width=5910&name=image%20\(8\).png)

  4. **OAuth 2.0:** Used by many modern cloud-based services. It allows for a client to gain access to protected server resources without having to share user credentials. Passwords are never passed from server to server with the OAuth framework. Think of it as the client application delegates the responsibilities of authentication to some other service instead of managing them on its own. Before the authentication process can start, OAuth requires that the client application register with the authorization service. It requires basic information such as name, website, and callback URL (HTTPS only) which is used to redirect the user once they have allowed access to their data. Once registered, the endpoint service provides a set of credentials: a client_id and a client_secret. The client secret must be kept confidential, otherwise, security is compromised.![image \(7\)](https://blog.cloud-elements.com/hs-fs/hubfs/image%20\(7\).png?t=1531412550947&width=5916&name=image%20\(7\).png)

OAuth 2.0 flow consists of the following steps: 
    1. The client application makes a request to the authorization server at endpoint service, which will respond by displaying a login and authorization UI page to the user - requesting permission to share _specific_ data assets stored within the endpoint service.
    2. Once approved by the user, an authorization grant is sent back to the requesting application which contains an authorization code.
    3. The requesting application then uses the authorization grant and authorization code to request an access token from the endpoints authorization server.
    4. The authorization server within the endpoint service then provides an access token that is specifically tailored for the requesting user - setting what level of access is granted (scope) that was authorized by the user in step 1.
    5. Next, the requesting application can use the access token to make requests to the endpoint service to retrieve data assets authorized by the user.

What are the OAuth 2.0 nuances that you have to compensate for in your application's code? How the authorization server shares the access token with the resource server is one. Also, refresh tokens and access token expiration times are implementation details that can vary across services.

Now that we are all experts on the different categories of API authentication, you can sympathize the next time you are in a sprint planning meeting and your developer's t-shirt estimates for adding the authentication portion of your integrations is larger in size than the one that the developer is wearing.

Small t-shirt sizes for the win.

There is a better way, with Cloud Elements, we've built authentication into ALL of our 150+ Elements. We've standardized to either one or two REST API calls, depending on the authentication type in play.

Our Elements account for the nuances with authentication, regardless of the endpoint's authentication type and specs. For example, refresh tokens? Session timeouts? Handled automatically by the Element. We've done the hard work for you, leveling the authentication playing field. Making your t-shirt size estimates more consistent.

![](https://blog.cloud-elements.com/hs-fs/hubfs/tshirt.png?t=1531412550947&width=2916&name=tshirt.png)

Our Elements not only reduce the development effort required for your integrations, they go way beyond that. In fact, once authenticated, all that is needed to access your customer's endpoint data is a Cloud Elements granted instance token - kinda like the access token in the OAuth 2.0 flow. Example:

For endpoints that are authenticated via OAuth (e.g. [SFDC how2 video ](https://youtu.be/dOBx4MXBORs)), the path follows the flow scenario in the **blue** below:

  * The first call is made to `GET /elements/{keyOrId}/oauth/url` \- which passes in the Client ID, Client Secret, and Callback URL (obtained from the registered app - see above).
  * The user authenticates via the UI provided by the endpoint's authorization server. Once authenticated, the authorization code is returned.
  * The second call is made to `POST /instances` to create a new credentialled Element instance - passing in the authorization code. If successful, a unique Element instance token is returned, which is used with all subsequent calls to get or post data to the user's endpoint service, in this case, Salesforce.com. The level of access depends on the authorization scope as determined during the first step.
![](https://blog.cloud-elements.com/hs-fs/hubfs/image%20\(10\).png?t=1531412550947&width=2072&name=image%20\(10\).png)

For all other (non-OAuth) endpoints, the path is the **orange** flow scenario in the above:

  * The user enters their credentials based on the authentication type: key(s), username and password, or token(s).
  * The call is made to `POST/instances` to create a new credentialled Element instance.

Want more goodness? More t-shirt size reducing things about the `POST /instances` API resource call:

  1. For OAuth endpoints, the Element will encrypt and store the access and refresh tokens, and use the refresh token when needed to automatically refresh the access token set. Thus, your developers don't have to build the framework to do this - including managing session timers!
  2. Given that the JSON body payload for the `POST/instances` will vary by endpoint - Cloud Elements has already figured those nuances out, tested them, added the necessary code to the Element to compensate for the endpoint's inevitable authentication nuances, and mapped out a JSON [payload sample ](https://developers.cloud-elements.com/docs/elements/salesforce/salesforce-create-instance.html?elementId=23)-- just cut and paste from the example provided.
  3. Once the unique instance token is retrieved, you only need to store it in your application - usually in a table where you keep your customer's information - just store the instance token and the name of the endpoint (e.g. sfdc). When you include it in subsequent API calls, our platform will use it to determine what endpoint service it is associated with and whose credentials to use.

Not a believer yet?

No problem, it can take an example to see just what I mean when I say, "We do the hard work for you." So, here is an example of taking a size L authorization implementation and reducing it to a **size S** using Cloud Elements:

![](https://blog.cloud-elements.com/hs-fs/hubfs/bullhorn-logo-01.png?t=1531412550947&width=204&name=bullhorn-logo-01.png)

**Scenario 1: Via Native Bullhorn API**

**Note: The access token in the response is only valid for 10 minutes, then you will need to make an additional call with the refresh token to retrieve another pair of tokens.**

![](https://blog.cloud-elements.com/hs-fs/hubfs/Screen%20Shot%202018-07-03%20at%2012.27.55%20PM.png?t=1531412550947&width=374&name=Screen%20Shot%202018-07-03%20at%2012.27.55%20PM.png)

  1. Go to the authorization page with registered OAuth information to login in the client's user, i.e. _https://auth.bullhornstaffing.com/oauth/authorize?client_id={client_id}&response_type=code&redirect_uri={optional redirect_uri}_
  2. Log into the application via the Auth UI and prompt permission to share specific data assets stored within the endpoint service. Once approved by the user, an authorization grant is sent back to the requesting application which contains an authorization code.
  3. The requesting application then uses the authorization grant and authorization code to request an access token from the endpoints authorization server, i.e. **POST**_ https://auth.bullhornstaffing.com/oauth/token?grant_type=authorization_code&code={auth_code}&client_id={client_id}&client_secret={client_secret} _The authorization server within the endpoint service then provides an access token and a refresh token that is specifically tailored for the requesting user - setting what level of access is granted (scope) that was authorized by the user in step 2.

**Note: In Bullhorn's authorization, both the access token and the session token only last 10 minutes. The client needs to implement a scheduled job or lazy refresh to ensure that our tokens are not expired.**

4\. With the access token, you need to make a call to the login API to retrieve the session token, i.e. **POST**_https://rest.bullhornstaffing.com/rest-services/login?version=2.0&access_token={xxxxxxxx}_

5\. With the session token, you can make requests to the endpoint service to retrieve data assets authorized by the user.

6\. Once 10 minutes elapses, we encounter an error in trying to make a request to the endpoint service to retrieve data asserts, **403 Expired session token error.**

7\. With the refresh_token from step 4, we will make a refresh call to get a new pair of access and refresh tokens to use for the next 10 minutes, i.e **POST**_https://auth.bullhornstaffing.com/oauth/token?grant_type=refresh_token&refresh_token={refresh_token}&client_id={client_id}&client_secret={client_secret}_

**NOTE: Repeat steps 6-9 every 10 minutes **[Click here for the Bullhorn Auth reference. ](http://bullhorn.github.io/Getting-Started-with-REST/)

8\. With the new access token, you need to make a call to the login API to retrieve the session token (example in 4).

9\. With the new session token, you can make requests to the endpoint service to retrieve data assets authorized by the user.

**Scenario 2: Via Cloud Elements API**

![](https://blog.cloud-elements.com/hs-fs/hubfs/image%20\(6\).png?t=1531412550947&width=600&name=image%20\(6\).png)

**Note: Cloud Elements switched to specifying a 12-hour session length due to experiencing refresh issues with BullHorn's default session setting of 10 minutes. There is an undocumented BullHorn parameter setting for session length.**

  1. **Get Elements OAuth Information **http://api.cloud-elements/elements/api-v2/elements/bullhorn/oauth/url?apiKey=insert_bullhorn_client_id&apiSecret=insert_bullhorn_client_secret&callbackUrl=www.mycoolapp.com/auth 
    1. The result of this API invocation is an OAuth redirect URL from the endpoint. Your application should now redirect to this URL, which in turn will present the OAuth authentication and authorization page to the user. When the provided callback URL is executed, a code value will be returned, which is required for the Create Instance API.
  2. **Create an Instance:** to provision a Bullhorn Element instance, use the /instances API: https://api.cloud-elements.com/elements/api-v2/instances win a body payload of: 

3\. Store the returned instance token to make subsequent API resource calls to post and/or retrieve protected data in BullHorn.

[Click here for the Cloud Elements BullHorn Element reference.](https://developers.cloud-elements.com/docs/elements/bullhorn/bullhorn-create-instance.html?elementId=1702)

Are you ready to reduce your t-shirt size? Take it to the next step, call my bluff with the above and try it out - here is a [How2 doc ](https://resources.cloud-elements.com/cloud-elements-how-tos/guide-to-cloud-elements-trial-contact-sync) with videos that will step you through not only the aspects above, but also how to put all the other aspects of your integrations on a Hollywood diet. Soon, all your integrations will be a size small.

Be good, aloha.
