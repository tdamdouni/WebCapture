# Building a Start-Up Using Serverless Technologies — Part 1

_Captured: 2018-07-17 at 19:14 from [dzone.com](https://dzone.com/articles/building-a-start-up-using-serverless-technologies?edition=385247&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-17)_

[Learn how modern cloud architectures use of microservices has many advantages and enables developers](https://dzone.com/go?i=300448&u=https%3A%2F%2Fwww.cloudentity.com%2Fwhite-paper-microservice-devsecops-zone%2F) to deliver business software in a CI/CD way.

## Introduction

In this series, we'll be looking at how to create a start-up using only serverless technologies.

We'll be using AWS Lambda, and other AWS technologies, the [Serverless framework](https://serverless.io), and of course, Go!

In this part of the series, we'll start by creating our serverless project, and explore some of the basic concepts when creating serverless API's. By the end of the part, we will have a couple of serverless functions and a DynamoDB table.

## Prerequisites

First you will need to create an AWS account, and you will need to generate some security credentials and ensure those are active on your machine. You can do this with the AWS CLI tool `$ aws configure`.

You will also need to install serverless `$ npm install -g serverless`.

## What Will We Be Building?

We will be building a start-up which allows self-employed people to keep track of work they've done for each client, and to automatically send them an invoice at a set date of the month. Pretty simple, also kinda useful. I wanted us to build something with actual value, that we could get something out of. Also, I'm aware this probably isn't some new innovative business idea, if it was, I wouldn't be using it as a tutorial, but it's useful enough to serve as a real-world example.

## Why Serverless?

If you're a start-up, even in a big business, dealing with infrastructure is a huge cognitive and financial overhead for any team. Typically you'd have DevOps engineers or ops people constantly tweaking and maintaining the health and performance of technologies running on servers, even in the cloud, servers have to be maintained and updated.

One of the great things about microservices, is how your domain models are contextually bounded by each service, each service represents a single entity and its functionality. This makes software easier to reason about, especially in large systems. However, the downside to that is that now you have to worry about networking, service discovery, and communication.

Serverless treats your services as a group of functions, like functional programming, functions are created and combined in order to create something bigger. Part of the power of Serverless, is this functional basis. Your system becomes a mesh of functions, which, when combined, create a system you can reason about, that you can test and update with a greater degree of confidence.

Finally, from a business point of view, with servers, you're paying for the entire time they're running, which in all probability is 24/7. Sure, you can utilize auto-scaling to cut down some of those costs when traffic is quiet. but you're still paying for a constant resource.

With serverless, that model is flipped on its head. Instead of paying for a constant resource, you only pay when your code is being used, in other words, you're not paying for your code when it's sat on a server doing nothing. This means you can really reduce your costs.

So what are the down-sides? Well, sometimes your function can take a little longer to fire up as when your function hasn't been used for a short period (seconds), it's powered down again. So it has to be fired back up again. This is "cold-start," and can typically take about a second sometimes, but once it's fired up, it's kept in the background for a while in case any more requests are soon to follow. But you only ever pay per 200ms of run time. The cold start performance is getting better, and I'd say was still acceptable for most use-cases.

Another use-case serverless probably isn't a good idea is if you have a very hot service, something that's dealing with hundreds of thousands of requests per second for example, i.e a constant considerable load of traffic. In which case cold-starts would probably be less acceptable, and they would likely become far more expensive than standard servers are.

## Let's Begin!

First of all, let's create our serverless project:

This will create a new serverless project, using the AWS + Go + Dep template and do a bunch of set-up for us. You should have a new directory which looks like this:

![](https://ewanvalentine.io/content/images/2018/05/Screen-Shot-2018-05-19-at-11.35.05.png)

We'll start by making a few small tweaks. First up, we'll create a new directory called `functions`, it feels a little nicer not to just have all of our functions in the root, especially as we add a user interface, etc.

Then delete the two functions the template has created for us, `hello` and `world`, we won't be using those. Though, feel free to take a quick look at the code to see how a basic Lambda is set up.

It's incredibly simple; Lambda starts a handler function, which returns a response, just like any old HTTP request. Ours are going to be a little different as we'll be using the AWS API Gateway in-front of all our Lambdas, but we will go into that more later.

For now, let's create two new directories within our new functions directory: `create-client` and `get-clients`. In each of those, create a `main.go` file. Then open `functions/create-client/main.go`, let's create our first function and start storing some data. But first, let's add a test. One other great thing about Lambda functions, they're so, so easy to test. You effectively pass in the spoofed request, then you just compare what you expect to get out of the Lambda as a response. Easy!
    
    
    func (repo fakeRepo) Store(*model.Client) error {
    
    
    	assert.Equal(t, http.StatusCreated, response.StatusCode)

Pretty easy, right? We're just passing in a request, and testing that nothing breaks. Now the function:
    
    
    func (h handler) Handler(request events.APIGatewayProxyRequest) (events.APIGatewayProxyResponse, error) {
    
    
    	if err := json.Unmarshal([]byte(request.Body), &client); err != nil {
    
    
    	if err := h.repository.Store(client); err != nil {
    
    
    	conn, err := datastore.CreateConnection(os.Getenv("REGION"))

So here we have our first function, fully tested and ready to go! But you'll notice a few libraries I've created in a directory named `pkg`. Pkg, according to the recommended go project structure, is a place to house re-usable Go code. I've created a library for connecting to the datastore, a helper for building responses (this can be a little tedious without), and finally, I've created a package for our core data models, as multiple functions will use the same models.

Here's our datastore function:
    
    
    func CreateConnection(region string) (*dynamodb.DynamoDB, error) {
    
    
    	sess, err := session.NewSession(&aws.Config{

Pretty straightforward -- it takes a region as an argument, and creates a connection to AWS DynamoDB and returns the datastore instance, and of course an error if applicable.

Now, our helper functions:

These just allow us to pass our response data in, in any format and have the JSON marshaling, etc handled in a consistent way every time. This allows our functions to focus on wrangling our data and actually doing the important stuff!

Finally, our first model and repository:
    
    
    func (repository *ClientRepository) Fetch(key string) (*Client, error) {
    
    
    	result, err := repository.Conn.GetItem(&dynamodb.GetItemInput{
    
    
    	if err := dynamodbattribute.UnmarshalMap(result.Item, &client); err != nil {

As you may have guessed, we're using AWS DynamoDB as our data storage engine. DynamoDB is Amazon's answer to NoSQL, such as MongoDB. It's very powerful, and it's already scaled for you, so you don't have to worry about maintaining a datastore cluster or scaling it. This is the beauty of using AWS technologies: a lot of the hard work is done for you. If you do opt for a traditional database model, not a serverless database, just be wary of how many open connections your database can support. If you suddenly fire up a thousand concurrent Lambda functions, each of which set up their own connections, this can cause problems. Just remember that Lambdas are highly concurrent.

Now we have some code to make our functions nice and neat, and most importantly the function itself, it's time to deploy our function using the serverless CLI.

First, take a look at the `serverless.yml` file in the root of our project, and ensure you have something like this:
    
    
    # Provider relates to your cloud provider here, so AWS, Google etc

Please read the comments I've left in the above example, as they explain a little about what they're for. The gist of this is, we're telling Serverless to use DynamoDB, giving it some information about what access our function should have, we're creating our function, referencing our function code (which will be a compiled binary), and then we're giving some additional Cloudformation config, which will create us our DynamoDB table.

Now all we need to do is compile our binary and deploy our serverless function!

I've updated our `Makefile`:

Now run `$ make && sls deploy`. You should see something like this:

![](https://ewanvalentine.io/content/images/2018/05/Screen-Shot-2018-05-21-at-13.18.31.png)

If you take a look in the AWS console under the Lambdas, you should be able to see your new function. If you also check under DynamoDB, you should also be able to see your new Clients table. Great! That was easy!

Take that URL and post some data to it:

![](https://ewanvalentine.io/content/images/2018/05/Screen-Shot-2018-05-21-at-13.23.05.png)

> _Now check your DynamoDB table:_

![](https://ewanvalentine.io/content/images/2018/05/Screen-Shot-2018-05-21-at-13.23.50.png)

There we have it! Our first serverless function, passing data into a datastore. In the next part in this series, we'll hook up a few more functions and start building out some more functionality. We'll also look at authentication using JWT and custom authorizers. Authorizers are like middleware functions which we can proxy all of our other functions through to ensure they have valid access tokens.

[You can check out the repo here](https://github.com/EwanValentine/invoicely).

Sponsor me on [Patreon](https://www.patreon.com/ewanvalentine) to support more content like this.

Discover how to [deploy pre-built sample microservices OR create simple microservices from scratch.](https://dzone.com/go?i=300428&u=https%3A%2F%2Fwww.cloudentity.com%2Fdemo-reward-zone%2F)
