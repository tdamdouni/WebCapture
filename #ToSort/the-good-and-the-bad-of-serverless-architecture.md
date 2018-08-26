# The Good and the Bad of Serverless Architecture

_Captured: 2018-06-12 at 19:06 from [dzone.com](https://dzone.com/articles/the-good-and-the-bad-of-serverless-architecture?edition=379259&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-06-12)_

###  The cloud structure's most popular component has multiple advantages and disadvantages to consider, as well as multiple use cases. 

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

If you've chosen to read this article, you're likely aware that serverless computing is the next big thing in the cloud paradigm. In the last few years, around the time Amazon Web Services introduced its Lambda platform, serverless has become mainstream and buzzword-worthy with brands like BBC, Airbnb, Netflix, Nike, and many more adopters of the new approach to handle their back-end efforts.

Let's begin by saying that the word _serverless_ does not represent the actual state of the technology. There's still a server somewhere; you just don't need to buy, manage, or maintain it anymore. You outsource all server management to someone else, adding a level of abstraction in your cloud infrastructure. For developers, it means an ability to finally push server provisioning backstage and an overall friendlier way to create applications. For businesses - faster time to market and an idea of focusing on the _what_ and _why_ of deployment, instead of the _how_. Basically, the serverless approach is business-driven, the means by which third parties handle your technical concerns while you focus on delivering results.

Now, you may think, _"We already keep our infrastructure in the cloud and don't own any hardware. So, how is this different?"_

Using a **traditional cloud model** (often called Cloud 1.0), you simply move your storage and networking to the cloud, but you still have to access and monitor it remotely via virtual machines (VMs). The serverless approach takes it to another level. Here, a programmer chooses an environment in which the code is written (Node.js. Python, C#, etc.) and uploads the code file which is then automatically deployed by the system. By using a vendor's own ecosystem, you can easily describe how these services communicate and where they can access data. This is a near NoOps approach where most of the Ops is outsourced to a vendor.

![](https://www.altexsoft.com/media/2018/03/evolution-of-cloud.png)

> _How application deployment has evolved with cloud_

For a deeper understanding of how it works, and what benefits it brings, let's first describe some of the defining characteristics of serverless architecture.

## Serverless 101

**Function-as-a-Service**

Another name for serverless computing is Function-as-a-Service (FaaS), referring to the way developers assemble code into building blocks called _functions_. This is very similar to [microservices](https://www.altexsoft.com/blog/engineering/using-microservices-for-legacy-system-modernization/?utm_source=DZone&utm_medium=referral) where a large code monolith is split into small, manageable elements that can be scaled and updated separately and parallelly. However, FaaS takes it to the next level by breaking up the monolith even further.

![](https://www.altexsoft.com/media/2018/03/monolith.png)

> _Microservices vs serverless: same concept, different implementation_

**Event-driven coding**

You obviously don't want your home security camera to record everything that happens on your street 24/7. That's why we use motion-activated cameras to detect suspicious behavior when we're not at home. Serverless architecture works similarly: just like a motion sensor, it only works when a particular pre-programmed event is triggered. Serverless is stateless, meaning it only executes a task and doesn't store or reuse requests.

**Scalable services**

The serverless approach is flexible and ideal for scaling applications. A FaaS vendor takes each of your functions and runs them in separate containers. This allows you to scale them endlessly and automatically. This is another difference between serverless and traditional cloud - here you don't have to purchase the assumed amount of resources; you can be as flexible as possible. To make sure the travel management platform 4site can flexibly grow, we used [AWS Lambda for the server(less) side](https://www.altexsoft.com/case-studies/travel/altexsoft-cornerstone-information-systems-building-a-cloud-web-dashboard-as-a-corporate-travel-management-solution/?utm_source=DZone&utm_medium=referral) of the project.

**Billing per invocation**

In a traditional cloud model, you need your servers to be ready to process requests at all times. Constant server availability leads to significant back-end costs every month, irrespective of CPU time and memory that are actually used. It's like leaving your heater on all year long, regardless of the weather or change of seasons, and paying huge sums for unneeded electricity. Alternatively, serverless vendors allow you to pay a fraction of a price per request, which means that your costs will depend only on how much traffic you had this month.

Function-as-a-Service vendors such as [Amazon Web Services Lambda](https://aws.amazon.com/lambda/), [Microsoft Azure Functions](https://azure.microsoft.com/en-us/services/functions/), [Google Cloud Functions](https://cloud.google.com/functions/), and [IBM Bluemix OpenWhisk](https://console.bluemix.net/openwhisk/) provide similar opportunities. When it comes to pricing, they're all easy on the budget: up to one million requests are free, giving you a great starting point. The difference lies mostly in the community support and the availability of supported languages, which makes the choice rather personal.

### What's the Big Deal?: Pros of Serverless Computing

Engineering-wise, the benefits of serverless are obvious. It's a simplified approach to development that eliminates a complicated layer, streamlining engineering efforts. But what about the business side of things? How do you persuade stakeholders that FaaS is the way to go?

#### Cheaper than the traditional cloud

As we mentioned, FaaS allows you to pay a fraction of the price per request. If you're a startup, you can [build an MVP](https://www.altexsoft.com/blog/business/minimum-viable-product-types-methods-and-building-stages/?utm_source=DZone&utm_medium=referral) nearly for free and ease into the market without dealing with huge bills for minimum traffic.

#### Scalable

Everyone wants to build the next Uber, but would you risk provisioning infrastructure just in case? With serverless, you don't have to make a choice, but you'll still be ready for any volume of growth.

#### Lower human resources costs

Just as you don't have to spend hundreds or thousands of dollars on hardware, you can stop paying engineers for maintaining it. That's exactly how co-founders of productivity app Moo.do [managed](https://www.entrepreneur.com/article/293668) to deliver a product with their team of two.

#### Ability to focus on user experience

Abstraction from servers allows companies to dedicate more time and resources to developing and improving customer-facing features.

### What to Keep in Mind: Cons of Serverless Computing

#### Vendor lock-in

When you give a vendor the reins to control your operations, you have to play by their rules. It's also not easy to port your application to Azure if you've already set it up on Lambda. The same concern refers to coding languages: Right now only [Node.js](https://www.altexsoft.com/blog/engineering/the-good-and-the-bad-of-node-js-web-app-development/?utm_source=DZone&utm_medium=referral) and Python developers have the freedom to choose between existing serverless options.

#### Learning curve

Despite the comprehensive documentation and community resources, you may soon find out that the learning curve for FaaS tools is pretty steep. Also, to painlessly migrate to serverless, you might want to split your monolith into microservices, another complicated task to tackle. That's why it's preferable to get help from professionals experienced in serverless tools.

#### Unsuitable for long-term tasks

Lambda gives you five minutes to execute a task and if it takes longer, you'll have to call another function. Serverless is great for short real-time or near-real-time processes like sending out emails. But long duration operations such as uploading video files would require additional FaaS functions or be better with "server-ful" architecture.

### Serverless Architecture Use Cases

Currently, most of the technology adopters are startups who seek for a possibility to scale painlessly and lower the entrance barrier. Serverless is also a perfect approach for applications that don't run continuously but rather have quiet periods and peaks of traffic.

#### **Internet of Things applications**

The real-time response nature of the serverless approach works great for IoT use cases. Motion activated cameras that we've already mentioned, along with applications that react to changes in weather, temperature, or health conditions are perfect for the serverless paradigm that won't allow your services to sit idle 24/7.

#### **Virtual assistants and chatbots**

People using chats expect immediate responses which is why serverless data processing can be faster. As your application grows from one hundred to several thousand users, your processing time should also stay the same which is automated with FaaS.

#### **Image-rich applications**

To maintain great user experience, developers have to provide multiple versions of the same images for different screen sizes - from desktops, to tablets and smartphones. This significantly decreases loading time. However, the tooling from AWS and Google will automatically optimize your images for any needs, making it a perfect solution for image-heavy applications.

#### **Agile and Continuous Integration pipelines**

The idea of running the code only when a certain event is triggered is perfectly in line with Agile or[ Continuous Integration principles](https://www.altexsoft.com/blog/business/continuous-delivery-and-integration-rapid-updates-by-automating-quality-assurance/?utm_source=DZone&utm_medium=referral). Separating your codebase into functions also helps with bug fixing and shipping updates. Serverless is an overall friendly way for maximum automation and rapid deployment processes.

## Is Serverless the Future?

Going serverless doesn't just mean a technical change but also a mindset change. For many companies running on legacy infrastructure, the migration will be painful and not as cost-effective as it's promised to be for starting organizations. When you already have an established workflow, adopting FaaS tools to completely get rid of servers to manage is hard to justify. Plus, serverless is far from mainstream, though it's moving in that direction and pretty fast.

In its [Hype Cycle for Emerging Technologies 2017](https://www.gartner.com/smarterwithgartner/top-trends-in-the-gartner-hype-cycle-for-emerging-technologies-2017/), Gartner predicts that serverless/FaaS will reach its plateau of productivity in 2-5 years, along with machine learning, VR, and IoT. The technology is already available. The real struggle here is to determine the breadth of possible use cases and waiting for the larger language and functionality pool from all vendors.

_Originally published on AltexSoft's blog "[The Good and the Bad of Serverless Architecture](https://www.altexsoft.com/blog/cloud/pros-and-cons-of-serverless-architecture/?utm_source=DZone&utm_medium=referral)"_

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)
