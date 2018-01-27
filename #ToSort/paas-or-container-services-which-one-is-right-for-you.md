# PaaS or Container Services: Which One Is Right for You?

_Captured: 2017-12-09 at 01:56 from [dzone.com](https://dzone.com/articles/paas-or-container-services-which-one-is-right-for?edition=343106&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-08)_

Are you joining the containers revolution? Start leveraging container management using Platform9's [ultimate guide to Kubernetes deployment](https://dzone.com/go?i=243221&u=https%3A%2F%2Fget.platform9.com%2Fjzlp-kubernetes-deployment-models-the-ultimate-guide%2F).

For many years, Platform as a Service (PaaS) has been the model of choice for developers in the world of cloud computing. But container services are starting to gain more currency in the world of coding. While the two have coexisted for some time, experts are starting to see a shift toward container services as the primary means of managing an application's requirements. In fact, Gartner [estimates](http://www.computerweekly.com/news/4500278148/Gartner-warns-IT-leaders-about-the-perils-of-using-private-platform-as-a-service) that 70% of PaaS users will end up choosing a container service to create apps, during the development process. Read on to learn more about why this change is taking place, and what it means for your company and its apps.

## Why PaaS?

Before PaaS, development teams needed to build infrastructure (and maintain it) for every app they developed. For complicated apps, this was tedious work: You had to write scripts or manually configure servers, storage, security, and infrastructure.

PaaS provided a platform that apps would run within. Rather than the individual application teams providing all of this standard plumbing, it was built into the platform, which the app then interfaced with. This was an elegant solution and offered developers unprecedented agility.

## PaaS and Containers

Containers [made PaaS possible](https://thenewstack.io/role-platform-service-container-era/). Containers are operating system constructs that limit and manage resources for an application. With containers, you could now "pack" all the code needed into the container, which the PaaS then builds on to run and manage the application.

It's important to remember that in first-generation PaaS solutions, these containers were typically proprietary, not open-source. And while PaaS made coding apps swifter and more elegant, it did this by standardizing certain programming decisions, including the language or tools used, and the abstraction of infrastructure. Developers would follow a set of rules to allow the PaaS to take their software artifacts and run it in the PaaS solution's containers.

So while PaaS drove productivity, it also [limited developers' choices](http://www.stratoscale.com/blog/devops/containers-and-paas-what-is-the-relationship-between-them/). But because PaaS was such an efficient solution, and one most enterprises liked (because it allowed them a certain amount of control), it remained the gold standard in app development for a long time.

## Container Software

Breaking free of PaaS became more viable with the advent of container software like [Docker](https://www.docker.com/). These containerization programs allowed any developer to easily describe their app components and build a container image. A container image built in this manner has everything it needs to run smoothly on any system, without any middleware or virtualization layer. Hence, it's also typically very efficient-far more so than a virtual machine.

With Docker and comparable programs, apps are independent from platforms. And they come with everything they need, so they should run identically across different systems. Plus, many of these containers are open source-unlike the containers used in most first-generation PaaS solutions.

## The Future of PaaS

With container software, developers have created a new solution to the problem that caused them to create PaaS in the first place. Container software promises to free developers from many of the strictures that were placed on them with PaaS. For instance, when using a container management program to deploy your app, you can code in any language and use any component you like, whereas PaaS solutions typically limited you to a few languages and components.

However, containers still need to be managed. This is where container management software comes in. By providing services for deploying, monitoring, and managing containers, container management software can do everything that a PaaS can do without the constraints of a fixed platform.

It's likely that some enterprises will try to hold on to PaaS, at least for a while. PaaS is familiar, by this point. And because the platform in a PaaS solution aids in governance (and containers can vary based on their contents), it's likely that some organizations will stay with PaaS for a set of applications.

But container services make delivering portable apps a simple and versatile process. Many teams, especially in the DevOps world, are latching onto container services as their new preferred means of coding, deploying, and managing apps. Over time, you'll likely see many more companies abandoning PaaS in favor of elegant, lightweight, versatile container-based solutions.

Using Containers? Read our [Kubernetes Comparison eBook](https://dzone.com/go?i=243223&u=https%3A%2F%2Fget.platform9.com%2Fjzlp-kubernetes-comparison-ebook%2F) to learn the positives and negatives of Kubernetes, Mesos, Docker Swarm and EC2 Container Services.
