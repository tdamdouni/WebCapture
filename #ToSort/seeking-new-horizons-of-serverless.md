# Seeking New Horizons of Serverless

_Captured: 2018-04-03 at 18:45 from [dzone.com](https://dzone.com/articles/seeking-new-horizons-of-serverless?edition=371204&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-04-03)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

![Diving into Serverless](https://dzone.com/storage/temp/8539537-nikko-macaspac-263785-unsplash.jpg)

> _Are you dead in the water with your Serverless development?_

Serverless is a misnomer. A perception. It was not materialized until it became a household name, a few years ago. If you'd ask whether there are servers in serverless, the answer -- unsurprisingly -- is a BIG yes. Now, the million-dollar question -- do you have to worry about them?

No.

Back in the day, it was all just bare-metal servers, which were kept on-premises and managed by the organizations themselves. Then came the virtual machine, a piece of software that mimics the hardware-based servers. Cloud was the next big thing inspired by the distributed computing platforms. Containerization, a.k.a. OS-level virtualization, came along and gained popularity afterwards. However, later, IaaS (Infrastructure as a Service) had covered some ground due to the emerging popularity of the cloud by then. Provisioning servers became automated with PaaS as the next step of IaaS.

Technology continually evolves and, like it or not, so does everything around us. In the last decade, we saw drastic improvements in connectivity, compute power, storage, etc. Serverless started appearing more and more (even got us [Baader-Meinhoffed](https://science.howstuffworks.com/life/inside-the-mind/human-brain/baader-meinhof-phenomenon.htm)) after Business Development VPs started making [impact stories](http://readwrite.com/2012/10/15/why-the-future-of-software-and-apps-is-serverless/) and this continued the trend of PaaS (Platform as a Service) with some significant paradigm shifts. With Amazon Web Services launching Lambda at 2014 [ReInvent conference](https://aws.amazon.com/blogs/security/2014-reinvent-roundup/), serverless became inevitable. By today, it is one of the [trending topics](http://serverlessconf.io/) in the software architecture world.

## Diving into Serverless

Serverless computing is a cloud computing model of which applications and services can be built and run without managing any servers. As such, the name has been derived corroborating the fact that provisioning, scaling, and managing of servers are entirely hidden from the operator. Serverless incorporates two different but overlapping realms -- BaaS, shorthand for Backend as a Service, and FaaS, shorthand for Function as a Service.

Serverless is not a [new kid on the block](https://medium.com/@janaka_bandara/sigma-the-new-kid-on-the-serverless-block-48b0fa02ad2b), even though some misapprehends it to be a relatively new concept. Zimki started offering the first "pay per use" code execution platform in 2006 -- before they [withdrew the service](https://blog.gerv.net/2007/09/zimki_shuts_down/) at the end of 2007. Heroku by Salesforce has been silently operating their web application deployment model since 2007. Google App Engine was released in April 2008 with limited features by Google. It started out as a custom Python execution framework and now turned out to be one of the favourite cloud platforms for web application development and hosting.

### Brave New Waves

With the event-driven wave hitting the coast, ephemeral, stateless compute containers came into play. Unlike traditional architectures, these compute engines were invoked only once by a 3rd-party -- and killed. People started using monikers -- Functions as a Service (FaaS) emerged. This was briskly leveraged by the developers for focusing and implementing own business logic triggered by specific events.

FaaS completely abstracts the infrastructure layer from the developer charging only for the time of use. Quoting [AWS Lambda](https://aws.amazon.com/lambda/),

> Run code without thinking about servers. Pay only for the compute time you consume. 

FaaS market is driven mainly by the shift from DevOps to serverless computing lately. Global forecasts predict the serverless market growing at a [rate of 32.7%](https://www.businesswire.com/news/home/20170227006262/en/7.72-Billion-Function-as-a-Service-Market-2017---Global). Industry experts have some [enticing views](http://www.eweek.com/innovation/predictions-2018-why-serverless-processing-may-be-wave-of-the-future) about the progression of serverless technology too.

### Serverless, the Hero

Introduction of serverless eliminates the woe to manage clusters of servers and the traditional "always on" server requirement. The underlying fleet of servers scales gracefully on its own, provisioning appropriate infrastructure, even to meet massive surges in traffic. They are regularly monitored and managed by the providers -- also security patches and other immunization shots are taken care of. This cuts a considerable portion of the budget as it results in notable reductions in operational cost, not to mention the hassle.

In serverless, you only pay as you use; the invocations are billed by fractions of seconds. Implementing a production-ready output from a mere idea is super-fast. Developer productivity for a first-time experience is a significant gain compared to struggling over different software stacks set up internally. AWS and pretty much all the other serverless solution providers give [free tier](https://aws.amazon.com/free/) options and come as language agnostic endpoints (except for Google Cloud, others provide multiple runtime/development environments) which makes the first-time hands-on experiences much more relieved.

### Serverless, the Villain

This does not mean that serverless is all god-like; it might include some [hidden costs incurred](https://medium.com/@amiram_26122/the-hidden-costs-of-serverless-6ced7844780b). Usually, these costs don't encompass only CPU and RAM usage, but the number of API requests, storage, and network might get their fair share. Sometimes, according to your specific business requirement, an implementation with multiple functions may be more difficult than having one with a single container. Code maintenance may incapacitate you, due to the distributed nature of your overall logic -- or for more complex use cases, going with Kubernetes might be advantageous since it's more mature.

Lack of integration testing facilities on localhost is a huge downside of the existing providers. There is no easy way to emulate, but can be overcome to a certain extent by using [Serverless Framework](https://serverless.com/) or [aws-sam-local](https://aws.amazon.com/about-aws/whats-new/2017/08/introducing-aws-sam-local-a-cli-tool-to-test-aws-lambda-functions-locally/). Manual machine tuning befitting your application is impossible because the server layer is intangible.

Provider lock-in can be challenging when moving forward since each serverless platform is a far cry from each other based on their uniqueness and limitations. Because of the [cold starts](https://hackernoon.com/im-afraid-you-re-thinking-about-aws-lambda-cold-starts-all-wrong-7d907f278a4f), applications may experience high latency at the beginning.

## Serverless Competition

AWS is not the only FaaS provider in the market. There is a handful of other enterprise giants competing for the fattening market. Microsoft Azure enhances event-driven serverless compute experience with [Azure Functions](https://azure.microsoft.com/en-us/services/functions/). IBM's serverless domain provides [IBM Cloud Functions](https://www.ibm.com/cloud/functions) which is based on Apache OpenWhisk, an open source project. [Google Cloud Functions](https://cloud.google.com/functions/) is the Google Cloud Platform's version of FaaS, which is still in beta.

Different providers provide a stack of fully managed products in their serverless platforms. These backend services require no provisioning, maintaining, or administration. Here's a depiction of the various components in each serverless platform.

![Image title](https://dzone.com/storage/temp/8541541-infographic-serverless-platform-showdown.jpg)

> _Infographic: Components of major serverless platforms_

Apart from these, [Firebase](https://firebase.google.com/) is the Google Cloud Platform-backed (acquired, [as usual](http://www.wired.co.uk/article/google-acquisitions-data-visualisation-infoporn-waze-youtube-android), in 2014) mobile and web application development platform which consists of multiple integrated services. Most of the serverless providers showcase IoT framework support, mobile backend support and cognitive application development support as well.

Most Amazon web services have availability zone specific endpoints to compensate the latency in the applications around the globe. Developers have the freedom to use these regional endpoints or the default North Virginia endpoint. You can read more about AWS services that support particular regions in [here](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/). Just like that, other serverless providers support different availability zones as well.

AWS Lambda and other services have SDKs that support serverless development in multiple programming languages. Amazon recently (2018 January) [announced](https://aws.amazon.com/blogs/compute/announcing-go-support-for-aws-lambda/) Go support. Read [this article](https://headmelted.com/serverless-showdown-4a771ca561d2) to know agreat deal about a detailed comparison of different serverless providers.

## Many Faces of Serverless

Serverless applications let you run code without provisioning or managing servers. Serverless domain empowers a myriad of application opportunities. Some of them are divulged here as follows.

#### 1 -- Real-time data processing

Real-time processing is found to be coined widely with serverless. Image resizing for viewing on different devices such as desktop computers, smartphones, tablets are done by The Seattle Times [using AWS Lambda](https://aws.amazon.com/solutions/case-studies/the-seattle-times/). SiteSpirit [uses IBM cloud](https://www.ibm.com/case-studies/sitespirit) data services to build their cloud-based media library.

#### 2 -- Real-time stream processing

Localytics [uses Lambda](https://aws.amazon.com/solutions/case-studies/localytics/) to process billions of historical and live social media trend data for business users to query. IBM Cloud Functions can be integrated with Apache Kafka supported IBM Message Hub for [processing stream data](https://github.com/IBM/ibm-cloud-functions-data-processing-message-hub). Plexure, a company engaged in innovative retail businesses based in New Zealand, [uses Azure serverless technologies](https://customers.microsoft.com/en-us/story/plexure-dev-azure) to bring customer experience to the next level -- with the help of Azure Functions and Azure Logic Apps, now customers get alerts about the in-store digital display.

#### 3 -- Extract, Transform, Load (ETL)

Zillow, one of the largest real-estate brands [utilizes AWS serverless stack](https://aws.amazon.com/solutions/case-studies/zillow-zestimate/) to provide customers with a smooth experience in near-real-time home valuation.

#### 4 -- IoT Backends

In the IoT domain, there is an increasing growth of applications using serverless platforms. This [exciting story](https://medium.com/openwhisk/openwhisk-for-a-smart-city-data-application-dccd7894e0e1) explains how GreenQ, a smart residential waste collection company, exploits IBM Bluemix technologies to engage in a fast and more efficient service.

#### 5 -- Mobile Backends

Bustle.com is a website catering to women which provides news, fashion and many more. They use Lambda and API Gateway for its iOS and website backend. With the [move to new serverless architecture](https://aws.amazon.com/solutions/case-studies/bustle/), developers no longer worry about managing and provisioning infrastructure, all they focus on is innovating. The mobile app [WeatherGods](https://itunes.apple.com/us/app/weather-gods/id1041512978?mt=8) uses IBM Cloud Functions (former IBM OpenWhisk) to notify users about specific weather events (hurricane in Florida, for example) aligning god avatars according to their preferences.

#### 6 -- Serverless web applications

TimerCheck.io is a "deceptively simple web service with superpowers" in [Eric Hammond's words](https://alestic.com/2015/07/timercheck-scheduled-events-monitoring/). The service is entirely built on Amazon API Gateway and AWS Lambda, and it provides an unlimited number of timers that can run infinitely.

#### 7 -- SaaS event processing

San Joaquin Valley College (SJVC) is a private junior college in California. To simplify the IT management and provide the students with a better experience, they [moved their learning management system](https://customers.microsoft.com/en-us/story/san-joaquin-valley-college) to Microsoft Azure and Office 365. With the help of Microsoft FastTrack, SJVC embraced the serverless technology and continued their journey of innovation.

Apart from these most popular ones, you can find more use cases of [AWS](https://aws.amazon.com/solutions/case-studies/enterprise/), [Azure](https://azure.microsoft.com/en-us/case-studies), and [IBM](https://console.bluemix.net/openwhisk/).

## Empowering Serverless Development

Software architecture world is steadily being absorbed by serverless. It's not going to be "Serverless Everything" anytime soon as there are still many blanks to be filled. Tooling is improving, but again, there are still [gaps to be bridged](https://medium.com/statuscode/its-all-going-to-be-serverless-9e16fe721f36). The earlier mentioned Serverless framework provides a CLI tool that lets users to be integrated with multiple cloud providers.

[Cloud9](https://docs.c9.io/docs/faq-general), once an independent cloud-based IDE was [acquired by Amazon](https://www.forbes.com/sites/janakirammsv/2016/07/18/the-master-plan-behind-amazons-acquisition-of-cloud9-ide/#aaad64672c1a) to plug development aspect into its serverless stack. However, setting up a Cloud9 development environment requires a new Amazon EC2 instance or your own Linux server. The getting started the process is reported to be more complicated than the original Cloud9 (c9.io) [by many users](https://community.c9.io/t/please-dont-shutdown-original-c9-io/20955/4). Check [this neat trick](https://dzone.com/articles/writing-a-self-sufficient-aws-lambda-function) attempting to come up with a self-sufficient AWS lambda function, which quashes the need of uploading a bundle with third-party dependencies -- built locally. Microsoft Azure is powered by Visual Studio, another versatile but heavy cloud IDE with team services.

### Think Serverless

SLAppForge, a totally new player, [recently announced](https://globenewswire.com/news-release/2018/02/06/1333797/0/en/SLAppForge-Announces-Sigma-a-Cloud-IDE-for-Serverless-Computing.html#.WnnY4MV60OI.twitter) its beta release of [Sigma](https://sigma.slappforge.com/), a customized editor for the development and deployment of serverless applications. It's a hybrid model exploiting the beauty of drag-and-drop style and the full power of raw code. Sigma hides the underlying complexities of the platform from the developers using its own, "very" serverless architecture -- which means, now you don't have to dig into piles and piles of documentation and tutorials.

This [powerful IDE](https://slappforge.com/) is equipped with intuitive code suggestions, context-aware code completion, auto-generated code snippets--still supports only Node.js though. It also takes care of the Continuous Integration, and Continuous Delivery flows of your serverless applications. If you have a web browser (I bet you already do!), a GitHub account and an AWS account, you're all set -- because there's _nothing_ to install. Deploying your serverless application is minutes away now, not hours, not days.

## Conclusion

The paradigm shift to serverless is becoming inescapable by the day, just like was the change from on-premise to cloud. The Big Day that all applications go serverless is not far away. It's high time to jump on the bandwagon and be a serverless developer since everything is propelling you to be more productive and efficient. Keep aside the worries about infrastructure; focus fully on the business logic. The ball is in your court; jump-start [your serverless development](https://sigma.slappforge.com/#/signup) now!

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

Topics:

serverless ,serverless architecture ,cloud ide ,cloud computing ,functions as a service ,lambda ,slappforge ,software development ,continuous delivery ,continuous integraiton
