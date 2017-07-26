# The Genius of the Law of Demeter

_Captured: 2017-05-17 at 00:19 from [dzone.com](https://dzone.com/articles/the-genius-of-the-law-of-demeter?edition=298107&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-16)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D).

The [Law of Demeter](http://www.ccs.neu.edu/research/demeter/papers/law-of-demeter/oopsla88-law-of-demeter.pdf) might be one of the most well-defined, useful, and concisely written rules of Object-Oriented software development ever. It might also be one of the most often ignored things in our profession -- other than deadlines.

Let's take a deep dive into what it says, what it actually means, and how to obey it in letter and spirit.

## Why Should We Obey the Law of Demeter?

There are well-known abstract concepts in Object-Oriented programming, like encapsulation, cohesion, and coupling, that could be theoretically used to generate clear designs and good code. While these are all very important concepts, they are just not pragmatic enough to be _directly_ useful for development. One has to _interpret_ these concepts, and with that, they become somewhat _subjective _and start to depend on people's experience and knowledge.

The same can be said for other concepts like the [Single Responsibility Principle](https://en.wikipedia.org/wiki/SOLID_%28object-oriented_design%29), or the [Open/Closed Principle](https://en.wikipedia.org/wiki/SOLID_%28object-oriented_design%29), etc. These allow a very wide margin for interpretation, so the practicality, the direct usefulness, is therefore diminished.

The genius of the Law of Demeter comes from the succinct and exact definition, which allows for a _direct_ application when writing code, while at the same time almost automatically guaranteeing proper encapsulation, cohesion, and loose coupling. The authors of the Law managed to take these abstract concepts and distil the essence of them into a clear set of rules that are universally applicable to Object-Oriented code.

## So What Does It Say?

The Law, in its original form, is stated this way:

> For all classes C, and for all methods M attached to C, all objects to which M sends a message must be
> 
>   * M's argument objects, including the self object or
>   * The instance variable objects of C
> 
> (Object created by M, or by functions or methods which M calls, and objects in global variables are considered as arguments of M.)

In the early days of Object-Orientation, objects were supposed to "send messages" to each other. That is how they communicated. So the term "objects to which M sends a message" roughly translates to "objects used by M," or in a more practical definition "objects on which M calls a method on."

You might have noticed that there are some very important additional points made in parentheses after the two rules. They seem like clarifications mentioned just in passing, but they are actually additional rules. So let's reformulate the whole Law so all points stand independently:

For all classes C, and for all methods M attached to C, all objects to which M sends a message must be:

  1. `self` (`this` in Java)
  2. M's argument objects
  3. Instance variable objects of C
  4. Objects created by M, or by functions or methods which M calls
  5. Objects in global variables (`static` fields in Java)

## What Does It Mean?

Well, the law formulates what we are _allowed_ to do in any given method M. So, let's work backward and find out what it is exactly what this law _prohibits_.

Rule #4 states, that all objects created during the call to M, either directly or indirectly, are allowed. So the prohibition must be among objects that already existed when the call began.

These already existing objects must have a reference to them, otherwise, nobody would be able to access them. Therefore these objects must be referenced from fields (variables) of other objects. Rule #5 allows global objects, so that leaves us with objects in instance variables.

Rules #1, #2, and #3 further allows "self", M's parameters and all objects in instance variables of C.

That means that the Law prohibits "sending a message" to any already existing object that is held in instance variables of _other_ classes, unless it is also held by our class or passed to us as method parameters.

## Examples

Let's look at some examples of the Law in action:

The method call `sendShutdownMessage()`_i is_ obviously allowed, because it is covered by Rule #1. Any method can be called on the current object.

How about this one:

That is also allowed, because of Rule #3 (as `socket` is an instance variable of this class).

But, what about this one:

This _is_ a violation of the Law of Demeter. The method received the parameter `person`, so all method calls on this object are allowed. However, calling any methods (in this case `getBytes()`) on the object returned by either `getName()` or `getPhoto()` is _not_ allowed. Assuming standard getters, these objects are already existing objects in other objects' instance variables, therefore they are exactly the kind of objects this method should not have access to.

## Chain Calls

Some explanations of the Law concentrate on so-called "chain calls", that is, expressions which contain multiple dereferencings. Or stated plainly, multiple "dots", like this:

This is almost certainly a violation of the Law, since all those objects (owner, address) are presumably already-existing instance variable values, to which the Law prohibits access.

However, it is not the chain-calling that makes the above a violation, but the access to certain objects. The following "refactored" code still violates the Law:

As above, the objects in `owner`, `ownerAddress`, and `ownerStreet` are still not covered by any of the rules, therefore no methods should be called on them.

## Fluent APIs

Some interpretations of the Law argue that since chain-calls are not allowed, fluent APIs are also forbidden. Fluent APIs are created to allow syntactically easy usage of a library or set of classes. They look like this:

To determine whether such a construct is allowed, we just have to check each method call to see whether it is specifically allowed. The `ReportBuilder` object is created in this method right now, so the first method call `withBorder(1)` is on a freshly created object. This is explicitly allowed by Rule #4.

All the following method calls, including the last `build()` call are all using the returned objects from the previous call. What is the return value of all these methods? Well, most of the fluent APIs just return the same object over and over again. That is still covered by Rule #4 because the builder is an object that was created in this code. Some fluent APIs use immutable objects and return a new object every time. But even if this is the case, Rule #4 still applies to indirectly created objects too.

So the Law of Demeter does _not_ prohibit fluent APIs.

## "Wrapper" Methods

Some, including the [Wikipedia Article on the Law of Demeter](https://en.wikipedia.org/wiki/Law_of_Demeter), argue that the Law implies the usage of "Wrapper" methods to get around calling methods on foreign objects, like this:

There are a couple of problems with this approach. For example: How is `getOwnerAddressStreet()` implemented? Presumably like this:

So two new methods are introduced, but there was no real structural or design change. One could argue that while the Law was _technically_ followed, the spirit of the Law was still violated.

The structure is still visible in the method name, and we all know that the caller wants to get the street of the address of the owner of the car.

The question is: Why does the caller want that, and how does he/she even know that this information exists at this point? This is when applying the Law blends together with Object-Oriented Design. Obviously, the purpose of the Law is not to roll additional hurdles in our way and make our lives more difficult. The same way that our job is not to make sure that we _technically_ follow all the rules without thinking about our overall design.

What the Law is quite clearing saying is that you shouldn't access the Street in this structure. As in, you shouldn't even know it's there. Don't trick the definition by introducing wrapper methods! There is a deeper design issue here that needs to be addressed (no pun intended)!

## Pure "Data Structures"

In his book [Clean Code](https://books.google.de/books/about/Clean_Code.html?id=_i6bDeoCQzsC&redir_esc=y), Robert C. Martin has a short section on the Law of Demeter, where he makes two interesting points. One is that perhaps by using direct access to variables, the Law could be circumvented. So instead of this...

...which is not acceptable, it could be transformed into the following, which complies with the Law, since it doesn't involve method calls:

There are two arguments against this line of reasoning. One is that it still just tries to work around the Law instead of heeding its advice. And the second is that direct access to fields arguably still qualifies as "sending a message," since it is still just communication between two objects.

There is a more nuanced point made by Uncle Bob regarding the above -- that the Law of Demeter should not apply to pure data structures anyway.

Pure data structures ("objects" that have no behavior, just data) are integral building blocks of a procedural, functional or a mixed paradigm approach. As such, they are of course exempt from having to comply with the Law of Demeter, which is a Law for Object-Oriented development.

## Getters

Most, if not all of the negative examples for the Law of Demeter given involve "getter" methods. These are methods like this:

It is not a coincidence that this is the case. Let's imagine another method, which uses this getter:

Is the above call even allowed? Well, technically yes. The `car` object is a direct parameter to the method, so I may call methods on this object.

However, let's think about what can be done with the result of this call. The method returns an `owner` object, which is neither a parameter nor an object that the `Garage` has direct access to. Therefore there can be no further method calls on this object. Not `toString()`, not `hashCode()`, nothing!

This might be considered unexpected. So that means while calling the getter itself might be technically legal, we can't actually _use_ the result. It seems getter methods violate the Law of Demeter almost by design.

As previously said, this is neither a coincidence nor is it unintentional. In the Object-Oriented paradigm, objects are supposed to tell other objects what to do -- delegate, instead of querying data from others and doing everything themselves.

## When to Apply

There are some opinions in blog posts and other articles expressing that the Law of Demeter is less of a "law" and only a "suggestion" or a "guideline." Or that it is fine in theory, but does not apply to certain objects, like data structures, Java Beans, entities, business objects, value objects, data transfer objects, or objects for presentation or persistence.

An Object-Oriented developer should be aware that more often than not, these opinions come from a background of different programming paradigms, in which the Law of Demeter might very well have a different weight or even interpretation than in Object-Orientation.

The Law of Demeter is _the_ law of the land in Object-Oriented development. As the original paper itself calls it, it is the Law of Good Style. Complying with the Law technically and in spirit everywhere is the _minimum_ required to produce proper, well designed Object-Oriented code.

## Conclusion

The Law of Demeter is a very well-defined set of rules for Object-Oriented development. Following these rules in letter and spirit takes little effort if one is applying good Object-Oriented Design principles anyway.

Furthermore, it produces clear signals if the code is deviating from the Object-Oriented path, therefore it is an invaluable tool to keep our designs and code style on the right track.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D).
