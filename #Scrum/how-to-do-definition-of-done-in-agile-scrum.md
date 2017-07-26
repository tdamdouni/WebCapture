# How to do Definition of Done in agile / scrum 

_Captured: 2016-12-31 at 09:56 from [www.extremeuncertainty.com](http://www.extremeuncertainty.com/how-definition-of-done-agile-scrum/)_

The "Definition of Done" is one of the most important concepts in Scrum, yet a lot of people don't understand it properly. When understood and used properly, the Definition of Done is a powerful guide for consistent delivery of quality. When not understood or used properly, you will likely end up in an inconsistent mess of poor quality. Especially with multiple teams work on one project. So make sure to get it right!

![definition of done in agile scrum](http://www.extremeuncertainty.com/wp-content/uploads/2016/04/done-150x150.jpg)

> _looks like we need a three way handshake!_

## What Definition of Done is

The basic idea of a "Definition of Done" is that a team has a set of criteria for what a story needs to meet, in order to be considered complete. So for every user story that enters your [Kanban](http://www.extremeuncertainty.com/glossary/) flow, you have clear rules for what needs to be done in order to get it through to the other side of the board.

Definitions of Done will of course vary from project to project and organisation to organisation, but they might typically look something like this:

  * All acceptance criteria have been verified
  * [UX](http://www.extremeuncertainty.com/glossary/) and visual designs completed
  * Functional and non-functional tests completed and recorded
  * Security and risk analysis completed
  * All risks have been accepted or mitigated.

There would probably be a few more, this is just to give you an idea.

### How to use definition of done in agile

In scrum, the job of the dev team is to perform all of the required activities to get the user stories in the sprint across to the other side of the board. That is, to make sure all of the Definition of Done criteria have been met for all of the user stories. It acts as a useful "checklist", since if the dev team are doing their job properly and checking these for every story, no user stories should be slipping through without meeting all of these criteria.

It is considered a good practice to print out the Definition/s of Done on a big piece of paper. And then stick them next to your team's VMB. This can act as a handy reminder if you are ever unsure or have forgotten them. It can also be a talking point / reference point in your daily standup. E.g. "So this morning I just moved this user story into Done." "Really?" (looks at the definition of done) "Have we completed non-functional tests for that? I didn't think the results were back yet?" "Oh crap you're right, I better not move it yet".

### Definition of Done does not just have to be for user stories

Many people think that the Definition of Done should not just apply to user stories. For example, you could have a Definition of Done for features and epics. So in your Definition of Done for features, you could have something like

  * all high priority user stories have completed Integration Testing
  * the UX and visual designs for all end to end flows completed
  * all major error scenarios and unhappy paths for this feature have been considered and handled
  * all high priority defects for all stories have been fixed.

Again, just an example. You might think of something similar for an epic or initiative. This can help you ensure the overall consistency and quality for a feature before it goes out to production, and help make sure you don't release features that have some solid components but some buggy parts also.

### Definition of Done is not just for one kanban state

If you want to get a bit more advanced with Definition of Done, you can try implementing multiple Definitions of Done: one for each [Kanban](http://www.extremeuncertainty.com/glossary/) state in your process. So you would have a Definition of Done for moving a user story from Backlog to Ready for Development (that might be "story normal form is written, acceptance criteria defined, UX completed"). And a Definition of Done for moving a user story from In Development to Ready for Test (that might be "story is completed with unit tests, which are all passing in Dev environment"). And so on.

Your "master" definition of done, to move a story to "Ready for Production" (or similar) is then an aggregate of all the other Definitions of Done for all of the other Kanban states. Plus potentially some specific ones you need to release that you haven't done in previous Kanban states (these could be Product Owner agrees to release, User Acceptance Testing passes, Tech Manager review, or anything specific to your organisation). This is a bit more advanced and I would not do this right away for an organisation starting out new in Scrum / Kanban.

You could take this even further and have multiple sets of Definitions of Done for multiple states. One set for user stories to move through each Kanban state, another set for features to move through each of the Feature Kanban states (if you have defined Kanban states for features to move through). Maybe another set for each of the states that epics can move through, and so on. This is quite advanced.

## ![definition of done agile scrum](http://www.extremeuncertainty.com/wp-content/uploads/2016/04/done2-150x150.jpg)

What Definition of Done is not

There is some confusion and misuse of Definition of Done out there. I'll try and clear things up.

### Definition of Done is not the same as Acceptance Criteria

Some people get mixed up between Definition of Done and Acceptance Criteria. They are not the same. Acceptance Criteria are specific criteria for a specific Backlog Item for that to be built. The are mainly used by testers and developers to define tests for the story and guidelines for how to build it. Definitions of Done are rules for all (well, most) of the Product Backlog Items that a team or project or organisation builds. Definitions of Done often encompass and include Acceptance Criteria. That is, the Definition of Done for a user story could (and should) include something like "all acceptance criteria have been verified".

### Definition of Done is not an excuse to shoehorn people into processes and policies that don't fit them

Having standard Definition of Done for multiple teams working on multiple things is good, because you have a standard yardstick for all your work. This can reduce surprises and improve consistency and quality. However, always remember to apply common sense. Sometimes they just don't apply to certain tasks or stories or even teams. It depends on what the particular work is and the particular context it is happening in. For example, performance and capacity testing might not apply to an internal tool that is only used by 10 people. Start with the overall guidelines, then apply exceptions and modifications where it makes sense to do so.

Anyway I hope this has cleared things up around this topic!

Question: do you still find Definition of Done confusing? Or have you applied it in a different way than this? Let me know in the comments!
