# Inference Made Simple

_Captured: 2017-05-25 at 21:23 from [dzone.com](https://dzone.com/articles/inference-made-simple?oid=twitter&utm_content=buffer4c669&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Need to build an application around your data? [Learn more](https://dzone.com/go?i=200129&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) about dataflow programming for rapid development and greater creativity.

In a [previous blog tutorial](https://blog.grakn.ai/populating-mindmapsdb-with-the-world-5b2445aee60c), we demonstrated how to import some example SQL data into GRAKN.AI. In this article, we will work with the same data, which is about [countries and cities of the world](https://dev.mysql.com/doc/world-setup/en/). Here, we use it to illustrate how to use [inference](https://en.wikipedia.org/wiki/Inference) to find information that is stored implicitly within the dataset.

This article will be useful if you are getting started with GRAKN.AI and want a simple example of how to write inference rules using [Graql](https://grakn.ai/pages/documentation/graql/graql-overview.html). If you haven't already set up GRAKN.AI, please see the [previous tutorial](https://blog.grakn.ai/populating-mindmapsdb-with-the-world-5b2445aee60c), or check out our [setup guide](https://grakn.ai/pages/documentation/get-started/setup-guide.html).

## Introduction to Inference

Consider the following statements:

It is possible to infer the following:

The initial statements can be seen as a set of premises. If all the premises are met, we can infer a new fact (that sheep are vegetarians). If we hypothesize that sheep are vegetarians, then the whole example can be expressed with a particular two-block structure: IF some premises are met, THEN a given hypothesis is true.

This is how reasoning in Graql works. It checks whether a set of Graql statements can be verified and, if they can, makes an inference from a second block of statements. The first set of statements (the IF part or, if you prefer, the antecedent) is called the left hand side (LHS). The second part (also know as the consequent) is, not surprisingly, the right hand side (RHS). Using Graql, both sides of the rule are enclosed in curly braces and preceded by, respectively, the keywords `lhs` and `rhs`.

## Setting Up the Example

Our example can be found on GitHub in the [sample-projects repo](https://github.com/graknlabs/sample-projects/tree/master/example-inference). We aren't going to walk through how to migrate SQL data here, since that's a topic that was covered [previously](https://blog.grakn.ai/populating-mindmapsdb-with-the-world-5b2445aee60c), although the scripts to perform migration directly from SQL into GRAKN.AI are available in the repo (just consult the [readme file](https://github.com/graknlabs/sample-projects/tree/master/example-inference)).

For simplicity, we are going to load the ontology and data directly into GRAKN.AI. If you haven't already done so, please download and install the latest version of GRAKN.AI (I used 0.12), and start the engine from your terminal. If you're not sure about any of this, please see our [setup guide](https://grakn.ai/pages/documentation/get-started/setup-guide.html).

Download the example from the [sample-projects repo](https://github.com/graknlabs/sample-projects/tree/master/example-inference) and load the ontology into a graph:

Then load the data (this may take a few minutes):

## What's in the Data?

My esteemed colleague Miko already discussed inference in an [earlier blog article](https://blog.grakn.ai/how-to-find-information-that-is-not-there-de0d66360179). Things have changed a little in that the Graql syntax has moved on since he wrote it, but his article included a very nice explanation of how inference works using Italian cities, provinces, and regions to illustrate. It was such a neat example that I've found a practical example that is similar. Let me explain…

The SQL data I migrated into GRAKN.AI consisted of a number of tables. In this example, I'm looking at the table of data about countries and a separate table about cities. The countries table contains a number of columns with data about individual countries (such as their name, population, life expectancy, surface area, etc.). For simplicity, for each country, I migrate just the name, international country code, world region (for example, Eastern Africa, Southeast Asia) and continent it is situated in.

The city table contains a number of columns, but, in this example, I've imported the name of the city and the local district it resides in, which seems loosely based on the division of a country into states (for example, Texas, Iowa, etc. for the U.S.) or provinces/territories.

The city table also contains a country code to represent the country the city is located within. I've used that to build a relation between cities and countries using the GRAKN.AI [knowledge model](https://grakn.ai/pages/documentation/the-fundamentals/grakn-knowledge-model.html). The `has-city` relation is shown in the [ontology](https://github.com/graknlabs/sample-projects/blob/master/example-inference/ontology.gql), which is pretty simple, but I'll explain it further below:

IF a city is in a country, THEN it must be located in the same continent and world region as the country.

IF a country contains a city, THEN it must contain the local district in which the city is located.

![](https://cdn-images-1.medium.com/max/800/1*ZaXoWUxn2AVTJ5PeB9i5GQ.png)

> _A diagram of the world example ontology._

This is why, in the ontology, a `city` entity has a resource called `inf-continent`. The reasoner uses a set of "rules" that are a Graql version of what I've written above to work out `inf-continent` by inspecting the related `country` and the `continent` it resides in. Likewise, the `city` entity has a resource called `inf-world-region` and the `country` entity has a resource called `inf-local-district`.

As humans, we understand the concept that a city is in a country, and a country is in a continent, and thus a city is also in the same continent as the country. We have to write rules for a computer to make the same intuitive leaps.

At the bottom of the [ontology.gql](https://github.com/graknlabs/sample-projects/blob/master/example-inference/ontology.gql) file, you'll see the coded Graql rules for reasoning over the dataset. For example, to infer the continent in which a city is located:

You can find out more about writing rules from the [GRAKN.AI documentation](https://grakn.ai/pages/documentation/graql/graql-rules.html).

Note that while we are able to make inference using city, country, and continent information (and similarly for district and region fields), it isn't possible or sensible to apply the same model to all the information in the world dataset. For example, we cannot say that because the population of a country is one million, and a city is within that country, the population of the city is also one million, since a country is usually more than a city (Vatican City being a possible exception). We could write a rule that says that if the population of a country is `x`, we know that the population of any city within that country is less than `x`. Common sense, from a human brain, is needed before reasoning can take place!

## Making Some Queries

Let's make some queries to get some inferred knowledge from the world database.

Firstly, let's find out the local district, world region (inferred) and continent (inferred) for a couple of cities, Cardiff and Melbourne:

Melbourne is in Victoria, which is in Australia and New Zealand (region), which is in Oceania (continent).

So, Cardiff is in district Wales (that's in the data), but the reasoner is also telling us that it is in the British Islands (region), which is in Europe (continent).

Melbourne is in Victoria, which is in Australia and New Zealand (region), which is in Oceania (continent).

![](https://cdn-images-1.medium.com/max/800/0*vECkxhpcxFetvMMN.)

> _Now let's specify a country and find all the local districts in contains through reasoning._

Now let's get a bit more creative, and ask about cities containing the word "Victoria", and find out where in the world they are.

Now, let's get five cities in Oceania:

## Summary

The queries above show how information can be inferred from data, despite not being stored explicitly. It is a very trivial example, but the intention is to show the basics of reasoning and how to construct rules in Graql.

Of course, real-world models are filled with hierarchies and hyper-relationships, but this makes querying a dataset challenging, not least because traditional query languages are only able to retrieve explicitly stored data, and not implicitly derived information.

[Check out](https://dzone.com/go?i=200130&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) the Exaptive data application Studio. Technology agnostic. No glue code. Use what you know and rely on the community for what you don't. [Try the community version](https://dzone.com/go?i=200130&u=https%3A%2F%2Fexaptive.city%2F%23%2Flanding%3Freferrer%3DGeneral).
