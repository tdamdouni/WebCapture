# Value Objects

_Captured: 2017-04-14 at 00:11 from [dzone.com](https://dzone.com/articles/value-objects?edition=290900&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-13)_

[Bitbucket](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

Since I've already set you up in a [DDD](http://amzn.to/2nGLUXU) mood with the [previous post](https://dzone.com/articles/aggregate-pattern), let's capitalize on that further. In this post, I'll try to provide an easy explanation of Value Objects and their benefits.

## Motivation

Most of the concepts we're modeling in our software have **no global identity**. If you wonder what I meant with the previous sentence, look inside your entity classes. Each of them contains a bunch of fields, usually represented by standard types such as `String` or `BigDecimal`, or by simple data structures. These, without the context of the enclosing entity, cannot be distinguished from other `String`s, `BigDecimal`s, or structures. We don't identify them by ID of any kind; we identify them only by their **values**.

For example, if we were talking about a `Person` class, we would probably see fields like `firstName`, `lastName`, or `address`. A person has a clear, global identity. If there was an object representing me, the object would refer to a real guy sitting at work, finishing a blog post and waiting to go home - I'm an entity. On the other hand, if we were talking only about a `String` like "Grzegorz", we don't have this global scope - it's just a **value**.

Values like the ones mentioned above can have certain logic associated with them e.g. validation, transformations or calculus. As we're using an OO language, it makes all the sense in the world to use its powers and combine the value and the logic together in an object.

## Value Objects

The Value Objects pattern does just that - it transforms our values into objects. Everything boils down to wrapping the standard types inside our own, named by the concept their representing:

As the value objects have no identity, we compare them together by simply comparing all the values they contain:
    
    
        return Objects.equals(street, address.street) &&
    
    
                Objects.equals(city, address.city) &&

Usually, we also make/treat the value objects as immutable, i.e. instead of changing the value objects, we create new instances that wrap the new values:
    
    
    this.address = new Address(event.street, ...);

There are practical and conceptual reasons behind this. From the practical perspective, immutable types are handy, as they can be easily shared between different objects and returned by the entities without the risk of compromising consistency. From the conceptual perspective, it makes sense to create a new instance of a value object when the value changes, as we're literally assigning a _new value_.

## Benefits

For a person unfamiliar with the concept, this might look like heavy overengineering. In reality, value objects have some nice advantages:

  * They make our code safer, as the type system prevents us from doing stupid mistakes: 
  * They give us the flexibility in terms of internal representation. For example, I could easily change...:   
...to...:   
...without changing most of the `PersonId` clients.
  * As mentioned, they also encapsulate related logic e.g. validation:   
Or calculus: 
    
                return new Money(amount + other.amount);

## Drawbacks

The obvious drawbacks of value objects are that the numbers of classes in the project might grow significantly and, as they're usually immutable, the number of created objects, too. While I wouldn't initially care about the performance, as in most cases it would not be a bottleneck, I'd be extremely careful not to overdo the concept and bloat the project with a ton of String wrappers that do nothing but wrapping. In my projects, I create value objects only when I see that there is a piece of logic to encapsulate.

## Implementing Value Objects

All the examples I've shown by now were in pseudo-Java, as their purpose was to convey the idea rather than show all the guts. Now we'll look at three real implementation examples for value objects - using plain Java, Project Lombok, and JPA.

### Plain Java

If we're not using libraries like Lombok or Immutables, and we don't use JPA for persistence, we can implement value objects in plain Java. Basically, this boils down to implementing an immutable class by ourselves and providing an equals method that compares fields by values. As a reminder, to create such an immutable class, we have to:

  * Make it `final`
  * Make all the fields `final` (this also implies no field mutation in methods and creating new objects when someone wants a value object with different data)
  * Copy all mutable state during construction and retrieval
    
    
            Date extendedTo = new Date(toExclusive.getTime() + millis);
    
    
            if (this == o) return true;
    
    
            if (o == null || getClass() != o.getClass()) return false;
    
    
            result = 31 * result + toExclusive.hashCode();

### Project Lombok

Many of us use plugins like [Project Lombok](https://projectlombok.org/index.html) or [Immutables](https://immutables.github.io/) to limit the amount of boilerplate code we need to write. The former has a [@Value](https://projectlombok.org/features/Value.html) annotation designed specifically to support easy creation of value objects -- it auto-generates `private` and `final` keywords, a constructor, getters, and `equals`/`hashcode` methods. It's important to know that it does not support defensive-copying, which may force us to use different types than we'd normally do. In our example, we have to use `Instant` instead of `Date`.

### JPA

It's common for developers store their value objects in a relational database using JPA. In such a case, we need to relax the immutability constraints and add some annotations. Since the implementation can't make the fields `final`, we have to be more careful about people not adding setter methods to the value objects.

## Summary

The Value Objects pattern transforms values in our projects into real objects, giving us more type safety, hiding implementation, and giving a home to all related logic. That being said, we should always evaluate if the mentioned benefits outweigh the drawbacks of creating extra classes, which, in Java, implies extra source files and a rapidly growing size of the project. To implement a value object, we simply wrap a value into an immutable class with an equals/hashcode pair that compares the objects by values.

[Bitbucket is the Git solution](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)
