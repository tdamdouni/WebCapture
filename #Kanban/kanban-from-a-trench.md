# Kanban from a Trench

_Captured: 2018-06-26 at 19:30 from [dzone.com](https://dzone.com/articles/kanban-from-a-trench?edition=383260&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202018-06-26)_

**The Agile Zone is brought to you in partnership with [Techtown Training](https://dzone.com/go?i=275424&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddzone%26utm_medium%3Dfooter). Learn how DevOps and SAFe® can be used either separately or in unison as a way to make your organization more efficient, more effective, and more successful in our [SAFe® vs DevOps eBook](https://dzone.com/go?i=275424&u=http%3A%2F%2Fpages.aspeinc.com%2FSAFe-vs-DevOps.html%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_campaign%3Dsafe_vs_devops%26utm_content%3Debook).**

## **Introduction**

After forming part of a software project team that got underway with a significant project at the BBC Worldwide in 2013, I felt that it would be useful to release a few notes about my experience of Kanban and how it helps to deliver good quality software to customers.

_Here are some notes that I prepared in order to deliver a Kanban motivational speech to an engineering community on a subsequent project outside of the BBC._

## **Kanban from a Trench**

Kanban is a technique for managing the software development process. It doesn't tell us how to develop software but provides techniques that help us to enforce what _we, (as a software development team), _agree is the right formula to develop acceptable quality software for our customers.

As an example, we may determine that an adequate software engineering process requires the following:

  * Well understood and agreed on requirements to be the foundation of onward development.
  * Development is sympathetic to an evolving well understood architecture that's published for the entire team to work from.
  * We practice JIT development/engineering - only do what is required when it's required.
  * A set of coherent, well planned and engineered tests are built and maintained - from unit tests to UAT.
  * Deployment and release management is actively managed through planning and coordination.
  * Feature development priority adjustments are possible in order that our agile team can respond quickly to change instigated by key stakeholders.
  * Peer review of all team assets - code, documentation, user manuals, and tests - as a minimum.
  * Feature designs are documented with light-weight descriptions and pictures - bullet points and photos of whiteboards. Sometimes, formal UML diagrams can be justified, i.e. for _state_ or _sequence_ representations.
  * The development process must evolve with the team, product, and organizational aspirations.

## **The Kanban Board**

For the Kanban projects in which I have been involved, our project board typically consists of five key areas:

  1. a team pool (a collection of names),
  2. a group of associated columns that represent our software engineering process,
  3. some streams,
  4. a set of feature tasks in various stages and
  5. a calendar of significant events.
![bk-1](http://greendotsoftware.co.uk/wp-content/uploads/2014/01/bk-1.png)

#### **1) Team Pool**

The team pool is a collection of names/avatars, each one a picture and name of a person who is available for work on tasks - each team member usually has two avatars. You can work on at least one task at a time, often we have the capacity to take on another task in parallel.

These avatars help teach us about how we work as a team. For example, if an attempt is made to assign an avatar to more than two tasks, or is very frequently switched between tasks before tasks are finished, the board is very likely telling us something that we need to understand and deal with. Maybe we have insufficient resources in the team, maybe we have knowledge concentrated in one person (exclusive knowledge). Regardless, we need to record this and if it continues to happen, take some corrective action to resolve it.

#### 2**) Group of Associated Columns**

These columns represent phases or major milestones in our software development process. Kanban does not prescribe these columns as listed here below but suggests what might be a good starting point for our team to move forward from - the process will grow and evolve with the team.

![bk-2](http://greendotsoftware.co.uk/wp-content/uploads/2014/01/bk-2.png)

As an example, the following columns were used for the BBC Worldwide project in which I was involved:

**Inventory** - A collection of features that will have a broad level description in order that it can be understood (three-point estimation only at this stage). No further detail is required right now - remember, JIT.

**Identify** - Features that we've agreed to spend some further time on. We need to understand if the feature is date driven, what the value proposition is, how to understand if the goal is achieved or not (once it's deployed we need to measure success), identify significant dependencies (other work/functions etc). Which release version/date is targeted etc.

**Analyse and Design** - During this stage we will define and refine acceptance criteria - these will be written on the card. We now need to gather sufficient requirements such that the customer will get what they want (and hopefully asked for) and we understand how to build it. We will discuss and record BDD scenarios in preparation of QA. Analysis and design will be peer reviewed with a minimum agreed number of team members who have business, technical, and architectural knowledge relevant to the feature undergoing development. If necessary, the feature will be broken down into smaller units/tasks, each consisting of work that will last (approximately) between 0.5 and 5 days. Wireframes (from the whiteboard) will be drawn, described and agreed/approved by the customer. The feature will be reviewed in terms of architecture. The general test approach will be agreed, also consider technical debt, i.e. missing tests for existing code packages. Agree on documentation of the feature, it's setup, configuration, user manual entries etc. Agree to commit to building the feature.

**Develop and QA** - Each new class, service, or technical feature must have been written, have passed tests and executable documentation where required. Automated tests will be created and triggered by schedule. Tasks will not leave this column until they have been added into 'develop' (a Git branch) and all tests green-ticked.

**Ready to Deploy** - Team agrees that they're happy for the feature to go into the next release and a demo to the customer is conducted.

One of the _key_ aspects of Kanban is** Work In Progress (WIP)** limits. Kanban tells us that it's better not to take on too much and that we should always consider finishing things in preference to starting new ones. This is often quite a challenge for teams new to Kanban because it means instead of taking on a new task, you may have to go and pair with someone that's already working on a task. We all know that pairing should be encouraged, this is one route towards that. Pairing work may be coding, testing, documentation, QA, infrastructure, etc. WIP limits are defined for each column, they may have different values depending on the team size, columns and our experience of what works. We can increase WIP limits but beware consequences such as blocking. Instead of increasing WIP limits, get work finished instead.

It's often convenient to decompose a column into two parts, one to show in-progress tasks and one to show those that have been completed but are not ready to move into the next column.

#### **3) Some streams**

It's sometimes easier to track and read the board if groups of related tasks are bunched together in a stream. If during analysing and design a feature is broken down into, e.g.saye they are related.

![bk-3](http://greendotsoftware.co.uk/wp-content/uploads/2014/01/bk-3.png)

#### **4) Feature tasks**

The focus of the Kanban board is the tasks that represent feature development. The aim is to pull tasks through the system (from the right-hand side) rather than push them in from the left.

Each task card contains a progress history. It's not unusual for cards to have extensions attached to the reverse of them, design diagrams, JIRA numbers, dependencies, dates for movement along the board.

To further aid recognition, it's quite useful to use color-coded cards such that feature work, documentation, infrastructure, and bugs can be easily recognized.

It's really important that the Kanban work board is maintained up to date, so this is something that usually takes place each morning - a stand-up. Whoever is running the stand-up will go through the tasks on the board and ask for an update from any person working on the task.

#### **5) Project Calendar**

The entire team needs to know if somebody is sick, on holiday or that a release is imminent.

## How Do We Do Maintenance?

We could consider that two classes of bug exist, those directly related to features currently being undertaken and those related to historical feature development. Bugs related to current feature development should be fixed by the feature crew/team working on it, up to and including the User Acceptance Test phase, i.e. post-deployment.

The primary difference between product feature development and historical bug fixing seems to be the stability of day-to-day work tasks and their duration - frequently changing priorities (intra-day) and generally, very short develop/test life-cycle. Ideally, we'd expect features to undergo development, in part or whole, during a period of days or weeks. Context switching is expensive so we want engineers to remain focused on the feature(s) that they're working on rather than frequently switching between features and historic bugs.

Therefore, having two project boards (or two streams on a single board), one representing core feature development and one representing bugs could suit quite well. The aspects that are different in these two regards, that need separating, are the units of work, rather than team members. Therefore, it's a sensible approach to enable team members to be available to work on both core feature development and historical bugs as work-loads and priorities dictate.

### **Existing Technical Debt**

We need to work out a mechanism that promotes, encourages and tracks necessary refactoring in order that it's well socialized, publicised and coordinated. Could we track this as a stream on the main board or use a distinct Kanban board to track it?

### **Estimation**

For Inventory tasks, three-point estimation will be used. Best case, worst case and expected. We'll use this to help drive which features to take on first given an arbitrary set of features that require development for a given release. This estimation can be further refined when breaking a task down in the Analysis and Design stages. This information will help feed into a release tracking board that represents feature dependencies and release dates.

### **Architecture**

At any stage of any feature or release, it should be possible to view an architecture diagram to use for alignment of feature development. Interesting aspects are current architecture, aspirational next step architecture and final state architecture. Of course, all three of these will move over time as the product and its environment matures.

As with all other work, an architectural conjecture will be proposed and presented to the team as part of the general review process. None of this work is hidden, it will all appear as tasks on the Kanban board.

### **Demos**

It should have been made clear from column exit criteria, but running a demo for the customer or his/her representative is a pre-requisite to a feature being added to a release.

### **GitFlow**

At what stage does software make it into 'develop', _release_ and _support_. The Kanban board needs to be well aligned with our release process, or vice-versa.

_Following a series of probing and explorative questions, the team commenced trying to understand what it would take in order to establish engineering satisfaction for software production._

## What Does the Team Consider as Adequate Product Engineering?

Collectively, the team has identified the following criteria as those that are essential to building a product of sufficient quality such that we are happy to give it to our customers.

The groupings are somewhat artificial, but give us an idea of the type and spread of areas for which we have collectively, accumulated important engineering criteria.

![Screen Shot 2014-01-02 at 16.58.05](http://greendotsoftware.co.uk/wp-content/uploads/2014/01/Screen-Shot-2014-01-02-at-16.58.05.png)

## **The Kanban Board**

The physical Kanban board will be the master copy of feature development status. We need to build and place a board in an area that's always accessible, as several team members have observed it would not be a good idea to have this located in a meeting room.

JIRA tickets will be created for the highest-level feature names but at the end of the process, i.e. when they hit the last column (I.e. UAT). Generally, we will not get bogged down in keeping JIRA up-to-date with the physical board - communication is key and that can't be replaced by an issue tracking system so let's not try.

From the previous examples, we will now define the columns that we're going to use and assign exit criteria to each of them.

## **Board Management**

Although, as a software development team collectively, we will own the process, the Kanban board needs to be actively managed along with the teams using the board. Sometimes we will require arbitration, encouragement, steering, and decisions in order to operate. If an agile coach is not available, we need to identify someone to adopt the role of coach or manager.

**Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=266427&u=http%3A%2F%2Fpages.techtowntraining.com%2FDevOpsRoadmapDzone_DevOpsTransformationRoadmap.html%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_campaign%3Ddevops-transformation), brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266427&u=http%3A%2F%2Fwww.techtowntraining.com%2F). **

Topics:

kanban ,agile approach ,agile ,kanban elements ,kanban board ,technical debt ,estimation
