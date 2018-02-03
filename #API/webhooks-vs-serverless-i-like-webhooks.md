# Webhooks vs. Serverless: I Like Webhooks

_Captured: 2018-02-02 at 16:54 from [dzone.com](https://dzone.com/articles/webhooks-vs-serverless-i-like-webhooks?edition=359105&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202018-02-01)_

The serverless vs webhooks debate has been discussed in developer communities for a couple years now. It usually comes up as the answer to this question: "How do we add more functionality to our platform faster?" Since everyone wants to build features faster, it comes up a lot.

In a perfect world, you'd be able to hire 100,000 engineers, split them into teams of four (_with no managers!_), and have each team own a feature: spec it out, build it, iterate on it with user feedback, and do it all in perfect harmony with every other team.

But let's get real. This isn't a perfect world, there's no way a company would ever have four engineers work in a team without management (_ha_)!

So while you may not be able to build features at a fast enough pace to keep up with your product and user growth, you can cheat your way around it with a popular hack: platform extensibility.

Instead of requiring your engineers to sit down and develop every single feature every single user has ever requested, you can turn your product into a "platform" that your customer's developers can build against. This way, if a customer wants a feature badly enough, they can integrate with your platform APIs and, bam, the previously unavailable feature can now be made available! It's ingenious.

So how do you (as a successful business owner) allow other developers to extend your platform? You've got a lot of choices. Most of them are horrible, however, so I'm only going to talk about the most popular two: webhooks and serverless.

## Serverless Is the Answer!

If you've been following the internet hype train over the last few years (_specifically, since 2014_), you'll be familiar with the term "serverless," also known as "lambdas," "functions-as-a-service," etc.

What all these terms basically refer to is a pattern known as _serverless extensibility_.

In order to accommodate your customers extending your platform, you allow them to upload some code to your servers that _you _will run when certain events happen in your product.

I'll give you a good example.

Let's say you're building an application hosting platform (_a-la [Heroku](https://www.heroku.com/)_). Heroku provides functionality like running your application code, logging errors, and provisioning infrastructure (databases, etc.).

If a customer is using your platform and wants to send an email to their accounting team every time a new database is provisioned, this can be somewhat tricky unless your platform provides either a feature to do this or extensibility options so the customer can do it on their own.

So, you decide to allow serverless extensibility. A customer can now upload some code (in JavaScript) to run on your platform every time a new piece of infrastructure is provisioned.

The customer reads through your docs, and writes a small function that looks something like this:

And then uploads it to your website.

This is pretty cool for the customer! Without needing to bug you and wait for your engineering team to build this email feature out, they were able to write some code to accomplish exactly what they wanted!

And not only can customers "hook" into your platform when THE infrastructure is being provisioned, they can hook in anywhere! Your platform provides tons of different extensibility options to make it possible for customers to run their code after or before almost every major platform event!

There are a few core benefits to this:

  * The customer can easily build out features they need, and not be bottlenecked by the speed of your engineering team.
  * You lose fewer customers because they've now got a way to work around issues in your product.
  * You're able to iterate more quickly on your core platform product because you're now able to narrow your scope.

## The Flip Side of Serverless

So now that you've built out serverless extensibility functionality for your customers, you've opened up an infinite amount of customization options. But at what cost?

John, who runs Engineering for one of your largest customers, didn't sign up for this. Your serverless extensibility created a bunch of ongoing work for him and his team:

  * He has to figure out how your serverless functions work, what hooks are available, etc. This is a high learning curve and requires all of his engineers to have a thorough understanding of your product in order to be productive.
  * Because your serverless platform only supports running JavaScript ES5 code at the moment, John's team of C# engineers are having issues writing their complex application logic in JavaScript which they are not all familiar with.
  * John's team doesn't have any insight into how your serverless platform is running his code: they can't figure out how to monitor server resources, how to do proper unit and integration testing, how to look for failures, etc.
  * John's team now has to manage code in many different places as opposed to just one GitHub repository. Now, each serverless function John's team writes must be manually uploaded into the right place in your platform website, maintained, and updated from time to time. Because there is no direct way to integrate these serverless functions into the team's existing codebase, this code is now fragmented across your platform which makes it hard to work with.
  * John's team is now in a sticky security situation: they've got to write proprietary code and store it on YOUR platform. They've also got to store sensitive credentials like their email account information, and any other related credentials required to run their serverless software. The security team at John's company isn't thrilled.

The larger the company, the more challenging this becomes. Coordinating between different groups of engineers to figure out where a particular piece of functionality is located is difficult and time-consuming. Updating previous hooks becomes a test of patience. And documentation for the team's codebase becomes exponentially larger to include all of the domain-specific knowledge required to write, update, and maintain these serverless hooks.

These side effects negate the purpose of the original goal: to let customers get the functionality they need faster.

And these are just the _customer-facing_ side effects you'll notice. There's a vast array of other messes this will cause you and your company:

  * You've got to build secure, isolated code execution environments to run customer code in a sandbox. This is incredibly hard in practice. If you search for "[docker escalation](http://lmgtfy.com/?q=docker+escalation)" on Google, you'll see what I mean. Even amazing services like Amazon Lambda (the first really serverless player) that have incredibly large security teams can expose themselves to funny [security ](https://www.youtube.com/watch?v=YZ058hmLuv0)issues.
  * You've got to ensure you respect the customer's software IP that is now running in your infrastructure.
  * You've got to scale your infrastructure to support arbitrary amounts of customer code in addition to worrying about your own service issues.
  * You've got to expose more and more transparent tools to allow your customers more insight into your system: error logs, performance monitoring, etc. The list can ultimately go on forever.
  * You've got to write documentation to explain each and every hook you support and how it works. You've also got to show users how to upload the code to your platform, how to test it, etc.

Bottom line? Building serverless extensibility functionality into your product will likely be the most expensive thing you ever do, engineering-wise - both for you and your users.

## Webhooks, Going Beyond Serverless Extensibility

An older approach that's been tested time and time again is webhooks. While webhooks are not "old" by any means, they predate serverless extensibility patterns by at least seven years. My buddy [Jeff Lindsay](http://progrium.com/blog/) coined the term back in 2007.

The idea behind webhooks is simple: instead of _you_ running a customer's code on _your platform_, you instead just fire off an HTTP POST request to the customer every time something happens, and the customer can then perform whatever logic they need based on those incoming requests.

Simple, right?

This is a great approach because it's easier to manage and scale for all parties involved.

It's simpler for _your_ company because you now only need to fire off HTTP requests when events happen. You don't need to worry about executing someone else's software, scaling it, etc. The most complicated thing you have to do is retry failed HTTP requests (which is mandatory for pretty much all HTTP requests anyhow!).

It's simpler for your customers because they don't need to learn anything new (other than reading your docs to find out what requests you make, and what data you send).

Customers can simply implement backend logic in their already existing application in whatever language/framework/etc. they prefer. The customer doesn't need to learn a new tech stack, new deployment patterns, and doesn't need to figure out how to create a bunch of small, independent programs that are scattered all over the place.

Webhooks allow customers to extend your platform in a simpler, easier-to-understand way.

## Webhooks in the Wild

[Twilio](https://www.twilio.com/) is one of the best-known API services in the world. Twilio provides API services to manage telephony stuff: phone calls, SMS messages, MMS messages, etc.

Since day one Twilio has provided core webhook support in their platform.

Let's say you're building an SMS application:

  * You buy a phone number through Twilio.
  * Every time that phone number receives an SMS message Twilio sends an HTTP POST request to your web server with the message data inside.
  * You then receive an HTTP POST request to your web app, where you parse the request, figure out what the message said, and then take some action (_maybe you send a response, for instance_).

Using this simple back-and-forth messaging pattern, webhooks allow Twilio customers to easily integrate with the platform and build high-value apps without the hassle.

**NOTE**: My good friend [Carter Rabasa](http://carter.rabasa.com/) at Twilio recently released support for serverless extensibility _in addition to_ their core webhook support. This was a smart move, as they now appeal to everyone (_even people who crazily prefer serverless extensibility patterns!_).

Remember Heroku from the serverless example before? I hope so!

Heroku's application hosting platform recently started [supporting webhooks](https://blog.heroku.com/heroku-webhooks), and it's everything I ever dreamed of, and then some!

Heroku customers are now able to easily hook into their app infrastructure on Heroku, and perform complex logic to scale their services more easily, cut down cost, keep their ops team informed of issues, etc.

[GitHub webhooks](https://developer.github.com/webhooks/) have been around forever, and are the foundation of many popular developer services like [Travis CI](https://travis-ci.org/).

GitHub webhooks allow you to hook into just about every possible action that can be taken on a source repository. They're excellent for analyzing code, tracking team performance, automating testing and deploys, as well as a number of other great use cases.

## Webhooks in Your Product

Implementing serverless extensibility is hard - both for you and your customers. While there are some people who prefer it, it can be a lot of work for everyone involved.

As someone who's been building developer tools and API services for nearly 17 years now, one of which generates nearly 30 billion API requests per month, I'd encourage you to take some time to think about the best possible way for you to open your platform up for customization.

Picking the wrong extensibility options can be a painful mistake, so it's a good idea to think through the tradeoffs of both approaches and pick what makes the most sense for you.

## Summary

While both serverless extensibility and webhooks serve the same purpose, one is dramatically simpler than the other.

Webhooks are a simple solution to a complex problem, while serverless extensibility is a complex solution to a complex problem.

In computer science, as well as many other areas of professional and personal life, I like to take the simple path.

I hope this has been useful.

_The article "[Why Are Webhooks Better Than Serverless Extensibility?](https://developer.okta.com/blog/2017/10/11/why-are-webhooks-better-than-serverless-extensibility)" first appeared on the Okta blog on Oct. 11, 2017._
