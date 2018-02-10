# Serverless with Fn Project on Kubernetes for Docker

_Captured: 2018-02-06 at 17:14 from [dzone.com](https://dzone.com/articles/serverless-with-fn-project-on-kubernetes-for-docke?edition=359129&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-02-06)_

## Docker for Mac

Last week I deployed [Fn Project](https://github.com/fnproject) on Kubernetes as a quick smoke test. Fn is the new serverless platform that was open sourced at Java One 2017. Running it on Kubernetes is easier than ever because [Docker directly supports Kubernetes now, as announced at the last DockerCon](https://blog.docker.com/2017/10/kubernetes-docker-platform-and-moby-project/). In the end, it just worked without any issues.

## Fn Project

Fn Project is an interesting new approach to the serverless world. It is cloud-agnostic. with Docker as the only dependency, and therefore avoids the cloud vendor lock-in. Also, developers are not bound to certain languages when using Fn. Functions are automatically placed into a Docker image without any additional effort for the developer, so they can be run anywhere by just pointing Fn to the correct image on Docker hub.

Fn ties into the world of Cloud Native Computing Foundation projects with support for Kubernetes and Prometheus as a first start and hopefully more to come.

To reproduce the steps, first make sure the latest version of Docker with Kubernetes support is installed properly and [Kubernetes is enabled](https://rominirani.com/tutorial-getting-started-with-kubernetes-with-docker-on-mac-7f58467203fd) (in my case this is 17.12.0-ce-mac45 from the edge channel).

### Prerequisites and Checks

With Kubernetes on Docker running, list the images of running Docker containers. This should show you the containers required for K8s if you enabled it in the Docker console under preferences:

Next, check if there are existing contexts. For example, I have mini tube and GKE configured as well. Make sure the * (asterisk) is set to docker-for-desktop:
    
    
    *         docker-for-desktop                           docker-for-desktop-cluster                   docker-for-desktop                           
    
    
              gke_fmproject-194414_us-west2-a_fm-cluster   gke_fmproject-194414_us-west2-a_fm-cluster   gke_fmproject-194414_us-west2-a_fm-cluster   

If it is not set correctly, you can point kubectl to the correct Kubernetes context with the following command:

Also, you can see the running nodes:

Check out the cluster, it just consists of a single node:

### Setup

To get better visibility into K8s I recommend to install the [Kubernetes Dashboard](https://github.com/kubernetes/dashboard):

The dashboard is running in the kube-system namespace. You can check this with the following command:

#### Enable Port Forwarding for the Dashboard

Enable port forwarding to port 8443 with the following command and make sure to use the correct pod name:

With a web browser connect to https://localhost:8443. When asked, allow access to the untrusted site and click on "Skip".

#### Alternative to Port Forward: Proxy

Alternatively, you could access it via the proxy service:

Then use the following URL with the browser

![](http://www.munzandmore.com/wp-content/uploads/2018/01/Screen-Shot-2018-01-17-at-16.41.38.png)

## Fn on Kubernetes

### Helm

Make sure your Kubernetes cluster is up and running and working correctly. We will use the K8s package manager [Helm](https://github.com/kubernetes/helm) to install Fn.

![](http://www.munzandmore.com/wp-content/uploads/2018/01/Screen-Shot-2018-01-17-at-16.27.02.png)

Follow the instructions to [install Helm(https://docs.helm.sh/using_helm/#installing-helm) on your system, e.g. on a Mac it can be done with brew. Helm will talk to Tiller, a deployment on the K8s cluster.

#### Init Helm and Provision Tiller

You can simply follow the instructions about installing [Fn on Kubernetes](https://medium.com/fnproject/fn-project-helm-chart-for-kubernetes-e97ded6f4f0c). I put the steps here for completeness. First, let's clone the fn-helm repo from github:

Install chart dependencies (from requirements.yaml):

Then install the chart. I chose the release name fm-release:

![Kuberbetes Services](http://www.munzandmore.com/wp-content/uploads/2018/01/Screen-Shot-2018-01-17-at-16.41.24.png)

> _Kuberbetes Services_

Then make sure to set the FN_API_URL as described in the output of the command above.

This should be it! You should see the following deployment from the K8s console.

TTry to run a function. For more details checke the Fn Helm instruction on [github](https://github.com/fnproject/fn-helm).

![](http://www.munzandmore.com/wp-content/uploads/2018/01/Screen-Shot-2018-01-17-at-16.27.58.png)

## Summary

Installing Fn on K8s with Helm should work on any Kubernetes cluster. Give it a try yourself, [code some functions](http://www.munzandmore.com/2018/aws/fn-project-on-public-clouds) and run them on Fn / Kubernetes. Feel free to check out my [Serverless slides](https://speakerdeck.com/fmunz/serverless-architectures-devoxx-2017-presentations-includes-aws-lambda-fn-project).
