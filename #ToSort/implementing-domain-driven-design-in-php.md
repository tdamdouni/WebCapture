# Implementing Domain-Driven Design in PHP

_Captured: 2017-04-20 at 13:40 from [dzone.com](https://dzone.com/articles/implementing-domain-driven-design-in-php?oid=twitter&utm_content=buffer50eb0&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Domain-Driven Design is a software development methodology for tackling complex software projects to deliver an end-product that meets the goals of the organization. In fact, Domain-Driven Design promotes focusing the project on an evolving core model.

It will teach you how to effectively model the real world in your application and use OOP to encapsulate the business logic of the organization.

## What is a Domain Model?

In my opinion, a Domain Model is your perception of the context to which it applies. Let me describe it a bit more. 'Domain' itself means the world of the business you are working with and the problems they want to solve. For example, if you want to develop an app for online food delivery, your domain will be everything (problems, business rules, etc.) about online food delivery that needs to be done in your project.

The Domain Model is your structured solution to the problem. The Domain Model should represent the vocabulary and key concepts of the problems of the domain.

## Ubiquitous Language:

'Ubiquitous Language' is the language that is used by business experts to describe the Domain Model. It means that the development team uses the language consistently in all communications, and also in the code. This language should be based on the Domain Model. Let me give an example:

In the code above, I create a new product, but in the application, the product must be added, not created:

In a development team, if someone creates a product and someone else adds a product, this will violate ubiquitous language. In this case, if in the product add method we have some extra actions such as sending emails, they all will be missed, and also the definition of adding a product in the team will change. We would have two different definitions for one term.

## Layered Architecture:

In this article, I am not planning to talk about object-oriented design. But Domain-Driven Design proposes the fundamentals of a good design. Eric Evans believes:

> Developing a good domain model is an art.

In order to develop a good domain model, you need to know about Model-Driven Design. The connection of the model and the implementation is called Model-Driven Design. The Layered Architecture is one of the Model-Driven Design blocks.

Layered Architecture is the idea of isolation of each part based on years of experience and convention. The Layers are listed below:

  * User Interface
  * Application Layer
  * Domain Layer
  * Infrastructure Layer

The **User Interface** is responsible for showing information to the user and interpreting the user's commands. In Laravel, the view is the User Interface (presentation) Layer.The **Application Layer** is the way we communicate with the world outside (out of the application domain). This layer behaves as a public API for our application. It does not contain business rules or knowledge. Controllers in Laravel are located here.

The **Domain Layer** is the heart of business software. This layer is responsible for representing the concepts of the business, information about the business situation, and business rules.The **Infrastructure Layer** provides generic technical capabilities that support the higher layers and also support the pattern of interactions between the four layers (that is why repositories are located in this layer).

The connection between layers is mandatory, but without losing the benefit of the separation. The connection would be in one direction. As you see in the schema above, the upper layers can communicate with lower layers. If the lower layers need to connect with an upper layer, they must use patterns such as callbacks or observers.

## Value Objects and Entities:

I'm a big fan of Value Objects. I think they are the heart of OOP. Though they seem simple, DDD value objects are a serious point of confusion for many, including me. I've read and heard so many different ways of describing value objects from a variety of perspectives. Luckily, each of the different explanations, rather than conflicting with one another, helped me build a deeper understanding of value objects.

Value objects are accessible by their value rather than identity. They are immutable objects. Their values don't change (or change rarely) and have no lifecycle (it means they are not just like a row of your database table that can be deleted), such as currencies, dates, countries, etc.

You may create value objects that you do not recognize as value objects. For example, an email address could be a string, or it could be a value object with its own set of behaviors.

The code below is a sample value object class:

Entities are objects that are accessible with an identity in our application. Exactly, in fact, an entity is a set of properties that have a unique identifier. A row of database tables would be a good example. An entity is mutable, because it can change its attributes (usually with setters and getters) and also it has a lifecycle, meaning it can be deleted.

Does an object represent something with continuity and identity -- something that is tracked through different states or even across different implementations? Or is it an attribute that describes the state of something else? This is the basic distinction between an **Entity** and a **Value Object**.

## Aggregates:

A model can contain a large number of domain objects. No matter how much consideration we put into modeling a domain, it often happens that many objects depend on one another, creating a set of relationships, and you cannot be 100% sure about the result. In other words, you should be aware of the business rule that must always be consistent in your domain model; only with that knowledge can you reason about your code with confidence.

Aggregates help to reduce the number of bidirectional associations among objects in the system because you are allowed to store references only to the root. That significantly simplifies the design and reduces the number of blindsided changes in the object graph. On the other hand, aggregates help with decoupling of large structures by setting rules for relations between entities. (Note: Aggregates can also have properties, methods, and invariants that don't fit within one single class)

In order to implement aggregates in our applications, Eric Evans has set some rules in his book, and I list them below:

  * The root entity has a global identity and is ultimately responsible for checking invariants.
  * Root entities have a global identity. Entities inside the boundary have a local identity, unique only within the aggregate.
  * Nothing outside the aggregate boundary can hold a reference to anything inside, except to the root entity. The root entity can hand references to the internal entities to other objects, but those objects can only use them transiently, and may not hold on to the reference.
  * As a corollary to the above rule, only aggregate roots can be obtained directly with database queries. All other objects must be found by traversal of associations.
  * Objects within the aggregate can hold references to other aggregate roots.
  * A delete operation must remove everything within the aggregate boundary at once (with garbage collection, this is easy. Since there are no outside references to anything but the root, delete the root and everything else will be collected).
  * When a change to any object in the aggregate boundary is committed, all invariants of the whole aggregate must be satisfied.

## Factories:

In the OOP world, a Factory refers to an object that has the single responsibility of creating other objects. In Domain-Driven Design, Factories are used to encapsulate the knowledge necessary for object creation, and they are especially useful to create Aggregates.

An Aggregate Root that provides a Factory Method for producing instances of another Aggregate type (or inner parts) will have the primary responsibility of providing its main Aggregate behavior, the Factory Method being just one of those. Factories can also provide an important layer of abstraction that protects the client from being dependent on a particular concrete class.

There are times when a Factory is not needed, and a simple constructor is enough. Use a constructor when:

  * The construction is not complicated.
  * The creation of an object does not involve the creation of others, and all the attributes needed are passed via the constructor.
  * The developer is interested in the implementation and perhaps wants to choose the strategy used.
  * The class is the type. There is no hierarchy involved, so no need to choose between a list of concrete implementations.

## Repositories:

A Repository is basically a layer that sits between your project's domain and the database. Martin Fowler, in his book _Patterns of Enterprise Application Architecture_, writes that a repository

> Mediates between the domain and data mapping layers using a collection-like interface for accessing domain objects.

This means that you should think of accessing the data in your database in the same way as you would work with a standard collection object.

Let me explain a bit more. Imagine in Domain-Driven Design you might need to create an object, either with a constructor or a factory; you must request it from the root of the Aggregate. The problem is now that the developer must have a reference to the root. For large applications, this becomes a problem because one must make sure the developers always have a reference to the object needed. This will lead to developers creating a series of associations which are not really needed.

Another reason why repositories matter is accessing the database. The programmer must not be aware of the details needed to access a database. As the database is in the infrastructure layer, it has to deal with lots of infrastructure details instead of dealing with domain concepts. Furthermore, if the developer requests a query to run, this will lead to exposing even more of the internal details of the query that's needed.

If we do not have a repository, the domain focus will be lost and the design will be compromised. So if developers use queries to access data from a database or pull a few specific objects, domain logic moves into queries and developer code, so the aggregates will be useless.

Finally, the repository acts as a storage place for globally accessible objects. The repository may also include a strategy. It may access one persistence storage or another based on the specified strategy.

## Implementing in Laravel:

As you might already know, the best choice to implement DDD in PHP is the Doctrine ORM. In order to implement aggregates and repositories, we need to make some changes in our entities and create some files in our domain layer.

Today I've decided to implement a small part of the application in which the user can create a page or modify it. Every page can contain many comments, and each comment can have some sub-comments. Administrators can approve/reject comments after they have been added.

In the above scenario, the first step is creating a base repository in your domain layer, a base repository derived from Doctrine EntityRepository, that will let us have all built-in Doctrine Repository functions. We can also put our common functionality in here, and all of our repositories must inherit from it. The implementation looks like this:

We have two repositories. The first one is the page repository and the second one is the comment repository. All of the repositories must have the `entityClass` property to define an entity class. In this case, we can encapsulate (private property) the entity to our repositories:

I use the Doctrine command line to generate my entities:

As you can see, in the above code I define relationships in entity annotations. Implementing relationships in Doctrine ORM can seem very complicated, but it is actually not that difficult once you familiarize yourself with how things work. The only way you can add comments is by calling `addComments` in the `page` entity, and that method only accepts a `comment` entity object as input. This will make us sure about our code functionality.

My aggregate looks like:

We need an aggregate which is responsible for limiting access to the comments only if it is valid `PageId` ; I mean that without `PageId`, accessing `comments` is not possible. Let's say `comments` without valid `page id` have no meaning and are not accessible. Also, there is a `comment` factory method which helps us to encapsulate business rules.

And the factory method:

I defined two factories. The first one is the type of comments and the second one is the comment interfaces which make it mandatory for every comment to implement `choisir` method.

The `Comment` Factory method provides inner parts of the aggregate.

As you see in the code above we have two class `Comment` and `AdministrativeComments`. The `Commentfactory` will decide which class must use. Some unnecessary class or methods such as `Authorization` class and `reject` method are omitted here. As you might see in the code above, I use `RequestFactory` for validation. This is the other factory method in our application that is responsible for validating input data. This kind of validation has a definition in Domain-Driven Design and also added in laravel 5+.

## Conclusion:

Covering all of these definitions would require many articles, but I have done my best to summarize it. That was only a simple example of an aggregate root, but you can create your own sophisticated aggregate, and I hope this example helped.
