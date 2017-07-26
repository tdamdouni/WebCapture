# Building an Intuitive DSL in Java

_Captured: 2017-04-19 at 21:38 from [dzone.com](https://dzone.com/articles/building-a-dsl-in-java?oid=twitter&utm_content=buffer9511d&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Bitbucket](https://dzone.com/go?i=201143&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=201143&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

When I started [RuleBook](https://github.com/rulebook-rules/rulebook), I used just a simple method chaining Domain Specific Language (DSL) that also leveraged Java 8's new Lambda functionality. However, as my desire to enhance the [internal] DSL and create a better experience for the language grew, I found just having a couple of objects that chained their own methods together wasn't enough.

## The Order of Words Matters

If the goal of a DSL is to create a human readable English-like language, then even an internal Java DSL that builds a Domain Specific Language out of a General Purpose (GP) language must strive to follow some rules of continuity. Take, for example, the Given/When/Then (GWT) language format associated with Business Driven Development. If Given <Some State> When <Some Condition> Then <Some Action> makes sense. But Then <Some Action> Given <Some State> When <Some Condition> doesn't make as much sense, especially if both statements are equivalent according to a DSL.

Now, let's throw a few more monkey wrenches into the system. It's pretty common for multiple 'then' statements to be allowed in GWT languages. Also, let's assume that there is an optional 'using' keyword that can be used to constrain the state available to a subsequent 'then' statement (like in [RuleBook](https://github.com/rulebook-rules/rulebook)). Now, even if the language doesn't apply ordering constraints, it becomes pretty clear that the order of the keywords used matters. And since order matters for the language to properly translate into the desired functionality, the language should apply the necessary constraints on that order to guard against unwanted behavior.

### Enforcing Order

Let's take a simple GWT format DSL interface that uses method chaining via a builder.

Using the above interface, both of the following code snippets are valid.

However, the first code snippet doesn't make a whole lot of sense. For example, if using() filters data for a then() action, which action is it applied to? Then there's how it reads. "Then some action happens, given some state, then some other action happens using some subset of the state" doesn't exactly have a logical linguistic flow. It would make more sense to have the language enforce some rules like the following:

  1. Only a 'given', 'when', 'using' or 'then' method can be the first method.
  2. Only a 'given', 'when', 'using' or 'then' method can follow a 'given' method.
  3. Only a 'then' or 'using' method can follow a 'when' method.
  4. Only a 'using' or 'then' method can follow a 'using' method.
  5. Only a 'using', 'then' or 'build' method can follow a 'then' method.

Using these rules, the first builder's sequence of method calls becomes invalid. However, this can't be done with a single builder. For each unique rule, a unique builder is required. Therfore, enforcing order using method chaining is done by chaining builders.

Taking the example a step further, the GwtThenBuilder interface might look like the following:

## Consistency Matters Too

What makes something intuitive? Is it a result of natural instinct or conditioning? Let's take driving a car for example. Most of us reading this probably know how to drive a car. But certainly none of us were born knowing how to drive a car. Yet right now, if someone handed us some car keys, we would likely know how to use those keys to drive a car. And that's true for just about any car. It's intuitive because it's known. And similarly, if you know how to drive one car, you know how to drive almost every other car. I imagine if there was a car where the normal rules of how to drive a car didn't apply then not many people would drive it. That's because people gravitate to what's known. And what's known or what can easily be known through conditioning is what we refer to as intutive.

Like driving a car, or the old adage about riding a bike, languages that have a familiar and consistent set of rules can be said to be intuitive. And intutive languages are easier to learn and adopt than unintuitive languages. Domain Specific Languages are no different. So, if you want to create one that is 'intuitive' and easy adopt, keep the options limited, keep its use familiar and keep its ruleset concise.

### Using the Tools in the Java DSL Toolbox

There are a few approaches to constructing an internal DSL out of the Java language. The common approaches are:

**Method Chaining**

**Method Sequencing**

**Nested Method Calls**

**Lambda Expressions**

When constructing a single statement, method chaining may seem like a great choice for everything. But what happens if you want to combine statements. If you use method chaining for constructing individual statements and then also use it for combining statements then the demaracation between statements can be confusing. Take the following example.
    
    
    builder.add().given(data1).when(cond1).then(action1).add().given(data2).when(cond2).then(action2);

Here, using one approach to define a statement and another to create a strict separation between statements would make the language easier to read. But this is also where consistency comes into play. You wouldn't want method chaining to be used for creating statements, while method calls are used for separating statements sometimes and have method sequencing used for separating statements other times. Such inconsistencies can make any DSL difficult to learn and use and they are easy traps to fall into.

## Summary

Building an intuitive [internal] Domain Specific Language (DSL) takes more than just following commonly accepted development practices, like abstracting the expression language from the API. It requires a thoughtful understanding of how the language should be used and how it should not be used. Attention to things like the order of words and consistency within the language can go a long way towards making a language both usable and easy to understand.

[Bitbucket is the Git solution](https://dzone.com/go?i=201144&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=201144&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

### Like This Article? Read More From DZone
