# CQRS: Understanding From First Principles

_Captured: 2018-03-14 at 15:56 from [dzone.com](https://dzone.com/articles/cqrs-understanding-from-first-principles?edition=368193&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=microservices%202018-03-14)_

Learn the Benefits and Principles of [Microservices Architecture for the Enterprise](https://dzone.com/go?i=274453&u=http%3A%2F%2Ftransform.ca.com%2FAPI-microservice-architecture-for-the-enterprise.html%3Fcid%3DNA-DSP-API-AEL-000195-00001674-000000492%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dmicroservices_api_acquire%26utm_content%3Dna_eb1-microservice-arch-ent-ddc-preroll%26mrm%3D)

There seems to be no end to the choices you have for architecture when building an application. You don't want to fall victim to [cargo cult programming](https://blog.ndepend.com/cargo-cult-programming/), so you need to truly understand the options available. Today, we'll focus on one option, called CQRS.

CQRS leads to a clean architecture that's easy to maintain. Let's take a look at the underlying principles of CQRS. This will help you understand what the benefits are and whether you want to use it in your applications.

## CQRS Principle: Separate Commands From Queries

CQRS stands for command query responsibility segregation. What does that mean? In a nutshell, it's an architectural pattern that separates the application layer of your software into a command stack and a query stack. It was first described in the book _[Object-Oriented Software Construction_](https://www.amazon.com/gp/product/0136291554) by Bertrand Meyer.

Meyer stated that there are two types of methods in object-oriented software:** commands** and **queries**. Commands are operations that change the application state and return no data. These are the methods that have side effects within the application. Queries are operations that return data but don't change application state.

In concrete terms for .NET developers, your application will have two "stacks," or namespaces. One namespace will be _YourApplication.CommandStack _and the other _YourApplication.QueryStack_. This structure gives you a clear picture of what pieces of code change the state of the application. If you like to think of software in terms of domain models, this structure has two of them-a query model and a command model. These are different models that have their own operations and representations of data. These representations can then be optimized for their specific purpose. (More on that later.)

Changes to data tend to cause the most bugs. Having a clear understanding of which parts of the application change data and which do not will help with maintainability and debugging.

## CQRS Principle: Build SOLID Software

[SOLID](https://en.wikipedia.org/wiki/SOLID_\(object-oriented_design\)) is a set of object-oriented software principles that are expressed quite well in the CQRS architecture.

CQRS states that commands need to be separate from queries. Methods that have surprise side effects are not welcome. A method does one thing and one thing only, either returning data or changing it. Thus, CQRS is a great expression of the single responsibility principle.

Without this separation of commands and queries, you may end up with domain models that are full of state, commands, and queries that make them much harder to reason about and maintain over time.

The interface segregation principle states that many client-specific interfaces are better than one general-purpose interface. CQRS forces you to define clear interfaces between the parts of the system. The client talks to either a command interface or a query interface. There's a clear distinction and choice for the client. Therefore, the client knows exactly what to expect.

## CQRS Principle: Optimize for Your Specific Situation

One of the great parts of using CQRS in your application is the choices it enables. The flexibility gained by separating commands and queries allows for specific optimization of different parts of the application based on your needs. Let's take a look at three examples of this.

### Basic CQRS

First, following basic CQRS design allows for optimization of reads and writes. The design of the query stack represents the most efficient way to read data. The command stack only needs to worry about how to write data. Basic CQRS typically shares one database between both the command and query models.

### CQRS with Two Databases

However, you can take optimization a step further by creating your application with two databases: a read database and a write database. Use a relational data store that's optimized for writing on the command side. Use a denormalized or NoSQL data structure on the query side to make reads from the read database as fast as possible. Since most applications read data much more often than they write data, this separation and subsequent optimization makes a ton of sense in many applications. If your applications require high performance at all times, this variation of CQRS will allow you to highly optimize the command and query models for optimum performance.

### Event Sourcing CQRS

Event sourcing CQRS involves storing all changes to an object as a series of events in an event store. The write side replays the events of a particular object to derive the current state of the object. The read side database holds the current state of all objects for fast reading of data. Event sourcing CQRS is the most complex option.

Event sourcing CQRS provides several strong benefits, despite the added cost. First, the event store acts as an audit trail for the entire system. Heavily regulated industries will find this feature quite useful. Second, you can always recreate the state of any object by replaying the event store. If your production read database is destroyed somehow, use the event store to recover in a fraction of the time. Third, the event store can feed its data into multiple read databases. The query code chooses which data store to use for any given situation. For example, you could populate graph databases, OLAP cubes, search indexes, and any other store you need.

## Do You Need CQRS in Your Application?

Even though CQRS sounds impressive, caution is in order. CQRS is a software design pattern. It's great to have in the toolbox, but it may not be applicable to every situation. Don't make the mistake of applying this one pattern to every application you build. A skilled software engineer or architect will carefully determine where this pattern fits. Let's take a look at some guidelines of where you can use this pattern.

CQRS fits best in [domain-driven design](https://en.wikipedia.org/wiki/Domain-driven_design) (DDD) architectures. DDD focuses on building rich domain models to capture complex business logic. Use it within certain bounded contexts to help simplify the models. Having a command model and query model can help to simplify each model so they don't grow too large. On the other hand, be careful not to introduce it into contexts where the command and query models end up sharing similar functionality. In these cases, it will add complexity to try to separate the models. Just use one.

Using CQRS with event sourcing (CQRS/ES) is a natural fit for applications that depend greatly on events. For instance, if you own a downstream service that responds to events from a UI or other system, you can use CQRS/ES to keep track of all events and thus reconstruct the domain at any point in time by reading the events. The API exposed to the users of the service will be simple and clean.

## Use Your Tools Skillfully

You can find a good review of CQRS and its benefits and challenges at [Martin Fowler's blog](https://martinfowler.com/bliki/CQRS.html). In a nutshell, remember that it brings great benefits:

  * Smaller models that handle either commands or queries.
  * Simpler API for the consumers of the service
  * The ability to optimize the read and write sides for your specific needs (domain models and data sources)

However, realize that CQRS also adds complexity. More advanced applications require the use of multiple data stores. Those data stores and the domain models at runtime have to be kept in sync. Even skilled teams can have trouble if it's used in the wrong applications. CQRS is a scalpel, not a machete. Use it skillfully, carefully, and in the right contexts, and you'll greatly improve the maintainability and performance of your applications.

Microservices for the Enterprise eBook: [Get Your Copy Here](https://dzone.com/go?i=274454&u=http%3A%2F%2Ftransform.ca.com%2FAPI-microservice-architecture-for-the-enterprise.html%3Fcid%3DNA-DSP-API-AEL-000195-00001674-000000493%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dmicroservices_api_acquire%26utm_content%3Dna_eb2-microservice-arch-ent-ddc-postroll%26mrm%3D)
