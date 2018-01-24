# Agile Framework Comparison: Scrum vs Kanban vs Lean vs XP

_Captured: 2017-11-29 at 18:22 from [dzone.com](https://dzone.com/articles/agile-framework-comparison-scrum-vs-kanban-vs-lean?edition=339091&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202017-11-29)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

If you are new to Agile, it may hard to wrap your head around the concept. That is because Agile is just a set of [abstract principles](http://agilemanifesto.org/principles.html) that are void of any particularities on how to turn them to life. Hence, there are all sorts of practice-oriented frameworks, the most popular among which are Scrum, Kanban, Lean, and XP.

While this is a comparison post, analyzing these frameworks is still a bit like contrasting apples with oranges, because some of these methods piggy-back on or complement one another (especially when they apply to different parts of the development lifecycle).

## Scrum

Scrum could be called **the** framework for Agile software development. Once, I met with colleagues from a previous job and told them that we were "doing Agile" at my new job. The first thing I got asked was, "Oh, so are you doing Daily Scrum and stuff?" In many people's view, Scrum is synonymous with Agile.

**Scrum is, first and foremost, a managerial framework**. It's about things developers do when they're not writing code. Scrum explicitly prescribes a model, according to which developers plan their work, update their plans, and analyze how things went in retrospect. The framework introduces the role of Scrum Master, a dedicated person whose task is to facilitate the process and make sure it's being followed.

### Artifacts

The main Scrum "artifacts" (information disseminators) are:

  1. _User Story_. A small piece of functionality that the team is going to work on during a time-boxed period known as Sprint. The usual format is: _As a [user role], I want [the system to do this and that], so that [such and such business value is delivered]_. It must have a "Definition of Done" that will be used to determine if the story has been implemented properly.
  2. _Task_. It can be related or unrelated to a User Story. For example, setting up a new development environment or investigating a CPU memory issue are tasks that are unrelated to User Stories.
  3. _Backlog_. A list of User Stories and Tasks for future Sprints.
  4. _Sprint backlog_. A list of User Stories and Tasks (aka "work items") picked from Backlog for the current Sprint.
  5. _Product increment_. A potentially shippable piece of functionality delivered at the end of the Sprint.
  6. _Extensions_. Reports like Burndown Chart, Velocity, etc. used to keep track of the team's progress.
![Scrum process workflow infographic](https://www.objectstyle.com/f/blog_posts/Scrum-workflow.png)

### Roles

  1. _Development Team_. It includes developers, QA engineers, UI/UX designers, business analysts, and anyone else you need to deliver the new functionality. Scrum teams normally have three to nine members. When nine people is not enough, the team is split into two.
  2. _Scrum Master._ They host Daily Scrum meetings, planning/grooming/retrospective meetings, and help team members solve communication issues. Scrum Master is not a team member, so they can work with several teams at once.
  3. _Product Owner_. A stakeholders' representative who communicates the vision (which serves as a basis for User Stories) to the Scrum team, prioritizes User Stories and accepts/rejects them at the end of each Sprint.

### Values

  1. Commitment (to goals in the Sprint).
  2. Courage (to do what you think is right).
  3. Focus (on the work items in the current Sprint).
  4. Openness (about any challenges you face).
  5. Respect (trust that everyone is doing their best).

## Kanban

The Kanban framework was invented by a Toyota engineer Taiichi Ohno. In the late 1940s, Toyota representatives observed how supermarkets restock their goods based on what's been picked off the shelves. This led Toyota to create a supply system where production plans would be driven by actual consumption.

One of the key ideas of Kanban is to **refrain from producing a surplus**. Kanban achieves this by using [Kanban cards](https://en.wikipedia.org/wiki/Kanban#Kanban_.28cards.29) and a Kanban board to visualize how resources move through the production cycle. This gives everyone involved maximum insight into the process and helps managers address surplus/shortage in real time.

The Kanban system also introduces the notion of "pull" over "push," meaning that workers pull in work according to their capacity, as opposed to work being fed to them on a conveyor belt or in the form of a to-do list.

In software engineering, Kanban means there's a limit on the amount of work one can have in progress at a time. In other words, there could be a cap on the number of cards the team can have inside the "In Progress" column on the Kanban Board. This is done to increase focus and decrease context switching.

Another aspect of Kanban development is that activities are always tied to customer needs and that there is ongoing communication with the customer. Nothing is produced unless it economically benefits the customer.

### Principles

  1. Focus - reduce multitasking.
  2. Decrease waste.
  3. Customer needs come first (i.e. their business needs - ROI).
![Kanban development process workflow infographic](https://www.objectstyle.com/f/blog_posts/Kanban-workflow.png)

### Practices

  1. Visualization.
  2. Limiting work in progress.
  3. Flow management (can be done either by managing queues or by limiting work in progress).
  4. Making policies explicit.
  5. Using feedback loops.
  6. Experimental evolution.

The key difference between Kanban and Scrum is that Kanban is continuous, while Scrum is iterative. Kanban is better suited for teams that have a lot of unplanned work coming up (support issues, emergency fixes, urgent feature requests) during the Sprint. This way, instead of waiting until the end of the Sprint, the team can start working on items as they appear and re-prioritize tasks on the fly.

## Lean Software Development

To help you understand the essence of this approach, it's best to tell you the story of its author Mary Poppendieck. In the '80s, Mary found herself in a predicament. She was an IT manager at a large videotape plant where scheduling was done using the then-popular MRP software. The plant was in a precarious economic situation because their competitors from Japan were making higher-quality video cassettes faster and cheaper.

This had gotten Mary Poppendieck to consider adopting the "just-in-time" approach used by their competitor. Armed with a poorly-translated copy of the book written by a Toyota manager, Mary got down to work. As a result, almost immediately upon making the changes, the plant went from producing 60% of planned weekly pack-out to [producing 95% of it](https://www.youtube.com/watch?v=ypEMdjslEOI&feature=youtu.be&t=39m29s).

The tremendous success Mary Poppendieck experienced with the plant and in her further career lead her to write [Lean Software Development ](https://www.amazon.com/Lean-Software-Development-Agile-Toolkit/dp/0321150783)(co-authored with her husband, Tom Poppendieck). Because Lean borrows heavily from Kanban, you'll see many similarities between the two approaches.

![Lean startup process workflow infographic](https://www.objectstyle.com/f/blog_posts/Lean-workflow.png)

**Parameter**
**Lean**
**Kanban**

Principles

  1. Eliminate waste.
  2. Amplify learning.
  3. Decide as late as possible.
  4. Deliver as fast as possible.
  5. Empower the team.
  6. Build integrity in.
  7. See the whole.

  1. Focus - reduce multitasking.
  2. Decrease waste.
  3. Customer needs come first (i.e. their business needs - ROI).

Practices

  1. Seeing waste.
  2. Value stream mapping.
  3. Set-based development.
  4. Pull systems.
  5. Queuing theory.
  6. Motivation.
  7. Measurements.
  8. TDD (also pertains to Toyota's stop-the-line philosophy of uprooting flaws early on).

  1. Visualization.
  2. Limiting work in progress.
  3. Flow management (two major ways to do it: managing queues and limiting work in process).
  4. Making policies explicit.
  5. Using feedback loops.
  6. Experimental evolution.

Just like Kanban, Lean strives to reduce waste and maximize value to the customer. Waste could be building the wrong feature, waiting/multitasking/switching, wasting time doing something that will never be used or starting anew. There's also the "pull" concept that comes from Kanban, as well as the idea that you should trust that your workers are making their best effort (i.e. have respect).

As for the differences, unlike Kanban, Lean has some prescriptions regarding engineering practices (TDD, for example). At the same time, Lean is less prescriptive on delivery time-boxes, with the team potentially being ready to deploy at any time.

Some other concepts frequently associated with Lean are the Minimal Viable Product, which is the version you release as soon as you can - often even ahead of writing any documentation - failing fast, and making binding commitments (such as main architectural decisions) as late as possible.

## XP - Extreme Programming

Extreme programming started as an experiment by Kent Beck, who was working for Chrysler at the time. The idea was to take cherry-picked programming practices to the extreme and see what happens. For instance, instead of code reviews, you do pair programming, technically reviewing code non-stop. Later, as more companies began adopting this approach, certain rigid rules started to be omitted - such as daily integration tests.

Nowadays, one can see XP practices used by teams that utilize Scrum, Kanban, and other organizational Agile methodologies to squeeze the most out of the developers' potential.

Contrary to conventional belief, XP does **not** simply equal pair programming. While pair programming is one the twelve practices used in XP (scroll down for the full list), it's not the only one there is. XP offers an algorithm for process management, too.

Another thing to note is that ideally, all XP practices should be used together, or else they won't work - because of this, critics have compared XP to "[a ring of poisonous snakes](http://www.softwarereality.com/lifecycle/xp/safety_net.jsp)" and "a house of cards," where extracting one element renders the entire process ineffective.

![XP extreme programming feedback loops infographic](https://www.objectstyle.com/f/blog_posts/XP-feedback.png)

The managerial aspects of XP have received some criticism from project managers. For instance, the customer being constantly present is considered a source of stress. Besides, having no requirements and designing the system on the fly may be very ineffective.

### Values

XP values very much correlate to those in Scrum. See the table:

**XP**
**Scrum**

1\. Communication
1\. Openness

2\. Simplicity
2\. Focus

3\. Feedback
3\. Commitment

4\. Courage
4\. Courage

5\. Respect
5\. Respect

Just like Kanban and Lean, XP also sees to it that no waste is produced, focusing on writing the code you need today instead of thinking about tomorrow, next month, etc. This is called the YAGNI (You Aren't Gonna Need It) approach. There's also the planning game that is done together with the customer.

### Practices

  1. Planning game.
  2. Test-driven development ("write unit tests first").
  3. Pair programming.
  4. Whole team (customer/actual user of the program is available for feedback).
  5. Refactoring of design improvements.
  6. Small releases.
  7. Coding standards.
  8. Collective code ownership.
  9. Simple design.
  10. System metaphor (naming things in a way that programmers, customers, and everyone else understands).
  11. Sustainable pace (no overtime).

## In Conclusion

In this post, I tried to clarify the differences between the four popular Agile methods: Scrum, Kanban, Lean, and XP. Like I wrote in the beginning, it's not always possible to pin a particular practice to just one framework, and teams often use hybrid methodologies to organize an Agile development process.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
