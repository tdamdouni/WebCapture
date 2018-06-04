# Schema-First API Design

_Captured: 2018-02-22 at 17:47 from [dzone.com](https://dzone.com/articles/schema-first-api-design?edition=362128&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202018-02-22)_

![](https://i.imgur.com/XrBO4V4.jpg)

You're building an API.

You develop a backend service with a few endpoints and deploy it to production. You publish several official language-specific API clients as well as an API documentation. The day ends on a happy note.

The following day, a new feature is going to be added the API. To do that, you have to:

  * Update the server implementation to support the new feature.
  * Update all client libraries (one SDK for each supported platform and language).
  * Update the documentation.
  * All the above must be consistent with each other.
  * Also, the front-end team is blocked until your backend API is complete.

You let out a heavy sigh.

> Is there a better way to do this? 

For each change made to your API, several steps must be performed to keep all development artifacts consistent with each other. Officially supported API client SDKs must support the latest HTTP API endpoints. The documentation must also be consistent and true to the actual implementation.

Each of these steps is labor-intensive and error-prone. Thus, it makes sense for us to automate these tasks away so we can focus on actually building features. The question is: how?

Instead of going straight to development, we start with **an API specification**.

## Schema-First API Design

The schema-first API design approach advocates for writing your API definition first in one of many API specification languages before writing any code. Writing an API specification has several benefits:

### Improved API Design

API specifications represent a contract for an API.

![](https://i.imgur.com/F6pvy24.png)

With an API specification and tools such as Swagger UI, you can visualize your API so that other developers and stakeholders can learn and give design feedback early on. You can even run a mock service based on an API spec that other teams can immediately interact with.

Identifying issues in the design before writing any code is a much more efficient and streamlined approach than doing so after an implementation is already in place.

> Discussing your API and settling on the contract before it is developed tends to lead to better designed APIs. 

### Iterate Faster Across Multiple Teams

With an API specification, development projects that involve multiple teams (backend, web, mobile, etc.) can proceed much faster than traditional methods would allow.

Front-end teams can immediately start building components regardless of whether or not the backend components are ready because we can generate and run mock services based on an API specification. Teams can work in parallel, without being blocked by another team's progress.

### Create Tests for Your API

Your API specification provides a contract that describes what a successful response will look like when someone calls your API. This contract can be re-purposed to generate test cases which can drastically decrease the amount of effort needed for testing your APIs. You can create functional tests and run mock services from your API spec.

### Generate Code and Documentation

![](https://i.imgur.com/Ug7AkZ6.png)

A schema-first approach creates a single source of truth that can be used to generate all kinds of development artifacts. Well-defined API specs can be used to automatically scaffold an API and generate an API reference and client SDKs that communicate with the API.

### Summary

Adopting schema-first API design has a small initial cost, but the benefits gained from it are significant.

## API Specification Languages

API Specification Languages defines a language-agnostic, standard representation of your REST APIs. Examples of API specification languages include [OpenAPI](https://swagger.io/specification/), [API Blueprint](https://apiblueprint.org/), and [RAML](https://raml.org/).

In the next section, we'll look at the OpenAPI specification language and the tooling surrounding it.

## The OpenAPI Specification Language

![](https://www.openapis.org/wp-content/uploads/sites/3/2016/10/OpenAPI_Pantone.png)

APIs form the connecting glue between modern applications. Nearly every application uses APIs to connect with corporate data sources, third-party data services or other applications. Creating an open description format for API services that is vendor-neutral, portable, and open is critical to accelerating the vision of a truly connected world.

OpenAPI is a JSON/YAML-based API specification language and framework for describing, producing, consuming, and visualizing RESTful web services. The overarching goal of OpenAPI is to enable client and documentation systems to update at the same pace as the server.

> _ What's the difference between OpenAPI and Swagger?_ OpenAPI is the official name of the specification. The development of the specification is fostered by the [OpenAPI Initiative](https://www.openapis.org/), which involves more the 30 organizations from different areas of the tech world -- including Microsoft, Google, IBM, and CapitalOne. Smartbear Software, which is the company that leads the development of the Swagger tools, is also a member of the OpenAPI Initiative, helping lead the evolution of the specification. 

> Swagger is the name associated with some of the most well-known, and widely used tools for implementing the OpenAPI specification. The OpenAPI 3.0 specification is based on the Swagger 2.0 specification. The Swagger toolset includes a mix of open source, free, and commercial tools, which can be used at different stages of the API lifecycle. 

OpenAPI offers more than just a specification language, other tools in the ecosystem include:

  * **[Swagger Editor](https://editor.swagger.io//#/):** Swagger Editor lets you edit OpenAPI specifications in YAML inside your browser and to preview documentation in real time.
  * **[Swagger UI](https://swagger.io/swagger-ui/):** Swagger UI is a collection of HTML, Javascript, and CSS assets that dynamically generate beautiful documentation from an OAS-compliant API.
  * **[Swagger Codegen](https://github.com/swagger-api/swagger-codegen):** Allows generation of API client libraries (SDK generation), server stubs, and documentation which is automatically given an OpenAPI spec.
  * **[Swagger Inspector](https://swagger.io/swagger-inspector/):** API Inspection tool that lets you generate OpenAPI definitions from existing API.

An OpenAPI Specification allows you to describe an API including (among other things):

  * General information about the API.
  * Available paths (e.g. `/resources`).
  * Available operations on each path (e.g. `GET /resources/{id}`).
  * Input/Output for each operation.

Here is a minimal OpenAPI spec in YAML:

There are 8 sections at the [root level](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.0.md#oasObject) in the OpenAPI 3.0 spec. There are many nested objects within these root level objects, but at the root level, there are just these objects:

  * `openapi`: **Required.** The semantic version number of the OpenAPI Specification version that the OpenAPI document uses (e.g. `3.0.0`.)
  * `info`: **Required.** Provides metadata about the API.
  * `servers`: An array of Server Objects, which provide connectivity information to a target server.
  * `components`: An element to hold various schemas for the specification.
  * `security`: A declaration of which security mechanisms can be used across the API.
  * `tags`: A list of tags used by the specification with additional metadata.
  * `externalDocs`: Additional external documentation.
  * `paths`: **Required.** The available paths and operations for the API.

> ![](https://techsparx.com/software-development/openapi/img/swagger-editor-online.jpg)
> 
> > _You can use the online Swagger editor to follow along!_

Let's look at each of the above sections briefly.

### The `info` Section

The `info` object provides metadata about the API.

> Remember to try it on the online [Swagger editor](https://editor.swagger.io//#/)! 

### The `servers` section

The `servers` section specifies the API server and base URL. You can define one or several servers, such as production and sandbox.

On Swagger UI, users will be able to choose the servers to send requests to from this predefined list:

![](https://i.imgur.com/P49dxc8.png)

### The `components` Section

[Components](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.0.md#components-object) are a set of reusable objects for the rest of the API, such as:

[JSON-schema](http://json-schema.org/) based definition of input and output data types.

The global `components/schemas` section lets you define common data structures used in your API. They can be referenced via `$ref` whenever a schema is required - in parameters, request bodies, and response bodies.

For example, this JSON object:

can be represented as:

and referenced elsewhere with `$ref: '#/components/schemas/Pet'`.

#### Response objects

Expected responses for different HTTP response codes of an operation.

Operations can have parameters passed via URL path (`/users/{userId}`), query string (`/users?role=admin`), headers (`X-CustomHeader: Value`) or cookies (`Cookie: debug=0`). You can define the parameter data types, format, whether they are required or optional, and other details:

Here is an example of the `example` keyword in a response body:

You can also define Security Scheme, Header, [Link](https://swagger.io/docs/specification/links/) (hypermedia), and [Callback](https://swagger.io/docs/specification/callbacks/) (webhook) objects in the `components` section.

The use of `components` is entirely optional. It's most useful for storing any frequently used domain objects in a reusable way.

> All objects defined within the components object will have no effect on the API unless they are explicitly referenced from properties outside the components object. 

### The `security` Section

The `security` object specifies the security or authorization protocol used when submitting requests. OpenAPI supports the following authentication methods:

  * HTTP authentication: Basic, Bearer, and so on.
  * API key as a header or query parameter or in cookies.
  * OAuth 2
  * OpenID Connect Discovery

At the root level of your OpenAPI document, add a security object that defines the global method we're using for security:

In the `components` object, we add a `securitySchemes` object that defines details about the security scheme we're using:

### The `tags` and `externalDocs` section

Imagine if you had an API with 50+ paths to describe. You would want to organize them into logical groups for users to navigate. The `tags` object provides a way to group the paths (endpoints) in the Swagger UI display.

Define your tags at the root level:

You can then use any defined tags in individual operations:

This will group operations with the same tags in Swagger UI:

![](http://idratherbewriting.com/learnapidoc/images/openapitutorial_tags.png)

> _Here's an example of an externalDocs object:_

### The `paths` section

In OpenAPI terms, `paths` are endpoints (resources), such as `/pets` or `/products/summary/`, that your API exposes, and operations are the `HTTP` methods used to manipulate these paths, such as `GET`, `POST` or `DELETE`.

First, let's list out the paths of our API:

Each path object (`/products.get`, `/orders.post`) is an operation. Here'a full example:

Each operation documents any parameters for the operation, the different kinds of responses, and other metadata. You can reference common data structures you've defined in the `components` section here.

## OpenAPI summary

That's all you need to get started! [Give it a try!](https://editor.swagger.io/)

Once written, an OpenAPI specification and Swagger tools can drive your API development further and save significant amounts of time and effort in the long term:

  * Use [Swagger Codegen](https://github.com/swagger-api/swagger-codegen) to generate a server stub for your API. The only thing left is to implement the server logic - and your API is ready to go live!
  * Use Swagger Codegen to generate client libraries for your API in over 40 languages.
  * Use [Swagger UI](https://swagger.io/swagger-ui/) to generate interactive API documentation that lets your users try out the API calls directly in the browser.

The Schema-first API design approach advocates for writing your API definition first in one of many API Specification languages before writing any code.

Adopting schema-first API design has a small initial investment and learning curve, but the benefits gained from it are significant. Writing an API specification poses many benefits such as improved API design, faster iteration, and automated code and documentation generation.

## Appendix

### What if I Already Have an API?

If you already have your API implemented (at least partially), you can make API calls to your API from [Swagger Inspector](https://inspector.swagger.io/builder) to automatically generate the OpenAPI file for any endpoint you call.

Here are some recommended resources for further learning:
