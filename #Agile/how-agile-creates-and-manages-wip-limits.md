# How Agile Creates and Manages WIP Limits

_Captured: 2017-02-21 at 01:34 from [dzone.com](https://dzone.com/articles/how-agile-creates-and-manages-wip-limits?oid=twitter&utm_content=buffer7e85c&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

As I'm writing the Agile project management book, I'm explaining how Agile creates and manages WIP (Work in Progress) Limits.

Iteration-based Agile manages WIP by estimating what you can do in an iteration. You might count points. Or, you use my preference, which is to count the (small) stories.

![](https://www.jrothman.com/wp-content/uploads/2014/12/kanban.iteration-1080x675-300x188.jpg)

If you use flow-based approaches, you use kanban. You set WIP limits for the columns on your board.

In this image, there's a limit of eight items in the Ready column, three in Dev and unit test, two in System test. The interesting question is how did this team decide on these limits?

This is a large-ish team. They have eight people aside from the PO: six developers and two testers. They decided to use a reasonable approximation for deciding on WIP limits:

  1. Take the number of people who work on a given column. That's the numerator. Here, for the Dev and unit test column, it's 6.
  2. Divide that number by 2. That gives you 3 as the WIP.

This team happens to have a policy of "No one works alone on the code," so their approximation works well. You might have a product that requires a front-end, middleware, and back-end developer for each feature. You would have a WIP limit of 2 on the Dev and unit test column because you need three people for each feature.

Now, there are only two testers on this team. How did they get to a WIP limit of 2?

The testers do not work together. They each work independently. That means they can each work on a story. They can't work on more than two stories at a time because they each take one story. This team agreed to work on stories until the story is done. There is no "Stuck" or "Waiting" column.

Every so often, the testers need help from the developers to complete a story. That's because the developers didn't realize something, or implemented something not quite right. In that case, the testers walk over to the developers and negotiate when the developer is available to help. Often, it's right away. Yes, the developers stop what they are doing, because finishing something they thought was done is more important than starting or completing something new.

If you need a Stuck or Waiting column, you might add WIP limits to that column also. Why? Because you don't want that column to turn into a purgatory/limbo column, where partly finished stories go and never emerge. You might call it Urgent, although I tend to reserve Urgent for support issues.

If you use iteration-based Agile, and you have unfinished work at the end of the iteration, consider using a kanban board so you can see where the work in piling up. You might have a problem with "Everyone takes their own story." (See [Board Tyranny in Iterations and Flow](https://www.jrothman.com/mpd/agile/2016/08/board-tyranny-in-iterations-and-flow/).)

If you have read [Visualize Your Work So You Can Say No](https://www.jrothman.com/mpd/portfolio-management/2017/02/visualize-your-work-so-you-can-say-no/), consider adding WIP limits to your board. You might have noticed I say I don't use WIP limits on my [paper board ](https://www.jrothman.com/mpd/project-management/2017/02/why-i-use-a-paper-kanban-board/)because the paper, the size of my board, limits my work in progress.

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).
