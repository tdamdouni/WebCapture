# Why We Comment Code

_Captured: 2017-06-23 at 13:12 from [dzone.com](https://dzone.com/articles/why-we-comment-code-yet-another-code-commenting-ar?edition=305129&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-22)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

First question: Do we really need another article on code commenting?

I think so; it's a topic like Exception Handling that benefits from more opinions being expressed.

I have recently participated in several discussions regarding code commenting in Java and Agile projects and based on those discussions I want to document and share some thoughts on commenting code in general and for Agile teams.

On the most basic level, why do we comment code?

One of the most important aspects of code is that it is usually not static; code is updated, enhanced, repurposed, modernized, and serviced because of bugs and the many other activities that touch the code. The code we write will be read and modified by people, including your future self, and may need to be debugged and modified in the future.

Regardless of who will work on the code, or when, useful commenting makes that work faster and reduces the opportunity for defects.

While **what** the code does should be "self-evident" from the syntax and reading of the code, the syntax does not communicate what you **intended** the code to do; it is possible (however unlikely) that you implemented the requirement incorrectly or made a logic error.

Also, it's good to consider the fact that there are many ways to implement business logic in order to fulfill a requirement. I'm sure the developer always has an insightful and well-reasoned thought process behind why a bit of logic was implemented a certain way; but the need to document in comments _why_ a specific implementation was selected still exists.

Comments will answer questions about implementation choices and design decisions without future maintainers guessing (and second-guessing) the developers' reasons and allow the modifier to determine if the implementation is still the best implementation as the application evolves and business requirements are refined or changed over time.

Of course, not all code needs the same level of commenting; DTOs do not require much commenting, but more complex implementations can and should have more comments than code. Common sense must prevail; there is no benefit to commenting much beyond the JavaDocs on getters and setters unless you're doing more than just assigning values to and returning values from properties.

There are many other things that do not need commenting, such as who makes changes or the date changes are made; that is in source control. The code self-documents what is being done, comments tell how and why it's being done - don't duplicate your effort.

Some objections I hear quite frequently are things like:

**"Commenting is not necessary if your code is written well"**: Commenting is necessary because you need to tell people what you **intended** to do and **why** you chose to do it a specific way. This is especially important in Agile groups and other organizations where uncertainties are often discussed with the Stakeholders or other team members directly. People that were not part of the conversation need to know the decisions made in those conversations.

**"Comments slow you down":** Any reduction in the pure speed of laying down lines of code is negligible; I've timed it. I spend at most 10 to 20 minutes commenting a class that took 3 to 6 hours to write. Also, just like in architecting a system, the implementation that completes a process in the shortest elapsed time for a single user may perform very badly under load.

I also find that while I am writing, comments help me to complete my work for a User Story faster because readability and comprehension of the code are increased with commenting.

**"Comments increase LOCs and increase maintenance costs":** Comments are not counted as LOCs and absolutely do NOT add to maintainability costs; they do just the opposite because they help developers understand the code now and in the future. Does anyone seriously suggest that Continuous Integration is wasteful because it slows you down? Commenting is just as important as CI.

**"Commenting is documentation and not an Agile practice": **Two problems with this; for any application with multiple releases and production support, documentation is vital and "Being Agile" is not an excuse to not document. The right level of documentation in Agile is the right info for all the stakeholders to do their work, but not more than is needed for that purpose.

The Agile Manifesto does not say "don't do documentation" it promotes "Working software over _comprehensive_ documentation" and "That is, while there is value in the items on the right, we value the items on the left more." The term "comprehensive" documentation in this context really means "more documentation than is needed."

I have an example of a class that illustrates the point I'm trying to make. I was taking a Statistics class for my MBA and the class was discussing the "[Monty Hall Problem.](https://en.wikipedia.org/wiki/Monty_Hall_problem)" I wrote a quick Test Harness that would allow me to run a simulation of the problem and vary the number of trials and even the number of doors.

I've included on GitHub the Test Harness class both with and without commenting. To be honest, I did over comment the code in this example; I didn't originally put this in source control and didn't externally document the requirements. That being said, I still didn't spend more than 30 minutes commenting the code. Between Code Reviews and future maintenance, more time the 30 minutes it took me to comment the code will be saved.

The example Monty Hall Problem code is available on [GitHub](https://github.com/mgeiser/MontyHallProblem).

Evaluate the MontyHallProblem_NoComments.java version of the class first and then evaluate the MontyHallProblem.java code.

Assume you have a Defect reported that the output of this code is faulty. Which version of the code will be easiest to debug and find the error in? Or, if the code isn't broken, which one will be easier to confirm that the code indeed works as designed and the reported Defect is "Works as Designed - No Defect"?

I have also tested the effect of commenting on productivity in real life. I had a new component that extended the Password Policy of an Identity and Access Management system to enhance the Password History retention. Two configuration options added were "The number of interim passwords before a password could be reused" and "The minimum number of elapsed days before a password could be reused."

Assume the "Number Password History Retained" value is 5 and "Minimum Days Between Reuse" is 90 days. The intent was that a password could not be reused for at least 90 days AND until 5 other passwords have been used in the interim. The initial code had a defect that created a logical OR rather than an AND in the implemented code; so, if you changed your password 6 times in a row, you could reuse the same password that just expired.

I gave the same code, one with comments and one without comments, to two very good and equally skilled mid-level developers. The developer with the commented code completed his work more than an hour sooner than the developer with uncommented code.

My guidelines for commenting:

  * Comment what you intended to implement (the code self-documents what you did implement).

  * Include explanations of how tricky and clever bits of code work.

  * Reference the User Stories/documents for the requirements you're implementing.

  * Capture implementation and other design or scope decisions (for example: why you chose a specific implementation such as a HashMap over a TreeMap or a LinkedHashMap).

  * Err on the side of too much commenting, especially when writing new code. As you review your code before check-in, commenting that needs to be tightened up will be obvious.

  * Don't let comments get stale; if you update code, update comments.

  * Commenting has a great ROI. Make clear expectations on commenting part of your standards and your Definition of Done.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Opinions expressed by DZone contributors are their own.
