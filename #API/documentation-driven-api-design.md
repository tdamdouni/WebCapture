# Documentation-Driven API Design

_Captured: 2017-07-28 at 08:03 from [dzone.com](https://dzone.com/articles/documentation-driven-api-design-1?oid=twitter&utm_content=buffer78ab2&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Share, secure, distribute, control, and monetize your APIs with the platform built with performance, time-to-value, and growth in mind. [Free 90-day trial](https://dzone.com/go?i=231226&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Ftechnologies%2Fjboss-middleware%2F3scale%2Fget-started%3Fsc_cid%3D701f2000000h30LAAQ) of 3Scale by Red Hat

_[This article is featured in the new DZone Guide to Integration: API Design and Management. Get your free copy for more insightful articles, industry statistics, and more!_](https://dzone.com/guides/integration-api-design-and-management)

Many companies and developers think documentation is something to be done as an afterthought, a nightmare for any developer who has been assigned the difficult task of having to go through each of the application's features and write about them and how they are used.

But think, what if you could speed up your API development by focusing on the documentation first? Documentation changes are cheap, code changes are expensive.

The philosophy behind Documentation-Driven API Design or Development is simple: from the perspective of a user, if a feature is not documented, then it does not exist, and if a feature is documented incorrectly, then it is broken.

## API Design - Documentation First

Designing an API is a special case because you're often designing for unknowns. You might not know:

  * What types of clients will consume the API, or their individual preferences.

  * The flow that any given consumer will take through your API endpoints.

  * Which information will be most valuable to the consumer.

With all of these unknowns, the best thing you can do for yourself and your consumers is to write your documentation first, as visibly as possible. The goal is to gather insight and recommendations from your consumers early and throughout the design process, turning your unknowns into knowns.

By designing your API through documentation, you can easily get feedback and iterate your design before any development happens. Changes are easier and faster to make in documentation than they are in code. Documentation can become an invaluable resource as you want to increase your company's Velocity.

The documentation gives the client team and test team something to work from before the server team has even implemented the documented endpoints. This prevents rework and parallelizes the efforts of the server and client teams. Coders and testers could start working at the same time to implement and test such an API.

When writing or updating documentation is a required first step of your development process, you ensure your documentation is always consistent with your code.

## 6 Guidelines for Working Documentation-Driven API Design

### 1\. Document Your API or Feature First

You can do this as you design an API, or later if you'd like to rework an existing API. Wherever the documentation becomes complicated or difficult to write, revisit the design. This process works because it is easier to spot complexity in the documentation than in the code. Figure out how you are going to describe the feature to users; if it is not documented, it does not exist.

### 2\. Do Documentation Reviews

Whenever possible, documentation should be reviewed by users before any development begins. This also gives you the chance to get your ideas peer-reviewed, since it helps users to understand what you are trying to do.

### 3\. Work in Parallel

Once documentation has been written, development should commence, preferably test-driven development. Both developers and testers can start working on the implementation, one focusing on writing code and the other on writing automatic tests.

### 4\. Testing

Unit tests should be written to test the features as described in the documentation. If the functionality is ever out of alignment with the documentation, tests should fail.

### 5\. Changes

When a feature is being modified, it should be modified documentation-first; when documentation is modified, so should the tests change. Along with the tests being changed, the coding will also have to be modified accordingly.

### 6\. Versioning

Documentation and software should both be versioned, and the versions should match so someone working with old versions of software will be able to find the proper documentation.

## API Documentation Design Fundamentals

Concise and clear documentation, which allows your API consumers to adopt it into their application quickly, is no longer optional for organizations that want to drive adoption of their APIs. According to SmartBear's 2016 State of API Report, 75% of organizations that develop   
APIs now have a formal documentation process. 46% say it is a high priority for their organization. A survey by ProgrammableWeb found that API consumers considered complete and accurate documentation as the biggest factor affecting their API decision-making, even outweighing price and API performance.

Good documentation accelerates development and consumption, and reduces the money and time that would otherwise be spent answering support calls. It is important to remember that documentation matters for internal API users as well. Do not assume that your internal stakeholders will have intimate knowledge of how to work with the API.

What should go into your API documentation? These are three features that should be ever-present in documentation:

  1. There should be consistency, meaning that an end user should be able to know what your documentation has in the offing. The terminology used should also be in line with your language.

  2. The documentation should be a complete scope of the features of your entire project. Private methods used should also be put down for your developers to utilize. The public features should be made explicitly available for your end users.

  3. It should also be up to date. This means that the documentation should maintain recent versions of the code used for the project.

There are, of course, no standards or hard-and-fast rules on what API documentation should have. As a general rule, whatever resonates with the developer community and makes it easy for them to understand an API is a good starting point.

Some general sections that are backed up by examples from established providers in the API economy:

  * A list of the resources with an explanation of the purpose of each in the context of the product or service being offered via the API.

  * Examples of API calls in a variety of languages and tools (curl, Postman collections, etc.). The   
examples are probably the most important section of the API document, as these are going to be used by your clients.

  * Guides that detail the workflows implicit in using the API, i.e. the sequence of API calls that do something meaningful in the context of the product or service the API offers.

  * An overview of the design principles adopted by the API provider and what that means for aspects adherence to REST (especially hypermedia), HTTP codes, etc.

  * Information on authentication, including schemes that may be implemented, such as OAuth or OpenID Connect.

  * General information on error handling with information on the HTTP return codes that will be returned.

![Image title](https://dzone.com/storage/temp/6025730-screen-shot-2017-07-24-at-112620-am.png)

## Open API Specification, a.k.a. Swagger

Some API documentation formats have the added benefit of being machine-readable. This opens the door to a multitude of additional tools that can help during the entire lifecycle of your API:

  * Create a mock server to help during the initial API development for both testers and client/server-side teams, and to test your API before deployment to ensure that the API and the documentation match.

  * Create interactive documentation that allows developers to perform demo requests to your API.   
These interactivity features will serve as an invaluable tool for both the developer and the debugger.

Among all the API documentation formats, the most popular and used by many big companies is the OAS (Open API Specification), or Swagger. It gives you the ability to design your API in a way that can be easily consumed by humans as well as machines.

The Open API/Swagger specification is a machine- and human-readable description format that defines the API's contract. This contract defines what data is exposed by the resources and services, and how the client should call these resources. While this idea seems simple, it has powerful implications for the multi-platform API economy, where services are built in many languages and consumed by clients across different devices.

Today, thousands of API teams around the world use the Open API Specification and Swagger tooling to generate documentation for their internal and public-facing APIs.

There are many practical uses for implementing the OAS into your API workflow starting from code generation (try out ApiBldr, a Visual Open API Builder that helps you build Open API Specification for your API. It's also able to generate client and server SDKs from the OAS) and ending with generation of beautiful interactive documentation that can easily be shared   
with the API's end users.

## Conclusion

API documentation, as detailed above, is no easy task. Organizations not only need to work on technical writing, but also must make sure the documentation is secure and easy to work with.

Everyone agrees that documentation is an absolute must if you want to guarantee that your API is well understood by potential consumers and business partners. While some people believe that starting an API project with initial documentation is a good idea, most people struggle to actually write something.

After you finish your documentation, you can quickly generate the code for your API using the many tools out there, like ApiBldr, for example.

__[This article is featured in the new DZone Guide to Integration: API Design and Management. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/integration-api-design-and-management)__

Explore the core elements of owning an API strategy and best practices for effective API programs. [Download](https://dzone.com/go?i=231227&u=https%3A%2F%2Fengage.redhat.com%2F3scale-api-owners-s-201706160312%3Fsc_cid%3D701f2000000h30LAAQ) the API Owner's Manual, brought to you by 3Scale by Red Hat

### Like This Article? Read More From DZone

Opinions expressed by DZone contributors are their own.
