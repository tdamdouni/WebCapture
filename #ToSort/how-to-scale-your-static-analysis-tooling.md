# How to Scale Your Static Analysis Tooling

_Captured: 2017-05-21 at 10:21 from [dzone.com](https://dzone.com/articles/how-to-scale-your-static-analysis-tooling-1?oid=twitter&utm_content=bufferbc800&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

_Editorial Note: I originally wrote this post for the NDepend blog. You can [check out the original here, at their site](https://blog.ndepend.com/how-scale-static-analysis-tooling/)._

If you wander the halls of a large company with a large software development organization, you will find plenty of examples of practice and process at scale. When you see this sort of thing, it has generally come about in one of two ways. First, the company piloted a new practice with a team or two and then scaled it from there. Or, second, the development organization started the practice when it was small and grew it as the department grew.

![Image title](http://www.daedtech.com/wp-content/uploads/2014/11/UpFrontPlanning.jpg)

But what about "rolled it out all at once?" Nah, (mercifully) not so much. "Let's take this thing we've never tried before, deploy it in an expensive rollout, and assume all will go well." Does that sound like the kind of plan executives with career concerns sign off on? Would you sign off on it? Even the pointiest haired of managers would feel gun shy.

When it comes to scaling a static analysis practice, you will find no exception. Invariably, organizations grow the practice as they grow, or they pilot it and then scale it up. And that begs the question of, "how?" when it comes to scaling static analysis.

Two main areas of concern come to mind: technical and human. You probably think I'll spend most of the post talking technical, don't you? Nope. First of all, too many tools, setups, and variations exist for me to scratch the surface. But secondly, and more importantly, a key person that I'll mention below will take the lead for you on this.

Instead, I'll focus on the human element. Or, more specifically, I will focus on the process for scaling your static analysis -- a process involving humans.

## Normalize on a Minimum Set of Core Rules/Metrics

The first thing to consider when scaling is the value proposition of scaling at all. By this, I mean that you could simply choose to allow groups at your organization to adopt organically, with no sense of standardization. In fact, you might be surprised to learn some teams have already adopted it here and there, on their own.

If you want to scale, you need to have some reason in mind. What makes it worth doing? Valid reasons often include concerns such as, "we want a minimum standard of quality" or "we want to measure some common statistics across our entire department." Sometimes you have more specific concerns, such as "we want custom checks for this type of security constraint or that type of regulatory compliance." (Though these may require customizing the analysis tools.)

Whatever your exact motivation, you have something you want common across the teams. You need to decide what, and then make it clear across the board.

## But Embrace Individual Team Norms

To realize the value proposition of scale you need the common rules or properties. But to avoid burying your teams in overhead and crushing their souls, you don't want to go overboard.

With something like this, you walk a fine line. The software design/architecture field is one of endless tradeoffs and shades of gray, with little black and white to be found. Here you navigate between getting good data and compliance and not burdening teams with undue bureaucracy. Go too far and teams spend more time complying with (and gaming) endless metrics and thresholds than they do implementing the business value brought by your software.

If you collect your paycheck from a seriously large organization, you know how mindless bureaucracy creeps into all facets of your day to day. You fight a constant battle against that. Don't let the static analysis tool become part of that battle. This tool should empower the team, which means that you should let them create their own norms and preferences around it.

## Have a Resident Expert or CoE

So far, I've established some boundaries on the philosophical rollout, but without nuts and bolts about who and how. Well, as I mentioned earlier, I do not plan to speak much to how. But now I will speak about who.

You need to find someone to own the company's static analysis practice. Depending on size and scope of the rollout, you might tap one person for this part time, or you may need a dedicated, full time team (which some organizations call a "Center of Excellence" or CoE). As you work with the people that understand the tech (or you get to understand it yourself), you'll start to get a better grasp on the personnel demands.

But whatever those may be, you need dedicated effort. These folks will own the rollout and maintenance and become experts in the tooling. _They_ are the ones that will come to understand the details of "how."

I mention this because organizations will often shift the burden to the teams. This tends to fail because no vehicle exists for dispute resolution and because no one has accountability when it slips through the cracks. Take this approach, and you'll have committees, bickering, and endless unproductive meetings. Someone needs to own this thing.

## Have Evangelists

But having an owner does not guarantee you organizational buy-in. In fact, you might wind up with the technical equivalent of Atilla the Hun going around and browbeating people about compliance. If so, you will wind up with hordes of developers that hate static analysis tooling.

You need _evangelists_ to win them over. These evangelists may be members of your CoE, but they may simply be fans and early adopters from the broader organization. Find enthusiastic volunteers, bring them into the fold, and then work with them on messaging about the tooling.

And regarding the messaging, you want something earnest. You don't want to come up with some power point that talks about "best of breed" or other things that will make developers quietly sneer behind the safe anonymity of some WebEx. You need to work out messaging as to how this genuinely helps individuals and teams. And, if you _can't_ work out that messaging, you're doing something wrong. After all, that's the entire point. So in that case, go back to the drawing board with your implementation until you find reasons that it helps the teams deliver better software more efficiently.

## Iterate

I'll wrap with one last, simple piece of advice. Don't expect to get everything right out of the gate. Just as you started small with a single team, start the full-scale rollout small with a few simple rules. Add, refine, and tweak from there as needed.

Simply by giving your organization access to static analysis and its insights, you're giving yourself a competitive advantage. So focus on getting that going first, and then build on that win as you go.

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
