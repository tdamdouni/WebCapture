# Going Serverless? Compare Your FaaS Options

_Captured: 2017-12-12 at 16:54 from [dzone.com](https://dzone.com/articles/going-serverless-compare-your-faas-options?edition=342132&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202017-12-12)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

As is typical with new concepts and technologies, the absolute definition of "serverless" or FaaS (Functions as a Service) is broad and undefined. In essence, it is a concept that takes cloud computing and "convenience as a service" to the extreme, spinning up processing power when your application needs it and responding with data.

Serverless is perfect for IoT devices, microservice architectures, or any other application that needs to be efficient. In this article, I will look beyond the major players (AWS, Azure, and Google) to highlight lesser-known contenders for you to consider for your next project.

Many share similarities and features, some are container-based, some open source (requiring setup on your part), and some don't describe themselves as "serverless" but share enough conceptual similarities I included them anyway.

## Google App Engine

I haven't included the better-known [Google Cloud Functions](https://cloud.google.com/functions/) on this list, but long before "serverless" existed as a word, and even before Lambda, there was [Google's App Engine](https://cloud.google.com/appengine/).

It supports Node.js, Java, Ruby, C#, Go, Python, and PHP, adds features such as routing traffic to different versions and applications, security, and access to Google's other cloud services. I wonder if App Engine and Cloud Functions will ever merge, but for now, it's a reliable option with ten years of development and usage.

![](https://1npo9l3lml0zvr6w62acc3t1-wpengine.netdna-ssl.com/wp-content/uploads/2017/11/faas-gcp.png)

> _Google App Engine_

## Webtask

From the team behind Auth0, [Webtask](https://webtask.io/) is a free serverless platform for undemanding projects written in JavaScript.

Despite this (lack of) cost, it has a decent CLI tool and support for secrets, NPM modules, logs, cron tasks, custom domains, and a whole lot of other features. Webtask requires familiarity with the concepts of serverless, but for anyone with that knowledge looking for a service to experiment with, then it's perfect.

![](https://1npo9l3lml0zvr6w62acc3t1-wpengine.netdna-ssl.com/wp-content/uploads/2017/11/fass-webtask.png)

> _Webtask_

## Apex

Using a Node.js shim, [Apex](http://apex.run) lets you use AWS Lambda with languages that it doesn't support. As Lambda adds more language support, Apex may become less useful, but for now, it still plugs a couple of useful holes.

As an open-source project, it does leave me wondering how quick it is at supporting new features as they emerge. But currently, it supports a wide range of Lambda functionality.

## PythonAnywhere

As the name suggests, [PythonAnywhere](https://www.pythonanywhere.com) only supports Python and is aimed at the education market.

It's more of a fully featured online IDE and hosting environment than pure serverless, but it does mean that smaller internet-connected devices can access the power of Python, so it shares some similarities. And for devices that have no screen, the platform can accept code pushes from any public repository.

## Apache OpenWhisk

[Apache OpenWhisk](http://openwhisk.incubator.apache.org) is a promising open-source option for anyone who prefers complete control of their applications.

Figuring out how to get started is a little confusing, a common problem with open-source projects. I followed a Getting Started guide that took about 30 seconds before I received an error message and got stuck.

If you're less concerned about the self-hosting aspect, then IBM's cloud functions use OpenWhisk under the hood. A quick search will find you dozens of resources to help get started, but most are written by IBM employees, so they still push you down the IBM Cloud platform.

The biggest stumbling block I hit was how to use OpenWhisk without IBM Cloud. I finally hit upon [this guide from The New Stack](https://thenewstack.io/hands-guide-creating-first-serverless-application-apache-openwhisk/) that suggests using Vagrant for local testing. This caused me to dig into [the codebase for OpenWhisk](https://github.com/apache/incubator-openwhisk) and discover that while it's possible to install and run on most platforms and start accepting requests, it's complex.

!Sign up for a free Codeship Account

## IBM Cloud Functions

As [IBM Cloud Functions](https://console.bluemix.net/openwhisk/) is hosted Openwhisk, I'll focus on what the service adds on top. Openwhisk has one of the better selections of runtimes and includes languages that better represent IBM's priorities such as Swift, PHP, and Java.

Recently IBM added a composer tool that lets you combine different services programmatically. They're pushing hard to show users what pieces of their cloud puzzle fit together to meet certain use cases. One of the biggest advantages of Openwhisk is its integrated access to IBM's Watson service, plugging your small internet-connected devices into a powerful artificial intelligence.

## Spotinst

You have possibly never heard of Spotinst as a cloud provider, but it also has [a serverless offering](https://spotinst.com/products/spotinst-functions/) that supports JavaScript, Ruby, Python and Java 8 and has a reasonable [free tier](https://spotinst.com/products/spotinst-functions/pricing/).

Spotinst is pretty much a host for the [Serverless Framework](https://serverless.com/), so its documentation is a little thin, and you'll have to jump between the two.

## Weblab

Currently in private beta, their website is a little lacking in information, but [Weblab](https://weblab.io) (will) offer JavaScript-based microservice hosting. [Pricing](https://weblab.io/#pricing) is average, and more of a Heroku-style model -- based on the number of processes you have running than compute time.

## Hook.io

While it doesn't claim to be serverless, [Hook.io](http://hook.io) offers microservices and webhook hosting that are close enough to the concept for me to include here. The platform supports a large range of programming and scripting languages, and anything that has an HTTP or cURL client can request a response.

![](https://1npo9l3lml0zvr6w62acc3t1-wpengine.netdna-ssl.com/wp-content/uploads/2017/11/faas-hookio.jpg)

_Hook.io_

## Kubeless

If you are already using Kubernetes for other aspects of your infrastructure, then [Kubeless](http://kubeless.io) adds a "ThirdPartyResource" function definition that allows you to deploy small code units to your cluster without the need for building container images each time.

It supports Python, Node.js, and Ruby, and also integrates with Kafka and Prometheus, again bringing serverless concepts to preexisting infrastructures.

## OpenFaas

In a similar vein to Kubeless, [OpenFaas](https://github.com/openfaas/faas) is a framework for building serverless functions with Docker and Kubernetes.

In theory, it supports any language supported by Linux and Windows containers, has its own web UI, and leverages a lot of the scaling and metrics features of Kubernetes, Docker, and Prometheus. This involves a modicum of initial setup on your part, and as a new project, [the current documentation](https://github.com/openfaas/faas/tree/master/guide) is lacking. However, once [you're set up](https://github.com/openfaas/faas/tree/master/guide#deployment-guides-start-here), I recommend [this blog post](https://blog.alexellis.io/quickstart-openfaas-cli/) that shows you how to use the OpenFaas CLI to create and deploy functions.

![](https://1npo9l3lml0zvr6w62acc3t1-wpengine.netdna-ssl.com/wp-content/uploads/2017/11/faas-openfass.jpg)

> _OpenFaaS_

## IronFunctions

Another solution that leverages a container-based infrastructure, [IronFunctions](http://open.iron.io) is an open-source serverless framework that you can self-host or use Iron's FaaS offering.

As it runs in containers, you can use any language supported by Linux and Windows. IronFunctions supports AWS Lambda format and the ability to import existing Lambda functions, and a CLI tool for easy creation and deployment of functions.

The project is less than a year old, but with backing from a well-established cloud-native provider, it shows promise and looks well designed.

## Serverless Framework

As the name implies, [the Serverless Framework](https://serverless.com/framework/docs/) is not so much a platform but a framework that helps you create serverless applications on top of other platforms.

The intention is that you can write your code once and deploy to whichever platform you prefer. In reality, the experience varies depending on the languages and features each platform supports. You might it find it best to start developing from a "minimum shared feature set," separating out platform-specific features into supplemental functions.

Phew. That's a lot of options to consider, and I'm sure I missed one or two. I'd love to hear which you've tried, your experiences, and recommendations.

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)
