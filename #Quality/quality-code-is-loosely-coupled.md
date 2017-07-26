# Quality Code Is Loosely Coupled

_Captured: 2017-05-14 at 21:49 from [dzone.com](https://dzone.com/articles/quality-code-is-loosely-coupled?edition=298100&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-14)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

While [cohesion](https://dzone.com/articles/cohesion-and-testability), which was the subject of the last three posts, is about the internal consistency of a class or method, coupling is a code quality that looks at the relationship between entities.

There are two distinct forms of coupling: loose coupling and tight coupling. One is good, the other isn't--and I always forget which one is which. They both sound pretty bad to me so I prefer using the terms intentional coupling and accidental coupling instead.

The best kind of coupling is part of the domain model. We want the right kind of coupling in our systems. We're not striving for systems with no coupling at all. A system with no coupling is a system that does nothing! Instead we're striving for the right kind of coupling, one that's needed to create the right kind of behavior, but no more.

I've found that bad coupling usually gets into a system as a secondary effect, the primary cause of which is that one of the other code qualities are missing.

For example, when classes are not cohesive they have many reasons for clients to couple to them. This type of approach, which is a common practice, causes systems to be tightly bound together, making it very difficult to change and to extend.

Loose coupling is about making external calls indirectly through abstractions, such as abstract classes or interfaces. This allows the code to run without having to have the real dependency present, making it more testable and more modular.

One of the best known techniques for working with external dependencies is dependency injection. Dependency injection is simply the practice of separating the instantiation of a service from its usage. If you want to use a service, then instead of instantiating it and invoking it, request that another entity instantiate it and then give you access to it because then you can be passed a mock instead of the real object, which will help facilitate automated testing.

It's really that simple act of injecting dependencies rather than instantiating them that lets us automate the testing of our software.

I want my coupling to be explicit. I want to keep the relationships between my entities clear and intentional, using strong contracts. This helps me avoid a whole range of errors and also nicely partitions my system.

We want coupling to reflect the nature of the problem and if we model a system well then each class only knows about what it needs to know about. This is how we limit knowledge in a system. The reason we want to limit knowledge in a system is that it limits points of failure and reduces the impact of change on a system.

Generally speaking, the more loosely coupled the system is, the more flexible it is. Sometimes we need maximum flexibility so we look at patterns like the Observer Pattern or the Vsistor Pattern. Other times we don't need a lot of flexibility so we opt to build software in such a way that it reflects the structure of what it is we're modelling.

Coupling is all about the relationship between classes and we only get a handful of relationships that we can have between classes. One class can contain another class, which in languages like Java and C# means that one object has reference to another object. These languages also have the notion of inheritance where one class can inherit from another class. Classes can also implement a common interface.

These are the primary ways in which classes can relate to each other. There are only a handful, so using the right ones in the right ways is absolutely critical.

Does a package have an address or does an address have a package? We don't give these things a second thought in the real world, but in the virtual world we make the rules, so we have to be explicit.

I want coupling where I intend it to be and no coupling where I don't intend it to be. It's that simple in theory, but in practice… well, that's another story.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
