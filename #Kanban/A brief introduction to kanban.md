# A brief introduction to kanban

_Captured: 2016-06-12 at 01:58 from [www.atlassian.com](https://www.atlassian.com/agile/kanban)_

Kanban is another framework used to implement agile. Back in the 1940s, Toyota optimized its engineering process by modeling it after how supermarkets stock shelves. Supermarkets stock just enough product to meet consumer demand, a practice that optimizes the flow between the supermarket and the consumer. Because inventory levels match with consumption patterns, the supermarket gains significant efficiency in inventory management and optimizing for the customer. When Toyota brought that idea to its factory floors, teams (such as the team that attaches the doors to the car's frame) would deliver a card, or "kanban", to each other (say, to the team that assembles the doors) to signal that they have excess capacity and are ready to pull more materials. Although the signaling technology has evolved, this system is still at the core of "just in time" manufacturing today.

Kanban does the same for software teams. By matching the amount of [work in progress](https://www.atlassian.com/agile/wip-limits) to the team's capacity, kanban gives teams more flexible planning options, faster output, clear focus, and transparency throughout the development cycle.

### Flexibility in planning 

A kanban team is only focused on the work that's actively in progress. Once the team completes a work item, they pluck the next work item off the top of the [backlog](https://www.atlassian.com/agile/backlogs). The [product owner](https://www.atlassian.com/agile/product-management) is free to re-prioritize work in the backlog without disrupting the team, because any changes outside the current work items don't impact the team. As long as the product owner keeps the most important work items on top of the backlog, the development team is assured they are delivering maximum value back to the business. So there's no need for the fixed-length iterations you find in scrum.

**ProTip: **Savvy product owners always engage the development team when considering changes to the backlog. For example, if user stories 1-6 are in the backlog, user story 6's [estimate](https://www.atlassian.com/agile/estimation) may be based on the completion of user stories 1-5. it's always a good practice to confirm changes with the engineering team to ensure there are no surprises.

### Minimizing cycle time

Cycle time is a key [metric](https://www.atlassian.com/agile/metrics) for kanban teams. Cycle time is the amount of time it takes for a unit of work to travel through the team's workflow-from the moment work starts to the moment it ships. By optimizing cycle time, the team confidently forecast the delivery of future work.

Overlapping skill sets lead to smaller cycle times. When only one person holds a skill set, that person becomes a bottleneck in the workflow. So teams employ basic best practices like code review and mentoring help to spread knowledge. Shared skills mean that team members can take on heterogeneous work, which further optimizes cycle time. It also means that if there is a backup of work, the entire team can swarm on it to get the process flowing smoothly again. For instance, testing isn't only done by QA engineers. Developers pitch in too!

In a kanban framework, it's the entire team's responsibility to ensure work is moving smoothly through the process.

### Efficiency through focus

Multitasking kills efficiency. The more work items in flight at any given time, the more context switching, which hinders their path to completion. That's why a key tenant of kanban is to limit the amount of work in progress (WIP). Work-in-progress limits highlight bottlenecks and backups in the team's process due to lack of focus, people, or skill sets.

For example, a typical software team might have four [workflow](https://www.atlassian.com/agile/workflow) states: to do, in progress, code review, and done. They could choose to set a WIP limit of 2 for the code review state. That might seem like a low limit, but there's good reason for it: code that hasn't been reviewed not only hasn't shipped yet, but may need significant re-work before it is ready to ship. So it's important to take action on code reviews right away, and setting a WIP limit helps the team hold themselves accountable to that. It forces the team to knock out those reviews before pulling in new work.

![A key tenant of kanban software development is to limit the amount of work in progress \(WIP\).](https://www.atlassian.com/wac/agile/kanban/sectionWrap/00/column/00/moreContent/03/imageBinary/agile_kanban_board.png)

### Making metrics visual

One of kanban's core values is continuous improvement. But how do teams ensure they're continuing to improve? One word: visuals. When the team can see data, it's easier to spot bottlenecks in the process (and remove them!). Two common reports kanban teams use are control charts and cumulative flow diagrams.

A control chart shows the cycle time for each issue as well as a rolling average for the team.

**ProTip: **The team's goal is to reduce the amount of time an issue takes to move through the entire process. Seeing the average cycle time drop in the control chart is an indicator of success.

![A control chart shows the cycle time for each issue in kanban agile development. ](https://www.atlassian.com/wac/agile/kanban/sectionWrap/00/column/00/moreContent/06/imageBinary/agile_control_chart.svg)

A cumulative flow diagram shows the number of issues in each state. The team can easily spot blockages by seeing the number of issues increase in any given state. We can see in the chart below the amount of code waiting to be merged (red) significantly increases over time. This creates a bottleneck that denies the customer of features and fixes that have already built, and increases the likelihood of massive integration conflicts when the work does get merged upstream.

![A cumulative flow diagram shows the number of issues in each state in kanban agile development. ](https://www.atlassian.com/wac/agile/kanban/sectionWrap/00/column/00/moreContent/08/imageBinary/cumulative_flow_diagram.svg)

In the example above, the team realizes the backup just before 1 September and quickly swarms to bring the amount of un-merged code back down to an acceptable level.

### Moving toward continuous delivery

We know that [continuous integration](https://www.atlassian.com/agile/continuous-integration)-the practice of building and validating code incrementally throughout the day-is essential for maintaining quality. Now let's meet CI's older, more sophisticated cousin: continuous delivery (CD). This is the practice of releasing work to customers frequently-even daily or hourly. Kanban and CD beautifully complement each other because both techniques focus on the just-in-time (and _one_-at-a-time) delivery of value.

The faster a team can deliver innovation to market, the more competitive their product will be in the marketplace. And kanban teams focus on exactly that: optimizing the flow of work out to customers.

### Scrum vs. kanban

Kanban and [scrum](https://www.atlassian.com/agile/scrum) share some of the same concepts but have very different approaches. They should not be confused with one another.

Scrum Kanban

Cadence
Regular fixed length sprints (ie, 2 weeks)
Continuous flow

Release methodology
At the end of each sprint if approved by the product owner
Continuous delivery or at the team's discretion

Roles
Product owner, scrum master, development team
No existing roles. Some teams enlist the help of an agile coach.

Key metrics
Velocity
Cycle time

Change philosophy
Teams should strive to not make changes to the sprint forecast during the sprint. Doing so compromises learnings around estimation.
Change can happen at any time

Some teams blend the ideals of kanban and scrum into "scrumban." They take fixed length sprints and roles from scrum and the focus on work in progress limits and cycle time from kanban. For teams just starting out with agile, however, we strongly recommend choosing one methodology or the other and running with it for a while. You can always get fancy later on.
