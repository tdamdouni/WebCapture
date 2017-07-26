# API Development: Design-First or Code-First?

_Captured: 2017-02-27 at 02:26 from [dzone.com](https://dzone.com/articles/design-first-or-code-first-whats-the-best-approach?edition=272906&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-26)_

### In design-first, the plan is converted to a doc and code is built. In code-first, the API is coded based on the plan and a readable doc is generated from it.

Learn how API management supports better integration in [Achieving Enterprise Agility with Microservices and API Management](https://dzone.com/go?i=126027&u=http%3A%2F%2Fpages.3scale.net%2Fmicroservices-api-management-dzinteg.html), brought to you in partnership with [3scale](https://dzone.com/go?i=126027&u=https%3A%2F%2Fwww.3scale.net%2F%3Futm_campaign%3Ddzintegration%26utm_source%3Ddzoneint%26utm_content%3Dbumper)

With the popularity of API description formats like [Swagger (OpenAPI)](http://swagger.io) and API Blueprint, serious thought has been given on the best approach to building APIs based on historical usage and best practices.

API description formats act as a contract that end users can utilize to understand how to best work with your API. This contract is language-agnostic and readable by both humans and machines, helping to streamline adoption and improve interoperability between applications.

An API contract in the OpenAPI (Swagger) specification will look something like this:
    
    
    description: | ####Echos back every URL, method, parameter and header
    
    
    Feel free to make a path or an operation and use * * Try Operation * * to test it.The echo server will

## Design-First vs. Code-First API Development

When it comes to using API description formats, two important schools of thoughts have emerged: the design-first" and the code-first approach to API development.

The code-first approach is a more traditional approach to building APIs, with the development of code happening after the business requirements are laid out, eventually generating the documentation from the code. The design-first approach advocates for designing the API's contract first before writing any code. This is a relatively new approach, but is quickly catching on, especially with the use of API description formats.

To understand the two approaches better, let's look at the general process followed during the API lifecycle. Like any product, the concept of the API starts with the business team identifying an opportunity. The opportunity is analyzed and a plan to capitalize on it is created in a text document by strategists, analysts and other business folks. This document is then passed along to the development team, which is where the plan takes some tangible form.

There are two possibilities from here on to develop the API:

  1. **Design-first:** The plan is converted to a human and machine readable contract, such as a Swagger document, from which the code is built.
  2. **Code-first: **Based on the business plan, API is directly coded. From this, a human- or machine-readable document, such as a Swagger document, can be generated.

Finally, after the API is functioning, it is sufficiently tested and then deployed to a suitable host.

![DesignvsCode](https://i1.wp.com/swaggerhub.com/wp-content/uploads/2017/02/DesignvsCode.jpg?w=759)

## Choosing the Right Approach

There are advantages and disadvantages associated with both approaches, and at the end of the day, choosing the right approach boils down to your immediate technological and strategic needs that you wish to solve with your APIs. Let's dive into when and why you would choose the design-first or code-first approach.

## Design-First Approach

### When Developer Experience Matters

A well-designed API can do wonders for the adoption and consumption of your APIs, and good design can be better achieved with the design-first approach. If your API strategy involves the high adoption of your API and retention of users integrating with your API, then good Developers Experience (DX) matters. An effective API design helps your end consumers quickly understand your API's resources and value propositions, reducing the time taken for them to integrate with your API. An API with consistent design decreases the learning curve when integrating with your API, making it more likely to have higher reuse value and engagement.

### When Delivering Mission-Critical APIs

The biggest reason to go for the design-first approach is when your API's target audience is external customers or partners. In such a case, your API is a key distribution channel that your end customers can use to consume the services you provide, and good design plays a key role in determining customer satisfaction. Such APIs play a critical role in representing your organization's services, especially in an omnichannel ecosystem, where consistency in information and hassle-free consumption is an important indicator of business success.

### When Ensuring Good Communication

The API contract can act as the central draft that keeps all your team members aligned on what your API's objectives are, and how your API's resources are exposed. Identifying bugs and issues in the API's architecture with your team becomes easier from inspecting a human-readable design. Spotting issues in the design, before writing any code is a much more efficient and streamlined approach, than doing so after the implementation is already in place.

## Code-First Approach

### When Delivery Speedy Matters

Developers can start implementing the API much faster if they start coding the API directly from the requirements document. This is important if your go-to-market strategy emphasizes speed and agility as important factors for the success of the API program. The fact that automation is much easier in the code-first approach helps strengthen this case, with a lot of libraries supporting scaffolding server code, functional testing, and deployment automation.

### When Developing Internal APIs

The code-first approach affords speed, automation, and reduced process complexity, at the cost of good developer experience. If the API will only be consumed by the team or company that's building it, then the code-first approach is an ideal solution. This is especially true if the API developed is small with only a few end points, that will only be used internally.

## Summary

There are positives and negatives to both approaches. The approach you take to developing your APIs will play a vital role in determining how they're consumed and maintained. Who are your API's end consumers? What needs do they have? What are you trying to solve with your API program? These are the types of questions that should guide your decision making when it comes to choosing the right methodology to your API development.

Unleash the power of your APIs with future-proof API management - [Create your account](https://dzone.com/go?i=126028&u=http%3A%2F%2Fpages.3scale.net%2Ffuture-proof-api-management-dzinteg.html) and start your free trial today, brought to you in partnership with [3scale](https://dzone.com/go?i=126028&u=https%3A%2F%2Fwww.3scale.net%2F%3Futm_campaign%3Ddzintegration%26utm_source%3Ddzoneint%26utm_content%3Dbumper).
