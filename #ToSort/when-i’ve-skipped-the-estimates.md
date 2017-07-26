# When I’ve Skipped the Estimates…

_Captured: 2017-07-08 at 09:07 from [paulmboos.com](https://paulmboos.com/2015/07/14/when-ive-skipped-the-estimates/?utm_content=buffer08a74&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

![spiral_clock](https://paulmboos.files.wordpress.com/2015/07/spiral_clock.jpg?w=424&h=424)

While the debate carries on whether one must have estimates or not, I thought I'd provide a viewpoint of when I found them no longer needed.

However, before go there, let's start off with a bit of a story about when estimates were not useful, but required, so I took the *EASIEST* path out.

Let's go back to 2008; I was just hired on as a software development Branch Chief in USDA and asked to prepare the budget for the next fiscal year. Of course, the first thing I did was poll around on what upcoming work there was. No one knew except that the same amount of maintenance as was last year. That was easy, apply an inflation factor on what we had this year, add a management reserve, and we're done.

Now onto the harder problem: what about the unknown new projects looming.

![dollar_tunnel](https://paulmboos.files.wordpress.com/2015/07/dollar_tunnel.jpg?w=600&h=450)

So I investigated how these normally got funded; any estimate done is simply reported up the chain (as requested Development monies), but the funds are actually provided by the programs that need the work done for them. These are used as a projection for the branch and nothing more. Any work really done goes through its own process of requesting and then actual money is provided.

So I asked, how many projects did we do the year prior and how much did they cost? And the year prior? And the prior to that? 4 projects, 4 projects, and 6 projects were the answers. (I won't go into the money numbers, but I'll note this branch did not develop super huge applications, but small to medium sized applications with some complexity - a GIS app, an analytical app, several tracking type apps, a loan package development application, that may give you the picture.) I didn't need to know the number of apps for the reporting, but I used that number to calculate the average cost per app we developed, projected into 2009 dollars; adding a standard deviation game me some more certainty, then a 15% management reserve. Once I had those numbers, the process was literally a half hour to run through the math a couple of times to ensure I was on target.

My project managers could not believe I was going to use that number; they always went around to each potential customer and asked them to conjecture on applications or upgrades they wanted. Most never got funded and something else came up and got funded, so why spend time estimating what never happened.

This was a very low precision estimate, but got me in a reasonable and justifiable target number. (If the system allowed for ranges, I would have provided those, but alas it didn't.)

I'm guessing you are wondering how 'correct' I was with that… We had 5 projects and it was fairly close to the average. The next year we did the same thing, but it was off - much higher as the Recovery Act kicked into high gear, but as I pointed out before, it didn't matter.

OK, that was budgets built using the least painful method of estimates possible. (Sometime in the future, ping me on how I executed on real work within the branch… The spoiler hint is I limited the WIP of projects going on at any one time, so that I could keep my team close to constant size, the increase meant I experienced a contractor headcount increase by about 2 people.

So now onto some maintenance estimation I did away with…

When I took over running the maintenance team at Office of Pesticide Programs, every Software Change Request (SCR) came in went into a queue where it was examined in a meeting and the contractor told to go estimate it. When the contractor came back with their estimate, usually a week later, the work was approved. They estimated in time and they could then quote the money as they figured out who was going to do the work and then they could apply their labor rate. This singular meeting was at least an hour long every week and consisted of telling the contractor go estimate the amount of work to do and report out on estimates made. This never went anywhere; no one did anything with these estimates. We never said no to the SCRs for the legacy systems we maintained, mostly because no one worked with the business well enough to know whether it should happen or not. On top of that, there were 20 some legacy apps with at least that many stakeholders to try and satisfy. Perhaps at some point, this estimation process was used to say no, but with the mostly low complexity work coming in, there was no drive to say no.

We set budgets based on annual contractor headcount. Perhaps at some point this estimation exercise was used for this, but it wasn't any longer.

So I did a couple of things, I killed the meeting. I put the onus on the government application maintenance staff to work with the business to prioritize the work in their viewpoint. I set-up a rule set for taking these priorities, along with a quick technical assessment (that set severity) and the date in, to establish a prioritization across all apps. I got these stakeholders to agree to this scheme so I didn't have to fight with each app. We still never said no, we just prioritized the work not started constantly.

And I eliminated the estimates. I decided on contractor staff based on how much work I could get through; I concentrated on further process improvements before I thought of increasing headcount. (You can [read about the Kanban system that was set-up](https://www.govloop.com/community/blog/epas-office-of-pesticide-programs-systems-design-development-branch-launches-kanban-for-software-maintenance/) on GovLoop if you so desire.)

To go full circle to where once again I found an estimate helpful in this environment was a potential regulatory change was going to require a rather large piece of work to our legacy PowerBuilder app. I was asked how long it would take; the upper management was interested in ensuring that we had enough lead time to get it done. Not having it done, had a financial impact on the Agency.

Since I had a Kanban system implemented in Trac, I filtered out that legacy's enhancements to similar ones and calculated the average and two standard deviations. I gave them that range with stating the high number had 95% confidence we'd fit within it. They deeply appreciated the accuracy and precision in this case. This is a form of estimation of course, but the real point is day-to day, we never estimated; there was zero value in it. We did capture actual data though using our system, which made predictability possible just as I mentioned above.

Hopefully this will help others at least understand one context where estimations weren't needed and also where low fidelity estimates were good enough to establish a reasonable estimate. I consider myself a no estimates guy, only because I look at the assumptions of why I need to estimate and if I don't and can derive a more suitable answer in some manner, I'll probably use that. It's all a matter of context.
