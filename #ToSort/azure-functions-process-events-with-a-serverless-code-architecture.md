# Azure Functions: Process Events With a Serverless Code Architecture

_Captured: 2017-03-01 at 03:00 from [dzone.com](https://dzone.com/articles/azure-functions-process-events-with-a-serverless-code-architecture?edition=271922&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-28)_

Download the [Essential Cloud Buyer's Guide](https://dzone.com/go?i=123025&u=http%3A%2F%2Fpd.internap.com%2Fcloud-buyers-guide-DZ) to learn important factors to consider before selecting a provider as well as buying criteria to help you make the best decision for your infrastructure needs, brought to you in partnership with [Internap](https://dzone.com/go?i=123025&u=http%3A%2F%2Fpd.internap.com%2Fcloud-buyers-guide-DZ).

What's up guys, Eze is here. During our [last posts](https://dzone.com/users/2967529/skielo.html) we were talking about Firebase, AngularJs, and a bunch of cool tools to create rapidly powerful front-end apps, in case you missed it you can check [here](https://kieldev.wordpress.com/category/angularjs/). Today, I want to bring you some server side code that runs in a serverless architecture. Yes, we are going to talk about **Azure Functions**.

## About Azure Functions

This is a cool feature that the Azure team has created for us. The idea is to mix events and code to execute in a serverless environment, which basically means you don't need to care about where your code is going to run, server configuration, how much memory you're using, or which OS version you're dealing with. You just need to define the code to execute and which event is going to trigger our function. As they say:

> An event-based serverless compute experience to accelerate your development. It can scale based on demand and you pay only for the resources you consume.

## Common Scenarios for Azure Functions

**Trigger by time**: Azure Functions uses CRON job syntax to specify an event based on a timer. So let's say that we want our code to run every 10 minutes.

_**Azure service event**_: We can set up our function to execute every time something happens in an Azure service. For example, when a new file is uploaded into blob storage.

_**Serverless web application architectures**_: This one in particular is the one I've used for our example. In this case, a front-end app calls a function to execute a procedure on the server side.

## Function Components

As you can see in the image below, the Azure function is made up by two files: The first one is _function.json_, which represents the structure of our function -- basically the metadata of our function. The second one is a _run.csx_ file (because I'm using C#), which is the method we want our function to execute. Microsoft offers us a web editor to edit our functions directly in the browser, but if we want, we can configure a GitHub project and set up an automatic deploy when we push to our repository.

![function.png](https://kieldev.files.wordpress.com/2017/01/function.png)

I have a working example in this [link](https://github.com/skielo/CityTimer) if you want to see the complete implementation. In this example, every time a user makes a request in our front-end app, we call this Azure Function to store the request in an Azure storage table, as you can see below:
    
    
    public static async Task<HttpResponseMessage> Run(HttpRequestMessage req, ICollector<Request> outTable, TraceWriter log)
    
    
                    RowKey = Guid.NewGuid().ToString(),

And there you have it! For more details on Azure Functions, you can use this [link](https://azure.microsoft.com/en-us/services/functions/).

If you found this post useful, please don't forget to press the like button and share it. If you are in doubt, don't hesitate to ask a question and, as always, thank you for reading.

The Cloud Zone is brought to you in partnership with [Internap](https://dzone.com/go?i=109853&u=http%3A%2F%2Fpd.internap.com%2Fbare-metal-101-pr). [Read Bare-Metal Cloud 101](https://dzone.com/go?i=109853&u=http%3A%2F%2Fpd.internap.com%2Fbare-metal-101-pr) to learn about bare-metal cloud and how it has emerged as a way to complement virtualized services.
