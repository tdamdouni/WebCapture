# Grokking software patterns

_Captured: 2015-12-11 at 10:00 from [web.archive.org](http://web.archive.org/web/20090212123131/http://immike.net/blog/2007/05/15/grokking-software-patterns/)_

If you've been programming for any period of time then you've probably heard about these things called patterns. But unless you're a professional you're probably not quite sure what they are, or what they're good for. I've decided to start cataloging some of the software patterns I use most frequently in my projects. But before I do that, I figured I should try explaining what a software pattern is.

#### A Quick History

It all started when, in 1987, two fellows named [Kent Beck](http://web.archive.org/web/20090212123131/http://en.wikipedia.org/wiki/Kent_Beck) and [Ward Cunningham](http://web.archive.org/web/20090212123131/http://en.wikipedia.org/wiki/Ward_Cunningham) had some trouble finishing a design for a consulting gig. The pair had been reading a book called [A Pattern Language](http://web.archive.org/web/20090212123131/http://en.wikipedia.org/wiki/A_Pattern_Language) that was written by a relatively obscure architect named [Christopher Alexander](http://web.archive.org/web/20090212123131/http://en.wikipedia.org/wiki/Christopher_Alexander).

Alexander had gone through a bunch of traditional architecture and found common elements (e.g. Roof Garden, Main Entrance, Bathing Room, Open Stairs, etc). The idea was that by cataloging these "patterns" he could make it easier for architects to communicate. It's no surprise then that programmers, who generally feel that every problem can be solved by simply adding another layer of abstraction, jumped at the chance to use abstractions to communicate. Ward and Kent came up with a small set of common UI patterns, then let the users design the interface themselves using their new pattern language - and apparently it worked.

Skipping ahead a few years to 1995, a [Gang of Four](http://web.archive.org/web/20090212123131/http://c2.com/cgi-bin/wiki?GangOfFour) (GoF) fellows named Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides who were inspired by Kent and Ward's success published a book called _[Design Patterns](http://web.archive.org/web/20090212123131/http://www.amazon.com/Design-Patterns-Object-Oriented-Addison-Wesley-Professional/dp/0201633612)_. This is probably the most influential object-oriented software development book ever published (which puts it at about #57,283,287 overall). And [the rest](http://web.archive.org/web/20090212123131/http://c2.com/cgi-bin/wiki?HistoryOfPatterns), as they say, is history.

#### So, wtf is a pattern then?

It's simple really… so simple that it's hard to explain. A pattern is an idea that has been useful in at least one practical context, and will likely be useful in others. A pattern won't solve a problem, but simple describes how to approach the problem in a way that makes solving it easy. Patterns are rooted in practice, not theory. They're not produced by academics in ivory towers, they're recognized in existing solutions and cataloged. [Martin Fowler](http://web.archive.org/web/20090212123131/http://www.martinfowler.com/), a famous "pattern hatcher," explains that he _discovers_ patterns, he does not _invent_ them.

Patterns come in many forms, reflecting varying degrees of abstraction and specialization. Design patterns are probably the most commonly discussed software patterns. This type of pattern solves a recurring problem in software engineering, and typically shows relationships or interactions between classes or objects in a system. There are also analysis patterns, which reflect conceptual structures of business processes (like how to represent a [quantity](http://web.archive.org/web/20090212123131/http://www.martinfowler.com/ap2/quantity.html) or [range](http://web.archive.org/web/20090212123131/http://www.martinfowler.com/ap2/range.html)) rather than actual software implementations. Model patterns describe different approaches to data modeling, and architectural patterns express a fundamental structural organization schema for a software system (like the [Model View Controller [MVC] pattern](http://web.archive.org/web/20090212123131/http://en.wikipedia.org/wiki/Model-view-controller)).

If you're still having some trouble understanding what a pattern is, this example from _Design Patterns_ might clear things up:

> Novelists and playwrights rarely design their plots from scratch. Instead, they follow patterns like "Tragically Flawed Hero" (Macbeth, Hamlet, etc.) or "The Romantic Novel" (countless romance novels). In the same way, object-oriented designers follow patterns like "represent state with objects" and "decorate objects so you can easily add/remove features." Once you know the pattern, a lot of design decisions follow automatically. 

#### What makes a pattern

There are four essential elements of a pattern:

  1. The **_pattern name_** is a brief phrase that represents a complex problem, a solution, and any relevant consequences. This is the abstraction part I talked about earlier. Once you've given a pattern a name, you don't need to describe it any more. A paragraph of text is potentially replaced with a single phrase (e.g. let's make the database class a _singleton_).
  2. The **_problem_** is the grounds or motivation for the pattern. It describes when a particular pattern should be applied. Oftentimes the hardest part of using patterns is recognizing a problem and realizing that a pattern exists to solve it.
  3. The **_solution_** is an abstract description of how the problem is solved. It's **not** a concrete implementation. The solution is not code - it's not even pseudocode. Rather, it explains how to approach the problem in a way that makes solving it obvious.
  4. The **_consequences_** are the trade-offs that you make by selecting one solution over another. For design patterns the consequences are the typical space and time trade-offs seen in computer science. Consequences also include the impact on a system or component's flexibility, ease of reuse, extensibility, and portability. Many patterns have alternatives, so consequences can also help you identify which pattern to use.

#### Why use software patterns

So why should you care about patterns? Well, let me explain…

First, patterns document best practices. Instead of discovering the proper architecture for a piece of software the hard way, patterns tell you up front what the best solution is. Like I said, patterns come from practice. So by definition a pattern has been used to successfully solve a problem at least once.

Patterns are also typically composable, which means that they're easy to integrate with other patterns. In fact, most pattern descriptions will list other patterns that are particularly suited for interaction. Patterns not suited for interaction (if any exist) are typically documented as a consequence of using a particular pattern. So by using patterns you're improving your architecture, and applying best practice solutions in a manner that feeds on itself. And if a pattern reduces flexibility in some way, at least it's documented and well understood.

Finally, patterns are language independent solutions that will transfer, with minor modification, to a variety of situations. In five years, when Ruby on Rails has fallen out of favor and Java is just a distant memory you'll still be able to apply patterns. And next time you're trying to explain the architecture of your new web application to a colleague you can skip the lecture and simply tell them that "it's built around a [Front Controller](http://web.archive.org/web/20090212123131/http://www.martinfowler.com/eaaCatalog/frontController.html) and uses a [Template View](http://web.archive.org/web/20090212123131/http://www.martinfowler.com/eaaCatalog/templateView.html)."

If you've ever wondered what separates a good programmer from a great one, patterns are it. Good programmers can write pretty much anything once you've told them what you want and given them an example. Great programmers have learned through experience how to implement functionality without looking at someone else's code for inspiration, or using a recipe. They have a deep understanding of how various types of components interact, and what combination of relationships and behavior produce high quality systems. Patterns encapsulate this knowledge so that the rest of us can be great too.

If you're interested in learning more about patterns, make sure you [subscribe to my feed](http://web.archive.org/web/20090212123131/http://immike.net/blog/feed). I'll be posting descriptions and example implementations for patterns that I've found particularly useful in projects that I've worked on.
