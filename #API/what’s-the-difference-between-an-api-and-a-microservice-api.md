# What’s the Difference Between an API and a Microservice API?

_Captured: 2017-10-19 at 19:37 from [dzone.com](https://dzone.com/articles/whats-the-difference-between-an-api-and-a-microser?edition=334792&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-19)_

### The difference is size; one is a quick, easy, and discrete connector of building blocks, the other a large, highly formatted API.

[Learn more](https://dzone.com/go?i=250324&u=http%3A%2F%2Fblog.scalyr.com%2F2017%2F08%2Fcareerbuilder-resolves-customer-issues-5x-faster-scalyr%2F) about how CareerBuilder was able to resolve customer issues 5x faster by using Scalyr, the fastest log management tool on the market.

Thanks to Simon Peel, Chief Strategy Officer and Chief Marketing Officer at [Jitterbit](http://www.jitterbit.com), for taking the time to explain to me how APIs are evolving with the adoption of microservices. Simon has been involved with APIs and integration throughout his career with IBM, Cast Iron Systems, Peakstone Corporation, Vitria Technologies, and Micro Focus. The last four of which he took public or helped get acquired.

**Q: What do you see as the most important elements of microservices APIs versus regular APIs?**

A: Traditional APIs tend to be very large and can perform a lot of disparate functions. An example would be the powerful salesforce.com APIs. A microservices API typically has one job or a small set of closely related jobs is autonomous and works in a quick, easy, and discrete manner--like an individual building block.

**Q: Which programming languages, frameworks, and tools to you see being used to build out microservices APIs?**

A: We see Java, C, C++, Node, Swagger and all sorts of frameworks. However, we encourage clients to create microservices APIs using our simple low-code tool without needing to worry about languages and frameworks. Most companies already have a plethora of code and applications they can pull from, leaving them free to focus on the composition of innovative new applications. Essentially, this allows them to get on with the exciting job of creating new apps from building blocks versus creating the building blocks themselves.

**Q: How have microservices APIs changed application development?**

A: The great thing about microservices is that you can change individual components of an application without having to maintain/fix/rewrite/test huge sections of code. You can even sway out building blocks to add enhanced functionality, while again limiting the amount of work usually required by such changes. For some programmers, this can mean a new journey into stateless programming and may require them to unlearn some of what they've been doing, so that they can save themselves work and time in the future.

**Q: What kind of security techniques and tools do you find for securing microservices APIs?**

A: We're always reminding customers implementing microservices that although this may seem like a brave new world, they still need to identify and follow security policies and procedures, pen testing, and authentication. We find API management tools do a good job of governing security on the frontend.

**Q: What are some real-world problems you are helping your clients solve with microservices APIs?**

A: Taking a monolithic application, breaking it into microservices and then reconnecting those microservices in ways that are most useful for the business. We worked with a European insurance company with a monolithic system that was locked out of the comparison websites because it was behind their firewall; the company website was the only way to run quotes and offer policies. We broke out their quote engine, their risk engine, and several other components into microservices, and then rewired them into a small set of useful APIs that could be accessed by the top comparison websites. We did this work in fewer than four weeks with microservices APIs and helped their developers understand how to construct well-formed microservices. Prior to microservices, this would have been a six- to 12-month project.

**Q: What are the most common issues you see affecting the development of microservices APIs?**

A: Lack of access to skilled and experienced developers and integrators who have been there and done that, when it comes to developing fully fledged apps constructed from microservices. Hackathons are a great source of ideation, for example, but as this is a relatively new field. Currently, there isn't a horde of experienced professionals who have taken MVPs and turned them into massively scalable production apps. We also need people with architectural skills in addition to those knowledgeable about the languages and tools used to build microservices. Our tools help with this because they enable developers to rapidly create microservices in a low-code environment without having to understand all the nuances of existing SaaS or on-premise applications. They can focus on composing apps, versus hand coding microservices.

**Q: Do you have any concerns regarding the current state of microservices APIs?**

A: It's a double-edged sword. On the one hand, you are able to build a lot by combining all these small, interdependent services. However, when problems happen, where do you look? Root-cause detection across a sea of independent microservices written by many different programmers, tools, (and even companies) can be challenging.

**Q: What's the future of microservices APIs from your perspective?**

A: Once you get over the initial hurdles of building microservices, you are able to start building apps much faster using services from many sources, and this results in tremendous creative freedom. One example of a new-found freedom is the use of AI. AI has been locked in the backroom since the '50s. It's now accessible with an API call. The right use cases will enable you to leapfrog competitors. Forget about science projects--think about what you can do to add value to your line of business and go show them something amazing.

**Q: What do developers need to keep in mind when working on microservices APIs?**

A: Think small. Imagine in a Lego canister, the one connector that can be used to make a lot of different things. That's the API that will be used ubiquitously. Make APIs that facilitate. Focus on what makes the greatest impact. Focus on quality versus quantity so you're not overwhelmed with the number of microservices or APIs.

**Q: What else do we need to keep in mind regarding microservices APIs that we haven't discussed?**

A: Everyone needs to understand the difference between APIs and microservices on a level sufficient to determine which one to use to solve the business problem at hand. It's not a one-size-fits-all answer. Not everything needs to be a microservice. Will it be used internally or externally? Microservices and APIs can be used internally or externally, but as a general rule, microservices are most often used internally, while APIs are used to expose functionality to the outside world.

[Find out more](https://dzone.com/go?i=250325&u=http%3A%2F%2Fblog.scalyr.com%2F2014%2F05%2Fsearching-20-gbsec-systems-engineering-before-algorithms%2F) about how Scalyr built a proprietary database that does not use text indexing for their log management tool, allowing customers to search 1TB of data in under a second.
