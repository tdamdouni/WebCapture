# OO Design Principles

_Captured: 2017-03-22 at 22:00 from [blogs.agilefaqs.com](http://blogs.agilefaqs.com/2012/06/07/oo-design-principles/)_

Following Object Oriented Design Principles have really helped me designing my code:

  * **[S**ingle Responsibility Principle](http://blogs.agilefaqs.com/2009/10/19/single-responsibility-principle-demystified/)
  * **[O**pen Closed Principle](http://c2.com/cgi/wiki?OpenClosedPrinciple)
  * **[L**iskov Substitution Principle](http://c2.com/cgi/wiki?LiskovSubstitutionPrinciple) or Design by Contract
  * **[I**nterface Segregation Principle](http://c2.com/cgi/wiki?InterfaceSegregationPrinciple)
  * **[D**ependency InversionPrinciple](http://c2.com/cgi/wiki?DependencyInversionPrinciple)
  * **[DRY** - Don't Repeat yourself](http://c2.com/cgi/wiki?DontRepeatYourself)
  * Triangulate - When you are not sure what the correct abstraction should be, instead of pulling out an abstraction upfront, you get the second case to work by duplicating and modifying a small piece of code. Once you have both the solutions working, find the "generic" form and create an abstraction

Along with these principles, I've also learned a lot from the 17 rules explained in the [Art of Unix Programming](http://catb.org/~esr/writings/taoup/html/) book:

  * Rule of **Modularity**: Write simple parts connected by clean interfaces
  * Rule of **Clarity**: Clarity is better than cleverness.
  * Rule of **Composition**: Design programs to be connected to other programs.
  * Rule of **Separation**: Separate policy from mechanism; separate interfaces from engines
  * Rule of **Simplicity**: Design for simplicity; add complexity only where you must
  * Rule of **Parsimony**: Write a big program only when it is clear by demonstration that nothing else will do
  * Rule of **Transparency**: Design for visibility to make inspection and debugging easier
  * Rule of **Robustness**: Robustness is the child of transparency and simplicity
  * Rule of **Representation**: Fold knowledge into data so program logic can be stupid and robust
  * Rule of **Least Surprise**: In interface design, always do the least surprising thing
  * Rule of **Silence**: When a program has nothing surprising to say, it should say nothing
  * Rule of **Repair**: When you must fail, fail noisily and as soon as possible
  * Rule of **Economy**: Programmer time is expensive; conserve it in preference to machine time
  * Rule of **Generation**: Avoid hand-hacking; write programs to write programs when you can
  * Rule of **Optimization**: Prototype before polishing. Get it working before you optimize it
  * Rule of **Diversity**: Distrust all claims for "one true way"
  * Rule of **Extensibility**: Design for the future, because it will be here sooner than you think
  1. [What is Simple Design? ](http://blogs.agilefaqs.com/2009/02/02/what-is-simple-design/) Simple is a very subjective word. But is Simple Design as well equally subjective? Following is what dictionary.com has to...
  2. [Mother of all Software Design Principles ](http://blogs.agilefaqs.com/2008/09/24/mother-of-all-software-design-principles/) Design is the art of making constant trade-off decisions; Good Design has balanced Trade-offs! The problem with design, as with...
  3. [Why are Design Patterns Important? ](http://blogs.agilefaqs.com/2008/09/05/why-are-design-patterns-important/) Short: They help us solve recurring design problems. Note that : design patterns don't solve the problem themselves, they help...
  4. [Micro-Design v/s Macro-Design v/s BUFD ](http://blogs.agilefaqs.com/2008/09/22/micro-design-vs-macro-design-vs-bufd/) My 2 cents to help with all the confusion out there with the word Design. (when I say Design, I...
  5. [Source Code is the Design ](http://blogs.agilefaqs.com/2009/02/01/source-code-is-the-design/) Following a DesignFest @ Directi, there has been a lot of discussion on "what is Design?", "should one design before...
  6. [Single Responsibility Principle Demystified ](http://blogs.agilefaqs.com/2009/10/19/single-responsibility-principle-demystified/) Lately, I've sensed some confusion in developers around the Single Responsibility Principle (SRP). Its easy to say every object or...
  7. [I'm not Attacking the Agile Manifesto Principles, I'm begging for Improvement ](http://blogs.agilefaqs.com/2010/03/19/im-not-attacking-the-agile-manifesto-principles-i-begging-for-improvement/) In 2001, following were a great set of principles for a Software Development team. Our highest priority is to satisfy...
  8. [When does Design begin? ](http://blogs.agilefaqs.com/2008/09/21/when-does-design-begin/) I used to think that Design really beginnings once you have the requirement (user story) in place. Over the years,...
  9. [What heuristics do you use to decide Long Method Smell? ](http://blogs.agilefaqs.com/2011/03/25/what-heuristics-do-you-use-to-decide-long-method-smell/) I find myself using the following heuristics: Can I quickly comprehend what is going on? Do I need to parse the method's...
  10. [Unit Tests Validates Micro-Design ](http://blogs.agilefaqs.com/2008/09/22/unit-tests-validates-micro-design/) I'm about to make a rather controversial statement now: "Developers who use purely inside-out avatar of TDD, .i.e. use unit...

This entry was posted on Thursday, June 7th, 2012 at 9:09 PM and is filed under [Agile](http://blogs.agilefaqs.com/category/agile/), [Code Smells](http://blogs.agilefaqs.com/category/code-smells-2/), [Design](http://blogs.agilefaqs.com/category/design/), [Programming](http://blogs.agilefaqs.com/category/programming/). You can follow any responses to this entry through the [RSS 2.0](http://blogs.agilefaqs.com/2012/06/07/oo-design-principles/feed/) feed. You can skip to the end and leave a response. Pinging is currently not allowed.
