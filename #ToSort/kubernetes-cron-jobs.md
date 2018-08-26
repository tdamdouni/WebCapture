# Kubernetes: Cron Jobs

_Captured: 2018-03-06 at 18:24 from [dzone.com](https://dzone.com/articles/kubernetes-cron-jobs?edition=366208&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-03-06)_

One of the reasons I stood up a [Kubernetes cluster on Raspberry Pis](https://chrisshort.net/my-raspberry-pi-kubernetes-cluster/) in my house was because of the savings I wanted to gain by not running high-available, redundant infrastructure in the cloud. Kubernetes provides high-availability by design. It's pretty awesome the possibilities that exist given this capability. Need a web server to constantly run? Build a container and throw it in the Kubernetes cluster. Need a service available all the time? Package it and ship it to the Kubernetes cluster.

## Legacy Systems

I have four old Raspberry Pi boxes doing various things here in the office for me. They do a single task fine, but I have over-extended one of the first-generation Raspberry Pis. I'd like to deprecate the older Raspberry Pis as they are no longer effective boxes. To do that, I need to move the workloads (like a cloud migration). One thing I have no shortage of running on these Raspberry Pi boxes are cron jobs. I have a cron for almost everything I do. Monitoring, updating web apps, detecting changes in domain name configurations, etc.

## k8s Jobs and Cron Jobs

Kubernetes has the concept of _Jobs_. To quote the official [Jobs documentation](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/#what-is-a-job), "A job creates one or more pods and ensures that a specified number of them successfully terminate." If you have a pod that needs to run until completion no matter what, a Kubernetes Job is for you. Think of Jobs as a batch processor.

[Kubernetes _Cron Jobs_](https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/) are a relatively new thing. But, I am ecstatic that this is a standard feature in modern Kubernetes clusters. This means that I can tell the cluster one time that I want a job to run at certain times. Since Cron Jobs build on top of the existing Job functionality, I know that the job will be run to completion. The job will run on one of the six nodes I have in my Kubernetes cluster. Even if a pod is destroyed mid-job, it will spin up on another node and run there. High-available cron jobs have been a beast I've tried to slay many times. This is now a solved problem and all I have to do is implement it.

The implementation of Kubernetes _Cron Jobs_ is like many other things with Kubernetes: YAML. There are a few projects to help with wrangling your YAML ( [ksonnet](https://ksonnet.io/) for example) but, that is a discussion for another article. For now, let's get a Dockerfile and Kubernetes configuration file put together.

## Use Case

I moved my newsletter, [DevOps'ish](https://devopsish.com/), off of Medium and on to [Netlify](https://www.netlify.com/) with [Hugo](http://gohugo.io/) as a static site generator. This makes for a very fast and easy to manage website. But, the one piece of functionality lost in the move is the ability to schedule posts. Netlify provides a build hook that will trigger builds when called. I can write the newsletter and set it to a date in the future. Hugo, by default, will not publish articles unless a build is completed after the specified date. Calling the build hook URL via `curl` with a cron job is a way to implement scheduled posts with Hugo on Netlify.

## Dockerfile

The Dockerfile is pretty simple. Pull from `alpine:latest`, install `curl`, and run a `curl` command. But, I don't want the build hook URL exposed in the Dockerfile. Loading the URL as a variable via a [Kubernetes Secret](https://kubernetes.io/docs/concepts/configuration/secret/) is advisable. Do this so that the artifacts have no sensitive data and so that they can be shared publicly. Here is the Dockerfile:
    
    
            && apk add --no-cache curl

### Docker Build

As my Kubernetes cluster runs on Raspberry Pi, I make sure to pull this Dockerfile down to a Raspberry Pi dev box I have and build it there:

The name is whatever you want it to be. I will likely rename this to netlify-curl or some other more appropriate name when I'm ready.

### Docker Registry

The next step is to add the image to a Docker registry. I thought about running a Docker registry in the Kubernetes cluster itself, but then I realized [Google Container Registry](https://cloud.google.com/container-registry/) (GCR) is a thing. Since I have a fair amount of stuff in Google Cloud, I decided to use GCR for simplicity and availability (also that whole "state inside Kubernetes" thing).

Heptio has a great guide titled _[Google Cloud Registry (GCR) with external Kubernetes](http://docs.heptio.com/content/private-registries/pr-gcr.html)_. If you are going to use GCR with an external Kubernetes cluster, I highly recommend reading this first. Once GCR is configured, your Kubernetes cluster is configured to use GCR, and the container is built, you have to tag it for GCR:
    
    
    docker tag devopsish-netlify-cron gcr.io/chrisshort-net/devopsish-netlify-cron

Then push the newly tagged container image to GCR:
    
    
    gcloud docker -- push gcr.io/chrisshort-net/devopsish-netlify-cron:latest

## Kubernetes Secret

As previously mentioned, the next piece will be the Kubernetes Secret. There are a lot of ways to skin the k8s secret cat. Secrets can be loaded one time via command line or by applying a configuration file. I chose the configuration file method because I will save them in 1Password then delete them. The secret file will look something like this:

The redacted url string will be the Netlify build hook URL. As this is an Opaque secret, the string will need to be base64 encoded:

Once the base64 string is added to the file, apply it:

## Cron Job Configuration

Piecing together the [Kubernetes Cron Job](https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs) configuration file is relatively easy. Schedule is a required field, and if you're familiar with cron, it will look identical to the Cron format string.

One pitfall I experienced is Kubernetes uses UTC exclusively. Make sure you take that into account when you're creating your schedule.

Here is what the Kubernetes configuration file is specifying:

  1. Create a CronJob named devopsish-netlify-cronjob
  2. Schedule it to run the first minute of every hour from 0200 to 1400 UTC on Sunday, Monday, Friday, and Saturday
  3. Pull the image from gcr.io/chrisshort-net/devopsish-netlify-cron:latest using the provided secrets for gcr
  4. Set an environment based off the url key in the secret named devopish-build-hook
  5. Run container on CronJob schedule

Apply the configuration file and you're off to the races:

## Conclusion

And voila! You have built a Docker container, deployed the image to Google Container Registry, configured the Kubernetes cluster to pull images from GCR, created a secret to store the build hook, and created the CronJob. If everything works okay, the following command should show an active cron job:

Now go celebrate your high-availability, damn near guaranteed to run every time Kubernetes Cron Job! Congratulations!

> **[Subscribe to DevOps'ish](https://chrisshort.net/newsletter/)** for updates on Kubernetes as well as other DevOps, Cloud Native, and Open Source news.
