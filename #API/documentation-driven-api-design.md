# Documentation-Driven API Design

_Captured: 2017-01-24 at 20:51 from [dzone.com](https://dzone.com/articles/documentation-driven-api-design?edition=265881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-24)_

Build APIs from SQL and NoSQL or Salesforce data sources in seconds.[ Read the Creating REST APIs white paper](https://dzone.com/go?i=142024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714743%3B137084581%3Bk), brought to you in partnership with [CA Technologies](https://dzone.com/go?i=142024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714743%3B137084581%3Bk).

Documentation doesn't have to be as Herculean a task as it is made to appear. This assumption has made documentation be seen as something to be done as an afterthought, which is usually a nightmare for any developer who has been assigned the difficult task of having to surf through each of the application's features in a bid to try to understand exactly what each method in the app is designed to do.

Most times, there's hardly any time left to work on the documentation of an application because of the deadline for the completion of the application. Thus, you find hurriedly scribbled information put out as the documentation for the application, with the developer hoping and praying that the app's end users don't get to discover some errors before he or she does.

How much better it would be if the documentation for an application is properly written so that its end users can rate it high.

How great it would be if this documentation became an invaluable resource and tool for a development team, in which you have already documented the details you need to before even writing a lot of code.

This document could be shared between the development teams like and testers and all could start working at the same time to implement such an API.

Documentation's place in API development is strengthened via interactivity. When you speak of the best documentations, you speak of the documentations that have the capacity to make API calls straight from the site in itself -- in other words, interactive documentation.

Once the audience and users can directly gain access and interact with the API from the documentation, it would help to increase the capacity of a developer to work successfully with the API in implementing a client.

These interactivity features can serve as a very invaluable tool for both the developer and the debugger.

## 3 API Documentation Design Features

These are three features that should be ever present in a documentation:

  1. **There should be consistency**, meaning that an end-user should be able to know what your documentation has in the offing. The terminology used should also be in line with your language.

  2. **The documentation should offer a complete scope of the entire features of your project.** Private methods used should also be put down for your developers to utilize. The public features should be made explicitly available for your end users.

  3. **It should also be current**, meaning that the documentation should maintain recent versions of the code used for the project.

There are also bonuses that your documentation has to offer.

Your documentation should serve as a guide that will assist your developer in building a consistent utility product, one that can be used to test run your API quality and can help in the enhancement of proper communication within your development team.

## Fundamental API Documentation Sections

You need authentication information describing which authentication scheme your API uses.

If you're using OAuth, don't forget to explain how to set up an OAuth application and obtain the API key and secret.

You need to explain errors and how they're communicated to API consumers. You should explain if you follow any error standard, i.e., the HTTP status codes and how errors are generally communicated inside responses.

You need to include endpoints and information on how to consume them, including requests and responses. This is considered the main section in which you expose all your API methods, explain how they can be reached, and note what kind of parameters are allowed.

With these three sections, you're off to a great start because you've already documented most of what is needed to consume your API and your offering.

As you're about to find out, this is often not enough. As you obtain more sophisticated consumers, you'll end up having to offer them documentation on non-functional aspects of your API.

For your developers or testers, having some sort of an API mock based on your documentation could be a fantastic boost to the development.

## What API Documentation Should Contain

There are, of course, no standards or hard-and-fast rules on what API documentation should have. As a general rule, whatever resonates with the developer community and makes it easy for them to understand an API is a good starting point.

Some general sections that are backed up by examples from established providers in the API economy:

  * **A list of the resources** with an explanation of the purpose of each in the context of the product or service being offered via the API.

  * **Examples of API calls **in a variety of languages and tools (cURL, Postman collections, etc.). The examples are probably the most important section of the API document, as this is going to be used by your clients.

  * **Guides that detail the workflows implicit in using the API**, i.e., the sequence of API calls that do something meaningful in the context of the product or service the API offers.

  * **An overview of the design principles** adopted by the API provider and what that means for aspects adherence to REST (especially hypermedia), HTTP codes, etc.

  * **Information on authentication**, including schemes that may be implemented such as OAuth or OpenID Connect.

  * **General information on error handling** with information on the HTTP return codes.

  * **An interactive API explorer** that allows the developer to readily bring all this information to life.

## Starting Your API Document

Begin by writing your documentation first. Start by converting your requirements for each feature into documentation. Do this even if you haven't been provided with as many specifications as necessary. This should be done even before you work on your unit tests or even the code.

Your documentation should be used to share knowledge. This is so that both the end users and the internal developers get the right information on how to proceed with the project -- especially the internal developers who would need to understand the documentation in order to explain tit.

After writing the documentation for the API project, it is now time to convert written comments and other content of the documentation into the colorful website and other customizable templates.

All of these will be done with little effort as you go on to produce complete feature sites for your projects.

## 3 API Documentation Template Resources

Among all the API documentation formats, three of them deserve a mention because they let you design your API in a way that can be easily consumed by humans as well as machines:

  1. **Swagger and Open API. **There let you easily generate your own API server code, client code, and the documentation itself. Open API Initiative (OAI) is focused on creating, evolving, and promoting a vendor neutral API description format based on the Swagger specification.

  2. **RAML. **RESTful API Modeling Language offers an easy way to specify an API by using patterns.

  3. **API Blueprint.** This is a standard based on the popular Markdown format that lets you easily generate code from the documentation.

## Summary

Everyone agrees that documentation is an absolute must if you want to guarantee that your API is well understood by potential consumers and business partners. While some people believe that starting an API project with initial documentation is a good idea, most people struggle to actually write something.

Think of planning your documentation first as a way of creating more time to work on the main project.

In the long run, having great documentation can you save you a lot of time and can help you get more clients and easily build the project at hand.

After you finish your documentation you can quickly generate the code for your API using the many tools out there.

The Integration Zone is brought to you in partnership with [CA Technologies](https://dzone.com/go?i=142025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714699%3B137084580%3Bt). Use CA Live API Creator to quickly [create complete application backends, with secure APIs and robust application logic](https://dzone.com/go?i=142025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714699%3B137084580%3Bt), in an easy to use interface.
