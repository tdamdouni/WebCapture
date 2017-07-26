# Calculating Dependency

_Captured: 2017-04-16 at 10:31 from [dzone.com](https://dzone.com/articles/dependency?edition=290923&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-15)_

[Download Microservices for Java Developers](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034): A hands-on introduction to frameworks and containers. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034).

What does the concept of dependency mean in programming? Is it important in modern development process? Does the concept of dependency have a different meaning when we speak about procedural programming, object-oriented programming, or functional programming? In this post, I will try to sum up all the knowledge I gained during my life as a software developer.

## The Very Beginning

First of all, we need to have, clearly in mind, the concept of dependency in everyday language. _Merriam-Webster_ gives the following definition of dependency:

> The quality or state of being influenced or determined by or subject to another.

Clarifying. Sometimes we simply need to return to our roots for a deep understanding of a concept. So, a component that is dependent on another is influenced by it. What does that mean? If a component changes internally, its implementation, or externally, its interface, it is probable that all dependent components should change accordingly.

We have just derived that _dependency between two components is a measure of the probability that changes to one component could affect also the other_. The stronger the dependency between the components, the higher the above probability.

### **Coupling**

Coupling between components measures their degree of dependency. Tightly coupled components have a high probability of changing together; loosely coupled components have a lower probability.

In software engineering, we have a _mantra_ that was taught to us from the very beginning:

> Dependency between components must be minimized, making components loose coupled.

Why is this principle so important? The main concept behind it is that we should be free to change a component to resolve a bug, or to add a new feature, or to do whatever we want, without having to worry about changes to other components of the architecture.

Why are changes considered so dangerous in software development? Every time we change a component, there is the risk that we are introducing a bug. To avoid regressions, we have to re-execute all tests associated with the changed components (what if we have not automated testing? Ask [Robert C. Martin](https://8thlight.com/blog/uncle-bob/2014/05/02/ProfessionalismAndTDD.html)…)

Moreover, we might not directly own the dependent components. In such cases, changes must be discussed with external developers, properly scheduled, and so on. This is one of the main reasons that stops the evolution of an architecture.

Finally, this principle is so important because of the dynamism of software architectures. There is no software product that does not change over its lifetime. Changes happen, changes are part of the software world.

## Object-Oriented Programming and Dependency

In object-oriented programming, the above concept of the component is usually identified by a _type_. Basically, in object-oriented programming, we are interested in dependencies among types -- concrete types (classes) or abstract types (abstract classes and interfaces).

The different kinds of dependency between types are well-summarized in the following figure.

![Different kinds of dependency between types in Object Oriented Programming](http://rcardin.github.io/assets/2017-04-10/types_dependencies.png)

The figure maps all possible types dependencies into four equivalence sets. The notation used is UML. Let's have a brief look at every one.

### **Dependency**

On the left, we find the weakest form of dependency. With a dashed arrow between two types in UML, we model a dependency that:

> declares that a class needs to know about another class to use objects of that class.

The following code fits exactly the above definition.

As you can see, the only part of `A` that `B` needs to know is the interface inferred by `A` methods. So, if `A` changes its interface, i.e. the signature of method `methodA`, a change in `B` might be required.

### **Association**

Increasing the level of dependency, we find _association_.

> Association means that a class will actually contain a reference to an object, or objects, of the other class in the form of an attribute.

Translating into code, we have something similar to the following.

Different from the previous category, an association means that a class is _made of_ references to other classes. Their behavior starts to be more coupled because the relationship between the types is not temporary anymore, but it starts to be something permanent (i.e. throughout the lifetime of an object).

In our example, references to `A` inside `B` are allowed in every method of the latter, widening the scope of possible dependencies from `A`.

### **Aggregation and Composition**

Aggregation and composition are stronger versions of the association relationship: They add additional properties to the latter. Essentially, an aggregation states that one type _owns_ the other, which means that it is responsible for its _creation_ and _deletion_.

The composition adds the feature where if `B` is a composition of `A`, then there can be only an instance of the first that owns an instance of the second. Instances of `A` _are not shared_ among different instances of `B`.

An example of composition is represented by the following code.

These relationships generate a strong dependence between types because one type has to know how to build an instance of the other.

### **Inheritance**

_Inheritance_ represents the strongest type of dependency relationship that can be defined between two different types.

> If you find yourself saying that the class is a type of another class, then you might want to consider using inheritance (or generalization).

`A` is known as a _parent class_, whereas `B` is known as _child class_.

> A child class inherits and reuses all of the attributes and methods that the parent contains and that have public, protected, or default visibility.

Inheritance is also known as _implementation reuse_. The quantity of code that is shared among the two types is huge. It is possible that every change to `A` can result in a change to `B`. This is the real _tight coupling_! And did you notice that, using inheritance, the _information hiding_ principle is not respected anymore?

However, not all the types of inheritance are bad guys. Inheritance from abstract types mitigates the drawbacks of this kind of relationship. Why? The lower the shared code, the lower the degree of dependence. _Type inheritance_, which means that a class implements an interface, it is not harmful: Only interface methods' signatures are shared.

## Calculating the Degree of Dependency

You should have noticed a pattern from the above descriptions. The more the quantity of shared code between two types, the stronger the dependency. It is also true that the wider the scope of this dependency in terms of time, the stronger the dependency.

It would be nice if there was a mathematical formula to calculate the degree of coupling between two classes. With the information that we gave, we can try to formalize it.

Given two classes. `A` and `B`, the degree of dependency between them can be derived using the following formula.

![Dependency formula](http://rcardin.github.io/assets/2017-04-10/dependency_formula.png)

is the quantity of code (i.e., SLOC) that is shared between types `A` and `B`.

is the total amount of code (i.e. SLOC) of the `B` class.

is a factor between 0 and 1. The wider the scope between `A` and `B`, the greater the factor.

Here's the result. The values range between 0 and 1: A value of 0 corresponds to no dependency, and a value of 1 corresponds to the maximum degree of dependency.

When `A` and `B` hold the weakest type of dependency we saw so far,

is near to 0, whereas it is near to 1 when inheritance holds.

For example, if `B` inherits from `A`, then, the shared code is represented by all the code of `A` that does not have a `private` scope. Whereas, if a method of `B` simply refers to an instance of `A` among its parameters, the shared code will be represented only by the signatures of `public` methods of `A`.

It is important to note that the degree of dependency between `A` and `B` it is directly proportional to the probability that if `B` is changed, `A` should be changed accordingly.

![Dependency formula](http://rcardin.github.io/assets/2017-04-10/degree_proportionality.png)

Finally, the total degree of dependency of type `A` can be calculated as _the mean_ of the dependency degrees with respect to every other single type in the architecture.

![Dependency formula](http://rcardin.github.io/assets/2017-04-10/total_dependency_degree.png)

## Conclusions

Summing up, we gave a definition of dependency in software engineering. We tried to understand why dependency among components should be minimized. We revised how UML helps us to visually manage the dependencies, in the object-oriented world. With this information, we tried to formalize a formula to calculate the degree of dependency between two classes.

[Download Modern Java EE Design Patterns](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035): Building Scalable Architecture for Sustainable Enterprise Development. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035).
