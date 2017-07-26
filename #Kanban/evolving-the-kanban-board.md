# Evolving the Kanban Board

_Captured: 2017-02-26 at 23:49 from [dzone.com](https://dzone.com/articles/evolving-the-kanban-board?edition=272906&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-26)_

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

My wife and I are planning to move. We aren't sure where we want to move to, or indeed how much we have to spend. Naturally, though, we want to get the highest possible selling price for our current house in order that we have as many options as possible. So we called in a "house doctor" to help.

After she (the house doctor, not the wife) had recovered from the initial shock of seeing how we have customized a fairly standard 4-bedroom house into a 6-bedroom eclectic disaster, she produced a report containing a list of cosmetic improvements we should make in order to attract prospective buyers. The list is long, with jobs for myself, my wife, and our local handyman. We needed to make the project manageable in a way that would allow us all to contribute as and when we have the time. So I found an old whiteboard in the garage and made this:

![full2](https://silkandspinach.files.wordpress.com/2017/01/full2.jpg?w=594)

As you can see, I drew a very rough plan of the house, including sections for upstairs, downstairs, the attic, and the outside. We then wrote a small sticky note for every improvement suggested by the house doctor (blue) and some that we had always wanted to do ourselves (yellow).

When we finish a task, we simply remove the ticket. For example, you can see that we have already finished all of the tasks needed in the Office (priorities, right?).

![up1](https://silkandspinach.files.wordpress.com/2017/01/up1.jpg?w=594)

And why am I telling you all this? Because this is what I recommend teams do for their software projects. When you pick up the next feature, draw an architecture diagram and populate it with sticky notes. The resulting board is a "map" showing the feature and the tasks that need to be done in order to deliver that feature (thanks to [Tooky](https://twitter.com/tooky/status/821802655764844545) for that analogy).

  * The diagram you draw for Feature A might differ from the one you draw for Feature B because you might be touching different parts of your estate. That's cool. The diagram needs to be the one that's most appropriate for the work you're about to do.
  * The visual representation of your architecture allows more people to be engaged in discovering the tasks that need to be done to deliver the feature.
  * And it allows everyone, often including non-programmers, to see and understand the scope and impact of what is to be done.
  * Sometimes doing a task will spawn others: things we didn't consider when we did the original feature break-down; things we've learned by making changes or completing spike tasks; things we or the Product Owner couldn't envisage sooner. That's fine -- we simply add and remove sticky notes as we think of them (and look for opportunities to slice off a separate feature that we can push back onto the ideas heap). The whole thing is quite dynamic, and yet very well controlled at the same time.
  * If possible I like to include testing in the scope of the stickies, possibly adding a few explicit testing task stickies where necessary.
  * As you finish each task (whatever "finish" means for your team), either remove the task's sticky note or mark it with a big green tick. For our house doctor board, we've decided that removing the stickies is best. But for software teams, I generally recommend adding big green ticks to completed tasks. This allows anyone to see how much progress you have made through the current feature, and which areas still need more work.
  * Sometimes the distribution of ticked and un-ticked stickies will suggest opportunities for splitting the feature and releasing a subset earlier than planned.
  * Hold stand-up meetings around the diagram as often as you need, and certainly whenever anything significant changes (some of the teams I coach have been known to hold informal stand-ups 4-5 times each day). The architecture diagram helps facilitate and focus these discussions and makes it much easier for everyone to contribute.
  * Note that all of the above works best when the team has a single feature in flight. A WIP limit of one, single piece flow.
  * This approach works well when combined with the [5-day challenge](https://silkandspinach.net/2014/05/14/estimating-user-stories-the-5-day-challenge/).

As usual with the recommendations I write in this blog, this idea is probably not a new one. But it is highly effective, and I recommend you try it.

Update:

I gave a lightning talk on this topic at the [Lean Agile Manchester meetup this week](https://www.meetup.com/Lean-Agile-Manchester/events/236800330/). There is a video (below), although unfortunately, you can't actually see what's on the slides. So I uploaded the slides [here](http://www.slideshare.net/kevinrutherford/evolving-the-kanban-board).

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).
