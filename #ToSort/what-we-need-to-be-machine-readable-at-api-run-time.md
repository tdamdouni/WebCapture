# What We Need to Be Machine Readable at API Run Time

_Captured: 2018-03-08 at 14:04 from [dzone.com](https://dzone.com/articles/what-we-need-to-be-machine-readable-at-api-run-tim?edition=366219&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202018-03-08)_

The Integration Zone is brought to you in partnership with [Cloud Elements](https://dzone.com/go?i=263425&u=https%3A%2F%2Fresources.cloud-elements.com%2Febooks-private%2Fguide-to-api-integrations-ebook%3Futm_campaign%3DAPI%2BIntegration%2BeBook%26utm_medium%3Ddisplay%26utm_source%3Ddzone). What's below the surface of an API integration? Download [The Definitive Guide to API Integrations](https://dzone.com/go?i=263425&u=https%3A%2F%2Fresources.cloud-elements.com%2Febooks-private%2Fguide-to-api-integrations-ebook%3Futm_campaign%3DAPI%2BIntegration%2BeBook%26utm_medium%3Ddisplay%26utm_source%3Ddzone) to start building an API strategy.

I had breakfast with Mike Amundsen ([@mamund](https://twitter.com/mamund)) and Matt McLarty ([@MattMcLartyBC](https://twitter.com/MattMcLartyBC)) of the CA API Academy team this morning in midtown. As we were sharing stories of what each other was working on, the topic of what is needed to execute an API call came up. Not the time consuming find an API, sign up for an account, figure out the terms of service and pricing version, but all of this condensed into something that can happen in a split second within applications and systems.

How do we distill down the essential ingredients of API consumption into a single, machine-readable unit that can be automated into what Mike Amundsen calls, "find and bind." This is something I've been thinking a lot about lately as I work on my API discovery research, and there are a handful of elements that need to be present:

  * **Authentication** \- Having keys to be able to add authentication.
  * **Surface Area** \- What is the host, base URL, path, headers, and parameters for a request?
  * **Terms of Service** \- What are the legal terms of service for consumption?
  * **Pricing** \- How much does each API request cost me?

We need these elements to be machine readable and easily accessible at discover and runtime. Currently, the surface area of the API can be described using OpenAPI, that isn't a problem. The authentication details can be included in this, but it means you already have to have an application setup, with keys. It doesn't include new users in the equation, meaning discovering, registering, and obtaining keys. I have a draft specification I call "API plans" for the pricing portion of it, but it is something that still needs a lot of work. So, in short, we are nowhere near having this layer ready for automation-which we will need to scale all of this API stuff.

This is all stuff I've been beating a drum about for years, and I anticipate it is a drum I'll be beating for a number of more years before we see it come into focus. I'm eager to see Mike's prototype on "find and bind," because it is the only automated, runtime, discovery, registration, and execute research I've come across that isn't some proprietary magic. I'm going to be investing more cycles into my API plans research as well as the terms of service stuff I started way back when alongside my API Commons project. Hopefully, this will move all this forward another inch or two, and flesh out more of the machine-readable components we'll need at this layer.

Your API is not enough. Learn why (and how) leading SaaS providers are turning their products into platforms with API integration in the ebook, [Build Platforms, Not Products](https://dzone.com/go?i=263426&u=https%3A%2F%2Foffers.cloud-elements.com%2Fbuild-platforms-not-products-ebook%3Futm_campaign%3DPlaforms%25252C%252520Not%252520Products%252520eBook%26utm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_content%3Dtext) from Cloud Elements.
