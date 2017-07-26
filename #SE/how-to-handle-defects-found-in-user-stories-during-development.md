# How to handle Defects found in User Stories during Development?

_Captured: 2017-01-07 at 18:41 from [www.digite.com](http://www.digite.com/blog/how-to-handle-defects-found-in-user-stories-during-development/)_

![defect_userstory](http://www.digite.com/blog/wp-content/uploads/2016/02/defect_userstory.png)

We often hear the question - In Kanban, what should we do if a User Story in Test column is found to have a bug that needs to be fixed?

Let's say the workflow is something like this: Todo -> Development -> Test -> Release

If a User Story has completed Development and moved to Test, and a tester finds a bug, what should we do to that User Story? Is it right to leave that User Story in Test and the developer should stop their current development work to fix this Defect first? If so, does this mean that developers must be interrupted all the time to clear the bugs found in Test? Is this a better than moving the User Story that has bug back to Todo or Development phase?

A developer works on a feature - which may be modeled as a User Story or an Enhancement or a Change Request - and during its development life cycle, issues or bugs may be found during various testing stages (unit, system, integration, etc.) as well as code reviews - and these issues may be captured/ reported as Defects or Bugs or Issues.

Without getting into specific processes that different teams might follow, there are broadly two methods of modeling this on a Kanban board that teams use.

The first option one is, depending on the stage where an Issue or a Bug is reported, the User Story is moved back to the earliest Working stage (Design In-Progress or Dev in-Progress, for example) and reworked on to fix the Issue or Bug. Depending on the nature of the defect, the User Story might move all the way back to the "Ready Stage" or to an intermediate stage such as Design or Development, etc.

![Kanban - Failure Demand Option 1](http://www.digite.com/blog/wp-content/uploads/2016/02/Kanban-Failure-Demand-Option-1.png)

In this case, no separate Defect cards are logged. The User Story moves back as needed, whenever an issue or a bug is found in it.

The second option is, the User Story is 'blocked' wherever the issue or bug was reported and a new Issue or a Bug is created as a card and taken up for work at the earliest stage it needs to be taken up in (including perhaps in a completely separate swim-lane with its own workflow for fixing such issues or bugs. In the picture below, cards with the red square represent blocked user stories - which are then linked to their associated defects.

# **![Kanban - Failure Demand Option 2](http://www.digite.com/blog/wp-content/uploads/2016/02/Kanban-Failure-Demand-Option-2.png)

**

The process typically favored is the second option, since it has the following advantages -

  1. It clearly highlights and visualizes the User Stories, which are blocked due to defects being found in them.
  2. It specifically identifies and allows 'assignment' to 'failure-demand' - and enables analysis of this failure demand.
  3. It allows you to model a different workflow/ process for Issues/ Defect resolution if you wish, in a separate swim lane, which further helps the analysis of cycle time (resolution time), throughput and other metrics which might help you make SLA commitments to your customers.
  4. If your team is focused on implementing and following WIP limits, it puts pressure on developers to resolve and close open defects against their name since blocked items also occupy their WIP limit.

You do have to make sure that developers follow the process of linking (associating) Stories to their Defects/ Issues (which a Kanban**[ software such as SwiftKanban**](http://www.digite.com/swiftkanban/) enables fairly easily) and also to unblock the User Story when the Defect is closed, so that the developer's WIP limit opens up for doing additional work.

How do you handle in-flight User Stories and Defects? How do you deal with the blocked User Story? Do you consider that to be part of the Developer's WIP? While a User Story is blocked, should you allow the Developer to work on some other User Story - or focus on getting this first user story unblocked and working again so there is minimal 'blockage of flow'? While you and your team may have had a specific process before you adopted Kanban, did you change your process once you adopted Kanban? Has it impacted your team's performance? It would be great if you can share your experiences here.

There is also a very nice blog post written by Kanban thought-leader Dr. Masa Maeda on a related topic you might also be interested in looking at - **[How to handle Tickets (or Defects) during Sprint Planning?](http://www.digite.com/blog/how-to-handle-tickets-during-sprint-planning/)** which deals with the planning aspect of each sprint and the inclusion of tickets (Interrupt-driven) along with User Stories (Planned).

**Mahesh Singh  
Co-founder, Sr. VP - Marketing  
**

If you liked this post, don't forget to tweet about it and share it!
