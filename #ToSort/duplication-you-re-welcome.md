# Duplication, You're Welcome

_Captured: 2018-05-15 at 16:42 from [dzone.com](https://dzone.com/articles/duplication-youre-welcome?edition=376300&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202018-05-15)_

There are models to describe the process of learning, such as the [Dreyfus model](http://wiki.c2.com/?DreyfusModel) or [Shuhari](http://wiki.c2.com/?ShuHaRi), but I'd like to explain another process when learning a new technical skill. It is composed of 2 phases:

  1. **Fascination**. This is when we learn a new concept that sounds really good to solve our problems, and we apply it in any place we have an opportunity. We are so convinced about its advantages that it seems we have a radar to detect a place in which we can apply it. It's like the first stage at Shuhari, but we are absolutely fascinated and we don't believe in _another world_.
  2. **Questioning**. This is when we have assimilated that concept and we are able to decide where it's convenient to implement it. We have learned from the previous stage and now we are moderate and reasonable about our decisions.

But sometimes it's really difficult to jump to the second stage because we are continuously receiving messages about a concept for years. It's the case of **no duplication**.

This week, I was reviewing a test class with 4 extracted parameterized methods (for 4 different types of expectations) and 6 extracted methods (for 6 different JSON files). I sat with the author of that class and we applied inline method refactoring. After that, we realized that the test class was more readable and understandable without those 10 additional methods, despite having duplicated source code.

A few weeks ago, I helped to separate two different modules. They were together, because they had some similar domain objects, although they didn't use the same properties. It was really difficult to know which properties and methods needed each module.

What's the reason of those extracted methods or that reuse?

`Alerts: duplicated lines (%) > 10%`

One of the metrics we can find in static code analysis tools is the **percentage of duplicated lines**. Managers need metrics and this one is usually included as a guarantee of **quality code**. However, striving for a certain number of duplicated lines in a board can cause these consequences:

  * Over-generalization
  * Over-anticipated abstractions
  * Early decisions about common parts
  * Coupling
  * Levels of indirection, adding difficulty to understand the source code

We tend to associate this metric with **D.R.Y. Principle (Don't Repeat Yourself)**, but let's read the principle carefully:

> Every piece of knowledge must have a single, unambiguous, authoritative representation within a system.

This principle is talking about **knowledge**, not duplicated lines. Two pieces of code could be apparently similar, but have completely different reasons to change, because they represent different pieces of knowledge. Therefore, removing that duplication can muddle the logic and make any future change worse.

That's the reason why I usually highlight **knowledge** when explaining the third rule of [simple design](http://wiki.c2.com/?XpSimplicityRules):

> No **knowledge** duplication.

To sum up, some recommendations:

  * Try to postpone your decisions about duplicated code, because it's a question of trade-offs
  * When you find two apparently similar pieces of source code, question whether you find a reason to have to change them at the same time
  * Use the metric about duplicated lines only as **guidance**, but don't try to strive for a number in a board, compromising the understanding of source code

## Further reading

  * _[99 Bottles of OOP. A practical guide to Object-Oriented Design](https://www.sandimetz.com/99bottles/)_, by Sandi Metz and Katrina Owen, where we can find this sentence: 

> DRY makes sense when it reduces the cost of change more than it increases the cost of understanding the code.
