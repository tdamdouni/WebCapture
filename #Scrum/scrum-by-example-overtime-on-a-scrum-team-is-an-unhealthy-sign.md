# Scrum By Example – Overtime on a Scrum Team is an Unhealthy Sign

_Captured: 2017-07-27 at 21:01 from [agilepainrelief.com](https://agilepainrelief.com/notesfromatooluser/2014/03/scrummaster-tales-overtime-on-a-scrum-team-is-an-unhealthy-sign.html?utm_content=buffera173d&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer#.WXo4a6CbGaM)_

![](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2014/03/clock-arms-Freepik.jpg)

> _Overtime ticks past on the clock_

_The [Scrum By Example](http://agilepainrelief.com/notesfromatooluser/category/agile/scrum/scrummaster-tales) is a series of stories about ScrumMaster John who attended one of my courses. He is the ScrumMaster for the WorldsSmallestOnlineBookstore._

Things have been going well for our ScrumMaster John and the team as they build out the WorldsSmallestOnlineBookStore. The team is ramping up towards their first public launch and, in the past week and a bit, they could feel the tension increasing.

Three weeks before the scheduled release date, Ellen, the CEO, comes to the team's Daily Standup (without asking permission first). At the end of the standup she says, "It's really important for this release to be a success. I want to see lots of overtime in the next three weeks and no slacking. Everyone must be busy." After her speech, a few people mutter "Okay," and then the team quietly walk to their desks.

For the first week the team manage to deal with the added pressure, then Ellen has her bi-monthly meeting with the investors. The investors say it's not acceptable for the product to go to market with only one credit card supported (currently Visa), nor is it okay to do a soft-launch in Canada first. The site must be able to ship anywhere in North America.

Ellen returns to the team room and she is clearly on fire. She interrupts the working day to announce the additional requirements. "I realize this will be hard and there will some additional work but our investors think these changes are critical. Save time, stop writing those Unit Tests or trying to do any other engineering stuff."

John and Doug try to warn Ellen of the damage this will cause, but Ellen says, "Damn the torpedoes, we've got to get this out there. These two new features must get in, but don't drop any of the existing features. They're all priority one." In a panic, the team just start work. Of course the team aren't able to release after two more weeks with sixty hour weeks. In fact, they're struggling to release six weeks after the investors meeting.

During the overtime period:

  * Thirty new defects were written, more than in the previous three months.
  * Ian spent most of week working on supporting Amex as a credit card, before Ellen decided it wasn't as important as MasterCard/Visa support. So the feature got dropped but the code was left in the system.
  * Ian's code for the Amex feature created a bug in the previously working Visa feature that wasn't noticed until after the release because the team had stopped working on updating the existing automated acceptance tests.
  * Most team members stopped collaborating, and as a result Kirby misunderstood and spent several days writing server code that didn't fit with a client side code that Doug was writing.
  * Tonya got sick.
  * The late hours were having a significant effect on Martin's family life. He walked into Don's office (John's director) and threatened to quit if the overtime didn't change soon.

The release finally went live after six weeks, but instead of the rave reviews the team hoped for, users gave the store mixed reviews. They liked the basic system but found it had many bugs and subtle usability issues.

## Analysis

Why did a little overtime cause all these problems?

![Overtime - never hurt anyone](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2014/03/Overtime-small.jpeg)

> _Some key causes:_

  * Focusing on 100% utilization of team members (Ellen's comment - "no slacking") ensured that when people didn't have an obvious high priority user story to work on, then they would do anything to look busy. It turns out that systems (both human and mechanical) that are run at high utilization rates become fragile, inflexible, and error prone. (For more detail see Steve Gamble - [The Importance of Slack](http://www.stevegamble.com/redevelopment/2011/06/the-importance-of-slack.html))
  * Lacking clearly defined priorities, all the work got started at once. Later on when it was decided that Amex support wasn't as important, a week of Ian's time had been wasted.
  * With all the features being started at once, there was limited collaboration and no [swarming](http://www.infoq.com/news/2013/02/swarming-agile-teams-deliver). Limited collaboration meant that defect rates went up since there were fewer brains involved in each design decision.
  * When there is a lot of work in progress, [multi-tasking](http://www.infoq.com/articles/multitasking-problems) becomes the norm. After every context switch (i.e. moving to a new task, even answering an email) it takes 20-25 minutes to regain the highly productive state of work called [flow](http://www.amazon.ca/Flow-The-Psychology-Optimal-Experience/dp/0061339202) that high performance teams seek to achieve. In addition, error rates go up in part because we don't always correctly remember the context of a task when we switch back.

In a case like this, it often boils down to the CEO not having a good understanding of the Product Backlog for the team. In addition there is no map of the overall portfolio to help make the choices clear. Lacking better information, Ellen believed she could just keeping demanding more output with few consequences.

## How could John have handled this better?

The day Ellen first came into the room with the demand for overtime (before the investors meeting), John could have taken her aside later in the day and discussed the costs. The simplest explanation might have been that any system has a "[hull speed](http://agilecraft.wordpress.com/2014/02/13/hull-speed-for-systems/)", i.e. a maximum speed that can achieved without dramatically increasing the amount of effort. Adding more pressure won't make a significant difference to the speed and in some cases just risks damaging the hull. Instead of overtime, John could have suggested this would be a good time to reinforce [core hours](http://agilepainrelief.com/notesfromatooluser/2011/10/scrum-master-tales-more-interruptions.html), shutdown outlook for most of the day, and cancel most meetings outside of the team. They could even tell the company not to interrupt the team at all during the core hours. All of these changes have the goal of giving the team members more focused time.

When the investors demanded more features in the same timeframe, John and Product Owner Sue could have shown Ellen the product backlog as it stood. They could have asked her what she would either drop completely or delay until after the release to achieve the new goals. In addition, they could have asked her for the priorities of each of the new items. Even during a crunch, the team would still benefit from spending a couple of hours doing [backlog refinement](http://agilepainrelief.com/notesfromatooluser/2012/07/scrummaster-tales-story-splitting-fun.html#.UxAjBfRdVjo) with the new features. This would ensure that the team members have a common understanding and get at least minimal acceptance criteria for each. This would increase the chances that team members would collaborate during the crunch period.

In the future, Ellen would benefit from seeing a map of the overall project portfolio of the work in flight and queued - a portfolio map that gets updated every few weeks so she always has recent information to share with the investors. In addition, it would help with realistic expectations management.

But those positive Scrum practices didn't happen for our hapless team this time, and instead they will spend the better part of the next three to four months undoing the damage of the overtime.

_Clock image [designed by Freepik](http://www.freepik.com/free-vector/entrepreneurs-around-the-clock_774088.htm). Remaining image by Agile Pain Relief Consulting. _
