# An Introduction to Modeling and Language Engineering – Christmas Edition Part 1

_Captured: 2018-01-03 at 16:22 from [blogs.itemis.com](https://blogs.itemis.com/en/an-introduction-to-modeling-and-language-engineering-christmas-edition-part-1?utm_source=hs_email&utm_medium=email&utm_content=59754756&_hsenc=p2ANqtz--tYRmRnArsY2sr83H6rWwTIdudlvNeW1vdPh14W_1fgcEsIz2oEzdGULrPecfdvcLY8Id84VGqlFAzteTK4K4onICZzw&_hsmi=59754756)_

It's Christmas time again. Time to work less and play more. As a kid, a parent or just for the fun of it.

Christmas is also the time of meeting friends and family and answering questions like "How is your job?" and "What does itemis do?".

With modeling and language engineering being the core of many itemis projects and activities, let me try to introduce some modeling basics with the help of games and toys - hopefully making it a bit more accessible and fun!

## About Models, Abstractions and Meta Models

Already back in 1976 the statistician George Box figured it out: "All models are wrong!"   
The Playmobil horse was never a real horse, the LEGO® spaceship was not a real spaceship and Super Mario and Lara Croft were not real either. But we didn't have a problem with them not being real because they were perfectly useful to play with.

Let's take the Millennium Falcon from the Star Wars universe as an example to explain a few things that we deal with at itemis every day: models, abstractions and meta models.

For those born before 1932 or after 2014, this is a picture of the Millennium Falcon.

![Millennium-Falcon.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/Software%20Development/Millennium-Falcon.jpg?t=1514992779618&width=2172&height=1629&name=Millennium-Falcon.jpg)

> _(Picture by William Warby: https://www.flickr.com/photos/wwarby/31618033034)_

It is obvious that a "real" Millennium Falcon is a pretty complex system: hyperdrive, weapons, hiding places and so on. Spaceships are very big and very expensive to build.

So in order to model a spaceship as a useful toy, we have to introduce abstractions. The abstractions define the specific aspects that the model encompasses. This reduces complexity and also makes the model affordable.

Here are a few examples of how to model the Millennium Falcon and what the main characteristics of the models are:

  1. A LEGO® model: consists of colored plastic components that can be be mechanically attached to one another, representing the rough shape and color of the spaceship. It is a lot smaller than a real spaceship. It can't fly.
  2. A iron cast mode: made of metal like a real spaceship. No moving parts to play with. Does not fly.
  3. A CAD computer model: digital model of the structure and geometry of the individual components of the spaceship and how they relate to each other. Still can't fly.
  4. A space ship model in a Star Wars computer game: digital model, looks exactly like the real thing, it includes behavior of the real Millennium Falcon: and yes, it can fly!

All of the above models are useful in different scenarios and for different types of users. Hundreds of other models exist serving different purposes and focusing on different aspects of the physical structure, the components or the behavior of the Millennium Falcon. Think of photos, puzzles or live-size models used in the film studios during the production of the Star Wars movies.

Take away points:

  * Models are very useful representations of our reality: we use them all the time.
  * Models reduce complexity by introducing abstractions.

Now that we have an idea what models are, we can have to look at another important modeling aspect: meta models.

Meta models define the elements that can be used in the modeling process and how they relate to one another. In the world of LEGO® the meta model defines the type of building blocks and the way they can be connected.

Meta models can also be seen as the rules that are associated with building the model. Strong meta models enforce strict rules and boundaries when creating a model. Weaker meta models give more freedom and apply fewer restrictions.

Creating a clay model of a spaceship gives maximum freedom and creativity in the modeling process. The shape, the size and the details of the ship can vary greatly. The clay does not restrict guide the modeling process. The clay meta model is weak.

A 500 piece puzzle of our Millennium Falcon in contrast has the strongest possible meta model. There is only one way to use the puzzle correctly. There is no room for creativity in the process. The puzzle's meta model automatically helps you to "get it right" as missing or wrongly placed parts can easily be spotted.

The LEGO® model is in between the clay model and the puzzle model in terms of the degree of freedom and the number of limiting rules. It allows the player to combine the available parts in a very flexible way while at the same time enforcing some basic rules: e.g. bricks only fit together in a certain orientation.

What is more fun to play with? That only depends on personal preference.

What is more fun to work with? That depends on the task at hand.

If the model is small and easy enough to fully understand all dependencies and side effects, then a weak meta model with hardly any rules might just be fine. Think of Microsoft Word® or Powerpoint® as "clay of system modeling" - with no real limitation to the author's creativity.

In a more complex world with thousands of requirements, product variations and many sometimes conflicting forces such as cost, performance, safety and security you might want to give up some "creative freedom" and in return get some support from the system to ensure the model's correctness or completeness.

Take away points

  * Meta models define the underlying model elements and how they relate to each other. In a very real sense, they define the "language" you can use to express your models.
  * The structures and rules enforced by the meta model might limit the degrees of freedom of the user but in return can help to "get the model right".  


##   
Model Transformations

Transformers® make good christmas presents. They have the ability to transform from a car or a truck into a robot - and then back again. This is a very cool trick!

System models can also be transformed from one model to another model. Depending on the underlying meta models, this transformation might or might not work equally well in both directions.

LEGO® models again can serve as an example. If one model consists of big, black bricks it can easily be transformed into a model consisting of smaller, colorful bricks without losing any previously modeled information like the physical shape of the modeled object.

The transformation in the opposite direction might not work equally well as the larger bricks are limited in their ability to form smaller shapes and black bricks can't represent different colors.

Of course at itemis we typically don't play with LEGO®. We deal with models like UML, SysML, EMF, Franca or Autosar. Very often it is useful to transform models. Every software language consists of specific notations, syntax and grammar (= meta model). The programs written in a software language are models. Because of this, model transformation can help us to pull off a very useful trick: it can help us to generate software code from other models like EMF or Franca. This is usually referred to as "Code Generation".

Yes, and sometimes we actually do play with LEGO®.

![Lego-model-itemis-logo.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/Software%20Development/Lego-model-itemis-logo.jpg?t=1514992779618&width=2172&height=1158&name=Lego-model-itemis-logo.jpg)

> _(itemis LEGO® model and instruction manual courtesy of Mathis Birken)_

[Part 2 of the introduction deals with additional concepts related to modeling](https://blogs.itemis.com/en/an-introduction-to-modeling-and-language-engineering-christmas-edition-part-2). Sticking to our familiar LEGO® models we will look at languages, domain specific languages (DSLs) and what the language engineers at itemis do.
