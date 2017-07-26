# Why Go Serverless?

_Captured: 2017-07-07 at 06:55 from [dzone.com](https://dzone.com/articles/why-go-serverless?edition=306234&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-06)_

Linkerd, the open source service mesh for cloud native applications. [Get the complete guide](https://dzone.com/go?i=216221&u=http%3A%2F%2Fhubs.ly%2FH07NSwr0) to using Linkerd and Kubernetes to build scalable, resilient applications.

Most of the talk about serverless these days focuses on how to integrate with a function-as-a-service provider, how to orchestrate your calls, tools for troubleshooting in a serverless world, and so on. However, not much of it is focused on the most important question behind choosing serverless architectures over a more traditional approach: why?

In this post, we'll present a few different reasons to choose a serverless architecture over a more traditional client-server approach, or even over a containerized approach such as Docker.

## Reducing Development Costs

One of the primary reasons to go serverless is as the name suggests - you want to remove the server from the equation. While it's true that there is no such thing as a truly "serverless" application (serverless is just a different way to refer to cloud-hosted servers), by choosing a serverless provider you stand to gain simply from not having to write server code.

In a traditional client-server application, all APIs and endpoints on top of your data need to be implemented by a developer. These are included either by writing the code yourself using a framework like Rails, or by leveraging a third-party tool that can convert your underlying sources into a callable REST API.

With a serverless architecture, you take advantage of a third-party to outsource much of the back-end technology, removing the need to do some of the more complex tasks associated with bringing a web application to market. This significantly reduces your development costs. Your developers can focus on the user interface and user experience, the unique aspects of your app that have the most bang for the buck.

## Reducing DevOps and Maintenance Costs

There are a number of costs directly involved in developing and hosting a web application. These include developer salaries, hosting fees, domain registration fees, data transfer fees, and so on. Furthermore, with web applications, you often need to keep the server constantly available, to handle requests that can come in at any time of day. This means that for low-activity apps, that may use only one hour a day of computing time, you still need to pay for the other twenty-three hours your app was available but unused.

With Function-as-a-Service utilities like [AWS Lambda](https://aws.amazon.com/lambda/), you can further reduce your costs by ensuring you are only billed when the application is active. Function-as-a-Service runs on a pay-per-execution model, so you only pay for hosting and computing resources when your code is actually being called. Many web applications are often idle, so this can prove to be significant cost savings.

While you can make some similar gains using products like Docker to host containers on Heroku, you won't be able to get to the sheer level of granularity allowed by Function-as-a-Service serverless providers, who only spin up an instance when an individual function is actually called. This intermittent mounting and unmounting of containers reduces hosting and resource usage costs by making sure that your code is only active when it is actually needed.

## Reducing Time-to-Market

In addition to reducing the amount of code and operating costs, serverless apps require less effort to bring to market than their traditional counterparts. By sacrificing hardware and server-side flexibility, you can reduce the amount of time it takes to develop your app simply by moving the complexity onto the client side, unifying your efforts into a single language in your code base.

Furthermore, as you don't need to find a provider, stand up a server, configure the web server software, and get your app running on a machine, you end up with a far simpler problem. You also end up with a larger array of hosting choices, as serverless apps need only a CDN that can serve their files to end users, as opposed to a specialized web server running a programming language's runtime while handling requests from users over the web.

Finally, by outsourcing your app's server-side to a serverless provider, you enhance your security by allowing the third party to manage that aspect of your application. In doing so, you remove the effort needed to secure a web server, a database server, and any other back-end security concerns that would be paramount in a traditional client-server application.

## Conclusion

While many apps cannot operate in a serverless context due to unique or problematic application requirements, apps that have the option to go serverless have a number of benefits when compared with their traditional client/server brethren. By using a serverless provider, you can reduce the amount of code you need to write, letting a third party handle building your API on top of your data source for you.

You can also reduce your operating costs by allowing your code to run in a more intermittent manner, spinning up (and tearing down) instances only when they are needed.

Based on these two benefits - and a host of others that would require more space than I have available to touch on - you'll also see a reduction in time-to-market for your product, as you can focus on the look, feel, and behavior of your application right out of the gate. While a serverless architecture may not be right for you, it is a viable and smart choice for a growing number of companies.

Linkerd, the open source service mesh for cloud native applications. [Get the complete guide](https://dzone.com/go?i=216222&u=http%3A%2F%2Fhubs.ly%2FH07NSwr0) to using Linkerd and Kubernetes to build scalable, resilient applications.
