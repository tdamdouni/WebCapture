# Rethinking Component Teams for Flow

_Captured: 2017-01-15 at 20:50 from [dzone.com](https://dzone.com/articles/rethinking-component-teams-for-flow?edition=263882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-15)_

### How can you fix shortcomings on your teams? A common approach is to bring in specific area experts to augment your capabilities, but this can be hard to manage.

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

A couple of weeks ago, I spoke locally about [how to manage your project portfolio](https://www.jrothman.com/books/manage-your-project-portfolio-increase-your-capacity-and-finish-more-projects/). Part of the talk is about understanding when you need project portfolio management and flowing work through teams.

One of the (very sharp) fellows in the audience asked this question:

> As you grow, don't you need component teams? 

I thought that was a fascinating question. As agile organizations grow, they realize the value of cross-functional teams. They staff for these cross-functional teams, and then they have a little problem. They can't find enough UX and UI people, or they can't find enough database people, or they can't find enough writers, or they can't find some other necessary role for the "next" team. They have a team without necessary expertise.

If managers allow this, they have a problem: They think the team is fully staffed, and it's not. They think they have a cross-functional team that represents some capacity. Nope.

Some organizations attempt to work around the scarce expertise problem. They have "visitors" to a team, filling in where the team doesn't have that capability.

When you do that, you flow work through an incomplete team. You're still flowing work, but the team itself can't do the work.

You start that, and sooner or later, the visitor is visiting two, three, four, and more teams. One of my clients has 12 UI people for 200 teams. Yes, they often have iterations where every single team needs a UI person. Every single team. (Everyone is frustrated: the teams, the UI people, and management.)

When you have component teams and visitors, you can't understand your capacity. You think you have capacity in all those teams, but they're component teams. They can only go as fast as the entire team, including the person with the scarce expertise, can deliver features. When your team is not first in line for that scarce person, you have a Cost of Delay. You're either multitasking or waiting for another person or you're waiting for an expert. (See [CoD Due to Multitasking](https://www.jrothman.com/mpd/portfolio-management/2014/02/cost-of-delay-multitasking-part-2/), [CoD Due to Other Teams Delay](https://www.jrothman.com/mpd/portfolio-management/2014/02/cost-of-delay-due-to-other-teams-delay-part-5/), and [Diving for Hidden Treasures](https://www.jrothman.com/books/diving-for-hidden-treasures/).)

What can you do?

  1. **Flow work through the experts. **Instead of flowing work through teams that don't have all the expertise, flow work through the experts (not the teams).
  2. **[Never let experts work alone](https://www.jrothman.com/articles/2012/02/management-myth-2-only-the-expert-can-perform-this-work/). **With any luck, you have people in the team working with the experts. In Theory of Constraints terms, this is exploiting the constraint. It doesn't matter what other work you do. If your team requires this expertise, you need to know about it and exploit it (in TOC sense of exploitation).
  3. **Visualize the flow of work. **Consider a Kanban board such as the one below that shows all the work in progress and how you might see what is waiting for whom. I would also measure the Cost of Delay so you can see what the delay due to experts is.
  4. **Rearrange backlog ranking** so that you have fewer teams waiting for the scarcity.
![Image title](https://dzone.com/storage/temp/3988010-screen-shot-2017-01-12-at-105318-am.png)

Here's the problem: When you allow teams to compete for scarcity (here, it's a UI person), you don't get the flow of work through the teams. Everything is slower. You have an increased Cost of Delay on everything.

Visualizing the work helps. Flowing the work through the constrained people will show you your real capacity.

Needing component teams is a sign someone is still thinking in terms of [resource efficiency, not flow efficiency](https://www.jrothman.com/mpd/agile/2015/09/resource-efficiency-vs-flow-efficiency-part-5-how-flow-changes-everything/). I bet some of you will tell me it's not possible to hire new people with that skill set locally. I believe you.

If you can't hire, you have several choices:

  * **Have the people with the scarce expertise consciously train others** to be ready for them, when those scarce-expertise people become available. Even I can learn some capability in the UI. I will never be a UI expert, but I can learn enough to prepare the code or the tests or the experiments or whatever. (I'm using UI as an example.)
  * **Change the backlogs and possibly reorganize as a [program](https://www.jrothman.com/books/agile-and-lean-program-management-scaling-collaboration-across-the-organization/).** Now, instead of all the teams competing for the scarce expertise, you understand where in the program you want to use that scarce expertise. Program management can help you rationalize the value of the entire backlog for that program.
  * **Rethink your capacity and what you want the organization to deliver when.** Maybe it's time for smaller features, more experiments, and more MVPs before you invest a ton of time in work you might not need.

I am not a fan of component teams. You could tell, right? Component teams and visitors slow the flow of releasable features. This is an agile management problem, not just a team problem. The teams feel the problem, but management can fix it.

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).
