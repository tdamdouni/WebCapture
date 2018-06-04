# Best Practices for Continuous Delivery

_Captured: 2018-04-11 at 19:10 from [dzone.com](https://dzone.com/articles/best-practices-for-continuous-delivery?edition=373199&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-04-11)_

With the influx of DevOps-related products and services on the market, today's application delivery toolchain has become complex and fragmented. Watch [Avoiding the DevOps Tax](https://dzone.com/go?i=286421&u=https%3A%2F%2Fabout.gitlab.com%2F2018%2F03%2F21%2Favoiding-devops-tax-webcast%2F) to learn best practices for integration and automation to realize a faster DevOps lifecycle.

Transitioning your development team to continuous delivery can be a big undertaking. Just like your CD automation process, you should take it in stages, don't change everything all at once and have the option to rollback if there's a problem. Although the process can be challenging, the benefits of doing so will allow you to respond more quickly to customer needs and ultimately be more competitive in the marketplace.

### Benefits of Automation

Other benefits of automation include:

  * Time to market reduced from weeks and months to days or hours.
  * Less error prone software means reduced go to market risk.
  * Less time spent on Ops reduces the costs of software development.
  * A more empowered development team.

Once you've successfully built an automatic pipeline, you can use some of the best practices listed here to fine-tune your pipeline before switching over your entire development environment.

We've grouped these best practices into three main categories:

  * #1. Software Architecture - overall architecture of your services and products sets the tone for how your build pipeline is constructed and how your teams interact with it.
  * #2. Automation Patterns - automation and test strategies.
  * #3. Company Culture - team organization, transparency, and responsibilities.

## 1\. Software Architecture

### Adopt Microservices - Sensibly

In order to implement a truly agile and automated pipeline, it is recommended that your products have been architected into microservices.

To read more about why you need microservices see: [What are Microservices?](https://www.weave.works/blog/what-are-microservices/), and [An Introduction to Microservices: an AWS perspective](https://www.weave.works/blog/introduction-microservices-aws-perspective/).

Unless you're creating an application from scratch, re-architecting your entire application can be a monumental effort. If you have an existing system, it may be best to switch over to microservices incrementally. You may, for example, adopt the [strangler pattern](https://www.martinfowler.com/bliki/StranglerApplication.html), an approach developed by Martin Fowler that increments your monolithic architecture to microservices while still leveraging existing business systems.

In this method, your mission-critical systems are maintained and the new architecture is built around it. Over time, the old systems are gradually replaced with the new architecture rather than 'going all-in'.

## 2\. Automation Patterns

### Implement GitOps

For optimized Mean Time to Recovery (MTTR), you should implement GitOps.

GitOps works by using Git as a source of truth for declarative infrastructure and applications. Automated delivery pipelines roll out changes to your infrastructure when changes are made to Git.

Not only is there is a 'source of truth' for both your infrastructure and application code, but when disaster strikes, infrastructure can be quickly restored from Git by your development team, reducing your MTTR from hours to minutes.

For more on GitOps, see "[Operations by Pull Request](https://www.weave.works/blog/gitops-operations-by-pull-request)" and "[GitOps: High-velocity CICD for Kubernetes](https://www.weave.works/blog/gitops-high-velocity-cicd-for-kubernetes)."

### Automate With Security in Mind

An important consideration when working with a large team and automated pipelines to Kubernetes are security credentials for your cluster. In order to deploy an update to your cluster, credentials have to be kept somewhere. Ideally, these should be kept inside the cluster and if they live outside, then they should be kept secure in something like [Vault](https://www.vaultproject.io/).

### Push vs. Pull Pattern

A pull-type automated pipeline offers better security because your CI is decoupled from the CD. Most of the CI/CD tools available today use a push-based model. Push-based means that code goes through the pipeline starting with the CI system and continues its path through a series of encoded scripts or by using 'kubectl' by hand to push changes to the Kubernetes cluster. Overall if used carelessly, CI can be an entry point to your systems.

A pull pattern like that of Weave Cloud, relies on of two key components: a Deploy Automator that watches the image registry and a Deploy Synchronizer that sits in the cluster to maintain its state.

![](https://images.contentstack.io/v3/assets/blt300387d93dabf50e/bltbfa1e1e178b2fa8e/5ac694ad781602830bdf9457/download)

> _The pull approach is more secure because Weave Cloud deploy:_

  * Only carries out operations permitted by Kubernetes' Role Based Access Control (RBAC), policy and security. Trust is shared with the cluster and not managed separately.
  * Binds natively to all Kubernetes objects and knows whether operations have completed or need to be retried.

### Don't Rebuild Images From Scratch Each Time

Save valuable time by not rebuilding images every time you run updates through your pipeline. Build each container image just once and 'promote' it through each test sequence/environment, and do not rebuild each time. If you are practice GitOps, you can make changes to declarative configuration files in Git or you can use Weave Cloud deploy to do it for you.

### Decouple Deployments From Releases

Adding in a deployment stage before you release to your customers allows you to do smoke tests, or even more involved testing like blue-green deployments, canary or A/B testing.

An important distinction to be aware of is the difference between a deployment and a release. A deployment is when software has been tested and installed into a particular environment; whereas, a release is when those changes actually get into the hands of your end-users.

### Measure Your Pipeline Success

Establish and track key metrics across your pipeline. You can measure these both before you started automation and then compare the results after you've automated.

  * Deployment Frequency - number of deployments done per day.
  * Change Lead Time - amount of lead time it takes to deploy a change.
  * Mean Time to Recovery (MTTR) - the time it takes to restore your application if disaster strikes.
  * Change Fail Rate - amount of downtime expressed as a percentage of uptime.

## 3\. Company Culture for Continuous Delivery

### Create an Open No Blame Culture

Create transparency around the process of automation. Allow developers to make mistakes, so that gaps in the process can be addressed and corrected. This is also true once you've achieved automation as well where developers need full ownership over the pipeline, and when tests fail, code changes can be rolled back quickly.

### Everyone Takes Responsibility for the Build

With a fully automated pipeline, anybody should be able to diagnose and fix a build a problem. This not only results in a more democratized software development process, but it also fosters better teamwork and collaboration across your whole organization.

## Final Thoughts

Error-prone manual deployments increase both risks and costs for software releases and can diminish a company's ability to remain competitive in their respective fields. Implementing an automated Continuous Delivery pipeline can be a daunting task, but in the end is worth the initial disruption.

With the influx of DevOps-related products and services on the market, today's application delivery toolchain has become complex and fragmented. Watch [Avoiding the DevOps Tax](https://dzone.com/go?i=286422&u=https%3A%2F%2Fabout.gitlab.com%2F2018%2F03%2F21%2Favoiding-devops-tax-webcast%2F) to learn best practices for integration and automation to realize a faster DevOps lifecycle.
