# Why Serverless?

_Captured: 2018-03-06 at 18:23 from [dzone.com](https://dzone.com/articles/why-serverless-1?edition=366208&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-03-06)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

Web applications are traditionally deployed on **[web servers](https://en.wikipedia.org/wiki/Web_server)** running on physical machines.

As a software developer, you needed to to be aware of the intricacies of the server that runs your software. In order to get an application running on a server, you can spend hours downloading, compiling, installing, configuring, and connecting all sorts of components. The OS of your machines need to be constantly upgraded and patched for security vulnerabilities.

**Managing servers is a time-consuming task which often requires dedicated and experienced systems operations personnel.**

![What server maintenance can feel like -- Metropolis \(1927 film\)](https://i.imgur.com/tyDSU2V.jpg)

## What Is the Point of Software Engineering?

Contrary to what some might think, the goal of software engineering is not to deliver software. A software engineer's job is to deliver value -- to get the usefulness of software into the hands of users.

At the end of the day, you need servers to deliver software. However, the time spent managing servers is time you could have spent on developing new features and improving your application. Instead of worrying about servers, you want to focus on _shipping_.

**When you have a great idea, the last thing you want to do is set up infrastructure.** How can we minimize the time required to deliver impact?

## Moving to the Cloud

Over the past few decades, improvements in both the network and the platform layer -- technologies between the operating system and your application -- have made cloud computing easier.

Back in the days of yore (the early 1990s) developers only had bare metal hardware available to run their code, and the process of obtaining a new compute unit can take from days to months. Scaling took a lot of detailed planning, a huge amount of time and, most importantly, money. A shift was inevitable. The invention of [virtual machines](https://en.wikipedia.org/wiki/Virtual_machine) and the [hypervisor](https://en.wikipedia.org/wiki/Hypervisor) shrunk the time to provision a new compute unit down to minutes through virtualization. Today, [containers](https://www.docker.com/what-container) gives us a new compute unit in seconds.

DevOps has evolved and matured over this period, leading to the proliferation of **[Infrastructure-as-a-Service](https://en.wikipedia.org/wiki/Infrastructure_as_a_service)** (IaaS) and **[Platform-as-a-Service](https://en.wikipedia.org/wiki/Platform_as_a_service)** (PaaS) providers. These third-party platforms lets you delegate the task of maintaining the execution environment for their code to capable hands, freeing the software developer from server and deployment concerns.

![Platform-as-a-Service \(PaaS\) providers allows developers to develop, run, and manage applications without the complexity of building and maintaining their own infrastructure](https://i.imgur.com/NBIGc62.png)

Today, developers have moved away from deploying software on physical computers sitting in their living room. Instead of manually downloading and building a bunch of platform-level technologies on each server instance (and later having to repeat the process when you scale) you can go to a simple web user interface on your PaaS provider of choice, click a few options, and have your application automatically deployed to a fully provisioned cluster.

When your application usage grows, you can add capacity by clicking a few buttons. When you require additional infrastructure components, set up deployment pipelines, or enable database backups, you can do this from the same web interface.

The state of Platform-as-a-Service (PaaS) and cloud computing today is convenient and powerful - but can we do better?

The next major shift in cloud computing is commonly known as "Serverless" or "Functions-as-a-Service" (FaaS.)

> Keep in mind that the phrase "serverless" doesn't mean servers are no longer involved. It simply means that developers _no longer need to think that much about them._ Computing resources get used as services without having to manage around physical capacities or limits. 

![Cloud Computing Evolution](https://i.imgur.com/slhgi6y.png)

Serverless is a **software development approach** that aims to eliminate the need to manage infrastructure by:

  * Using a **managed compute service (Functions-as-a-Service)** to execute your code, and
  * Leveraging **external services and APIs** (third-party Software-as-a-Service products.)

There is now an abundance of third party services: APIs that handles online payments, transactional email, user analytics, code quality measurement, content management, continuous integration, and other secondary concerns. In our everyday work we also make use of external tools for project management, file sharing, office administration, and more.

![Third-party services developers rely on for software development.](https://i.imgur.com/Uw5uDmB.png)

Instead of spending valuable resources on building up secondary capabilities such as infrastructure and server maintenance, developers can _focus on their core value proposition_. Rather than building things from scratch, developers can connect prefabricated parts together and prune away secondary complexity from the application. By making use of third-party services, you can build loosely coupled, scalable, and efficient architectures quickly.

The Serverless movement and FaaS platforms are a major step towards delegating infrastructure problems to companies that are much better positioned to deal with them. No matter how good you become at DevOps, Amazon, Google, or Microsoft will almost certainly have done it better. You can now get all the benefits of a modern container farm architecture without breaking the bank or spending years building it yourself.

Why go Serverless? So you can always be shipping.

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

Topics:

serverless ,serverless architecture ,serverless computing ,cloud computing ,software development ,software architecture ,programming ,web applications ,faas ,paas
