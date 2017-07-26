# When to Write Setters

_Captured: 2017-03-28 at 00:28 from [dzone.com](https://dzone.com/articles/when-to-write-setters?oid=twitter&utm_content=bufferf4556&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

What every Java engineer should know about microservices: [Reactive Microservices Architecture](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone). Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).

I have set out, almost unconsciously, to use constructor injection by default in the last few years while writing object-oriented applications. With Dependency Injection as a given, constructor injection satisfies most of my requirements for building an object graph and dynamically configuring collaborators.

## The Spectrum

I see the statefulness of an object not as an absolute but over a spectrum.

At one end of the spectrum, we have** immutable objects**: these objects acquire a configuration in their constructor and are effectively final (to employ a Java-specific term) for the rest of their lifecycles. Their fields are private and there's no way of modifying them outside of the constructor; their collaborators are only scalars or other immutable objects. In Java fields can even be final so that accidental reassignment is regarded as a compile-time error.

The physical state of an object may still change without its external behaviour being affected, like in the case of caching. I still consider this kind of white-box-immutable objects as immutable.

**Stateful objects** instead may have behavior that changes as a result of its own state (or of its collaborators). You call some Command methods on it, and the response of further calls to Query methods change. Hopefully the Commands encapsulate some domain logic to constrain the state transition to a valid and modelled one.

At the extreme end of the spectrum, we find **setters**: methods which only mutate the value of one or more fields, possibly skipping any validation, domain modeling or consistency check. The setters considered here are public methods because their limited-scope versions do not provide the same violations.

If you want to write procedural code, setters proliferate (still it's probably easier to just use public fields at that point). There are only a few valid use cases where I have found setters useful in object-oriented programming, and here is the (short) list.

## Configuration Which Has Default Values

Classes may have a few configuration values that you are able to tune; especially when there is more than a few of these parameters, I find useful to separate hard dependencies in the constructor and setters that are able to override the default parameters when the object has already been constructed. If you forgot to call these methods, the object still has to work correctly.

**Alternative solutions** for this use case are of course **constructors with default parameters**, which I definitely prefer if there are not so many options to tune (1 or 2). You can also look into with **Value Objects** which produce a new instance upon reconfiguration, and model all of the configuration parameters as a single entity; or into a **Builder** if you want to invest in an additional class and its API.

## Adding Observers

Observers (or listeners if you prefer) are collaborators which are notified of internal events happening inside an object that may interest them.

I treat the observers of an object as an append-only list data structure, with an empty list or array as the natural Null Object. The object is **initialized without any observer**, and a setter like _addListener(...)_ has the more limited capability of adding an observer but not of removing or modifying an existing one.

The nature of the Observer pattern is investing on a common bus that many observers can be attached to, even if they come from different packages and libraries. Therefore, I find it natural to support the dynamic wiring of other objects, even if they make the object more mutable can before. The needs of integration become more important than guaranteeing the safety of construction in these scenarios.

## Reconstitution

When objects are **unserialized** from a cold storage such as a stream of bytes or a JSON object, encapsulation is very likely going to be violated. Object-relational mappers have been doing this for ages by working directly on annotated private fields, with sometimes powerful results but also lots of dangers from storage and code being out of sync.

In the scenarios where you control the reconstitution of objects, such as rebuilding an object from a MongoDB document, it's often easier to provide an explicit API like a setState() method than to rely on the magic of a library which is going to bypass your public methods. To contrast the possible misuse, you can tag this method as @private (or package protected in Java), or make it very awkward to use outside of the persistence context by requiring a particular data structure to be passed in.

## Conclusion

There are very few use cases for setters in real object-oriented programming; default to constructor injection and to immutable objects to avoid overcomplicating your design. Employ setters for non-mandatory, cross-cutting initializations so that your code does not have to bend over backwards to support these use cases while at the same time it can be robust to cowboy modification of internal state.

Microservices for Java, explained. Revitalize your legacy systems (and your career) with [Reactive Microservices Architecture](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone), a free O'Reilly book. Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).

### Like This Article? Read More From DZone
