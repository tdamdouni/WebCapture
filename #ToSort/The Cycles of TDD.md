# The Cycles of TDD

_Captured: 2015-10-17 at 21:59 from [blog.cleancoder.com](http://blog.cleancoder.com/uncle-bob/2014/12/17/TheCyclesOfTDD.html)_

When you first learn Test Driven Development, it sounds simple and easy. If you learned it in 1999, like I did, the rule was to simply write your unit tests first. Indeed, we called it Test First Design back then.

I sat with Kent Beck in 1999 and paired with him in order to learn. What he taught me to do was certainly test first; but it involved a more fine-grained process than I'd ever seen before. He would write _one line_ of a failing test, and then write the corresponding _line_ of production code to make it pass. Sometimes it was slightly more than one line; but the scale he used was was very close to line by line.

### **Second-by-Second** _nano-cycle_: The Three Laws of TDD.

A few years later this fine granularity was codified into three rules: the so-called [Three Laws of TDD](http://programmer.97things.oreilly.com/wiki/index.php/The_Three_Laws_of_Test-Driven_Development).

  1. You must write a failing test before you write any production code.
  2. You must not write more of a test than is sufficient to fail, or fail to compile.
  3. You must not write more production code than is sufficient to make the currently failing test pass.

I, [and many others](http://bit.ly/1AEPxKX), have written about these three laws over the years. They now appear in many different styles, formats, and injunctive statements. But the goal is always to promote the _line by line_ granularity that I experienced while working with Kent so long ago.

_The three laws_ are the _nano-cycle_ of TDD. You follow them on almost a second-by-second basis. You will likely iterate them a dozen or so times before you finish a single unit test.

### **Minute-by-Minute**: _micro-cycle_: Red-Green-Refactor

If we pull back to the minute by minute scale we see the _micro-cycle_ that experienced TDDers follow. The _[Red/Green/Refactor](http://www.jamesshore.com/Blog/Red-Green-Refactor.html) cycle_.

![](http://marcabraham.files.wordpress.com/2012/04/06_red_green_refactor.jpg)

This cycle is typically executed once for every complete unit test, or once every dozen or so cycles of the three laws. The rules of this cycle are simple.

  1. Create a unit tests that fails
  2. Write production code that makes that test pass.
  3. Clean up the mess you just made.

The philosophy is based on the idea that our limited minds are not capable of pursuing the two simultaneous goals of all software systems: 1. Correct behavior. 2. Correct structure. So the RGR cycle tells us to first focus on making the software work correctly; and then, _and only then_, to focus on giving that working software a long-term survivable structure.

Again, [many](http://bit.ly/1AESA5D) people have written about this cycle. Indeed the idea derives from [Kent Beck's original injunction](http://c2.com/cgi/wiki?MakeItWorkMakeItRightMakeItFast):

> _Make it work. Make it right. Make it fast._

Another way to think about this idea is:

> _Getting software to work is only half of the job_.

Customers value [two things](http://seasidetesting.com/2013/03/12/testing-and-the-two-values-of-software/) about software. The way it makes a machine behave; and the ease with which it can be changed. Compromise either of those two values and the software will diminish in real value to the customer.

Executing the _Red/Green/Refactor_ cycle takes on the order of a minute or so. This is the granularity of refactoring. Refactoring is not something you do at the end of the project; it's something you do on a _minute-by-minute_ basis. There is no task on the project plan that says: Refactor. There is no time reserved at the end of the project, or the iteration, or the day, for refactoring. Refactoring is a continuous in-process activity, not something that is done late (and therefore optionally).

### **Decaminute-by-Decaminute**: _milli-cycle_: Specific/Generic

At the 10 minute level we see the _milli-cycle_ in operation. [The Specific/Generic cycle](http://thecleancoder.blogspot.com/2010/11/craftsman-63-specifics-and-generics.html).

> _As the tests get more specific, the code gets more generic._

As a test suite grows, it becomes ever more specific. i.e. it becomes an ever more detailed _specification_ of behavior. Good software developers meet this increase in specification by increasing the _generality_ of their code. To say this differently: _Programmers make specific cases work by writing code that makes the general case work._

As a rule, the production code is getting more and more general if you can think of tests that you have not written; but that the production code will pass anyway. If the changes you make to the production code, pursuant to a test, make that test pass, but would not make other unwritten tests pass, then you are likely making the production code too specific.

It is often said that the fine grained structure of the three laws and the Red/Green/Refactor cycle [lead to local-optimizations](http://c2.com/cgi/wiki?RefactoringEqualsReparametrization). Without the "big picture" the developer cannot imbue the software with the correct structure for the overall problem, and instead drives towards a structure that is good for the local case; but not for the general case.

The symptom of the local optimum is "[Getting Stuck](http://thecleancoder.blogspot.com/2010/10/craftsman-62-dark-path.html)." In order to make the next test pass you must write a large amount of code _outside_ of the nano-cycle of the three laws, and even outside of the micro-cycle of RGR. In other words, you have gone down a path that forces you out of the TDD process.

Once you are stuck, the only solution is to backtrack up through the previous tests, deleting them, until you reach a test from which you can take a different fork in the road.

Why do you get stuck? Because you were not adding sufficient generality to the production code. You were making the tests too specific, to quickly. The solution is to backtrack and then add specificity to the tests more slowly, while adding generality to the production code more quickly. This frequently forces you to choose a different set of tests to follow.

To avoid getting stuck we evaluate our position every few minutes; looking for specificity in the production code. Have we taken shortcuts that make the production code resemble the tests in some way? Do the most recent changes to the production code fail to pass more tests than we have written?

This is the cycle in which we apply the _[Transformation Priority Premise_](http://en.wikipedia.org/wiki/Transformation_Priority_Premise). We look for the symptoms of over-specificity by checking the kinds of production code we have written.

### **Hour-by-Hour**: _Primary Cycle_: Boundaries.

The final primary cycle of TDD is the cycle that ensures that all the other cycles are driving us towards a [Clean Architecture](http://blog.8thlight.com/uncle-bob/2012/08/13/the-clean-architecture.html). Ever hour or so we stop and check to see whether we have crossed, or are encroaching upon, a significant architectural boundary. Often these boundaries are difficult to see while in the throes of the nano- and micro-cycles. You can start to smell them at the decaminute level, but even then our gaze is still too narrowly focused.

So every hour or so we stop and look at the overall system. We hunt for boundaries that we want to control. We make decisions about where to draw those boundaries, and which side of those boundaries our current activities should be constrained to. And then we use those decisions to inform the nano-cycles, micro-cycles, and milli-cycles of the next hour or so -- the _primary_ cycle -- of Test Driven Development.
