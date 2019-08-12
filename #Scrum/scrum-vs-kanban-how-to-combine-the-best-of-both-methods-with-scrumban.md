# Scrum vs. Kanban: How to combine the best of both methods with Scrumban

_Captured: 2019-01-24 at 21:49 from [techbeacon.com](https://techbeacon.com/app-dev-testing/scrum-vs-kanban-how-combine-best-both-methods)_

# Scrum vs. Kanban: How to combine the best of both methods

![public://pictures/Yvette-Francino .jpg](//techbeacon.scdn7.secure.raxcdn.com/sites/default/files/styles/profile_image_sm/public/pictures/Yvette-Francino%20.jpg?itok=XZ91Por8)

[Yvette Francino](/contributors/yvette-francino), Agile Consultant, Yvette Francino, LLC 

Though scrum is by far the most popular [agile methodology](http://techbeacon.com/agility-beyond-history%E2%80%94-legacy%E2%80%94-agile-development), in recent years, many organizations have been experiencing issues with it and are moving to a Kanban model for their software development efforts. There are some valid challenges with scrum that may make Kanban a better [choice for teams](http://techbeacon.com/building-agile-team-go-fantasy-reality). However, Kanban comes with its own set of advantages and disadvantages.

Some teams are getting the best of both worlds by combining techniques from scrum and Kanban, by using either _**Scrumban**_ or their own unique methodology. I've gathered some resources that will outline the challenges of each methodology and show you a few ways to mitigate those challenges by combining scrum and Kanban in various ways.

World Quality Report 2018: The State of QA and Testing

[ GET REPORT ](https://software.microfocus.com/en-us/assets/application-delivery-management/world-quality-report-2018?utm_campaign=00134846)

## The differences between scrum and Kanban

A comparison of scrum and Kanban shows that they are similar in many ways. Both are empirical models that embrace principles of lean and agile development. Both encourage early and frequent delivery, self-organized teams, continuous improvement, high quality, and the prioritizing of requirements based on business value.

 

Scrum is much more prescriptive in nature, requiring certain components:

  * **Roles**: The [scrum master](http://techbeacon.com/how-recruit-great-scrum-master), the product owner, and the development team
  * **Artifacts**: Product backlog, sprint backlog, and product increment
  * **Time-boxed events**: The sprint, which includes sprint planning, daily standups, sprint reviews, and retrospectives

[The Scrum Guide](http://www.scrumguides.org/docs/scrumguide/v1/scrum-guide-us.pdf) gives very specific guidelines for each of these and is quite rigid in expecting team adherence, with the primary responsibility of the scrum master being to “ensure that scrum is understood and enacted.”

[Kanban](https://kanbanery.com/ebook/GettingStartedWithKanban.pdf), on the other hand, is not prescriptive at all. It has only three rules:

  1. **Visualize workflow**
  2. **Limit work in process (WIP)**
  3. **Measure and improve flow**

With so few rules, it would be quite easy to apply them to scrum. Most scrum teams already visualize workflow with the use of a task board. If teams apply WIP limits, measure flow, and improve flow through retrospectives, they could essentially apply the “rules” of Kanban to their existing scrum methodologies, though some might argue that flow is not optimized with time-boxed iterations.

_[ Webinar: [World Quality Report 2019: Focus on the Financial Services Sector_ _](https://www.brighttalk.com/webcast/8653/345220?utm_source=techbeacon&utm_medium=techbeacon&utm_campaign=WQRFin)]_

## Challenges with pure scrum

The Scrum Guide is emphatic that sprints must be time-boxed to a month or less (with two weeks being more typical) and that sprints should result in a potentially releasable product for each increment. Some teams believe that time-boxed [scrum sprints slow the team down](https://medium.com/@__tosh/why-scrum-sprints-slow-you-down-3f33dba6f583#.a1kml0j16), introducing unnecessary overhead.

Additionally, teams using scrum are asked to commit to delivering production-quality, working software at the end of each short sprint. Teams are taught that, because they are providing the estimates rather than having them handed down by management, they will be working at a sustainable pace. However, teams are pressured to have their code designed, coded, and tested and to host a demo for their stakeholders, all in a very short time frame. This pressure to deliver working, production-quality code in short increments may not be realistic and may actually cause _more_ anxiety for the team, not reduce it.

With scrum, teams commit to delivering the stories they agree upon and add to their sprint backlog. However, they may encounter issues during the sprint that they are unable to resolve, or they may get interrupted by a high-priority bug fix or another unexpected issue that prevents them from finishing the stories in their sprint backlog. Because they already committed to completion of the user stories and a demo will be expected, they may decide to cut corners or add technical debt in order to meet their time-boxed, imposed deadlines.

Proponents of scrum argue that the short iterations and mandatory retrospectives will provide the feedback needed to continuously improve both processes and the product. The time-boxed sprints, though challenging, also help provide discipline and structure. In theory, missed deadlines will help teams learn over time how to more accurately plan their sprints and not overcommit. Because the sprints are short, any failures will be accepted as opportunities to learn and improve.

## Challenges with pure Kanban

Kanban, on the other hand, provides very little structure. It's not really a methodology, but more of a technique. If you don't start out using a more disciplined approach, new teams are likely to flounder. For this reason, methodologists often recommend that new agile teams start with a more prescriptive methodology, such as scrum.

Another criticism of Kanban is that it is too linear. Since it was used first at Toyota in a manufacturing line, many people feel it’s more relevant in situations that have repeatable processes rather than complex systems like software development. Kanban is often recommended for maintenance work rather than new-feature development.

In [The Problem with Kanban](http://www.jroller.com/robwilliams/entry/the_problem_with_kanban), Rob Williams notes that his team enjoys the simplicity of a lean approach over scrum, but they still have trouble.

> “The biggest problem with Kanban is that it's designed for a world where things go through the line once (e.g. a carmaker). In software, this is almost never the case.”
> 
> —[Rob Williams](http://www.jroller.com/robwilliams/entry/the_problem_with_kanban)

Without mandated retrospectives, there is also the risk that the team will not take the time to regularly reflect and improve.  That being said, lean principles do suggest that the team regularly go through a PDCA (plan-do-check-act), and many teams practicing Kanban do carry on the practice of hosting regular retrospectives, even though they are not mandated as they are in scrum.

## Combining scrum and Kanban

Corey Ladas was the first to describe a scrum/Kanban hybrid methodology, coining the term “Scrumban.” Ladas authored the 2009 book _Scrumban: Essays on Kanban Systems for Lean Software Development_. [In one essay](http://leansoftwareengineering.com/ksse/scrum-ban/), he describes the approach, suggesting starting with scrum and then optimizing until reaching a point where the time-boxed ceremonies mandated by scrum are no longer necessary.

> “Scrum can be a useful scaffold to hold a team together while you erect a more optimized solution in place. At some point you can slough off the cocoon and allow the pull system to spread its wings and take flight.”
> 
> —[Corey Ladas](http://leansoftwareengineering.com/ksse/scrum-ban/)

However, removing time-boxed events isn't the only interpretation of Scrumban.

In the more recently released book _[The Scrumban [R]Evolution: Getting the most out of Agile, Scrum, and Lean Kanban](http://www.amazon.com/The-Scrumban-Evolution-Software-Development/dp/013408621X)_, Ajay Reddy opens with:

> “Although Scrumban has evolved as a framework over the years, it has no definitive guide or definition. In fact, as highlighted early in this book, several “authoritative” sources disagree about what Scrumban actually represents.”
> 
> —[Ajay Reddy](http://www.amazon.com/The-Scrumban-Evolution-Software-Development/dp/013408621X)

Reddy’s model, rather than mixing scrum and Kanban, is described as “a management framework that emerges when teams employ scrum as their chosen way of working and use the Kanban Method as a lens through which to view, understand, and continuously improve how they work.” Reddy’s model of Scrumban suggests time-boxed iterations when appropriate, but it also suggests specialized teams and functions along with deliberate economic prioritization.

 

In fact, many organizations have teams, such as maintenance teams or SysAdmin teams, that use Kanban without time-boxed sprints, and others, such as new-feature development teams, that use scrum _with_ time-boxed sprints. 

Large enterprise frameworks such as the [Scaled Agile Framework (SAFe) and Disciplined Agile Delivery (DAD)](http://techbeacon.com/large-scale-agile-frameworks-compared-safe-vs-dad) make use of both scrum and Kanban models, depending on the context.

## Find your starting point, then go from there

It’s not much of a surprise that agile experts disagree on the definition of Scrumban. How can there be a definitive approach to any agile methodology when one of the primary rules is to adapt the methodology for your own purposes? The important thing to remember is that teams need structure and discipline at least as a starting point before they can adapt and improve.

Though scrum is much more prescriptive than Kanban, newly formed teams typically benefit from the structure and discipline of a more defined methodology. Others who would like the structure and continuous learning provided by scrum but want more of the continuous flow provided by Kanban might benefit from a scrum/Kanban hybrid, perhaps by starting with a defined Scrumban approach.

Agile experts may have differing opinions on the specifics or terminology, but regular reflection and improvement is something they all agree is beneficial and is common to all agile methodologies. Start by understanding the underlying lean and agile concepts behind scrum and Kanban, implement a defined methodology, and regularly reflect and improve.
