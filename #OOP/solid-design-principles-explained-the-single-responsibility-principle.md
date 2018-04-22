# SOLID Design Principles Explained - The Single Responsibility Principle

_Captured: 2018-03-13 at 19:48 from [dzone.com](https://dzone.com/articles/solid-design-principles-explained-the-single-respo?edition=367191&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-13)_

SOLID is one of the most popular sets of design principles in object-oriented software development. It's a mnemonic acronym for the following five design principles:

  * Single Responsibility Principle
  * Open/Closed Principle
  * Liskov Substitution Principle
  * Interface Segregation Principle
  * Dependency Inversion

All of them are broadly used and worth knowing. But in this first post of my series about the SOLID principles, I will focus on the first one: the Single Responsibility Principle.

[Robert C. Martin](http://blog.cleancoder.com) describes it as "a class should have one, and only one, reason to change."

Even if you have never heard of Robert C. Martin or his popular books, you have probably heard about and used this principle. It is one of the basic principles most developers apply to build robust and maintainable software. You can not only apply it to classes, but also to software components and [microservices](https://stackify.com/what-are-microservices/).

## **Benefits of the Single Responsibility Principle**

Let's address the most important questions before we dive any deeper into this design principle: Why should you use it and what happens if you ignore it?

The argument for the single responsibility principle is relatively simple: it makes your software easier to implement and prevents unexpected side-effects of future changes.

### **Frequency and Effects of Changes**

We all know that requirements change over time. Each of them also changes the responsibility of at least one class. The more responsibilities your class has, the more often you need to change it. If your class implements multiple responsibilities, they are no longer independent of each other.

You need to change your class as soon as one of its responsibilities changes. That is obviously more often than you would need to change it if it had only one responsibility.

That might not seem like a big deal, but it also affects all classes or components that depend on the changed class. Depending on your change, you might need to update the dependencies or recompile the dependent classes even though they are not directly affected by your change. They only use one of the other responsibilities implemented by your class, but you need to update them anyway.

In the end, you need to change your class more often, and each change is more complicated, has more side-effects, and requires a lot more work than it should have. So, it's better to avoid these problems by making sure that each class has only one responsibility.

### **Easier to Understand**

The single responsibility principle provides another substantial benefit. Classes, software components and microservices that have only one responsibility are much easier to explain, understand and implement than the ones that provide a solution for everything. This reduces the number of bugs, improves your development speed, and makes your life as a software developer a lot easier.

## **A Simple Question to Validate Your Design**

Unfortunately, following the single responsibility principle sounds a lot easier than it often is.

If you build your software over a longer period and if you need to adapt it to changing requirements, it might seem like the easiest and fastest approach is adding a method or functionality to your existing code instead of writing a new class or component. But that often results in classes with more than responsibility and makes it more and more difficult to maintain the software.

You can avoid these problems by asking a simple question before you make any changes: What is the responsibility of your class/component/microservice?

If your answer includes the word "and", you're most likely breaking the single responsibility principle. Then it's better to take a step back and rethink your current approach. There is most likely a better way to implement it.

## **Real-World Examples of the Single Responsibility Principle**

You can find lots of examples of all SOLID design principles in open source software and most well-designed applications. such as your Java persistence layer and the popular frameworks and specifications, which you most likely used to implement it.

One of them is the [Java Persistence API (JPA) specification](https://www.jcp.org/en/jsr/detail?id=338). It has one, and only one, responsibility: Defining a standardized way to manage data persisted in a relational database by using the object-relational mapping concept.

That's a pretty huge responsibility. The specification defines lots of different interfaces for it, specifies a set of entity lifecycle states and the transitions between them, and even provides a query language, called [JPQL](http://thoughts-on-java.org/jpql).

But that is the only responsibility of the JPA specification. Other functionalities which you might need to implement your application, like validation, [REST APIs](https://stackify.com/multiple-media-types-java-microservices-resteasy/) or [logging](https://stackify.com/application-logging-apm-strategy/), are not the responsibility of JPA. You need to include other specifications or frameworks which provide these features.

If you dive a little bit deeper into the JPA specification, you can find even more examples of the single responsibility principle.

### **JPA EntityManager**

The _[EntityManager](https://docs.oracle.com/javaee/7/api/javax/persistence/EntityManager.html)_ interface provides a set of methods to persist, update, remove and read entities from a relational database. Its responsibility is to manage the entities that are associated with the current persistence context.

That is the only responsibility of the _EntityManager_. It doesn't implement any business logic or validation or user authentication. Not even the application-specific domain model, which uses annotations defined by the JPA specification, belongs to the responsibility of the _EntityManager_. So, it only changes, if the requirements of the general persistence concept change.

### **JPA AttributeConverter**

The responsibility of the _EntityManager_ might be too big to serve as an easily understandable example of the single responsibility principle. So, let's take a look at a smaller example: an _[AttributeConverter](http://www.thoughts-on-java.org/jpa-21-how-to-implement-type-converter/)_ as the JPA specification defines it.

The responsibility of an _AttributeConverter_ is small and easy to understand. It converts a data type used in your domain model into one that your persistence provider can persist in the database. You can use it to persist unsupported data types, like your favorite value class, or to customize the mapping of a supported data type, like a [customized mapping for enum values](https://www.thoughts-on-java.org/jpa-21-type-converter-better-way-to).

Here is an example of an _AttributeConverter_ that maps a _java.time.Duration_ object, which is not supported by JPA 2.2, to a _java.lang.Long_: The implementation is quick and easy. You need to implement that AttributeConverter interface and annotate your class with a _@Converter_ annotation.

As you can see in the code sample, the _DurationConverter_ implements only the two required conversion operations. The method _convertToDatabaseColumn_ converts the _Duration_ object to a _Long_, which will be persisted in the database. And the _convertToEntityAttribute_ implements the inverse operation.

The simplicity of this code snippet shows the two main benefits of the single responsibility principle. By limiting the responsibility of the _DurationConverter_ to the conversion between the two data types, its implementation becomes easy to understand, and it will only change if the requirements of the mapping algorithm get changed.

### **Spring Data Repository**

The last example to talk about is the [Spring Data repository](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#repositories.core-concepts). It implements the repository pattern and provides the common functionality of create, update, remove, and read operations. The repository adds an abstraction on top of the _EntityManager_ with the goal to make JPA easier to use and to reduce the required code for these often-used features.

You can define the repository as an interface that extends a Spring Data standard interface, e.g., _Repository_, _CrudRepository_, or _PagingAndSortingRepository_. Each interface provides a different level of abstraction, and Spring Data uses it to generate implementation classes that provide the required functionality.

The following code snippet shows a simple example of such a repository. The _AuthorRepository_ extends the Spring _CrudRepository_ interface and defines a repository for an _Author_ entity that uses an attribute of type _Long_ as its primary key.

Spring's _CrudRepository_ provides standard [CRUD](https://stackify.com/what-are-crud-operations/) operations, like a _save_ and _delete_ method for write operations and the methods _findById_ and _findAll_ to retrieve one or more _Author_ entities from the database. The _AuthorRepository_ also defines the _findByLastName_ method, for which Spring Data generates the required JPQL query to select _Author_ entities by their _lastname_ attribute.

Each repository adds ready-to-use implementations of the most common operations for one specific entity. That is the only responsibility of that repository. Similar to the previously described _EntityManager_, the repository is not responsible for validation, authentication or the implementation of any business logic. It's also not responsible for any other entities. This reduces the number of required changes and makes each repository easy to understand and implement.

## **Summary**

The single responsibility principle is one of the most commonly used design principles in object-oriented programming. You can apply it to classes, software components, and microservices.

To follow this principle, your class isn't allowed to have more than one responsibility, e.g., the management of entities or the conversion of data types. This avoids any unnecessary, technical coupling between responsibilities and reduces the probability that you need to change your class. It also lowers the complexity of each change because it reduces the number of dependent classes that are affected by it.

Read more: Get a primer on [OOP Concepts](https://stackify.com/oops-concepts-in-java/) in Java and learn about the 4 main concepts: [abstraction](http://stackify.com/oop-concept-abstraction/), [encapsulation](http://stackify.com/oop-concept-for-beginners-what-is-encapsulation/), [inheritance](http://stackify.com/oop-concept-inheritance/), and[ polymorphism](http://stackify.com/oop-concept-polymorphism/).
