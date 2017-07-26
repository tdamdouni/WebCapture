# MVC Pattern Language (Part 1)

_Captured: 2017-04-16 at 23:30 from [dzone.com](https://dzone.com/articles/mvc-pattern-language-part-1?edition=290924&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-16)_

[Bitbucket](https://dzone.com/go?i=201143&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=201143&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

There seems to be a lot of misconceptions related to MVC. Some consider it a technique for code reuse, others think it's how you group classes in web applications, and some have even mistaken it for the frameworks that claim to support the pattern. In this post, we'll take a look at a [paper written by Trygve Reenskaug](https://heim.ifi.uio.no/~trygver/2003/javazone-jaoo/MVC_pattern.pdf) and try to figure out what its original creator really means when he talks about MVC.

## MVC Pattern Language

The first two sentences of the abstract already shed some interesting light on MVC:

> MVC was conceived in 1978 as the design solution to a particular problem. The top level goal was to support the **user's _mental model_** of the relevant information space and to enable the user to inspect and edit this information. 

I intentionally emphasized the part about mental models, as this is a central concept in MVC. We'll be talking about these a lot in this post. In case you've never heard about mental models before, here's a nice quote by Jay Wright Forrester:

> The image of the world around us, which we carry in our head, is just a model. Nobody in his head imagines all the world, government, or country. He has only selected concepts, and relationships between them, and uses those to represent the real system. 

To combine the two quotes together into something digestible: The original goal of MVC was to create a piece of software that resembles the user's internal image of a certain problem space and allow the user to interact directly with that image. (Was that digestible?)

25 years after Trygve Reenskaug presented the idea of MVC, he wrote a paper called [The Model-View-Controller (MVC) - Its Past and Present](https://heim.ifi.uio.no/~trygver/2003/javazone-jaoo/MVC_pattern.pdf) in which he explores other ideas that support the original goal and combines them into an MVC Pattern Language.

In this two-part article, I'll go over each of the patterns it contains and try to briefly explain them in a friendly way. The goal of this article is not to duplicate or rewrite the original text. I'd rather like to spread the original idea and inspire further reading.

## 1\. Integrated Domain Services

Most, if not all, enterprises work in multiple (sub-)domains, e.g. finance, controlling, customer relations, etc. The whole system used by the enterprise has to be somehow integrated together.

Instead of creating one huge application that supports all of the domains, we create separate ones per each of the (sub-)domains. Reenskaug calls these applications _domain services_. Each of them should be tightly integrated internally but loosely integrated to other applications.

This pattern should resemble the [microservices architecture](http://amzn.to/2oXXsEd) style that's been very popular lately and the _bounded context_ pattern known from [DDD](http://amzn.to/2nTYQWH). At the same time, as we'll see in the next pattern, a domain in the MVC understanding does not necessarily have to match a _bounded context_ in DDD.

## 2\. Line Department Owns Domain Components

A single business domain can be handled by multiple departments in an organization. Each of these departments may have different needs, which in turn might lead to compromises when designing the application.

The pattern suggests splitting a _domain service_ into _domain components_ that match the departments' responsibilities inside an organization. Then, a department is given full authority inside its _component_. To coordinate all _components_ together, the pattern suggests the use of interfaces.

While Integrated Domain Services resembled a more coarse-grained flavor of DDD _bounded contexts_, this pattern seems like a more fine-grained version of it to me. As Trygve Reenskaug points out, going too fine-grained with this can make the organization more dependent on certain people and their personal characteristics. Thus, the whole organization might become more fragile and harder to change.

## 3\. Mental Object Models

As I probably failed to explain in the beginning of the post, to make information systems more friendly and comprehensible for the users, they should be based on the users' mental models. Building a mental model is hard, as it requires users' active participation and understanding of the modeling language.

The solution suggested in the paper is to build a _modeling language based on the concept of interacting objects_ and, ultimately, making the modeling language become the programming language itself. Given such language would be sufficiently easy, the users could design parts of the applications themselves.

Basically, it's the same old problem over and over. We can't go inside the users' heads and so we're doomed to misunderstand what they mean and want. Then, before we get everything right (if that's even possible), the requirements change and the process starts over and over. Maybe instead of studying mind-reading, we could create tools that would allow users to model the program themselves. Ah, those programmers' dreams!

## 4\. Personal Information Systems

Although splitting a system into domains is a good idea on the back-end side of the system, the split is not that obvious on the front-end side. An individual might have a job that requires data and functionalities from multiple different domains. We want to provide him with an _integrated information system_, in which he can do all the tasks assigned to him.

To do that, we provide the individual with _tools_ that allow him to perform all of his tasks using a personal computer. Under the hood, each of the _tool_ uses _domain services_.

Considering the fact that companies and job responsibilities rapidly change, we need to ensure a fast way of providing new tools or new combinations of information. This moves us back to the programmers' dream zone which, in this case, is _(semi-)automatic tool generation_.

## 5\. Domain User Matrix

In the previous pattern, we've seen a discrepancy between an individual and the _domain services_. That discrepancy can go even further - the domain services might not match his mental models at all. He might be thinking in different objects than actually exist in the domains.

In such case, we can create a layer of _business objects_ on top of the _domain components_ that will bridge the gap.

The _business objects_ look to me like _object roles_ and _contexts_ from the [DCI architecture](http://tidyjava.com/dci-architecture-visionary/). These are also supposed to match the user's mental model and orchestrate the domain under the hood. Also, as Trygve Reenskaug points out, the presence of _business objects_ might cause logic to leak between them and the _domain components_ they use.

## Summary of Part 1

In this part, we covered a lot -- from the deep corners of _domain services_ and their _components_, up to the users' heads and their mental models. We talked how the two don't necessarily need to match together and how to bridge the gap using _tools_ and _business objects_. In the meantime, we came across two particularly cool ideas that have not been implemented widely enough yet - _modeling languages_ for the users and _(semi-)automatic tool generation_.

In the next part, we'll look at the lower level patterns in the MVC Pattern Language, which will allow us to bridge the gap between the user's mental model and the tool even further.

[Bitbucket is the Git solution](https://dzone.com/go?i=201144&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=201144&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)
