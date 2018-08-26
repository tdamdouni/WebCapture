# What Is GitOps, Really?

_Captured: 2018-08-24 at 16:44 from [dzone.com](https://dzone.com/articles/what-is-gitops-really?edition=385414&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-08-24)_

Easily enforce open source policies in real time and reduce MTTRs from six weeks to six seconds with the Sonatype Nexus Platform. See for yourself - [Free Vulnerability Scanner.](https://dzone.com/go?i=290455&u=https%3A%2F%2Fwww.sonatype.com%2Fsoftware-bill-of-materials%3Futm_campaign%3Ddzone%252520-%252520AHC%26utm_source%3DDZone%252520-%252520AHC%2525202018%26utm_medium%3DDZone%252520-%252520AHC%2525202018)

A year ago, we published an introduction to [GitOps - Operations by Pull Request](https://www.weave.works/blog/gitops-operations-by-pull-request). This post described how Weaveworks ran a complete Kubernetes-based SaaS and developed a set of prescriptive best practices for cloud-native deployment, management, and monitoring.

The post was popular. Other people talked about GitOps and published new tools for [git push](https://github.com/hasura/gitkube), [development](https://dzone.com/articles/weaveworks-gitops-developer-toolkit-part-one-skaff), [secrets](https://www.weave.works/blog/storing-secure-sealed-secrets-using-gitops), [functions](https://blog.alexellis.io/introducing-openfaas-cloud/), [continuous integration](https://jenkins.io/blog/2018/03/19/introducing-jenkins-x/), and more. Our website grew, with [many more posts and GitOps use cases](https://www.weave.works/blog/category/gitops/). But people still had questions. How is this different from traditional [infrastructure as code](https://puppet.com/blog/a-deployment-pipeline-for-infrastructure-a-devops-case-study-at-nbn) and [continuous delivery](https://twitter.com/jezhumble/status/1002596116230221824)? Do I have to use Kubernetes? etc.

We soon realized that we needed a new jumping off point, with

  1. More examples and stories
  2. A concise definition of GitOps
  3. A comparison with traditional continuous delivery

This blog provides that. Read on for an updated introduction to GitOps, CI/CD, and Developer Experience. We focus mainly on Kubernetes, although the model may be generalized.

## A Story of GitOps

Imagine Alice. She runs a business, "Family Insurance," that sells health, travel, car, and property insurance packages to parents who are too busy to figure out the details by themselves. The business began as a side project when Alice was working as a data scientist in a bank and she realized she could use advanced data algorithms to analyze and assemble family packages more efficiently than by hand. Some investors funded the project and now the business turns over $20M per year and is growing fast with 180 staff in a variety of roles. Among those is a technology team that builds and operates the website, database and customer analytics. This team has 60 staff and is led by Alice's CTO, Bob.

Bob's team run their production systems in the cloud. Their main applications run on GKE -- using Kubernetes on Google cloud -- and they use several data and analytics tools as well.

Family Insurance hadn't planned to use containers but got caught up in the excitement around Docker. They soon found that using GKE made it easy to set up clusters for testing new features. They added Jenkins to provide a CI solution and use Quay for the container registry. Then they wrote some Jenkins scripts that pushed new containers and config to GKE.

Today though, Alice and Bob are getting frustrated with the team's velocity, and how it affects the pace of their business. Introducing containers didn't seem to improve velocity as much as the team hoped. Sometimes, deployments break and it's not clear that a code change was responsible. Config changes are also hard to track. Often they have to create a new cluster, and re-deploy their apps, as it's the easiest way to undo the kind of mess the system turns into. Alice is worried this will get worse as the app grows, and there is a new ML project looming on the horizon. Bob feels that he has automated a lot of manual processes -- so why is the pipeline still brittle, requires manual intervention and unscalable?

Then they find out about GitOps and it enables them to move forward -- faster.

Alice and Bob's team have spent years hearing about Git-based workflows, DevOps, and infrastructure as code. It's not super new. But GitOps brings a set of opinionated and prescriptive best practices about applying these ideas in the context of Kubernetes. There are [quite a few people and vendors talking about it](https://twitter.com/search?q=gitops&src=typd), including on [Weaveworks' blog](https://www.weave.works/blog/gitops-high-velocity-cicd-for-kubernetes).

The Family Insurance team adopt GitOps. Now they have an automated operating model that works for Kubernetes and combines "speed" with "stability" because they

  * Find that the team gets more than 2x the work done and nobody is distracted
  * Stop maintaining scripts. Instead: they can focus on new features and advance their engineering practices, e.g. implement canary deployments and improve testing.
  * Have a deployment process that rarely breaks
  * Recover deployments from partial failures correctly without manual intervention
  * Gain greater confidence in their delivery systems. Alice and Bob now find it easy to split up the team into microservices teams all working in parallel
  * Execute 30-50 changes per day or more with each team, and try out new techniques
  * Onboard new developers quickly, who can deploy code to production ("by pull request") within hours
  * Easily pass SOC2 compliance

## What Just Happened?

GitOps is two things:

  1. An operating model for Kubernetes and cloud-native. It provides a set of best practices to join up deployment, management and monitoring for containerized clusters and applications. An elegant "[1 slide" definition](https://twitter.com/vitorsilva/status/999978906903080961) from [Luis Faceira](https://2018.agilept.org/speaker_luis_faceira.html) is shown below.
![](https://images.contentstack.io/v3/assets/blt300387d93dabf50e/blt7165a5438d93ba5d/5b7af80c22d8d14d0bcdbc06/download)

  

  2. A path towards a developer-centric experience for managing applications. We're applying the Git workflow to operations, as well as development. Note that this is not just about Git push, it's about how we set up the entire CI/CD toolchain and UI/UX.

### A Note on Git

If you are not familiar with version control systems and Git-based development workflow, we highly recommend diving in. Working with feature branches and pull requests can seem like black magic at first, but it is worth the effort. Here is a [good article to get you started.](https://codeburst.io/trunk-based-development-vs-git-flow-a0212a6cae64)

## How Kubernetes Works

In our story, Alice and Bob came to GitOps after using Kubernetes. Indeed, GitOps has a strong affinity with Kubernetes -- it is an operating model for Kubernetes-based infrastructure and applications.

### What Does Kubernetes Give Users?

Here are some key properties:

  1. You can describe everything in the Kubernetes model as a declaration
  2. The Kubernetes API server accepts a declaration as an input, and then continually tries to drive the cluster to the state described in the declaration
  3. The declarations are adequate to describe and manage a broad class of workloads, or "applications"
  4. Changes to the application and cluster are then due to either 
    1. Changes to container images, or
    2. Changes to the declarative specification
    3. Errors in the environment, eg a container crashes

### Kubernetes' Excellent Convergence Properties

If a group of configuration updates is made by a human operator, the Kubernetes orchestrator will apply changes to the cluster until its state has _converged to the updated configuration_. This model works for any Kubernetes resource and is extensible using Kubernetes Custom Resource Definitions (CRDs). Therefore Kubernetes deployments have the following excellent properties:

  * **Automation:** Kubernetes updates provide a mechanism for automating the process of applying a set of changes correctly and in a timely manner.
  * **Convergence:** Kubernetes will keep trying to update until success.
  * **Idempotence:** multiple applications of convergence have the same outcome.
  * **Determinism:** assuming adequate resources, the updated cluster state depends only on the desired state.

## How GitOps Works

We've learned enough about Kubernetes to explain GitOps.

Let's go back to Alice and Bob's microservices teams at Family Insurance. What are some of the workflows that they want to carry out? Have a look at the table below. If there are parts that seem new or strange, please suspend disbelief and bear with us. This is just an example workflow using Jenkins. There are many other workflows that use alternative tools.

What we can see is that every update ends up with changes to the config files and Git repos. These changes in Git then result in the "GitOps operator" updating the cluster.

![Image title](https://dzone.com/storage/temp/10042343-screen-shot-2018-08-21-at-95940-am.png)

## A Concise Description of GitOps

  1. Describe the desired state of the whole system using a declarative specification for each environment. (In our story, Bob's team owns the whole system config in Git.) 
    1. A git repo is the single source of truth for the desired state of the whole system.
    2. All changes to the desired state are Git commits.
    3. All specified properties of the cluster are also observable in the cluster so that we can detect if the desired and observed states are the same (converged) or different (diverged).
  2. When the desired and observed states are not the same then: 
    1. There is a convergence mechanism to bring the desired and observed states in sync both eventually, and autonomically. Within the cluster, this is Kubernetes.
    2. This is triggered immediately with a "change committed"alert.
    3. After a configurable interval, an alert "diff" may also be sent if the states are divergent
  3. Hence all Git commits cause verifiable and idempotent updates in the cluster.
  4. Convergence is eventual and indicated by: 
    1. No more "diff" alerts during a defined time interval
    2. A "converged" alert (eg webhook, Git writeback event)

### What Is Divergence?

To repeat: _All specified properties of the cluster are also observable in the cluster._

Some examples of divergence:

  * A change in a configuration file, due to a merged update in Git
  * A change in a configuration file, due to the GUI effecting a commit to Git
  * Multiple changes in the desired state due to a merged PR to Git followed by a container image build and subsequent config updates
  * The observed state changes in the cluster due to an error, resource conflicts causing poor behavior, or just random "drift" from the original state

### What Is the Convergence Mechanism?

Some examples:

  * For containers and clusters, the convergence mechanism is provided by Kubernetes.
  * The same mechanism can be used to manage Kubernetes-based applications and frameworks (eg Istio, Kubeflow).
  * The mechanism to manage the workflow between Kubernetes, the image repos and Git is provided by the [Weave Flux GitOps operator](https://github.com/weaveworks/flux) that is a part of [Weave Cloud](https://cloud.weave.works/).
  * For the underlying machines, the convergence mechanism should be declarative and autonomic. In our experience, [Terraform](https://blog.gruntwork.io/why-we-use-terraform-and-not-chef-puppet-ansible-saltstack-or-cloudformation-7989dad2865c) is the closest to this but does require human oversight. In this sense, GitOps extends the tradition of Infrastructure as Code.

GitOps combines Git with Kubernetes' excellent convergence properties to provide a model of operations.

GitOps lets us say: _only systems that can be described and observed can be automated and controlled._

### GitOps Is for the Whole Cloud Native Stack -- Terraform and More

GitOps is not only about Kubernetes. In GitOps we want the whole system to be managed declaratively and using convergence. By a "whole system," we mean a collection of environments running Kubernetes, e.g. "dev cluster 1," "production." Each environment includes machines, clusters, applications, as well as interfaces to external services eg data, monitoring.

Notice how important Terraform is for the bootstrapping problem here. Kubernetes has to start somewhere, and using Terraform means that we can apply the same GitOps workflows to create a control plane that underpins Kubernetes and applications. This is a helpful best practice.

Applying GitOps concepts to the layers above Kubernetes is an exciting area of active development. So far we have seen GitOps type solutions for Istio, Helm, Ksonnet, OpenFaaS, and Kubeflow, as well as Pulumi, who are re-inventing the app dev layer for cloud-native.

## Kubernetes CI/CD -- Comparing GitOps to Other Approaches

We said GitOps is two things:

  1. An operating model for Kubernetes and cloud-native, described above; and
  2. A path towards a developer-centric experience for managing applications.

For many people, GitOps is all about the Git push workflow. We like this, too! But there is more to it; let's now look at CI/CD pipelines.

### GitOps Provides Continuous Deployment for Kubernetes

GitOps provides a mechanism for continuous deployment that removes any need for standalone "deployment management systems". Kubernetes does the work for you.

  * A management update to the application requires an update in Git. This is a transactional update to the desired state. "Deployment" is then enacted within the cluster by Kubernetes itself based on the updated description.
  * Because of how Kubernetes works, these updates are convergent. This provides a mechanism for continuous deployment in which all updates are atomic.
  * Note: [Weave Cloud](https://cloud.weave.works/) provides a GitOps operator that integrates between Kubernetes and Git to enable CD by reconciling desired and cluster state.

### No kubectl, No Scripts

You should avoid using Kubectl to update the cluster and especially avoid using scripts to group kubectl commands. Instead, with a GitOps pipeline in place a user can update their Kubernetes cluster via Git.

Benefits include:

  1. **Correctness.** A group of updates may be applied, converged and finally validated, which gets us closer to the goal of atomic deployment. By contrast, using scripts provides no guarantee of convergence. We say more about this below.
  2. **Security.**[To quote Kelsey Hightower](https://twitter.com/kelseyhightower/status/939003832805179392?lang=en), "Limit the scope of access to a Kubernetes cluster to automation tools and cluster administrators who may have to debug it or keep it running." See also my [blog post on Security and Compliance](https://www.weave.works/blog/gitops-compliance-and-secure-cicd) as well as this recent use case of [Homebrew being hacked via credentials in a careless Jenkins script](https://medium.com/@vesirin/how-i-gained-commit-access-to-homebrew-in-30-minutes-2ae314df03ab).
  3. **Developer Experience.** Kubectl exposes the machinery of the Kubernetes object model, which is quite complex. Ideally, users should interact with the system at a higher level of abstraction. Again, I shall defer to Kelsey here - [please see this summary.](http://superuser.openstack.org/articles/kubernetes-boring/)

## The Difference Between CI and CD

GitOps improves on existing CI/CD models.

The modern CI server is an orchestration tool. Specifically, it is a tool for _orchestrating CI pipelines_. These include build, test, merge to trunk, etc. CI servers automate management of complex multi-step pipelines. A common temptation is to script a set of Kubernetes updates and execute that script as a pipeline step to "push" changes to the cluster. Indeed many people do this. However, it is sub-optimal and we shall now talk about why.

CI should be used to merge updates to trunk, and the Kubernetes cluster should update itself to manage CD "internally" based on those updates. We call this [the "pull" model for CD](https://www.weave.works/blog/gitops-compliance-and-secure-cicd) in contrast to CI "push." CD is part of _runtime orchestration_.

### Why CI Servers Should Not Do CD Using Direct Updates to Kubernetes

_Don't use a CI server to orchestrate direct updates to Kubernetes as a set of CI jobs. This is an [anti-pattern as set out ](https://www.weave.works/blog/kubernetes-anti-patterns-let-s-do-gitops-not-ciops)in this blog post._

Let's go back to Alice and Bob. What kind of problems did they encounter? Bob's CI server is applying changes to the cluster, but if it fails, then Bob doesn't know what state the cluster is in, or is supposed to be in, or how to rectify it. This is also true if it succeeds.

Let's assume that Bob's team built a new image and then patched their deployments to deploy the image, all from a CI pipeline. If the image builds OK, but the pipeline fails, the team is left to figure out:

  * Did the update deploy or not?
  * Do we trigger a new build? Will that result in side-effects that we don't want to do again -- and with the potential of having two builds of the same immutable image hanging around
  * Do we wait for another update before triggering the build?
  * Which bit failed? What steps need to be replayed (and which steps are safe to replay).

Using Git-based workflows doesn't guarantee that Bob's team will not encounter these problems. They could still fail to push a commit, or move a tag, or whatever; but, it's much closer to being a clear pass-or-fail.

In summary, the reason CI servers should not do CD is:

  * Update scripts are not always deterministic and it's easy to make mistakes.
  * CI servers do not converge to a declarative model of the cluster, they fail out.
  * Idempotency guarantees are hard. Users need to understand deep system semantics.
  * Recovery from partial failure is harder.

_NOTE on Helm: If you want to use Helm, we recommend combining it with a GitOps operator, e.g. [Flux-Helm](https://www.weave.works/blog/managing-helm-releases-the-gitops-way). This will help with convergence. Helm itself is not deterministic or atomic._

## GitOps Is the Best Way to Do Continuous Delivery for Kubernetes

Alice and Bob's team adopt GitOps and find that it is much easier to deliver their products, at high velocity and without losing stability. Let's finish this blog post with some illustrations of what their new set-up looks like. Note that we are talking below about applications and services primarily, but you can also use GitOps to manage the whole platform.

### Operating Model for Kubernetes

Please review the following diagram. This shows Git and the container image repository as shared resources between two orchestrated lifecycles:

  * A continuous integration pipeline that reads and writes files to Git and can update the container image repository
  * A GitOps runtime pipeline that combines deployment with management and observability, which reads and writes files to Git and can load container images
![](https://images.contentstack.io/v3/assets/blt300387d93dabf50e/bltccdc2969d11fa365/5b7afd0d1739fa520bbbb0bd/download)

## Key Takeaways

  1. **Separation of Concerns:** Note that the two pipelines can only communicate by updating Git or the image repo. In other words, there is a firewall between CI and runtime operations. We call this the immutability firewall because all updates to the repos create a new version. See also [slides 72-87 of this presentation](https://www.slideshare.net/weaveworks/continuous-lifecycle-london-2018-event-keynote-97418556) for more info on this topic.
  2. **Use any CI and Git server:** GitOps works with any of these. Please keep on using your favorite CI servers, Git, image repos, and test kits! Almost all the other Continuous Delivery tools in the market want you to use their own CI, or Git server, or image repo. That can be a blocking factor in the adoption of cloud native. With GitOps, you can keep using your existing tools.
  3. **Events as an integration tool:** Whenever Git is updated, the runtime is notified by Weave Flux (or Weave Cloud operator). Whenever Kubernetes accepts a set of changes, then Git is updated. This provides a simple integration model for creating workflows for GitOps, as illustrated below.
![](https://images.contentstack.io/v3/assets/blt300387d93dabf50e/bltd5fe58e6b6d4fbf4/5b7afdd9a3326f570bb87474/download)

## To Conclude

GitOps provides strong update guarantees which should be required of any modern deployment of "CI/CD" tool:

This is important because it provides an operating model for developers in cloud-native.

  * Traditional systems management and monitoring tools are associated with operations teams working from a runbook associated with a specific deployment.
  * In cloud-native systems management, observability tooling is the best way that a development team can measure the effects of deployments fast enough to react to them.

Imagine having many clusters deployed across many clouds, and many services each with their own teams and deployment plans. GitOps provides a scale-invariant model for managing all this.

To find out more, you can:

Automate open source governance at scale across the entire software supply chain with the Nexus Platform. [Learn more.](https://dzone.com/go?i=290456&u=https%3A%2F%2Fwww.sonatype.com%2Fwp-enforce-open-source-policies-with-confidence)
