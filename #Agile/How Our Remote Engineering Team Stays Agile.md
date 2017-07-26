# How Our Remote Engineering Team Stays Agile

_Captured: 2016-05-20 at 16:51 from [www.helpscout.net](https://www.helpscout.net/blog/agile-remote-teams/)_

One of the foundational principles of [Agile](http://agilemanifesto.org) is _individuals and interactions_ over _processes and tools_.

In the past, this meant agile teams needed to be co-located to take advantage of high-bandwidth, face-to-face communication -- at least, that's been the prevailing belief across the industry.

> While proximity offers inarguable benefits, engineers also need long periods of focus time.

Having led co-located teams, remote teams, and mixtures of the two, I'm convinced there are significant advantages to remote teams and that agile methods can be adapted to them.

**With a remote team, you're able to:**

  * Hire the best and brightest engineers from [anywhere in the world](https://www.helpscout.net/blog/hiring-top-talent/).
  * Document and share all communications naturally via chat and video recordings.
  * Assemble meetings in a flash.
  * Say goodbye to commute issues.
  * Hire for and champion diversity, [which does wonders for the effectiveness of a team](https://www.gsb.stanford.edu/insights/diversity-work-group-performance).
  * Offer your team a more flexible work schedule.
  * Provide extended coverage throughout time zones with limited burnout risk.

With those compelling advantages, you shouldn't have to choose between "co-located and agile" and "remote and waterfall." At Help Scout, we've adapted agile processes to optimize for our distributed engineering team -- it's the best of both worlds.

## The tools we chose

We use [Trello](https://trello.com) to track work, because it's more lightweight and delightful for engineers to use than feature-heavy tools like [Jira](https://www.atlassian.com/software/jira). While Trello isn't optimized for software development out of the box, we've been able to make up for some of that with Trello plug-ins:

  * [Corrello](https://getcorrello.com) -- for tracking projects and Epics across iterations with burndown charts and velocity analytics regarding our progress.
![Corrello integration with Trello](https://www.helpscout.net/images/blog/2016/may/5-19-corrello.png)

![Git Hub integration with Trello](https://www.helpscout.net/images/blog/2016/may/5-19-git.png)

  * [Help Scout](http://help.trello.com/article/1007-using-the-help-scout-power-up) (of course!) -- so we can see customer conversations related to bugs or other work that needs to be tackled.
![Help Scout integration with Trello](https://www.helpscout.net/images/blog/2016/may/5-19-hs.png)

  * [Voting](http://help.trello.com/article/788-voting-on-cards) -- so we can track the team's interest in addressing technical debt, new tools or process changes.
![Voting in Trello](https://www.helpscout.net/images/blog/2016/may/5-19-voting.png)

We also use a wonderful tool called [Retrium](https://www.retrium.com) to facilitate our retrospectives, [Appear.in](https://appear.in) for small ad hoc meetings or peer code review (it's faster to set up than Google Hangouts), and Slack for nearly everything else.

## Trading standups for asynchronous updates

Engineers need to have a regular daily cadence, or standup, for communication and collaboration, to ensure peer-to-peer transparency and help prevent projects from being delayed or going off the rails. These standups help prevent the sad old story:

Q: How did this project get delivered a year late?

A: One day at a time.

With a fully distributed team, daily standups can be a huge pain -- across time zones, scheduled meetings force everyone to interrupt their work at times that inevitably are not ideal for at least one person. Daily meetings don't offer the flexibility we want to provide our team members if, for example, they want to start earlier on some days or attend an event at their child's school.

Even if you do go to the trouble of video-recording those, the viewer can't just turn to someone and ask them to clarify what they said. Instead, we ask everyone, at either the beginning or ending of their day, to share in their team's Slack "standup" channel:

  * What they did since yesterday's update.
  * What they plan on doing before the next update.
  * Whether anything is blocking them.

These updates provide transparency so the team doesn't annoy one another by asking, "So what are you up to? How is it going?" all the time -- we stay informed and in sync without anyone nagging anyone else. They also:

  * Give everyone visibility on how things are progressing and whether there are any impediments that need resolving.
  * Allow blockers, clarifications or misunderstandings to be addressed as soon as they occur.
  * Draw out engineers who might prefer to be "heads down" and coding.
  * Allow engineers to relay issues to their peers who can chime in and prevent technical blocks.
  * Show engineers the meaningful progress they're making and provide a history of progress.
  * Help engineers articulate a plan for the day and make commitments to each other. Engineering is a team sport, and often one person's work can't proceed until someone else provides the piece(s) they need to get their work done.

With these asynchronous updates, we get the benefits of daily standups without the negatives, and there's a searchable record at everyone's disposal.

## How we handle retrospectives and planning meetings

One regular, non-optional meeting is our retrospective at the end of every iteration. The team meets to address what worked, what didn't, and what we can do to improve.

> This is the single most important meeting we have because without it we don't learn and evolve.

While we still schedule a video meeting, we also use [Retrium](https://www.retrium.com) to facilitate a multi-stage retrospective that draws out everyone's feedback. Its "private brainstorming" feature prevents the groupthink that can occur when some folks say nothing and just agree with others' ideas without sharing their unique perspectives.

![VRetrium](https://www.helpscout.net/images/blog/2016/may/5-19-retrium.gif)

We also use Google Hangouts for our sprint planning meetings. Before the meeting, the team sizes the highest-priority Trello cards using [story points](https://agilefaq.wordpress.com/2007/11/13/what-is-a-story-point/) and records them with a simple Chrome extension called [Scrum for Trello](https://chrome.google.com/webstore/detail/scrum-for-trello/jdbcdblgjdpmfninkoogcfpnkjmndgje?hl=en). After reviewing the sprint goals, the team uses Trello to claim the number of cards they feel they can accomplish during the next two weeks and expands each card with a checklist of tasks.

## Demo all the things!

Agile engineering teams often hold a demo at the end of an iteration, or when a feature is done. While these demos work well for co-located teams, they can be another bottleneck for geographically distributed ones. The overhead of scheduling a remote, whole-team meeting can be a drag.

Rather than these demos, For every [Github pull request that has UX impact](https://help.github.com/articles/using-pull-requests/), we submit an animated GIF that demonstrates the software before and after the feature is implemented. These GIFs succinctly show off the feature, and the pull request includes details on the solution's background, solution and impact with a link back to the original Trello card.

![software ux change impact](https://www.helpscout.net/images/blog/2016/may/5-19-ux.gif) _GIF demonstrating a UX change made to Help Scout's [Docs](https://www.helpscout.net/knowledge-base/) product_

With these gifs our team is quickly oriented to the scope and impact of the change. No site to log in to, no account or data to set up, no "play" button to press (or ignore). We've found there's no better way to quickly communicate the change to a broad audience.

For non-visual changes, the pull request includes all the same background details without the animated GIF. For significant changes that adopt new technology or involve a large refactor, we record a deep dive.

## Record deep dives to disseminate knowledge

Engineering teams need to share technical information to break down silos and eliminate single points of failure where progress comes to a halt (e.g., when one engineer is on vacation). Code reviews and code quality improve dramatically when people are educated about the technology, approach and constraints of what was implemented.

To spread this knowledge, we run "deep dive" talks over video conference. While an audience makes the session dynamic and raises questions that can lead to additional insights, we don't make attendance mandatory. As long as we have a critical mass of 4-6 people, we hold the session, record it and post it internally for anyone to review later. These recordings also make excellent onboarding resources for new hires to learn not only about how our product was built, but the design thinking that influenced the end result.

## Optimize for asynchronous communication

Culture and communication are oxygen for remote engineering teams. Since Help Scout was my first experience leading a 100% remote team, I did a lot of listening before making any changes.

I've learned to optimize nearly everything for asynchronous communication -- daily standups, code reviews, feature demos, project updates and so on. I try to over-communicate in writing so there's always a record, and I insist on weekly or bi-weekly [one-on-ones](https://www.helpscout.net/blog/one-on-ones/). We do our best to record most video sessions so they can be reviewed at any time, and we always hold retrospectives.

> "Agile" and "remote" don't have to be at odds -- they can be as compatible as peanut butter and chocolate.

With a deliberate culture of consistent asynchronous communication, team members can focus on their work while staying in the loop. Our engineers thrive in an environment that promotes autonomy, trust and flexibility. The end result is a motivated and productive engineering team that can spend more time delivering value for our customers and our business and less time in painful meetings and long email threads.
