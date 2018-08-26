# Promoting Decentralized Governance

_Captured: 2018-04-03 at 18:43 from [dzone.com](https://dzone.com/articles/promote-decentralized-governance-via-clean-archite?edition=371203&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202018-04-03)_

###  A combination of autonomous and self-directed team leadership can achieve five essential goals of production without a central authority. 

**The Agile Zone is brought to you in partnership with [Techtown Training](https://dzone.com/go?i=275424&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddzone%26utm_medium%3Dfooter). Learn how DevOps and SAFe® can be used either separately or in unison as a way to make your organization more efficient, more effective, and more successful in our [SAFe® vs DevOps eBook](https://dzone.com/go?i=275424&u=http%3A%2F%2Fpages.aspeinc.com%2FSAFe-vs-DevOps.html%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_campaign%3Dsafe_vs_devops%26utm_content%3Debook).**

In an organization with multiple development teams, a natural concern would be to keep control of the various systems being developed.

This impulse is derived from a desire to meet the goals of the organization, which could be along the following lines:

  1. Solutions should be delivered to production as quick as possible;
  2. The systems should be able to stand the test of time;
  3. Everyone on the team can work on any system and in any area of the system;
  4. Developers can move between teams; and,
  5. Developer satisfaction

Before looking at various ways teams could work, let's flesh out some aspects of the above goals.

**Goal 1.** This Is Dependent on How the Team Is Structured and Operates.

If the team owns everything end-to-end and has automated building, testing and deploying, then this goal should allow them to get out to production at an interval of their choosing (that could be daily, biweekly, weekly etc.).

But what if the team doesn't own everything end-to-end, but is dependent on one or more teams to be finished before things can be pushed to production? In such a scenario you are only as fast as the slowest team.

This is where Conway's law plays a part, but an important point when structuring teams is whether the approach taken primarily benefits your customers or is it one that conveniently matches how your business works today.

**Goal 2.** This Depends on the Combination of Approach, Architecture, Language, Tools and Frameworks Used.

An approach that helps with an evolving system would be Domain Driven Design (although if you haven't used it before then you may find that it affects goal 1, but I would suggest that the extra effort is worth the long-term gain).

A helpful way to justify the adoption of something is to use Architecture Design Records, that the entire team can put their names to. It also provides those coming afterwards with the ideas behind why things are the way they are.

**Goal 3. **This is made easier if the entire team agrees on what is used and how, but sometimes different systems are built differently by subsets of the team. In this situation the goal can be reached by the developer's willingness to learn something new and put in the effort to become proficient at it.

**Goal 4.** This can be influenced by the guidelines (or restrictions - depending on your point of view) placed on teams with regards to the systems they are tasked to build and maintain.

**Goal 5.** A big part of developer satisfaction is the ability to have one's knowledge and experience acknowledged, encouraged and see it act as a catalyst for change.

## Why Is Decentralised Governance Important?

The team is where the systems are built, where the knowledge and experience reside. If one disregards that and stipulates from the outside or from above how things should be done, then this can be a source of demotivation and distrust.

Placing value in decentralised governance of teams is effectively handing over control to the grass roots of the systems.

But how decentralised should teams be?

## The Balancing Act of Decentralised Governance

Given the above goals, how should teams be set up and what guidance (if any) should they be given when tasked to build systems for the business?

### Fully Autonomous Teams

One way would be to let teams have full autonomy of their systems. In this case the development team has full control over what happens and how, with little to no outside influence.

This could certainly cover goals 1, 2 and 3, but what about 4 and 5?

Goals 4 and 5 could certainly be met if the team primarily contained well-experienced and multiskilled developers, but not every organisation has Apple-, Google-, or Netflix-grade developers in their teams.

What if the autonomy results in systems with poorly thought out architecture or if over time they have taken on more responsibility than intended because there was no clear boundary of what the system was intended for?

Would other developers want to move to such a team? Would they be satisfied working on such systems?

Another concern of this approach is that the organisation could become dependent on certain individuals as they were the talented/strong willed developers who helped make the choices within the team. If the team is not fully onboard with how the systems are built or how the team operates, then this can lead to certain systems only being able to be maintained by one or two developers.

### Everything is Common

Another way would be to make every team use a common approach. This would mean that every team would use the same architecture, tools, languages and frameworks.

This could certainly cover goals 1, 2, 3 and 4, but not necessarily the fifth, as there is a strong potential that developers' will feel restricted.

One could assume that since this approach potentially covers 4 out of 5 goals compared to the one above covering 3 out of 5, then this approach is surely preferable.

But goals are not equally weighted. Developer satisfaction is a major contributor to keeping your most talented developers. Should they become dissatisfied or underappreciated due to their knowledge or experience not falling within the parameters of the common approach, then the likelihood of losing them increases.

### Some Things Are Common, and Some Are Autonomous

Since there are pros and cons to both above, then maybe a preferable approach would be to combine them.

What if we let each team have autonomy for the tools, languages and framework, but they all had to follow a common clean architecture? (As mentioned previously I'd also recommend taking a Domain Driven Design approach).

How would this allow us to meet our goals:

The first two approaches were both capable of meeting goals 1, 2 and 3 so this approach would naturally be able to as well. The intention is to also meet goals 4 and 5.

**Goal 4.** With clean architecture the system is structured in such a way that what the system does is explicitly separated from how it does it. What a system does in no way involves tools or frameworks. This way a new developer coming from another team (or sub teams) would at least be familiar with what each system does, as that is how they architected their own systems.

Domain Driven Design brings structure and discipline to a team allowing them to identify the boundaries of their systems and help them evolve their systems with clear intent.

If you believe that the architecture and boundaries of your own systems are good and clearly delineate their purpose, then a similar architecture at another team is not going to put you off from joining them. On the contrary, one would appreciate that level of commonality.

How the system does it requires the developer to learn the tool, language and framework. That's not to say one is happy to learn anything that is new, but it would be likely that some teams would be using things that developers in other teams would be happy to try out.

And this is what leads to the fifth goal.

**Goal 5.** Developer satisfaction is obtained by allowing developers to apply their knowledge and experience to effect change within the team and organisation. Developers are happy to move around as acknowledgement of their skills and experience matches them with the right team.

Also, as teams have a considerable amount of autonomy then developers would have the opportunity to move around and learn something new that motivates them, while at the same time contributing their own experience to the team.

**Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=266427&u=http%3A%2F%2Fpages.techtowntraining.com%2FDevOpsRoadmapDzone_DevOpsTransformationRoadmap.html%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_campaign%3Ddevops-transformation), brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266427&u=http%3A%2F%2Fwww.techtowntraining.com%2F). **
