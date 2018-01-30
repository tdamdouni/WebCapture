# Design Patterns — Coming Full Circle

_Captured: 2016-03-23 at 15:12 from [medium.com](https://medium.com/swlh/design-patterns-coming-full-circle-d8292e261dc6)_

![](https://cdn-images-1.medium.com/max/800/1*Rzk5Ag9PWeUdwxOOmVIhOw.png)

#### Architecture Inspires Software: Design Patterns

Christopher Alexander, an Austrian-born architect, had a simple, elegant idea. His idea was that people should name and describe solutions to common problems in architecture. He called this a 'design pattern'.

Christopher Alexander described 253 of these design patterns in his seminal book _A Pattern Language_, published in 1977, that covers everything from macro to micro design. On the macro end he describes patterns in regional and town planning such as "Pattern 3: City Country Fingers" and "Pattern 52: Network of Paths and Cars". In the middle of the spectrum he describes the relationship between buildings, for example "Pattern 101: Building Thoroughfare" and "Pattern 106: Positive Outdoor Space". On the micro end he describes individual spaces and how to make them livable and delightful, using patterns such as "Pattern 159: Light on Two Sides of Every Room" and "Pattern 201: Waist High Shelf".

> _Pattern 159: Light on Two Sides of Every Room  
_Locate each room so that it has outdoor space outside it on at least two sides, and then place windows in these outdoor walls so that natural light falls into every room from more than one direction.

All 253 patterns when used together, in Christopher Alexander's words, "create a coherent picture of an entire region, with the power to generate such regions in a million forms, with infinite variety in all the details". Moreover, a practitioner needn't focus on all 253 patterns at once -- a smaller sequence of patterns can be used as a pattern language to focus on a smaller part of the environment, say a single building or even a single room within a building. In short, the design patterns, whether taken together or individually, articulate guidelines that can be reused for a customized design.

Fast forward a decade from the initial publication of _A Pattern Language_ to 1987, when two computer scientists, [Kent Beck](https://en.wikipedia.org/wiki/Kent_Beck) and [Ward Cunningham](https://en.wikipedia.org/wiki/Ward_Cunningham), inspired by the work of Christopher Alexander, began experimenting with applying the idea of design patterns to programming. They presented their work at the [OOPSLA](https://en.wikipedia.org/wiki/OOPSLA) conference (Object-Oriented Programming, Systems, Languages & Applications), subsequently sparking a new school of thought in the software engineering community.

Over the next few years these ideas gained traction, and in 1994 the Gang of Four ([Erich Gamma](https://en.wikipedia.org/wiki/Erich_Gamma), Richard Helm, [Ralph Johnson](https://en.wikipedia.org/wiki/Ralph_Johnson_%28computer_scientist%29), and [John Vlissides](https://en.wikipedia.org/wiki/John_Vlissides)), a group of software engineering researchers, published an influential book -- _[Design Patterns: Elements of Reusable Object-Oriented Software_](https://en.wikipedia.org/wiki/Design_Patterns) -- which still lives on the bookshelves of many a software engineer (which is saying a lot for a book that is more than two decades old!).

![](https://cdn-images-1.medium.com/max/800/1*eaKM2sr72Gp4sd9VBNL59A.gif)

> _Gang of Four at OOPSLA conference, 1994_

To this day, the book is widely regarded as an important source for object-oriented design theory and practice. Object Oriented Programming (OOP for short) is a programming model organized around objects. It focuses on the operations those objects can perform, and the data on which those objects operate.

The key idea of a software design pattern, like an architectural design pattern, is that it is a general reusable solution to a commonly recurring problem. It's not a finished design that can be directly translated into code, but rather it's a description of how to solve a problem that can be used in many different situations.

A few examples of common software design patterns are:

  * _Observer pattern_: **A** tells **B** to notify **A** whenever **B** changes. An example of the Observer Pattern applied to daily life is when you sign up for text alerts for your upcoming flight. If the flight is delayed or if there's a gate change you receive notification of that change.
![](https://cdn-images-1.medium.com/max/800/1*bsphq9eu79OjEmSBTwVd8g.png)

> _Flight alerts keep you informed, like the Observer Pattern_

  * _Proxy pattern_: **A** is a lightweight stand-in for a big, heavy, inflexible object **B**. An analogy of the Proxy Pattern in real life is being able to drop a letter into a USPS mailbox on the corner rather than having to make the trek to the nearest post office to drop off your letter. The mailbox is a proxy for the post office.
![](https://cdn-images-1.medium.com/max/800/1*cp6WfMIuTkVXCGzTH3o6Ew.jpeg)

> _A USPS box is a proxy for the Post Office_

  * _Command pattern_: treat a series of actions as a single command, which can easily be undone or redone. Real-world examples of this are undo/redo in programs like Google Docs, or the history palette in Photoshop.

Software design patterns are generally language agnostic, meaning they can work equally well whether written in C++, Go, Javascript, Python, Java, Ruby, PHP, Dart, or some other language. They simply outline an approach to solving a problem that many others before you have experienced. The same way they say there are only [7 basic plots to Hollywood movies](https://en.wikipedia.org/wiki/The_Seven_Basic_Plots), there are a finite number of challenges we typically face in software engineering. In the movies, the characters may be different, but the stories they tell are familiar. Similarly in software engineering, the specifics may be different, but there's a limited number of truly unique problems.

In the software industry, it took many years and legions of people before today's software design patterns were codified. It was a process of experimentation, refinement, and critique that has helped shape how software designs are conceived and implemented. What's important, though, is that these patterns _were_ codified, so that the entire industry could benefit.

The same cannot be said for architecture. While Christopher Alexander put forth an initial collection of design patterns, the experimentation, critique, refinement, and eventual adoption that software design patterns have gone through simply hasn't happened in architecture. The vast majority of building design projects today are bespoke, with people solving the same problems over and over again. At Flux we ask, **what might the world look like if the AEC industry were to embrace the notion of design patterns in the same way as the software industry?** Could we harness the collective wisdom and knowledge of the AEC community to benefit the entire industry?

What might that world look like?

_-- Jen Carlile, Co-founder, Software Engineer, Flux.io_
