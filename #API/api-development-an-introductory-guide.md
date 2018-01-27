# API Development – An Introductory Guide

_Captured: 2018-01-26 at 18:08 from [dzone.com](https://dzone.com/articles/api-development-an-introductory-guide?utm_source=Top%205&utm_medium=email&utm_campaign=Top%205%202018-01-263)_

The Integration Zone is brought to you in partnership with [Cloud Elements](https://dzone.com/go?i=263425&u=https%3A%2F%2Fresources.cloud-elements.com%2Febooks-private%2Fguide-to-api-integrations-ebook%3Futm_campaign%3DAPI%2BIntegration%2BeBook%26utm_medium%3Ddisplay%26utm_source%3Ddzone). What's below the surface of an API integration? Download [The Definitive Guide to API Integrations](https://dzone.com/go?i=263425&u=https%3A%2F%2Fresources.cloud-elements.com%2Febooks-private%2Fguide-to-api-integrations-ebook%3Futm_campaign%3DAPI%2BIntegration%2BeBook%26utm_medium%3Ddisplay%26utm_source%3Ddzone) to start building an API strategy.

Most modern applications use APIs to build the core of the application upon which the graphical interfaces are built. These interfaces can be mobile apps, desktop applications, and even websites. By having the business logic in a central place, you enjoy the benefit of only having to develop the most complex piece of code just once, and then using that elsewhere.

The APIs you write will most likely be 'consumed' by other developers within or outside your organization depending on whether your API is private or public. Make sure you spend time in the design process and that your APIs are developer-friendly.

In this article, Tahir Malik, our head of R&D at dinCloud, mentions important guidelines to keep in mind while developing APIs.

### **Build RESTful Endpoints:**

An endpoint in an API is essentially a URL that performs certain functionality, whose output varies depending upon the HTTP method you use to call it. These endpoints must be meaningful and must represent your resources in nouns, not verbs. Consider an example where we want to create an endpoint to return user data in our database when the endpoint is called. The two endpoints you may decide to create could be:

_1\. yoursite.com/user_

_2\. yoursite.com/get-user-data_

The first example is RESTful, as 'user' is a noun, whereas in the second example we are using a verb, 'get.'

Verbs are handled using HTTP methods, which, in a way, means your mapping with CRUD operations in your database.

  * _GET /users_ \- Use this method to only retrieve (READ in CRUD) data of a given resource. _Example: Read user's profile data for display._
  * _POST /users_ \- Use this method to create a new entity in a given resource. _Example: Create a new user in your system._
  * _PUT /users/11_\- Update an existing resource completely. _Example: Update all fields of the User record in the database._
  * _PATCH /users/11_ \- Partially update an existing resource. _Example: Update email address only in the database and leave other fields as they are._
  * _DELETE /users/11_ \- Delete an entity. _Example: Delete the user record in your database._
  * _OPTIONS /users_ \- Provides a list of HTTP methods supported by your endpoint. _Example: Users endpoint may only have GET, POST, and DELETE methods supported, but not PATCH._

Endpoints must be consistent to eliminate guesswork for developers. For this purpose, always use plural for resources. For instance, 'user' entity must be presented as '`/users`' not '`/user`.'

You are likely to have resources with relations to other resources. Consider that you have another resource, 'addresses,' that has a relation to 'users.' Every user in the system may have different addresses. In your API, you can handle this relation like this:

  * _GET /users/11/addresses_ \- Retrieve all addresses linked with user 11.
  * _GET /users/11/addresses/3_ \- Retrieve all addresses linked with user 11.
  * _POST /users/11/addresses_ \- Create a new address for user 11.
  * _PUT /users/11/addresses/3_ \- Update the complete address with ID 3 for userID 11.
  * _PATCH /users/11/addresses/3_ \- Partially Update the address with ID 3 for the userID 11.
  * _DELETE /users/11/addresses/3_ \- Delete address #3 for the user # 11.

**Note:** '11' and '3' in the above examples are identifiers (primary keys) of the records that you are trying to modify. I recommend using UUID instead of plain IDs for this purpose.

**Your application must use SSL: **SSL must be used to encrypt your API communication with consumers even if it's happening within your internal applications. This will reduce the risks of eavesdropping and credential hijacking significantly.

**HTTP Errors: **Your API must be able to handle all kind of requests and return errors in as descriptive a form as possible. The following are the default HTTP error codes you can use:

200 - Generic everything is OK.

201 - Created something OK.

202 - Accepted but is being processed a sync (power off, provisioning, etc.).

400 - Bad Request (invalid syntax).

401 - Unauthorized (no current user and there should be).

403 - The current user is forbidden from accessing this data.

404 - That URL is not a valid route, or the item resource does not exist.

410 - Data is deleted or doesn't exist.

405 - Method Not Allowed (calling post method when only get is allowed, etc.).

500 - API internal error.

503 - System is in maintenance mode.

You can also use custom error codes along with the HTTP ones to simplify the response and improve the documentation.

Example: 401 '_123_','you must be logged in'

### **Documentation:**

Put effort into your documentation, especially for public APIs. Clearly define your endpoints, their methods, and error messages with examples. Having examples of requests and responses will help you reduce the number of queries you may get from consumers. If your API has multiple versions, you should maintain their documentation separately.

### **JSON vs. XML:S**

If possible, avoid using XML at all. It is old, hard to read, and not supported by most platforms these days. Some legacy and enterprise apps still require XML though.

If your API supports both JSON and XML, change the output based on the requested format. This format can be requested in the URL in the form of an extension "/users.xml", query string "/users?" or in request headers. I prefer URLs to headers as it makes it easy to explore APIs in the browser.

### **API Versioning:**

APIs must be versioned to avoid pitfalls for API consumers. As your application and adoption rates grow, you are likely to add more functionality that may not be possible without expanding existing code and models. To address that, you may have to introduce new functionality in a different version.

Versions can be added to the URL 'mysite.com/v1/users' or in the header of the request.

### **Upgrades and Compatibility:**

When creating a new version of an API, it's important to check for backward compatibility. Especially if you have a large community using your APIs, you want to avoid a new upgrade breaking someone's queries.

### **Search and Filtering:**

I recommend using a query string for search and filtering options, as it makes it easier for programmers to not just implement that, but also to do quick tests in the browser.

Example: `GET /users?`

### **Pagination:**

Pagination should be implemented using limit and offset. If a consumer does not pass these variables, there should be default values set for both. I prefer query strings for pagination.

`GET /users?&`

Use the custom HTTP header, _X-Total-Count_, to include the total number of records in your response, as well as links to previous and upcoming pages in your HTTP header link.

### **Final Words:**

While all of the above information may appear daunting at first, it will get easier as you dive deeper into APIs and start building some endpoints on your own. The good news is that all major programming languages provide existing API frameworks that you can leverage to build your own API. Most of these frameworks do all the heavy lifting for you and you just have to focus on your business logic implementation.

Designing APIs is an art and it is like creating a GUI for the developers who will be consuming your API. Just like having a great UI makes users happy, having a good API will make your consumers happy.

Your API is not enough. Learn why (and how) leading SaaS providers are turning their products into platforms with API integration in the ebook, [Build Platforms, Not Products](https://dzone.com/go?i=263426&u=https%3A%2F%2Foffers.cloud-elements.com%2Fbuild-platforms-not-products-ebook%3Futm_campaign%3DPlaforms%25252C%252520Not%252520Products%252520eBook%26utm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_content%3Dtext) from Cloud Elements.

Opinions expressed by DZone contributors are their own.
