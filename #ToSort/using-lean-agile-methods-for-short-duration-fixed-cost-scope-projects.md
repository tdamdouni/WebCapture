# Using Lean/ Agile Methods for Short Duration Fixed-Cost/Scope Projects

_Captured: 2017-01-07 at 18:38 from [www.digite.com](http://www.digite.com/blog/applicability-of-agile-lean-kanban-methods-for-fixed-scope-fixed-budget-projects-with-short-duration/)_

![LtdWIPLogo](http://www.digite.com/blog/wp-content/uploads/2014/03/LtdWIP-150x150.png)

The Pune Chapter Meet of the Limited WIP Society was held on Mar 8, 2014. This session objective was to address challenges faced by Lean-Kanban practitioners in their projects. Participants from 4 different organizations attended this session. A couple of problems were posed by the participants ([Meetup Link](http://goo.gl/Co16zZ)) ahead of time. We decided to work on the first one for this session.

**Problem Statement:** Some projects are fixed scope, fixed budget and have relatively small duration - 3-4 months. In this case, would it make more sense to go for: a) Pure Critical chain or Microsoft project plan based date based approach b) Combination approach: Critical chain based planning followed by Kanban execution. c) Pure Kanban flow based execution approach with no date based plan for individual stories.

The team started the session by working in teams to identify what aspects of Lean/Kanban facilitate small project execution that have fixed scope, fixed budget and small duration ("+ives") and what aspects don't ("-ives").

![1](http://www.digite.com/blog/wp-content/uploads/2014/03/1.jpeg)

Next, they came to the white board, brought all their points and grouped them together. The result looked something like this!

![2](http://www.digite.com/blog/wp-content/uploads/2014/03/2.jpeg)

**Result:** The team, working independently, had identified 18 positives vs 14 negatives in adapting Lean/Kanban/Agile principles to fixed scope, fixed budget projects with a short duration That a very positive reinforcement of their suitability. Therefore, Option C was taken as the way forward for the rest of the session.

While the session started with a focus on projects with short duration, it was evident that except for a couple of points, this discussion was valid for project of fixed scope/budget, independent of any duration.

The following Positives were identified when applying Agile/Lean methods to these projects:

**Positive Contributors**

**Planning**

  * If using SCRUM, defined planning activity
  * Small Cycles
  * Estimate upfront (high level) and understand the feasibility of delivering
  * Divide into stories; complete logical business flows
  * Can help in sustainable pace

**Quality**

  * Higher Quality Delivery
  * Stable Software

**Scoping and Prioritization**

  * Early Start of mature (well defined items)
  * Focus on prioritizing - very relevant
  * Principles of Agile help; focus on blockers
  * Power visualization

**Early Feedback**

  * Still relevant
  * Demos are confidence building

**Team**

  * Team empowerment is positive
  * Collaboration
  * Encourage small team size
  * Cross functional teams

After a brief discussion on the positives, since the positives were stronger than the negatives, the focus on the remaining session was how to mitigate the negative factors in these projects.

The group decided to focus on the negative contributors. Each group was given one of the negative areas to focus on. They were asked to break up the negative contributors to the next level (identified as LI below) and identify possible resolutions for the same. Then, all teams converged and refined the possible resolutions in each of the areas. The following negative contributors were identified with a clear path to resolve them.

**Negative Contributors**

**Planning Area**

**Negative Factor:** MSP is used for Portfolio and Program PlanningResolution Approach: Lean Methods exist for Portfolio Level Planning, like Portfolio Boards. We need to educate that it a myth that Agile = No planning.

![3](http://www.digite.com/blog/wp-content/uploads/2014/03/3-300x179.jpeg)

Hence, training, education and pilot programs need to be considered as a means to bring about awareness on the importance of planning and the methods available.

Negative Factor:For such small projects, the team might have good visibility of the scope. Budget, scope and timeline for such projects are often well defined. Hence, they might be tempted to plan heavily upfront and execute based on that.**Resolution Approach:** High level planning is good and if the details are available and if everyone feels assured about it, then doing isn't a negative. Avoid detailed estimation, planning to man hour level and then getting into variance tracking. This will lead to timelines getting met at the expense of quality and work-life balance.

Negative Factor:In a very dynamic environment, MSP helps in quick impact analysis.Resolution Approach:

This is not accurate. With MSP, the defined path was cumbersome. One would find the critical path, then do all kinds of jugglery like fast tracking, crashing, etc. It was based on estimates and we all understand that estimates are dead on arrival!So, we need to move all stakeholder discussions to velocity/throughput centric discussions. To enable this to happen, a lot of training needs to happen for all stakeholders involved.

**Negative Factor:** No Dates; hence, things pile up. Project Manager does not get sense of delays; lack of timeline; project delivery date is variable.**Resolution Approach:** The obvious answers the team came up with was to have time boxes (what SCRUM does). Also, it was discussed that Kanban does not have anything against Due Dates. In fact, many Kanban team use Due Dates. The risk is that Due Dates should not construed as milestones that puts pressure to finish the job, no matter what.

**Resource Management**

**Negative Factor:** MSP helps in Resource Planning, Capacity Planning.

  * Cards pile up in the end; no flexibility to take care of scope uncertainty
  * No targets for SWP; ST is not able to plan testing
  * Sudden resource requirements that come up case disruption to the whole project

![](http://www.digite.com/blog/wp-content/uploads/2014/03/4-288x300.jpeg)

**Resolution Approach:**

  * The best way forward is to have stable teams. However, if this is not possible in a given environment, we should be able to visualize this constraint and give time to stakeholders to plan resources. The way to do this is document in this blog.
  * Another approach is to under-allocate critical resources. They are often called in to help others or take care of some critical work in the pipeline.

**Testing**

Negative Factor:One has to test repeatedly, specifically regression. Since the project duration is short, the tendency is to test at one shot in one batch.**Assumption:** Testing and development are being done by 2 different people.

**Resolution Approach:** Automation

![](http://www.digite.com/blog/wp-content/uploads/2014/03/5-300x244.jpeg)

Where automation is not practical or feasible for whatever reason, the team felt that right documentation or Knowledge Transfer to the tester can help reduce repeat testing. If the tester understands the scope of each user story well, then he can focus on the scope of that user story and in subsequent test cycles, focus on scenario based testing. In a specific environment where ST is expected to "Certify" the product quality and hence, need to re-test "all" test cases, including unit level test cases, the recommended approach is to focus on reviewing the comprehensiveness of the Unit Test Cases and Unit Test Results. That would help Dev teams get better by not taking Unit Testing lightly. By ST doing unit level testing, it makes Dev teams continue with their current practices.In cases where Dev teams are mandated to Junit testing, ST teams can seek the Junit Code Coverage data to understand the level of comprehensiveness of Unit Testing.

**Environment/ Infrastructure**

**Negative Factor:** The team identified Configuration, Sanity, Missing HFs, Connectivity, Overloading of environment as all related issues to environment, infrastructure.**Resolution Approach: **Environment/ Infrastructure planning cannot be a batch mode process. Just like capacity planning, Environment/ Infrastructure needs to be continuous process. Whenever a card gets prioritized within the backlog, all its environment and infrastructure needs can be defined on a card and put in a parallel swim lane to track them to closure (see screen shot)

![](http://www.digite.com/blog/wp-content/uploads/2014/03/6-228x300.jpeg)

  * Get people from the Infrastructure/ Environment teams involved in the Sprint planning process; if you are following the Kanban method, pull them in whenever Backlog grooming happens.
![7](http://www.digite.com/blog/wp-content/uploads/2014/03/7.jpeg)
