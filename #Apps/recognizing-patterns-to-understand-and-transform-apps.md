# Recognizing Patterns to Understand and Transform Apps

_Captured: 2017-07-30 at 20:50 from [dzone.com](https://dzone.com/articles/recognizing-patterns-to-understand-and-transform-a?edition=0&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-07-30)_

What every Java engineer should know about microservices: [Reactive Microservices Architecture](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Futm_source%3Ddzone%26utm_medium%3Dpre-roll-text%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Djava-zone). Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Futm_source%3Ddzone%26utm_medium%3Dpre-roll-text%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Djava-zone).

Code is arguably the most valuable asset for many organizations. However, the value trapped in the code is not easy to use.

Why?

In this article, we are going to see how we can extract and process knowledge in code by specifying patterns. We will see:

  1. A clear example of what we mean by extracting knowledge from code.
  2. An explanation on how to implement this approach in practice (with code available on GitHub).
  3. Why we want to extract knowledge from code.

## Diving In

Let's see what we mean in practice with the simplest example we can come up with. And let's see it working with real code.

Of course, recognizing properties is a very simple example, something we are all familiar with, but the same idea can be applied to more complex patterns.

There are many patterns that can be used:

  * Patterns typical of a language: Think about for loops to iterate over collections.
  * Design patterns: singleton, observer, and delegate, to name just a few.
  * Patterns related to frameworks: Think about all the applications based on MVC or the DAO defined to access database tables.
  * Project-specific patterns: For example, in [JavaParser](http://javaparser.org/), we use the same structure for the dozens of AST classes we defined.

Patterns can range from small pieces of a single method to the organization of entire applications.

Patterns can also be applied _incrementally_: We can start recognizing smaller patterns, making the application simpler, and then recognize more complex patterns over the simplified application.

## How Knowledge Ends Up Being Trapped in Code

Developers use a lot of small, idiomatic patterns when writing programs. Experienced developers apply them automatically while implementing their solutions. Slowly, they build these large applications that contain a lot of knowledge, which is enshrined in the code.

The problem is that the initial idea is not stated explicitly in the code. The developer translates it into code by using some of the idiomatic patterns typical of the language, or patterns linked to the framework they're using, or those that are specific to the organization.

Somewhere, a developer is thinking: "This kind of entity has this property," and they are translating it to a field declaration, to a getter and a setter, to a new parameter in a constructor, to some additional lines in the _equals_ and the _hashCode _methods. The idea of the property is not explicitly present in the code: You can see it if you are familiar with the programming language, but it requires some work.

> There is so much noise, so many technical details that shadow the intention

But this is not true just for Java or for properties: When a developer determines that an object is unique, they could decide to implement a singleton, and again, this means following certain steps. Or maybe the dev wants to implement a view or a Data Access Object (DAO) or any other typical component required by the framework they are using. In any case, all the knowledge is scattered in the code and difficult to retrieve.

Why is this bad?

For two reasons:

  * It is difficult to _see the knowledge._
  * It is difficult to _reuse that knowledge._

### Knowledge in Code

A lot of work goes into understanding a problem and building a representation of the solution in the code. There are a lot of micro-decisions, a lot of learning involved in the process. Then, all of this effort leads to knowledge.

Where does this knowledge go?

This knowledge is typically not written down directly, it is instead represented in the code. The fact is that, on many occasions, this knowledge is translated in a _mechanical_ way into code. Therefore, this translation can be reversed. The problem is that to _see _the knowledge present in the code, you need to look directly at the code, read it carefully, and mentally deduce the knowledge that is present there.

To understand things:

  * We need to understand programming and the typical patterns we use.
  * We need to check the details.
  * This process is done mentally, the result is just in our head and cannot be processed automatically.

If the knowledge was represented directly, to a higher level of abstraction, it could be easier to check, and it could be accessible to more people.

### Difficulty Reusing Knowledge

We have seen that, basically, the only way we have to extract knowledge from code is reading it and understanding it. The results stay in our head, so they are not usable by a machine. If we instead had a representation of the abstract knowledge, the original intentions, we could elaborate them for different goals.

We could, for example, use that knowledge to **generate diagrams or reports**.

Do you want to know how many views have been written? How many tables we have in the database? Easy! Project managers could get their answer without having to ask. And they would get always the updated, honest answers on the state of the code.

We could also use that information for re-engineering applications, even partially. Some aspects of your application could be **migrated to a different version of a library**, to a different framework, or even a different language. It would not mean that complex migration could be performed completely automatically, but it could be a start.

## Implementation Using the Whole Platform

Ok, we have talked about the problem, so let's talk about a solution we can build today.

We previously discussed how to [build grammars using the Whole Platform](https://tomassetti.me/getting-started-with-the-whole-platform-grammars/), and we have seen it when looking into [Domain Specific Languages](https://tomassetti.me/domain-specific-languages).

The code is available [on GitHub](https://github.com/wholeplatform/whole-examples), courtesy of Riccardo Solmi, the author of the [Whole Platform](https://whole.sourceforge.io/).

### Defining Higher Level Concepts

First of all, we need to define the higher level concepts that we have in mind but are not expressed _explicitly_ in the code. For example, the concept of a property of a Java bean.

In model-driven parlance, we define the metamodel: i.e., the structure of those concepts.

### Define How to Recognize Such Concepts in Java Code

Once we have those concepts defined, we need to specify how to identify them in the code. The Whole Platform uses a Domain Specific Language to specify patterns. It looks like this:

![](https://i0.wp.com/tomassetti.me/wp-content/uploads/2017/07/Screen-Shot-2017-07-01-at-10.45.00.png?w=1394&ssl=1)

> _What are we saying here?_

We are saying that a certain pattern should be looked at in the selected node and all its descendants. The pattern should match the given snippet: a Field Declaration with the private modifier, associating the label _type_ with the type of the field and the label _name_ with the name of the field.

![](https://i0.wp.com/tomassetti.me/wp-content/uploads/2017/07/Screen-Shot-2017-07-01-at-10.45.00-copy.png?w=353&ssl=1)

What should happen when we recognize this pattern?

We should:

  1. Remove the corresponding getter: We will match a method with the expected name (calculated by the _getterName_ function), the expected type, taking no parameters, and returning a field with the expected name.
  2. Remove the corresponding setter: It should be a method returning void, with the expected name, the expected parameter, and assigning the parameter to the field with the expected name.
  3. It should replace the Java field with this higher-level concept representing the whole property (here, it is named Field, but Property would have been a better name)
![](https://i2.wp.com/tomassetti.me/wp-content/uploads/2017/07/Screen-Shot-2017-07-01-at-10.45.00-copy-2.png?w=747&ssl=1)

Now, we just need to add this action into the contextual menu, under the group name _Refactor_. We can do that in Whole by defining actions.

![](https://i2.wp.com/tomassetti.me/wp-content/uploads/2017/07/Screen-Shot-2017-07-01-at-10.45.39.png?w=491&ssl=1)

Voila! We have now the magic power of recognizing patterns in any piece of Java code. As easy as that.

### Doing the Opposite: Expand the Concepts

So far, we have discussed how to recognize patterns in code and map them to higher level concepts.

However, we can also do the opposite: We can expand higher level concepts into the corresponding code. In the Whole Platform, we can do this with this code:

![](https://i1.wp.com/tomassetti.me/wp-content/uploads/2017/07/Screen-Shot-2017-07-01-at-10.46.06.png?w=928&ssl=1)

> _Let's focus exclusively on the property definition. Each instance is expanded by:_

  1. Adding a field declaration.
  2. Adding a getter.
  3. Adding a setter.
  4. Adding a parameter to the first constructor.
  5. Adding an assignment in the first constructor. The assignment takes the value of the parameter added and assigns it to the corresponding field.

Now, the way we recognize the pattern and the way we reverse it is not 100% matching in this example. Bear with us over this little discrepancy. We just wanted to show you two different ways to look at properties in Java.

![](https://i1.wp.com/tomassetti.me/wp-content/uploads/2017/07/Screen-Shot-2017-07-01-at-10.46.06-copy.png?w=826&ssl=1)

## What This Approach Could Be Used For

We see this approach being useful for three goals:

  * Running queries to answer specific questions about code.
  * Understanding applications.
  * Transforming or re-engineering applications

### Queries

We could define patterns for all sort of things. For example, patterns could be defined to recognize views defined in our code. We could imagine running queries to identify patterns. Those queries could be used **by project managers or other stakeholders** involved in the project to examine the progress of the project itself.

They could also be used **by developers** to navigate the code and familiarize themselves with complex code bases. Do we need to identify all observers or all singletons in this legacy codebase? Just run a query!

### Understanding Applications

The fact is that programming languages tend to be very low level and very detailed. The amount of boilerplate code varies between languages, sure, but it is always there.

Now, one problem is that the amount of code could hide things and make them difficult to notice. Imagine reading 10 Java beans in a row. Among them, there is one that implements the _equals_ method slightly differently from what you would expect -- like for some reason it ignores one field or compares one field using identity instead of equality. This is a detail that has a meaning but that **you would very probably miss** as you look at the code.

Why is that?

This happens because after looking at a large amount of code and expecting to see certain patterns, you become _blind_ to those patterns. You stop reading them without even noticing it.

By recognizing patterns automatically (and precisely), we can represent higher level concepts and easily spot things that do not fit in common patterns, like slight differences in _equals _methods.

We have seen how to recognize bean properties, but we can go further and recognize whole beans. Consider this example.

![](https://i2.wp.com/tomassetti.me/wp-content/uploads/2017/07/Patterns.001-2.jpeg?w=979&ssl=1)

This shows the relevant information. All the redundant information is gone. This makes things obvious.

We can recognize incresingly complex patterns by proceeding incrementally. In this way, exceptions pop up and do not remain unnoticed.

### Transforming Applications

When we write code, we translate some higher level ideas into code and follow an approach that depends on the technology we have chosen. Over time, the best technology could change, even if the idea stays the same. We still want the same views, but maybe the way to define them has changed in the new version of our web framework. Maybe we still want to use singletons, but we decided it is better to use public static methods with lazy initialization to provide the instance, instead of using a public static field.

By identifying higher level concepts, we could decide to translate them differently, generating different code. This process is called re-engineering, and we can perform it automatically to some extent. It seems like a good idea to me, and it is another advantage of using patterns to identify higher level concepts.

## Summary

Code has an incredible value for organizations because it captures a lot of knowledge in an executable form. As we evolve our applications and cover more corner cases, we improve our knowledge and our code. After years of developing a code base it becomes often invaluable for the organization owning it. However, that value is pretty much frozen: There is not much we can do with it. It is even difficult to understand exactly how much information there is in the code.

We think that one approach to extracting knowledge from the code is proceeding bottom up: recognizing the small abstractions and composing over them, step by step, until we recognize larger structures and patterns and can representy the big picture hidden in our application.

Using the Whole Platform is invaluable for these experiments.

Microservices for Java, explained. Revitalize your legacy systems (and your career) with [Reactive Microservices Architecture](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Futm_source%3Ddzone%26utm_medium%3Dpost-roll-text%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Djava-zone), a free O'Reilly book. Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Futm_source%3Ddzone%26utm_medium%3Dpost-roll-text%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Djava-zone).

### Like This Article? Read More From DZone
