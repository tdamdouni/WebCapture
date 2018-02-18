# Scrum Alone is Not Enough

_Captured: 2018-02-18 at 17:26 from [agilepainrelief.com](https://agilepainrelief.com/notesfromatooluser/2015/01/scrum-alone-is-not-enough.html?utm_content=buffera1d61&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer#.Womo-oq1KhB)_

![Scrum Alone Is Not Enough](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2015/01/scrum-alone-not-enough-2.jpg)

To be successful with Scrum in the long term you need more than the basic framework. This is intentional. Scrum provides the structure as a starting point, but it's designed to work well when applied with other effective patterns.

Like the [Design Patterns](http://en.wikipedia.org/wiki/Design_pattern) movement of the late '90s, a pattern can be used by itself or with others. E.g. the [Command Pattern](http://en.wikipedia.org/wiki/Command_pattern) and the [Memento Pattern](http://en.wikipedia.org/wiki/Memento_pattern) can be combined to build an effective undo/redo system. Scrum is only one pattern for one team. It gives you the bare minimum framework that could possibly work, however in many contexts you will need to incorporate other tools/patterns to build more effective systems.

### Beyond Scrum you should consider:

- Effective Agile **Engineering** Practices - such as Unit Testing, Continuous Integration, Test Driven Development, Acceptance Test Driven Development (or BDD), Pair Programming. Without practices like these, the health of your codebase will degrade over time.

- **[Kanban**](http://agilepainrelief.com/notesfromatooluser/2015/02/kanban-portfolio-view.html) - (a tool to understand and improve flow) to help understand the flow of work at both the team and organization level. Without a good understanding of flow of work through the organization, we might make a change that is a local improvement but harms the whole. ([Part 1: Visualize Your Work](http://agilepainrelief.com/notesfromatooluser/2015/02/kanban-portfolio-view.html) | [Part 2: Limit WIP, Measure and Improve](http://agilepainrelief.com/notesfromatooluser/2015/03/kanban-portfolio-view-continued.html))

- **[Portfolio Management](http://agilepainrelief.com/notesfromatooluser/2015/06/portfolio-management.html)** - the art of making big picture decisions about which major chunks of work the business would like focused on next. Organizations need portfolio management to ensure that major priorities are understood by the team's Product Owners and worked on in priority order. ([Part 1: Portfolio Management](http://agilepainrelief.com/notesfromatooluser/2015/06/portfolio-management.html) | [Part 2: Idle Teams](http://agilepainrelief.com/notesfromatooluser/2015/07/portfolio-management-idle-teams.html))

- **[Organizational Improvement](http://agilepainrelief.com/notesfromatooluser/2015/09/taking-organizational-improvement-with-scrum-seriously.html)** - many issues that Scrum helps to find can't be solved by the team or their ScrumMaster. Instead, organizations need to establish an ongoing improvement team dedicated to resolving these problems. ([Part 1: Taking Organizational Improvement Seriously](https://agilepainrelief.com/notesfromatooluser/2015/09/taking-organizational-improvement-with-scrum-seriously.html) | [Part 2: Case Study](https://agilepainrelief.com/notesfromatooluser/2015/11/taking-organizational-improvement-seriously-case-study.html))

- **Intra Team Coordination** - How will you coordinate the work among teams? Scrum of Scrums is the most well known pattern and yet is rarely the best choice.

- **Team Organization** - How will you organize your teams? As Component Teams? As Feature Teams? Using the Spotify model of Squads, Tribes and Guilds?

> ### There are no best practices.

Scrum itself could prescribe all of this, but that would be missing an important Agile point: there are [no best practices](https://agilepainrelief.com/notesfromatooluser/2010/03/there-are-no-best-practices.html). A practice that works well in one organization (or context) may not work well in yours. This is especially true when it comes to working effectively at a large scale where repeatable patterns are only just starting to emerge. Even where consistent patterns are starting to emerge (i.e. Large Scale Scrum, Enterprise Scrum, …), it is often unclear which one will apply in a specific context.

Finally, remember that Scrum isn't intended to fit your current organization and its existing structure. It is intended to force us to consider what is working and what needs improvement.

Scrum is just the starting point.

_In the next few months, I will explore patterns that can be effective when attempting Scrum at a larger scale (more than three teams). What topics would you like me to explore?_

_Image by Agile Pain Relief Consulting. Elements of image [designed by Freepik](http://www.freepik.com/)._

  
![Portfolio Management](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2015/06/scrum-alone-not-enough-portfolio-management.jpg)

(_Continued from [Portfolio Management Part 1](http://agilepainrelief.com/notesfromatooluser/2015/06/portfolio-management.html) in the [Scrum Alone is Not Enough series](http://agilepainrelief.com/notesfromatooluser/2015/01/scrum-alone-is-not-enough.html)._)

Imagine that the Portfolio Management group is giving the individual Product Owners a budgetary envelope of an approximate size. As Product Owners, we expect to make small bets on individual User Stories that will deliver value to the customer. The Portfolio Management group wants to make mid-sized bets (>1 Team Sprint) that will deliver value to the customer.

But let's say the current Sprint is one in which some Team members don't really have a lot to do. This is the type of scenario that often drives management crazy because they see idle workers, and traditional thinking is that idle workers don't deliver value. This rarely ever happens in real life because there's almost always more work than there is Teams to do it, but should the rare situation occur when one doesn't have work in the current Sprint, questions that arise may be things like:

  * should we temporarily reassign those Team members to other teams/projects that are lagging behind, to help them catch up?
  * should we give them a feature that is further down the road in the backlog to work on in the meantime, with the thinking that it will give us a head start on it since they're sitting idle anyway?

The answer is, of course, to do neither.

If the 'idle' Team were to join another Team temporarily, it wouldn't speed things up - just the opposite, it would slow everything down. Disrupting that Team's effectiveness and cadence, their contribution would be much smaller than their effect in reducing the other Team's capacity. In addition, it could harm moral by suggesting that the other Team can't handle the tasks themselves.

And if the idle workers start developing a Feature that is further ahead on the Backlog, it undermines the Product Owner and Portfolio Management's priority settings and decisions, which leaves room for "hey, could you do me a quick favour" requests within the Sprint that weren't in the Sprint backlog. By the time the rest of the Team gets to that feature in the backlog, they may find that the work the idle Team had made on it is obsolete and needs to be undone before they can make new progress.

The best solution is have 'idle' Team members look at the board and see if there are bottlenecks that they can help with within their own Team. They could also pay down their technical debt, or spend time learning something that expands their capacity as a Team to work outside of their current area/column(s) on the Kanban chart. For example, [the Team in the previous examples](http://agilepainrelief.com/notesfromatooluser/2015/06/portfolio-management.html) might teach themselves something about testing or creating effective online help.

The most effective thing (in terms of delivering value) is to not focus on the idle worker at all, but continue to focus on finishing the work and maximizing value delivered to the customer. This is where Portfolio Management can really excel, by understanding this fundamental truth and facilitating it.

_Image by Agile Pain Relief Consulting. Elements of image [designed by Freepik](http://www.freepik.com/free-vector/vector-infographic-free-gear-template_714785.htm)._
