# What Is an Ontology?

_Captured: 2017-03-16 at 21:26 from [dzone.com](https://dzone.com/articles/what-is-an-ontology?edition=283884&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-16)_

Whether you work in SQL Server Management Studio or Visual Studio, Redgate tools integrate with your existing infrastructure, [enabling you to align DevOps for your applications with DevOps for your SQL Server databases.](https://dzone.com/go?i=188128&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25667) Discover true Database DevOps, brought to you in partnership with [Redgate](https://dzone.com/go?i=188128&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25667).

## The Simplest Definition You'll Find… or Your Money Back*

This is a short blog post to introduce the concept of an ontology for those who are unfamiliar with the term, or who have previously encountered explanations that make little or no sense, as I have. I'm aiming to "democratize knowledge of this topic" as one of my colleagues put it.

![Image title](https://dzone.com/storage/temp/4626727-maze-cheating.jpg)

Having spent the last six months reading around this subject in my new role at [GRAKN.AI](https://grakn.ai/), with numerous frustrated and cyclical Google searches, I think I'm in a good position to attempt a simple explanation. If, like me, you aren't a philosopher, mathematician, or hard-core computer science PhD, you may be put off by definitions such as [this from Wikipedia](https://en.wikipedia.org/wiki/Ontology_%28information_science%29):

> "…an ontology is a formal naming and definition of the types, properties, and interrelationships of the [entities](https://en.wikipedia.org/wiki/Entities) that really or fundamentally exist for a particular [domain of discourse](https://en.wikipedia.org/wiki/Domain_of_discourse). It is thus a practical application of philosophical [ontology](https://en.wikipedia.org/wiki/Ontology), with a [taxonomy](https://en.wikipedia.org/wiki/Taxonomy_%28general%29)…"

> "An ontology is a formal, explicit specification of a shared conceptualization."

Maybe it's just me, but although I know the meaning of those words, I don't really understand anything when they're put together as above. Google isn't massively helpful either:

![](https://cdn-images-1.medium.com/max/1600/1*ookd6N7k3MgHKKh6B-IoyQ.png)

To be fair, if you stick with it rather than run away screaming, the Wikipedia article I cited above continues to explain that an ontology is:

> "…a model for describing the world that consists of a set of types, properties, and relationship types. There is also generally an expectation that the features of the model in an ontology should closely resemble the real world (related to the object)…"

This makes more sense to me, as I'm familiar with object-oriented C++, and it doesn't sound that unlike it. I thought I'd illustrate the definition with an example using an ontology in [GRAKN.AI](https://grakn.ai/) to define objects, express their properties, and show how the objects relate to one another.

Still with me? I hope I've not slipped into the territory of confusing semantic terminology just yet (by the way, please see the end of this article for more examples of ontological explicative horrors).

## The Grakn Knowledge Model

In Grakn, we use four types in an ontology:

  * **entity** \- Represents an object or thing. For example, a person, a man, a woman.
  * **relation** \- Represents relationships between things. For example, a parent-child relationship between two person entities.
  * **role** \- Represents the roles involved in a specific relation. For example, in a parent-child relation, there are roles of parent and child, respectively.
  * **resource** \- Represents the properties associated with an entity or a relation, for example, a name or date. Resources consist of primitive types and values, such as strings or integers.

Grakn has its own declarative graph query language, called Graql, for expressing an ontology that can be loaded into a graph. Let's look at a simple example from the [Grakn documentation](https://grakn.ai/pages/index.html), which uses genealogy data from a family that lived in the 18th and 19th century. Here is the ontology:

The `sub` keyword expresses sub-typing, so `person sub entity` is simply describing that a person is a sub-type of the built-in Graql `entity` type.

In the ontology above, there is one entity sub-type, or category of object, which is a `person`. The `person` can take one of two different roles in a `parentship` relation with another person entity: a `parent` or `child` role. The `parentship` relation has a single property associated with it (a date of birth), while the `person` entity has a number of properties, such as names, age, and gender.

![Image title](https://dzone.com/storage/temp/4626730-1vz5hicyhsqjgf7vbmo4pfa.jpeg)

Of course, this is a contrived example, designed to show the basic elements of a Grakn ontology. It is possible to build a more extensive hierarchy through inheritance (entities to represent a man or a woman could inherit from an abstract person entity for example) and to introduce additional relations and roles (for example, marriage).

## Why Do We Need an Ontology?

We need an ontology to allow Grakn to discover whether the data has any inconsistencies (also known as validation) and to extract implicit information from data (known as inference).

As an example of validation, consider a glitch in the data whereby a person was incorrectly named as a parent of themselves. In adding the data, Grakn would spot that a person entity was attempting to take both `parent` and `child` roles in a parentship relation, and would flag it up as an inconsistency.

Graql uses machine reasoning to perform inference over data types and relation types, to discover implicit associations. A nice example is to use the gender of a `person` to infer more specific details of their role in a `parentship` relation (whether they are the `mother` or `father`, or `daughter`or `son`).

We can extend the ontology we defined above to show those additional roles:

We also need to provide Graql with some "rules" to follow to infer these new roles in the parentship. I won't show them in Graql, as it isn't particularly readable, and the object here is to illustrate what they do rather than how they are written. In effect, they say that in a parentship relation:

  * If the parent is male and the child is male, the roles are `father` and `son`.
  * If the parent is female and the child is male, the roles are `mother` and `son`.
  * If the parent is male and the child is female, the roles are `father` and `daughter`.
  * If the parent is female and the child is female, the roles are `mother` and `daughter`.

The rules are applied by Graql across the dataset to build new information from what is already contained in the data.

To find out more about how to work with the Grakn knowledge model, we recommend you take a look at our documentation: in particular the [Quickstart Tutorial](https://grakn.ai/pages/documentation/get-started/quickstart-tutorial.html) and [Knowledge Model](https://grakn.ai/pages/documentation/the-fundamentals/grakn-knowledge-model.html) guide. If you're stuck or need to talk to us, please join our growing [Grakn Community](https://grakn.ai/community.html).

## *Money Back Guarantee

I hope this post has simplified a difficult topic to describe. As the article is provided for free, we are sorry that we can't offer you a refund if I failed. But let me know in the comments.

I'd like to be clear that I mean no disrespect to the original authors of some of the above terrifying explanations, who are experts in their fields and writing for the _cognoscenti_. Just for entertainment, here are a few other amazingly opaque definitions. Please hit us up in the comments or tweet [@GraknLabs](https://twitter.com/graknlabs) if we haven't included your personal favorite…

[Gruber 2008](http://web.dfc.unibo.it/buzzetti/IUcorso2007-08/mdidattici/ontology-definition-2007.htm): " …an ontology defines a set of representational primitives with which to model a domain of knowledge or discourse."

[Gene Ontology Consortium](http://www.geneontology.org/faq/what-ontology): "Ontologies are 'specifications of a relational vocabulary'. In other words they are sets of defined terms like the sort that you would find in a dictionary, but the terms are given hierarchical relationships to one another. The terms in a given vocabulary are likely to be restricted to those used in a particular field or domain, and in the case of GO, the terms are all biological."

If you liked this post, please take the time to recommend it or leave us a comment.

It's easier than you think to [extend DevOps practices to SQL Server with Redgate tools](https://dzone.com/go?i=188129&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25673). Discover how to introduce true Database DevOps, brought to you in partnership with [Redgate](https://dzone.com/go?i=188129&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25673).

Topics:

grakn.ai ,semantic database ,knowledge graph ,graql ,database ,tutorial ,semantic application

Opinions expressed by DZone contributors are their own.
