# Will Serverless Be the Future of Enterprise Application Development?

_Captured: 2018-01-29 at 21:23 from [dzone.com](https://dzone.com/articles/will-serverless-be-the-future-of-enterprise-applic?edition=358101&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-29)_

Create a continuous deployment pipeline with open source tools. [Watch the screencast.](https://dzone.com/go?i=272426&u=https%3A%2F%2Fwww.fastly.com%2Flc%2Fci-cd-with-terraform%2F%3Futm_medium%3Ddisplay%26utm_source%3Ddzone.com%26utm_campaign%3DFY18Q1_GatedContent_CI%2FCDTerraform%26utm_content%3DDzone_BumperTextLink)

Serverless is currently one of the hot topics out there in software architectural patterns. Like many other terms or trends in software engineering, serverless also doesn't have a clear definition of what it is. In this post, I'll walk-through a basic overview of serverless and a few examples around it. Further, this will explore the potential of serverless and discuss on some of the debatable points around serverless.

![](https://cdn-images-1.medium.com/max/1600/1*yasWWPSn5lpv_z6tbyxntg.png)

> _What is Serverless?_

As per MartinFowler.com:

> Serverless architectures refer to applications that significantly depend on third-party services (knows as Backend as a Service or "BaaS") or on custom code that's run in ephemeral containers (Function as a Service or "FaaS") 

In simple terms as I see, if you are not maintaining or managing your own infrastructure to run your application and you pay as per your usage (never pay for idle), while getting the required level of high availability, scalability, and fault tolerance automatically from your vendor, you are running a serverless application. As an owner of an application which runs on a serverless environment, you can put all your focus on your application business logic without worrying about the infrastructure that it runs and other non-functional requirements around your application such as high availability, fault tolerance, and scalability.

## Will Serverless Be Just a Hype?

If you are new to serverless and you are considering it as an architect, this will be one of the main concerns that you will have. Yes, serverless is a trending topic these days, but after considering the past and how technology evolves, I personally believe that it won't be just a short-term hype, but rather that it will stay there for at least next 3-5 years. Technologies around serverless will be changed or replaced, but the concepts behind serverless would not.

## How Technology Actually Evolves Towards Serverless?

Before going to explain how powerful serverless is, let's first see how it has evolved over last few years.

> "You have to know the past to understand the present." ― Carl Sagan 

This is how it evolves over the time…

  * 1989-1991 --World Wide Web invented by Sir Tim Berners-Lee
  * 2011 -- Envolve/Firebase, real-time database as a service
  * 2013 -- Docker, "containers are better than virtual machines"

Likewise, AWS lambda was born and the word serverless came out to the stage together with FaaS. Although we see that Lambda as the starting point for serverless, containerization was the first hit for the movement towards serverless. With the invention of the containerization concept, world-leading cloud service providers were able to provide services to their customers with the concept, "pay as you use" together with most required non-functional requirements to run their business using their infrastructure.

There are four key characteristics of a serverless application:

  1. No server management -- as the name implies, for a serverless application, there aren't any physical servers are involved at the application owner's end. If you are the application owner, you have no idea how many servers are running on behalf of your application and their physical location.
  2. Flexible scaling -- since you don't have an idea about the physical server layer, you don't have to worry about the scalability. Your application will be allocated more resources on demand to manage the required level of capacity (which can be processing, memory, disk, database storage etc.)
  3. High availability -- redundancy and fault tolerance are built-in features of serverless frameworks. You don't have to keep your own servers to make your application highly available. If there are processing node failures, the underline framework will be automatically spawned a new node or several nodes for you and you won't feel anything at all.
  4. Never pay for idle -- In serverless environment, you never pay for the idle time which is one of the key advantages when it comes to cost considerations.

## Are FaaS and Serverless the Same?

This is kind of a trending FAQ these days since there are some people who claim that FaaS is the technical implementation of the serverless concept. There are others who believe that serverless is not bounded to FaaS, but is rather a concept which is applicable more broadly. I'm in agreement with the latter group; let me explain why.

FaaS is just the event-driven processing part of the serverless architecture. For an application, there are many other required building blocks such as data persistence, data streaming, messaging, user management and many more, to be there, to serve some end-to-end functionality. Most importantly there can be some applications without a FaaS component at all, but still can be considered as a serverless application.

As an example, if we need some static web hosting, we can do that without considering about physical servers at all, thanks to world-leading cloud service providers. If we consider AWS as our cloud service provider, we can host our web page content in an S3 bucket and enable static web hosting to host our web page. To make it complete you can use Route 53 for DNS and CloudFront for CDN.

Another example would be a web application with a thick client which will use back-end services only for authentication and data persistence. You can implement this kind of an application without having your own physical servers as well as a FaaS component at your side. There are many services you can use for both authentication and data persistence.

## Will Serverless be the Future?

Before answering this, I suggest you check [this](https://aws.amazon.com/#Explore_Our_Products) page which is the product section of the AWS page. If you see carefully, there are around 100 "as a service products" which cover complete software development life cycle, starting from development to deployment and maintenance.

What do you think about the vision of AWS? I strongly believe that they will drive this effort to change the world that we will be able to develop, test, deploy and maintain our applications fully on top of their solutions. In fact, we won't be charged for the idle time as well, while they will be able to cover 90% of the cases from their services.

If you are still not ready to believe me, check out the growth of AWS services within last two years, they are rapidly expanding their boundaries and enhancing their offerings to cover almost all the requirements in software life cycle process from the infrastructure point of view. Yes, some of those services are not yet 100% complete (few of them are released within last two months) and completely replaceable for on-premise products. However, within next 2-3 years, they will make sure, that you don't have to think twice before going for cloud offerings while selecting infrastructure for your application development, deployment, and maintenance.

So, where are these cloud service providers taking software development and maintenance process? Definitely, their objective is to cover all the possible scenarios in serverless approach and give their clients to a comfort zone to make sure they only have to focus on their business logic and will be able to put their full potential for that.

## Will Faas Be Able to Reach the Required Level of Capacity?

Now you may be thinking this -- if we are going to move to the serverless paradigm, how capable of FaaS, to facilitate required level of processing capability. Let me explain this with an example FaaS offering, AWS Lambda (of course AWS is not the only leading players in this section, but I'm selecting the one I am more familiar with). Yes, if you consider current [limitations/constraints](https://docs.aws.amazon.com/lambda/latest/dg/limits.html) of AWS Lambda, you can easily argue that AWS Lambda doesn't have a capacity to facilitate almost all the processing scenarios (I'm still referring event-based applications) However, for me, almost all these limitations are only soft limits which can be easily relaxed based on customer requirements. Trust me, in the future, they will definitely extend these limits to make sure Lambda is capable of covering at least 90% of the cases.

A recent [report](https://www.businesswire.com/news/home/20170227006262/en/7.72-Billion-Function-as-a-Service-Market-2017---Global) claims that the FaaS market is projected to grow up to 32.7% by 2021. This is only for FaaS, if you look at the complete picture of serverless paradigm, you will understand how much potential that it has.

## Conclusion

Serverless is currently a trending topic which will definitely be a major hit within next few years. In the future you won't have to worry about the infrastructure; your complete software life cycle will depend on cloud service providers. If you are enthusiastic to be up to date with the technology, I welcome you to become familiar with the serverless paradigm and these cloud offerings.

As I have mentioned at the very beginning, most of these points are debatable which do not have concrete definitions or answers. So if you have any concerns, I'm happy to meet you in the comments section!

Strengthen & support your microservices with logic at the edge. [Here's how.](https://dzone.com/go?i=273424&u=https%3A%2F%2Fwww.fastly.com%2Flc%2Fenhance-microservices%3Futm_medium%3Ddisplay%26utm_source%3Ddzone.com%26utm_campaign%3DFY18Q1_GatedContent_MicroservicesBrief%26utm_content%3DDzone_BumperTextLink)

Topics:

serverless ,serverless application model ,serverless architecture ,aws ,enterprise integration ,enterprise app development ,google cloud services ,cloud computing ,faas

Opinions expressed by DZone contributors are their own.
