# Myth 3: In Scrum, Releases Are Done Only at the End of the Sprint

_Captured: 2018-02-18 at 17:20 from [dzone.com](https://dzone.com/articles/myth-3-in-scrum-releases-are-done-only-at-the-end?edition=338997&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-28)_

**[Download this white paper](https://dzone.com/go?i=150025&u=https%3A%2F%2Fwww.scrum.org%2FAbout%2FAll-Articles%2FarticleType%2FArticleView%2FarticleId%2F1029%2FCharacteristics-of-a-Great-Scrum-Team%3Futm_source%3DDZone%26utm_medium%3DArticle%26utm_campaign%3DGreatScrumTeam) to learn about the ways to make a Scrum Team great, brought to you in partnership with [Scrum.org](https://dzone.com/go?i=150025&u=https%3A%2F%2Fwww.scrum.org%2FAbout%2FAll-Articles%2FarticleType%2FArticleView%2FarticleId%2F1029%2FCharacteristics-of-a-Great-Scrum-Team%3Futm_source%3DDZone%26utm_medium%3DArticle%26utm_campaign%3DGreatScrumTeam). **

_Scrum is intended as [a simple, yet sufficient framework for complex product delivery](https://guntherverheyen.com/2017/09/14/scrum-period/). Scrum is not a one-size-fits-all solution, a silver bullet or a complete methodology. Instead, Scrum provides the minimal boundaries within which teams can self-organize to solve a complex problem using an empirical approach. This simplicity is its greatest strength, but also the source of many misinterpretations and myths surrounding Scrum. In this series of posts we - your 'mythbusters' [Christiaan Verwijs](https://www.linkedin.com/in/christiaanverwijs/) and [Barry Overeem](https://www.linkedin.com/in/barryovereem/) - will address the most common myths and misunderstandings. PS: The great visuals are by [Thea Schukken](https://www.linkedin.com/in/theaschukken/)._

### Myth 3: In Scrum, Releases Are Done Only at the End of the Sprint

Today we address a pretty persistent myth. The myth becomes apparent in statements like "Scrum is inflexible because new releases are only possible after the Sprint completes" or "DevOps or Kanban are better suited for us because they allow us to release faster." Either way, the core of the myth is that Scrum only allows teams to release working software at the end of a Sprint, which reduces speed and flexibility if teams are capable of doing this faster.

### Busting the Myth

This myth is an example of making a framework more important than the goal, even though it is based on a misunderstanding of the framework in this case. The purpose of the Scrum framework is to develop products and solve complex problems by using an empirical process that promotes rapid feedback. In short iterations, we use feedback (internal and external) to clarify both the problem and discover the best solution. By doing so, we avoid solving the wrong problem and/or implementing a sub-optimal solution. Given that goal, how likely is it that Scrum would force teams to deliver working software only at the end of a Sprint?

The purpose of the Sprint is to give the Development Team sufficient time to transform a selection of items from the Product Backlog [into a new, usable, "Done"-increment](http://scrumguides.org/scrum-guide.html#artifacts-increment). What constitutes "Done" varies by team, and should be defined and understood by those involved. For some teams, an increment is "Done" when the code has been written and lives on a shared branch in a code repository. For other teams, an increment is "Done" when it has been deployed to some pre-production environment (staging, Q&A, integration, etc.) or to the production environment itself.

> The completeness of the increment is defined by the amount of time that is still needed to get the increment to users (e.g. to production). 

The more time that is needed, the less Agile the organization is. After all, increments are only truly valuable when they are in the hands of users. And the quality and completeness of the feedback declines as the completeness of the Increment declines.

Having said this, the Sprint represents a _minimal_ boundary for when to deliver a "Done" increment. There is nothing in the Scrum Framework that prevents Scrum Teams from releasing working software throughout the Sprint, as long as the Product Owner is involved in the decision to release. Scrum actually encourages Scrum Teams to progressively expand the "Done"-ness of their increment to the most complete version (e.g. released to production). This optimizes the value of the empirical process that is the foundation of Scrum, as feedback becomes increasingly more applicable and realistic.

![Image title](https://dzone.com/storage/temp/7298144-myth-3-visual-750x410.png)

### Origins of the Myth

**One origin** for this myth is a misunderstanding of what constitutes an "Increment." The Scrum Guide simply defines it as [the sum](http://scrumguides.org/scrum-guide.html#artifacts-increment) of all the Product Backlog items completed during the Sprint. The increment _can _be a package of new features to be deployed in one go at the end of a Sprint. But it doesn't have to be. An increment can also be the sum of functionality that has been released during the Sprint.

**A second origin** lies in the usage of terminology like "Potentially releasable product increment" or "Potentially shippable product increment." Although not intended this way, the qualifiers can support a belief that increments are only (potentially) "shipped" or "released" at the end of a Sprint.

**A third**, and more recent, origin lies in the distinction that is sometimes made between Scrum and DevOps. Using some version of this myth, it is argued that DevOps is superior to Scrum because it allows teams to release working software faster. Because DevOps does not know the concept of a Sprint, it is argued that working software can be released whenever the team deems it "ready."

But Scrum and DevOps are close friends, both trying to implement an empirical process with a feedback cycle that is as short as possible. Where Scrum has a strong focus on the process that is needed to build what stakeholders need, DevOps deals with practices and technical enablers that make this possible. In a sense, Scrum provides a compass and a destination to travel to, while DevOps provides sturdy boots to do so without getting blisters or stepping on sharp stuff. They really are two sides of the same coin.

### What About the Sprint Review?

But what is the purpose of the Sprint Review if everything has already been released during the Sprint? If your Sprint Review only consists of a demo then, yes, the event devolves into a simple repeat of things you already know. But a demo of working software is only a small part of the Sprint Review. The [primary purpose](http://scrumguides.org/scrum-guide.html#events-review) of this event is to inspect what was done during the Sprint and to decide what next things can be done to optimize value.

> The more "Done" the increment is, the more useful the feedback that is gathered will be. 

So if the team has already released working software during the Sprint, this makes the Sprint Review an excellent opportunity to inspect feedback from real users and adapt based on the insights that emerge from that. The value of the Sprint Review actually increases as the "Definition of Done" of a team moves towards "Released to production."

### Tips

  * As a Scrum Master, **coach your team to continuously expand their Definition of Done**. More simply speaking, help the team to reduce the amount of work left to do after they consider it done (e.g. testing, quality assurance, release, documentation).

  * **Invest in learning about DevOps and its associated practices**, like automated testing, infrastructure as code, virtualization, and continuous delivery. They are critical enablers for releasing faster without compromising stability and quality.

  * If your Sprint Review is only a demo, and your team is able to release throughout the Sprint, **use the Sprint Review for its intended purpose:** to gather feedback on the delivered increment, the Product Backlog, business conditions, and promote collaboration between everyone involved.

  * With your team and within your organization, **reflect on the amount of work that needs to be done _after _a team considers an increment "done" **(e.q. QA, deployment). Help both the organization and the team to change processes and practices to decrease this amount of 'undone' work.

### Closing

In this post, we discussed the myth that Scrum Teams at best release working software at the end of a Sprint, constraining teams that are capable of releasing faster. In this post, we showed that the Scrum Framework actually encourages teams to improve their process, infrastructure, and practices to the point where releases can be done throughout the Sprint. This maximizes the quality of the feedback of the empirical process that Scrum tries to implement. We also offered a few tips to help you move towards this point.

What are your thoughts on this myth? Do you agree with this post, or not at all? Let us know in the comments.

_Want to separate Scrum from the myths? Join our_[ _Professional Scrum Master_](http://www.barryovereem.com/psm-training/)_ or_[ _Scrum Master Advanced _](http://www.barryovereem.com/scrum-master-advanced/)_courses (in Dutch or English). We guarantee a unique, eye-opening experience that is 100% free of PowerPoint, highly interactive, and serious-but-fun. Check out our public courses (Dutch) or contact us for in-house or English courses._

![Image title](https://dzone.com/storage/temp/7298156-the-mythbusters-768x477.png)

![](http://www.barryovereem.com/wp-content/uploads/The-MythBusters.png)

**[Learn more](https://dzone.com/go?i=259322&u=https%3A%2F%2Fwww.scrum.org%2Fresources%2Fconvergence-scrum-and-devops%3Futm_source%3Ddzone%26utm_medium%3Ddevops) about the myths about Scrum and DevOps. [Download the whitepaper](https://dzone.com/go?i=259322&u=https%3A%2F%2Fwww.scrum.org%2Fresources%2Fconvergence-scrum-and-devops%3Futm_source%3Ddzone%26utm_medium%3Ddevops) now brought to you in partnership with Scrum.org.**
