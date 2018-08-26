# Going Serverless with Amazon Web Services (AWS) - The Traditional Approach

_Captured: 2018-03-02 at 20:26 from [dzone.com](https://dzone.com/articles/going-serverless-with-amazon-web-services-aws-the?edition=365216&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-02)_

Get the Metrics Collection and Monitoring Essentials [tutorial collection](https://dzone.com/go?i=274448&u=https%3A%2F%2Fwww.digitalocean.com%2Fcommunity%2Ftutorial_series%2Fmetrics-collection-and-monitoring-essentials%3Futm_medium%3Dbumper%26utm_source%3Ddzone%26utm_campaign%3Dbrand%2Bsimplicity%2Bat%2Bscale%26utm_content%3Ddistributed%2Bmicroservices%2Bdeployments). A 4-part tutorial series from [DigitalOcean](https://dzone.com/go?i=274448&u=https%3A%2F%2Fwww.digitalocean.com%2F%3Futm_medium%3Dbumper%26utm_source%3Ddzone%26utm_campaign%3Dbrand%2Bsimplicity%2Bat%2Bscale%26utm_content%3Dmetrics%2Bcollection%2Bmonitoring).

_This is the first blog of a series of two blogs, Going Serverless with Amazon Web Services (AWS)_

_1\. The Traditional Approach _

_2\. The Modern Approach _

In this blog, I am going to develop a very basic sample serverless application from scratch, utilizing AWS serverless components. Before moving forward, let's have a look at some terminology.

> There is no Cloud, It's just someone else's computer! 

This statement (_joke_) is true to a certain extent. But cloud computing offers lot more advantages which can't be expected from _someone else's computer _such as ([source](http://searchcloudcomputing.techtarget.com/definition/cloud-computing)),

  1. Self-service provisioning: Whenever you need resources, it is just a matter of few mouse clicks
  2. Elasticity: Scale up or down your resources ⇒ Saves money and time
  3. Pay per use
  4. Workload resilience: You don't have to worry about redundancy. Most of the times, service vendors take that burden for you!

In a nutshell, when it comes to cloud computing, you don't have to worry about infrastructure. Just keep worrying about **resource provisioning, your application logic**, **or code**.

### Serverless Computing

Serverless computing can be considered as a new variant or a new execution model of cloud computing where you get backends and processing units as a service(BaaS and FaaS).

Let's take an example from AWS world. With traditional cloud computing when we wanted to do processing, we had to get an EC2 instance provisioned and keep that instance up and running 24x7. At the same time, we had to pay for that instance whether we use it or not. Apart from that, we had to apply security patches, update OSes ourselves to keep our instance away from security threats. But with the introduction of Lambda, the new processing unit of Serverless family, things changed dramatically. With lambda, we just have to worry about our code and just forget about load balancing, security patches and even high availability.

So in Serverless computing, we even don't have to worry about resource provisioning, we just have to worry about our **code and application logic.**

### Let's Go Serverless with a Sample Use Case

#### Backend for a Contact Us form

![](https://cdn-images-1.medium.com/max/800/1*vtrQxvoUJFkRLfKWpfGvkQ.png)

Static websites can be hosted on services like Google Drive or even on github without any cost. But this advantage becomes useless when we want to add a simple yet essential dynamic component, such as a "Contact Us" form for the website. Either we have to run a server at the backend to collect "Contact Us"data, or we have to purchase a service which facilitates a backend for our _"_Contact Us" form. Either of these options costs us a fixed amount per month regardless of the traffic we get for our website and regardless of the fraction of people out of that traffic, who wants contact us.

We need to have the following components in the backend, in order to support above scenario.

  * REST endpoint which accepts AJAX calls from Contact Us page.
  * Processing unit to validate and accept incoming requests.
  * A database to persist responses.

In order to address above requirements, I am going to choose following the AWS services to implement my serverless contact us form backend.

![](https://cdn-images-1.medium.com/max/800/0*Zq99s1TVfDI5Oqk-.jpg)

Due to the simplicity of the sample use case, we can even drop Amazon Lambda and directly persist REST payload accepted by API Gateway to the DynamoDB. But for the sake of completeness, let's assume that we have to perform **complex **validations on the request payload. (API gateway can be configured to perform simple validations on payload as well, but let's assume my validation requirements are way more complex than the capabilities of APIG)

In this blog post, let me show you the _**_traditional, slowest and toughest_** _way of implementing this solution.

## Traditional Approach-- Using AWS Console

### Step 1 -- Creating the DynamoDB Table

You can start creating a table by clicking **Services ⇒ DynamoDB**

![Creating a DynamoDB table](https://cdn-images-1.medium.com/max/1000/1*Ytd1q4TzdJtXFMkSnaDe2Q.gif)

> _Creating a DynamoDB table_

Then, AWS will take you to the DynamoDB dashboard where you will see an option to create a table.

![Table name & Partition key are mandatory fields](https://cdn-images-1.medium.com/max/800/1*bj3NFyjGUWi3luebBa8kRw.png)

> _Selecting Partition Key & Sort Key_

In DynamoDB, when we create a new table, we can configure the read/write throughput that we expect from the table. In AWS DynamoDB world, we measure this throughput in read/write capacity units.

> One read capacity unit represents one strongly consistent read per second, or two eventually consistent reads per second, for items up to 4 KB in size. One **write capacity unit** represents one write per second for items up to 1 KB in size. 

Let's assume one partition of DynamoDB is capable of providing a maximum of 3,000 read capacity units or 1,000 write capacity units. Then, if we request 5,000 read capacity units and 1,000 write capacity units per table, AWS back-end is going to create DynamoDB partitions based on following formula. (This is just an assumption based on DynamoDB spec, the actual partitions created is not visible to the users)

This is similar to having 3 buckets, that can hold data. Whenever we write an entry to the table, DynamoDB is going to store that in one of above 3 partitions, based on the _Partition Key_ we have selected. ** The goal of the partition key is to select it carefully, such that our data get evenly distributed between the partitions.**

Within the partitions, entries are going to be ordered based on the _Sort Key_ that we choose at the provisioning time.

So in my example use case, I am going to select _email _as my partition key, which is unique for each person. Within the partitions, I am going to sort entries by date. However, having a _Sort Key_ is optional in DynamoDB. I am going to keep read/write capacity units for my table at their default values(5 & 5). So just one partition will be created in AWS servers to support my _contact_us_ table.

After setting all necessary parameters, click on ** Create **to start table creating process.

### Step 2 -- Writing AWS Lambda Code

Let's navigate to the Lambda console by clicking on ** Services ⇒ Lambda ⇒ Create Function**

![](https://cdn-images-1.medium.com/max/1000/1*gEhWYAxFI9KGiTPDjzBIGg.gif)

In order to create a lambda, we need to give a unique name and specify a run-time environment. Since Lambda is going to access your other AWS resources on behalf of you, you need to assign a role to lambda with sufficient permissions to access relevant AWS resources.

![](https://cdn-images-1.medium.com/max/800/1*R57Qj2rOddrDBLcYvbNorg.png)

Best practice is to assign a role, such that we assign only necessary permissions to our lambda function.

The function in my case, just need permission to do a _putItem _operation on DynamoDB.

### Creating a Role for Lambda Function

You can easily create a role (or use an existing role) with following permissions by following [AWS documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create.html).

  * dynamodb:PutItem
  * logs:CreateLogGroup
  * logs:CreateLogStream
  * logs:PutLogEvents

### Writing Lambda Code

Initially, I am going to write my function without any validations or extra logic. Since I am not going to use any 3rd party libraries initially, I can write the code directly in the AWS lambda console.

> The **Lambda **service has preinstalled the ** AWS SDK** for ** Node.js**

Now, let's assume I want to do some validations on the request before persisting them. (As stated initially, that is the whole purpose of using a lambda in this simple use case, instead of calling DynamoDB directly from API Gateway).

Since, inbuilt IDE of lambda console, doesn't has support to add 3rd party libraries, now I have to write my lambda function locally, in my computer and upload that code as a zip file(bundled with necessary dependencies) via lambda console.

### Creating Lambda Bundle Locally

I am going to start by initializing a new nodejs project and add necessary dependencies via node package manager.

Even in this case, it is not necessary to add AWS-SDK as a dependency to my node project. I am using _[validate.js](https://validatejs.org/)_ to validate the fields in the incoming request with a minimum effort.

Now, my code looks like follows, including request validation.

Now my local directory structure looks like follows.

![](https://cdn-images-1.medium.com/max/800/1*sDfyz002EM15jU3IngnrLA.png)

In order to deploy this as a lambda code, I have to make a zip file including everything in this folder and upload it via Lambda console. In order to do that, _code entry type _of my existing lambda function should be switched from __**Edit code inline**_ _to _**Upload a .ZIP file**_.

![](https://cdn-images-1.medium.com/max/800/1*HIXpPMqI2hr9bafnFHdtNA.png)

When it comes to this point, we have a fully functioning back end, and the only task left is to expose this back end through an API, so my Lambda function can be triggered externally from the _ Contact Us_ HTML form.

Let's go ahead and create an API Gateway resource to trigger this lambda function.

### Step 3 -- Creating API Gateway trigger

You can easily create an API from the Lambda console itself without having to navigate to the API Gateway console.

However, in my case, there are few tweaks that should be done to the generated API, and for that, I have to jump quickly to the API gateway console by clicking on the newly created API.

![](https://cdn-images-1.medium.com/max/800/1*A-a7kYf24GRGDm6mdZBigw.gif)

Here, I'm turning off lambda proxy integration (You may read about lambda integration types [here](https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started-with-lambda-integration.html)) and enabling CORS for my API endpoint.

After applying these changes, I have to redeploy my API to apply the changes.

![](https://cdn-images-1.medium.com/max/800/1*VpJzEYz3PqMVUaAtoTwo2w.gif)

Now you can test your API using any HTTP client of your choice and integrate this backend with your HTML contact us form.

This is the traditional approach for developing a serverless application and I hope you have realized that, with serverless computing, you can forget **resource provisioning** and just focus on **code and** **application logic.**

In the next blog post, let's see how we can develop a serverless application with the modern approach, where we forget both **resource provisioning** and **code (Yes!****) **and just focus on the ** application logic.**

Getting Started with Kubernetes: [A Webinar Series](https://dzone.com/go?i=280427&u=https%3A%2F%2Fwww.digitalocean.com%2Fcommunity%2Ftutorials%2Fwebinar-series-getting-started-with-kubernetes%3Futm_medium%3Ddisplay%26utm_source%3Ddzone%26utm_campaign%3Dbrand%2Bsimplicity%2Bat%2Bscale%26utm_content%3Dbumper_webinar%2Bkubernetes%2Bdzonecloud) brought to you by DigitalOcean
