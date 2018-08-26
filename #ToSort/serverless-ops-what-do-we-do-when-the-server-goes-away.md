# Serverless Ops: What Do We Do When the Server Goes Away?

_Captured: 2018-03-23 at 13:27 from [dzone.com](https://dzone.com/articles/serverless-ops-what-do-we-do-when-the-server-goes-1?edition=368224&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-03-23)_

The Nexus Suite is uniquely architected for a DevOps native world and creates value early in the development pipeline, provides precise contextual controls at every phase, and accelerates DevOps innovation with automation you can trust. [Read how in this ebook](https://dzone.com/go?i=222229&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

When I began to use AWS Lambda and built my first serverless service, I was excited by the speed of delivery I could achieve. With these striking benefits, I knew others would be excited, as well. The result? Less worrying about provisioning capacity for my service, and more time spent on the actual features of that service. That excitement also led me to question my future role as an operations or DevOps engineer. What would I do if there were no servers to manage? What would I do each day? How would I explain my job? How would I explain my value to my current employer or a new prospective one? What would I do when the server goes away?

Now is the right time to start discussing operations in a serverless world. If we don't, then it will be defined for us. On one end currently, there are people proposing NoOps -- the transfer of operational responsibilities to software engineers. On the other end are people who believe the operations team will change, that they will always be needed.

The truth of the future lies somewhere in between these two approaches The complexity of production operations is changing shape and expanding. As traditional problems in operations become abstracted away by serverless computing, the makeup of teams and organizations operating SaaS products will change. Yet, many problems still exist: proper architectural design, observability, deployment, security, and more.

To say it bluntly: Teams without operational expertise are at risk.

Operations never goes away; it just evolves in meaning and practice. The principles of operations and operations engineers still have tremendous value. However, we as a community need to be the ones who define our new role.

With that in mind, here's what this post will cover:

  * Exploration of operational responsibilities in a world where so many layers of the stack are abstracted away.
  * A proposal for an organizational role to fill these new responsibilities.

This post is a start at defining this new operations role, but keep in mind that it's not the only way to define the ops role under a serverless architecture. I tend to work at SaaS startup companies and think of operations in that context. This is the start of a conversation. People will disagree with my observations, ideas, and conclusions, and that is good. Those disagreements will help us find the right answers for different people and different organizations.

Here's how I see the future of operations in a serverless infrastructure.

## What Is "Operations"?

Let's start with a common definition. I find people understand operations differently, each correct in their own way. The choice of definition just signals a person's point of view. The end result is people talk past one another about different things.

At the highest level, operations is keeping the tech to run your business going. But beneath that, the term "operations" can be used in several different ways. People tend to conflate these meanings because, for the longest time, they were tightly coupled.

Operations is:

  * A team
  * A role
  * A responsibility
  * A set of tasks

Traditionally, the responsibility of operations was held by the operations engineer on the operations team. That has changed significantly over the past several years with the introduction of DevOps. We tore down the silos, and without that rigid structure around us to keep those meanings coupled, they started to break apart from one another.

Developers started to assume some of the responsibilities of operations when they were no longer able to toss code over the wall to the operations team. The classic example of this division of operations responsibility is when someone says, "developers get alerts for their services first."

On the other end of the definition, some organizations introduced cross-functional teams composed of engineers who possessed operational and software development skills. These organizations do not have an ops team, and they don't plan on having one.

In the middle, the role itself has varied heavily. In some organizations, the role has varied little much more than adding automation understanding like Puppet, Chef, and Ansible to the skill set. Some teams have approached automation as a means of augmenting traditional operations responsibilities while others have seen operations engineers trend much closer to being a developer, developing in the configuration management and other tooling.

So what does serverless hold for these definitions of operations?

## What Will Operations Be With Serverless?

What I see for operations in a serverless world is two-fold:

  1. The operations team goes away.
  2. The operations role reassumes primary responsibility of the operations role back from developers.

Serverless operations is not NoOps. It is not anti-DevOps and a return to silos. With the dissolution of traditional ops teams, these engineers will need new homes. Those homes will be individual development teams, and these development teams will be product pods or feature teams. This new approach will lead the rise of cross-functional teams; a goal so many of us have talked about but have failed to achieve.

### The Product Pod: Cross Function in Action

Many organizations have already adopted product pods and feature teams. These are typically cross-functional multidisciplinary teams that exist to solve a particular problem or set of problems. These teams thrive through the collaboration between team members of different skill sets, experiences, and perspectives.

What does a product pod look like in practice? In the organizations I've been in, they've typically consisted of the following roles:

  * Product manager
  * Engineering lead
  * Backend developer (1-2)
  * Frontend developer (1-2)
  * Product designer and/or UX researcher (sometimes one person)

The product manager is the person on the team who is responsible for owning and representing the needs of the business. The PM's job is to understand the business needs and turn them into actionable ideas. Similarly, you'll have a product designer or UX researcher that will work with the PM to turn these ideas into full-fledged designs and prototypes. The tech lead, in turn, is responsible for estimating the amount of technical work involved and leading the engineering effort. From there, you have a number of backend and frontend engineers as appropriate.

The end result is a small team focused on using their differing skills to solve a business problem. The cross-functional set of skills on the team leads to a stronger team and better systems.

### Our Role in the Product Pod

As the member of a product pod, what will the role of the operations person be? Overall, they will be the person responsible the holistic health of the systems or services provided by the team. The operations person will act as a utility player. They will be good at their primary role ensuring the reliability of the team's services. They will also be good enough at other roles on the team to augment, offload, or fill-in in a limited capacity when necessary.

As a member of the product pod, the operations engineer will reassume the primary responsibilities for the reliability and performance of the system as a whole. That doesn't mean they'll be the first one paged every time. It means that they will be the domain expert in those

While software developers focus on the individual components, the operations engineer will be responsible for the system as a whole. They'll take a holistic approach to ensuring that the entire system is running reliably and functioning correctly. This, in turn, will free up software developers to spend more time on feature development and less time on operations.

## The Ops Skillset

So, what are the skills the person in the ops role will require in order to be effective? Let's break this down into two sets: The skills ops currently possess that underpin the value they provide, and the skills many operations people will need to level up or possibly begin acquiring.

### The Skills We Bring

Let's run through the set of skills that an operations expertise brings to a team. These skills have historically been the primary set for an operations engineers; these are the focus of their expertise..

  * Systems engineering
  * Platform/tooling understanding
  * People skills (important for all roles)

Our systems engineering skills involve designing, building, operating, scaling, and debugging systems. Our role has required us to have an overall understanding of the systems we're responsible for. This means spotting weaknesses, potential areas of improvement, and understanding how changes may affect the overall reliability and performance of a system.

All engineers develop expertise in the platforms and tooling they regularly use. A frontend engineer develops expertise in JavaScript and frameworks. (Or invents their own...) A backend engineer develops expertise in building APIs and communicating between distributed backend systems. As operations engineers, we develop expertise in tooling and platforms. In an AWS environment, we hone expertise in tools like CloudFormation and Terraform, which have a steep initial learning curve. We also have expertise in aspects of AWS -- like understanding the idiosyncrasies of the different services: for example, Lambda cold starts and how its CPU scaling is tied to function memory allocation.

Finally, there's our people skills. Let's stop calling them soft skills while we're here. People are hard, whereas computers are fairly deterministic in their behavior. People, however, are not. Much of the work of operations engineers is taking requests from people, and figuring out the actual problem a person is trying to solve. Good operations teams are service teams that understand the needs of the people they are trying to serve. These skills serve to enhance the relationship the technical team will have with a product manager.

### The Skills We Need

Here's the skills we'll need to level up on or even still acquire. The evolution in different directions of the operations role has resulted in an uneven distribution of these skills.

There is absolutely no doubt about it, the operations person is going to need to learn to code. On top of that, they're going to need to learn the chosen language(s) of their team. Whether it's Python (yea!), JavaScript (well, okay.), Java (ummm...), or Erlang (really???), the operations person will need to be proficient in the language.

Remember the ops person is a utility player. They're not there to be a developer. Being proficient in the language means being able to read it, code light features and fix light bugs, and doing some code review. If you're quizzing the person on fizz-buzz or asking them to do something with b-tree, you're probably doing it wrong. However, if you're asking them to code a basic function, or read a block of code, explain it, and show points of potential system failure, congrats! You're doing it right.

On the positive side for the code-phobic, nanoservices are much simpler than monoliths or even microservices. Rather than snaking your way through a large code base, you should be able to isolate your issue in many cases down to a single function, and therefore just a small subset of code to work with. This should make understanding the code easier.

## The Ops Role Responsibilities

In a serverless environment, once an operations engineer has joined a product pod, then what do they do each day? What will their job description be?

We need to be able to articulate a set of responsibilities to our organization; to explain the role, because, without a job description, you have no job. And, if you can't explain it, then someone else will… And that possibly means your job will be explained away because of "NoOps."

Much of the ops role will be reclaiming past responsibilities that developers started to own. Again, the ops person won't be the sole person responsible for these areas, but they will be the primary owner and tasked with enabling their fellow teammates to meet these challenges where appropriate.

### Systems Standards and Best Practices

Operations engineers will take the responsibility of establishing the systems standards, and best practices for building reliable and performant serverless systems. We should be defining the correct patterns to use (and when to use them), and ensuring that these are adhered to.

Take a simple task like passing an event between parts of a serverless system. The average person will do what they know, and stick to what they did last time. But even such a simple task can be solved in a variety of ways on AWS. What are the pros and cons of SNS over SQS? What about a Lambda fanout function? Perhaps the event should be written to persistent storage like S3 or DynamoDB and events from those actions be used to trigger more work actions?

What's the correct choice? That's going to depend on the problem you're trying to solve and the constraints. (For the record, I typically hate Lambda fanout functions because they require more error handling in the fanout function to not lose events rather than just letting the system's design handle resiliency.)

### Build, Deploy, and Management Tooling

What is one of the major obstacles we all face as engineers? Understanding our tooling. Our tooling is often significantly complex, but we learn as much as we really need to know to get the job done.

Tooling like Serverless Framework and CloudFormation can be complex. I find many developers are not exactly fans of them. Your dev teammates WILL hardcode stuff and thwart a lot of the problem-solving CFN has built in. CloudFormation can be very flexible if you know how to properly use it. Serverless Framework improves greatly on CloudFormation with its plugin capabilities. Writing Serverless Framework plugins to solve organizational issues will replace writing Puppet facts and Chef `knife` plugins.

There will also be testing and deployment work to be done. Start with your standard testing frameworks for Python, Node, or Go. But wait, there's more! What about load testing? If your service's compute layer can rapidly scale, what does that mean for your data layer? Can your DynamoDB table keep up with the Lambda's writing to it, and what happens to those failed writes due to write throttling? Can your SQS consumers keep up with the queue? Implementing tools like _Artillery_ to find scaling issues, that an Ops person will then take on solving, will become a part of the role.

Once all tests are passed, it's time to roll out new code. Eventually, organizations will want to blue/green deployment systems, feature flags, and more to ensure the graceful rollout of code to production users. Someone will need to build that.

### Scaling and Performance Tuning Systems

I grouped these two together because they're both a part of modifying an already running system and because they can be boiled down to meeting newly established system metric objectives. Scaling a system to go from servicing an order of magnitude more events is the same class of work as trying to reduce response times by a certain number of milliseconds. There is an established baseline, a target objective, and system to be modified to meet the objective.

The work of scaling systems narrows with serverless. The individual system components scale for you on their own. You aren't responsible for scaling your messaging, queuing, storage, or database layers. So what's left to tune and how do you scale?

Lambdas can have their amount of amount of memory increased, which also increases the amount of CPU available to a Lambda. Instead of creating new compute instances and rolling them in while you roll out the old ones, changing memory is a simple click or stack deployment with Serverless Framework or CloudFormation. Additionally, you'll also be looking at replacing components of a system with different services. If SNS is too slow, then perhaps it's time to evaluate Kinesis? Or maybe the system as a whole and its event pathways need rethinking?

There will be code changes to evaluate, from fixing inefficient functions to looking at replacing individual functions with ones written in a different language. At a certain point in scaling Lambda memory, an additional CPU core becomes available. Perhaps a function should be rewritten in a language that can utilize that extra core efficiently? (Isn't the ability to rewrite a single nanoservice function pretty cool compared to rewriting an entire microservice!?!?)

But with all this ability to easily scale creates new potential issues. Can the downstream services in your system handle the new scale or performance? Someone will need to look at the system as a whole and understand how upstream changes will play downstream.

### Reliability of Systems

We've been handling the monitoring, metrics, logging, and observability of our systems, and will continue to do so. The issues we'll be looking for will change. Rather than host CPU and memory utilization, we'll be looking for function execution length of time, cold starts, and function out of memory exceptions. The ops person will be responsible for selecting and instrumenting the proper tooling for the team and solving the issues that surface. If a function has started to throw out of memory exceptions, the ops person should be responsible for resolving the issue by increasing function memory (the easy but more expensive way), or through refactoring the given function.

Additionally, how many of the metrics and logging solutions we use designed for microservices, or even monoliths, are appropriate for nanoservices? Nanoservices are functions, and we're told the best functions do a single thing. So why is your function responsible for doing its named function? ... And writing metrics, and writing logs, and writing errors? Sure, there's CloudWatch, but its delay isn't short enough for many teams. Maybe we need to rethink how we deliver those to other platforms.

### Coding and Code Review

There's no getting around that operations engineers will need to code and be involved in other areas of the coding process. What this looks like in practice will vary by team and need, of course, but there should be some established minimums.

The team's operations engineer should be proficient in the coding language(s) of the team. They should be able to fix light bugs. In the process of investigating error logs while handling their reliability role, instead of just filing a ticket for a software engineer, an operations engineer should be able to look at the problematic code area and fix low hanging fruit. If they can't, then they should be able to write up a detailed ticket explaining the problem and where they think the code goes wrong.

> _"This should be wrapped in a try/except block to handle API failures. Let me add that."_

Ideally, we should also eventually level up to be able to code simpler tasks and features. I add this because it improves our skills and keeps them sharp. It also has practical value when a team needs to ship. Work that could be punted down to a more junior engineer (or even an intern) can be handed to the operations engineer to augment the output of developers.

> _"I can put up an REST endpoint that will ingest webhook data, parse it, perform a few web requests to enhance the data, and publish it to another system." (_[Inspiration from Alice Goldfuss](https://twitter.com/alicegoldfuss/status/932079153582452736)_.)_

Finally, there's code review. We should be bringing our unique knowledge and perspective of how the platforms we use work, and also think about the code as a part of the greater system.

> _"When you add a record to Route53, the action is queued. You need to use the callback and check that the operation was successful. Here's what you need to do."_
> 
> _"This function should have retries because we may fail at the end here, but you can't safely retry the function because we'll end up with duplicate DynamoDB records due to this spot earlier."_

One area of friction will be developers incorrectly assessing the value and skills of an operations engineer solely on their coding abilities. The operations engineer is only a part time developer, and they should be treated as such. If a team requires a senior developer for senior developer work, then give that work to a senior developer. Developers on the team will need to recognize the value of their operations engineer and the expertise they bring. If not, the operations engineer will be set up to fail, and the team as a whole will fail to achieve what other more cohesive teams can.

### Security

The good news on the topic of security: ops can stop focusing its time and effort on the hosts the code runs on. That's the responsibility of AWS now. Think about the recent Meltdown and Spectre attacks as an example, and the time people spent rolling out, rolling back, and rolling out patches again. Instead of patching systems, an ops person would continue ensuring that performance and reliability of services remain within acceptable parameters as AWS performed their work. That means monitoring for an acceptable rate of Lambda invocation failures, and then execution times remain acceptable. This is, of course, work already being done as a part of standard reliability responsibilities. This is effectively freeing up time.

However, that time is going to be filled up quickly. The time saved will be spent on tasks that we previously didn't give enough time to. Have you audited your S3 buckets? Do you have any that are publicly accessible that shouldn't be? Do your Lambda functions have IAM roles with least privilege access? We can spend more time securing out non-EC2 resources.

With this additional time, ops can also travel up the stack and into AppSec. The lowest hanging fruit: are application dependencies up to date _and_ free of vulnerabilities? Currently, ops spends time patching hosts, but often not enough time ensuring application dependencies are up to date. Ops will work on tasks like secrets management and ensuring that secrets are properly stored and rotated.

These tasks are merely examples; that's not to say that they aren't currently being handled. They are just handled at varying levels across many organizations.

### System Cost Management

Serverless brings some new and interesting challenges to cost around the pay per use model.

First, there's the technical challenge of preventing runaway Lambda functions. Recursive functions are a thing and a valid design choice for particular workloads. But anytime you see one, you should ensure that the loop will exit or you may end up with some surprises in your bill. (Ouch! This recently happened to me... )

The issue isn't just code, either. A malformed message in an SQS queue can lead to a queue that never drains, and a function that continuously executes. Knowing your systems means knowing how and when to alert on unusual function activity. If you're processing a queue in periodic message dumps, then your consumers should exhibit a certain behavior -- like not executing for greater than a certain period of time. If they're not following that pattern, then maybe there's something to investigate?

There's also the difficulty of determining when a system becomes more suitable from a cost perspective to run in a container or even on an EC2 instance. The pay per use model of Lambda comes at a premium on actual invocations.

Finally, serverless gives you a unique ability to measure past the system level, and down to the feature level. I like to call this "application dollar monitoring". If you track cost per function invocation and overall system cost over time and then overlay feature deploys events, you have the ability to understand system cost changes at a much finer level. Potentially down the road, an organization may even be able to tie features to revenue and be able to make smarter decisions about feature value and feature work. Admittedly, right now you're talking about small dollar amounts, and the cost saving over EC2 may already be enough to not care at the feature level. However, in the future, as we become accustomed to the low costs of serverless, we will begin to care more.

## Conclusion

There's a lot in this post that's assumed, unexplained, and undefended. Over the coming months, I'll be expanding on the ideas and themes here. This piece has hopefully generated questions from people that will require further answering. Finally, what the ideas in this piece look like in practice and how to get there requires practical explanations.

Have thoughts on what you've just read? [Find me on Twitter](https://twitter.com/tmclaughbos) and let's have a conversation.

_A thank you goes out to several people who contributed feedback while I was writing this. They were _[Brian Hatfield](https://twitter.com/brianhatfield)_, _[Travis Campbell](https://twitter.com/hcoyote)_ and others in #atxdevops on _[HangOps](https://twitter.com/hangops)_, _[Ryan Scott Brown](https://twitter.com/ryan_sb)_, _[Ben Bridts](https://twitter.com/ikB3N)_, _[Rob Park](https://twitter.com/robpark)_, and _[Gwen Betts](https://twitter.com/gwennasaurus)_._

The DevOps Zone is brought to you in partnership with Sonatype Nexus. See how the Nexus platform infuses precise open source component intelligence into the DevOps pipeline early, everywhere, and at scale. [Read how in this ebook](https://dzone.com/go?i=222230&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).
