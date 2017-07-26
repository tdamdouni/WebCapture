# Software Development is Not a Form of Construction

_Captured: 2017-02-11 at 10:50 from [agilepainrelief.com](https://agilepainrelief.com/notesfromatooluser/2015/04/software-development-is-not-a-form-of-construction.html?utm_content=bufferf26cb&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer#.WJ7eWNe1KaM)_

![original graphic design by Freepik](https://agilepainrelief.com/wp-content/uploads/2015/04/construction1.jpg)

For years the software industry has used an analogy, with construction as its defining metaphor. The comparison is applied throughout the language of software: architecture, foundations, constructor, projects, building code. The language is so pervasive that it affects our thinking around software development, but unfortunately the metaphor is fundamentally broken and the flaws have led us down a number of bad paths.

In construction, a lot of emphasis is placed on predictability, getting the requirements correct up front, and cost reduction. These are all signs of a mature industry. We run into problems when we try to apply the same emphasis in software.

##### Rules of Thumb, Construction Codes, and Materials

Modern construction can trace its routes back hundreds or thousands of years, depending on where you put the starting line. As a result of all this history, there is a great deal of expertise codified in rules of thumb:

- In most areas the construction costs per square foot are a well-known constant. For instance, we recently did some home renovations and were warned by friends in the industry that the typical renovation in Ottawa costs from $35-50/sq ft. They were bang on.

- A good estimate for the depth of a concrete floor slab is the same as a 1/180 of its unsupported perimeter.  
(_The last from: [Designing With Your Thumb](http://www.beingbrunel.com/designing-with-your-thumb/) - Thomas Michael Wallace_)

Software, on the other hand, is at best 70 years old. Its rules of thumb don't have the same solid history to warrant unwavering application.

Eventually rules of thumb are codified and fixed as building codes. When constructing houses, building codes determine everything from how far apart the studs in the wall are, to the amount of insulation in the walls and roof. These codes mean that all houses meet a minimum standard and greatly increase the predictability of cost.

It is possible to have these construction codes because there are limited sets of building materials (wood, steel, etc) and tools (hammer, saw, etc). The properties of the materials and their failure modes are predictable, and the toolset that is used to work with the materials is small and well understood. Sure, materials and tools continue to evolve in the construction industry, but at nowhere near the same rate as evolution in software.

It's much harder to keep up with the list of new materials and tools in software. Programming languages, libraries, and supporting tools appear and evolve every year, as does their content. And even if we just stick to our existing languages and libraries, it may take years to explore all of their details and nuances to the extent that would be required for standardized codes.

It's the well-understood, stable materials and tools that make building construction codes possible. The instability of the software world guarantees that we will never have construction codes in our field.

## _There are no useful Rules of Thumb or Construction Codes in the software industry._

##### Physical Constraints and Stable Requirements

Buildings, bridges, and other construction works are governed by well-known physical limits. These limits dictate the size, shape, and use of a structure depending on the materials used. For example, wood framed buildings are limited in height from four to six stories. Bridge spans are limited in length by the materials used and how the properties of those materials relate to the physics involved.

The construction of buildings and bridges represents a problem domain that has been studied and tested for generations. As a result, the questions that have to be asked of the client are predictable and the range of possible answers is constrained.

Construction design has to fit into the constraints of site and function. As much fun as it might be to imagine an office building that spins around a single point like a gyroscope, it's both physically impossible and wouldn't meet the functional need. When building bridges or roads, there are clear standards for each jurisdiction based on the type and size of vehicle that you need to support.

Software isn't subject to these same constraints. If the customer really wants the equivalent of a gyroscope, we can probably deliver it. The types of users - and uses - that we need to support are far more widely varied than those in construction.

Once a building has been started and the foundation has been poured, you can't easily change the size or location on the site. Once the internal structure of a building has been started, you can't just decide to add a new elevator shaft or new wing to the building. When the footings of a bridge are in place it can't be moved 20m because the customer decides the bridge was in the wrong place. (Okay, you can, but effectively it requires you to throw away all existing work and start again from scratch).

With software we can make almost any change we want - from the simple to the complex, such as increase the number of supported users from 100 to 1000; change the product direction (_Yelp - started life as a tool to send friends recommendations for restaurants, doctors etc. It took on life as a review site only when the original functionality flopped._), change the programming language (_I've worked projects that moved from Java to .NET and back to Java_) - all for much less cost than starting again from scratch.

Because we have much greater flexibility in software, we are also able to accept changing requirements throughout the development process. Requirements that are discovered early in the development process often change a number of times before they're finally implemented.

In the world of construction, the architect can hand the builders a set of blueprints with fair confidence that the builder will interpret them correctly. While there will still be dialogue and a need for changes, the degree of change is nothing like the world of software. In software we have no effective way (even UML) to hand a blueprint to the developers and walk away. Instead of a blueprint, we have a series of ongoing conversations between the customer and the people building the software.

## _Software is open to far greater change than construction._

##### People

In construction, tradespeople are generally considered interchangeable and replaceable. It's assumed that if you change carpenters while framing a house, the results of their work will generally be the same.

In the game of software this is clearly not true. Because of the complexity and variance in both the tools (programming language and libraries) and problem domain developers, business analysts, testers and UX designers can't just be moved from one area to another.

People who see a relationship between software and construction often assume that people are replaceable and interchangeable. That is far from the truth. All substantial pieces of software are built by teams of people, so if you interchange or replace one team member with another, it costs a team in three major ways:

- They lose the tacit knowledge that their former team member had.

- They have to train the new team member on what they're building and what they have built so far.

- They have to spend time establishing an effective working relationship with the new person.

As a result, replacing or adding a new person slows the whole team down for at least 3-4 months. Individually, the new team member often takes even longer than that to become fully productive. While construction also suffers slow downs when people are changed, it will be to nowhere near the same degree as a software project.

Over 40 years after it was first written, the old [Fred Brooks](http://en.wikipedia.org/wiki/The_Mythical_Man-Month) quote still applies: "Adding more people to a late project just makes it later".

##### Conclusion

The construction metaphor that is often used to describe software is wrong. Sadly, because of its implications, we put a lot of emphasis in the wrong places:

* Getting the requirements right upfront instead of accepting that change is the norm

* Emphasizing the importance of architecture and architects instead of accepting that software is adaptable and can be change by anyone on the team

* Assuming people are replaceable and that problems related to time can be solved by adding more people instead of accepting that people are unique

* Seeking predictability instead of accepting our domain that isn't well understood

## _Software is in no way related to construction._

## _We're not building, we're exploring._

We're exploring the problem space of our customers. We're creating new ideas that happen to be expressed in code. So let's leave the old construction metaphors behind, because they're crumbling the foundation of the roads we're travelling together.

I'm not the first to explore this vein. Other views:

Martin Fowler: [The New Methodology  
](http://www.martinfowler.com/articles/newMethodology.html#SeparationOfDesignAndConstruction)StackOverflow: [What's wrong with the software construction analogy  
](http://stackoverflow.com/questions/1241912/whats-wrong-with-the-analogy-between-software-and-building-construction)Thomas Guest: [Why Software Development isn't Like Construction](http://wordaligned.org/articles/why-software-development-isnt-like-construction)  
Mishkin Berteig: [The software construction analogy is broken](http://www.kuro5hin.org/story/2003/3/13/211831/159)

_Image by Agile Pain Relief Consulting. Elements of image [designed by Freepik](http://www.freepik.com/)._
