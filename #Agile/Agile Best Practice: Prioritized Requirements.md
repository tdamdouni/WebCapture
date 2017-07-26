# Agile Best Practice: Prioritized Requirements

_Captured: 2016-04-24 at 11:21 from [agilemodeling.com](http://agilemodeling.com/essays/prioritizedRequirements.htm)_

Agilists want to develop software which is both high-quality and high-value, and the easiest way to develop high-value software is to implement the highest priority requirements first. This enables them to [maximize stakeholder ROI](http://AgileModeling.com/principles.htm#MaximizeStakeholderInvestment). Because requirements change frequently you need a streamlined, flexible approach to requirements change management: In short, agilists strive to truly manage change, not to [prevent it](http://www.ambysoft.com/essays/changePrevention.html). Three versions of this practice are presented:

[Figure 1](http://agilemodeling.com/essays/prioritizedRequirements.htm) overviews the Scrum approach to managing requirements where your software development team has a stack of prioritized and estimated requirements which need to be addressed ([Scrum](http://www.implementingscrum.com/) calls this prioritized stack a "product backlog"). There are several important points to understand:

  * New requirements are prioritized by your [project stakeholders](http://AgileModeling.com/essays/activeStakeholderParticipation.htm#Stakeholders) and added to the stack in the appropriate place. 
  * Fundamentally a single person needs to be the final authority when it comes to requirement prioritization. In Scrum, and [Disciplined Agile Delivery (DAD)](http://DisciplinedAgileDelivery.com) which adopts this role from Scrum, this person is called the [product owner](http://AgileModeling.com/essays/productOwner.htm). 
  * Although there is often many project stakeholders, including end users, managers, architects, operations staff, to name a few and the product owner is responsible for representing them all. 
  * The stack/backlog is initially filled as the result of your [ requirements envisioning](http://AgileModeling.com/essays/initialRequirementsModeling.htm) efforts at the beginning of the project (in Scrum they call this "populating the backlog").
  * Each iteration (a "sprint" in [Scrum terminology](http://www.ambysoft.com/essays/scrumTerminology.html)) your team pulls an iteration's worth of work off the top of the stack and commits to implementing it by the end of the iteration. 
  * Your project stakeholders have the right to define new requirements, change their minds about existing requirements, and even reprioritize requirements as they see fit. 
  * Stakeholders are responsible for making decisions and providing information in a timely manner. On some projects a [business analyst](http://AgileModeling.com/essays/businessAnalysts.htm), often in the role of product owner, may take on this responsibility. Whoever is in this role will need to work together with the other stakeholders to ensure everyone is represented fairly, often a difficult task. 
  * The priorities of non-requirement work items are either negotiated by the team with stakeholders or are addressed as part of slack time within the schedule. Many Scrum teams are now putting more than just requirements, such as defects, on their backlogs.

**Figure 1. Scrum requirements management.**

![Product Backlog](http://AgileModeling.com/images/productBacklog.jpg)

The approach depicted in [Figure 1](http://agilemodeling.com/essays/prioritizedRequirements.htm) is fairly simplistic, a reflection of what I would consider agile construction level thinking. [Figure 2](http://agilemodeling.com/essays/prioritizedRequirements.htm) overviews a more disciplined approach which extends the approach described above to managing the work items. This approach is the default suggested by [Disciplined Agile Delivery (DAD)](http://DisciplinedAgileDelivery.com) both of which reflect the real-world realities faced by agile delivery teams. There are a few interesting improvements that you should consider:

  1. **Go beyond functional requirements**. We know that we do more than just implement new requirements each iteration, we often do non-requirement related work such as take training, review products of other teams, address defects (I believe that [defects are simply another type of requirement](http://www.ddj.com/architect/205207998?cid=Ambysoft)) and so on. The point is that more than just requirements need to be on the stack, we really need work items. 
  2. **Take a risk-value approach**. Disciplined agile teams recognize that there are common risks faced by development teams, risks which they want to address as soon as possible. Such risks include the need to come to stakeholder consensus early in the project, a risk which can be addressed through [ requirements envisioning](http://AgileModeling.com/essays/initialRequirementsModeling.htm) and perhaps the development of a shared vision or project charter. Another common risk is the need to prove that your architecture strategy, identified via [ architecture envisioning](http://AgileModeling.com/essays/initialArchitectureModeling.htm), actually works. The most effective way to do this is to [ prove your architecture with working code](http://AgileModeling.com/essays/agileArchitecture.htm#ProveIt) by building an end-to-end skeleton, or steel frame, for your system which addresses the major technological risks faced by your team. [Disciplined Agile Delivery (DAD)](http://DisciplinedAgileDelivery.com) teams will look at their work item stack early in the project, typically during the Inception/"[iteration 0](http://www.ambysoft.com/essays/agileLifecycle.html#Iteration0)"/"sprint 0" part of the project to identify requirements which exhibit these technically risky features. If these requirements aren't at the very top of the stack, and they often are because risk and reward (value) have a tendency to be co-related, then they discuss the issue with their [product owner](http://AgileModeling.com/essays/productOwner.htm) and see if they can motivate that person (who is responsible for prioritization) to move those requirements to the top of the stack too. If a high-risk requirement is currently near the bottom of the stack then you should question whether that requirement is actually needed because chances are good you'll never actually get around to working on it as higher priority work will always take precedent.
  3. **Model a bit ahead**. Because we know that all requirements, let alone work items in general, are not created equal we shouldn't naively assume that we should just wait to pull an iteration's worth of work off the top of the stack at the beginning of the iteration. What if a work item is very complex, requiring a bit more thinking that what generally occurs in iteration planning sessions? Disciplined agile teams will adopt the [ Look-Ahead Modeling](http://AgileModeling.com/essays/modelAhead.htm) practice and look an iteration or two down the work item stack and invest the time to explore complex upcoming work items to reduce their overall project risk. Modeling a bit ahead is called backlog grooming in Scrum, revealing some of the unnecessary conceptual coupling amongst practices in Scrum.
![](http://AgileModeling.com/images/requirementsManagement.gif)

[Figure 3](http://agilemodeling.com/essays/prioritizedRequirements.htm) depicts a lean approach, common on [ Kanban](http://www.amazon.com/exec/obidos/ASIN/0984521402/ambysoftinc) teams, to requirements management. There are several key differences between the agile approach to requirements/work management and the lean approach:

  * **Options**. The work items are viewed as potential options to be addressed in the solution, not as required work items. As an aside, the term "requirement" in IT has always been questionable at best (if something is a requirement then how can some or all of it be dropped from your delivery scope?) but it is a term which I fear we will never be able to abandon. 
  * **Options are managed as a pool**. Where agile teams manage work items as a prioritized queue, lean teams manage options as a pool from which they work with stakeholders to select the highest value work when they have the capacity to perform the corresponding work. In effect prioritization is done on a just in time (JIT) with the team's stakeholders. This can be complex because individual stakeholders will have different priorities, so tradeoffs will need to be made, and because there may be different classes of service being supported by the team. Of course the risk mitigation issues described by the [disciplined agile strategy](http://agilemodeling.com/essays/prioritizedRequirements.htm) should also be considerations in which option is selected next.
  * **Options are potentially organized into classes of service**. Not all options are created equal. In the book [ Kanban](http://www.amazon.com/exec/obidos/ASIN/0984521402/ambysoftinc), David J. Anderson, describes several potential categories of options (which Anderson refers to as classes of service) which your team may consider. Many work items fall into the "standard" class where their prioritization is based primarily on their business value to your organization. Some work items have a fixed delivery date, this is common for requirements resulting from government legislation or contracts signed with your external customers. You may also have a (hopefully) small number of expedited work items, such as critical fixes for production problems or high-priority customer requirements. Finally, you may have some low-priority "intangible" work items that you know you'll need to address at some point in the future that you decide to address when the team believes is appropriate (perhaps to streamline other work, to take a rest from more challenging work, ...). It is important to note that the categories described here are not carved in stone, your team may identify different ones or may not need to categorize at all. Also, classes of service could be supported in the agile strategies described above as multiple queues.
  * **The goal is to limit work in progress (WIP)**. When agile teams strive to choose a fixed amount of functionality, just enough that they can implement in a single iteration, lean teams choose to produce a continuous flow of functionality pulling work into their "delivery system" when they have the capacity to do so. Limiting WIP increases the team's delivery predictability, improves quality (due to shorter feedback cycles), and increases productivity. 
  * **Old work items are culled**. Lean teams will often strive to identify aging rules where if a work item is in the pool longer than a certain amount of time, it is removed from the pool under the assumption that if it's gone that long without being important enough to be selected from the pool then it likely never will be. If the work item does prove to be needed it can always be added to the pool at a future date. Note that the aging rules will vary between teams, perhaps three months for one team although five months for another. Also, this strategy can be applied to either the product backlog or work item list approaches described earlier.

**Figure 3. Lean work management process.**

![Lean Requirements Management](http://AgileModeling.com/images/leanRequirementsManagement.jpg)

There are several ways that options are added by stakeholders:

  * When the team is initially formed, via requirements envisioning session(s).
  * In an impromptu manner as stakeholders think of them.
  * Via purposeful modeling sessions when the options pool nears being empty.
  * As enhancement requests or defect reports identified via usage of the existing production system. 

### 4\. Which strategy is right for you?

No one strategy is best in all situations, and you will need to identify choose and then tailor the one that works best for you. [Table 1](http://agilemodeling.com/essays/prioritizedRequirements.htm) compares and contrasts the strategies.

**Table 1. Comparing the strategies.**

**Strategy**
**Advantages**
**Disadvantages**
**When to Use It**

[ Product Backlog](http://agilemodeling.com/essays/prioritizedRequirements.htm)

  * Simple

  * Overhead associated with keeping the stack prioritized as priorities change
  * Requires multiple stacks, or a more complex prioritization scheme, to support classes of service
  * Typically requires teams to have an "overhead fudge factor", sometimes upwards to 30%, to account for non-requirements work each iteration

  * Simple situations (typically co-located agile teams developing fairly straightforward software)

[Work Item List](http://agilemodeling.com/essays/prioritizedRequirements.htm)

  * Easily supports different types of work items
  * "Overhead fudge factor" required is much smaller or non-existent compared with product backlog approach

  * Overhead associated with keeping the stack prioritized as priorities change
  * Requires multiple stacks, or a more complex prioritization scheme, to support classes of service

  * For agile teams in not-so-simple situations, particularly teams in scaling situations (see [ The Software Development Context Framework (SDCF)](http://disciplinedagiledelivery.wordpress.com/2013/03/15/sdcf/) )

[ Options Collection](http://agilemodeling.com/essays/prioritizedRequirements.htm)

  * Works for both agile and non-agile teams
  * No overhead of managing a prioritized queue
  * The overhead of the "planning game" at the beginning of each iteration goes away

  * Requires stakeholders who are sophisticated enough to prioritize the work on a JIT basis

  * Lean teams (e.g. [ Kanban](http://www.amazon.com/exec/obidos/ASIN/0984521402/ambysoftinc)) will adopt a variant of this strategy
