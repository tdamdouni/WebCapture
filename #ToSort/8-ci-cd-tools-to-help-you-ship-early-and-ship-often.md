# 8 CI/CD Tools to Help You Ship Early and Ship Often

_Captured: 2017-05-14 at 17:32 from [dzone.com](https://dzone.com/articles/8-cicd-tools-to-help-you-ship-early-and-ship-often?edition=298099&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-13)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Ensuring code quality and compliance is one of the toughest issues facing Node.js teams - we want to ship early and ship often, but we also want to ship _well_. You don't want to send something that's going to break, something that's going to fail, to the user, right?

Part of the way we've been able to keep up the _ship early, ship often_ mantra is through heavy automation. We've built out entire ecosystems around automation that allow us to ship _quickly_ and mitigate the majority of issues before they happen. One of the key developments in this process of automation has been the widespread adoption of Continuous Integration and Continuous Delivery, also known as CI/CD.

Last week, I published an article on some [convenient CI/CD tools for Node.js projects](https://nodesource.com/blog/seven-convenient-ci-cd-tools-for-your-node-js-projects). This week, I wanted to take a slightly different approach and share some lesser known tools you either may not have known about or not known to think of that can really provide a helpful boost to your development lifecycle in the CI/CD stage.

## Build Systems

### CodeShip

[CodeShip](https://codeship.com) is a pretty simple CI/CD platform that's awesome for smaller and medium teams. It's quick to set up and get going with extremely low friction - about comparable to Travis in terms of ease-of-use, which I mentioned in my article on [CI/CD tools for Node.js](https://nodesource.com/blog/seven-convenient-ci-cd-tools-for-your-node-js-projects) last week, but with a sizable set of integrations and options that will allow you to customize your CI/CD pipeline to your workflow and tools of choice.

If you want to get up and running _quickly_ with a CI/CD pipeline integrated into your workflow for a smaller team that's using one of the common cloud service providers (like Azure, GCP, or AWS - each of which they have docs for), CodeShip is probably going to be a good option for you. That said, you may want to look into others like [CircleCI](https://circleci.com/) or [MagnumCI](https://magnum-ci.com/) as alternatives.

### CodeFresh

[CodeFresh](http://codefresh.io/) is an interesting tool that I had the chance to learn a bit about at DockerCon in Austin a few weeks ago. Basically, they're taking a different approach and providing a CI/CD pipeline purely for your Docker images.

While not what I've thought as a typical application CI/CD platform, CodeFresh is giving an interesting way to think about and use CI/CD in the evolving landscape of containerization with [Docker](https://nodesource.com/blog/tag/docker), [Kubernetes](https://nodesource.com/blog/tag/kubernetes), and the Cloud-native landscape.

### Bamboo

[Bamboo](https://www.atlassian.com/software/bamboo) is a CI/CD offering from Atlassian. It has a pretty extensive out-of-the-box feature set and is runnable from your hardware. A more enterprise-focused solution with really competitive features, pricing, and support - it's an interesting CI/CD system that we've seen in production a few times at an impressive scale.

If you're using the Atlassian stack with your team, Bamboo is really an easy choice. It offers a ton of other integrations as well, so you can tweak it to your team's ideal workflow and get going.

## CI/CD in Your Version Control

### GitLab

[GitLab](https://about.gitlab.com/features/gitlab-ci-cd/) has done some super awesome development around the CI/CD story in their platform. At this point, after GitHub integration, I've been seeing GitLab CI/CD integration as a common base feature for almost any CI/CD tooling that's not entirely focused on free and open-source projects.

They've really built out a pretty extensive CI/CD feature set in a really short amount of time. One nice thing is that it's free on the hosted GitLab site, and comes built-in with the Enterprise version as well - so if you're using GitLab for version control, chances are you can get up and running with CI/CD pretty quickly.

### BitBucket

I've already mentioned Atlassian's Bamboo build system, but Atlassian also has integrated, hosted CI/CD tooling in BitBucket as well, which they call [Pipelines](https://bitbucket.org/product/features/pipelines). Basically, Pipelines are BitBucket's solution to CI/CD integration into the hosted SaaS version of BitBucket - again, if you're using BitBucket as part of your toolset, pipelines are a simple place to start integrating CI/CD into your workflows.

### GitHub's Integration Library

This is a feature I'd totally forgotten about until I was doing some research recently, but GitHub actually has a _really_ nice section for CI/CD in their [Integrations Library](https://github.com/integrations/feature/continuous-integration).

## CI/CD in Your Cloud

### Azure

Azure is growing really quickly with pretty impressive adoption by the CI/CD tools. Any CI/CD platform is going to support it at this point. [CodeShip](https://documentation.codeship.com/pro/continuous-deployment/azure/) and [CircleCI](https://circleci.com/integrations/azure/) both integrate into Azure natively, and Microsoft has been building some really good guides surrounding CI/CD and the Azure Container Service for other tooling like [Jenkins](https://docs.microsoft.com/en-us/azure/container-service/container-service-kubernetes-jenkins) and [DC/OS](https://docs.microsoft.com/en-us/azure/container-service/container-service-setup-ci-cd).

Microsoft has done a fantastic job with their CI/CD, Node.js, and container story on Azure to the point that you can now tailor a CI/CD system to your specific technical needs pretty rapidly, allowing you to set up and start shipping your apps to production with as little friction as possible.

### Heroku

Heroku's also got an interesting CI/CD tool, which they aptly call [Flow](https://www.heroku.com/continuous-delivery/on-heroku). Flow lets you set up what Heroku calls a Pipeline (different from BitBucket's Pipelines, mentioned earlier) that you can run your staging workflow, setup review apps that you can start up and spin down with relative ease, and integrate into GitHub for deployment requests and status.

Flow seems to be a perfect extension of the Heroku platform. It enables the quick spin-ups that Heroku has always been good at, and extends that strength into the CI/CD workflow.

## Just One More Thing...

If you'd like to keep reading about Node.js, deployment, security, and more, I've got some awesome resources for you.

Containers are becoming more and more central to the story surrounding the CI/CD toolchain. If you're working with CI/CD building Node.js apps, I definitely recommend you go check out our [tips for dockerizing Node.js apps](https://nodesource.com/blog/8-protips-to-start-killing-it-when-dockerizing-node-js) \- otherwise, you may want to check out our other [Docker articles](https://nodesource.com/blog/tag/docker).

Additionally, if you're interested in locking down your Node.js apps and getting insight into the security, licenses, and overall quality of your dependencies, you should check out [NodeSource Certified Modules](https://nodesource.com/products/certified-modules). We've built out Certified Modules as a tool geared toward ensuring security and quality all the way down - an important part of development and deployment strategies when working with Node.js applications at scale.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
