# Introducing AWS Lambda

_Captured: 2018-02-25 at 18:59 from [dzone.com](https://dzone.com/articles/introducing-aws-lambda?edition=364096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-25)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

You don't need a virtual machine to run your own source code any more as AWS Lambda offers execution environments for Java, JavaScript (Node.js), C#, Go, and Python. All you need to do is to implement a function, upload your source code and configure the execution environment. Afterwards, your source code is executed within a fully-managed computing environment. Your new tool enables you to automate operations tasks within your infrastructure with ease. This is because AWS Lambda is well-integrated with all parts of AWS. We use AWS to automate our infrastructure regularly. For example, to add and remove instances to a container cluster, based on a custom algorithm, or to process and analyze log files.

![Introducing AWS Lambda](https://cloudonaut.io/images/2018/02/introducing-aws-lambda.png)

AWS Lambda offers a maintenance-free and highly-available computing environment. You no longer need to install security updates, replace failed virtual machines, or manage remote access (SSH or RDP) for administrators. On top of that, AWS Lambda isn't billed by the second but per execution. Therefore, you don't need to pay for idling resources which are waiting for work (e.g. a task triggered once a day).

AWS Lambda is a powerful tool in different scenarios: a REST API for a web or mobile application, an event-driven system to process data, or even an IoT backend. We are also big fans of using AWS Lambda to automate operational tasks within our cloud infrastructure. For example, using a Lambda function to perform periodic health checks of a website. Or to add tags to newly launched EC2 instances automatically.

But what is AWS Lambda? We'll start with a short introduction.

> This article, excerpted from chapter 7 of [Amazon Web Services in Action, Second Edition](https://www.manning.com/books/amazon-web-services-in-action-second-edition?a_bid=387245ad&a_aid=mwittig), is about adding a new tool to your toolbox. The tool we're talking about is as flexible as a Swiss army knife, and it's called AWS Lambda.
> 
> ![Amazon Web Services in Action, Second Edition](https://cloudonaut.io/images/2017/09/aws-in-action-2nd-meap.png)
> 
>   
Save 37% off [Amazon Web Services in Action, Second Edition](https://www.manning.com/books/amazon-web-services-in-action-second-edition?a_bid=387245ad&a_aid=mwittig) with code `fccwittig` at [manning.com](https://www.manning.com/books/amazon-web-services-in-action-second-edition?a_bid=387245ad&a_aid=mwittig). 

## Executing Your Code with AWS Lambda

Compute capacity is available at different layers of abstraction on AWS: virtual machines, containers, and functions. Containers offer another layer of abstraction on top of virtual machines. Unfortunately, we don't cover containers in this article. AWS Lambda provides computing power as well but in a fine-granular manner: an execution environment for small functions, not a full-blown operating system or container.

## What Is Serverless?

When reading about AWS Lambda you might have stumbled upon the term serverless already. The following quote summarizes the confusion created by a catchy and provocative phrase:

> [… ] the word serverless is a bit of a misnomer. Whether you use a computer service such as AWS Lambda to execute your code, or interact with an API, there are still servers running in the background. The difference is that these servers are hidden from you. No infrastructure exists for you to think about and there's no way to tweak the underlying operating system. Someone else takes care of the nitty-gritty details of infrastructure management, freeing your time for other things.  
_Peter Sbarski, Serverless Architectures on AWS, Manning (2017)_

We define the following the following criteria for a serverless system:

  * No need to manage and maintain virtual machines.
  * Fully managed service offering scalability and high availability.
  * Billed per request and its resource consumption.

AWS isn't the only provider offering a serverless platform. Google (Cloud Functions) and Microsoft (Azure Functions) are competing with AWS in this area, for example.

## Running Your Code on AWS Lambda

As shown in the following figure, to execute your code with AWS Lambda the following four steps are needed:

  1. Writing the source code.
  2. Uploading your code and its dependencies (e.g. libraries or modules).
  3. Creating a function determining the runtime environment and configuration.
  4. Executing the function.
![Running your code on AWS Lambda](https://cloudonaut.io/images/2018/02/lambda-intro.png)

You don't need to launch any virtual machines. AWS executes your code in a fully-managed compute environment.

Currently, AWS Lambda offers runtime environments for the following languages:

  * Java
  * JavaScript (Node.js)
  * C#
  * Go
  * Python

Next, you'll learn more about AWS Lambda by comparing its concepts with virtual machines offered by EC2.

## Comparing AWS Lambda with Virtual Machines (Amazon EC2)

What's the difference between AWS Lambda and virtual machines? First off, the granularity of virtualization. On the one hand, a virtual machine provides a full operating system which is used to run one or multiple applications. On the other hand, AWS Lambda offers an execution environment for a function, a small part of an application.

Furthermore, Amazon EC2 offers virtual machines as a service. But you're still responsible for operating these virtual machines in a secure, scalable and highly available way. Doing this generates a bunch of operating tasks resulting in substantial maintenance effort. By contrast, AWS Lambda offers a fully-managed execution environment. AWS is managing the underlying infrastructure for you and provides a production-ready infrastructure to you.

Otherwise AWS Lambda is billed per execution, not per second that a virtual machine is running. You don't need to pay for unused resource waiting for requests or tasks any longer. For example, running a script to check the health of a website every five minutes on a virtual machine costs you a minimum of USD 4. Executing the same health check with AWS Lambda is free as you don't even exceed the never-ending monthly free tier.

The following table compares AWS Lambda and virtual machines in detail.

  
AWS Lambda Amazon EC2

Granularity of virtualization
Small piece of source code aka function.
A whole operating system.

Scalability
Scales automatically. Throttling limit prevents you from creating unwanted costs accidentally and can be increased by AWS support if needed.
Auto Scaling Group allows you to scale the number of EC2 instances serving requests automatically. But configuring and monitoring the scaling activities are your responsibility.

High Availability
Fault tolerant by default. Compute infrastructure spans multiple machines and data centers.
A virtual machine isn't highly available by default. Nevertheless it's possible to setup a highly available infrastructure based on EC2 instances as well.

Maintenance effort
Almost zero. You need to configure your function.
You're responsible for maintaining all layers between the operating system of your virtual machine and the runtime environment of your application.

Deployment effort
Almost zero due to a well-defined API.
Rolling out your application among a fleet of virtual machines is a challenge requiring tools and know-how.

Pricing model
Pay per request as well as execution time and memory.
Pay for operating hours of virtual machine billed per second.

## Learn More

Do you want to learn more? Check out chapter 7 of our book [Amazon Web Services in Action, Second Edition](https://www.manning.com/books/amazon-web-services-in-action-second-edition?a_bid=387245ad&a_aid=mwittig) including two real-world examples: website health check and automatically tagging a newly launched EC2 instance with it's owner.

Also, this [slide deck](https://www.slideshare.net/ManningBooks/amazon-web-services-in-action-second-edition-the-guide-to-cloud-infrastructure-automation-with-aws) introduces the rest our our book in more detail.

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

Topics:

aws lambda ,execution ,virtual ,code ,source ,cloud ,serverless ,aws ,function
