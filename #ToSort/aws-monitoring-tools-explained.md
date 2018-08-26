# AWS Monitoring Tools Explained

_Captured: 2018-03-22 at 19:26 from [dzone.com](https://dzone.com/articles/aws-monitoring-tools-explained?edition=368219&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-22)_

Create a continuous deployment pipeline with open source tools. [Watch the screencast.](https://dzone.com/go?i=272426&u=https%3A%2F%2Fwww.fastly.com%2Flc%2Fci-cd-with-terraform%2F%3Futm_medium%3Ddisplay%26utm_source%3Ddzone.com%26utm_campaign%3DFY18Q1_GatedContent_CI%2FCDTerraform%26utm_content%3DDzone_BumperTextLink)

![](https://www.appneta.com/blog/wp-content/uploads/2018/03/AWS-monitoring-tools-explained.jpg)

Managing security and performance in the cloud is a tradeoff. On the one hand, your traditional applications will certainly break--they'll be unable to monitor the data flaws that occur in the cloud, as there's no analogue in a traditional data center. On the other hand, you'll have undreamed-of visibility--something that no traditional data center can match. This visibility is a powerful tool--but only if it's correctly taken advantage of. Here's how to do that.

## **AWS and Other Public Clouds Move Fast**

When you're using the cloud, your management plane gives you the ability to see and control nearly everything that's going on inside your implementation, at a scale of detail unimaginable in an on-premises data center. The level of control is exhilarating, yet dangerous--anyone who has your login can create or destroy networks in seconds, see who's making API calls, identify where sensitive data is kept and so on.

The management plane doesn't just create a rather intense single point of failure in the cloud. It also introduces a level of velocity that's hard to keep up with. The same IP address might point to a different server from minute to minute, or it might just cease to exist.

The velocity of the cloud means that it will be difficult to keep consistent log files. In addition, you'll have logs coming in from all over the place. Every network in your cloud will produce its own log, and your cloud will contain dozens, hundreds or thousands of network connections. How do you aggregate these logs and [monitor cloud networks](https://www.appneta.com/blog/best-network-monitoring-tools-have-in-common/) for signs of incursion?

## **Narrowing Down Cloud Metrics**

Let's start with the premise that you can't monitor the entirety of a cloud network in detail and in real time. Therefore, you have to identify the metrics that are most useful for you to monitor and designate the rest as noise.

AWS contains a number of granular monitoring and security tools that will help administrators focus on the kind of security they need. This post will focus on AWS because, as we've written in the past, it's currently dominating IT use, with [over 40% market share](https://www.appneta.com/blog/aws-monitoring-tools-bridging-gap/). If you use the public cloud, you're most likely using AWS (but other public cloud platforms will have similar tools).

  * **Amazon Machine Images** will let you monitor the configuration of your cloud
  * **Amazon CloudTrail** monitors all API calls throughout your cloud
  * **Amazon CloudWatch** collects log files from various network segments and can funnel them to an on-premises SIEM

When used together, these services can drastically cut down on the number of false positives that you'll receive, while allowing administrators to automate some incident handling.

## **Tackling Cloud Security Without Lifting a Finger**

In theory, administrators want to know everything that's going on in their cloud. In practice, most security incidents are minor, and can be handled with automation that's built into AWS. Let's look at an example.

Imagine a user making an unauthorized configuration change. CloudTrail is going to see this configuration change, because the change involves making an API call. CloudTrail will log the API call, which means that the log will be collected by CloudWatch.

CloudWatch does more than collect logs--it can be configured with rules that activate under certain conditions. In this example, CloudWatch will activate as soon as it sees an API call coming from that configuration setting. When it activates, it will trigger a Lambda function.

[AWS Lambda](https://aws.amazon.com/lambda/) is part of the automation technology contained within AWS. They're extremely flexible pieces of code that will activate upon certain event triggers. In this example, the Lambda code will follow the event trigger from CloudWatch back up to the API call from CloudTrail. It will then check to see whether the API call came from an authorized user. Since it didn't, the Lambda can restore the setting. In other words, AWS can heal itself from security incidents without administrative intervention.

## **Eliminating False Positives Makes You That Much More Secure**

Where cloud security is concerned, it can be easy to drown in a sea of data. Fortunately, the very same tools that produce the data flood can also narrow it down. With the right tools and settings, you'll be able to respond to more serious security incidents with a great deal of time and information. You'll also get a better understanding of performance for users accessing workloads hosted by AWS. While AWS has some monitoring tools, you'll need a tool that can monitor the networks into and out of AWS so you can verify performance issues for yourself.

AppNeta helps administrators make that much more sense of AWS. Get critical information that goes beyond the default tools, and keep abreast of outages, application slowdowns, and spikes in usage. [Request a free trial today](http://info.appneta.com/APM-for-IT.html?Ref__c=20680) and add yet another powerful tool to your monitoring arsenal.

Leverage your CDN to optimize + secure your cloud infrastructure. [Here's how.](https://dzone.com/go?i=281421&u=https%3A%2F%2Fwww.fastly.com%2Flc%2Fedge-enforcer%3Futm_medium%3Ddisplay%26utm_source%3Ddzone.com%26utm_campaign%3DFY18Q1_GatedContent_CDN_EdgeEnforcer%26utm_content%3DDzone_BumperText)
