# Taking Organizational Improvement Seriously – Case Study

_Captured: 2017-08-04 at 23:44 from [agilepainrelief.com](https://agilepainrelief.com/notesfromatooluser/2015/11/taking-organizational-improvement-seriously-case-study.html?utm_content=bufferfbc0d&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer#.WYTqq2qbGf0)_

![Organizational Improvement](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2015/09/scrum-alone-not-enough-organizational-improvement.jpg)

(_Presented as an accompanying case study to Part 4 in the [Scrum Alone is Not Enough series](http://agilepainrelief.com/notesfromatooluser/2015/01/scrum-alone-is-not-enough.html)._)

In the [previous post](http://agilepainrelief.com/notesfromatooluser/2015/09/taking-organizational-improvement-with-scrum-seriously.html), we discussed how it's not enough to practice Scrum at the Team level and expect that it will solve all problems. Senior Management has to get involved for real Agile change to happen and high performance to be achieved. An important aspect of that is Systemic Problem Solving, which we'll look at closer using the World's Smallest Online Bookstore as a case study for examples.

## Systemic Problem Solving

Most teams that I encounter are very good at solving specific problems locally (at the team level). What is missing is a bigger picture, holistic view. [Systems thinking](http://www.thinking.net/Systems_Thinking/OverviewSTarticle.pdf) (pdf) is a tool that helps you take a Systemic - or bigger picture - view of whole systems.

Let's look at a couple of common organization problems as examples - namely "Long Regression Cycles" and "Product Owner can't seem to stay focused on the big picture".

### Long Regression Cycles

_Hereafter: LongRegressionCycle_

The Org Team recognizes that it has a problem with the regression cycles as illustrated:

![Regression Runtime in Days](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2015/11/Regression-Runtime-in-Days.jpg)

When long regression cycles are an issue, without a systemic approach the organization might first try adding more people to do regression testing. As a second step, they might try automated testing through the browser/GUI using a special team who has access to an expensive tool. Unfortunately, as we see below, this will likely lead us down the wrong path:

![Long Regression Cycle](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2015/11/LongRegressionCycle.png)

This is a simple [causal loop diagram](https://en.wikipedia.org/wiki/Causal_loop_diagram) -it's intended to help us look past the initial problem and see deeper causes.

Variables create cause and effect within a system. In a causal loop diagram, you start with a single part of the system that you can already identify and just keep asking "what influences this part?" then draw links between the interconnected parts using arrows pointing in the direction of influence. Once you can no longer think of additional parts or influences to add, you have a closed loop.

In this example, we can envision what may happen by playing through the loop, starting at "Features added" and following its influence to the "Regression Cycle Length". Keep going, and we can see that the often-used simple fix of asking a special team to automate regression tests through the Browser/GUI influences many variables and eventually exacerbates the problem that it was intended to solve.

The diagram makes it clear that GUI based automation is fragile, and having all the work done by a special team is creating an island of knowledge. These two problems combine, increasing the time it takes to find bugs and eventually even increases the number of bugs themselves.

To solve the underlying initial problem, we would have to also find an approach that doesn't recreate these same issues! Instead of a special team doing all of the test automation, the work should be done by every team. Instead of doing all the automation through the browser, do most of it through public api's (or their equivalent) that exist at the boundaries of the system.

Before making any change, the team creates a new version of the causal loop diagram to see if their proposed solution is an improvement on the original.

### Product Owner Can't Stay Focused on the Big Picture

_Hereafter: UnfocusedProductOwner_

In a second example, the Team sees a Product Owner making frequent revisions to the Team's work in Sprint. We can talk to the PO about this, but we can't just expect the PO to change unless we also identify and fix the underlying problem.

![PO can't stay focused](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2015/11/PO-cant-stay-focused.jpg)

As this image illustrates, we can see that the real problem is that the PO is under daily pressure from stakeholders to solve real and perceived customer problems. The challenge is how to set aside enough time to deal with those issues, while still making progress in the bigger goal. A causal loop diagram like this should help the organization discover the need for [Portfolio Management](https://agilepainrelief.com/notesfromatooluser/2015/06/portfolio-management.html), which would give the Product Owner some boundaries on how much short term work they should accept from the Team.

In each case, the key point is that the Org Improvement Team must make sure that they're solving the systemic - and not just surface - problem.

So let's look at how the World's Smallest Online Bookstore teams might do that, using a Scrum-like framework to achieve it.

Our World's Smallest Online Bookstore Organizational Improvement Team is working in two-week Sprints to stay in sync with their Development Teams. As we learned in [this post](https://agilepainrelief.com/notesfromatooluser/2015/09/taking-organizational-improvement-with-scrum-seriously.html), the Org Improvement Team operates in a manner similar to a regular Scrum Team, just with a few slightly relabeled components.

Let's see how the Organizational Improvement Team will tackle these problems.

#### Organizational Improvement Queue (aka Product Backlog)

Since the causal loop diagrams above showed us that creating special teams for test automation and simply asking the Product Owner to change weren't going to solve the problems.

The Org Team can avoid wasting time on ineffective, localized solutions and focus the Improvement Queue on finding specific things that will contribute positive systemic results. Such as:

  * LongRegressionCycle - Involve more members of each Development Team in test automation;
  * LongRegressionCycle -Find alternate means to test automation that don't involve the browser;
  * UnfocusedProductOwner - Support the Product Owners in saying no to more expedited customer requests…

#### Organizational Queue Refinement (aka Product Backlog Refinement)

After discussion with the Development Team representatives and the Team level Product Owners, it is agreed that the pressure that the POs feel to respond to all customer issues within two days is getting in the way of the Teams delivering on both quality (which leads to more customer issues) and the big picture. They also identify the need for site license JetBrains IntelliJ and "Reducing Product Build Times from 15 minutes to 5 minutes".

#### Sprint Planning

The Org Improvement Team commit to running several experiments to resolve the UnfocusedProductOwner challenge. Since this problem will need several months to address completely, they decide to do the following:

  * Limit the number of Customer Expedite Issues that a team will be asked to handle in one Sprint to two (down from the four that currently happen most Sprints).
  * Suspend the current PO bonus system for 6 months - taking the bonus pressure out of the equation for now. Wisely they don't try to get rid of this altogether yet - while bonuses are often distortive and lead to strange behaviours in the short term, this is too big of a problem to tackle at this time. Instead, they've delayed dealing with until a later date.
  * Give the existing Portfolio Management Team a stronger mandate. Once decisions are made at the Portfolio level, these goals supersede the needs of any one customer. If there are special customer needs, they need to be approved at the Portfolio level and not just left to an individual PO.
  * In addition, to stem the worst of the problem with LongRegressionCycle, they suspend the current automation through the browser approach for now. _This isn't really a solution, it's just avoiding making a bad situation worse. In the context of the SmallestOnlineBookStore, this may be the best that the Org Improvement Team can do for now._

_The first three tactics are really just trying to give an already good PO some better tools to say no to all except the most important customer issues._

In addition to the big item that the Org Improvement Team committed to tackling, I would also find a couple of smaller, high-priority items that are likely achievable in the first sprint, such as the JetBrains Site license and "Improve Build Times by at least 5 minutes." This won't solve all of the problems for the Product Owners - just a manageable first step for one Sprint, which will be valuable to get the Team started, show the rest of the company that change is coming and prove to the Organizational Improvement Team themselves that they can make change.

#### In Sprint

Org Team Members work with ScrumMasters, Team Level Product Owners and some team members to update the Portfolio Kanban Board. They review the Portfolio Kanban Board with the rest of the management team including the C-level execs so there is a clear of understanding of which features will delivered in the near future.

#### Daily Scrum

Several times in the week the team members gather on the edge of the Dev Team work areas for their equivalent of a Daily Scrum. They make it clear that the events are open to all and share information about the progress on their commitments for the Sprint.

#### Sprint Review

At the end of the Sprint, the Org Improvement Team review how many Customer Expedite Issues each of the Development Teams had to deal with. While there was a reduction, it is still higher than their commitment in Sprint Planning. This hints that on the next Sprint, the Org Improvement Team might consider more action.

In addition, the Build Times have reduced by 3 minutes, from 15 to 12. The people who put the effort into this explain that the simplest improvements have now been done and further reductions will require upgraded hardware or parallel builds.

They invited all interested Dev Team members to the event so that the news of the improvements (small as they were) started to spread.

#### Retrospective

The Org Improvement Team realize that part of the reason they didn't meet all of their goals this Sprint is a lack of time dedicated to solving the systemic problems. For their SMART goal, they commit to each helping drive at least one issue to truly done, setting aside other executive work if required.

### Conclusion

In our last post we saw what we needed:

> "Respondents report that senior management sponsorship and support is far and away the most important factor in adopting Scrum."_ (2015 State of Scrum Report)_

#### To succeed:

  * Small Wins - _the Org Improvement Team are making an effort to start to resolve the bigger challenges_
  * Communicate - _the Org Improvement Team engaged the Dev Team Members in the formal events (Daily Scrum and Sprint Review) and informal conversation to share their progress_
  * Show how we've engaged Management to constantly review Portfolio Board, to understand Scrum, and to be involved in solving the problems that Scrum finds - _the Portfolio Kanban board was reviewed by Senior Management with Dev Team Members present_
  * Build on the previous successes - _they haven't been working long enough at this yet_
  * Tie changes back to the bigger reason that the organization is undertaking the change (usually Quality or Time to Market). - _the Org Improvement Team explains to all that the solving the Product Owner focus problem will help improve Time to Market and also Quality_

Even with an Organizational Improvement Team, problems still aren't easy to solve, but they're solved more easily when addressed at the right level.

_Images by Agile Pain Relief Consulting. Elements of first image [designed by Freepik](http://www.freepik.com/free-vector/vector-infographic-free-gear-template_714785.htm)._
