# Low-Code Microservices

_Captured: 2017-11-11 at 00:41 from [dzone.com](https://dzone.com/articles/low-code-microservices?edition=334862&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-10)_

Share, secure, distribute, control, and monetize your APIs with the platform built with performance, time-to-value, and growth in mind. [Free 90-day trial](https://dzone.com/go?i=231226&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Ftechnologies%2Fjboss-middleware%2F3scale%2Fget-started%3Fsc_cid%3D701f2000000h30LAAQ) of 3Scale by Red Hat

Below, we'll show you how to create a complete microservice - including API and messaging, business logic, UI, even a new database - in minutes rather than weeks. Check out this low-code approach that offers a much quicker way for creating enterprise-class microservices and see if it might be right for you.

## Requirements

Microservices have become an accepted approach for driving value, both for IT and for the business. Let's identify some of the main drivers.

**Key Requirement**

**Approach**

**Notes**

**Digital Transformation**

Microservices

Microservices are synonymous with APIs and Messaging -providing the connectivity fundamental to Digital Transformation.

  


**Business Agility**

Microservices,

Low-Code

Microservices are all about speed: break down the monolith so that new ideas can be brought to market, and changes can be developed and deployed.

  


Low-Code increases velocity by automating common patterns.

  


**Simplicity**

Low-Code

Business Agility is multiplied by not only reducing the time, but also by increasing simplicity.

  


Low-Code targets this: more people, moving faster.

  


**IT Standards**

Standards

Low-Code systems must deploy using standard approaches, enforce security, integrate with existing systems and assets, and monitor performance.

  


**IT Governance**

Automation

Low-Code must maintain / improve the ability to ensure data integrity and security, and verify compliance.

## Creating Low-Code Microservices

Microservices are required for existing systems and new ones. So, a Low-Code Microservice needs to support multiple methodologies, as shown here:

![Figure 1 - Creating API Services](https://dzone.com/storage/temp/7137497-1.png)

> _Figure 1 - Creating API Services_

The most common scenario is a Microservice for (perhaps part of) an existing system (path 1 in the Figure above). Let's explore the process; to make it concrete, we will illustrate using CA's Live API Creator.

### 1\. Create an API from the APIs Screen 

![Image title](https://dzone.com/storage/temp/7137503-2.png)

> _Figure 2 - API Creation from Existing Databases_

### 2\. Select Your Database Type, and Supply the Credentials for Your Existing Database

![Image title](https://dzone.com/storage/temp/7137509-3.png)

> _Figure 3 - Database Connection_

### 3\. API Created from Schema

The system scans your schema, and creates a default API with an endpoint for each table, view and stored procedure:

![Image title](https://dzone.com/storage/temp/7137510-4.png)

> _Figure 4 - Default API Creation_

### 4\. Test Ready

No code generation, no deploy - the API can be tested instantly using a cURL-like interactive screen, as shown below. The API is enterprise-class: standard verbs (Get, Put, Post, Delete), with filtering and sorting. Pagination and Optimistic Locking are built in, along with full Swagger documentation.

![Image title](https://dzone.com/storage/temp/7137660-5.png)

> _Figure 5 - Testing your API_

### 5\. Declare Custom Endpoints for a Data Abstraction Layer

In most cases, you don't want to simply expose your schema - you want a secured Data Abstraction Layer. Use Security to designate which endpoints can be accessed for which Roles, and define Custom Endpoints.

Creation is point and click; we'll examine it in just a moment. In a typical Microservices environment, you'd likely expose just a few Custom Endpoints. You can also define cross-database joins to integrate multiple databases.

### 6\. Declare Logic and Security

As noted in Figure 1 ("API Creation"), you also use this Declare / Extend approach declare the logic and row/column security for your API. Your logic is expressed in spreadsheet-like rules. Your logic and security is defined for tables, and is automatically re-used over all Custom Endpoints.

Logic is extensible by server-side JavaScript. This enables you to invoke SQL, Web Services, and existing Java / JavaScript code). We'll also explore this shortly.

### 7\. Automatic Web App

API Creation also builds customizable Web App, called Data Explorer. It is suitable for testing, prototyping, and back office data maintenance. While Low-Code Microservices focuses primarily on creating a Microservices middle tier, this can eliminate significant client development effort, as well:

![Image title](https://dzone.com/storage/temp/7137675-6.png)

> _Figure 6 - Data Explorer_

## Sample Application

Now let's consider a service that requires a new database. You can use your existing database tools to create new databases, and proceed as noted above.

But, this requires a level of database expertise that is frequently not necessary and may be unfamiliar to some. And, it's tedious even for experts. This does not meet our Simplicity objective.

In many cases, Business Users view systems not as abstract diagrams (e.g., database diagrams), but as screens. So, the customization services in the Data Explorer also enable you to create your schema, requiring only familiar _business_ metaphors such as Master/Detail and Lookup.

To illustrate, imagine the Marketing Department needs a system with the UI below:

  * Partners Post APIs representing Events (conferences), with options for us to sign up for Exhibits (booths) and Talks
  * These are stored in our (new) database
  * The UI shown enables our team to select the Exhibits/Booths we want
  * The system enforces business logic to ensure these do not exceed budget
  * When approved, an MQTT or Kafka Message is sent to Accounting
![Image title](https://dzone.com/storage/temp/7137676-7.png)

> _Figure 7 - Marketing System Requirements_

We can build this entire system in 20 minutes using a Low-Code Microservices approach, as follows.

### UI / Schema Creation

Referring to Figure 2, we instead choose the "App First" option. This opens Data Explorer on an empty screen, with buttons to create tables and fields. Here is a screen showing the process:

  * We've already created the Events Table
  * And some Fields (like Budget)
  * We are now creating the Talks table

Throughout the entire process, the system automates clerical details such as keys, AutoNum fields, Foreign Keys, etc. This enables us to focus on the business problem… in business terms (a form).

![Image title](https://dzone.com/storage/temp/7137678-8.png)

> _Figure 8 - Schema Creation_

### API Creation

Database Creation creates a Default API, as for an existing database. But we need to create a _Custom Endpoint_, to match our business agreement with our partners:

  * A Nested Document (join), with Events, Talks, and Exhibits
  * With mapping and transformation logic to choose the desired fields, and alias them (our API agreement does not match our schema)

Our Data Abstraction layer is point and click: we create a resource, select the tables (joins are created automatically using schema information), and choose/alias our fields.

![Image title](https://dzone.com/storage/temp/7137679-9.png)

Figure 9 - API Creation

### Logic Creation

As users mark Exhibits and Talks as "Used", we need to roll up their costs to the Events, and validate the Budget is not exceeded. Typical multi-table business logic, captured as business rules attached to tables and columns, as shown here:

![Image title](https://dzone.com/storage/temp/7137680-10.png)

Figure 10 - Logic

The colored boxes are requirements. You can enter them directly, or import them from your Project Management system such as Agile/Central. You then attach them to your rules, providing Requirements Traceability.

Creating the validation rule is simple:

  1. Click Create Rule, and select the "Validation" rule type from the ensuing list (see Figure 11: Select Rule Type)
  2. Declare the Validation Rule as shown in Figure 12, Validation Rule: 
    1. The validation is attached to a table, here the Events table
    2. The code is JavaScript. 
      1. row represents an altered Events row, providing access to fields and related data. It's your Object Model, created automatically created by the system from the schema
      2. Since the system knows the fields (columns) in the table, it can provide code completion as illustrated below
    3. Rules are invoked automatically on updates. If a validation fails, the transaction is rolled back, and an exception is returned with the indicated Error Message
![Image title](https://dzone.com/storage/temp/7137546-12.png)

> _Figure 11 - Select Rule Type_

![Image title](https://dzone.com/storage/temp/7137547-12a.png)

> _Figure 12 - Validation Rule_

As shown in this example, rules are interdependent. The system automatically forward chains updates, even across tables, in an order determined from the dependencies.

We declare the rollup rule shown below so that when, for example, an Exhibits' Use flag is set to true, the Events' ExhibitsCost is incremented (and the Budget is checked):

  * On the Rules screen (Figure 10), click Create Rule
  * On the ensuing Select Rule Type screen (see Figure 11), select Sum
  * Enter the Sum rule as shown below
![Image title](https://dzone.com/storage/temp/7137548-13.png)

Figure 13 - Sum Rule

### Messaging

We're almost done. Our last requirement is to send a message to Accounting when an Event row is Approved. We define that as follows:

  * On the Rules screen (Figure 10), click Create Rule
  * On the ensuing Select Rule Type screen (Figure 11), select Event (somewhat like a trigger, except it runs in the middle tier, and is expressed in JavaScript)
  * Messaging is a familiar pattern, so the system provides a Code Example as shown below; we have simply altered it to fit our domain.

Although this is only 5 lines of code, there's a lot going on. We'll review it in a future article.

![Image title](https://dzone.com/storage/temp/7137682-14.png)

> _Figure 14 - Message Rule_

## Summary - Completed in 20 minutes

So, to review, to create our Microservice-based system:

  1. We painted our app idea, which created our UI and database
  2. We declared a Custom Endpoint to handle API requests from Partners
  3. We declared spreadsheet-like business rules for logic to roll up costs and check budgets
  4. We employed a JavaScript event to send a properly formatted MQTT (or Kafka) message to another system

Let's review how our Low-Code Microservices creation approach addressed the Business and IT requirements we laid out:

**Key Requirement**

**Approach**

**Notes**

**Digital Transformation**

Microservices

Our system provided **APIs** to accept in-coming Events, and **Messaging** for Accounting integration. A classic Digital Economy system.

  


**Business Agility**

Microservices,

Low-Code

This system was created in **20 minutes**, rather than weeks. It contained 5 lines of code.

  


See a summary in this [3-minute video](https://vimeo.com/239259439).

  


**Simplicity**

Low-Code

Low-Code **automated** low-level details like SQL, routes and controllers, logic dependencies, enabling us to operate at a business level of abstraction.

  


**IT Standards**

Standards

The resultant system is a fully **standard** Microservice - standard database access, APIs, Messaging, and deployment-ready for cloud/on premise, Web Servers, App Servers, Docker Containers, etc.

  


**IT Governance**

Automation

Our data integrity logic is** active** - automatically invoked on all API requests. And it's **transparent **- easily reviewed by IT and Business Users.

  


In future articles, we'll further explore the details of logic creation and operation, API and Microservice creation, and deployment. If you'd like to check it out yourself, you can obtain [a trial version here](https://www.ca.com/us/products/ca-live-api-creator.html).

Explore the core elements of owning an API strategy and best practices for effective API programs. [Download](https://dzone.com/go?i=231227&u=https%3A%2F%2Fengage.redhat.com%2F3scale-api-owners-s-201706160312%3Fsc_cid%3D701f2000000h30LAAQ) the API Owner's Manual, brought to you by 3Scale by Red Hat

Opinions expressed by DZone contributors are their own.
