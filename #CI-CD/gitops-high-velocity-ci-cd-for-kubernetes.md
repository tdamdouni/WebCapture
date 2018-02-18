# GitOps: High-Velocity CI/CD for Kubernetes

_Captured: 2018-02-15 at 20:05 from [dzone.com](https://dzone.com/articles/gitops-high-velocity-cicd-for-kubernetes?edition=362102&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-15)_

In response to accelerated release cycles, a new set of testing capabilities is now required to deliver quality at speed. This is why there is a shake-up in the testing tools landscape--and a new leader has emerged in the just released [Gartner Magic Quadrant for Software Test Automation](https://dzone.com/go?i=265440&u=https%3A%2F%2Fwww.tricentis.com%2Fresource-assets%2Fgartner-magic-quadrant-software-test-automation%2F%3Futm_source%3DDZone_Post_Roll%26utm_medium%3DText_Ads%26utm_campaign%3DDZoneDevOps%26utm_content%3D2017GartnerMQ).

> "The world is envisioned as a repo and not as a Kubernetes installation." -Kelsey Hightower 

This blog post is a round-up of useful information for people who want to do high-velocity continuous delivery using Kubernetes and Docker. When we say "high velocity" we mean that every product team can safely ship updates many times a day -- deploy instantly, observe the results in real time, and use this feedback to roll forward or back. The goal is for product teams to use [continuous experimentation](https://blog.acolyer.org/2017/09/29/the-evolution-of-continuous-experimentation-in-software-product-development/) to improve the customer experience as fast as possible.

If you're not yet familiar with GitOps, it's an agile software lifecycle for modern applications. Learn more by reading our blog series on the topic, starting with [Gitops - Operations by Pull Request](https://www.weave.works/blog/gitops-operations-by-pull-request).

## Use Case: High-Velocity CI/CD Is Game-Changing

How can one go from a single manual deployment per week to more than thirty, zero effort deployments per day?

Meet [Qordoba](https://qordoba.com/) \- a San Francisco based team who use machine learning to deliver optimized localization for big brands that market internationally. One of their teams is using Kubernetes-based microservices as part of the Qordoba backend. By adopting the GitOps practices and tools we recommend, they radically improved their ability to shape customers' UX:

1) Estimated time needed to fix prod software bugs: ~60% less time after using Weave Cloud

2) Estimated time to respond to customer requests: ~43% less time after using Weave Cloud

3) Uptime from 99% to 100% (so far…)

Qordoba moved from 1 or 2 deployments per week to 30+ per day. The key here is that every deployment is essentially "zero cost." That means: it takes very little time, it doesn't break half-way through leaving the team unable to return the system to a good state, and all changes can be rolled back. Zero cost deployment liberates the dev team to focus on UX and business logic - which creates value - iterating as fast as they like without fear of failure costs.

## Learn More: GitOps Intro Presentation

I presented this use case at [Kubecon 2017 ](https://www.cncf.io/blog/2018/01/10/look-back-kubecon-cloudnativecon-north-america-2017-part-1/)with [William Denniss, PM for Google Cloud](https://twitter.com/WilliamDenniss).

Some background: Weaveworks have operated [production Kubernetes cloud services on AWS](https://www.weave.works/technologies/weaveworks-on-aws/) for over two years. Recently we documented some best practices for this, [calling our approach "GitOps."](https://www.weave.works/blog/gitops-operations-by-pull-request) GitOps builds on proven DevOps techniques like [CI/CD](https://en.wikipedia.org/wiki/CI/CD) and [declarative ](https://blog.gruntwork.io/why-we-use-terraform-and-not-chef-puppet-ansible-saltstack-or-cloudformation-7989dad2865c)[infrastructure as code](https://www.thoughtworks.com/insights/blog/infrastructure-code-reason-smile) to deliver a joined up and automatable lifecycle for Kubernetes applications. We launched a '[free tier' GitOps capability with Google Cloud Platform at Kubecon](https://www.weave.works/press/releases/weave-cloud-on-the-google-cloud-platform/).

If you are interested in finding out how we do this - i.e. creating a high-velocity CICD pipeline - then I recommend you check out this presentation ([video](https://www.youtube.com/watch?v=BSqE2RqctNs&list=PLj6h78yzYM2P-3-xqvmWaZbbI1sW-ulZb&index=67), [slides](https://www.slideshare.net/weaveworks/gitops-modern-best-practices-for-high-velocity-app-dev-using-cloud-native-tools)).

![](https://images.contentstack.io/v3/assets/blt300387d93dabf50e/blt129dd4a21c27e69b/5a5f1a1098fa52700b13affb/download)

Kubecon is a community event so in this presentation William and I talk about the solution pattern, the technical role of Kubernetes deployment operators, and the open source projects that make it work.

## Instant Kubernetes CI/CD With Weave Cloud

If you liked this presentation and the idea of GitOps, then you might like to try it out. The quickest way to set it up is [via our Weave Cloud offering on Google.](https://go.weave.works/gcp)

This gets you:

  1. A Kubernetes pipeline set up in minutes
  2. One-click app deployment (of course: manual staging if needed)
  3. Full observability, dashboards & alerts

[Weave Cloud](https://www.weave.works/product/cloud/) is easily connected your Git repository and to any CI. This sets up a Kubernetes cluster for CICD so that you can benefit from continuous and high-velocity delivery like Qordoba above. On Google cloud, your GKE cluster is easily connected to Google's container builder and repo. But note: Weave Cloud works with any cluster, any network, any CI, any Git repo -- we don't force you down a path you may not like.

From this base, you can update and rollback applications via Git PRs or CLI or GUI. Finally, we provide integrated 'full stack' monitoring and management to complete the operational circle. Weave's integrated approach means that a developer can observe deployments as they happen and hence measure and react to the impact of a change. An example UI is shown below.

## ![](https://images.contentstack.io/v3/assets/blt300387d93dabf50e/blt24ae8eb76d34fb9f/5a5e93a9fea115660bfd33f0/download)

## Open Source GitOps

Our cloud service is a convenient and satisfying way to do GitOps for Kubernetes. But what if you are a developer who wants to set up and understand your own open source pipeline? Read more below to learn about some GitOps approaches you can take.

### Approach 1 - Use the Weave Flux Deployment Operator

We recommend that you use the operator pattern to listen for and orchestrate service deployments to your Kubernetes cluster. This approach is described by William Denniss in slides 15-21 of our Kubecon presentation ([video](https://www.youtube.com/watch?v=BSqE2RqctNs&list=PLj6h78yzYM2P-3-xqvmWaZbbI1sW-ulZb&index=67), [slides](https://www.slideshare.net/weaveworks/gitops-modern-best-practices-for-high-velocity-app-dev-using-cloud-native-tools)). Using the operator, an agent can act on behalf of the cluster to listen to events relating to custom resource changes and apply them consistently. In other words, the operator performs reconciliation between Git and the cluster.

The operator is implemented by [Weave Flux, an open source project](https://github.com/weaveworks/flux) that grew out of our many painful attempts to simplify our own microservices deployments to Kubernetes for our SaaS, Weave Cloud. Read more in [this blog post. "The GitOps Pipeline" ](https://www.weave.works/blog/the-gitops-pipeline)which sets out the benefits of orchestrating deployment rather than hand-coding it via CI plus scripts ("CI ops").

Flux is used in our [Weave Cloud](https://cloud.weave.works/) service. We encourage you to try it there or set it up yourself. We welcome external OSS contributors and companies interested in Flux. Many CI and deployment tools would benefit from a deployment operator.

### Approach 2 - GitOps Fundamentals the Kelsey Way

Kelsey Hightower has a remarkable habit of delivering great presentations that contain simple developer-first storylines and solutions. His keynote at Kubecon is no exception ([video](https://www.youtube.com/watch?v=07jq-5VbBVQ)).

Kelsey's talk is about continuous delivery using Github and Google Cloud and starts from the idea that "kubectl is the new SSH …. if you are using kubectl to deploy from your laptop to production, you're missing a few steps…". He then provides a demo which lays out the steps from Git through CI and staging, to production and observability dashboards. He makes the steps visible and explicit and I recommend [watching the video of his talk](https://www.youtube.com/watch?v=07jq-5VbBVQhttps://www.youtube.com/watch?v=07jq-5VbBVQ) to follow them.

Kelsey's analysis is founded on two premises:

  1. Kubernetes Deployment is not fully solved. He says: "How many people have end-to-end continuous delivery pipelines?" … Once you get to Kkubernetes, this is the next holy grail that you have to do ... this is where you should be focussing your time, big time"
  2. Developers want to drive changes through Git, and observe the results. He says: "Ideally if I make a code change, all I want is a URL to tell me where it's running….You get bonus points if you can give me metrics to tell me how well it's running…. If you give people visibility, they will stop asking for tools like kubectl to do their job, because now they can actually observe what's happening in the cluster"

This is substantially the same argument we have made in our [pitch for GitOps](https://www.weave.works/blog/devops-the-next-evolution-gitops). The key idea is that Git is the source of truth for the desired state of everything in your stack -- cluster, configuration, applications, tooling -- using declarative infrastructure as code. Please read our first blog post "[operations by pull request](https://www.weave.works/blog/gitops-operations-by-pull-request)" for more details.

## Choose Your GitOps Adventure

In this post, we have offered three approaches to trying out high-velocity CICD.

  1. An out-of-the-box service that provides a default CICD pipeline from Git to GKE clusters, using Weave Cloud, and includes monitoring, observability, audit, and features to support resilience and scale. This also works with other Kubernetes providers and your own CI.
  2. An introduction to Weave Flux, a standalone and open source deployment operator that is used in (1), and can run wherever you have a Kubernetes cluster.
  3. Kelsey's demo of how you can set up your own simple GitHub-to-Google pipeline

All three of these approaches are 100% consistent with each other. Let's compare them.

The [Weave Cloud service](https://go.weave.works/gcp) is the most integrated in that it sets up the GitOps pipeline for you and includes substantial support for [GitOps observability which is an important matter in its own right](https://www.weave.works/blog/gitops-part-3-observability). To borrow another quote from Kelsey's talk - we want "to give people visibility. One way to do that is to give people a curated dashboard that shows them what's actually happening."

The Weave Flux open source operator is focussed only on the "CD" part of CICD. By using Flux it means your release workflows can be made repeatable and manageable at scale and is a lot easier than using `kubectl` or by bolting scripts onto a CI tool. Flux is a coordination and notification agent that "speaks native Kubernetes" so that artefact changes such as code, config files, containers, tags, etc may be sync'd with cluster changes for any Kubernetes objects. You also get policies like "rollback," "automatic," and "manual" deployment (with more to come, e.g. blue/green and canary deployments).

Kelsey's approach is essentially a further decomposition into smaller parts. He provides an integration example from Git to CI to GKE, but does not provide a programmatic agent like the Flux operator. It would be perfectly reasonable to combine Kelsey's approach with Flux. Indeed [our Kubecon presentation](https://www.slideshare.net/weaveworks/gitops-modern-best-practices-for-high-velocity-app-dev-using-cloud-native-tools) shows such an integration on slide 21:

![](https://images.contentstack.io/v3/assets/blt300387d93dabf50e/blt2dd1055a93cc0429/5a5e93defea115660bfd33f6/download)

Note also that Kelsey recommends using a curated dashboard--Grafana in his demo. We agree that this is a good idea and supply such tooling in our cloud service, along with Slack integration too.

## What About Secrets?

This is the most frequently asked question about GitOps so far.

The good news is that our friends at Bitnami created a [Sealed Secrets open source project](https://github.com/bitnami/sealed-secrets) which specifically addresses a GitOps workflow. Sealed Secrets is a Kubernetes Custom Resource Definition Controller which allows you to store even sensitive information (aka secrets) in Git, which previously has not been an option. See also [Building Serverless Application Pipelines](https://www.youtube.com/watch?v=8P-aXKylCVs), presented by Bitnami's Sebastien Goasguen at Kubecon.

In addition, you can [use Weave Cloud's Deploy feature in conjunction with Sealed Secrets](https://engineering.bitnami.com/articles/secure-gitops.html) to create a continuous deployment pipeline where all operations are git based and where the desired state of your apps is declared in your git repos including your secrets.

## What About Helm?

[Helm charts](https://codeengineered.com/blog/2018/helm-review-2017/) are a great way to package potentially complex Kubernetes applications for atomic deployment. To find out more about Helm I recommend this [cool Kubecon talk by Vic Iglesias](https://www.youtube.com/watch?v=WugC_mbbiWU).

We are working on a way to treat Helm charts as first-class objects in a GitOps workflow. This is a very exciting idea: it combines the benefits of Helm, namely 'chart' encapsulation and templating, with the benefits of GitOps, including a version-controlled deployment history that helps recreate the cluster when it goes down; the automation of cluster state updates to reflect updates of Charts and their customizations as well as the automation of cluster state updates to reflect container image rollouts. And more :)

## How Can I Get Involved?

If any of the above is exciting to you, please get in touch. There is lots you can help with. Other areas of work include advanced policies such as blue/green and canaries. Tools like Istio encourage control of routing configuration at runtime, eg. updating a % weighting on traffic flow. How can GitOps do this? Traditional Infra-as-code suggests deployment artefacts are immutable, and canaries represent mutable configuration. By the same token, in the future, we hope that many software packages will be offered as Kubernetes add-ons - such as [Istio](https://www.weave.works/blog/istio-weave-cloud/), [OpenFaaS](https://www.weave.works/blog/colorisebot-openfaas-and-weave-cloud), and [Kubeflow](https://www.weave.works/blog/kubeflow-and-weave-cloud). How can we make these GitOps-aware out of the box?

## Further Reading

[Read our latest whitepaper](https://go.weave.works/CICD-whitepaper?LSD=blog), "**Making the Leap from Continuous Integration to Continuous Delivery**" which details the hurdles that DevOps teams must clear in order to move from CI to CD and the best practices for making the difficult leap. It is designed as a resource for DevOps practitioners who want to take full advantage of the efficiencies and operational advantages that CD enables, yet struggle to overcome conceptual, cultural and technological challenges.

Recently published [Gartner Magic Quadrant Report for Software Test Automation ](https://dzone.com/go?i=265436&u=https%3A%2F%2Fwww.tricentis.com%2Fresource-assets%2Fgartner-magic-quadrant-software-test-automation%2F%3Futm_source%3DDZone_Pre_Roll%26utm_medium%3DText_Ads%26utm_campaign%3DDZoneDevOps%26utm_content%3D2017GartnerMQ)provides an objective benchmark of all test automation solutions based on industry surveys, customer inquiries, product evaluations, and more.
