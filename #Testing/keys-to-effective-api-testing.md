# Keys to Effective API Testing

_Captured: 2018-09-18 at 07:35 from [dzone.com](https://dzone.com/articles/keys-to-effective-api-testing?edition=397198&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-09-17)_

[Download the blueprint](https://dzone.com/go?i=228233&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) that can take a company of any maturity level all the way up to enterprise-scale continuous delivery using a combination of Automic Release Automation, Automic's 20+ years of business automation experience, and the proven tools and practices the company is already leveraging.

API endpoints make websites work. Simply put, they are the conduits that data moves through. Login functionality? Frequently an API call for authentication. Click on a new section of a webpage? Often an API call for content. Clearly, APIs are a critically important part of any web application. The way that we test these endpoints is incredibly important. At [API Fortress](https://apifortress.com), we like to maintain the best practices that follow for effective API testing.

## **Rule 1: Keep It DRY**

DRY is an acronym for "Don't Repeat Yourself." This simple idea forms a core principle of good programming. When we are writing tests, even in [API Fortress](https://apifortress.com)' visual composer, we're still programming and should make every effort to adhere to the principles of writing good code. Let's say that I have an endpoint that provides user data. The relational database providing the user data has ten entries, and I'd like to write tests to validate the responses when each one of these entries is called. There's no "All Users" route as our organization has no real business need for one. The only way to access the data in each of these endpoints is to send multiple calls, one for each entry in the database. How could we accomplish this without repeating code?

The non-DRY solution to this problem would be to write the request and assertions for each individual user in the user endpoint. This would work, of course. However, if we're talking about an endpoint with ten entries, we're talking about writing the same test ten separate times. If we have 5 assertions in the basic test structure, we're going to be looking at 50 individual assertions.

How can we make this test DRY-compliant? Well, we know that the schema across all users should match. If the schema is the same, then the assertions to validate that schema should also be the same. Instead of rewriting the same test over and over again, we can leverage a loop component from [API Fortress](https://apifortress.com) and iterate over each user in the endpoint. We can pass the list of users as a static dataset (CSV, XML, JSON, etc.) and reference each user without manually rewriting our test. Now our test is nice and DRY.

## **Rule 2: Make Your Intentions Clear**

Rule 1 (Keep it DRY) is an easily defined technical rule. Rule 2 is a bit murkier. When writing API tests, it's important to make your intentions clear so that the next person to use this test knows exactly why you wrote it. This can be done in a number of ways. First, leveraging comment components in [API Fortress](https://apifortress.com) allows us to make our intentions very clear by writing them out in plaintext. Well-documented code is a big part of communicating intent.

## **Rule 3: Treat the API You're Testing Like a Consumer Would**

If you're testing an API, be certain to treat it exactly as the consumer would. Sometimes, in the course of writing test suites, we focus too much on what we know to be the proper response. In order to properly vet our API endpoints, we need to introduce the sort of errors that a user might introduce. For a moment, we need to take off our developer/tester hat and think like the user. After all, things rarely break in predictable ways in a live environment so it's extremely important to test as if we're already there.

## **Rule 4: Eliminate as Many Fixed Data Sources as Possible**

In a live environment, API endpoints often rely on the output from other APIs. The only way to ensure that this relationship is intact is to create an integration test that calls the first API and then leverages the result of that call to hit the second API. When we begin testing the second API with static expected data from the first API, we are no longer testing the environment holistically. Wherever possible, we should be following actual user flows and creating integration tests rather than testing individual endpoints in a vacuum.

Testing is an integral part of the development cycle. Testing API endpoints is an extremely important part of a holistic testing strategy. Unit testing in a development environment is a great place to start, but without testing the interaction between endpoints in a staging or live setting, unforeseen issues can appear in a new release. The rules discussed here are certainly not the only things to consider when developing an API testing strategy, but they're a great jumping off point. Keep testing!

[Download](https://dzone.com/go?i=228234&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) the 'Practical Blueprint to Continuous Delivery' to learn how Automic Release Automation can help you begin or continue your company's digital transformation.

Opinions expressed by DZone contributors are their own.
