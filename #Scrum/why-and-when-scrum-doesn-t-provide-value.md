# Why (and When) Scrum Doesn't Provide Value

_Captured: 2016-05-22 at 13:32 from [dzone.com](https://dzone.com/articles/scrum-kanban-or-just-agile?utm_medium=feed&utm_source=feedpress.me&utm_campaign=Feed:%20dzone%2Fagile)_

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121021&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=121021&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

Before going deep in the subject, I would like to emphasize that this post is completely personal. You might agree or disagree. It's up to you. You might even have really good experiences applying these agile frameworks. Nevertheless, personally, I don't think they provide much value and let me explain why.

First things first, Kanban, Scrum aren't equal to the Agile Manifesto. They are agile software development frameworks. They suggest methodologies to apply agile principles. The [Agile Manifesto](http://agilemanifesto.org/) is simple, clean and doesn't enforce any methods. Let's recall the Agile Manifesto.

![Image title](http://www.yusufaytas.com/wp-content/uploads/2016/03/agile_software_development.jpg)

As you can see, it's up to you to how to apply the Agile Manifesto because it's open-ended. The Manifesto follows the [KISS](https://en.wikipedia.org/wiki/KISS_principle) principle; however, frameworks derived from agile principles don't follow KISS. In my experience, they can make your life even more complicated than it was before. They introduce new roles, new methods, and new discussions. From now on, I'll go through examples to highlight why I don't see much value in applying these frameworks.

**Example #1: **Planning Poker

Assumption: Estimates done through days to complete a task.

  * Why somebody else estimate my task? 
    * Amount of time spent on a task is personal 
      * One might lack some technical/domain ability
      * People work different number of hours
      * Wrong estimates can decrease one's morale
    * Team can't know every piece of software produced
  * Estimates never include disasters 
    * Stop-the-world-and-fix bugs occur occasionally
    * Refactorings

So, estimating task completion as a group doesn't provide much value and is probably a great loss of time. Planning poker might take half of the day but you can deliver a small feature or a bug in that time span. I'll admit that planning poker is a fun activity and can be useful for those who joined the team recently.

**Example #2: **Meetings

A typical scrum team has between five and nine people. In an ideal world where everyone works on the same project, a scrum team makes sense. Nonetheless, that's not the case for most of the teams I've seen. Hence, team meetings becomes problematic because there is no focus.

  * Teams are expected to carry more than one project and most probably many projects. 
    * Status updates from different projects don't catch attention.
    * One project can dominate the others.
    * Roles? Come on! They become useless in one man projects.

On the other hand, meetings can provide information exchange and general view of the team. They are needed, but probably not everyday. Most importantly, meetings focussed on individual projects are much more effective.

**Example #3: **Roles

Roles are important part of agile frameworks and they aren't easy to learn and practice. Furthermore, they are strict, so they restrict freedom of developers.

  * Learning and applying roles are costly
    * Learning each role would take at least a day
    * Deciding on who's who can be a challenge
    * Companies pay a lot for training programs
    * You don't get certified for every role even after training
  * Loss of Freedom 
    * Direct interaction to the customer is lost since we have a product owner
    * Scrum masters can be bossy

Clear roles and structure might be good for some organisations and might be a hindrance for others.

I've just gone over 3 examples; however, one might come up with many others. I think it's worth to discuss an alternative to these frameworks. Thus, I'll suggest two simple methods which you might be familiar with already. I believe these two methods follow the KISS principle.

**Method #1: **Task Board

![Image title](http://www.yusufaytas.com/wp-content/uploads/2016/03/task_board.png)

A board to visualize what's currently going on. It might be a software tool or it might be just physical post-its. There might be estimates on individual tasks.

**Method #2: **Task Priority

A task priority is weighted sum of customers becoming happy/unhappy divided by number of days to spend on a task. I'll give an example to visualize:

  * Customer#1: 2, Customer#2:3, Customer#3:90
  * Task#1 takes 2 days and Task#2 takes 3 days
  * Customer#3 wants Task#2
  * Customer#1 and Customer#2 want Task#1
  * Priority for Task#1 = (2+3)/2 = 2.5
  * Priority for Task#2 = 90/3 = 30

So, we first work on Task#2 and than Task#1. Note that bugs probably have more weight because fixing broken software is more important.

That's it. Nothing more. These two methods don't tell you or enforce you to conform certain rules. They are just focussed on delivering value and visualising status of software that's worked on. Anything more than this stuff can be specific to teams or projects.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
