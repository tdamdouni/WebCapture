# When Is Self-Encapsulation Worth It?

_Captured: 2017-03-24 at 01:37 from [dzone.com](https://dzone.com/articles/when-is-self-encapsulation-worth-it?edition=286905&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-23)_

What every Java engineer should know about microservices: [Reactive Microservices Architecture](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone). Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).

Data encapsulation is a central tenet in the object-oriented style. This says that the fields of an object should not be exposed publicly, instead all access from outside the object should be via accessor methods (getters and setters). There are languages that allow publicly accessible fields, but we usually caution programmers not to do this. _Self-encapsulation_ goes a step further, indicating that all _internal_ access to a data field should also go through accessor methods as well. Only the accessor methods should touch the data value itself. If the data field isn't exposed to the outside, this will mean adding additional private accessors.

Here's an example of a reasonably encapsulated Java class Charge:
    
    
      public Money getAmount() { return Money.usd(units * rate); }

Both fields are immutable. The units field is exposed to clients of the class via a getter, but the rate field is only used internally, so doesn't need a getter.

Here is a version using self-encapsulation.

Class ChargeSE:
    
    
      public Money getAmount() { return Money.usd(getUnits() * getRate()); }

Self-encapsulation means that `getAmount` needs to access both fields through getters. This also means I have to add a getter for `rate`, which I should make private.

Encapsulating mutable data is generally a good idea. Update functions can contain code to execute validations and consequential logic. By restricting access through functions, we can support the [UniformAccessPrinciple](https://martinfowler.com/bliki/UniformAccessPrinciple.html), allowing us to hide which data is computed and which is stored. These accessors allow us to modify the data structures while retaining the same public interface. Different languages differ in details of what is "outside" for an object by various kinds of [AccessModifier](https://martinfowler.com/bliki/AccessModifier.html), but most environments support data encapsulation to some degree.

I've come across a few organizations that mandated self-encapsulation, and whether to use it or not has been a regular topic of debate since the 90s. Its advocates said that encapsulation was such a benefit that you wanted to incorporate it to internal access too. Critics argued that it was unnecessary ceremony leading to unnecessary code that obscured what was going on.

My view on this is that most of the time, there's little value in self-encapsulation. The value of encapsulation is proportional to the scope of the data access. Classes are usually small (at least mine are), so direct access isn't going to be an issue within that scope. Most accessors are simple assignments for the setter and retrieval for the getter, so there's little value in using them internally.

But there are common circumstances where self-encapsulation is worth the effort. If there is logic in the setter, then it's wise to consider it for any internal updates too. Another circumstance is when the class is part of an inheritance structure, in which case the accessors provide valuable hook points for subclasses to override behavior.

So my usual first move is to use direct access to fields, but refactor using [Self-Encapsulate Field](http://www.refactoring.com/catalog/selfEncapsulateField.html), should circumstances demand it. Often, when faced with the forces that lead me to consider self-encapsulation, I can resolve the problem by [extracting a new class](https://refactoring.com/catalog/extractClass.html).

Microservices for Java, explained. Revitalize your legacy systems (and your career) with [Reactive Microservices Architecture](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone), a free O'Reilly book. Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).
