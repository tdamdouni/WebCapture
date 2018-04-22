# API Is Not Just REST, Part 2

_Captured: 2018-02-22 at 16:57 from [dzone.com](https://dzone.com/articles/api-is-not-just-rest-part-2)_

### **Negotiating CSV**

As the API Evangelist, I work with a lot of government and business users. One thing I've learned working with these groups is the power of using comma-separated values (CSV) as a media type. I know that us developers and database folks enjoy a lot more structure in our lives, but I have found that allowing for the negotiation of CSV responses from APIs, can move mountains when it comes to helping onboard business users, and decision makers to the potential of APIs-even if the data format doesn't represent the full potential of an API. CSV responses are the low bar I set for my APIs, making them accessible to a very wide business audience.

![](https://s3.amazonaws.com/kinlane-productions/talks/api-days-paris-2018/api-not-rest-6.png)

CSV as a data format represents an anchor for the lowest common denominator for API access. As a developer, it won't be the data format I personally will negotiate, but as a business user, it very well could mean the difference between using an API or not. Allowing me to take API responses and work with them in my native environment, the Excel spreadsheet, or Google Sheets environment. As I am designing my APIs, I'm always thinking about how I can make my resources available to the masses, and enabling the negotiation of CSV responses whenever possible, helps me achieve my objectives.

### **Negotiating XML**

I remember making the transition from XML to JSON in 2009. At first, I was uncomfortable with the data format and resisted using it over my more proven XML. However, I quickly saw the potential for the scrappy format while developing JavaScript applications, and when developing mobile applications. While JSON is my preferred and default format for API design, I am still using XML on a regular basis while working with legacy APIs, as well as allowing for XML to be negotiated by the APIs I'm developing for wider consumption beyond the startup community. Some developers are just more comfortable using XML over JSON, and, who knows, maybe by extending an XML olive branch, I might help developers begin to evolve in how they consume APIs.

![](https://s3.amazonaws.com/kinlane-productions/talks/api-days-paris-2018/api-not-rest-7.png)

Similar to CSV, XML represents support for a wider audience. JSON has definitely shifted the landscape, but there are still many developers out there who haven't made the shift. Whether we are consumers of their APIs or providing APIs that target these developers, XML needs to be on the radar. Our toolbox needs to still allow for us to provide, consume, validate, and transform XML. If you aren't working with XML at all in your job, consider yourself privileged, but also know that you exist within a siloed world of development, and you don't receive much exposure to many systems that are the backbone of government and business.

### **Negotiating JSON**

I think about my career evolution, and the different data formats I've used in 30 years. It helps me see JSON as the default reality, not the default solution. It is what is working now, and reflects not just the technology, but also the business and politics of doing APIs in a mobile era, where JavaScript is widely used for delivering responsive solutions via multiple digital channels. JSON speaks to a wide number of developers, but we can't forget that it is mostly comprised of developers who have entered the sector in the last decade.

![](https://s3.amazonaws.com/kinlane-productions/talks/api-days-paris-2018/api-not-rest-8.png)

JSON is the default media type I use for any API I'm developing today. No matter what my backend data source is. However, it is just one of several data formats I will potentially open up for negotiation. I feel like plain JSON is lazy, and whenever possible I should be thinking about a wider audience by providing CSV and XML representations, but I should also be getting more structured and standardized in how I handle the requests and responses for my API. While I want my APIs to reach as wide an audience as possible, I also want them to deliver rich results that best represents the data, content, media, algorithms, and other digital resources I'm serving up.

### **Hypermedia Media Types**

Taking the affordances present when humans engage with the web via browsers for granted is one of the most common mistakes I make as an API designer, developer, and architect. This is a shortcoming I am regularly trying to make up for by getting more sophisticated in my usage of existing media types, and allowing for consumers to negotiate exactly the content they are looking for, and achieve a heightened experience consuming any API that I deliver. Hypermedia media types provide a wealth of ways to deliver consistent experiences, that help deliver many of the affordances we expect as we make use of data, content, media, and algorithms via the web.

![](https://s3.amazonaws.com/kinlane-productions/talks/api-days-paris-2018/api-not-rest-9.png)

Using media types like Hal, Siren, JSON API, Collection+JSON, and JSON-LD are allowing me to deliver a much more robust API experience, to a variety of API clients. Hypermedia reflects where I want to be when it comes to API design and architecture that leverages the web, but it is a reflection I have to often think deeply about as I still work to reach out to a wide audience, forcing me to make it one of several types of experiences my consumers can negotiate. While I wish everyone saw the benefits, sometimes I need to make sure CSV, XML, and simpler JSON are also on the menu, ensuring I don't leave anyone behind as I work to bridge where we are with where I'd like to go.

### **API Query Layers**

Knowing my API consumers is an important aspect of how I use my API toolbox. Depending on who I'm targeting with my APIs, I will make different decisions regarding the design pattern(s) I put to work. While I prefer investing resources into the design of my APIs and crafting the URLs, requests, and responses my consumers will receive, in some situations my consumers might also need much more control over crafting the responses they are getting back. This is when I look to existing API query languages like Falcor or GraphQL to give my API consumers more of a voice in what their API responses will look like.

![](https://s3.amazonaws.com/kinlane-productions/talks/api-days-paris-2018/api-not-rest-10.png)

API query layers are never a replacement for more RESTful, or hypermedia, approaches to delivering web APIs, but they can provide a very robust way to hand over control to consumers. API design is important for providers to understand, and define the resources they are making available, but a query language can be very powerful when it comes to making very complex data and content resources available via a single API URL. Of course, as with each tool present in this API toolbox, there are trade-offs with deciding to use an API query language, but in some situations it can make the development of clients much more efficient and agile, depending on who your audience is, and the resources you are looking to make available.

### **Webhooks**

In my world, APIs are rarely a one-way street. My APIs don't just allow API consumers to poll for data, content, and updates. I'm looking to define and respond to events, allowing data and content to be pushed to consumers. I'm increasingly using Webhooks as a way to help my clients make their APIs a two-way street, and limit the amount of resources it takes to make digital assets available via APIs. Working with them to define the meaningful events that occur across the platform, and allow API consumers to subscribe to these events via Webhooks. Opening the door for API providers to deliver a more event-driven approach to doing APIs.

![](https://s3.amazonaws.com/kinlane-productions/talks/api-days-paris-2018/api-not-rest-11.png)

Webhooks are the 101 level of event-driven API architecture for API providers. It is where you get started trying to understand the meaningful events that are occurring via any platform. Webhooks are how I am helping API providers understand what is possible, but also how I'm training API consumers in a variety of API communities about how they can deliver better experiences with their applications. I see webhooks alongside API design and management, as a way to help API providers and consumers better understand how API resources are being used, developing a wider awareness around which resources actually matter, and which ones do not.

### **Websub**

In 2018, I am investing more time in putting Websub, formerly known as the word which none of us could actually pronounce, PubSubHubbub. This approach to making content available by subscription as things change has finally matured into a standard and reflects the evolution of how we deliver APIs in my opinion. I am using Websub to help me understand not just the event-driven nature of the APIs I'm delivering, but also that intersection of how we make API infrastructure more efficient and precise in doing what it does. Helping us develop meaningful subscriptions to data and content, that adds another dimension to the API design and even query conversation.

![](https://s3.amazonaws.com/kinlane-productions/talks/api-days-paris-2018/api-not-rest-12.png)

Websub represents the many ways we can orchestrate our API implementations using a variety of content types, push and pull mechanisms, all leveraging web as the transport. I'm intrigued by the distributed aspect of API implementations using Websub, and the discovery that is built into the approach. The remaining pieces are pretty standard API stuff using GETs, POSTs, and content negotiation to get the job done. While not an approach I will be using by default, for specific use cases, delivering data and content to known consumers, I am beginning to put Websub to work alongside API query languages and other event-driven architectural approaches. Now that Websub has matured as a standard, I'm even more interested in leveraging it as part of my diverse API toolbox.th

### **Server-Sent Events (SSE)**

I consider webhooks to be the gateway drug for API event-driven architecture. Making API integrations a two-way street, while also making them more efficient, and potentially real time. After webhooks, the next tool in my toolbox for making API consumption more efficient and real-time are server-sent events (SSE). Server-sent events (SSE) is a technology where a browser receives automatic updates from a server via a sustained HTTP connection, which has been standardized as part of HTML5 by the W3C. The approach is primarily used to establish a sustained connection between a server, and the browser, but can just as easily be used server to server.

![](https://s3.amazonaws.com/kinlane-productions/talks/api-days-paris-2018/api-not-rest-13.png)

Server-sent events (SSE) delivers one-way streaming APIs which can be used to send regular and sustained updates, which can be more efficient than regular polling of an API. SSE is an efficient way to begin going beyond the basics of client-server request and response models and pushing the boundaries of what APIs can do. I am using SSE to make APIs much more real-time, while also getting more precise with the delivery of data and content, leverage other standards like JSON Patch to only provide what has changed, rather than sending the same data out over the pipes again, making API communication much more efficient.

### **Websockets**

Shifting things further into real-time, websockets is what I'm using to deliver two-way API streams that require data be both sent and received, providing full-duplex communication channels over a single TCP connection. WebSocket is a different TCP protocol from HTTP but is designed to work over HTTP ports 80 and 443 as well as to support HTTP proxies and intermediaries, making it compatible with the HTTP protocol. To further achieve compatibility, the WebSocket handshake uses the HTTP Upgrade header to change from the HTTP protocol to the WebSocket protocol, pushing the boundaries of APIs beyond HTTP in a very seamless way.

![](https://s3.amazonaws.com/kinlane-productions/talks/api-days-paris-2018/api-not-rest-14.png)

SSE is all about the one-way efficiency, and websockets is about two-way efficiency. I prefer keeping things within the realm of HTTP with SSE unless I absolutely need the two-way, full-duplex communication channel. As you'll see, I'm fine with pushing the definition of API out of the HTTP realm, but I'd prefer to keep things within bounds, as I feel it is best to embrace HTTP when doing business on the web. I can accomplish a number of objectives for data, content, media, and algorithmic access using the HTTP tools in my toolbox, leaving me to be pretty selective when I push things out of this context.

Tune back in tomorrow for the third and final installment!
