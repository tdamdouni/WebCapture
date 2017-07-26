# Why Docker Can’t Solve All Your Problems in the Cloud

_Captured: 2017-07-08 at 09:21 from [dzone.com](https://dzone.com/articles/why-docker-cant-solve-all-your-problems-in-the-cloud?edition=306238&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-07)_

### As containers gain steam and Docker takes off, here are some guidelines to keep in mind about implementation and why it isn't the end-all answer.

Linkerd, the open source service mesh for cloud native applications. [Get the complete guide](https://dzone.com/go?i=216221&u=http%3A%2F%2Fhubs.ly%2FH07NSwr0) to using Linkerd and Kubernetes to build scalable, resilient applications.

Docker and other container services are appealing for good reason. They are lightweight and flexible. For many organizations, they enable the next step of platform maturity by reducing the needs of a runtime to the bare essentials (at least, that's the intent).

When you dig into the benefits afforded by containers, it's easy to see why so many companies have started projects to:

  * Containerize their apps and supporting services
  * Achieve isolation
  * Reduce friction between environments
  * Potentially improve deployment cycle times

The software development pattern of small things, loosely coupled, can go even further with an architecture built around containerization. We're big fans at Threat Stack, and continue to invest in supporting our customers who rely on them. In fact, we recently announced official CoreOS support for our agent.

However, we have discovered that there is no shortage of misunderstandings about Docker (no surprise, given the rapid growth and pace of change) and other container services in terms of:

  * How their benefits are realized
  * The impact on infrastructure/operations
  * The implications on overall SDLC and Ops processes

Containers certainly offer plenty of benefits, and it makes good sense to explore whether and how they could work for your organization. But it is also a good idea to take off the rose-colored glasses first and approach this technology realistically.

## Why Docker? Why Now?

Many organizations today are running _tons _of AWS instances to spin up new apps, services, databases, etc., and otherwise grow their businesses. While it's super-simple to scale, they've realized this comes with various types of overhead:

  * Replicated compute resources to run a host OS
  * Tons of processes that aren't relevant to your app
  * More instances to manage

This can lead to sprawl, inconsistencies in core images, and process and budgetary challenges. Finance wants to know how Ops teams are modeling their growth and spend, security teams are trying to keep their arms around the growth to ensure that the organization is meeting the goals of its security strategy, and engineering wants to know they can get the flexibility they need to deploy new components quickly. At the same time, the business needs to grow.

So a key question becomes: **How can we optimize our processes, optimize our AWS environment (to save money), and still do what we need to do?**

Docker -- at least on the surface -- appears to offer an answer to this conundrum.

One common theme we've heard from organizations with a lot of AWS instances is the thinking that they can reduce the number of raw instances by increasing the size of individual instances and running containers.

For example, if you have 600 AWS instances that are 1 CPU and 4-5 GB of RAM each, maybe you're thinking you could use Docker containers to reduce that to 100 instances, with 32 CPUs, and 64GB of RAM. Then you can significantly reduce your AWS costs, since you'll have fewer instances. Great, right? Well… It's not that simple.

## What to Consider Before Moving to Containers

In the short term, the shift described above may work for some use cases. But in the long term, as with many technology choices, you're trading one set of complexities for another. Why?

### A New Tech Stack

Well, as soon as you start to run containers at scale, you need to invest in a management and orchestration platform to manage your containers and their resources. This requires a whole tech stack of its own.

And because container usage patterns are still a relatively new subject, there aren't a lot of best practices to rely on, so figuring out the strategy will mean continuous iteration towards production and organizational buy-in that this may impact delivery schedules, depending on the implementations.

### Management Challenges

Other big challenges with containers include the following:

  * How to manage them
  * How to maintain visibility in them
  * How to know when containers are an appropriate solution (and when they aren't)

As far as that third bullet, today, we are seeing a lot of "Docker rationalization." By this, we mean that a lot of organizations are moving to containers _because they can,_ and figuring out the use cases as they go along. This isn't an inherently bad thing (iteration is how evolution happens), but when it comes to determining the impact to your platform's availability, security, and cost-efficiency, it's better to lay out a clear set of use cases with goals ahead of time.

### Security Risks

While it may make sense on the surface to move your workloads to containers, the devil is always in the details. With the greater freedom and optionality that comes with containers comes a responsibility to manage new types of risk. Security can be really challenging when it comes to containers, because there just aren't tried-and-true best practices that you can rely on yet.

As you scale, you'll want to understand how to exert appropriate controls over the images you're using, how they're built, and the scope of access provided to processes. You should know the answers to questions like these in advance:

  * Should a developer ever be allowed to log into a running container in prod?
  * Are we going fully immutable across all containers?
  * How will we manage image size?

Layout out clear answers to these questions at the beginning will help tremendously in keeping your implementation clean and clear.

## Be Honest About the Challenges

Companies are opening up about the challenges they are facing with the complexity of containers, and we hear all the time from people who are running into difficult questions such as:

  * How many and what type of instance types do I need to run these containers? And, what are my true performance bottlenecks?
  * Since the characteristics of my workload are changing over time, how do I know when my container infrastructure needs to adapt and be re-modeled?
  * How do I deal with scaling? Keep going up? Scale out? How do I reduce my surface area but not introduce SPoFs?
  * How do I handle security for containers, my processes running in them, and what they can access outside of the container?

Problems can arise from a lot of vectors. One of the most important things to keep in mind is that, while Docker can indeed help you run faster, **having a powerful engine doesn't get you far if you don't have the rest of the car built to support it.**

## The Future Is Bright

It's clear that containers are a huge part of the future of cloud infrastructure, and we're embracing it at Threat Stack. We'd like to see more organizations approach containers with an open mind that is balanced with a recognition of the risks inherent in containerization.

The good news is that moving your workloads to containers doesn't actually have to reduce visibility. You just need to recognize that Docker can't solve _all_ your problems in the cloud, and that, like any other technology, it should be approached with a healthy mix of optimism and skepticism.

Linkerd, the open source service mesh for cloud native applications. [Get the complete guide](https://dzone.com/go?i=216222&u=http%3A%2F%2Fhubs.ly%2FH07NSwr0) to using Linkerd and Kubernetes to build scalable, resilient applications.
