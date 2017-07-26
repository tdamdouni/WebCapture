# How to keep systems & teams in sync while managing requirements
How to keep systems & teams in sync while managing requirements

_Captured: 2016-12-03 at 17:15 from [flip.it
http://flip.it/5OeUo1](http://flip.it/5OeUo1
http://flip.it/5OeUo1)_

![team](https://www.getzephyr.com/sites/default/files/styles/285x212-orig/public/women-1209678_1920.jpg?itok=u4Vv2hZo)

Collaboration is key to successful software development, both between customers and the development team and within the team itself. If business and technical decision-makers aren't on the same page about what an application is required to do, you risk having to do excessive rework on software that still fails to meet your customers needs. In traditional [waterfall testing](http://www.guru99.com/what-is-sdlc-or-waterfall-model.html) and development, software developers typically concern themselves with three types of requirements, often addressed at different stages in a software project: _Business requirements_ that describe why the product is being built and identify the benefits both customers and the business will reap; _User requirements_, which describe what tasks or business processes a user will be able to perform with the product; and _Functional requirements_ that describe the specific system behaviors that must be implemented. In traditional waterfall development, functional requirements often reside in a software requirements specification (SRS) document, which is used by analysts to communicate detailed requirements information to developers, testers, and other project stakeholders.

User stories, a less formal approach, are used in agile development to help shift the focus on software projects from writing about software requirements to talking about them. User stories are short, simple descriptions of a feature told from the perspective of the person who wants the new capability, usually a user or customer of the system. User stories are often written on index cards or sticky notes, and arranged on walls or Kanban boards to facilitate planning and discussion.

![](https://www.getzephyr.com/sites/default/files/kanban%20board_0.jpg)

> _Kanban Board_

On agile projects, user stories are the smallest units of work done by a development team and usually follow this standard user-story template:

_As a {type of user}, I want {goal} so that I {receive benefit}._

Here's a simple example from a banking website application that illustrates a user story:

_As a bank customer, I want to be able to check my bank account balance in real-time so that I can see if any purchases I'm about to make will result in overdraft charges._

**If You're Not Managing Change, Change Is Managing You**

[Agile software development](https://www.getzephyr.com/resources/whitepapers/step-step-guide-scaling-agile-across-project-teams-and-departments) teams embrace change and understand that requirements will evolve throughout a project, which is why agile methodologies allow requirements to be defined iteratively in the product backlog. In the [Scrum](https://en.wikipedia.org/wiki/Scrum_\(software_development\)%20) methodology, the product backlog is an ordered list of requirements that the scrum team maintains for each product. The backlog changes as business conditions change, technology evolves, or new requirements are defined. Continuous customer involvement is necessary on agile projects since the customer must prioritize the requirements and make the final decision about which ones will be addressed in each new iteration.

On scrum projects, the Product Owner (PO) is the member of the agile team who serves as the customer proxy and is responsible for defining user stories and prioritizing items in the team's backlog. User stories are sketched out by the PO, and then the entire product team collectively determines more detailed requirements. The PO prioritizes items on the product backlog based on considerations such as business value, risk, dependencies, and date needed.

**Limitations of User Stories**

User stories are a quick and easy way to handle rapidly-changing customer requirements without the need to create more formalized software requirements documents. Since they're intended to be "conversation starters" rather than detailed specifications, they're difficult to scale to large projects with plenty of complex requirements. User stories are a good way to manage requirements on small application development projects with co-located teams of 8-10 members, but they can lead to a "Tower of Babel" effect on larger multi-team development projects where an individual user story may be open to many different interpretations.

![](https://www.getzephyr.com/sites/default/files/safe-big-board-100591734-large.idge.png)

> _Scaled Agile Framework_

Image Source: [CIO](http://www.cio.com/article/2936942/enterprise-software/introducing-the-scaled-agile-framework.html)

**Requirements Management Using Large-scale Agile Frameworks **

Luckily, effective agile requirements management is available beyond the team level using one or more of the following large-scale agile frameworks: the Scaled Agile Framework (SAFe), the Disciplined Agile Delivery (DAD), or Large Scale Scrum (LeSS).

The SAFe framework provides guidance for agile requirements management at the Team, Program, and Portfolio level. SAFe Teams typically consist of 5-9 people who work in two-week scrums using XP (Extreme Programming) methods, pulling work from the Program backlog. The length of each team's scrum is synchronized with 5-10 other SAFe teams at the Program level (the next level up), as part of an "Agile Release Train" that includes the development teams and other stakeholders. The highest level of the SAFe framework, the Portfolio level, defines ways that executives and agile leaders can use lean processes like [value streams](https://en.wikipedia.org/wiki/Value_stream_mapping) to identify and prioritize features, which can then be broken down at the Program level and scheduled on Agile Release Trains.

In his book, [Agile Software Requirements: Lean Requirements Practices for Teams, Programs, and the Enterprise (Addison-Wesley, 2011)](https://www.amazon.com/Agile-Software-Requirements-Enterprise-Development/dp/0321635841) , SAFe's Chief Methodologist, Dean Leffingwell, outlines a series of software requirements best practices that are useful for agile projects at the Team, Program and Portfolio level.

Thinking long and hard about what makes a good user story is a worthwhile effort at the Team level. Leffingwell recommends Bill Wake's **[INVEST mnemonic** ](http://xp123.com/articles/invest-in-good-stories-and-smart-tasks/)for agile software projects as a reminder of the characteristics of a good quality Product Backlog Item (or **PBI)** for short.

**The INVEST Mnemonic for Agile Software Projects**

**Letter**

**Meaning**

**Description**

**I**

**Independent**

The PBI should be self-contained, in a way that there is no inherent dependency on another PBI.

**N**

**Negotiable**

PBIs, up until they are part of an iteration, can always be changed and rewritten.

**V**

**Valuable**

A PBI must deliver value to the stakeholders.

**E**

**Estimable**

You must always be able to estimate the size of a PBI.

**S**

**Small**

PBIs should not be so big as to become impossible to plan/task/prioritize with a certain level of certainty.

**T**

**Testable**

The PBI or its related description must provide the necessary information to make test development possible.

At the Program Level in SAFe, Leffingwell outlines how larger-scale requirements management is handled via a synchronized Agile Release Train (ART). The key idea behind ART is that multiple teams are on the same train and develop User Stories (at the Team Level) that roll up into Features (at the Program Level) over five iterations [which corresponds to the classic Plan-Do-Check-Adjust (PDCA) learning cycle, with an extra "Hardening, Innovation and Planning" iteration thrown in]. This helps multiple agile teams get used to building software in iterations, and shipping it when business conditions call for it--which SAFe labels "Develop on Cadence, Deliver on Demand."

![](https://www.getzephyr.com/sites/default/files/value%20streams.png)

> _SAFe Agile Release Trains and Value streams follow the same program increment cadence_

**Differences in ****SAFe between Themes, Epics, Features, and Stories**

**Type of**

**Information**

**Description**

**Responsibility**

**Time Frame**

**and Sizing**

**Expression**

**Format**

**Testable**

Investment

Theme

_Big_, audacious,

game changing,

initiatives.

Differentiating,

and providing

competitive

advantage.

Business execu-

tives, Portfolio

management.

Span strategic planning

horizon, 12 to

18+ months.

Not sized,

controlled by

percentage

investment.

Any: text, prototype, PPT, video,

conversation.

No

Epic

Bold, impactful,

marketable

differentiators.

Portfolio management. Business

analysts, product

and solution

management,

system architects.

6 to 12 months.

Sized in points.

Almost any,

including

prototype,

mock-up, short

phrase, or vision

statement.

No

Feature

Short, descriptive,

value delivery

and benefit-

oriented state-

ment. Customer

and marketing

understandable.

Product manager

and product

owner.

Fits in an internal

release (PSI),

divide into

incremental

subfeatures as

necessary.

Sized in points.

Key phrase

or user story

voice form.

May be

elaborated with

system use cases.

Yes

Story

Small, atomic.

Fit for team and

detailed user

understanding.

Product owner and team.

Fits in a single

iteration.

Sized in story points.

User story

canonical form.

Yes

**Disciplined Agile Delivery DAD (Ambler)**

Disciplined Agile Delivery (DAD), developed by Scott Ambler and Mark Lines, is similar to SAFe in that it is built on existing lean and agile techniques. DAD's approach to requirements management is an extension of that used by the Scrum methodology. Where Scrum treats requirements like a prioritized stack called a product backlog, DAD takes a broader view of requirements to include work activities like training, bug fixes, review of other teams' products, and so forth. With the DAD approach, your [software development and release](https://www.getzephyr.com/resources/whitepapers/getting-qa-and-developers-work-together) teams have a stack of prioritized and estimated work items, including requirements, which need to be addressed. Stakeholders are responsible for prioritizing the requirements on the list, whereas developers are responsible for estimating the effort required to implement the requirements they choose to work on. The priorities of non-requirement work items are either negotiated by the team with stakeholders or are addressed as part of slack time within the schedule.

![](https://www.getzephyr.com/sites/default/files/dad.png)

> _Disciplined agile requirements change management process_

The DAD framework is designed to work across three project _phases_: Inception, Construction, and Transition. DAD's strength is in providing more guidance in the areas of architecture and design, which occur at the inception phase earlier in a project's lifecycle. It's also strong at deployment (in the transition phase) since it has explicit [DevOps testing](https://devops.com/devops-continuous-testing/) and strategies built into the framework. While DAD recognizes there is a significant risk to doing detailed modeling up front due to changing requirements, it also favors using modeling as part of brainstorming sessions, called "[model storms](http://agilemodeling.com/essays/modelStorming.htm)," on a just-in-time basis to explore details behind a requirement or to think through a design issue with stakeholders.

**Scaling Lean & Agile Development LeSS (Larman, Vodde)**

Large-scale Scrum (LeSS) , created by Craig Larman and Bas Vodde, has two frameworks that provide guidance for agile requirements management: Framework-1, designed for smaller companies (up to 10 Scrum teams, with 7 members each), and Framework-2, also referred to as LeSS Huge, designed for up to a few thousand people on one product. LeSS expands on the basic team Scrum framework by organizing several feature teams under a single Product Owner (PO). Framework-2 adds the notion of an Area PO (APO) to handle scaling in larger organizations.

Unlike traditional development, which is often organized into single-function groups such as analysis or architectural-component groups such as an User Interface group, the LeSS framework-2 organizes groups around customer requirements. It does this by adding a "requirement area" column to the Product Backlog and classifying each item into one area (see Figure-4). This allows one Product Backlog to be divided into distinct Area Backlog views (see Figure-5). Importantly, almost all of the agile teams that use the larger LeSS framework-2 are flexible enough to work on any Product Backlog item, which allows all of the teams to focus on the highest-value work.

The LeSS framework-2 is a set of several framework-1 groups (one per requirement area) that work in parallel in a common iteration. Compared to SAFe and DAD, LeSS is a more flexible and non-proscriptive agile scaling framework, which may not make it the best choice for enterprises and large-scale development projects that need more structure. Although LeSS has been described as a way do 'Scrum at scale,' "a key purpose of LeSS and the implication of its name," as [Larman recently stated](http://www.citerus.se/keeping-it-simple-at-scale-an-interview-with-craig-larman/), "is actually descaling through organizational simplification--descaling the number of roles, organizational structures, dependencies, architectural complexity, management positions, sites, and number of people."

**Keeping the Change Request Door Open**

Evolving requirements are a reality on all IT projects. The agile methodology relies on the notion of a dynamic product backlog to manage change and keep systems and teams in sync as business conditions change, technology evolves, or new requirements are defined. What distinguishes agile from traditional development is the focus on evolving the end product to a point of customer satisfaction rather than trying to get it all right up front. It's the role of the customer to prioritize requirements on the backlog and make the final decision about which ones will be addressed in each iteration.

User stories and [agile test management](https://www.getzephyr.com/products) are a great way to handle rapidly-changing customer requirements without the need to create more formalized software requirements documents but they can cause problems on larger multi-team agile development projects. Using one or more of the best practices outlined above for large-scale agile frameworks will go a long way in helping reassure your customers that the software change request door is always open and you have a process to place to manage requirements to meet your customer's business goals at any stage of the agile project lifecycle.

**Related Articles:**
