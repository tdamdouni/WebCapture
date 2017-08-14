# Why Yammer Believes the Traditional Engineering Organizational Structure is Dead

_Captured: 2017-07-26 at 22:57 from [firstround.com](http://firstround.com/review/Why-Yammer-believes-the-traditional-engineering-organizational-structure-is-dead/)_

[Kris Gale](https://www.linkedin.com/in/kgale), VP of Engineering at [Yammer](https://www.yammer.com/), argues the key to building fast at scale lies in small teams. He explores intricacies of organizational design in engineering and explains how making intentional decisions throughout growth ensures that you don't lose the things that are unique and special about being a startup. At the end of the day, it's your job as a CTO to think about how engineering can be organized and optimized.

**Small Teams Ship Faster**

In the early days, the Yammer team took a very heads-down approach. By focusing much more on the product itself, they didn't really consider hiring in the context of building a larger organization. As the company continued to expand, they realized that the marginal increase in productivity for every new engineer decreases over time because of greater overhead.

Simultaneously, the rest of the world recognized the fact that Yammer was doing big things. Startups were mimicking their product left and right, and even the big companies were launching products to directly compete with theirs. Yammer felt strongly that there could only be a single dominant player in the space and if they weren't nimble enough it wouldn't be them. Modern web applications need to be nimble and need to change.

Yammer employed a small teams approach in order to ship faster. But that means more than just organizing your company into small teams. If those teams are in any way restricted from shipping code into production, then they're useless. They need to be free to get stuff done outside of the larger organization.

**Specialization in Small Teams**

In the very early days of Yammer, when the team first launched a feature, they'd split it up among the three engineers by way of specialization. It wasn't terribly rigid, so if there was a ton of Rails work, Gale would still help out even though Rails wasn't his key strength. Your goal should be to create similar-styled groups, ones that are small and specialized but not rigidly siloed because different problems will demand different expertise (and you should have different experience).

**Serial Processes & Big Tech Companies**

While this approach worked really well at three engineers, as the Yammer team grew they moved to a more traditional model of engineering organizational design, one where everyone was broken up by functional expertise. So there was a back-end team, front-end team, mobile team, etc. By the end of 2010, the company was up from three engineers working on features to roughly 30. But were they ten times faster? No.

Per Amdahl's law of parallel computing, the speedup of a program using multiple processors in parallel computing is limited by the time needed for the sequential fraction of the program. For example, if you have a computation (that you can only parallelize half of), you could throw 100 processors at it and you'd only get a twofold increase in speed. If you throw another 100 processors at it, you're just going to get slightly closer to 2x. You spend a fixed amount of time in the serial half of that computation.

> People make the incorrect assumption that software engineering is writing code to a spec, but it's not. The engineering decisions you make also matter a lot -- and no one builds engineering organizations with this in mind.

If you imagine a typical medium-to-large engineering organization, you might have a front-end team, a back-end team, and potentially a "middleware" team. Those teams own their code bases, and each one has a proprietary manager, and those managers report up to some boss. The point is that the organization usually matches the code's architecture.

When it comes time to do work, the managers at the top have to make decisions about what's being built before they can break up and delegate work. You then have questions like, "What is the back-end team going to do?" and "How does that interface with the front-end team?"

Ultimately, if you've broken up work in the way described above, where the top-level managers have to divide tasks and then delegate them, you're doing it wrong. Think about it. If the individual who's actually implementing the code spots something that's wrong with the spec, he or she has to propose a change all the way up the ladder, which then has to filter back down. It's a blocking process and will bring product development to a halt. Meanwhile, the other engineers in different parts of the organization will see this as churn since they're not working closely with the engineer who proposed the change. They won't understand the rationale behind the revision itself.

At Yammer, they said screw all of that.

**Management Should Not Make Engineering Decisions**

People will always tell you to hire individuals who are better and smarter than you. If you take them up on their advice, then shouldn't you be able to trust these people to make decisions that would normally fall on you? Ultimately, it's your job as an engineering leader to build and nurture an organization. Your transition from coding to focusing exclusively on the organization probably needs to happen sooner than you think.

I don't think you should be building a product. I think you should be building an organization that builds a product.

Be very wary of only trusting managers with engineering decisions. In fact, you should delegate these all the way down to individual contributors. If managers are the only ones making decisions as you grow past 30 to 40 people, that should be a red flag.

**So how do you actually build features with this in mind?**

When Yammer builds features, they aim to improve one of their three core metrics:

On a more basic level, Yammer aims to build features that attract, retain, and sell to customers. While your core metrics might not be the same, you should definitely start with a few key goals that are communicated throughout the organization. Otherwise, you can't enable everyone at your company to make good decisions.

In a traditional organization, PMs will come up with an idea and write a spec for it. That's sort of a misnomer at Yammer. Rather than build a rigid specification of what needs to be built, a spec is viewed as a starting point for a cross-functional team to fully flesh it out. If there's too much text or too much already prescribed, be wary. You should want your engineers who are involved to understand the decisions that went into the feature so they can implement the code in the most efficient and effective way possible.

**The Two & Ten Rule**

Yammer's biggest rule of thumb is two to ten people, two to ten weeks -- which means they generally don't do projects that are larger or more complicated. There is a non-linear relationship between the complexity of a project and the wrap-up integration phase at the end. If you go anywhere beyond ten weeks, the percentage of time in the wrap-up phase becomes disproportionate.

If you employ the two to ten rule, it'll also force you to release often, test your assumptions, and not over-invest in mistakes. It's sort of the lean startup mentality, and if you're going to try and do that, you have to codify it in your organization.

You must develop a sense of urgency. Often very long projects cause engineers to lose track of the end goal. Think of it in terms of hiking. You start off feeling really fresh, you're super excited about the hike ahead and you're moving quickly. As you make progress though, your body starts to get tired and you can't see where you began or where you're going. If you're at that point, it takes a lot of mental will to force yourself to keep moving. Unfortunately, a lot of organizations have put engineers in that middle phase for the majority of their jobs.

But, near the end, you can start to make out the end of your trail and you get excited. Every step you take is clearly moving toward bringing the goal closer to you. It's important to keep your engineers in this state, one where they can measure progress and see it visually. It's the only way to maintain urgency and morale.

**Code Ownership**

Beware of creating code ownership -- designing your organization in such a way where people own code bases can create a lot of perverse incentives that you'll want to avoid. At Yammer, organization is broken into areas of expertise. Ultimately, engineers are really smart and self-motivated and if you get them aligned with your business's goals they'll do amazing things (even autonomously).

**Determine What a Team That Actually Does Work Looks Like**

Before Yammer puts together a product team around a feature, they examine a spec in closer detail. Specifically, they try and estimate the amount of effort that needs to go into a given feature.

**Take Product X.** It's an imaginary feature that's going to increase virality by providing a way to invite your friends during the signup flow. In this particular example, it's fair to say that it's front-end heavy so you might need two UI people. And since you'd probably need to change some of the sign-up flow, you'll need someone from your Rails team to code these new endpoints.

Once your product team agrees on a priority for the project, all that's left is waiting for the engineers (in this case two front-end and a Rails guy) to free up. At Yammer, they actually have a big physical whiteboard called the "Big Board" that has a sweeping grid overlay. On one side the board lists the projects; on another, there's a list of all of the engineers who work on features. There's an obvious physical constraint where an engineer can only be assigned to one project at a time. The big board also helps to provide transparency about priorities. Every single engineering development resource is accounted for, and at any point the CEO can walk by and say, "Oh, so _this_ is what engineering is doing."

If you're able to guarantee complete focus on a single project, it will speed up your company's velocity in a big way. While everybody knows how expensive context switching is, it's staggering that nobody builds that into their organization as a constraint. With total focus, you build one thing, ship it, and then are able to move onto something else.

**But Then Who's Left to Fix the Bugs?**

With everyone working on features, who's available to handle bug squashing? At Yammer they just build more cross-functional teams to handle this responsibility. They take a few people from the Rails team, the front-end team, the mobile team, etc. and say, "Your job is to handle all the incoming bugs and work down our list." It's a temporary gig (like all the project-oriented groups), and people rotate on and off of it. This organizational structure has enabled them to handle support in a way that doesn't block feature-engineering.

It also doesn't create a second class of engineers. As opposed to simply telling a bunch of junior engineers to fix a bunch of bugs, they involve the senior people too. This is very intentional: When you fix bugs, you want people to be able to fix the root of the cause, not just for a ticket to go away. Senior people should feel empowered to refactor code if necessary.

This system also creates a feedback loop between the people building features and those fixing the bugs. When people see the frequency and types of bugs, it helps to inform decisions about product engineering moving forward.
