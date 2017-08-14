# Introducing Functions as a Service (FaaS)

_Captured: 2017-08-11 at 19:33 from [dzone.com](https://dzone.com/articles/introducing-functions-as-a-service-faas?edition=315394&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-11)_

[Functions as a Service (FaaS)](https://blog.alexellis.io/functions-as-a-service/) is a framework for building serverless functions on top of containers. I began this project as a proof of concept in October last year when I wanted to understand if I could run [Alexa skills](https://blog.alexellis.io/serverless-alexa-skill-mobymingle/) or Lambda functions on Docker Swarm. After some [initial success](https://github.com/alexellis/funker-dispatch), I released the first version of the code in Golang [on GitHub in December](https://github.com/alexellis/faas/commits/master?after=235da9261746748e9ae32320dbdda19d053d7407+349).

This post gives a straightforward introduction to serverless computing, then covers my top 3 features introduced in FaaS over the last 500 commits, and finishes with what's coming next and how to get involved.

![Image title](https://dzone.com/storage/temp/6205931-prom-stars.png)

From that first commit, FaaS went on to gain momentum and over 2,500 stars on GitHub along with a small [community of developers and hackers](https://github.com/alexellis/faas/blob/master/community.md), who have been giving talks at meetups, writing their own cool functions, and contributing code. The highlight for me was winning a place in [Moby's Cool Hacks keynote session](https://blog.docker.com/2017/04/dockercon-2017-mobys-cool-hack-sessions/) at Dockercon in Austin in April. The remit for entries was to push the boundaries of what Docker was designed to do.

![Image title](https://dzone.com/storage/temp/6205932-c9zvao-vyaal7ki-embed.jpg)

## What Is Serverless?

### **Architecture Is Evolving**

"Serverless" is a misnomer -- we're talking about a new architectural pattern for event-driven systems. For this reason, serverless functions are often used as connective glue between other services or in an event-driven architecture. In the days of old, we called this a service bus.

![Image title](https://dzone.com/storage/temp/6205935-evolution.png)

> _Serverless is an evolution_

### **Serverless Functions**

A serverless function is a small, discrete, and reusable chunk of code that:

  * Is short-lived
  * Is not a daemon (long-running)
  * Does not publish TCP services
  * Is not stateful
  * Makes use of your existing services or third-party resources
  * Executes in a few seconds (based on AWS Lambda's default)

We also need to make a distinction between _serverless products_ from IaaS providers and open source software projects.

On one hand, we have _serverless products_ from IaaS providers such as Lambda, Google Cloud Functions, and Azure Functions. On the other hand, we have frameworks such as FaaS, which let an orchestration platform such as Docker Swarm or Kubernetes do the heavy lifting.

![Image title](https://dzone.com/storage/temp/6205940-cloud-native.png)

> _Cloud Native -- bring your favorite cluster._

A serverless product from an IaaS vendor is completely managed so it offers a high degree of convenience and per-second/minute billing. On the flip-side, you are also very much tied into their release and support cycle. Open-source FaaS exists to promote diversity and offer choice.

### **What's the Difference With FaaS?**

FaaS builds upon industry-standard Cloud Native technology:

![Image title](https://dzone.com/storage/temp/6205961-68747470733a2f2f7062732e7477696d672e636f6d2f6d6564.jpeg)

> _The FaaS stack_

The difference with the FaaS project is that any process can become a serverless function through the [watchdog](https://github.com/alexellis/faas/tree/master/watchdog) component and a Docker container. That means three things:

  * You can run code in whatever language you want
  * For however long you need
  * Wherever you want to

> Going Serverless shouldn't have to mean re-writing your code in another programming language. Just carry on using whatever your business and team needs.

Example:

For example, `cat` or `sha512sum` can be a function without any changes, since functions communicate through stdin/stdout. Windows functions are also supported through Docker CE.

> This is the primary difference between FaaS and the other open-source serverless frameworks which depend on bespoke runtimes for each supported language.

Let's look at three of the big features that have come along since Dockercon, including [CLI](https://github.com/alexellis/faas-cli) and function templating, Kubernetes support, and asynchronous processing.

#### 1\. The New CLI

#### **Easy Deployments**

I added a [CLI](https://github.com/alexellis/faas-cli) to the FaaS project for making deploying functions easier and scriptable. Prior to this, you could use the API Gateway's UI or `curl`. The CLI allows functions to be defined in a YAML file and then be deployed to the API Gateway.

Finnian Anderson wrote a great intro to the FaaS CLI on [Practical Dev/dev.to](https://dev.to/developius/functions-as-a-service---deploying-functions-to-docker-swarm-via-a-cli)

#### **Utility Script and Brew**

There is an installation script available, and John McCabe helped the project get a recipe on `brew`.

or

#### **Templating**

Templating in the CLI is where you only need to write a handler in your chosen programming language and the CLI will use a template to bundle it into a Docker container -- with the FaaS magic handled for you.

> There are two templates provided for Python and Node.js, but you can create your own easily.

There are three actions the CLI supports:

  * `-action build`: creates Docker images locally from your templates
  * `-action push`: pushes your templates to your desired registry or the Hub.
  * `-action deploy`: deploys your FaaS functions

> If you have a single-node cluster, you don't need to push your images to deploy them.

Here's an example of the CLI configuration file in YAML:

_sample.yml_

Here is the bare minimum handler for a Python function:

This is an example that `pings` a URL over HTTP for its status code:

_./sample/url_ping/handler.py_

If you need additional `pip` modules, then also place a `requirements.txt` file alongside your handler.py file.

You'll then find a Docker image called alexellis2/faas-urlping, which you can push to DockerHub with `-action push` and deploy with `-action deploy`.

> You can find the [CLI in its own repo](https://github.com/alexellis/faas-cli).

#### 2\. Kubernetes Support

As a [Docker Captain](https://blog.docker.com/2016/09/5-minutes-docker-captains-2/), I focus primarily on learning and writing about [Docker Swarm](https://docs.docker.com/engine/swarm/), but I have always been curious about Kubernetes. I started learning how to setup [Kubernetes](https://kubernetes.io/) up on Linux and Mac and wrote [three tutorials](https://blog.alexellis.io/tag/k8s/) on it, which were well-received in the community.

#### **Architecting Kubernetes Support**

Once I had a good understanding of how to map Docker Swarm concepts over to Kubernetes, I wrote a technical prototype and managed to port all the code over in a few days. I opted to create a new microservice daemon to speak to Kubernetes rather than introducing additional dependencies to the main FaaS codebase.

FaaS proxies the calls to the new daemon via a standard RESTful interface for operations such as: Deploy, List, Delete, Invoke, and Scale.

Using this approach meant that the UI, the CLI, and auto-scaling all worked out the box without changes. The resulting microservice is being maintained in a new GitHub repository called [FaaS-netes](https://github.com/alexellis/faas-netes) and is available on DockerHub. You can set it up on your cluster in around 60 seconds.

#### **Watch a Demo of Kubernetes Support**

In this demo, I deploy FaaS to an empty cluster, then run through how to use the UI, [Prometheus](https://prometheus.io/) and trigger auto-scaling too.

#### **But Wait... Aren't There Other Frameworks That Work on Kubernetes?**

There are probably two categories of Serverless frameworks for Kubernetes -- those which rely on a highly specific runtime for each supported programming language and ones like FaaS, which let any container become a function.

FaaS has bindings to the native API of Docker Swarm and Kubernetes, meaning it uses first-class objects that you are already used to managing such as _Deployments_ and _Services_. This means there is less magic and code to decipher when you get into the nitty gritty of writing your new applications.

> A consideration when picking a framework is whether you want to contribute features or fixes. OpenWhisk, for instance, is written in Scala. Most of the others are written in Golang.

### 3\. Asynchronous Processing

One of the traits of a serverless function is that it's small and fast, typically completing synchronously within a few seconds. There are several reasons why you may want to process your function asynchronously:

  * It's an event and the caller doesn't need a result
  * It takes a long time to execute or initialize -- i.e. TensorFlow/machine learning
  * You're ingesting a large number of requests as a batch job
  * You want to apply rate limiting

I started a prototype for asynchronous processing via a distributed queue. The implementation uses the [NATS Streaming](http://nats.io/documentation/streaming/nats-streaming-intro/) project but could be extended to use Kafka or any other abstraction that looks like a queue.

![Image title](https://dzone.com/storage/temp/6205995-screenshot-2461.png)

I have a Gist available for trying the asynchronous code out:

  * [Run through the FaaS/Async Gist](https://gist.github.com/alexellis/62dad83b11890962ba49042afe258bb1)
![Image title](https://dzone.com/storage/temp/6206010-clip-1.png)

Thanks to the folks at [Packet.net](https://packet.net/) a new logo and website will be going live soon.

> Packet are automating the Internet and offer great value bare-metal infrastructure in the cloud.

### **Speaking**

I'll be speaking on [Serverless and FaaS at LinuxCon North America in September](https://www.linuxfoundation.org/announcements/session-lineup-announced-for-linux-foundation-open-source-summit-north-america). Come and meet me there, and if you can't make it, follow me on [Twitter @alexellisuk](https://twitter.com/alexellisuk/)

### **Get Started!**

Please show support for FaaS and **star** the GitHub repository and share this blog post on Twitter.

You can get started with the TestDrive over on GitHub:

I'm most excited about the growing [Kubernetes support](https://github.com/alexellis/faas-netes) and [asynchronous processing](https://github.com/alexellis/faas/issues/103). It would also be great to have someone take a look at running FaaS on top of [Azure Container Instances](https://github.com/alexellis/faas/issues/117).

### **All Contributions Are Welcome**

Whether you want to help with issues, coding features, releasing the project, scripting, tests, benchmarking, documentation, updating samples, or even blogging about it, there is something for everyone, and it all helps keep the project moving forward.

So if you have feedback, ideas, or suggestions then please post them to me [@alexellisuk](https://twitter.com/alexellisuk) or via one of the GitHub repositories.

Not sure where to start? Get inspired by the [community talks and sample functions](https://github.com/alexellis/faas/blob/master/community.md), including machine learning with TensorFlow, ASCII art, and easy integrations.
