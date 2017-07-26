# MVC Pattern Language (Part 2)

_Captured: 2017-04-18 at 19:46 from [dzone.com](https://dzone.com/articles/mvc-pattern-language-part-2-patterns-6-11?edition=293881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-18)_

[Download Microservices for Java Developers](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034): A hands-on introduction to frameworks and containers. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034).

Welcome to the second part of my write-up about the **MVC Pattern Language**! In case you missed the [first part](https://dzone.com/articles/mvc-pattern-language-part-1), this two-part piece targets popular misconceptions about MVC and tries to shed some "new" light on the topic by analyzing an oldish [Trygve Reenskaug's paper](https://heim.ifi.uio.no/~trygver/2003/javazone-jaoo/MVC_pattern.pdf). This part covers patterns 6.-11.

## 6\. Model/Editor Separation

As we said in the previous post, a user wants to interact directly with his _[mental model](http://tidyjava.com/mvc-pattern-language/#mental-models)_ and he does that using _[business objects](http://tidyjava.com/mvc-pattern-language/#business-objects)_. This calls for presentation logic inside the _business objects_ that would allow the user to interact directly with each of them. Those objects can grow very complex without that extra logic and, if you consider different GUIs for different users, mixing the two could make things unmaintainable.

Therefore, we can split the _business objects _into two parts: _model_ and e_ditor_. The _model _holds information and behavior, while the _editor_ handles presentation and user input.

We're still mainly concerned by aligning with the user's _mental model_ and those can vary from user to user. Therefore, it would be nice if this task was aided by a _[modeling language](http://tidyjava.com/mvc-pattern-language/#modeling-language)_ and/or _[(semi-)automatic tool generation](http://tidyjava.com/mvc-pattern-language/#personal-information-systems)_.

## 7\. Input/Output Separation

The _editor_ object mentioned in the previous pattern combines both presentation and input handling logic. In most non-trivial examples, combining the two responsibilities together is way too much complexity for little-to-none common code between the two.

Therefore, we can split the _editor_ into two objects - _view _which would be responsible only for presentation, and _controller_ which would be responsible only for handling user input.

As you probably noticed, I'm using words like "can" and "would" all around. This is because the separations I'm describing are not mandatory and sometimes even counter-productive. Sometimes, the roles of _model, view_, and _controller_ can all be played by a single object as well as they could be played by three different objects. You need to analyze each case carefully considering both code complexity and aligning with the user's _mental model_.

## 8\. Tools for Tasks

Merely presenting a single object using an _editor_ is not enough. To do his job properly, the user has to perform tasks which can span across multiple _editors_.

To support that, we distinguish a _tool _role, responsible for coordinating different _editors_ in a way that supports user's tasks.

Similarly to above, the _tool/editor _separation is also optional (needless) in simple cases. Of course, when talking about _editors_, we mean them either as a single object or as a _view-controller_ pair.

## 9\. Tool as a Composite

This pattern groups together several of the patterns mentioned before to answer a general problem: A user wants to interact with a with a complex model consisting of multiple interconnected objects.

To enable this, we structure the GUI into the following parts:

  * The _User _with his goals and tasks
  * The _Model _responsible for representing the user's _mental model_
  * The _Editors_ that display and, if necessary, allow editing relevant information
  * The _Tool_ that coordinates the editors

This is the original MVC pattern as presented in the late 70s. If you were to remember one thing from this longish two-part post, remember this pattern with the exact descriptions of each of the parts. In particular, remember that it was the _User_ mentioned as the first thing in MVC and that the model part should correspond to the **user's mental model**.

## 10\. Synchronize Selection

If a _user_ selects an object in one of the _views_, the others should reflect it as well to maintain an illusion of interacting directly with the object model.

To achieve that, we make the _tool_ object responsible for synchronizing the selection between all underlying _views_.

In case the _controller_ plays the role of the _tool_, it will be the one to do the synchronization. If we allow for multi-selection, the implementation of this mechanism can get significantly complex.

## 11\. Synchronize Model and View

The underlying _model_ can change, while being presented by a _view _object, either due to user's commands or some external party changing it. The _view_ has to reflect this change to the user.

Therefore, we make the _view _observe the underlying _model_ as in the GOF _observer pattern_.

It's important to make sure that the changes don't occur too often and don't negatively affect the user's experience e.g. via constant re-rendering of the whole GUI. Use of transactions can help us achieve the former. The second is rarely a problem when using modern GUI tools.

## Summary of Part 2 and Final Words

In this part, we went through the lower-level patterns that make our GUI code more manageable and the user experience more pleasant. If you were familiar with MVC before, you most likely knew the patterns presented here. What, I suppose, most have not known is that we're doing all these for the best possible user experience. We're constantly trying to bridge the gap between the user and his mental model. **It's not some nerdy, class-separation, cool framework tricks. It's all about the user.**

**Congratulations!** You're an MVC adept now and you now much more about creating habitable GUIs for your users. I hope that from now on, whenever you think MVC two words will come to your mind: **mental models**. If you're looking for some next steps, I strongly recommend reading the [MVC stuff on Trygve Reenskaug's page](http://heim.ifi.uio.no/~trygver/themes/mvc/mvc-index.html). And don't forget to share all this stuff with others! MVC is like a good TED talk - it contains an idea worth spreading!

[Download Modern Java EE Design Patterns](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035): Building Scalable Architecture for Sustainable Enterprise Development. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035).
