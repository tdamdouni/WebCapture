# The Shift to Microservices and Continuous Delivery

_Captured: 2018-04-26 at 07:20 from [dzone.com](https://dzone.com/articles/the-shift-to-microservices-and-continuous-delivery?edition=376196&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=microservices%202018-04-25)_

[Download the How to Build (and Scale) with Microservices eBook](https://dzone.com/go?i=288421&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-how-to-build-scale-with-microservices%2F%3Futm_source%3Ddzone%26utm_medium%3Dsponsorship%25252520content%25252520syndication%26utm_campaign%3Dbumper%25252520text%25252520sponsorship%26utm_content%3Dhow%25252520to%25252520build%25252520and%25252520scale%25252520%26utm_term%3Ddzone%25252520bumper%25252520text%25252520sponsorship%26utm_budget%3Ddigital) and learn how microservices are rapidly emerging as the architecture of choice. Brought to you in partnership with[ AppDynamics](https://dzone.com/go?i=288421&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-how-to-build-scale-with-microservices%2F%3Futm_source%3Ddzone%26utm_medium%3Dsponsorship%25252520content%25252520syndication%26utm_campaign%3Dbumper%25252520text%25252520sponsorship%26utm_content%3Dhow%25252520to%25252520build%25252520and%25252520scale%25252520%26utm_term%3Ddzone%25252520bumper%25252520text%25252520sponsorship%26utm_budget%3Ddigital).

Do you want to know how microservices became so popular? In this blog we provide a brief history of microservices, how this architecture became the catalyst for companies adopting "continuous delivery" and "continuous processes" and how you can use Weave Cloud to help with your own transition to continuous delivery and deployments.

Specifically, we'll shed light on these topics:

  * Netflix and Microservices
  * Microservices, Docker, and Kubernetes
  * Are Microservices right for everyone?
  * What Weave Cloud Adds to Microservices and Kubernetes
  * GitOps, Weave Cloud, and Continuous Delivery

## Netflix and Microservices

With the phenomenal success of Netflix and their ability to deliver more features faster to their customers, many companies have wanted to know how Netflix leveraged technology to gain such a huge competitive advantage.

After a disastrous release with [a misplaced semicolon, Adrian Cockcroft, former Netflix Cloud Architect](https://www.slideshare.net/adriancockcroft/goto-berlin) decided to shift their entire architecture from a monolith to microservices.

![](https://lh4.googleusercontent.com/BwNWo-OBtsi7sjeYzVk0vcDjMcwmwakBo4kERL4xHlU9QfizcdMvFKhjg2rDQPOgWCF12oPRZL_TsAbqbY93sQF5eilohaUyXgDa9qCE2w4ABfOHV21I_JpQE7koSb-95OQypZE)

> _Monolith vs. Microservices architectures._

The problem with a monolithic architecture is that when new features are developed and tested, it took considerable effort to deploy those changes to production:

  * Multiple teams needed to coordinate their code changes.
  * Deploying several features all at once required a lot of upfront integration and functional testing.
  * Development teams were also restricted to using one or two languages.

The shift to microservices empowered Netflix developers to deliver new features much faster to their customers.

Microservices are defined as a loosely coupled service-oriented architecture with bounded contexts. This means that if every service has to be updated simultaneously, it's not 'loosely coupled'; and along the same lines, if you have to know too much about the surrounding services then you don't have 'bounded contexts'.

See also Martin Fowler and James Lewis original blog that discusses the definition: "[Microservices: a definition of this new architectural term](https://martinfowler.com/articles/microservices.html)".

## Microservices, Docker, and Kubernetes

Docker containers lend themselves very well to microservices. By running your microservices in separate containers, they can all be deployed independently. Containerization removes the risk of any friction or conflict between languages, libraries or frameworks. Because Docker containers are extremely portable and can operate in isolation from one another, it is very simple to create a microservices architecture with containers.

### Container Orchestration

Once you have a large number of microservices all running in Docker Containers, you need a way to manage or to orchestrate those containers so that they make sense as an application. This is where you need an orchestrator (cluster manager) like Kubernetes or Docker Swarm and many others.

It used to be that you had to make an informed choice on which orchestrator to use, but as of the beginning of last year, the orchestration wars were mostly won and Google's Kubernetes came out on top. All of the major cloud providers now support [Kubernetes with easy-to-install solutions](https://www.weave.works/technologies/kubernetes-installation-options/).

So the gist of this is that for most companies to be competitive, you have to architect your applications around microservices and run them in a Kubernetes cluster - although some companies do run Docker containers on other orchestrators as well.

### Are Microservices Right for Everyone?

Despite the popularity of microservices, moving in this direction may not be right for every organization. First, it makes more sense if your team is larger than 1-3 people--when you're too small, microservices can add unnecessary additional overhead.

Microservices are useful for when you need to scale operations and have to handle thousands of requests. They are best utilized by very large teams who are split into smaller teams working on different aspects of your application with their own set of microservices to manage.

Additionally, microservices are necessary if you need to distribute your workload across multiple clusters or data-centers. But without that need, it is not necessarily vital that an organization switch to a microservices environment.

## What Weave Cloud Adds to Microservices and Kubernetes

Even though microservices have helped make organizations scale and move faster for the reasons cited above, the complexity of managing microservices especially when running in an orchestrator in a public cloud has increased.

Weave Cloud minimizes the complexity of updating microservices running in Kubernetes by providing automatic continuous delivery, cluster visibility, and monitoring.

Infrastructure tasks that would otherwise be required if developers were to manually update microservices in Kubernetes is taken care of by Weave Cloud. And because it's a SaaS, developers spend more time producing code rather than performing Ops tasks.

> "Bring your Kubernetes cluster and just add Weave Cloud" \- Alexis Richardson, CEO Weaveworks. 

With Weave Cloud, developers can continuously add features and continuously deploy those updates to their app in real-time without having to interact directly with Kubernetes. This is not only safer from a [security point of view,](https://www.weave.works/blog/how-secure-is-your-cicd-pipeline) but it also allows multiple teams to work on different microservices without any downtime. And most importantly, the velocity of code updates and new features deployed to production is increased 2-fold, giving companies a competitive advantage.

## GitOps, Weave Cloud, and Continuous Delivery

With declarative infrastructure now being the norm and with Kubernetes' ability to perform rolling updates with zero downtime, it's possible to initiate your entire pipeline from Git. We've been calling this method of continuous delivery and cluster management - GitOps.

### **Operations by Pull Request**

GitOps is a way to do continuous delivery and deployments. It works by using Git as both the impetus of the pipeline and the source of truth for declarative infrastructure and applications. Automated delivery pipelines roll out changes to your infrastructure when changes are made to Git. But the idea goes further than that - it also uses tools to compare the actual production state with what's under source control and can also tell you when it doesn't match the real world.

### **Faster Deployments**

Our users are reporting up to 60% faster deployments with Weave Cloud. This is partially because we have removed the manual interactions with the Kubernetes cluster. Developers don't have to know anything about Kubernetes if they don't want to and they especially don't have to figure out which YAMLs edit. To make it even simpler, all of your manifests are versioned in Git by Weave Cloud.

### **More Secure Deployments**

CICD pipelines are well-known attack vectors. The problem with many of the tools on the market today, is that they extend their continuous integration tool to include continuous delivery. This is often done with a bunch of scripts spread across your dev environments. Scripts that sometimes include cluster credentials. But with Weave Cloud deployments made to your cluster are secure, since credentials and other secrets never leave the cluster.

Read more about [GitOps in our four-part blog series](https://www.weave.works/blog/category/gitops/).

### Weave Cloud Doesn't Lock You In

Weave Cloud connects to your Git repository and to any Continuous Integration (CI) tool and container repository like DockerHub, JFrog or GKR. For example, on Google Cloud, your GKE cluster is easily connected to Google's container builder and repo and [Weave Cloud with just a few clicks.](https://go.weave.works/gcp) Weave Cloud also works with any cluster or orchestrator, any network, any CI, and any Git repo -- your team can use their existing tools or the ones they are already familiar with.

This is in contrast to many of the platforms out there on the market that provide what's sometimes referred to as a "walled garden". Many of these platforms will have most of the tools you want, but they will be of varying quality and usefulness.

Weave Cloud, by contrast, gives you choice, and this allows you to take advantage of open source tools that otherwise wouldn't be available to you if you were locked in using one of the PaaS (Platform as a Service) platforms.

## Final Thoughts

Throughout this blog, we provided some context and discussion around why you need microservices and how they came about in the first place. We also showed you how with Weave Cloud, you can manage microservices and Kubernetes deployments efficiently and increase developer productivity.

[Learn how to track microservices](https://dzone.com/go?i=286452&u=https%3A%2F%2Fwww.appdynamics.com%2Fapp-iq-platform%2Fmicroservices-iq%2F%3Futm_source%3Ddzone%26utm_medium%3Dsponsorship%26utm_campaign%3Dmicroservics%252520sponsorship%26utm_content%3Dmicroservics%252520sponsorship%26utm_term%3Ddzone%252520microservics%252520sponsorship%26utm_budget%3Ddigital) deployed in elastic infrastructure such as containers or cloud where nodes scale up and down very rapidly.
