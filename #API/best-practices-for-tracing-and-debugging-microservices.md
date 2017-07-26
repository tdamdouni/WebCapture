# Best Practices for Tracing and Debugging Microservices

_Captured: 2017-04-20 at 13:50 from [dzone.com](https://dzone.com/articles/best-practices-for-tracing-and-debugging-microserv?oid=twitter&utm_content=bufferb57d3&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).

In this article, I'll be talking about some techniques for debugging and fault-finding in microservices architectures.

One of the issues we've had for a long time -- in fact, ever since distributed computing became a thing -- has to do with debugging issues with a single business process that is run across multiple machines at different times. When software was monolithic, we always had access to the full execution stack trace and we knew the machine that we were running on. When we encountered an error, we could write all the information we needed to a log and later inspect it to see what went wrong.

When applications started running over small farms, we no longer knew exactly which machine we were running on. A look at the whole farm was a highly inefficient but often taken route. With the advent of cloud computing, where compute instances are ephemeral, we cannot rely on machine logs to be there when we come to analyzing log data. We need to get serious about how we manage our logging so that we have a decent chance of tracking down and fixing issues.

Here are my best practices for tracing and debugging your microservices.

## 1\. Externalize and Centralize the Storage of Your Logs

The first thing you need to do is to treat the data integrity of your logs seriously. You cannot rely on retrieving information from a physical machine at a later date, especially in an auto-scaled virtual environment. You wouldn't allow a design where important customer data was stored on a single virtual machine with no backup copy, so you shouldn't do this for logs.

There's no absolute right answer to how you store your log information whether it's in a database, on disk, or in an [S3 bucket](https://aws.amazon.com/s3/), but you need to be sure the storage used is durable and available.

Tip: If you're on AWS, you can always direct your output to [CloudWatch](https://aws.amazon.com/cloudwatch/). On Azure, consider using [Application Insights](https://azure.microsoft.com/en-gb/services/application-insights/). We will be going into more detail on logging in future articles, as getting this right is fundamental to success in making operationally supportable services.

## 2\. Log-Structured Data

Many of the logging components we get now will output JSON documents for each log instead of outputting flat rows in a text file. This type of data structure is important because log processing and collation tools can easily process each record, and the information you provide in each record can be richer.

## 3\. Create and Pass a Correlation Identifier Through All Requests

When you receive an initial request that kicks off some processing, you need to create an identifier that you can trace all the way through from the initial request and through all subsequent processing. If you call out to other components or microservices in order to complete your processing, then you should pass the same correlation identifier each time.

Each of your subsequent components and microservices need to use this identifier in their own logging so that you can collate a complete history of all of the work done to process a request.

## 4\. Return Your Identifier Back to Your Client

It's all very interesting if you can trace the flow through your system for a given request, but not much fun if you get a support call and you have no idea which request you need to be looking at.

When your API client has made a request and initiated a process, you should return a transaction reference in the response headers. When your Ops team needs to investigate the issue, they should be able to provide the transaction reference with a support call and you can find the relevant information in the logs.

## 5\. Make Your Logs Searchable

It's a good start to capture your log data, but you're still left with a haystack of information even if you have the identifier of your needle. If you're going to be serious about support, then you should be able to search and retrieve a collated and filtered set of information for a single request.

Even if your data isn't initially being written into a data warehouse, you might want to look at offline processing that loads it into one. You've got plenty of options for this, such as the [ELK stack](https://www.elastic.co/products/logstash) or [AWS Redshift](https://aws.amazon.com/redshift/). If you're on the Azure stack, you could choose [Application Insights](https://azure.microsoft.com/en-gb/services/application-insights/), as mentioned above.

## 6\. Allow Your Logging Level to Be Changed Dynamically

Most logging frameworks support multiple levels of details. Typically, you'll have error, warning, info, debug, and verbose as the default logging levels available to you, and your code should be instrumented appropriately. In production, you'll probably log info and the above, but if you have problems in specific components, then you should be able to change the tracing to debug or verbose in order to capture the required diagnostic information.

If you're getting problems, you should be able to make this change to logging levels on the fly while your systems are running, diagnose the issue, then return the logging back to normal afterward.

## Summary

Fault-finding in distributed microservices can be difficult if you don't readily have access to the logs from all of the machines your code runs on. Virtualized cloud instances, which can disappear at any time, exacerbate the problem because you cannot go back to a machine instance later to see what has happened.

Planning the management of logs and how you conduct fault finding needs to be done at the design phase and executed with the appropriate tooling and technique. Once you've cracked this, supporting your systems will be a whole lot easier.

Learn tips and best practices for optimizing your capacity management strategy with the [Market Guide for Capacity Management](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html).
