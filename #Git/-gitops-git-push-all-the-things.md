# GitOps — Git Push All the Things

_Captured: 2018-08-30 at 09:52 from [dzone.com](https://dzone.com/articles/gitops-git-push-all-the-things?edition=387235&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-29)_

[Download the blueprint](https://dzone.com/go?i=228233&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) that can take a company of any maturity level all the way up to enterprise-scale continuous delivery using a combination of Automic Release Automation, Automic's 20+ years of business automation experience, and the proven tools and practices the company is already leveraging.

In today's competitive environment you need to deliver features quickly without compromising on quality. But it can be difficult for most organizations to keep up and balance current release management practices with traditional operations procedures. And now with developers taking an end-to-end "you build, you own it" approach to development processes, they need tools and methods they know best in order to quickly adapt.

At the most recent Continuous Lifecycle conference in London, Alexis Richardson delivered the keynote address entitled, "GitOps: Git Push All the Things" where he discussed the industry challenges, including current CI/CD trends and how all of these tools and processes are converging with operations and monitoring. In addition to this, Alexis explained how by applying GitOps best practices, developers can take control of both the development and operations pipelines using the tools with which they are most familiar.

![](https://images.contentstack.io/v3/assets/blt300387d93dabf50e/blt09c1798dc77e0eb1/5b3ccdabfda2af4e7866be6f/download)

## Three Principles of GitOps

GitOps can be summarized by these principles:

### **1\. Everything that can be described must be stored in git**

By using Git as the source of truth, it is possible to observe your cluster and compare it with the desired state. The goal is to describe everything: policies, code, configuration, and even monitored events and version control it all. Keeping everything under version control enforces convergence where changes can be reapplied if at first they didn't succeed.

### **2\. Kubectl should not be used directly**

As a general rule, it's not a good idea to deploy directly to the cluster using the command line utility `kubectl`. Many people let their CI tool drive deployment, but by doing that you're potentially giving a notoriously hackable thing access to production.

### **3\. Use a Kubernetes controller that follows an operator pattern**

With a Kubernetes controller that follows the operator pattern, your cluster always stays in sync with 'the source of truth' via its configuration files that have been checked into Git. And since the desired state of your cluster is kept in Git, it can be observed for differences against the running cluster.

This third point was expanded upon by Alexis where he described how by comparing the desired state in Git with your running cluster state, it is possible to observe differences and then alert your team on those cases when the two states are out of sync. By installing a Kubernetes operator to your cluster, not only are deployments safer from a credentials point of view, but it also allows for an effective control and feedback loop. Your team can use this data to iterate and to improve upon both product features as well as updates to your cluster's infrastructure.

> "What can be described can be both validated and automated if you describe everything and keep it in version control. This gives you a mechanism for keeping the correct description of a system in version control and using that to automate the whole system. " \- Alexis Richardson 

Watch the talk in its entirety:

[Download](https://dzone.com/go?i=228234&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) the 'Practical Blueprint to Continuous Delivery' to learn how Automic Release Automation can help you begin or continue your company's digital transformation.
