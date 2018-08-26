# Is Serverless Just a New Word for Cloud Based?

_Captured: 2018-06-26 at 19:27 from [dzone.com](https://dzone.com/articles/is-serverless-just-a-new-word-for-cloud-based?edition=383261&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-06-26)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

![](https://www.percona.com/blog/wp-content/uploads/2018/06/serverless-architecture-300x159.jpg)

Serverless is a new buzzword in the database industry. Even though it gets tossed around often, there is some confusion about what it really means and how it really works. Serverless architectures rely on third-party Backend as a Service (BaaS) services. They can also include custom code that is run in managed, ephemeral containers on a Functions as a Service (FaaS) platform. In comparison to traditional Platform as a Service (PaaS) server architecture, where you pay a predetermined sum for your instances, serverless applications benefit from reduced costs of operations and lower complexity. They are also considered to be more agile, allowing for reduced engineering efforts.

In reality, there are still servers in a serverless architecture: they are just being used, managed, and maintained outside of the application. But isn't that a lot like what cloud providers, such as Amazon RDS, Google Cloud, and Microsoft Azure, are already offering? Well, yes, but with several caveats.

When you use any of the aforementioned platforms, you still need to provision the types of instances that you plan to use and define how those platforms will act. For example, will it run MySQL, MongoDB, PostgreSQL, or some other tool? With serverless, these decisions are no longer needed. Instead, you simply consume resources from a shared resource pool, using whatever application suits your needs at that time. In addition, in a serverless world, you are only charged for the time that you use the server instead of being charged whether you use it a lot or a little (or not at all).

## **Remember When You Joined That Gym?**

How many of us have purchased a gym membership at some point in our life? Oftentimes, you walk in with the best of intentions and happily enroll in a monthly plan. "For only $29.95 per month, you can use all of the resources of the gym as much as you want." But, many of us have purchased such a membership and found that our visits to the gym dwindle over time, leaving us paying the same monthly fee for less usage.

Traditional Database as a Service (DBaaS) offerings are similar to your gym membership: you sign up, select your service options, and start using them right away. There are certainly cases of companies using those services consistently, just like there are gym members who show up faithfully month after month. But there are also companies who spin up database instances for a specific purpose, use the database instance for some amount of time, and then slowly find that they are accessing that instance less and less. However, the fees for the instance, much like the fees for your gym membership, keep getting charged.

What if we had a "pay as you go" gym plan? Well, some of those certainly exist. Serverless architecture is somewhat like this plan: you only pay for the resources when you use them, and you only pay for your specific usage. This would be like charging $5 for access to the weight room and $3 for access to the swimming pool, each time you use one or the other. The one big difference with serverless architecture for databases is that you still need to have your data stored somewhere in the environment and made available to you as needed. This would be like renting a gym locker to store your workout gear so that didn't have to bring it back and forth each time you visited.

Obviously, you will pay for that storage, whether it is your data or your workout gear, but the storage fees are going to be less than your standard membership. The big advantage is that you have what you need when you need it, and you can access the necessary resources to use whatever you are storing.

With a serverless architecture, you store your data securely on low-cost storage devices and access as needed. The resources required to process that data are available on an on-demand basis. So, your charges are likely to be lower since you are paying a low fee for data storage and a usage fee on resources. This can work great for companies that do not need 24x7x365 access to their data since they are only paying for the services when they are using them. It's also ideal for developers, who may find that they spend far more time working on their application code than testing it against the database. Instead of paying for the database resources while the data is just sitting there doing nothing, you now pay to store the data and incur the database associated fees at use time.

## **Benefits and Risks of Going Serverless**

One of the biggest possible benefits of going with a serverless architecture is that you save money and hassle. Money can be saved since you only pay for the resources when you use them. Hassle is reduced since you don't need to worry about the hardware on which your application runs. These can be big wins for a company, but you need to be aware of some pitfalls.

First, serverless _can_ save you money, but there is no guarantee that it _will_ save you money.

Consider 2 different people who have the exact same cell phone -- maybe it's your dad and your teenage daughter. These 2 users probably have very different patterns of usage: your dad uses the phone sporadically (if at all!) and your teenage daughter seems to have her phone physically attached to her. These 2 people would benefit from different service plans with their provider. For your dad, a basic plan that allows some usage (similar to the base cost of storage in our serverless database) with charges for usage above that cap would probably suffice. However, such a plan for your teenage daughter would probably spiral out of control and incur very high usage fees. For her, an unlimited plan makes sense. What is a great fit for one user is a poor fit for another, and the same is true when comparing serverless and DBaaS options.

The good news is that serverless architectures and DBaaS options, like Amazon RDS, Microsoft Azure, and Google Cloud, reduce a lot of the hassle of owning and managing servers. You no longer need to be concerned about Mean Time Between Failures, power and cooling issues, or any of the other headaches that come with maintaining your hardware. However, this can also have a negative consequence.

#### The challenge of enforced updates

About the only thing that is consistent about software in today's world is that it is constantly changing. New versions are released with new features that may or may not be important to you. When a serverless provider decides to implement a new version or patch of their backend, there may be some downstream issues for you to manage. It is always important to test any new updates, but now some of the decisions about how and when to upgrade may be out of your control. Proper notification from the provider gives you a window of time for testing, but they are probably going to flip the switch regardless of whether or not you have completed all of your test cycles. This is true of both serverless and DBaaS options.

#### A risk of vendor lock-in

A common mantra in the software world is that we want to avoid vendor lock-in. Of course, from the provider's side, they want to avoid customer churn, so we often find ourselves on opposite sides of the same issue. Moving to a new platform or provider becomes more complex as you cede more aspects of server management to the host. This means that serverless can cause deep lock-in since your application is designed to work with the environment as your provider has configured it. If you choose to move to a different provider, you need to extract your application and your data from the current provider and probably need to rework it to fit the requirements of the new provider.

#### The challenge of client-side optimization

Another consideration is that optimizations of server-side configurations must necessarily be more generic compared to those you might make to self-hosted servers. Optimization can no longer be done at the server level for your specific application and use; instead, you now rely on a smarter client to perform your necessary optimizations. This requires a skill set that may not exist with some developers: the ability to tune applications client-side.

## **Conclusion**

Serverless is not going away. In fact, it is likely to grow as people come to a better understanding and comfort level with it. You need to be able to make an informed decision regarding whether serverless is right for you. Careful consideration of the pros and cons is imperative for making a solid determination. Understanding your usage patterns, user expectations, development capabilities, and a lot more will help to guide that decision.

In a future post, I'll review the architectural differences between on-premises, PaaS, DBaaS and serverless database environments.

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

Topics:

cloud ,database ,cloud storage ,payment model ,serverless computing ,cloud computing
