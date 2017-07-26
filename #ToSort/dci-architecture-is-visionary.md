# DCI Architecture Is Visionary

_Captured: 2017-03-14 at 15:26 from [dzone.com](https://dzone.com/articles/dci-architecture-is-visionary?oid=twitter&utm_content=buffer35100&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Bitbucket](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

Welcome in the sixth installment of my architecture series. So far we have covered 5 similar architectural styles, from the [Layered Architecture](https://dzone.com/articles/layered-architecture-is-good) to the [Clean Architecture](https://dzone.com/articles/clean-architecture-is-screaming). In this article, we'll look at something substantially different - the _DCI_ architecture by James Coplien and Trygve Reenskaug.

## What Is DCI?

As I said before, the _DCI_ architecture is different than the five [styles ](http://tidyjava.com/layered-architecture-good/)[that](https://dzone.com/articles/hexagonal-architecture-is-powerful) [we](https://dzone.com/articles/onion-architecture-is-interesting) [previously](https://dzone.com/articles/package-by-feature-is-demanded) [discussed](http://tidyjava.com/clean-architecture-screaming/). The main difference between _DCI_ and the rest is that it tells you (close to) nothing about _layers_ and code organization, in the sense of what package should your classes go into. So what does it tell us?

_DCI_ stands for _Data_, _Context_, and _Interaction_. This name should resonate with the way most people understand object-orientation. We have some context i.e. a user's incoming request, we retrieve some data, i.e. the objects, and we make those objects interact to satisfy the user's request. So far, everything should feel common. Let's move to the uncommon part.

### Data

The _Data_ part of _DCI_ consists of domain objects a la _entities_ in DDD or Clean Architecture. The major difference between _DCI_'s _data_ object and a typical entity is that the data object is relatively stupid. It's not anemic. It can still contain important domain methods that would preserve it's invariants etc., but it shouldn't contain a single method that is specific to an application's _use case_ and not the domain itself. If this feels blurry, think about the concept of printers that some people promote:

They claim that this approach to serializing objects is better because it promotes better encapsulation and hence better object-orientation. In _DCI_'s _data_, such an approach could not take place since printing is part of a _use case_ and not a part of the domain object.

### Interactions

So where does the _use-case_-specific code go? The answer is: in the object _roles_. The concept of _roles_ is pretty unique to _DCI_ - I haven't seen it in any other major architectural style. The _roles_ are supposed to dynamically extend the _data_ object's behavior with the _use case_-specific functionality. Since such functionality might want to operate on object's state (like the printer above), an object _role_ should preferably have access to the object's internals e.g. via accessors or simple methods. In pseudo-code, our example with an extracted _role_ could look like this:

I see two major benefits of this approach. First, the domain object is not cluttered by peripheral stuff that it would not contain if not for some _use case_. Second, an object _role_ can be played by objects of different classes, as long as they contain data and methods necessary to fulfill the _role_. In our example, we could print a magazine the same way we print a book (we should adjust the _role_'s name then).

### Context

The place where _data_ objects are retrieved and _roles_ assigned is called the _context_. This would be a rough equivalent of an _application service_ or Clean Architecture's _use case interactor_. Why only rough? Because ideally, a context should provide the _roles_ with references to all collaborators in a _use case_, call one of the _roles_ and do nothing else.

Think about a bank transfer. We have two accounts - source account and destination account. Obviously, the account is a _data_ object, while source account and destination account are _roles_. When the source account decreases its own balance, it wants to let the destination account know that it should increase its balance. Once this is done, a success message is shown in the GUI. Does that mean that the SourceAccount should carry around a destination account and a GUI reference? And if there were more collaborators, should each of them contain a reference to each one it collaborates with. That could easily get out of hand. Hence, DCI assumes that object _roles_ should know what collaborators they have based on the _context_ in which they execute.

### All Together

Let's walk through things the way control flows in the application. A user presses a button that sends a use-case-related request. An application receives that request, instantiates an appropriate _context_, and passes the request to it. The _context_ retrieves all _data_ objects necessary to fulfill the _use case_'s goal and assigns appropriate _roles_ to them. Then, it sends a message to an object _role_ that begins a series of _interactions_ between the objects. If there is a need to communicate something to the user, it's also done by the _roles_. Once it's complete, the user's goal should be achieved.

![](http://tidyjava.com/wp-content/uploads/2017/03/ss2017-03-09at07.08.16.png)

## The Essence of DCI

I see two special things about _DCI_: separating the stable from the ever-changing and having real networks of collaborating objects.

### Separating the Stable

The idea of extracting the _use case-_specific logic to separate constructs called object _roles_ might seem odd to you at first. So far I said that it prevents clutter and allows for better code reuse. That's all true, but at a class level. At the perspective of the whole architecture, it has a far more profound meaning. We are separating things that change at different rates and for different reasons ([Single Responsibility Principle](https://dzone.com/articles/single-responsibility-principle-explained), anyone?!).

Think about it. If you get your domain model right, or rather right enough, it should not change unless the domain itself changes - it's **STABLE**. On the other hand, new _use cases_ or parts of them that operate in this domain can flow in and out all the time. Businesspeople can change their mind. Add this feature, delete that, change something. The _use case_ stuff is **EVER-CHANGING** and it changes mostly because people change their mind. Have you ever heard developers complaining that the architecture should provide a **stable foundation** for future development and it doesn't do so? Well, it's hard to achieve that if you keep mixing things up.

### Networks of Collaborating Objects

It might seem surprising to you that I pointed it out. You know, isn't it what the whole object-orientation is supposed to be about? And yet we keep writing code, in which communication looks like this:

![](http://tidyjava.com/wp-content/uploads/2017/03/ss2017-03-09at07.10.46.png)

There's no collaboration. It's just the service, calling methods one by one. In _DCI_, the communication would look like in the picture presented in the **All Together** section.

## Implementing DCI

If you have thought all this time that such magic is impossible in Java, you were partly right. There is a project known as [Apache Polygene](http://polygene.apache.org/), formerly known as Apache Zest and Qi4J. It allows you to mix classes into each other in the _DCI-_way, but the code produced when working with it is at least complex. For this reason, we'll look at a [Marvin](http://fulloo.info/Examples/Marvin/) example instead:

As you can see, in Marvin, the _roles_ are defined inside the _context_ and actual objects are assigned to them the same way you'd assign fields. To initiate the _use case_ , we call the `Trans()` method, which calls the first _role_: `Source`. The source account is responsible for decreasing its own balance and telling `Destination` to increase its balance. For the example to work, the `Account` obviously needs to implement the `IncreaseBalance` and `DecreaseBalance` methods:
    
    
                    Ledgers.Add(new LedgerEntry(message, amount));
    
    
                    return ((ICollection<LedgerEntry>)Ledgers).Sum(e => e.Amount);

Of course, this is a toy example, so the whole _DCI_-thing looks more complex than the domain itself. Unfortunately, there aren't any non-toy examples online -- or I haven't found them. If you want more like this one, including even some Java code, you can check them out on [the DCI page](http://fulloo.info/Examples/).

## Benefits of DCI

Since I haven't seen or heard about a _DCI_ application running in production, we will look at its theoretical benefits.

  * **[Screaming](https://8thlight.com/blog/uncle-bob/2011/09/30/Screaming-Architecture.html)++** - it doesn't highlight just the _use cases_, it also highlights the _roles_ that objects play in these.
  * **Even higher cohesion and lower coupling **- there are no methods that take care of single use case peripheral concerns in your domain objects.
  * **Lean** - by putting the stable at its core, it helps to eliminate unnecessary rework in the process of adding features to the application.
  * **Plays well with DDD **- the domain model has an important place in the architecture, and it's pure and clutter-free.

## Drawbacks of DCI

  * **Learning curve **- the concept is pretty complex and there aren't too many good learning materials for it.
  * **Lack of good tools** - it's not really supported by any major programming language. You need to work around with existing mechanisms or niche tools like Polygene.
  * **Heaviness **- it's not an architecture for simple applications like CRUDs.

## When to Use DCI?

Initially, I wanted to put here some shallow advice that the team needs to know the architecture and the tools etc. But I changed my mind. If you're working for a company with over 5 employees in the Java field, don't go there. Even if your team feels good enough to pull it off, there's a high chance that you will produce something incomprehensible for your successors. And all the rework time saved by DCI, you'll spend struggling with niche tools and lack of community support. I imagine that the situation could look a little different in other languages, but I can't say for sure.

## Summary

_DCI_ changes the way in which we think about object-orientation on the architecture level. By separating _roles_ out of objects and making them communicate in _contexts_, we create real _networks of cooperating objects_. The _data_ part of our application, where the static picture of our domain lies, remains stable and uncluttered in the process of adding new features. Unfortunately, this cool vision suffers from a lack of good tooling and learning resources, especially in Java. But even if you shouldn't go _DCI_ in your projects right now, it's an architecture worth knowing and remembering.

If you want to learn more about architecture and DCI, check out [its Wikipedia page](https://en.wikipedia.org/wiki/Data,_context_and_interaction) or the excellent book [Lean Architecture for Agile Software Development](http://amzn.to/2mKnD31).

[Bitbucket is the Git solution](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

### Like This Article? Read More From DZone
