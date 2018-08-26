# Comparing Containers vs. Serverless

_Captured: 2018-06-26 at 19:26 from [dzone.com](https://dzone.com/articles/comparing-containers-vs-serverless?edition=383261&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-06-26)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

This post was originally published [here](https://caylent.com/containers-vs-serverless/).

In development history, we used to rely on single, physical servers. We manually set up, coded, scaled, and maintained our servers--practically nursing our charges day and night--to provide functionality for other machines. The process was slow, detailed, and required a lot in terms of personal time. From there, we began to mix combining our physical servers with a cluster format or used virtual machines to run multiple applications. Things got faster, but everything was still pretty manual. Eventually, we moved into Infrastructure-as-a-Service, otherwise known as IaaS, otherwise known as the Cloud.

Individuals could rent servers for a monthly fee, it was easier to scale up or down, and the process was significantly faster. The technology, Platform-as-a-Service (PaaS) already existed under Cloud technology as a method of delivery but provided even further improvements in security, scaling, etc. Containers also made PaaS possible and smoother too, providing even more benefits. And finally, later, Function-as-a-Service (FaaS) came into being, which many may know better by the name Serverless.

Some say that containers are yesterday's news, and serverless is the way to go for creating modern-day applications. Are they right? In fact, both represent architecture that is designed for future changes, and both are intended for leveraging the latest innovations. So, let's compare the two.

## Containers

Containers are dedicated or exclusive light-weight boxes which contain all pre-installed dependencies and application code. They can be run anywhere in a single package, quickly, consistently and reliably regardless of the deployment environment. Initially, the technology was innovative, but devs had to know Linux, and also had to know how to design a script to place an application in a container and run it as a host. When the San Francisco PaaS company Dotcloud was launched, they presented a CLI tool known as Docker which made managing containers easy. Then Google worked on an open-source platform called Kubernetes for managing containers. The rest is history, as they say, and today, there are now a great many cloud providers that offer hosts for containers.

## Serverless

Serverless is called such because the owner of the system does not have to purchase or rent servers for the back-end code to operate. They can be run without containers. That said, there are in fact still physical servers, as with any cloud-based service, but the end-user doesn't have to bother themselves about them. That's the responsibility of the service provider and the developers. Amazon's Lambda Service, launched in 2014, made the serverless technique a hot trend. When Amazon introduced API Gateway, the functionality became even better and more extensive.

## Which is Better: Containers or Serverless?

In reality, it seems that even though serverless is a newer technology than containers, they both have pros and cons that make them both useful and both relevant. So, it entirely depends on individual circumstances that need to be factored in when attempting to decide which solution is the right choice.

### Advantages of Containers

  1. Container technology allows you to make your applications as large as you want. Going serverless, that's not always the case, because size and memory constraints may occur.
  2. Migrating existing applications is easier to do with containers than it is serverless.
  3. You have flexibility and full control with containers when managing resources, setting policies, and controlling security. They can be run with various software stacks inside too. Testing, debugging, and monitoring is not as easy with serverless tech.
  4. A container, just by its nature, is portable. Move them around and run them anywhere. So, it doesn't matter if it's in the Cloud, on a bare metal server or whatever. They are vendor-agnostic whereas going serverless, by its nature, depends on a third party.
  5. A big complicated application may be better with containers. Then, if you choose to move your application over to the Cloud, it will be easy to follow through.

### Disadvantages of Containers

  1. One of the biggest disadvantages is the overhead. You are the one who has to run the container, make sure there are security fixes, and monitor them all as needed.
  2. The learning curve with containers can be steep; not only to get them going but to keep them maintained.
  3. Running containers can also get expensive.

### Advantages of Serverless

  1. One of the most important advantages is that there's no administration of infrastructure needed. Just upload your functions, and that's it. The rest is the responsibility of the service provider and the developer's problem. Without having to worry about hardware, the load is lightened on the application developer. So, IT organizations can focus on what they should be focusing on, which is developing applications instead of worrying about maintenance.
  2. There's no worry about scalability. The Cloud provider you choose does it for you by scaling automatically.
  3. Serverless is cheaper than containers. You pay per function execution. You don't pay for the idle time. When an application is not being used, it shuts down, and it's not incurring a cost. This is great for startups that are short on cash. Serverless computing can save a cash-strapped startup a lot of money.
  4. Updating or modify a single function is typically easier to do with loosely coupled architecture.
  5. Almost all serverless solutions support event triggers. Which means they are great for pipelines and sequenced workflows.

### Disadvantages of Serverless

  1. It's a technology that's not good for long-running applications. Containers are better for that.
  2. Serverless is considered "black box" technology, meaning you don't necessarily know what's going on inside.
  3. Serverless is commonly dependent on a third party. Changing to a third party provider can be a headache.
  4. The architecture of a true microservices environment can be very tricky to get right and typically requires significant upfront human resource costs for serverless.

So when comparing containers vs. serverless, you can see that there are pros and cons with both. It really comes down to choosing what is right for your solution needs.

If you have the income, the flexibility, and the knowledge to install and maintain containers, and you want to be in control, then they're a good choice, especially if you have large deployment needs. A developer can use Docker that runs on both Windows and Linux. And then, of course, there is Kubernetes which can help to manage large-scale container set-ups. The world of Kubernetes offers a wide variety of tools, (I've listed a [full 50 here](https://caylent.com/50-useful-kubernetes-tools/)) such as kubectl, for deploying and troubleshooting a container; Telepresence, another great development tool that uses a hybrid model; and Minikube, that allows you to run Kubernetes on your laptop without the need for WiFi.

Serverless, the newest of the technologies we've discussed, is typically fully managed. All the developer has to do is upload the code to the providers, which saves a lot of time and headaches. It's hands-off, so you don't have to concern yourself with the underlying infrastructure. The technology is great for startups who wish to save money or for those with a limited income because when it's not in use, it shuts down and no costs are incurred. It's a pay-as-you-go model. If you don't have an issue with limitations via vendor support or ecosystem lock-in, it can be a good solution for your needs.

Even though serverless is the newer technology, containers will still continue to play a significant and much-needed role. In fact, there are still developers who feel that serverless will not kill containers, and, furthermore, they don't even see serverless as a threat to container tech. There's a potential for their functionality overlapping, but only in some instances. Indeed, as we compare the pros and cons, that is currently the case. In fact, with the existence of serverless and containers, you may likely end up using both to satisfy different solutions.

The counterargument to this as anyone in technology knows is that things change at a rapid pace. What was once state-of-the-art becomes obsolete, replaced by something that is more efficient--and often cheaper. So, as serverless technology continues to evolve, we may see the time when containers do indeed become 'yesterday's news'.

[Caylent](http://www.caylent.com/) offers DevOps-as-a-Service to high growth companies looking for help with microservices, containers, cloud infrastructure, and CI/CD deployments. Our managed and consulting services are a more cost-effective option than hiring in-house and we scale as your team and company grow. Check out some of the use cases and learn how we work with clients by visiting our [DevOps-as-a-Service offering](https://caylent.com/devops-as-a-service/).

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

Topics:

containers ,serverless ,container adoption ,container application ,container deployment ,serverless architecture ,serverless computing ,serverless frameworks ,serverless development ,cloud
