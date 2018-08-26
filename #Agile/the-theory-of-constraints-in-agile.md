# The Theory Of Constraints In Agile

_Captured: 2018-03-20 at 18:03 from [dzone.com](https://dzone.com/articles/the-theory-of-constraints-in-agile?edition=368209&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202018-03-20)_

See why over 50,000 companies trust Jira Software to plan, track, release, and report great software faster than ever before. [Try the #1 software development tool](https://dzone.com/go?i=281431&u=https%3A%2F%2Fwww.atlassian.com%2Fsoftware%2Fjira%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Djira_adexp-psa-exp_global-eng_dzone-pre-post-roll-text%26utm_term%3DTry-the-number-one-software-development) used by agile teams.

![Image title](https://dzone.com/storage/temp/8401454-screen-shot-2018-03-07-at-100729-pm.png)

According to the Theory of Constraints from Eliyahu M. Goldratt, organizations are prevented from achieving their goals because of one or more constraints. The constraint in Agile, or any kind of software product development, might be some team or individual in the value stream that produces working-tested-remediated features (i.e. the production of value). Or, the constraint could be product quality-as in poor quality hinders sales.

The theory puts forth a process--the five focusing steps--for breaking the constraint.

> Breaking the constraint means to continuously improve the system such that the current constraint is protected or improved such that it is no longer a constraint.

Then you should repeat the process for the next constraint.

The Theory of Constraints has been applied to a wide array of industries including manufacturing, operations, supply chain, finance, project management, and even marketing and sales. Now, let's examine the 5 focusing steps, particularly through the lens of IT, Agile, and software product development.

### **Step One: Identify the Constraint(s)**

On the surface, this first step seems pretty straightforward. It's easy for Lean and Agile proponents to identify anti-patterns and poor practices and go "full tilt" at solving them. Improving the _system_ is a good thing...but improving every problem we see wouldn't necessarily improve the _system_. I'll write another post discussing whether it's fruitful to improve something that is _not _a constraint.

Agile proponents in IT often focus too much on the system of delivery and not enough on the business problem. For some great ideas on how to focus on that, refer to this podcast [about empathy maps,](https://www.leadingagile.com/podcast/creating-empathy%E2%80%A6-scott-sehlhorst/) or this podcast [about using personas to reduce risk](https://www.leadingagile.com/podcast/using-personas-r%E2%80%A6-scott-sehlhorst/), or this post by Chris Spagnuolo [about product vision tools](https://www.leadingagile.com/2014/03/product-vision-tools/).

Nevertheless, suppose you think your constraint is production and you've identified a bottleneck team. But then you realize you can also reduce headcount by making other (non-bottleneck) teams more efficient, and doing so would contribute to your goal of increasing profit. What you've identified is a second constraint. Follow these steps for each constraint.

Suppose that you further realize that product quality is limiting sales. In that case, you've identified yet another constraint to your goal (which is profit). It's wise to work that constraint as well.

### **Step Two: Exploit the Constraint**

This second focusing step is to get everything you can out of the bottleneck. There are an endless number of ways to waste bandwidth at the constraint. I'll note just a few things to watch for:

  * Get extreme clarity in the backlog so that you don't send poor quality inputs to the bottleneck.
  * Make sure all dependencies are resolved well in advance.
  * Eliminate the required daily commute to the office-at least for teams that are the bottleneck.

Don't spoil the output of the constraint downstream, wasting bottleneck bandwidth. For example, the bottleneck team's output may need to be integrated with another team's work in order to get the business value. If that team fails to do their part, you've wasted energy at the bottleneck. Or if you delay getting the output to production, or flub the marketing or sales process, you may miss a customer and waste the bottleneck's efforts.

> Don't have the constraint spend time doing work that others can do.

This may require a thorough examination of everything the constraint does. Assign other people to handle support activities, documentation, testing, estimating, status meetings, etc. Consider offloading personal business such as picking up the dry cleaning, shopping for a spouse's birthday present, picking up the kids from school or daycare, and picking up lunch or even dinner. I'm serious about this. That's likely much cheaper than adding additional people with skills that can alleviate the bottleneck.

The limitation at the constraint may just happen to be the number of communication paths in the system. Too many paths may be slowing down production. There are likely rules or procedures put in place to accommodate having so many people: code reviews by certain people, approval steps, written-over-verbal communication, branch and merge strategy, etc. These are forms of inertia that we'll warn against in the last step. Adding people reinforces those rules. Reduce the number of people involved with the constraint, and reduce rules that hinder the constraint.

### **Step Three: Subordinate Everything to the Constraint**

All other decisions should support how we have decided to manage the constraint(s). I alluded to this above when I mentioned reassigning work to other people. You should also ensure that everyone knows where the bottleneck is and that they are to drop anything they're doing if the bottleneck needs their assistance.

Ensure that the bottleneck never has to wait for a specialist's assistance. This can be done by allocating a specialist to the team, locating the specialist physically close to the team, make working agreements explicit (ex: "between 7am and 7pm, drop everything when the bottleneck team calls..."), re-architect the code or the process to remove the need for a specialist, etc.

This also means you should subordinate many of management's needs (habits) to the constraint, such as going to status meetings and submitting reports.

> Other teams don't need to be made to produce more. Quality of each team has to be just barely sufficient so as to not waste energy at the bottleneck.

Finally, leave [slack](https://www.leadingagile.com/2017/01/slack-agile-managers-role/) in non-bottleneck activities. One reason is so they can handle unplanned work. You don't want anyone upstream from the bottleneck to find themselves too busy and starve the bottleneck or break a commitment to the bottleneck team. Also, a heavily utilized system can inadvertently cause more work to flow through the bottleneck, or strain teams that the bottleneck depends on.

Efficiency is expendable in non-bottleneck activities.

### **Step Four: Elevate the Constraint**

The other things we've discussed are about improving throughput through the system by getting the most out of the constraint as it is. Elevate the constraint means to improve the constraint--to improve the throughput at the constraint by improving the constraint itself. It's the most expensive option and usually has a lag before the benefit arrives. This is why it's one of the later focusing steps.

There are many ways to elevate the constraint, and adding more people is probably the last option you should consider.

**Some better options are: **

  * Provide training
  * Improve tooling and automation
  * Procure faster workstations, etc.

All of these things impact the constraint directly, and negatively in the short run. Therefore, also invest in team building, team effectiveness, recognition, and things that make people feel good about their team and their employer.

Adding people tends to reduce the capability, efficiency, capacity, and throughput of the constraint in the short term due to the learning curve, time spent teaching and orienting, and time spent setting up new workstations instead of producing. Even worse is the burden of intercommunication. And, according to Brooks' Law, [adding people increases the coordination required](https://www.leadingagile.com/2018/02/applying-brooks-law/).

### **Step Five: Don't Let Inertia Cause a Constraint**

Repeat the process but, don't let inertia cause a constraint_._ Goldratt explains: "We cannot overemphasize this warning. What usually happens is that within our organization, we derive from the existence of the current constraints many rules. Sometimes formally, many times just intuitively. When a constraint is broken, it appears that we don't bother to go back and review those rules. As a result, our systems today are limited mainly by policy constraints."

There you have it. The Theory of Constraints as applied to Agile software product development.

Here's some more information on [Brooks' Law.](https://en.wikipedia.org/wiki/Brooks%27s_law) And, if you're interested, you can check out the book written by Fred Brooks himself. His book is called _[The Mythical Man Month_](https://www.amazon.com/Mythical-Man-Month-Software-Engineering-Anniversary/dp/0201835959/ref=sr_1_1?ie=UTF8&qid=1518099151&sr=8-1&keywords=mythical+man-month). Lastly, here's how to get more reading material written by [Goldratt](https://www.amazon.com/Eliyahu-M.-Goldratt/e/B000APWH4C).

See why over 50,000 companies trust Jira Software to plan, track, release, and report great software faster than ever before. [Try the #1 software development tool](https://dzone.com/go?i=281432&u=https%3A%2F%2Fwww.atlassian.com%2Fsoftware%2Fjira%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Djira_adexp-psa-exp_global-eng_dzone-pre-post-roll-text%26utm_term%3DTry-the-number-one-software-development) used by agile teams.
