# Agile Microservices in Minutes

_Captured: 2018-05-03 at 20:42 from [dzone.com](https://dzone.com/articles/agile-microservices-in-minutes?edition=377203&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-05-03)_

Learn the Benefits and Principles of [Microservices Architecture for the Enterprise](https://dzone.com/go?i=291431&u=https%3A%2F%2Ftransform.ca.com%2FAPI-microservice-architecture-for-the-enterprise.html%3Fcid%3DNA-DSP-API-AEL-000195-00001674-000000492%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dmicroservices_api_acquire%26utm_content%3Dna_eb1-microservice-arch-ent-ddc-preroll%26mrm%3D)

Build out your Agile Stories to deployable Microservices, in as little as minutes, by coupling your Agile Planning with Low-Code Microservices. Here's how, with a non-trivial example.

In this paper, we will address the following:

  1. _Agile Manifesto:_ the key Agile Manifesto tenets of Working Software, as the basis of Customer Collaboration and Response to Change (rapid iteration). It's the right goal, but the key challenge is: How to get Working Software, now?

  2. _Agile, Low-Code Microservices:_ key innovations that deliver Working Software, NOW: an App First approach that creates a system from the envisaged outcome, declarative business logic that links spreadsheet-like rules to Agile stories, and point and click APIs. We will show how these drive Customer Collaboration, and enable us to rapidly respond to change.

  3. _Example:_ how these deliver Microservices in (literally) minutes, instead of weeks. The example is non-trivial: an API to integrate with partners, a user interface, business logic for multi-table derivations and validations, and message-based internal integration.

## Business Agility: Strategic Competitive Advantage

Digital transformation is widely accepted as a requirement for competing successfully in today's app economy. Integrate your systems and Web/Mobile Apps with your business partners and existing systems, in a Modern Software Architecture based on API and Microservice technologies.

But beyond integration, we need Business Agility - _rapid_ innovation to provide new services, sustain engagement, and adapt to business/regulatory change. It's a strategic competitive advantage.

More than incremental improvements to frameworks, wizards, and IDEs, we need something disruptively better.

> "In the future, it will be as easy to create a system as it is to imagine it."   
\- David Shutt 

## Agile Manifesto: Collaborate With Working Software, Iterate Often

The Agile Manifesto makes clear that the first thing we need to do is fundamentally reconsider our approach to developing software. And it's far deeper than moving from waterfall to iterative.

Agile approaches have supplanted previous planning methodologies such as CASE and Rational Unified Process. Let's explore some of the key principles in the Agile Manifesto:

![Image title](https://dzone.com/storage/temp/8255057-agile-manifesto.png)

### Working Software

Getting Working Software, early in the project, sets up the other key tenants of Customer Collaboration and Response to Change, as described below.

### Customer Collaboration Based on Working Software

Instead of technical diagrams (database diagrams, swim lane diagrams, etc.) that Business Users don't understand, Agile values Collaboration based on Working Software. This rings true - experience has shown that operational screens communicate many-fold more effectively than documents or wire-frames. This reduces requirements risk, and promotes business agility.

### Responding to Change: Rapid Iterations 

Waterfall makes fatal assumptions that requirements don't change, and miscommunications are rare. Agile presumes change and miscommunication, so makes rapid iterations part of the process.

### But - Dev Automation?

The approach depends on _Working software_, early in the project. But how do we get that? We need agile _development automation_ to complement and support our agile methodology.

## Agile Low-Code Microservices: Key Innovations

The Agile Process depends on _Customer Collaboration_ based on _Working Software_. We require not only speed, but to use racing parlance, _early speed. _This requires several key innovations over current practice, described in the sections below.

## Working Software NOW - App First, for Outcome-Oriented Collaboration

Customer collaboration is most effective when it is based on Business Users' perspective, not technical artifacts such as database diagrams. We've all had the experience that conversations, documents, diagrams all pale next to a screen. Not just a wire-frame, but _working screens_. It's the outcome we are seeking and dramatically improves collaboration.

Creating screens with hand-coded approaches based on ORMs, routes, and controllers is quite slow, and far too complex for business users. Many have turned to Low-Code approaches.

But even Low-Code approaches require defining a database first, based on abstract concepts such as primary keys, and relationships based on foreign keys. This is still too complex.

Why not make _working screens_ the basis for development? Instead of _database first_, use an _App First_ approach - start with a _running_ (empty) app with facilities to mock up the outcome, and using _that_ to automate the database design.

![Image title](https://dzone.com/storage/temp/8851753-picture1.png)

For example, imagine starting with a running (empty) app, with a button to add a table. We click it, and add the Customer table. The system creates the table with some defaulted fields (e.g., name), the screen fields, and a sample row - all from the_ always-running app_.

More buttons enable us to add fields to the customer table/screen. In the users' mind, there is no distinction between the table and screen - they focus on the business outcome.

Now we add we add an Order grid (list) to our newly created Customer page. It's quite straightforward for the system to infer that Orders has a foreign key to Customers, and create the table - and the foreign key - automatically. We'll see an example of this below.

The result is not a wire-frame, but Working Software: not only the multi-screen User Interface, but also the underlying database schema, and persistence logic. Ready for Business Users to collaborate, so you can "fail fast" and discover issues at the start of the project, not the end.

### Declarative Business Logic

Backend business logic is a significant portion of any app - validations, computations, persistence. Along with integration, it's as much as half a traditional app. It's the iceberg under the surface of an app (or an API).

![Image title](https://dzone.com/storage/temp/8851759-picture2.png)

Low-code approaches often address such logic with Visual Programming. While these are attractive, they don't deal with the scale of logic required since they are _imperative_. Significant agility requires a much more powerful approach: _declarative._

[Wikipedia](https://en.wikipedia.org/wiki/Declarative_programming) defines declarative as expressing _logic without control flow_ - _"what," not "how."_ The most successful application of the concept is Reactive Logic, the conceptual basis for spreadsheets. These express complex logic without control flow, automating dependencies and invocation:

**Logic**

**Declarative**

**Downsides for Declarative**

**Imperative**

**Downsides for**

**Imperative**

**Dependency**

**Management**

Automatically ordered

  


  


Explicitly ordered code

**Maintenance** - new code must be inserted at the proper location, and re-ordered if dependencies changed

  


**Invocation**

Automatically Invoked

  


  


Explicitly Invoked code

**Quality** - bugs can result in failures to call required code

  


**Data Access**

Automatic Persistence

  


Explicit read/write

**Performance** - efficiency is statically baked into the code, unresponsive to changes in schema etc.

**Tedious -** SQL (or equivalent) statements require boring code, and cumbersome mechanisms to integrate into programming paradigmsn (ORMs, etc)

**Extensibility**

Limited to expressions

Not Extensible

Fully Extensible

  


_Table 1 - Declarative Logic vs. Imperative Code._

Spreadsheet-like Reactive Logic can be adapted to the world of databases:

  * Associate derivation rules with database columns, with automated chaining where the execution order is based on system-detected dependencies. To address most real-world problems, these need to include multi-table rules (e.g., "customer balance is the sum of the unpaid order amounts"), with full automation (and optimization) of underlying SQL.
  * Provide multi-column validation expressions for tables (e.g., "balance < credit-limit")
  * Integrate into the API processing, so that all PUTs, POSTs, and DELETEs _automatically_ invoke the underlying derivation and validation logic, in an order that reflects their dependencies.
  * Extensibility, so that Imperative code can be added to integrate existing code, and invoke external services (web services, email, etc.).

Reactive Logic is a major extension to the Low-Code approach. It improves the conciseness of typical database-oriented business logic by a factor of 40 (sic). We'll explore it further in an example, below.

### Responding to Change Through Automatic Invocation and Ordering

Working Software NOW facilitates Customer Collaboration, but another key agile principle is Responding to Change. This is supported by Declarative Reactive Logic: since execution is automatically ordered and optimized, iteration cycles consist of simply altering the rules. The system ensures that your logic is executed, and in the proper order.

## Point-and-Click APIs and Messages

Modern Software Architectures are built to integrate with partner and internal systems using APIs and Messaging. These also form a common backend that supports interactive web and mobile apps. APIs should be automatic, and customizable with point and click, not routes and controllers.

## Customer Collaboration

The Agile Manifesto emphasizes Customer Collaboration as a key element to ensure that systems meet real business requirements. There are several elements to this.

### Business Oriented Focus

As Developers, we must necessarily address dozens of underlying critical technical factors. These include database design (e.g., diagrams), ORM mappings, performance, security, and so on.

Important as these are, _business metaphors_ are critical for collaborating with business users. This means wire-frames and spreadsheet-like logic, not foreign keys and the like.

### Working Software NOW: App First

We noted above that the best basis for collaboration and iteration is Working Software _now_... based on the envisaged outcome, not database internals or non-operational wire-frames.

### Story/Logic Traceability

Agile is strong at capturing requirements that are not visual, as User Stories. For example,

> "As a Business User, I want the system to ensure that the   
customer's balance never exceeds their credit limit."

This is critical system information, both for IT implementers, and collaborative Business Users. Not only should it be captured as part of the system implementation, it should be mapped the Reactive Logic rules that actually implement the requirement. This particular Story maps to these 2 rules:

`"customer balance is the sum of the unpaid order amounts"  
"balance < credit-limit"`

Capturing this mapping facilitates Customer Collaboration with requirements traceability, transparent to both Business Users and IT. It's bi-directional - you can find the rules for a Story, or the Stories for a rule (impact analysis when considering a change). We'll see an example, below.

## Agile Low-Code in Action: Sample Application

Let's use Agile Low-Code Microservices to build a Microservice for a new database. Imagine the Marketing Department needs a system, envisioned wire-frame/Features shown below:

  1. Partners Post APIs representing Conferences, with options for us to sign up for Exhibits (booths) and Talks. These are stored in our (new) database.
  2. The UI shown enables our team to select the Exhibits/Booths we want to "use." The system enforces business logic to ensure their costs do not exceed budget.
  3. When approved, an MQTT or Kafka message is sent to Accounting.![Image title](https://dzone.com/storage/temp/8255132-wire-frame.png)

> _Figure 1 - Marketing System Requirements._

We can build this entire system in 20 minutes using the Agile Low-Code Microservices approach, as follows. To make things definite, we'll be using CA Live API Creator (LAC).

## Working Software NOW: UI/Schema API Creation

We can certainly use existing database tools to create a database, and a screen painter to create a UI. But, this requires a level of expertise that may be unfamiliar to some. And, it's tedious even for experts. It's a technology distraction, relative to the outcome we are seeking.

Working software NOW means we start from the _outcome_, in _business terms_ - the _screen_ that users may use to imagine their system. We create our schema from the API Creation page, by selecting App First.

![Image title](https://dzone.com/storage/temp/9006557-fi2.png)

_Figure 2 - Database Creation._

This opens Data Explorer on an empty screen, with buttons to create tables and fields so we can "sketch" out our app. We begin by adding the Conference table:

![Image title](https://dzone.com/storage/temp/8255136-new-conf-table.png)

> _We can then add fields (like Budget), and a related Talks table as shown below:_

![Image title](https://dzone.com/storage/temp/8255140-schema-creation.png)

_Figure 3 - Schema Creation._

So, by sketching our screen (outcome), we get Working software to facilitate collaboration:

  * A User Interface that is active - it can read and write data
  * A Database, where the system automates clerical details such as keys, AutoNum fields, Foreign Keys, etc. This enables us to focus on the business problem… in business terms (a form)
  * A Default API, matching our schema. This expands the notion of API First to make it an automatic outcome of Working software NOW. We'll see how to customize the "shape" of the API below, for a data independence layer. (Not shown, we can also secure the API so it is available only to authorized roles).

### Alternatively: Start With an Existing Database

Quick aside: while this example is focused on creating a _new_ database, it's often the case to start from an existing database (the first option in Figure 2). In such cases, the system automatically constructs a UI as illustrated below (from familiar Northwind).

![Image title](https://dzone.com/storage/temp/8852253-picture3.png)

This is a remarkably full-featured User Interface, with master/detail, filtering, sorting, updateable grids, screen transitions, etc. Customizations are also supported (we'll explore this in more detail in a future article).

![Image title](https://dzone.com/storage/temp/8255150-default-app.png)

> _Figure 4 - Default App Created From Database._

After default app creation, you can create APIs, Logic, and Integration as described in the following sections. While we won't go into in this paper, a common first step would be to specify authorizations for API access, including fine-grained security down to the row/column level.

## API Creation: Point-and-Click

Database Creation creates a Default API, as for an existing database. But, as shown in Figure 1 (Feature 1), we need to create a _Custom Endpoint_, to match our business agreement with our partners:

  1. A Nested Document (join), with Conferences, Talks, and Exhibits
  2. With mapping and transformation logic to choose the desired fields, and alias them (our API agreement does not match our schema)

Our Data Abstraction layer is point and click: we create a resource, give it a name (PartnerPost), select the tables (joins are created automatically using schema information), and choose/alias our fields, as shown below:

![Image title](https://dzone.com/storage/temp/8255152-api-creation.png)

_Figure 5 - API Creation._

## Create Stories, Import Into LAC

As foreseen by Agile, working software leads to customer collaboration. Part of collaboration is Data Model ("Wait! Customers can have more than 1 address"), which becomes quite apparent via the working software screen. And part of collaboration is the business logic ("Wait! We need to check the Budget!").

These requirements must be captured, prioritized, and formalized. An excellent way to do that is, of course, in an Agile tool, here CA Agile Central:

![Image title](https://dzone.com/storage/temp/8255157-agile-stories.png)

The real power begins with importing these into LAC. Since both products support APIs, we create a simple API to populate LAC Topics (the Story Import API is available from CA). These are shown below as the colored rectangles to the right of our rules. (Of course, we can create Topics manually, directly in LAC).

## Logic Creation: Spreadsheet-Like Declarative Business Logic

As users mark Exhibits and Talks as "Used," we need to roll up their costs to the Conferences, and validate the Budget is not exceeded (see Figure 1, Step 4). Typical multi-table business logic, captured as business rules attached to tables and columns, as shown here:

![Image title](https://dzone.com/storage/temp/8255161-logic.png)

_Figure 6 - Logic._

The colored boxes are Stories. As described above, you can enter them directly, or import them from your Project Management system such as Agile/Central. You then attach them to your rules, providing Requirements Traceability.

Creating the validation rule is simple:

  1. Click Create Rule, and select the "Validation" rule type from the ensuing list (see Figure 7: Select Rule Type), and specify the table (Conferences) for the validation.
  2. Declare the Validation Rule as shown in Figure 8, Validation Rule: 
    * The code is JavaScript. 
      * row represents an altered Conferences row, providing access to fields and related data. It's your Object Model, created and maintained automatically by the system from the schema
      * Since the system knows the fields (columns) in the table, it can provide code completion as illustrated below
    * Rules are invoked automatically on updates. If a validation returns false, the transaction is rolled back, and an exception is returned with the indicated Error Message.
![Image title](https://dzone.com/storage/temp/8255164-rule-type.png)

_Figure 7 - Select Rule Type._

![Image title](https://dzone.com/storage/temp/8255166-validation-rule.png)

_Figure 8 - Validation Rule._

As shown in this example, rules are interdependent: the validation depends on other computed fields, such as the ExhibitsCost. Recall from Figure 6:

The system automatically forward chains updates, even across tables, in an order determined from their dependencies. So, setting an Exhibits to will trigger the ExhibitsCost adjustment, which will trigger the budget check.

We declare the rollup rule as shown below:

  * On the Rules screen (Figure 6), click Create Rule
  * On the ensuing Select Rule Type screen (see Figure 7), select Sum

Enter the Sum rule as shown below:

![Image title](https://dzone.com/storage/temp/8255168-sum-rule.png)

_Figure 9 - Sum Rule._

## Messaging

We're almost done. Our last requirement is to send a message to Accounting when a Conferences row is Approved. We define that as follows:

  * On the Rules screen (Figure 6), click Create Rule
  * On the ensuing Select Rule Type screen (Figure 7), select Event (somewhat like a trigger, except it runs in the middle tier, and is expressed in JavaScript)
  * Messaging is a familiar pattern, so the system provides a Code Example as shown below; we have simply altered it to fit our domain.

Although this is only 5 lines of code, there's a lot going on. We'll review it in a future paper.

![Image title](https://dzone.com/storage/temp/8255172-message-rule.png)

_Figure 10 - Message Rule._

### Low-Code, Not No-Code - Extensibility, Leverage Existing Code

This messaging event illustrates an important point - while Reactive Logic is powerful, there's always something you need to do in code. So, Low-Code via JavaScript.

This not only provides an important extensibility, it enables you to leverage existing software running in the JVM. Server-based JavaScript is able to call out to Java and other code running in the (server-side) JVM.

## Summary: A Modern Software Factory

A Modern Software Factory is not simply a collection of existing tools. It is an _integrated_ set of tools, each providing _automation_ to turn business ideas into outcomes, with unheard-of speed. As shown below, our factory uses well-accepted tools, from Agile Planning to DevOps for Microservices.

This paper has addressed applying automation to the middle build phase. Formerly presumed to require hand-coding, Agile Low-Code introduces automation innovations: an App First approach to create Working Software NOW, and Declarative Business Logic. And it's integrated into your factory, with Agile Story inputs and Microservices outputs.

![Image title](https://dzone.com/storage/temp/8852261-picture4.png)

> _Let's summarize by assessing our:_

  * Outcome - what did we deliver?
  * Agile Mapping - does the process fit well with an Agile Approach?
  * Key Technologies - what's actually different here?

## Business Outcome: Minutes, Not Weeks

The most striking aspect is that we turned our idea into a business outcome in (20) **minutes, not weeks**. Disruptive Business Agility. Our outcome was a Modern Software Architecture: a deployable Microservice, including our API, Logic, UI and Message-based integration:

![Image title](https://dzone.com/storage/temp/8853273-picture5.png)

> _To review, we created a complete Microservice-based system:_

  * We painted our app idea, which created our working UI, database, and default API
  * We declared a Custom Endpoint to handle API requests from Partners
  * We imported our Agile Stories into LAC
  * We declared spreadsheet-like business rules for logic to roll up costs and check budgets
  * We employed a JavaScript event to send a properly formatted MQTT (or Kafka) message to another system

## Agile Approach: Working Software NOW, for Customer Collaboration and Iteration

The core objective of agile is to achieve the correct result, rapidly. We've shown that manual development is slow and complicates Collaboration, but an Agile Microservices approach can bridge the gap:

From CASE to RUP to Agile, a rigorous linkage from planning to development has been elusive.

  


**_Agile_ Low Code **automates significant elements of routine work:

  1. _Architectural:_ common service and persistence elements are automated, freeing you to focus on the logic...
  2. _Logic:_ declared in business-oriented terms, which is significantly more concise and promotes collaboration: 
    1. UI: App First creates working software (screens and databases) from envisaged outcomes
    2. Logic: spreadsheet-like business oriented rules automate invocation, ordering, persistence and optimization, traceable to originating Agile stories
    3. API: Point and Click data abstraction layter for system / mobile app integration
![Image title](https://dzone.com/storage/temp/8979830-agilelowcode.png)

The Agile Low-Code Microservices approach is considerably more than integrating Agile Stories with conventional development approaches and artifacts. Inspired by core tenants of the Agile Manifesto (left column), we've introduced four key innovations that enabled us to deliver our Microservice in minutes:

**Agile Manifesto **

**Low-Code Microservices: Key Innovations**  


  


**App First  
Working Software NOW**

**Declarative Business Logic**

**Point and Click APIs**

**Story / Logic Traceability**

**Working Software**

App First creates running screens and a database, instantly - directly from an envisioned outcome.

  


"Working" includes logic

"Working" includes external systems integration

  


**Customer Collaboration**

Enabled by Working Software NOW

Logic is Transparent to Business Users

  


  


Story Traceability is Preserved over Maintenance

**Responding to Change**

Revise Data Model, Presentation - on the running app

Automated: revised logic is automatically invoked, ordered and optimized

  


  


_Table 2 - Agile Manifesto Principles Inspire Key Innovations for Agile Microservices in Minutes._

![Image title](https://dzone.com/storage/temp/8255107-agile-low-code.png)

In future articles, we'll further explore the details of logic creation and operation, API and Microservice creation, User Interface Creation, and deployment.

### Check It Out

As clear as we've tried to make this description and example, there's never a substitute for hands-on. If you'd like to check out Agile Low-Code Microservices yourself, view [this video](https://vimeo.com/210714207), and obtain a [trial version of CA Live API Creator here](https://www.ca.com/us/products/ca-live-api-creator.html). Within literally minutes, you'll be able to connect to one of your databases, and the created Web App and API.

Microservices for the Enterprise eBook: [Get Your Copy Here](https://dzone.com/go?i=291432&u=http%3A%2F%2Ftransform.ca.com%2FAPI-microservice-architecture-for-the-enterprise.html%3Fcid%3DNA-DSP-API-AEL-000195-00001674-000000493%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dmicroservices_api_acquire%26utm_content%3Dna_eb2-microservice-arch-ent-ddc-postroll%26mrm%3D)

Opinions expressed by DZone contributors are their own.
