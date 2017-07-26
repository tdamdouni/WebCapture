# 5 Steps to Successfully Prepare for Microservices

_Captured: 2017-06-25 at 19:20 from [dzone.com](https://dzone.com/articles/5-steps-to-successfully-prepare-for-microservices?edition=305136&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-25)_

Learn how API management supports better integration in [Achieving Enterprise Agility with Microservices and API Management](https://dzone.com/go?i=126027&u=http%3A%2F%2Fpages.3scale.net%2Fmicroservices-api-management-dzinteg.html), brought to you in partnership with [3scale](https://dzone.com/go?i=126027&u=https%3A%2F%2Fwww.3scale.net%2F%3Futm_campaign%3Ddzintegration%26utm_source%3Ddzoneint%26utm_content%3Dbumper)

Microservices have been a hot topic for quite a while now - hundreds of conferences have been held, webinars streamed, and articles written on the subject. By now, you would assume that everybody is already aware of all the benefits and commodities they provide, as well as all the risks they come with. However, many organizations have jumped into the trend without many prior preparations. This, naturally, led to a lot of failures upon implementing this type of architecture.

As [a wise man once said](https://www.brainyquote.com/quotes/quotes/b/billgates104353.html), "The first rule of any technology used in a business is that automation applied to an efficient operation will magnify the efficiency. The second is that automation applied to an inefficient operation will magnify the inefficiency." I believe this philosophy also applies to microservices. Not preparing your organization for this transition will most probably result in failure. That's why, in this article, I will go through the five steps you need to follow in order to prepare for the implementation of the microservices architecture.

## **1\. Start With Drawing**

Many developers make the mistake of going straight to coding when developing a certain microservice. This is probably the biggest mistake you can make. Yes, maybe you will succeed in making one service; however, as their number increases, the whole thing will become a huge mess.

Like every other product that needs to be created, the process must start with designing. And by designing, I mean gathering around the table with the team and literally drawing the services on paper (or a whiteboard). Start by determining the main function of the application you are building. Then, by doing a top-down approach, break it down into the smallest possible units. Finally, present the interconnectivity of all those distinct pieces. These are the functionalities that will become your microservices.

![](https://dzone.com/storage/temp/5645174-compressed-1.jpg)

For example, in a book review application, the main function is the comparison of different books. However, many other functionalities have to be developed, such as creating user profiles, rating, commenting, a book database, etc. Identifying every single one of these is crucial for capturing them into microservices.

This process will last longer than a day and will require many iterations until perfected. Of course, you'll need input from many people from various departments in order to get diverse viewpoints and opinions, as well as to make sure you don't miss any functionalities of your system.

## **2\. Microservices Are NOT Organizational Units**

It seems natural to define the microservices according to the organizational units of your company. This might seem like an appropriate solution if you are building a monolithic application. However, it can be the wrong decision when implementing microservices architecture.

Maybe it would work for the sales department or customer services, but many organizations have a single unit that handles all databases. Thus, creating a microservice for all databases will lead to having a single point of failure. And that is one of the key features of microservices - NOT having a single point of failure!

Some of the functions you want to present through your services will probably stretch through several organizational departments, or maybe you'll need to build many microservices for a single department. To conclude, you should focus your architecture on the functions you want to provide, rather than the organizational structure of your company.

## **3\. Creating the Proper Team Structures**

Switching to a completely different architectural structure will certainly demand changes in the managerial and monitoring activities in the company. The focus in the first two steps was on designing the application to provide the right function to your end users. Now, it's time to make sure you have the appropriate operational support for the new architecture.

You will have to abandon the old departmental structure and focus teams around certain microservices. This means that each of these teams will consist of various members with different skill sets such as system analysts, UX/UI designers, backend and frontend developers, etc. This way, the teams are responsible for their project (microservice) from end to end - from development and deployment to operations, monitoring, and management. This, in turn, will increase their motivation to create the product they feel their own.

![](https://dzone.com/storage/temp/5645178-microservices-development-lifecycle-1.png)

The size of the teams will be determined by the overall size of the company/project; however, experts suggest that the ideal size is 8-10 people per team. Furthermore, unlike the monolithic architecture, a microservices architecture lets you scale the teams as you grow the business.

Of course, all teams will be actively collaborating towards the finalization of the whole project. This leads us to the main benefit from this kind of structuring - a much faster delivery of the end product to the market.

## **4\. Performance and Reliability Are Important, Too**

The whole idea behind switching to microservices architecture was to create an end product that has greater performance than the monolith, is more reliable (i.e. has a lower risk of downtime) and, of course, can be delivered to the market faster.

It's important to address performance as part of the design process to make sure any potential issues are considered early. Oftentimes, problems arise from the fact that microservice designs focus mainly on functionality. However, the service will become useless if it crashes or slows down significantly the first time it receives a larger load. Every service should have two or three alternative mechanisms it can use to continue operating when underlying resources fail, and it should quickly cycle through them if one fails to respond within an acceptable time frame.

Thinking about how to prepare your service for greater load variations upfront will help your application stand up to real challenges, giving you a competitive advantage on the market -which is the main reason why you decided to switch to microservices in the first place!

## **5\. Plan Changes Ahead**

It is impossible to ignore application changes. Developers add and remove functionalities all the time; they change the code, replace core elements of the app, and so on, all the time. This is even more present with a microservices application. It's actually more correct to say that microservices are constantly evolving.

When you deal with code updates several times a day, it's better to accept that change is a constant, rather than an occasional interruption to a stable state. Once you've recognized this, you will realize it's important to integrate the flexibility necessary for change right from the beginning. One way to make sure your app works properly the whole time is to prepare services APIs so that individual microservices can continue to interact with each other, even as they change. Furthermore, you should include version control to allow services to include both old and new service interfaces.

On the other hand, data storage evolution is much more challenging. Evolving database schemas to support new functionality traditionally has been the most difficult part of upgrading an application, and microservices do not make it any easier. However, the new technology of [NoSQL databases](http://searchdatamanagement.techtarget.com/definition/NoSQL-Not-Only-SQL) is far more flexible in terms of adding new fields without disrupting the existing structure. If you expect your data storage requirements to evolve (and who doesn't?), you should incorporate evolvable data storage as part of your microservices design effort.

We can agree that properly preparing for the transition to a microservices architecture is a key factor in the success of the whole project. Only with careful planning, innovative design thinking, and the proper operational and managerial structure will you be able to reap all the benefits that microservices provide!

Unleash the power of your APIs with future-proof API management - [Create your account](https://dzone.com/go?i=126028&u=http%3A%2F%2Fpages.3scale.net%2Ffuture-proof-api-management-dzinteg.html) and start your free trial today, brought to you in partnership with [3scale](https://dzone.com/go?i=126028&u=https%3A%2F%2Fwww.3scale.net%2F%3Futm_campaign%3Ddzintegration%26utm_source%3Ddzoneint%26utm_content%3Dbumper).
