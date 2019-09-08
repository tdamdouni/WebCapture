# API Design — Beauty Is in the Eye of the Beholder - DZone Integration

_Captured: 2019-08-28 at 19:33 from [dzone.com](https://dzone.com/articles/api-design-beauty-is-in-the-eye-of-the-beholder?edition=521291&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202019-08-28)_

****

Recently, a colleague asked me for examples of a “Beautiful API.” Immediately, I gave a tongue-in-cheek response, “Beauty is in the eye of the beholder.” Of course, to back this up, I quickly elaborated that an API that is beautiful to me may not be beautiful to them. This got me thinking...is there any way to classify or quantify what would make a beautiful API? If beauty is in the eye of the beholder, then who are the beholders of API beauty? After thinking about this for a bit, I concluded that there are two main beholders:

  * The developers who consume the API in order to create applications. 
  * The client applications themselves, created by the aforementioned developer, which fulfills some need by using the API (the application consumer).

So what can an API creator do to please these beholders?

## Developers

If you recall the following quote from Donald Knuth, he expressed that “programming is the art of telling another human what one wants the computer to do.” We can apply the same truth to API’s if we change two keywords. If we change the word “Programming” to “API creation” (and as we’re in 2019, we’ll replace “computer” with “system”), we get the following:

_**“API creation is the art of telling another human what one wants the system to do.”**_

Therefore, an API is about communicating with a human. A well-designed API should be easy to use, and thus make the developer’s experience in creating the application run very smooth. Ultimately, a good API will make the developer productive as quickly as possible. 

Adhering to the “principle of least astonishment” when designing an API, it means that the design should match the mental model of your audience and there should be no surprises; your audience should intuitively understand the API. Or to put it another way, the API creator should hope to minimize the WTFs/minute of the developers using your API:

![Image tiBeauty of an API can be measured in WTFs/minute  \(Good API versus Bad API\)tle](http://3.bp.blogspot.com/-ilMjE1Gh3Yg/VpUAmd-6TWI/AAAAAAAAAbg/-FJ08zxN42s/s1600/WFTPM.png)

Adhering to this principle would mean that accessing the API will feel natural to a developer. Nothing should be jarring. For example, authentication tokens should utilize standard security practice, error codes, and messages that are intuitive. i.e, an authorization failure would not return an HTTP 200 OK as an error status.

## API Product

When designing your API, you should adopt a product mindset. After all, the API is intended for use by someone else. Whether you think of it that way or not and whether you actually sell it or not, you have a product on your hands intended for use by someone else. As such, this product will have a lifecycle and success criteria. 

Your API should have a Product Manager assigned to help make adoption successful — the creation of the API should not just be a Jira task. The API needs to be nurtured and grown to be considered a success.

However, to nurture and grow an API can be difficult. One of the challenges that developers have in providing APIs has to do with ongoing maintenance and support. As a developer, once their API is being consumed, it becomes a contract. As with any contract, it must be followed to avoid a breach with the consumer. In other words, as a developer, you cannot make wholesale changes to an API because you will break your consumer's application. 

This becomes a pretty onerous responsibility, especially as business changes and innovation needs change. To mitigate against these types of issues, it is extremely important to spend time on design upfront; with proper design responding to changing needs can be achieved, while still maintaining the API’s contract. 

Remember that the API contract has a different lifecycle to the API implementation. A great example highlighting this difference in the implementation lifecycle is AWS’s S3 API. AWS CTO, [Werner Vogels, says](https://www.allthingsdistributed.com/2016/03/10-lessons-from-10-years-of-aws.html) that “S3 could best be described as starting off as a single-engine Cessna plane, but over time, the plane was upgraded to a 737, then a group of 747s, all the way to the large fleet of Airbus 380s that it is now.” However, if you look at the API contract, the current version of the Amazon S3 API is 2006-03-01.

## API First

Ideally, before any code is implemented for your API, the API contract (e.g. OAS 3.0) is defined for review by API consumers. Note that this contract could be defined in a tool like Stoplight.io or even with annotations in code, but the API is not implemented. 

Implementation should wait until the API has been reviewed and approved by its consumers. For example, if an API is the GUI for developers and if you map this to the accepted UI design workflow, then the contract is a wireframe and the API consumers are UI users validating what is presented in the wireframes. Once the contract has been refined and is delighting its API consumers, then implementation can start.

Remember that you are not the user/consumer of your API, so the more validation and feedback that you get the better. An additional way to achieve this is to provide a mock implementation of the contract and to ask your API Consumers to begin to code against the mock. As the consumers attempt to use the mock, they may see use cases and scenarios that were not considered, allowing redesign to occur before the API becomes a rigid contract.

![Image titleYou are not the user, the more API consumers reviewing the API the better \(photo from UX engineers laptop\) ](/storage/temp/12388594-20190819-165712-3-1.jpg)

## Client Applications 

Another aspect to consider when designing an API is the context in which your API will be used. For example, will the API be internal to your organization as part of a microservice architecture? Will the API be public and used in mobile apps? The context that the consuming applications are running within will affect the type of API that you provide:

  * **GraphQL** APIs lend themselves to mobile apps and help avoid the chattiness that is seen with REST APIs. With GraphQL, the client determines what data they want, how they want it, and in what format they want it rather than walking multiple REST requests — responses to find the resource the app requires.
  * **SSE** (Server-side events) if you need to push data from the server to a web application. 
  * **gRPC** — When your APIs are internal to your organization and not on the web (i.e. inside a microservice architecture) and when you control the consumer and the provider.

Knowing where the client apps will run will help to determine what API you should be providing.

## UIs for Developer Experience

Once your API is ready for prime time and ready to be consumed, you will make all the assets (documentation, SDK, code snippets, API definitions, endpoints) available in a developer portal, i.e. the watering hole where your target developers “hang out.” 

It is important to note that the SDK should not just be a thin veneer around the API definition, but it should contain samples, build tools for creating applications, etc. It should have everything to help reduce complexity and increase developer experience.

Remember, if you’re providing a UI application that accompanies your API, then it will only be useful to a developer in certain environments. Today, the adoption of CI/CD is the accepted norm for delivery and deployment of applications. A UI is most helpful at the start and end of a CI/CD pipeline, while all other intermediate environments should be considered headless. Therefore, providing a CLI is more useful to these headless, highly-automated environments. Thus, within a CI/CD pipeline, the following holds:

  * API and CLI are useful in all environments 
  * UI is useful at the initial and final environments 

Providing the correct CLI and GUI experiences will help enhance the overall developer experience for your API.

## Mirror Mirror

With a well-designed API, solid supporting documentation, and good support for developers’ existing tools, you will delight the technical consumers of your API every time. If you have followed the advice in this blog when you’re asked about a beautiful API is, then you will be able to turn to the mirror and say with confidence, “Mirror mirror on the wall, who has the fairest API of all?” And you will know the answer ;)

![“Mirror mirror on the wall who has the fairest API of all?”Image title](https://miro.medium.com/max/1200/0*iYxInpkP2GcjjAm-.jpg)
