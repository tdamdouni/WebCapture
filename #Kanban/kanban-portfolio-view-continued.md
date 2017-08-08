# Kanban Portfolio View – continued

_Captured: 2017-08-07 at 15:30 from [agilepainrelief.com](https://agilepainrelief.com/notesfromatooluser/2015/03/kanban-portfolio-view-continued.html?utm_content=buffer4826a&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer#.WYhra6CbGaM)_

![Kanban Portfolio view](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2015/02/scrum-alone-not-enough-kanban.jpg)

_(Continued from [Kanban Portfolio view](http://agilepainrelief.com/notesfromatooluser/2015/02/kanban-portfolio-view.html) and the 3 core rules. This is the conclusion of Part 2 in the [Scrum Alone is Not Enough](http://agilepainrelief.com/notesfromatooluser/2015/01/scrum-alone-is-not-enough.html) series.)_

## 2\. Limit Work In Progress

We know from [queuing theory](http://availagility.co.uk/2008/10/28/kanban-flow-and-cadence/), psychology of [multi-tasking](http://www.infoq.com/articles/multitasking-problems), and empirical evidence (_[Rally study](https://www.rallydev.com/finally-get-real-data-about-benefits-adopting-agile), [my summary](http://agilepainrelief.com/notesfromatooluser/2013/09/stable-teams-really-do-matter.html) of the Rally Study_) that more Work in Progress means less work gets done overall. **This leads to the second Kanban rule: Limit Your Work in Progress**.

Work that hasn't been deployed, shipped, or otherwise delivered to a customer has no real value. Value is only realized when the work is available for use by the customer.

The simplest way to Limit Your Work in Progress is to just watch for a few weeks how much work exists in each column. Make this your initial WIP (Work In Progress) Limit. The idea is that we shouldn't start new work before the existing work gets to done. Once each column has a WIP limit and the columns fill up, then we're forced to move downstream to help get the most downstream work to truly done.

In the context of the Bookstore:

![SmallestOnlineBookstore_Portfolio-WIP-Limits](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2015/03/SmallestOnlineBookstore_Portfolio-WIP-Limits.png)

In the above example, both John and Sarah's development Teams have no problem staying within their WIP limits of one. However, so much work has been done in the past week that the Online Help Team is swamped and falling behind. Improvements we make at the development Team level at this stage would just serve to build out more product that doesn't have online help. Instead, Team members from these Teams should volunteer to take on Online Help related work as part of their Sprint Commitment until the issue is solved. If this is a persistent problem, the organization needs to consider a more systemic fix - either finding more people to create the online help, or to include the online help in the Sprint level Definition of Done.

## 3\. Measure and Improve

**The third and final core Kanban rule.**

Too often we focus our energy improving the productivity of the development teams even when that won't change the amount of value delivered to the customer. A simple test: will doubling the productivity of a development team double the amount of value delivered to the customer? If not, then the development team isn't what needs to improve first.

Kanban affords us many opportunities to measure so we can know where to focus our energy to get the best improvement. The trick is to use these measurements judiciously.

* Cycle Time - measures the moment the team starts work on a request until it's delivered to production.

* Lead time - measures the moment that a request comes from the customer until it's delivered.

Which to measure first? In many cases, all we control is the Cycle Time. Unfortunately, if this isn't the major source of delay, then improving productivity here won't make a major difference to the customer. Lead Time is what the customer really sees, as their request enters the system and emerges sometime later.

The measurements (often shown via a [Cumulative Flow Diagram](http://brodzinski.com/2013/07/cumulative-flow-diagram.html)) show us where our limited improvement energy is most likely to bear fruit.

![CFD - Lead Time Vs Cycle Time](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2015/03/CFD-Lead-Time-Vs-Cycle-Time.png)

In the example above, we can see the bottleneck (online help) is downstream of our development teams. We have already determined by looking at the WIP that making a significant change in the productivity of our development teams wouldn't make any real difference in how quickly the customer received working software. So the challenge now is identifying that and determining how to get the value to the user quickly.

In many situations I encounter, there is a formal signoff before the application is deployed. In others, there is formal notification procedure to the end users. If this signoff or notification only happens once every four weeks, then the average item waits an additional two weeks after work on it is completed, while accruing no additional value. While these waits can't be wholly eliminated, the simplest thing to do is have them happen more frequently. Instead of once every four weeks, make it weekly. This cuts the average delay from two weeks to three days. Still not perfect, but tolerable if signoffs are required.

Once we've made our first improvement, wait for a few weeks, gather more data, and measure again.

In the case of the SmallestOnlineBookStore we can also see that Ideas are taking from ten to twenty weeks to get from the proposed stage to part of the Common Product Backlog. (_The picture below shows an unrealistically smooth development and deployment process._)

![CFD Showing how long it takes for an item to become part of the Teams Common Product Backlog](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2015/03/CFD-Showing-how-long-it-takes-for-an-item-to-become-part-of-the-Teams-Common-Product-Backlog.png)

This time it's clear that if we doubled the productivity of the development Team, we would double the value delivered to the customer, so in this case improving the Team's capacity will help.

**Warning** - don't confuse a CFD (Cumulative Flow Diagram) or other measurement with the real world. A measurement is just a hint to go find out what is really happening. In the world of Lean and Toyota, this is called a [Genchi Genbutsu](http://en.wikipedia.org/wiki/Genchi_Genbutsu). Take a walk and talk to the people doing the work. Find out what is really going on.

Once we understand what our basic Kanban system is telling us, it often helps to track additional information by categorizing as follows:

* Production Support/High Priority Work

* Work for Other Teams

* Interruptions

### _Production Support/High Priority Work_

A team that has a product live in the field might have to handle production support. When that happens our goal is to resolve the issue but also highlight the cost of handling additional work. In the long run the team need to reduce the defects that result in production support problems. Agile Engineering techniques (an upcoming post) will highlight approaches to solving this problem.

### _Working for/with Other Teams_

When working in a multi-team environment we have to accept that some portion of each team's time will be set aside to help their peers, even though this work won't directly advance the features on our own Products. When we use [Feature Teams](http://featureteamprimer.org/) we lessen the burden but we will still need to set aside time. Many Teams just allocate a fixed amount of their Sprint Capacity to helping their neighbouring Teams. In this case, during Sprint Planning the Team commits to helping other Teams up to that preset limit. The limit is usually agreed on in advance among the ScrumMasters and Product Owners of the respective Teams. As the reality of work tells what is really required, you can change the amount for future sprints.

### _Interruptions_

This is any other work (not High Priority or Work for Other Teams) that arrives outside of the Product Backlog and Sprint Planning meeting. Often it arrives in the form of "Could you do me a favour?" but sometimes there is no ask, it's just demanded. This is the source of much of the "dark work" mentioned in Part I. In the best of environments, the ScrumMaster has a seat next to the team room door. When an interruption arrives the ScrumMaster walks the person to the Kanban wall and shows them what other work will be harmed or delayed by dealing with interruption. If the person has enough power or influence they may insist their problem is addressed anyway. In that case, the Kanban wall and CFD can help everyone see the cost of interruptions.

Depending on how much work we have in these three categories, we can use a simple informal measure of this work by just counting the number of items in each category (Production Support, Other Teams, and Interruptions) per sprint and display it next to the CFD. This provides a simple visual representation and will show that the Sprints with the highest volume of these ultimately delivered less value.

Our goal here is to make clear the linkage between additional work and productivity.

If the volume is high enough that we require a more sophisticated model, we could go further and create a swim lane or row for each category (Production Support, Other Teams, and Interruptions) and then model them in our CFD. For the SmallestOnlineBookStore it might look like:

![SmallestOnlineBookstore_Portfolio_WithSwimLanes](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2015/03/SmallestOnlineBookstore_Portfolio_WithSwimLanes.png)

They decided to create dedicated lanes for the Production Support and Interruptions. These dedicated lanes highlight that while this work maybe necessary it reduces the productivity of the development teams. They also help keep this work highly visible.

When it comes to work for other Teams, they've chosen a different coloured card to help with tracking, but otherwise have included it as part of normal sprint work to indicate that this an expected normal activity.

Use the data you've gathered here to work with your peers - your goal is to reduce the rate of interruptions and eliminate many production support issues by raising quality (see the upcoming post on Agile Engineering Practices).

## Next Steps

Now that you have your first Portfolio Kanban board, and you know how to measure and improve, keep reviewing with all Team members once a week. Make it a regular rhythm or cadence. From time to time, review not just the content but also the board structure.

* Use it as a tool to start conversations and keep all work out in the open.

* Ensure your peers are involved in updating it so they feel ownership of the information.

* Keep it on real wall - if at all humanly possible, keep it on a physical wall, rather than in digital form. A wall that people will walk by multiple times a day and be reminded of the information. In addition, interacting with objects in the real world stimulates the brain in ways that a picture displayed on a large screen TV does not.

* Force Teams and the whole organization to make real prioritization decisions instead of just dumping more work in Team members' laps.

I recommend not tracking individual stories or tasks at the Sprint level on this board because it sends a signal to management that the individual item's progress should be tracked. It also signals to Team members that their Sprint level work is being watched and it sometimes becomes a tool to micromanage Team members, when the focus of Scrum is the opposite. Inside each Sprint, the Team (not the ScrumMaster) should have complete control over how their work is tracked.

Used well, a Portfolio Kanban Wall can help highlight where the improvement is required to improve the throughput of the whole organization, and not just one Team. Coupled with an Ongoing Organizational Improvement Team, it can be a powerful catalyst for change.

### Other Sources

Karl Scotland - [Portfolio Kanban](http://availagility.co.uk/2012/06/23/portfolio-kanban/)

Jason Little - [Designing an Enterprise Portfolio Kanban Board](http://www.agilecoach.ca/2013/03/31/designing-an-enterprise-kanban-portfolio-board/)

Pawel Brodzinski - [Portfolio Management with Kanban](http://leankit.com/blog/2012/06/the-benefits-of-portfolio-management-with-kanban/) and [Portfolio Kanban - Why Should I Care](http://brodzinski.com/2013/03/portfolio-kanban-why-should-i-care.html)

Sandy Mamoli - [Portfolio Kanban](http://www.infoq.com/presentations/portfolio-kanban)

Ian Mitchell - [The Kanban Sandwich](https://www.scrumalliance.org/community/articles/2013/june/the-kanban-sandwich-a-bite-size-recipe-for-agile-w)

Klaus Leopold - [Kanban and Its Flight Levels](http://www.klausleopold.com/2013/07/kanban-and-its-flight-levels.html)

Klaus Leopold & Troy Magennis - [Using Blocker Clustering, Defect Clustering, and Prioritization for Process Improvement](https://www.infoq.com/articles/blockers-defects-process-improvement)

_Images by Agile Pain Relief Consulting. Elements of first image [designed by Freepik](http://www.freepik.com/)._
