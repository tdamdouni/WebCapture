# API Is Not Just REST, Part 1

_Captured: 2018-02-22 at 16:58 from [dzone.com](https://dzone.com/articles/api-is-not-just-rest)_

_This is one of my talks from [APIDays Paris 2018](http://www.apidays.io/events/paris-2017). Here is the abstract: The modern API toolbox includes a variety of standards and methodologies, which centers around REST, but also includes Hypermedia, GraphQL, real-time streaming, event-driven architecture, and gRPC. API design has pushed beyond just basic access to data, and also can be about querying complex data structures, providing experience rich APIs, real-time data streams with Kafka and other standards, as well as also leveraging the latest algorithms and providing access to machine learning models. The biggest mistake any company, organization, or government agency can make is to limit their API toolbox to be just about REST. Learn about a robust and modern API toolbox from the API Evangelist, Kin Lane._

### **Diverse Toolbox**

After eight years of evangelizing APIs, when I participate in many API conversations, some people still assume I'm exclusively talking about REST as the API Evangelist - when in reality I am simply talking about APIs that leverage the web. Sure, REST is a dominant design pattern I shine a light on, and has enjoyed a significant amount of the spotlight over the last decade, but in reality on the ground at companies, organizations, institutions, and government agencies of all shapes and sizes, I find a much more robust API toolbox is required to get the job done. REST is just one tool in my robust and diverse toolbox, and I wanted to share with you what I am using in 2018.

![](https://s3.amazonaws.com/kinlane-productions/talks/api-days-paris-2018/api-not-rest-1.png)

The toolbox I'm referring tool isn't just about what is needed to equip an API architect to build out the perfect vision of the future. This is a toolbox that is equipped to get us from the present day into the future, acknowledging all of the technical debt that exists within most organizations which many are looking to evolve as part of their larger digital transformation. My toolbox is increasingly pushing the boundaries of what I've historically defined as an API, and I'm hoping that my experiences will also push the boundaries of what you define as an API, making you ready for what you will encounter on the ground within organizations you are delivering APIs within.

### **Application Programming Interface**

API is an acronym standing for application programming interface. I do not limit the scope of application in the context to just be about web or mobile applications. I don't even limit it to the growing number of device-based applications I'm seeing emerge. For me, an application is about applying the digital resources made available via a programmatic interface. I'm looking to take the data, content, media, and algorithms being made available via APIs and apply them anywhere they are needed on the web, within mobile and device applications, or on the desktop, via spreadsheets, digital signage, or anywhere else that is relevant, and sensible in 2018.

![](https://s3.amazonaws.com/kinlane-productions/talks/api-days-paris-2018/api-not-rest-2.png)

API does not mean REST. I'm really unsure how it got this dogmatic association, nor do I care. It is an unproductive legacy of the API sector and one I'm looking to move beyond. Application programming interfaces aren't the solution to every digital problem we face. They are about understanding a variety of protocols, messaging formats, and trying to understand the best path forward depending on your application of the digital resources you are making accessible. My API toolbox reflects this view of the API landscape, and is something that has significantly evolved over the last decade of my career, and is something that will continue to evolve, and be defined by what I am seeing on the ground within the companies, organizations, institutions, and government agencies I am working with.

### **SOAP**

I have been working with databases since 1987, so I fully experienced the web services evolution of our industry. During the early years of the web, there was a significant amount of investment into thinking about how we exchanged data across many industries, as well as within individual companies when it came to building out the infrastructure to deliver upon this vision. The web was new, but we did the hard work to understand how we could make data interoperability in a machine-readable way, with an emphasis on the messages we were exchanging. Looking back I wish we had spent more time thinking about how we were using the web as a transport, as well as the influence of industry and investment interests, but maybe it wasn't possible as the web was still so new.

![](https://s3.amazonaws.com/kinlane-productions/talks/api-days-paris-2018/api-not-rest-3.png)

While web services provided a good foundation for delivering application programming interfaces, it may have underinvested in its usage of the web as a transport, and became a victim of the commercial success of the web. The need to deliver web applications more efficiently, and a desire to hastily use the low-cost web as a transport quickly bastardized and cannibalized web services, into a variety of experiments and approaches that would get the job done with a lot less overhead and friction. Introducing efficiencies along the way, but also fragmenting our enterprise toolbox in a way which we are still putting back together.

### **XML and JSON RPC**

One of the more fractious aspects of the web API evolution has been the pushback when API providers call their XML or JSON remote procedure call (RPC) APIs, RESTful, RESTish, or some other mixture of philosophy and ideology, which has proven to be a dogma stimulating event. RESTafarians prefer that API providers properly define their approach, while many RPC providers could care less about labels, and are looking to just get the job done. Making XML and JSON RPC a very viable approach to doing APIs, something that still persists almost 20 years later.

![](https://s3.amazonaws.com/kinlane-productions/talks/api-days-paris-2018/api-not-rest-4.png)

Amazon Web Services, Flickr, Slack, and other RPC APIs are doing just fine when it comes to getting the job done, despite the frustration, ranting, and shaming by the RESTafarians. It isn't an ideal approach to delivering programmatic interfaces using the web, but it reflects its web roots and gets the job done with low-cost web infrastructure. RPC leaves a lot of room for improvement but is a tool that has to remain in the toolbox. Not because I am designing new RPC APIs, but there is no doubt that at some point I will have to integrate with an RPC API to do what I need to get done in my regular work.

### **REST at Center**

Roy Fielding's dissertation on representational state transfer, often simply referred to as REST, is an amazing piece of work. It makes a lot of sense, and I feel it is one of the most thorough looks at how to use the web for making data, content, media, and algorithms accessible in a machine-readable way. I get why so many folks feel it is the RIGHT WAY to do things, and one of the reasons it is the default approach for many API designers and architects - myself included. However, REST is a philosophy, and much like microservices, which provides us with a framework to think about how we put our API toolbox to work, but isn't something that should blind us from the other tools we have within our reach.

![](https://s3.amazonaws.com/kinlane-productions/talks/api-days-paris-2018/api-not-rest-5.png)

REST is where I begin most conversations about APIs, but it doesn't entirely encompass what I mean every time I use the phrase API. I feel REST has given me an excellent base for thinking about how I deliver APIs but will slow my effectiveness if I leave my REST blinders on, and let dogma control the scope of my toolbox. REST has shown me the importance of the web when talking about APIs and will continue to drive how I deliver APIs for many years. It has shown me how to structure, standardize, and simplify how I do APIs, and help my applications reach as wide an audience as possible using commonly understood infrastructure.

Tune back in tomorrow for more!
