# Kubernetes Resource Usage: How Do You Manage and Monitor It?

_Captured: 2018-02-06 at 17:16 from [dzone.com](https://dzone.com/articles/kubernetes-resource-usage-how-do-you-manage-and-mo?edition=359129&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-02-06)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

When people start looking at running containers in production at scale, they quickly realize they will need an orchestrator such as Kubernetes to efficiently schedule and orchestrate containers on the underlying shared set of physical resources. However, how do you control the resource usage of containers so that different images and projects each get their fair share of the resources? This is where things like container resource limits and resource quotas come in.

## How to Limit Container Resource Usage in Kubernetes

Within Kubernetes, containers are scheduled as pods. By default, a pod in Kubernetes will run with no limits on CPU and memory in a default namespace. This can create several problems related to contention for resources, the two main ones being:

  1. There is no control of how much resources each pod can use. Some images might be more resource heavy or have certain "minimum resource" requirements that we would like to see guaranteed.
  2. When different teams run different projects on the same cluster, there is no control how much resources each team can use.

These issues can be addressed respectively in Kubernetes in the following way:

  1. Developers can control the amount of CPU and memory resources per pod or container by setting [resource requests and limits](https://kubernetes.io/docs/concepts/configuration/manage-compute-resources-container/) in the pod configuration file.
  2. Cluster administrators can create namespaces for different teams and set [resource quota](https://v1-9.docs.kubernetes.io/docs/concepts/policy/resource-quotas/) (defined by a **ResourceQuota **object) per namespace. This limits the amount of objects that can be created in a namespace, as well as the total amount of resources that may be consumed by pods in that namespace.

In this blog post we will focus on the first aspect: how to set resource constraints on pods and containers, and equally important, how to keep track of these. In a follow up blog post, we will discuss similar aspects for resource quotas.

## Setting Container Resource Constraints

Within the pod configuration file **cpu **and **memory **are each a **resource type** for which constraints can be set at the container level. A resource type has a base unit. CPU is specified in units of cores, and memory is specified in units of bytes. Two types of constraints can be set for each resource type: **requests **and **limits**.

A **request **is the amount of that resources that the system will guarantee for the container, and Kubernetes will use this value to decide on which node to place the pod. A **limit **is the maximum amount of resources that Kubernetes will allow the container to use. In the case that request is not set for a container, it defaults to limit. If limit is not set, then if defaults to 0 (unbounded). Setting request < limits allows some oversubscription of resources as long as there is spare capacity. This is part of the intelligence built into the Kubernetes scheduler.

![](https://www.coscale.com/hs-fs/hubfs/Blog_Pictures/2018_01/kubernetes_resource_usage_requests_limits.png?t=1516799214378&width=711&height=346&name=kubernetes_resource_usage_requests_limits.png)

Below is an example of a pod configuration file with requests and limits set for CPU and memory of two containers in a pod. CPU values are specified in "millicpu" and memory in MiB.

You can now save this YAML to a file and create this pod:

`kubectl apply -f demo.yaml --namespace=demo-example`

## Analyzing Container Resource Usage

Once you have set the resource requests and limits, you also want to check how much actual resources the containers are using. This can be done via the CLI in the following way:

At the time writing this blogpost, kubernetes is missing a command in kubectl to show the resource usage in an easy way, it's an [open ticket.](https://github.com/kubernetes/kubernetes/issues/17512) Fortunately the kubernetes community is awesome and there some great clever commands we can use to give us an idea.

To see the how much of its quota each node is using we can use this command, with example output for a 3 node cluster:
    
    
    $ kubectl get nodes --no-headers | awk '{print $1}' | xargs -I {} sh -c 'echo {}; kubectl describe node {} | grep Allocated -A 5 | grep -ve Event -ve Allocated -ve percent -ve -- ; echo'
    
    
    gke-rel3170-default-pool-3459fe6a-n03g
    
    
      358m (38%) 138m (14%) 516896Ki (19%) 609056Ki (22%)
    
    
    gke-rel3170-default-pool-3459fe6a-t3b3
    
    
      460m (48%) 0 (0%) 310Mi (11%) 470Mi (17%)
    
    
    gke-rel3170-default-pool-3459fe6a-vczz
    
    
      570m (60%) 110m (11%) 430Mi (16%) 790Mi (29%)

To see the pods that use the most cpu and memory you can use the **kubectl top** command but it doesn't sort yet and is also missing the quota limits and requests per pod. You only see the current usage:
    
    
    kube-system kube-proxy-gke-rel3170-default-pool-3459fe6a 2m 12Mi
    
    
    kube-system kube-proxy-gke-rel3170-default-pool-3459fe6a 2m 12Mi
    
    
    kube-system fluentd-gcp-v2.0.9-5t9q6 8m 85Mi
    
    
    kube-system fluentd-gcp-v2.0.9-pd4s9 10m 84Mi
    
    
    kube-system kube-dns-3468831164-v2gqr 1m 26Mi
    
    
    kube-system event-exporter-v0.1.7-1642279337-180db 0m 13Mi
    
    
    kube-system kube-proxy-gke-rel3170-default-pool-3459fe6a 1m 12Mi
    
    
    kube-system l7-default-backend-3623108927-tjm9z 0m 1Mi
    
    
    kube-system kube-dns-3468831164-cln0p 1m 25Mi
    
    
    kube-system fluentd-gcp-v2.0.9-sj3rh 9m 84Mi
    
    
    kube-system kube-dns-autoscaler-244676396-00btn 0m 7Mi
    
    
    kube-system kubernetes-dashboard-1265873680-8prcm 0m 18Mi
    
    
    kube-system heapster-v1.4.3-3980146296-33tmw 0m 42Mi

Because of these limitations, but also because you want to gather and store this resource usage information on an ongoing basis, a monitoring tool comes in handy. This allows you to analyze resource usage both in real time and historically, and also lets you alert on capacity bottlenecks.

## Resource Requests and Limits in Coscale

[CoScale](https://www.coscale.com/) was built specifically for container and [Kubernetes monitoring](https://www.coscale.com/kubernetes-monitoring). It integrates with Docker, Kubernetes and other container technologies to collect container-specific metrics and events. In CoScale you can also check the container resource requests and limits.

Below is an example of a dashboard that shows per node how much resources have been reserved (in this example requests and limits defaut to the same value) and how much has actually been used. This high-level view gives you an idea how much resources in your cluster are currently reserved and used. This helps you to determine whether you need to add new nodes, or perhaps adapt the resource requests.

You can also expand the node view to see details about the individual containers and their resource requests and usage. This allows you to identify which containers are using most resources.

![](https://www.coscale.com/hs-fs/hubfs/Blog_Pictures/2018_01/container_resource_usage_and_limits.png?t=1516799214378&width=711&height=541&name=container_resource_usage_and_limits.png)

These dashboards help you to do a high level analysis, but CoScale also allows you to alert on these values to get real-time notifications, for example when CPU resource usage reaches 90% of its limits.

![](https://lh3.googleusercontent.com/DMbHMnotcq6s_5T_F6E40QF8T382KytlQilH14XTUrHWIGkHvREl07tfM1cr1AGw2pOtzjLMImF77Y9lX2lE90UzqOeuDCJbdrqiQ4yyUbT9pT-JzVprezZgjApPmM0OplZjTySu)

## Conclusion

Setting up container resource requests and limits is a first step towards effectively using resources in your Kubernetes cluster. Make sure you always set these values appropriately for your application. And after you set them, make sure you have monitoring and alerting in place to determine if you need to adapt these values or upgrade your cluster.

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)
