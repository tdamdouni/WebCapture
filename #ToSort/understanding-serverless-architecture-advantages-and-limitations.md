# Understanding Serverless Architecture Advantages and Limitations

_Captured: 2018-01-23 at 15:09 from [dzone.com](https://dzone.com/articles/understanding-serverless-architecture-advantages-a?edition=355120&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-01-23)_

### Serverless computing and architecture are rising topics in the tech community's consciousness. Read more about why they might be worth your attention.

Create a continuous deployment pipeline with open source tools. [Watch the screencast.](https://dzone.com/go?i=272426&u=https%3A%2F%2Fwww.fastly.com%2Flc%2Fci-cd-with-terraform%2F%3Futm_medium%3Ddisplay%26utm_source%3Ddzone.com%26utm_campaign%3DFY18Q1_GatedContent_CI%2FCDTerraform%26utm_content%3DDzone_BumperTextLink)

Just before all the hype about Microservices Architecture is gone, there is another term which is looming within the technology forums. Even though this is not entirely new concept, it became a talking topic recently. This hot topic is Serverless Architecture and Serverless computing. As I have already mentioned, this was around us for some time with the advent of Backend-as-a-Service, commonly abbreviated as BaaS or MBaaS. But it was at a different scale before AWS Lambda, Azure Functions and Google Cloud Functions came into the picture with their own serverless solutions.

![](https://cdn-images-1.medium.com/max/1000/1*KARkmNADCABhELk_fEQlvQ.png)

In layman's terms, Serverless Architecture or Serverless Computing means that your backend logic will run on some third party vendor's server infrastructure which you don't need to worry about. It does not mean that there is no server to run your backend logic, but rather that you do not need to maintain it. That is the business of these third party vendors like AWS, Azure and Google. Serverless computing has 2 variants.

  * Backend-as-a-Service (BaaS or MBaaS -- M for Mobile)

  * Function-as-a-Service (FaaS)

With BaaS or MBaaS, backend logic will run on a third party vendor. Application developer do not need to provision or maintain the servers or the infrastructure which runs this backend services. In most cases, these back end services will run continuously once they are started. Instead, application developers need to pay a subscription to the hosting vendor. In most cases, this subscription is weekly, monthly or yearly basis. Another important aspect of BaaS is that it will run on shared infrastructure and the same backend service will be used by multiple different applications.

The second variant is the more popular one these days which is Function-as-a-Service or FaaS. Most of the popular technologies like AWS Lambda and Microsoft Azure Functions as well as Google Cloud Functions fall into this category. With FaaS platforms, application developers (users) can implement their own backend logic and run them within the serverless framework. Running of this functionality in a server will be handled by the serverless framework. All the scalability, reliability, and security aspects will be taken over by this framework. Different vendors provide different options to implement these functions with popular programming languages like Java and C#.

Once these functions are implemented and deployed on the FaaS framework, the services offered by these functions can be triggered via events from vendor specific utilities or via HTTP requests. If we consider the most popular FaaS framework which is AWS Lambda, it allows users to trigger these functions through HTTP requests by interfacing the Lambda functions with AWS API Gateway. There are few main differences of FaaS when compared to BaaS.

  * Cost would be only for the amount of resources used (per minute level charging)
  * Ideal for hugely fluctuating traffic as well as typical user traffic
  * FaaS function will run for a short period of time (at max 5 mins for Lambda function)

All the above mentioned points proves that Serverless Computing or Serverless Architecture is worth giving a shot. It will simplify the maintenance of backend systems while giving cost benefits for handling all sorts of different user behaviors. But according to Newtons 3rd law, there is a reaction for every action, meaning there are some things we need to be careful when dealing with serverless kind of architectures.

  * Vendor locking can cause problems like frequent mandatory API changes, pricing structure changes and technology changes.
  * Latencies occur at initial requests can become challenging for providing better SLAs across multiple concurrent users.
  * Since server instances are come and go, maintaining the state of an application is really challenging with these types of frameworks.
  * Not suitable for running long-running business processes since these function (services) instances will destroy after a fixed time duration.
  * There are some other limitations like maximum TPS which can be handled by a given function within a given user account (AWS) is fixed by the vendor.
  * End-to-end testing or integration testing is not easy with the functions come and go.
  * Lack of monitoring and debugging capabilities to the user about the production system and it's behaviors. User had to trust whatever the monitoring options provided by the vendor.

Having said all these limitations, these things will change in the future with more and more vendors coming along with more improved versions of their platforms.

Another important thing is the difference between a PaaS and a FaaS (or BaaS or MBaas). With PaaS platforms, users can implement their business logic with a plethora of programming languages as well as other well known technologies. There will always be servers running in the backend specifically for the user applications and will run continuously. Due to this behavior of the PaaS frameworks, pricing is based on large chunks, usually weekly, monthly, or yearly. Another important aspect is the automatic scalability of the resources is not that easy with these platforms. If you have these requirements, considering a Serverless Computing platform (FaaS) would be a better choice.

Finally, with the type of popularity achieved by the Microservices Architecture, Serverless Architecture is well suited for adopting a MSA without the hassle of maintaining the servers, scalability and availability headaches. Even though Serverless computing has the capabilties to extend the popularity of MSA, it has some limitations when it comes to practical implementations due to the nature of vendor specific concepts. Hopefully these things will eventually go away with concepts like serverless framework.
