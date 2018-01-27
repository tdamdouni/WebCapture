# Is OOP Compatible With an Enterprise Context?

_Captured: 2017-11-17 at 21:29 from [dzone.com](https://dzone.com/articles/is-oop-compatible-with-an-enterprise-context?edition=335891&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-17)_

Learn how to troubleshoot and diagnose some of [the most common performance issues in Java today](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital).

This week, during a workshop related to a Java course I give at a higher education school, I noticed the code produced by the students was mostly ok -- entirely procedural. In fact, though the Java language touts itself as an Object-Oriented language, it's not uncommon to find such code developed by professional developers in enterprises. For example, [the JavaBean specification](https://en.wikipedia.org/wiki/JavaBeans) is in direct contradiction of one of OOP's main principles, [encapsulation](https://en.wikipedia.org/wiki/Encapsulation_\(computer_programming\)).

Another example is the widespread controller, service, and DAO architecture found equally in Java EE and Spring applications. In that context, entities are generally [anemic](https://www.martinfowler.com/bliki/AnemicDomainModel.html), while all business logic is located in the service layer. While this is not bad _per se_, this design separates between state and behavior and sits at the opposite end of true OOP.

Both Java EE and the Spring framework enforce this layered design. For example, in Spring, there's one annotation for every such layer: `@Controller`, `@Service`, and `@Repository`. In the Java EE world, only `@EJB` instances -- the service layer -- can be made transactional.

This post aims to try to reconcile both the OOP paradigm and the layered architecture. I'll be using the Spring framework to highlight my point because I'm more familiar with it, but I believe the same approach could be used for pure Java EE apps.

## A Simple Use Case

Let's have a simple use-case: from an IBAN number, find the associated account with the relevant balance. Within a standard design, this could look like:
    
    
        fun getAccount(@PathVariable("iban") iban: String) = service.findAccount(iban)
    
    
        fun findAccount(iban: String) = repository.findOne(iban)
    
    
    class ClassicAccount(@Id var iban: String = "", var balance: BigDecimal = BigDecimal.ZERO)

There are a couple of issues there:

  1. The JPA specifications mandates for a no-arg constructor. Hence, it's possible to create `ClassicalAccount` instances with an empty IBAN.
  2. There's no validation of the IBAN. A full round-trip to the database is required to check if an IBAN is valid.

Note: No, there's no currency. It's a simple example, remember?

## Being Compliant

In order to comply with the no-args constructor JPA constraint -- and because we use Kotlin -- it's possible to generate a synthetic constructor. That means the constructor is accessible through reflection, but **not** by calling the constructor directly.

Note: If you use Java, tough luck, I don't know of any option to fix that.

## Adding Validation

In a layer architecture, the service layer is the obvious place to put the business logic, including validation:

In order to be more OOP-compliant, we must decide whether we should allow invalid IBAN numbers or not. It's easier to forbid it altogether.

However, this means that we must first create the `OopAccount` instance to validate the IBAN -- with a balance of 0, even if the balance is actually not 0. Again, as per the empty IBAN, the code does not match the model. Even worse, to use the repository, we must access the `OopAccount` inner state:

## A More OOP-Friendly Design

Improving the state of the code requires a major rework on the class model, separating between the IBAN and the account, so that the former can be validated and can access the latter. The IBAN class serves both as the entrypoint and the PK of the account.
    
    
    class OopAccount(@EmbeddedId var iban: Iban, var balance: BigDecimal)
    
    
    class Iban(@Column(name = "iban") val number: String,
    
    
            if (number.isBlank()) throw IllegalArgumentException("IBAN cannot be blank")
    
    
            get() = repository.findOne(this)

Notice the returned JSON structure will be different from the one returned above. If that's an issue, it's quite easy to customize Jackson to obtain the desired result.

With this new design, the controller requires a bit of change:

The only disadvantage of this approach is that the repository needs to be injected into the controller, then be explicitly passed to the entity's constructor.

## The Final Touch

It would be great if the repository could automatically be injected into the entity when it's created. Well, Spring makes it possible -- though this is not a very well-known feature -- through Aspect-Oriented Programming. It requires the following steps:

### Add AOP Capabilities to the Application

To effectively add the AOP dependency is quite straightforward and requires just adding the relevant starter dependency to the POM:

Then, the application must be configured to make use of it:

### Update the Entity

  1. The entity must first be set as a target for injection. Dependency injection will be done through autowiring.
  2. Then, the repository must be moved from a constructor argument to a field.
  3. Finally, the database fetching logic can be moved into the entity:
    
        class Iban(@Column(name = "iban") val number: String) : Serializable {

Note: Remember that field-injection is evil.

### Aspect Weaving

There are two ways to weave the aspect, either compile-time weaving or load-time weaving. I choose the latter, as it is much easier to configure. It's achieved through a standard Java agent.

  

  1. Then, the Spring Boot plugin must be configured with the agent:
    
                <agent>${settings.localRepository}/org/springframework/spring-agent/2.5.6/spring-agent-2.5.6.jar</agent>

  


## And Then?

Of course, this sample leaves out an important piece of the design: How to update the balance of an account. The layered approach would have a setter for that, but that's not OOP. Thinking about it, the balance of an account changes because there's a transfer from another account. This could be modeled as:

Experienced developers should see some transaction management requirements sneaking in. I leave the implementation to motivated readers. The next step would be to cache the values because accessing the database for each read and write would be killing performance.

## Conclusion

There are a couple of points I'd like to make.

First, the answer to the title question is a resounding 'yes'. The results are true OOP code while still using a so-called enterprise-grade framework -- namely Spring.

However, migrating to this OOP-compatible design came with a bit of overhead. Not only did we rely on field injection, we had to bring in AOP with load-time weaving. The first is a hindrance during unit testing, the second is a technology you definitely don't want on every team, as they make apps more complex. And that's only for a trivial example.

Finally, this approach has a huge drawback: most developers are not familiar with it. Whatever its advantages, they first must be "conditioned" to have this mindset. And that might be a reason to continue using the traditional layered architecture.

I've searched Google for **scientific** studies proving OOP is better in terms of readability and maintainability: I found none. I would be very grateful for pointers.

The complete source code for this post can be found on [GitHub](https://github.com/nfrankel/oopspring) in Maven format.

Understand the needs and benefits around implementing [the right monitoring solution for a growing containerized market](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics.](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital)
