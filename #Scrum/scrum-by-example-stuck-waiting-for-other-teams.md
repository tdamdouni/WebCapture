# Scrum By Example – Stuck Waiting for Other Teams

_Captured: 2017-08-08 at 19:03 from [agilepainrelief.com](https://agilepainrelief.com/notesfromatooluser/2014/08/scrummaster-tales-stuck-waiting-for-other-teams.html#.WYnutaCbGaN)_

![stop sign image](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2014/08/stop-sign.jpg)

Getting stuck waiting for people outside your Scrum Team? Some examples of how to handle this situation.

John (ScrumMaster) and the team are humming along nicely building great new features for the SmallestOnlineBookStore. With the huge success of the first big release nine months ago, venture capital money has come flowing into the company. Significant investments have been made in Operations, Security, and Networking in addition to creating several new Development Teams. Unfortunately, all these new people are making it more difficult for the team to get the software they built deployed.

The new groups are often imposing their own reviews and processes on the software before it's deployed. Some changes are going to increase the load on the network and require review by the network team. Other changes affect the payment gateway, backend administration, and the services team who have a lead time of three weeks. All of these reviews, while increasing safety, have greatly slowed the delivery of new features.

The Development Team is getting frustrated because they feel their work is slowed artificially by the teams downstream of them (i.e. Networking and Security). The customers are getting annoyed because the previously great flow of features has slowed down to a crawl.

In addition, the team has created a Work in Progress (aka WIP) of one story per developer. This is both exacerbating and revealing the problem. It's exacerbating because the team doesn't have background to work on whenever their main task is stuck. It also reveals that the real problem isn't at the team level where the work is getting to "almost" done.

John creates a short list of options for the team: **Increase individual WIP limits** to 2; **Change the Definition of Done** so that Security and Network reviews aren't part of Done; **Add a column to their Scrum Task Wall** to account for both other groups and start working with the other departments to clear work more quickly.

## Analysis

Before we explore options in a situation like this I prefer to gather data. The best way in this case would be to create a Kanban wall that tracks the progress of a Story from initial idea to the moment it's deployed and is delighting customers. This, combined with a Cumulative Flow Diagram, will help the source of the Team's stress.

John, being aware this might be an issue, has been tracking the data for just over a month:

![ScrumMaster_Tales_-_Stuck_Waiting_for_Other_Teams_data_table](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2014/08/ScrumMaster_Tales_-_Stuck_Waiting_for_Other_Teams_data_table.jpg)

From the data we can produce a Cumulative Flow Diagram that looks like this:

![Cumulative Flow Diagram ](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2014/08/ScrumMaster_Tales_-_Stuck_Waiting_for_Other_Teams_CFD_chart.jpg)

So what does this chart show? The team isn't the bottleneck in this case. A simple test I use to tell is this:

"If we had a magical way to double the rate at which you deliver stories/features, would that make any real change in the rate at which customers get the features?"

At the development team level - Code, Code Review, Testing - clearly that isn't the case, the bottleneck is in "Done in Development", which is really just a buffer, and Network/Security review. Rather than make changes at the team level, we need to see what we can do to optimize the downstream work.

Based on this data, let's re-examine the team's options:

  * **Increase Individual WIP Limit **from 1 to 2 - _This really just masks the problem giving something else for someone to work on when their original item is stuck in Network or Security. As we've already seen the limit isn't at the team level, so optimizing there won't help._
  * **Change the Definition of Done** so that a Story is considered Done when it's handed off to an outside team. - _This doesn't really help the customer since the item still isn't deployed, it just makes each individual developer feel better. However, in creating an additional column for the downstream groups, we have effectively created a Definition of Done for each column. Kanban calls these "policies". So we have changed "Done" but only in the name of making our problems more apparent._
  * **Add a column to the Scrum Task Wall** - __We didn't quite do that, instead we created a Kanban wall that acknowledges some of the work is beyond our team's span of control.__

So let's add a new option:

  * **Start working with the other departments to clear work more quickly** - _In a Kanban oriented world, teams swarm downstream blockages. This would definitely be a good idea in our case._

Were I coaching John, I would get him to setup the Kanban tracking wall with the other teams and departments so that the entire company gets a view of where the work stands. I would invite people from each group to come update the wall every couple of days. By getting their involvement in set up and tracking, people from the other teams (i.e. Security and Networking) will appreciate that the data reflects their world and they will be more open to acting on the data. In addition, John (and his team) will gain greater insight into what is affecting Networks and Security - perhaps the company was suffering from a Denial of Service attack at the end of June and for a few days both teams were pulled from reviewing to handle the operational problem.

The team might also discover that they're found to frequently be violating security practices. In this case, mentoring from Security might increase the team's level of skill in this area, and reduce time spent in the review phase. Very often in cases like this, cross-training the team (see: [The Team Gets Bottlenecked](http://agilepainrelief.com/notesfromatooluser/2012/02/scrummaster-talesthe-team-gets-bottlenecked.html)) to help reduce the downstream bottleneck will help, however we won't know until we've gathered data and worked with the other teams to find out what the real problem is.

_As an aside, I don't recommend individual WIP limits when working as part of a Scrum Team - instead focus on the WIP for the entire team. It's a small change, but it makes it clear that the productivity of the team is more important than that of any one individual._

__First image [designed by Freepik](http://www.freepik.com). Remaining i_mages by Agile Pain Relief Consulting. _
