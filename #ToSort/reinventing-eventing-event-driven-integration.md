# Reinventing Eventing: Event-Driven Integration

_Captured: 2018-05-17 at 20:33 from [dzone.com](https://dzone.com/articles/reinventing-eventing-event-driven-integration?edition=376317&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202018-05-17)_

One of the most common customer use cases that I encountered while on our Sales Engineering team was _the ability for our customer's application to detect and react to changes in a given endpoint service_ -- such as a when a new contact is added in Hubspot or an invoice is updated in Quickbooks. Then, subsequently retrieving that newly added or updated information from the endpoint -- allowing our customer's application to keep that data in sync.

If you have a SaaS application and need to interact with data contained in external services that your customers are using, you have two choices to react to changes in those external services:

  1. Have the endpoint service tell you when a change happens
  2. Ask the endpoint what has changed since the last time you asked it

Which choice you select depends on what the endpoint supports ... or does it?

## Choice #1: Webhooks

If an endpoint supports webhooks, it can notify you in near real-time when a change happens. This is the best case scenario as your application doesn't have to react to changes until they happen. Kinda like when CNN pushes information to my cell phone as a news event unfolds, I don't have to go to the CNN website and look for changes. Nice and convenient, and it saves me time and also battery cycles.

### **So, What Exactly Is a Webhook?**

It is a "reverse API" where an HTTP callback is triggered when a change event, such as an update or delete, occurs for a given data element within the endpoint service. E.g. Shopify can call your application using a webhook when a customer has been added, updated, or deleted.

What makes webhooks so useful is that your application is only notified when the data object for the customer you care about changes, otherwise, the link is quiet. You can even set the exact callback URL for the webhook to use, allowing you to receive it how and where you want it, even per customer if you so choose. A payload with a subset of the changed information is included with the callback from a webhook -- super handy for keeping data in sync!

Is there a downside to using webhooks? Yes, there are three. First, not all endpoint services support webhooks. In fact, I chatted with one of our most experienced Element builders here at Cloud Elements, and his conclusion was that very few, perhaps less than 30%, of the endpoints that he's encountered support webhooks natively in their API. Second, the payload in the webhook, e.g. information for a contact that was added, will vary by endpoint, meaning you'll have to map it to a format reflecting how your application expects to digest it. Third, in some cases (e.g. [Salesforce Sales Cloud](https://trailhead.salesforce.com/en/modules/platform_events_basics)), setting up webhooks and subscribing to events requires your application to place a small amount of code directly in the endpoint service itself, on a per customer basis, which is not always convenient.

## Choice #2: Pollers

What if the endpoint service doesn't support webhooks? In this case, you will need to periodically ask the endpoint, "Has anything changed recently that I care about?" This is referred to as _Polling_ -- writing a query to periodically check for changes. Easy-peasy, right?

Well, easy on paper anyway.

Why? Because there are complexities with polling that you have to accommodate for, such as:

  * Varying query or search APIs; some have /search or /filter resources, and most support filtering results via a query parameter, e.g. /contacts?modified_date>=1521491467
  * Like webhooks, the data payload returned from the query will be unique and specific to a given endpoint, thus you'll have to map it to your data object
  * Maintaining state regarding what parameters you used the last time you queried - the "recently" part of the query

Thus, to support polling, you need to build a polling framework and use custom, endpoint specific code to manage through each endpoint's nuances. Not as easy as webhooks, for sure.

![Image title](https://blog.cloud-elements.com/hs-fs/hubfs/Polling%20vs%20Cloud%20Elements%20timeline.png?t=1525828768296&width=724&height=666&name=Polling%20vs%20Cloud%20Elements%20timeline.png)

What else do I need for events?

For each endpoint that your application integrates to, regardless of whether you are able to leverage webhooks or install a polling framework, you will need to consume the event data in a way that is useful to your application.

Your application will need to map and/or translate the endpoint specific data fields and associated values to the name and format structures that your application can handle. The examples shown in the table below are portions of an event payload that were returned from two endpoints as a result of polling for changes. These will need to be deciphered and mapped to the data structure required by your application.

**Salesforce: Updated Contact (Via Polling):**

**MS Dynamics: Created Contact (Via Polling):**

## **"What If" Scenarios**

  1. What if every endpoint returned a webhook?
  2. What if you didn't have to worry about endpoint specific API search nuances?
  3. What if every endpoint had a common payload in the received event payload?

Within the Cloud Elements platform, our Elements address EACH of these "what if's" out of the box, providing a consistent developer experience across every endpoint.

### What If #1

Every Element ([our prebuilt connectors](https://developers.cloud-elements.com/docs/quickstart/overview.html#element)) is capable of returning a webhook to a URL of your choice -- settable on a per customer authenticated connection basis -- _even if the endpoint doesn't support webhooks natively_. You can say that we "webhookify", or make every endpoint appear like it has webhooks natively, even if they don't! Yes, you read that correctly.

Note, however, that our platform uses polling behind the scenes in this case, and thus our callback will not be as real-time as a native webhook would be, you'll receive it based on how you set the polling frequency.

For example, for each customer credentialed connecter or authenticated Element [instance](https://developers.cloud-elements.com/docs/quickstart/overview.html#authenticated-element-instance), you can set the call back by customer:

**Set Callback Via UI, Per-Instance:**

![Image title](https://blog.cloud-elements.com/hs-fs/hubfs/Screen%20Shot%202018-03-22%20at%208.55.25%20AM.png?t=1525828768296&width=713&height=232&name=Screen%20Shot%202018-03-22%20at%208.55.25%20AM.png)

**Set Callback Via API, Per-Instance:**

For specifics on how to trial Cloud Elements and use our Eventing framework, consult pages 13 and 14 in [this tutorial](https://resources.cloud-elements.com/cloud-elements-how-tos/guide-to-cloud-elements-trial-contact-sync).

### What If #2

Every one of our Elements (currently over 130 in our public catalog) utilizes our [CEQL search](https://blog.cloud-elements.com/how-our-ceql-compares-to-sql-queries) capabilities and accommodates query or search nuances. Meaning, we preset the poller search query using our built-in _where_ clause (via CEQL) to search for and return the created, updated, or deleted data in the endpoint. In the event (pun intended) that you don't like how we configured the poller query, you can adjust these event query payloads and customize as needed.

**Quickbooks: preset "click to toggle" objects to receive change events:**

![Image title](https://blog.cloud-elements.com/hs-fs/hubfs/Screen%20Shot%202018-03-22%20at%208.56.35%20AM.png?t=1525828768296&width=208&name=Screen%20Shot%202018-03-22%20at%208.56.35%20AM.png)

**Edit Each Object Poller Query to Customize if Needed**

### What If #3

Every Element has a JSON payload that is returned in the webhook event payload. This contains both the native data fields from the endpoint AND a standardized set of event variables that you can count on being there for each and every payload. Thus, your developer can code to a standard rather than having to create and maintain endpoint specific field mapping code.

**Event from Salesforce: Standardized Portion Added by Cloud Elements:**

**Event from Dynamics: Standardized Portion Added by Cloud Elements:**

With the Cloud Elements platform, you don't have to choose when it comes to leveraging Events in support of keeping data in sync between your app and a given endpoint. In fact, you don't even need to know how events are defined for a given endpoint -- we've done that for you and will always provide a webhook with standardized information returned in the Event payload.

Just think of how many sprint cycles reading this blog just saved your company!

Enjoy. Aloha.

## The 2018 State of API Integration Report

Last year, the State of API Integration Report was our first inaugural research report that sought to sort through the proliferation of APIs setting the benchmark for our research on API integration. [T](https://offers.cloud-elements.com/the-state-of-api-integrations-report-2018?_ga=2.258694922.1851711976.1524499772-360051633.1522435897)[his year's report](https://offers.cloud-elements.com/the-state-of-api-integrations-report-2018) builds on observations from 2017, with the help of over 400 API enthusiasts who took the State of API Integration Survey at the end of last year.

With over [60%](https://offers.cloud-elements.com/the-state-of-api-integrations-report-2018) of the respondents agreeing that API Integration is **critical** to their business strategy, our report focused in on four key trends:

  1. When **building a platform strategy** \- how can you drive new revenue opportunities or deliver value through API integration.
  2. By understanding **drivers of adoption**, you can change how developers and end-users consume APIs and integration services.
  3. The **strategic shift of integration** has widely been driven by enterprise applications, like Enterprise Resource Planning (ERP).
  4. An **evolution of B2B integration** has organizations evolving the way they share and synchronize data with partners.

With expert contributions and insights from:

  * **Ross Garrett, VP of Marketing at Cloud Elements**
  * **Kin Lane, The API Evangelist**
  * **Isabelle Mauny, co-founder and CTO of 42Crunch**
  * **Mark Boyd, API Industry Analyst and Founder of Platformable**

The comprehensive research covers sections including a breakdown of the data, trends, common API business models, and event-driven integration. [Download it here](https://offers.cloud-elements.com/the-state-of-api-integrations-report-2018) to receive the report directly to your inbox.
