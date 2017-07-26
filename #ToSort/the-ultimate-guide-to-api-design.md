# The Ultimate Guide to API Design

_Captured: 2017-03-09 at 21:13 from [blog.qmo.io](https://blog.qmo.io/ultimate-guide-to-api-design/)_

So you need to design an API. Where do you start? Far too often internal services slowly turn into APIs. Hacked together one endpoint at a time. These undocumented spaghetti monsters just pile up technical debt and create enormous knowledge hurdles for new developers to scale over. This article is designed to help you either **start with a good footing** from scratch or to **refactor your existing API** into something far more manageable.

## The ToC

  1. Task Automators
  2. RESTful Architecture
  3. Core API Design   

a. HTTP Methods   
b. URL Path

  4. CRUD
  5. Listing
  6. Pagination
  7. Adhoc Queries
  8. Response Codes
  9. Error Handling
  10. Security   

a. SSL Encryption   
b. User Roles   
c. Basic Authentication   
d. OAuth2

  11. Versioning
  12. Documentation
  13. API Schemas
  14. Caching
  15. Conclusion
  
## Task Automators

![](https://blog.qmo.io/content/images/2017/02/image-task-automation.png)

A small detour, but it's always better to ask the tough questions first. **Do you even need an API**? This isn't a silly question. Most of the time this will be yes, but those other times you can save _A LOT_ of time by doing less development and look like a superstar.

Welcome to task automators. Some of you may be familiar with [IFTTT](https://ifttt.com/) (If This Than That) but IFTTT is intentionally designed to be consumer facing and is not equipped to handle many of the tasks you'd probably need. [1](https://blog.qmo.io/ultimate-guide-to-api-design/)

A newer API wrangler with plenty of **business integrations** is [Zapier](https://zapier.com/). Having all your cloud apps work together has never been easier. As of right now, Zapier provides over 750 integrations so almost all your cloud services will play nicely.

![](https://blog.qmo.io/content/images/2017/02/Zapier.png)

> _Source: Zapier_

Not only that but they offer **custom webhooks** so you can easily trigger anything with a simple HTTP call. Want to create a JIRA ticket when a critical error happens on your server? Easy. Sending an email, slack message or even a text is just a request away. Zapier also offers filters so you can have more flexibility by ensuring tasks are done only when you're sure you want them to be.

Another player in the API integration business you might want to check out is [CloudPipes](https://www.cloudpipes.com/). I've only lightly tested their service but they have many of the same features as Zapier. They certainly have less backing and it shows, but more options are always good to have so feel free to see how they stack up for your use case.

## RESTful Architecture

If you've gotten this far, you need an API. There are [many types of APIs](https://en.wikipedia.org/wiki/Application_programming_interface#Uses) but for this article, I'll focus on the main one these days - [REST APIs](https://en.wikipedia.org/wiki/Representational_state_transfer).

There are [6 key tenets](https://en.wikipedia.org/wiki/Representational_state_transfer#Architectural_constraints) that go into REST. I'll assume most of you are familiar with client-server (it isn't 1998 anymore) so I'll skip that. The main one to focus on is the concept of [statelessness](http://stackoverflow.com/questions/34130036/how-to-understand-restful-api-is-stateless). All the other aspects of REST rely extensively on having a **stateless API**.

> In REST applications, there must not be session state stored on the server side. Instead, it must the [sic] handled entirely by the client.
> 
> So, if there's session state on the server, it's not REST.
> 
> \-- Cassio Molin

Cassio wraps it up quite succinctly. **Don't save session state on your APIs**.

_Why is this?_

If we save session state on an API it is no longer considered stateless. Statelessness gives a huge benefit as it allows you to use the **full power of the cloud** to seamlessly switch from serving requests from Server A and Server B.

_Is your application receiving a huge spike in requests?_

Spin up a couple more servers and the users will be none the wiser.

Let's say you don't adhere to this. You're saving session data on your API and running it on two machines behind a load balancer. A user's first request goes to Server A, which saves all relevant information about where they are. They're authenticated on that server and maybe even storing other information like their latest requests there. What happens when instead of Server A they're now sent to Server B by your load balancer? Their authentication doesn't work and that machine knows nothing about them. 😓 Sad! Just make your API stateless and your DevOps team will thank you.

## Core API Design

![](https://blog.qmo.io/content/images/2017/02/image-api.png)

Now we plan our API patterns. There are always a few concerns here but taking a little time to make a coherent design will save you and your clients future headaches.

The primary things to consider when designing your API are the **HTTP methods**, **URL path**, how you're going to handle **adhoc queries** as they come up (assume your boss/client will ask for something unexpected, it never fails), and of course, the **response structure**.

##### HTTP Methods

Mozilla has a great reference for the definition of each [HTTP Method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods). Some of these will look familiar like `GET` and `POST` but others like `CONNECT` or `OPTIONS` will be far less familiar to most people.

Try to keep to the **standard meaning** of each of these when you're designing your API. We've all seen APIs built with only the `GET` method even when you're creating and updating objects. Frankly, they're idiots. Using the wrong methods on your API makes it less readable and can cause [serious problems](http://stackoverflow.com/a/1211897/2308157) for your service. Let's make APIs less chaotic by following the standard meaning of the methods.

`GET` is used when you query or retrieve an object or list of objects. Don't update anything (other than maybe audit logs) when the action is triggered from a `GET`.

`POST` is for when you want to **create** an object.

DELETE

`DELETE` is obvious. 💀 If you want to restrict access to your API in the future, these would be a great starting point.

PUT & PATCH

`PUT` and `PATCH`. These guys are the more controversial of the bunch and often misused. If you have a `PUT` endpoint it is supposed to "...replace all current representations of the target resource with the request payload." With `PUT` your client needs to send the **entire object** they wish to store, which should replace the entire record in the database. But with `PATCH` you send **part of the object** and only the fields specified will be saved while unmentioned fields will remain untouched.

URL path is the most visible to end users of your API so keeping this to a pretty pattern is a great starting place. One easy way to beautify your URLs is to **avoid query parameters** whenever possible. Let's see one example of this where we're trying to get the data of User with id `3749`.

`GET` `/search?type=User&id=3749`

`GET` `/user/3749` or generally as `/user/{id}`

## CRUD

We've seen an example of how to find a user by ID, but there are many other request types. Create, Read, Update and Delete or [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) is a common concept with APIs. The example we did above is an example of reading. If we continue out with our user example let's fill out the rest of CRUD access.

  * [Read](https://blog.qmo.io/ultimate-guide-to-api-design/) \- `GET` `/user/{id}`
  * [Update](https://blog.qmo.io/ultimate-guide-to-api-design/) \- `PUT` & `PATCH` `/user/{id}`
  * [Delete](https://blog.qmo.io/ultimate-guide-to-api-design/) \- `DELETE` `/user/{id}`

Request: `POST` `/user`
    
    
    {
      "name": "Alan Turing",
      "age": 32
    }
    

Response:
    
    
    {
      "id": 3,
      "name": "Alan Turing",
      "age": 32
    }
    

With our create request we passed in the body of our object and got back a saved version along with the newly minted ID which we can now use to search.

Request: `GET` `/user/3`
    
    
    NO BODY  
    

Response:
    
    
    {
      "id": 3,
      "name": "Alan Turing",
      "age": 32
    }
    

This response is fairly simple, giving us back our newly created user.

##### Update (Partial)

Request: `PATCH` `/user/3`
    
    
    {
      "age": 41
    }
    

Response:
    
    
    {
      "id": 3,
      "name": "Alan Turing",
      "age": 41
    }
    

With our partial update, we used `PATCH`, so **only the age** field was updated and the name field was untouched.

##### Update (Replace)

Request: `PUT` `/user/3`
    
    
    {
      "name": "Roy Fielding"
    }
    

Response:
    
    
    {
      "id": 3,
      "name": "Roy Fielding"
    }
    

The replacement update **totally replaces** the user. Since we only sent the name field, the age is no longer present as it wasn't set in the request.

Request: `DELETE` `/user/3`
    
    
    NO BODY  
    

Response:
    
    
    {
      "id": 3
    }
    

The response of the `DELETE` method doesn't need to respond with anything, but I've seen the ID passed back as a form of success. However, responding with an empty body is perfectly fine as well.

## Listing

With CRUD we've covered basic access to our objects, but this is still not enough for most applications. A common requirement you'll want to support is a filterless **search of objects**. If we stick with our user example you'll have something like this:

Request: `GET` `/user`
    
    
    NO BODY  
    
    
    
    {
      "data": [{
        "id": 1,
        "name": "Tim Berners-Lee",
        "age": 61
      }, {
        "id": 2,
        "name": "Ada Lovelace",
        "age": 36
      }, {
        "id": 3,
        "name": "Roy Fielding"
      }]
    }
    

You'll notice we received a list of users in the system but we placed it under a field called `data`.

_Why is this?_

For many developers you want to send back as little as possible unless it's required, but with APIs you'll find they have a tendency to have extra requirements over time. Placing the result under a field allows the **flexibility** to send other information with your result so you're ready for those changes as they come.

_What else would you want?_

It is typical for certain metadata to be sent along with the request to make it easier on the client. For instance, let's say you want to add the url that was called along with the date and result size.

Response:
    
    
    {
      "url": "https://example.com/user",
      "datetime": "2017-02-27T11:43:37+0500",
      "data": [...],
      "elements": 3
    }
    

So with the data not at the root level we're flexible and happy no matter what is thrown our way.

## Pagination

##### `GET` `/user?size={size}&page={page}`

So with our tiny list of 3 users, it's quite manageable but what happens if we have 500 users? What about 12,000? There is a point where loading them all will create massive **performance issues**. That's where [pagination](https://en.wikipedia.org/wiki/Pagination#Pagination_in_electronic_display) comes in. Paging reduces the strain on your database and also reduces your bandwidth while speeding up the response time. It almost seems like a **no-brainer** for most situations.

Request: `GET` `/user?size=1&page=2`
    
    
    NO BODY  
    
    
    
    {
      ...
      "data": [{
        "id": 2,
        "name": "Ada Lovelace",
        "age": 36
      }],
      "elements": 1
      "page": {
        "size": 1,
        "page": 2,
        "total": 3
      }
    }
    

So we asked the API to **restrict our results** to just 1, and that we would like the 2nd page. We also added paging information along with the request so the client can see what was requested along with the total number of items. We could have returned the number of pages as well, but that is a calculable value based on the page size and the total number of items.

## Adhoc Queries

##### `GET` `/search/findUserByAge?age={age}`

We've covered the most common searches you'll need to get your API chugging along. But like we mentioned, there are always **extenuating circumstances** that will come up. To handle these, we have the `/search/` path to hold our adhoc searches. You can come up with your own pattern for the naming of these adhoc queries, but **keep it simple** (hopefully even self-descriptive) for other developers to understand while still **following a pattern**.

Request: `GET` `/search/findUserByAge?age=61`
    
    
    NO BODY  
    
    
    
    {
      ...
      "data": [{
        "id": 1,
        "name": "Tim Berners-Lee",
        "age": 61
      }],
      "elements": 1
    }
    

## Response Codes

![](https://blog.qmo.io/content/images/2017/02/image-response-codes.png)

The URL path, query parameters, and body make up the bulk of each HTTP request, but there is a secret weapon hidden in our midst. [Headers](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields). There are plenty of standard header fields but the one we care about right now is the **status of the response**.

When designing an API, you should be returning proper [response codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes). To meet the bare requirements, you should respond with a `Status: 200 OK` on successful requests and `Status: 500 Internal Server Error` if there's a problem processing the request. Sending back a 201 on creation is a bonus.

Most web servers like [NGINX](https://www.nginx.com/) will send back relevant 301s when the page has moved and 404s when the path is not found, so you shouldn't worry about those. However, remember to return a 404 when a request is sent to a **non-existent ID**.

## Error Handling

_You've got proper response codes, but what happens when something is missing or the data is mangled?_

That's where validation and error handling come in. Client side validation is good UX, but server side **validation is mandatory**. If you don't validate on the server side, developers can either accidentally or maliciously misuse and corrupt your API and the data behind it.

Let's jump back to our examples of users. We now want name to be mandatory, so if I try to create (or update) a user without a name I should get an error back.

Request: `POST` `/user/`
    
    
    {
      "age": 23
    }
    
    
    
    {
      "error": 400,
      "message": "User must have a name"
    }
    

For validation errors, the standard status code to use is `Status: 400 Bad Request`. But along with that header, we also return a JSON body with a useful explanation for debugging the situation. This helps programmers and end users **fix their issues** with fewer support tickets clogging up your issue management system.

## Security

![](https://blog.qmo.io/content/images/2017/02/image-security.png)

Up to this point, we've been happily creating our API without concern about who has permission to access what. This is where our security comes in. Even the most open APIs would need to **restrict deletion privileges** or one bad actor could come in and remove all the data.

You should also keep in mind the **sensitivity of data**. We've been working on the example of users for our API, but typically user data is confidential as it contains personal information like address or maybe even banking credentials. Your users expect and deserve their data to be safeguarded.

Everything these days should go **behind SSL**. While you don't want to be paranoid, it is far too easy for people to snoop on public networks like Starbucks. Encryption is a **simple weapon** to keep your customer's data out of the wrong hands. Having that green lock in the address bar gives your clients a **sense of safety** with your products as a big bonus.

[Let's Encrypt](https://letsencrypt.org/) is a **free provider** of certificates. SSL certificates work easily on every major webserver. Personally, I find the [NGINX implementation](http://nginx.org/en/docs/http/configuring_https_servers.html) the simplest to get started with but they work with Apache and all others.

Almost every API will need to manage roles. Roles are a way of **granting access** to parts of your API without doing it per user. Instead, users are granted certain roles and those roles are checked to see if an action can be performed. If the user is not allowed to perform an action or has not provided valid credentials, you should return an error using `Status: 401 Unauthorized`.

##### Basic Authentication

[Basic auth](https://en.wikipedia.org/wiki/Basic_access_authentication) is your standard fare username and password type authentication. Typically you'll have usernames and hashed passwords stored in a database or you'll connect to another service like **LDAP** if your company has that.

You need to provide an endpoint for users to authenticate themselves, maybe `/auth`, and accept the username/password they'd like to use. If it is successful, you should pass back an **access token**.

To preserve statelessness, you'll want to cache the token server side outside the session with [Redis](https://redis.io/) being a popular choice for a token cache.

On the client side, you should save your token somewhere. For browser clients, this would be in a **cookie or local storage**.

Now that you have your token, make all requests to the API using the header `Authorization: Basic <YOUR_TOKEN>`. All your **protected endpoints** should be checking for this and validating incoming tokens against your token cache. If the token is valid but doesn't have access to an action you should respond with `Status: 403 Forbidden`

##### Password Encryption

Please don't keep plain text passwords sitting around! 😧 There are libraries in **all major languages** to handle proper encryption like [bcrypt](http://stackoverflow.com/a/14015883/2308157) for NodeJS and the [default security](http://stackoverflow.com/a/33085670/2308157) package for Java. Check to ensure you're using the latest algorithms as these update every couple years to make it harder for hackers to crack.

[OAuth2](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) is another **authorization scheme** and is easily more highly regarded than basic authentication. It is a huge topic and more complex than basic auth, but the benefits are great.

The primary reason OAuth has so many proponents is how it allows a third party to verify users without anyone in the middle. Your API can use an **OAuth provider** (such as Facebook or Google) to **validate** access behind the scenes.

We've all seen the 'Login with Facebook' buttons. What makes them work is OAuth. A user is **redirected** to Facebook to give consent for a third party to access your Facebook data through Facebook's API. Facebook then redirects you back to that third party along with **access tokens** they can save to confirm your identity and access your data.

## Versioning

APIs and the data behind them **change over time**. This could happen due to new requirements, new initiatives, and down the road deprecating old features that become obsolete. You'll want to keep this in mind when making your API.

##### What Not To Do

Some people prefer to make the assumption of making only backward-compatible changes. But this eventually **piles on features** and results in a bloated data model that becomes suffocating in short order.

Another more **reckless approach** is to just change the API whenever a requirement comes up. This has a way of infuriating your developer community as their products in production will break with every change, leaving them feeling like they are **building on quicksand**.

The way larger companies handle this is through versioning.

If you've ever used larger APIs you might have noticed a `/v2/` or `/v3/` in the path. This typically indicates the **API version** being used. Facebook is currently on v2.8 but supports the previous [few versions](https://developers.facebook.com/docs/graph-api/overview#versions) simultaneously as well. This is versioning and should be a familiar concept to most developers.

With versioning, you offer features across **various versions** that you intend to support, but with a certain shelf life. The benefit here is you can eventually modernize your API and the data model without having to continually support older releases.

The **problem** you'll encounter with versioning is supporting **multiple live versions**.

The solution: you generally want to put it under a versioned folder like `/v1/user` and `/v2/user`.

The safest way to handle multiple live APIs is to **keep the code separate** for v1 and v2. That way people using v1 can be assured that they won't see any changes to their stable calls as new API versions are released.

## Documentation

![](https://blog.qmo.io/content/images/2017/02/TwilioDocs.png)

> _Source: Mashape_

Maintaining & supporting the developer community is **at the core** of any good API. You want people to use it, and if they're going to use it, they need to be provided with **thorough documentation**. You don't need to beat them over the head with mundane details but you should at least have solid coverage of the core features and use cases **with examples**. Tutorials and examples help so absolutely include them.

One thing I notice that many API documentations miss is showing the **entire request and response**. Don't assume your clients can guess you only allow requests with `Content-type: application/json`. **If you require something**, state it or **show it explicitly** so they don't have to beg others on StackOverflow. Some developers won't bother with substandard documentation and would prefer to pack up and use something else.

##### Documentation Maintenance

You could try to document your API by hand coding HTML but this is a **daunting challenge**. With the enormity of your API, you're certain to make a mistake. You might forget to document a part, or you make a change to the format and forget to update the docs. This is how most teams end up with outdated and eventually completely obsolete documentation.

There are options to **auto-generate documentation** based on markup, which takes away the complexity of making and maintaining HTML yourself.

##### Documentation Tools

[Read the Docs](https://readthedocs.org/) is a freely hosted service which allows your markup to be auto-generated if you're using Python. The one caveat is your documentation will be public unless you pay to make it private.

A much more **versatile option** geared towards APIs is [ApiDocJS](http://apidocjs.com/). While you need NodeJS installed, it supports many languages other than Javascript such Java, C#, PHP, Python and Ruby. The downside of this is you're going to need many large comment blocks throughout your code.

Another tool for documenting your API is an API schema.

## API Schemas

Similar to other schemas such as [database](https://www.lucidchart.com/pages/database-diagram/database-models) or domain schemas, API schemas **describe metadata** about your interface.

A wonderful thing about defining your API as a schema is it provides a **language-agnostic** definition. Using these definitions there have been plenty of tooling which can generate documentation as well as SDKs in many languages. This cuts down the work you have to do to let your clients use your API in the language of their choice.

An article I found useful was one comparing a couple different [API documentation tools](https://opencredo.com/rest-api-tooling-review/). It's a little Java-centric but they touch on a couple of the top API schemas.

In order of popularity these are the **top three** at the time of writing:

**Swagger** has been a longtime favorite for schemas and hasn't slowed down with plenty of tooling upgrades being added to their [SwaggerHub](https://swaggerhub.com/). The [SwaggerEditor](http://swagger.io/swagger-editor/) lets you build your API definition and see the documentation as you make it, helping catch errors before they're a problem.

**API Blueprint** is open source and offers similar tooling as the others. They have a vibrant community of [plugins and tools](https://apiblueprint.org/tools.html#) including [Sublime Text Plugin](https://github.com/apiaryio/api-blueprint-sublime-plugin) and a [mock server](https://www.npmjs.com/package/drakov) that implements your schema for immediate testing before needing to code it out.

**RAML** is a great competitor and offers an [API Workbench](http://raml.org/developers/design-your-api) as well as several ways to export your schema to documentation.

## Caching

Once you've gotten your API running smoothly, you may have a breather for performance improvements. A common place people turn to for **performance improvements** is caching for their APIs.

HTTP offers a fantastic [built in caching](https://devcenter.heroku.com/articles/increasing-application-performance-with-http-cache-headers) using the `Cache-Control` header. Getting started is **simple** and won't require you to manage a large cache layer. If the request is sensitive, set `Cache-Control: private`, otherwise use `Cache-Control: public`.

Secondly, set the **latest date** the response should be valid, for example `Expires: Tue, 28 Feb 2017 21:31:12 GMT`. You'll generally want to set a **short expiration** like an hour so it doesn't get stale, but it depends on your data.

If the data is highly sensitive, you'll want to skip any caching entirely and use `Cache-Control: no-cache, no-store`.

## Conclusion

APIs may appear **deceptively simple** from first glance but hopefully this guide gives you a clear overview of where the complexity crops up. I tried to include **concrete examples** where I could and plenty of links with additional information. If you have any questions I didn't cover, I'll do my best to answer them in the comments below. Now go forth with purpose and make incredible APIs.
