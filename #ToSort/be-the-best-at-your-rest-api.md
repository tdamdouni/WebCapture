# Be the BEST at your REST API!

_Captured: 2018-05-25 at 19:39 from [dzone.com](https://dzone.com/articles/be-the-best-api-you-can-be?edition=379191&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-05-25)_

SnapLogic is the leading self-service enterprise-grade integration platform. Download the [2018 GartnerMagic Quadrant for Enterprise iPaaS](https://dzone.com/go?i=289438&u=https%3A%2F%2Fwww.snaplogic.com%2Flp%2Fdz-download-2018-gartner-magic-quadrant-for-enterprise-integration) or [ play around on the platform, risk free, for 30 days](https://dzone.com/go?i=289438&u=https%3A%2F%2Fwww.snaplogic.com%2Ffree-trial%3Futm_source%3DDZ).

Writing an API that works well and also easily for developers to implement is a must-have skill for any architect, designer, or team who is creating an API. It will matter much less if the API is being used for internal or external users because a well-written API will open many gates to excel at the intention of creating an API.

There is a long debate going on on the internet about the best ways to design the APIs, and it is one of the most discussed and sometimes fought topics among people. There are no official guidelines defined for how to make a perfect API.

Today, I will be sharing the experience that I have gained over the years about how to write good APIs that are not hated but well received by Developers/Users.

A good API is like a Mozart symphony. If you hit all the right notes and read the correct rhythm, the magic of music will happen.

## **What Is an API? -- **The Symphony****

API is the acronym for Application Programming Interface, which is a software intermediary that allows two applications to talk to each other. Each time you use an app like Facebook, send an instant message, or check the weather on your phone, you're using an API.

API is an interface through which many developers interact with the data. A well-designed API is always very easy to use and makes the developer's life very easy. API is the GUI for developers, and if it is confusing or not verbose, then the developer will start finding alternatives or stop using it. Developers' experience is the most important metric to measure the quality of APIs.

## 1) Terms We Should Know Even Before We Write First API

The following are the most important terms related to REST APIs:

  * **Resource** is an object or representation of something, which has some associated data with it and there can be set of methods to operate on it. E.g. Animals, schools and students are resources and _delete, add, _and _update _are the operations to be performed on these resources.
  * **Collections** are set of resources, e.g _Colleges_ is the collection of _College_ resource.
  * **URL** (Uniform Resource Locator) is a path through which a resource can be located and some actions can be performed on it.

## **2) API Endpoint -- The Music Notes**

Let's write few APIs for **Colleges** which has some **Students,** to understand more.  
_ /getAllStudents_ is an API which will respond with the list of students. Few more APIs around a **College** will look like this:

  * _/addNewStudent_
  * _/updateStudent_
  * _/deleteStudent_
  * _/deleteAllStudents_
  * _/promoteStudent_
  * _/promoteAllStudents_

There will be tons of other API endpoints like these for different operations. All of those will contain many redundant actions. Hence, all these API endpoints would be burdensome to maintain when API count increases.

**What is wrong?**  
The URL should only contain resources(nouns), not actions or verbs. The API path _/addNewStudent_ contains the action addNewalong with the resource name Student.

**Then what is the correct way?**  
_/colleges_ endpoint is a good example, which contains no action. But the question is how do we tell the server about the actions to be performed on colleges resource viz. whether to add, delete, or update?

This is where the _HTTP methods_ (GET, POST, DELETE, PUT), also called verbs, play the role.

The resource should always be plural in the API endpoint, and if we want to access one instance of the resource, we can always pass the ID in the URL.

  * method GET path _/colleges_ should get the list of all colleges
  * method GET path _/colleges/26_ should get the detail of college 26
  * method DELETE path _/colleges/26_ should delete college 26

In few other use cases, if we have resources under a resource, e.g Students of a College, then few of the sample API endpoints would be:

  * GET _/colleges/3/students_ should get the list of all students from college 3
  * GET _/colleges/3/students/45_ should get the details of student 45, which belongs to college 3
  * DELETE _/colleges/3/students/45_ should delete student 45, which belongs to college 3
  * POST _/colleges_ should create a new college and return the details of the new college created

**Point to remember:** The paths should contain the plural form of resources and the HTTP method should define the kind of action to be performed on the resource.

## **3) HTTP Methods (Verbs) -- The Music Tempo**

HTTP has defined few sets of methods, which indicates the type of action to be performed on the resources.

Keep in mind and think about the URL as a sentence where resources are nouns and HTTP methods are verbs.

The important HTTP methods are as follows:

  1. GET method requests data from the resource and should not produce any other data manipulations. E.g _/colleges/3/students_ returns a list of all students from college 3.
  2. POST method requests the server to **create** a resource in the database, mostly when a web form is submitted. Here the important thing to remember is** create. **It should only create new resources. No modifications to existing resources should be done by using POST. E.g _/colleges/3/students_ creates a new Student of college 3. POST is _non-idempotent,_ which means multiple requests will have different effects i.e. every time we make a call to POST method a new record or resource will be generated.
  3. PUT method requests the server to **update** the resource or **create** the resource if it doesn't exist. E.g. _/colleges/3/students/john_ will request the server to update, or create if doesn't exist, the _john_ resource instudentscollection under college 3. PUT is _idempotent_ which means multiple requests will have the same effects.
  4. DELETE method requests that the resources, or its instance, should be removed from the database. E.g _/colleges/3/students/john/_ will request the server to delete _john _resource from the students collection under the college 3. These are major methods that are should and will cover most of your requirements for an API. There are few more methods available but those are seldom used. You can definitely go and check the HTTP method official specification.

## **4) HTTP Response Status Codes -- The Melody **

When the client raises a request to the server through an API, the client should know the feedback, whether it failed, passed, or the request was wrong. HTTP status codes are a bunch of standardized codes that have various explanations in various scenarios. The server should always return the right status code.   
The following are the important categorization of HTTP codes:

**2XX (Success category)**

These status codes represent that the requested action was received and successfully processed by the server.

  * **200 Ok **The standard HTTP response representing success for GET, PUT or POST.
  * **201 Created **This status code should be returned whenever the new instance is created. e.g. on creating a new instance, using POST method, should always return 201 status code.
  * **204 No Content **represents the request is successfully processed but has not returned any content. DELETE can be a good example of this. The API DELETE _/colleges/43/students/2_ will delete the student 2 and in return, we do not need any data in the response body of the API, as we explicitly asked the system to delete. If there is any error, like if student 2 does not exist in the database, then the response code would not be of 2XX Success Category but around 4XX Client Error category.

**3XX (Redirection Category)**

  * **304 Not Modified** indicates that the client has the response already in its cache. And hence there is no need to transfer the same data again.

**4XX (Client Error Category)**

These status codes represent that the client has raised a faulty request.

  * **400 Bad Request** indicates that the request by the client was not processed, as the server could not understand what the client is asking for.
  * **401 Unauthorized** indicates that the client is not allowed to access resources, and should re-request with the required credentials.
  * **403 Forbidden **indicates that the request is valid and the client is authenticated, but the client is not allowed access the page or resource for any reason. e.g. sometimes the authorized client is not allowed to access the directory on the server.
  * **404 Not Found **indicates that the requested resource is not available now.
  * **410 Gone **indicates that the requested resource is no longer available which has been intentionally moved.

**5XX (Server Error Category)**

  * **500 Internal Server Error** indicates that the request is valid, but the server is totally confused and the server is asked to serve some unexpected condition.
  * **503 Service Unavailable **indicates that the server is down or unavailable to receive and process the request. Mostly if the server is undergoing maintenance.

## **5)Field Name Casing Convention for Your Data **

You can follow any casing convention, but make sure it is consistent across the application. If the request body or response type is _JSON,_ then please follow camelCase to maintain the consistency.

## **6) Searching, Sorting, Filtering, and Pagination**

All of these actions are simply the query on one dataset. There will be no new set of APIs to handle these actions. We need to append the query params with the GET method API.  
Let's understand with few examples how to implement these actions.

  * **Sorting -- **In case the client wants to get the sorted list of colleges, the GET _/colleges_ endpoint should accept multiple sort params in the query. E.g GET _/colleges?_colleges?sort=rank_asc__ would sort the colleges by its rank in ascending order.
  * **Filtering -- **For filtering the dataset, we can pass various options through query params. E.g GET _/colleges?_category=engineering&location=tokyo__ would filter the colleges list data with the college category of Engineering and where the location is Tokyo.
  * **Searching -- **When searching the college name in colleges list the API endpoint should be GET _/colleges?_search=_College of Engineering_
  * **Pagination -- **When the dataset is too large, we divide the data set into smaller chunks, which helps in improving the performance and is easier to handle the response. Eg. GET _/colleges?_page=23__ means get the list of colleges on 23rd page.

If adding many query params in GET methods makes the URI too long, the server may respond with 414 URI Too long HTTP status, in those cases params can also be passed in the request body of the POST method.

## **7) Versioning -- The Success**

When your APIs are being consumed by the world, upgrading the APIs with some breaking change would also lead to breaking the existing products or services using your APIs.

_http://api.univercity.com/v1/colleges/26/students_ is a good example, which has the version number of the API in the path. If there is any major breaking update, we can name the new set of APIs as v2 or v1.x.x

_http://api.univercity.com/v1/colleges/26/students_

_http://api.univercity.com/v1.2/colleges/26/students_

_http://api.univercity.com/v2/colleges/26/students_

This way, you can keep the different versions of your API running without impacting your existing users.

So here we come to the end of few guidelines that I put forward with my experience of API development. I would love to know your views about mentioned above fundamentals. Please leave a comment, and let me know!

If you liked this post, please share and comment.

With SnapLogic's integration platform you can save millions of dollars, increase integrator productivity by 5X, and reduce integration time to value by 90%. [Sign up for our risk-free 30-day trial!](https://dzone.com/go?i=286431&u=https%3A%2F%2Fwww.snaplogic.com%2Ffree-trial%3Futm_source%3DDZ)

Topics:

api architecture ,http ,api best practices ,rest api ,practical approach to api ,integration ,api

Opinions expressed by DZone contributors are their own.
