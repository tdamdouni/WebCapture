# Illegitimus Non Interruptus

_Captured: 2017-03-02 at 01:28 from [sites.google.com](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/illegitimus-non-interruptus?utm_content=buffer384fa&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

![](https://sites.google.com/a/scrumplop.org/published-patterns/_/rsrc/1485968867594/product-organization-pattern-language/illegitimus-non-interruptus/Cows_on_Selsley_Common_-_geograph.org.uk_-_192472.jpg?height=300&width=400)

> _Cows on Selsley Commons._

... the **tragedy of the commons** is a dilemma arising from the situation in which multiple individuals, acting independently and rationally consulting their own self-interest, will ultimately deplete a shared limited resource even when it is clear that it is not in anyone's long-term interest for this to happen. This dilemma was first described in an influential article titled "The Tragedy of the Commons", written by [Garrett Hardin](http://www.google.com/url?q=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FGarrett_Hardin&sa=D&sntz=1&usg=AFrqEzff4iizb8Poeb7faXb-PT3P1ZjNWA) and first published in the journal _[Science_](http://www.google.com/url?q=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FScience_%2528journal%2529&sa=D&sntz=1&usg=AFrqEzcJUfqbVDbfqgPSVU8JkNn1P6aADA) in 1968. -- _Wikipedia_

✥ ✥ ✥

**Scrum teams are often interrupted during a [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint) by changing priorities or problems in the field. Sales and marketing demands, combined with management interference, can cause chronic dysfunction in a team, repeated failure of [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint)s, failure to meet release dates, and even company failure.**

The [Scrum Team](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/scrum-team) is a critical resource for creating new software and maintaining old software. This makes them a central resource for debugging problems, technical communications with customers, marketing demos, and special projects to serve the needs of everyone in the company. See [Work Flows Inward](http://orgpatterns.wikispaces.com/WorkFlowsInward).

Often poor product ownership allows competing priorities in a company to reach a [Scrum Team](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/scrum-team). Some teams have even been bribed to work on features not in the company's [Product Backlog](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/product-backlog).

In almost all cases, it is desirable to have the [Scrum Team](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/scrum-team) "eat their own dog food." If they produce a defect that gets into the field they need to fix it as soon as possible. Setting up special maintenance teams to fix bugs incentivizes the [Scrum Team](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/scrum-team) to produce sloppy code with more bugs.

For these, and many other reasons, a [Scrum Team](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/scrum-team) is always exposed to interrupts that disrupt production.

**_Therefore:_**

**Explicitly allot time for interrupts and do not allow the time to be exceeded.**

Set up three simple rules that will cause the company to self-organize to avoid disrupting production.

This strategy will help the team re-plan during the [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint) to raise the chances of delivering the complete [Product Increment](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/regular-product-increment).

  1. The team creates a buffer for unexpected items based on historical data. For example, 30% of the team's work on the average is caused by unplanned work coming into the [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint) unexpectedly. If the team velocity averages 60 points, 20 points will be reserved for the interrupt buffer.
  2. All requests must go through the [Product Owner](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/product-owner) for triage. The [Product Owner](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/product-owner) will give some items low priority if there is no perceived value relative to the business plan. Many other items will be pushed to subsequent [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint)s even if they have immediate value. A few items are critical and must be done in the current [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint), so the [Product Owner](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/product-owner) puts them into the interrupt buffer.
  3. If the buffer starts to overflow, i.e. the [Product Owner](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/product-owner) puts one point more than 20 points into the [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint), the team must automatically abort, the [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint) must be re-planned, and management is notified that dates will slip.

It is essential to get management agreement on these rules and to enforce them. The [Product Owner](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/product-owner) must always be available, e.g. at least to have a [Surrogate Product Owner](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/surrogate-product-owner).

The [Product Owner](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/product-owner) balances the buffer size to balance short term customer satisfaction with future revenue generation. Often, a [Product Owner](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/product-owner) has third party metrics on customer satisfaction that he can adjust up or down with buffer size.

This strategy is independent of the focus on fixing all bugs that arise in the [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint) from backlog items worked on during the [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint). It is also independent of bugs assigned to a [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint) by the [Product Owner](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/product-owner) as part of [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint) planning to reduce technical debt. Low defect tolerance increases velocity in general, but exceeding the buffer typically generates at least a 50% reduction in velocity. Common sense must be used to balance these forces. See [Whack the Mole](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/whack-the-mole).

✥ ✥ ✥

These rules will invariably cause individuals to self-organize to avoid blowing up a [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint), as no individual wants to be seen as the direct cause of [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint) failure.

Even better, the buffer will tend to never be full, allowing the team to finish early and pull forward from the backlog and/or work on removing impediments. This is important because [Teams that Finish Early Accelerate Faster](https://sites.google.com/a/scrumplop.org/published-patterns/retrospective-pattern-language/teams-that-finish-early-accelerate-faster).

Counter-intuitively, this does not cause critical problems to be hidden or unresolved, The [Product Owner](https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/product-owner) will put any critical items on the [Product Backlog](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/product-backlog). The team will typically double velocity and get twice as much done in future [Sprint](https://sites.google.com/a/scrumplop.org/published-patterns/value-stream/sprint)s. This typically allows more than enough time to address critical items and often have spare capacity.

Picture from: Sharon Loxton, June 2006, [Geograph.co.uk](http://www.geograph.org.uk/photo/192472) (under CC BY-SA 2.0 license)
