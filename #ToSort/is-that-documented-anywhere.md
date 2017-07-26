# Is That Documented Anywhere?

_Captured: 2017-06-06 at 10:40 from [dzone.com](https://dzone.com/articles/is-that-documented-anywhere?utm_source=MVB&utm_medium=email&utm_campaign=Monday%202017-6-05)_

"Is that documented anywhere?" or "I am waiting for the documentation," are things you may have said or heard in relation to consuming another application's services. It's natural to require some assistance in the form of documentation when one does not know how to use the service.

How often are those questions asked when talking about an application with a UI? In this scenario, you are provided with a starting link, from which navigation throughout the rest of the system is made possible by subsequent links. The ability to navigate (via logically named links) is core to how one familiarizes themselves with the functionality that a UI exposes. For example, if I click on a link called "Change Password," I fully expect it to allow me to change my password, and if it does, then I know that this application allows the changing of passwords.

Given the value of navigation as a means of understanding functionality, I will look to apply it in a sample REST application.

## The Goal

The goal will be twofold:

  * Inform consumers about the application's functionality by providing them with a single starting link.
  * Avoid the need to create documentation external to the codebase.

I am going to start by using [Spring HATEOAS](http://docs.spring.io/spring-hateoas/docs/current/reference/html/) to create a navigable REST service. You can find the example on [Github](https://github.com/mahanhz/clean-architecture-example) (which uses the same repository from my previous article about clean architecture). This example application allows one to view customer details and edit them.

## The Example

Just like building a UI, one needs to think about what links should be available per response. The links will reside inside controllers, and for this example, I will start with these two:

**IndexController** - this will be the starting point of the application and will contain only links.

**CustomerController** - this will control the navigation related to customers and contain data as well as links.

One thing to note is that every response should contain a link to self, which will indicate where you are.

In Spring HATEOAS, links can be derived by linking to and calling the methods on controllers. This can be achieved by using the following Spring classes:

  * ControllerLinkBuilder
  * ResourceSupport
  * Link

### IndexController

This will have the following links:

  * self
  * customers

The self link can be created straight away, but we will have to wait with the customers link until the CustomerController is created.

The IndexController currently looks like so:
    
    
    @RequestMapping(path = { "/", "/api" }, produces = MediaTypes.APPLICATION_JSON_V1_VALUE)

When finished, the output will look like below:

One thing to point out here is that I am using a custom Media Type (application/vnd.example.clean.v1+json). This allows for future API versioning (or resource versioning, to be more accurate), should it be deemed necessary (or as a last resort!).

If I had used application/json, then the responses would be sent as application/hal+json, which would look like below (this can also be turned off via property spring.hateoas.use-hal-as-default-json-media-type):

### CustomerController

I am not going to go through every method, as you can look through the [Github](https://github.com/mahanhz/clean-architecture-example) repository for that.

I will only focus on the customers and customer links, as it brings up a question as to whether HATEOAS is enough on its own to achieve the goals.

The **customers** method will have the following links:

  * self
  * home
  * create a new customer link (this is a POST request)
  * link for each customer

The **customer** method will have the following links:

  * self
  * home
  * update the customer (this is an PUT request)
  * delete the customer (this is a DELETE request)
  * customers

All the links are navigable, but create, update, and delete are not GET requests, they are POST- PUT and DELETE respectively.

So, how does one provide consumers with the details to perform these altering actions?

## Documentation Inside Your Codebase

This is where one can use the complimentary benefits of [Swagger](http://swagger.io/). Swagger can be used to generate documentation about the REST services, which will be available at a location from within the application. This can then be shared with a consumer.

In this case, [SpringFox](http://springfox.github.io/springfox/) will be used. To get it to work is fairly simple:

  * Add the dependencies to the build file (web module in the example application).
  * Add a Swagger @Configuration file with @EnableSwagger2 and a Docket bean.

**Note:** If you prefer Swagger to be in "read-only" mode (e.g., when in production) then that can be configured by adding a UiConfiguration bean.

The URL should be available at **/swagger-ui.html** (in the Github example it can be located at http://localhost:13001/swagger-ui.html).

It's impossible to say that this approach is always enough, but I think that using HATEOAS and Swagger can greatly assist consumers in understanding the functionality of an application, and how to consume it.
