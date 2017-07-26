# Design for Testability

_Captured: 2017-03-10 at 03:50 from [blog.gdinwiddie.com](http://blog.gdinwiddie.com/2012/05/16/design-for-testability/?utm_content=bufferd7e23&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Asked on the [Agile-Testing](http://groups.yahoo.com/group/agile-testing/) mailing list:

> Lesson 136: Testability is often a better investment than automation.
> 
> (I'm quoting "Lessons Learned in Software Testing" by Kaner/Bach/Pettichord)
> 
> If anyone has practical examples of improving testability, I'd be very interested to understand, and grateful.

I first encountered the issues of testability when working with integrated circuit design in the 1980s. The same issues apply to software systems.

  1. You want to be able to easily put the system into a known state. It's best if you can get to the state you want for your test without going through a number of interactions or other states on the way.
  2. You want to be able to drive internal nodes of the system so that you can test parts in isolation. It's much harder to test everything through the GUI, public API, IC pins, or whatever is the normal interface.
  3. You want to be able to sense internal nodes of the system so that you can test parts in isolation. Like being able to drive internal nodes, this reduces the combinatorial complexity.
  4. The special access you add for testability does add some complexity, can provide new failure modes, and might leave some paths untested. Be aware of this and consider what these issues are for your system.

Your work gets a bit easier if you consider this as part of building the system, rather than just as part of testing it. If you build your tests first, the tests will specify the state and access you need for testability. Running these tests while the system is built will result in testability appearing almost magically. Because of that, I'd say that testability trumps automation only when you're already late in starting.
