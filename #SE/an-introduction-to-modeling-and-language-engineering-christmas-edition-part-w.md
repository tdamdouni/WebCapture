# An Introduction to Modeling and Language Engineering – Christmas Edition Part 2

_Captured: 2018-01-03 at 16:20 from [blogs.itemis.com](https://blogs.itemis.com/en/an-introduction-to-modeling-and-language-engineering-christmas-edition-part-2?utm_source=hs_email&utm_medium=email&utm_content=59754756&_hsenc=p2ANqtz--tYRmRnArsY2sr83H6rWwTIdudlvNeW1vdPh14W_1fgcEsIz2oEzdGULrPecfdvcLY8Id84VGqlFAzteTK4K4onICZzw&_hsmi=59754756)_

Now, with the [basics of modeling covered in part 1](https://blogs.itemis.com/en/an-introduction-to-modeling-and-language-engineering-christmas-edition-part-1), we can look into something else itemis does on a regular basis to solve tricky problems: Language Engineering.

## About Models and Languages

As we have seen, modeling always implies the presence of an underlying meta model. In the LEGO® world the meta model includes the various types, shapes and colors of the building blocks and the principles of how they can be connected. So the meta model of any given LEGO® set is defined by the types of pieces provided in the box and the principles of how the pieces can be connected. The pieces and the connection mechanisms can be seen as the "language" of any given LEGO® set.

In software engineering models are often created based on text-based programming languages. In this case the meta model or "language" defines the syntax, the grammar and the possibility to include functions in the process of modeling.

Programming languages do not only vary in terms of their syntax and grammar, they are also different on the level of the underlying features and concepts.

C is often deployed on specialized hardware like microcontrollers. These controllers have limited resources and are often used in vehicles, industrial systems or home automation. The concepts and the structure of C mirrors the hardware instruction set and is optimized to be resource efficient.

Java in contrast is a higher level, object oriented programming language. It typically does not run on resource-restricted micro controllers but on servers with plenty of resources. Since Java programs often are bigger than software written in C, it includes higher level concepts that help to structure and reuse software functions e.g. by introducing classes with the ability to inherit abilities.

SQL - Structured Query Language - is another type of programming language. SQL is designed for one specific purpose: handling information stored in relational databases. The syntax and the provided functions therefore are tailored to the domain of relational databases.

While being different in scope and structure, C and Java both fall in the category of general purpose languages. They are not designed to solve one particular type of problem but can be used across many domains. Languages like C++, C#, Python or XML fall in the same category.

SQL in contrast is tailored to one group of tasks in one domain: the query and manipulation of relational databases. It therefore falls in the category of Domain Specific Languages or DSLs. Other DSLs are HTML or MATLAB.

What is the equivalent of general purpose languages in the world of LEGO®? Well, when I grew up there where only 5 or 6 LEGO® colors available, and the shapes of the blocks were mostly rectangular. LEGO® figurines looked very generic. Building a spaceship required some creativity and some the willingness to compromise.

Today there is a variety of Domain Specific LEGO® "DSLs" available. Pirates with their ships, policemen including German Shepherds - and even our Millennium Falcon.

![lego-millennium-falcon.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/Software%20Development/lego-millennium-falcon.jpg?t=1514992779618&width=2172&height=1446&name=lego-millennium-falcon.jpg)

> _(Picture by Kim Do-hyun: https://www.flickr.com/photos/stickkim/6966161674)_

Note the custom parts used in the spaceship and the custom figurines and their accessories. With a very specific task at hand - building a Millennium Falcon - custom parts like antennas or cockpit windows make the modeling process a lot more efficient and the results more impressive.

Building a LEGO® Millenium Falcon in 1976 would have been a much more challenging task. Wondering if anybody would have recognized Chewbacca with a red top and blue pants…

So who gets to enjoy the advantages of Domain Specific Languages - be it the realm of computer languages, system engineering or LEGO®? Well, not everybody.

In the past there had to be a significant number of potential users (= market size) of programmers, engineers or gamers to justify the development and maintenance of any DSL. Consequently, DSLs often maintained a rather broad and technical character - the common denominator of the targeted group of experts.

So if you belong to the group of specialists that need to write queries for relational databases (SQL) or if you are a Star Wars fan you are lucky and you get your DSL.

However, if your area of specialization or interest is "niche", you have to make do with general purpose languages and go back to using square and rectangular lego bricks.

Take away points:

  * The modeling language and the meta model are closely related. They define the functions and concepts that can be expressed by the model.
  * Domain Specific Language (DSLs) provide customized notations, syntax and meta models to efficiently express functions and concepts for specific domains. 
  * In the past, creating DSLs for computer languages or systems was cumbersome and expensive and therefore limited to larger user groups and/or broad, general domains.

## Language Workbenches

Now that the advantages of DSLs haven been established, the question is how to give more experts and specialists in their domains access to more efficient ways of modeling?

Luckily we finally have arrived in the age of 3D printing!

Licensing and copyright issues aside, a 3D printer in conjunction with the matching software would allow LEGO® players to define and print any LEGO® parts of their choice. Unicorns instead of horses: simply print them! Star Trek instead of Star Wars figurines: just print them!

The new parts now can be engineered exactly to the player's needs.

Fortunately, with respect to creating Domain Specific Languages in modeling and software engineering, there also have been significant advances in the past years.

Martin Fowler's concept of Language Workbenches (LWB) is already more than a decade old. His vision and ideas in the meantime became reality.

Language Workbenches are software tools that are designed to efficiently build new programming languages including their syntax, grammar and underlying concepts (= meta models).

Language Workbenches are the "3D printers of software engineering". They allow the efficient creation of DSLs - even for very small groups of experts with very specific modeling needs. The user group for DSLs can now be as small as one team in one department.

Today, a number of Language Workbenches are available. One category focuses on a textual modeling approach. A popular example for a textual Language Workbench is Xtext.

Projectional Language Workbenches on the other hand are not limited to one type of notation. Instead they can flexibly project the content of models in any type of representation according to the user's needs and preferences. Jetbrain's Meta Programming System (MPS) today is the most popular projectional Language Workbench.

Projectional LWBs store model data in trees. This specific tree is also referred to as Abstract Syntax Tree (AST). The modeling information is stored in the elements of the AST and can then be projected to any notation: a text, a table, a mathematical formula or any form of graphical representation. As part of the projection process, the system can highlight certain aspects of the underlying model and hide other aspect. The user can flexibly pick and choose the abstractions relevant for the task at hand - "abstractions on demand".

Let's have a brief look at one real world example.

Security experts analyze and evaluate the security properties of technical systems. This could be a vehicle or an IOT device. In order to do that they have to first understand the basic structure and the main functions of the system. Here, they work closely with the engineering team that is familiar with the components, interfaces and data associated the with system. Based on this structure, security goals, attack vectors, damage potentials and propagation paths have to be modeled in an iterative way. Identified risks then are mitigated by e.g. adding encryption and the required keys. This in return has an affect on the original architecture and functions of the system.

While it is not important to fully understand every detail of the specific workflow above, the modeling challenges hopefully become clear. We have to define a model that designers, architects and security engineers can work on simultaneously while focusing on different aspects of the model. And, different tasks within the process benefit from different notations: graphs, tables, text, charts etc.

What a DSL in a customized editor built with a projectional language workbench could look like is depicted below. Please note that these are different projections of ONE model emphasizing different abstractions for different steps in the analysis phase incorporating a specific DSL for the security domain.

![DSL-Workbench.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Software%20Development/DSL-Workbench.png?t=1514992779618&width=2172&height=1230&name=DSL-Workbench.png)

Take away points

  * Language Workbenches are tools to efficiently build Domain Specific Languages. They are the "3D Printers of software engineering".
  * Projectional Language Workbenches give advanced modeling options as they can provide different views and notations on the same model.   


## **  
So what is the job of a Language Engineer?**

Language Engineers solve challenging problems in the realm of system or software modeling by creating Domain Specific Languages and models.

Often these problems are the result of increased complexity and the inability to manage this complexity with the established software tools and methods.

The reasons for the increased complexity can vary. From a growing number of functions and product variants, stricter regulatory documentation needs or the requirement to analyse the dependencies of cross cutting concerns like costs, performance, safety & security along the entire product development process.

Often weak meta models, e.g. requirements written in plain prose text, and the missing tool support for the experts "to get their models right" are the root cause for the need to advance in the area of methods and tools.

Language Engineers are typically part of a multidisciplinary team that includes team members and domain experts from the customer side. This always implies that language engineers get deep insights into many different domains: from automotive to industrial automation, medical, insurance or telecommunication. Language engineers also have to learn and understand dependencies of the work products of different user groups on the customer side. Jointly with the domain experts language engineers then help finding the right abstractions including the syntax, grammar and functions to model all relevant aspects of a domain. Language engineers are usually also involved in designing and building the tools that allow the domain experts to then create and work with the models.

The DSLs and the tool created for the purpose of the security analysis above is a typical example for the work of language engineers. Security methodology experts, potential users from different customers and the itemis language engineers defined the model including the relevant abstractions, suitable notations and projections. itemis then built the editor, in this cased based on a projectional LWB MPS from Jetbrains, to model, analyze and document security analysis projects.

If DSLs and language engineering sound like viable business approaches or exciting personal challenges for you for 2018, feel free to reach out and find out more.

But for the days ahead: work less and play more! Perhaps with LEGO®.

Enjoy the festive season and have a happy and healthy 2018!

![techy-merry-christmas-blue.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/Software%20Development/techy-merry-christmas-blue.jpg?t=1514992779618&width=2172&height=1035&name=techy-merry-christmas-blue.jpg)
