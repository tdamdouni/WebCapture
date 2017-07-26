# Workflow and APIs

_Captured: 2016-11-21 at 00:36 from [www.jordanmerrick.com](https://www.jordanmerrick.com/posts/workflow-and-apis/)_

In what is most certainly an early Christmas present for people like myself, [Workflow](https://itunes.apple.com/us/app/workflow-powerful-automation/id915249334?mt=8&uo=4&at=10l64N) has just received one if its most significant updates-extensive support for making API requests. I can't emphasize enough how useful this is and the impact it's going to have when it comes to iOS automation.

Workflow's "Get Contents of URL" action has been overhauled to provide support for GET, POST and PUT [request methods](https://en.m.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods), including custom header information. The action also features an easy-to-use way of creating a request body that handles the formatting and escaping of values automatically. This opens your workflows up to all kinds of interactions with many APIs, such as [Stripe](https://stripe.com/docs/api) or [GitHub](https://developer.github.com).

To demonstrate just how powerful this revamped action can be, I've created a few example workflows that leverage some popular APIs. These examples don't perform any sort of error handling, nor do they represent what the limits of Workflow are. Consider these workflows a starting point for building your own.

### A word about API keys

> Keep them secret, keep them safe.  
- Gandalf the Grey hat

Interacting with an API almost always requires some sort of API key or token. This is usually a string of random characters that can be used to directly perform actions on behalf of your account. If someone were to obtain this, they can not only access your account information but also perform actions on your behalf.

If you create a workflow that you want to share, make sure to remove your API key from it beforehand!

### GitHub: Create Gist

[This is a workflow](https://workflow.is/workflows/b261e70134cc468fbe9578050151e1ab) I've always wanted to create, and the new API support makes it possible. [Gists](https://gist.github.com/discover) are great to share small pieces of text information, such as code snippets or scripts. This action extension workflow accepts files of any type (though they must be text-based) and creates a [gist](https://gist.github.com/jordanmerrick/9f619c0aaffffd5bb46fad71e73e1477) using the [GitHub API](https://developer.github.com/v3/gists/).

You need to create a GitHub [personal access token](https://github.com/settings/tokens) before you can use this workflow. GitHub allows you to create multiple access tokens with different permissions. For the purpose of this workflow, I recommend creating a token that can only be used to work with gists.

### Stripe: Get Recent Charges

[Stripe](https://stripe.com) is a payments platform that's built for developers. This workflow retrieves some basic information about the last three charges processed on your Stripe account, such as:

  * Charge ID
  * Amount
  * Last four digits of the card used

To use [this workflow](https://workflow.is/workflows/af24d6a3b7b946a3ac13fa0b628351f4) yourself, include your test or live secret API key, depending on whether you want to retrieve test or live payment information.

### Stripe: Create a Payment

This is an excellent demonstration of Workflow's API support-use Workflow as a point-of-sale device! [This workflow](https://workflow.is/workflows/f64db248caea4b18a8078934b106324f) prompts you to enter credit card information and an amount to charge, along with some additional information, then creates a payment.

![Create a payment on Stripe using Workflow](https://www.jordanmerrick.com/media/stripe-workflow.gif)

A notification is displayed once the payment has been processed and a link to the payment in your Stripe Dashboard is copied to the clipboard.

![A payment created with Workflow](https://www.jordanmerrick.com/media/stripe-workflow.jpg)

### Stripe: Create a Customer

Moving on from creating payments, [this workflow](https://workflow.is/workflows/1d58787867954427a03dc1b59ac0491d) creates a customer object using the information you provide. A link to the customer object in your Stripe Dashboard is also copied to the clipboard.

### Digital Ocean: Create Droplet

Digital Ocean is a cloud computing platform that makes it easy to deploy a server (droplet) in just a few seconds. Using its API, [this workflow](https://workflow.is/workflows/1e7639925e41473ca8ead5eecb80af65) creates a new droplet using the information provided, such as the Linux distribution, how much RAM it should have, and the datacenter location.

### Digital Ocean: Get Droplets Info

[This workflow](https://workflow.is/workflows/8df3b8cb78b545d3874fc110f2992aec) simply retrieves a list of all your current droplets and provides the following information for each:

  * Name
  * ID
  * IP address
  * Status
