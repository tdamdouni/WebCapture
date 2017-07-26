# Quality Code Is Encapsulated

_Captured: 2017-06-05 at 02:24 from [dzone.com](https://dzone.com/articles/quality-code-is-encapsulated?edition=304121&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-04)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

To encapsulate something is to envelop and protect it. Encapsulation is a fundamental facility that every programming language supports at some level.

Encapsulation is about hiding implementation details so ideas can be expressed at higher levels and to protect those details from other parts of the system.

To me, most fundamentally, encapsulation means hiding implementation details. Instead of expressing how to do something, we express what to do. I like to say that encapsulation is hiding the "how" with the "what." Encapsulation is an important concept and an important code quality because it gives us the ability to change the implementation details without affecting other parts of the system.

We're packaging bits of functionality that include both data and behavior, and that functionality is supported through the interface it represents. We should make no assumptions about any other parts of the system. The more implementation details that we can hide, the freer we are in the future to change our implementation without affecting others.

Sometimes we unwittingly leak implementation details, and sometimes we make assumptions about a system that the author may or may not have intended.

In my book, _Beyond Legacy Code: Nine Practices to Extend the Life (and Value) of Your Software,_ I talk about well-capsulated software being designed from the outside-in perspective rather than the inside-out perspective.

Outside-in programming is when we design a feature or service from the consumer's perspective. We think about what the consumer wants to give us and what the consumer expects back. We name things, in terms of the services we provide, from the consumer's perspective. This helps us build cleaner APIs and stronger contracts. This is also the fundamental perspective that we take when we're doing test first development.

Outside-in programming is all about defining boundaries. It's about focusing on what we want to accomplish rather than how we plan on accomplishing it and it helps us build more autonomous systems that are easier to test and extend in the future.

When I talk about encapsulation I don't just mean hiding state or behavior. There are many things that can be hidden. Even the way we think about and refer to things can hide or reveal implementation details. When we make assumptions about those details and then those details change, we have to also update our code that depends on those assumptions. Any parts of the system that depend on implementation details will have to be changed when those details--business rules, the criteria that drive decisions in our business processes--change. When our business processes need to change, we want to be able to respond accordingly.

In object-oriented programming, we want to hide as much of the system from itself as possible. Like the saying goes: "encapsulate by policy, reveal by need."

In other words, hide as much as we can and only reveal what's needed to others in order to accomplish a task.

With regards to objects, I am always on a need-to-know basis. Design patterns are all about hiding different things. For example, there is a group of patterns that are all about hiding varying behaviors, another group of patterns that are about hiding the order of behaviors, or the number of behaviors, and so on. In fact, I believe that one quality of great software developers is their ability to hide as much as possible in their code while still accomplishing the task.

Being able to encapsulate the right things comes from a deep understanding of the problem domain. To encapsulate code, start by creating strong contracts that are enforced through your APIs. Keep state private and hide implementation details as much as you can.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
