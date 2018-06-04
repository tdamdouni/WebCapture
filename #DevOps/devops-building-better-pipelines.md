# DevOps: Building Better Pipelines

_Captured: 2018-03-23 at 13:26 from [dzone.com](https://dzone.com/articles/devops-building-better-pipelines?edition=368224&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-03-23)_

"The deployment pipeline takes value from development and delivers it to clients."

This is one of the better summations of a development pipeline that I have heard, and it came from [Dan Barker](http://danbarker.codes/) ([@barkerd427](https://twitter.com/barkerd427)) during his recent[ All Day DevOps](https://www.alldaydevops.com/) conference talk, " _Becoming a Plumber: Building Deployment Pipelines_." Dan's talk focuses on the value of pipelines, how to build them well, and how to build both development and infrastructure pipelines.

## **Traditional Pipelines**

The traditional pipeline: development-->test-->production servers is a good foundation, and, like the plumbing in your home, is helpful to generally get us where we want to go. However, as anyone who has raised boys knows, a toilet doesn't guarantee 100% compliance. The user isn't perfect.

It is similar to basic development pipelines. Things don't go quite as planned. As Dan mentioned in his talk, as a developer, he strides to keep his code all in dev, and then push to test, and then push to production. However, that doesn't always happen. And there are other inconsistencies that inadvertently crop up (such as tab vs. space), despite everyone's best intentions.

Dan is a chief architect and works in highly-regulated industries -- financial services, health care, and insurance -- so precision, compliance, audit trails, etc. are all the more important. He architects pipelines to ensure human error is minimized.

## **What's in a Pipeline?**

But why all of the fuss over pipelines? Well, first Dan touched on some of the values pipelines provide:

  * Abstract audit and compliance
  * Trivialities eliminated (spaces vs. tabs)
  * Security checks occur early/often
  * Tests all the things
  * Nimble security
  * Common artifact repositories
  * Standardized approval system
  * Apps become secure by default

But how do you architect a pipeline to deliver these values?

In the illustration below, you can see Dan's pipeline architecture where he offers key points that all of us should consider applying:

  * Production data is separated from development data. You can only get there through the pipeline
  * You interact with the Platform, and it configures the levels below it
  * You can duplicate containers as much as you want to scale horizontally, and can replicate that in production
  * The configuration must come from the environment

As he dug in, he started with covering the advantages of two types of pipelines, recognizing you need to select this first:

Scripted:

  * More powerful
  * Provides greatest level of flexibility

Declarative:

  * Only a little Groovy
  * Simpler to maintain
  * Easier to read and understand

Dan then dug into the technical nitty-gritty, such as shared libraries, setups, software to manage pipelines, [fabric8](https://fabric8.io/), [Kubernetes](https://kubernetes.io/), [Yahoo! Screwdriver](http://screwdriver.cd/), etc. and then made the observation that he thinks that deployment pipelines have fallen behind. In his real-life example, he and his team decided to take a more holistic approach to their pipeline (think: [the first way of DevOps](https://itrevolution.com/the-three-ways-principles-underpinning-devops/)) so they could build and deploy apps and also build and deploy the infrastructure.

## **Sharing Knowledge**

They built a system that is especially applicable to those in highly-regulated industries, and they hope to open-source it soon, so keep an eye on[@barkerd427](https://itrevolution.com/the-three-ways-principles-underpinning-devops/) for more info. In the meantime, he describes in detail the process it follows, software and libraries it uses, etc.

If you are looking to build better pipelines, if you want to find out how Dan built the dual pipeline for the apps and the infrastructure, or you are just interested in his thoughts on better pipelines and the advantages and disadvantages of different software packages, Dan's full talk is [here.](https://youtu.be/iDFsCaEKWew)

Yearning for more? You can watch any of the [2017 AllDayDevOps](https://www.alldaydevops.com/) sessions free-of-charge.
