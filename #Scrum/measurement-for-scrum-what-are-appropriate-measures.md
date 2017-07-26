# Measurement for Scrum – What are Appropriate Measures?

_Captured: 2017-07-08 at 09:39 from [agilepainrelief.com](https://agilepainrelief.com/notesfromatooluser/2016/09/measurement-for-scrum-what-are-appropriate-measures.html?utm_content=buffer2606d&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer#.WWCMOYWbGaO)_

We've seen the risks of assuming that everything is [normal distribution](https://agilepainrelief.com/notesfromatooluser/2016/03/bell-curves-and-measuring-badly.html), and also the problem with reporting a [single number](http://agilepainrelief.com/notesfromatooluser/2016/07/forecasting-metrics-and-the-lies-that-a-single-number-tell-us.html). What else do we need to be aware of? What can we usefully measure?

### Risks in Measurement

Many important things can't be measured using formal measurement systems. As a result, not enough attention is paid to them. For example, [Technical Debt](http://www.infoq.com/articles/technical-debt-levison) - there are some attempts to measure code complexity but they don't work well, so organizations sweep the problem under the rug until a code base becomes too complex and expensive to maintain. One of Nassim Taleb's key points is that [Black Swan](https://en.wikipedia.org/wiki/The_Black_Swan_\(Taleb_book\)) events couldn't have been predicted by mathematics before the event, however they look obvious in hindsight. Only better questions will help spot a risk in advance.

Always consider how your metric will be gamed. "Tell me how you measure me, and I will tell you how I will behave" - Eliyahu Goldratt[[1](https://agilepainrelief.com/notesfromatooluser/2016/09/measurement-for-scrum-what-are-appropriate-measures.html?utm_content=buffer2606d&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)]. People will do what it takes to meet what they believe they're being measured on, so we should only use metrics that, if gamed, we would be happy with the result. Example: if we measure Velocity (number of Story Points per Sprint), teams will rapidly find ways of inflating their Velocity (estimate higher, reduce effort on testing, etc.) in ways that produce a weaker product.

#### _People will do what it takes to meet what they believe they're being measured on._

Focus on a change or trend, and not the raw number itself. A change in a metric is just a hint to go look and see. It doesn't, in and of itself, tell us anything. For example, Unit Test code coverage (expressed as a percentage) goes down over the course of one Sprint. This may be bad - perhaps new code was introduced without accompanying Unit tests. Or it may be good - well tested code that was redundant was eliminated. So a metric is just a hint to have a conversation.

The Six Sigma[[2](https://agilepainrelief.com/notesfromatooluser/2016/09/measurement-for-scrum-what-are-appropriate-measures.html?utm_content=buffer2606d&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)] manufacturing process makes significant use of metrics to reduce defect rates by eliminating variability. But applying that same approach to software and product development would have a disastrous effect. Knowledge work, e.g. the work of building products (software or otherwise), is hard to measure because the nature of the work is inherently variable. What's the standard time to implement a feature? There is none. How long does it take to fix an average bug? There are no average bugs. When measuring, we need to be careful not to use the measure to eliminate the variability inherent to the work.

And then there's **Vanity Metrics**. Be careful of metrics that measure things that the customer doesn't value. [LeanKit](http://leankit.com/blog/2016/03/why-vanity-metrics-are-dangerous-holding-a-mirror-up-to-your-measures-of-success/) shows that focusing on 5 '9s' (99.999%) up time might cause us to put energy into solving the wrong problem. In the LeanKit example, 5 '9s' is the goal, and when customers complain about downtime, the DevOps person notices that 75% of the down time occurs when the nightly maintenance scripts are run. So they put time into improving the scripts to eliminate the problems, but the customer complaints don't go away. Yes, the complaints were about the percentage of downtime… but about downtime _during the day_! Focusing on the evening downtime misses the point. In another case, [American Airlines](http://onemileatatime.boardingarea.com/2016/03/09/customer-relations-american-airlines/) has promised a response to customer complaints within 20 minutes. However, many of the responses are clearly canned e.g. if you mention power supply problems on a particular plane, you'll get a response back that suggests that other people in your row might have been using the power, along with a link to the airlines FAQ. Instead of a useless response within 20 minutes, what the recipient really wanted was to know that maintenance had been sent a ticket for the problem.

Recheck your metrics frequently (at a minimum, every 3 months) and ask if they're still relevant. Ask if they're still helping to drive change. Drop metrics that are no longer helping.

When considering effective metrics, ask:

  * How will this measure help our customer?
  * Does this measure have a "best before" date?

How will a smart team game this metric? (And if they game it, will we be happy?)

Potential Measure What is it trying to measure? How does it help? How will it be gamed?  
Other concerns?

Defects that escape the Sprint
Quality
It sends a strong signal that zero defects is desirable.
People might argue about whether an item is a defect or just a new User  
Story.

Static Code Analysis (e.g. tools like [Sonar](http://www.sonarsource.com/) and [FindBugs](http://findbugs.sourceforge.net/), [PMD](https://pmd.github.io/))
Quality by doing static analysis
Static analysis tools can spot small mistakes in code and warn developers of potential bugs.
Static analysis can give people a false sense of security since the tools only check for bugs that can be proven by examining the code - they don't check for logic, implementation or intent errors. Tools are often used to summarize health with one or two numbers. As usual, the number is useful if it tells you to roll back the covers, but risky if you assume it means an area of your code base is safe.

Test Coverage
How much of the code is visited by automated tests (unit or acceptance tests)
It can help spot untested or even unused code.
People often assume that code visited by a test has been tested. All a test coverage tells us is the code was used by a test. It shows nothing about whether it was tested.

Customer Satisfaction measured via NPS (Net Promoter Score)
Whether the customer would be happy to recommend your product to their friends on a scale of 1-10. They're then asked why they choose that number.
Are you delighting your customers?
It can only be measured infrequently, so information arrives a long time after your work has been done. It doesn't correlate well to the product work your organization has done. The power is in the answer to the "why" question.

Team Member Happiness
Each Team rates their happiness with the Team or Organization on a scale of 1-5.
Happier people are more productive and focused. Jeff Sutherland has correlated Happiness with an increase Productivity and Revenue. When a team member's happiness dips it can be a warning sign that something we're doing is harming our organization.
Happiness can sometimes become a trap - a team's productivity plateaus and they're happy.

Cycle Time

Cycle Time
How long it takes an item to production from the moment the team starts working on it.
Work in Progress - whether it's in development, test, documentation or some other state delivers no value to the customer. Work only delivers value when the customer has it.

Lead Time
Length of time from the moment the idea is received to when it is delivered to the,customer.
Also takes into account the time an item sits waiting in a queue (Product Backlog,or otherwise before the team works on it).

Interruptions

Interruptions
How many times during the Sprint the team(s) have to deal with…
Creates awareness around the rate of interruption for the time.

Support Issues
…a support issue
Highlights either quality (product bugs) or usability issues (feature isn't used as the team intended).

Non-Product Backlog work requested
…work items that didn't come from the Product Backlog
Highlights quality work that is bypassing Product Ownership and Portfolio Management.

Other Interruptions
… interruptions that are not part of the previous categories
Highlights [Dark Work](https://agilepainrelief.com/notesfromatooluser/2015/03/kanban-portfolio-view-continued.html) and other things that are distracting the team

Dangerous Measures

Velocity
Average number of Stories or Story Points completed per Sprint
Can be [used to forecast](https://agilepainrelief.com/notesfromatooluser/2016/07/forecasting-metrics-and-the-lies-that-a-single-number-tell-us.html) when a feature will be released. It can also help a team spot long-term trends in their own work.
It is often misused to compare teams or measure productivity, which leads to a culture of velocity above all else (especially quality). If used, it should be used by only the team itself.

Bug/Defect Count
Number of Bugs logged in on the bug tracking system
A measure of quality
At best, measure defects in quality on the surface of the system. Missing:  
- Doesn't measure the internal quality of the code  
- Never complete since we will never find all the bugs  
- Stale Bugs that can be reproduced or are in parts of the system that are no longer used cloud the measure

Return on Investment
Revenue per Feature divided by Cost
Can't realistically be measured.

Productivity
Can't be measured, and if it was, it's unclear how it would help guide teams.

More Potential Measures

Ratio of Fixing Work to Feature Work
Measure very roughly the amount of time spent on fixing bugs vs new feature work. _This shouldn't require tracking hours, we want a rough ratio._
Helps us understand where effort is being spent. Helps a PO make better decisions about where they're spending their money.

How long does it take to test end to end?
How much testing would it require to have confidence in release?
Reminds us of the overhead/tax we need to pay before releasing our product on the world. _Since it's part of cycle time, we should feel pressure to reduce this from days to hours._

Release Frequency
How much time between releases?
Reducing time between releases can help us get paid more often.

Backlog change rate
How often are Product Backlog items added, removed, reprioritized, etc?
Too little and we should be concerned that we're not building the product the customer wants. Too much and we should be concerned about our ability to build a stable product.

[Skills Matrix](https://agilepainrelief.com/notesfromatooluser/2012/02/scrummaster-talesthe-team-gets-bottlenecked.html)/Team Learning
A skills matrix is a tool to help the team understand where it has a lot of knowledge and where it is weak. To measure, just look for where we have changed in the last period of time.
It can help nudge people to spend some of their learning time in a specific area where the team is weak.
If team members perceive they're personally being measured on this and this measures ties to their performance review/pay, they inflate their self-rating. So rate of change in Skills Matrix or Team learning is only useful if it is used by the team for their own needs.

[Cross Team Dependencies](https://github.com/FocusedObjective/FocusedObjective.Resources/blob/master/Presentations/Agile 2015 - Entangled - Solving the Hairy Problem of Team Dependencies \(Troy Magennis\).pdf)
The number of things that one team needs from another team.
The more things we need from other teams, the less freedom we have in prioritizing work (lead time is increased, etc.) The measurement allows us to spot the kinds of dependencies we suffer from. If we haven't already, this  
measure should force us to discover [Feature Teams](http://www.infoq.com/articles/scaling-lean-agile-feature-teams). And if we have, it should force us to invest in skills where we still depend on other teams.

Number of recent experiments run
Count the number of experiments run since the last measurement.
Agile Organizations are continually challenging the status quo. Counting the number of experiments can act as a reminder to run them and measure the results.
Experiments for the sake of experiments is also bad, so the trend doesn't matter as much as being reminded to run experiments.

Unfinished Stories, aka Adherence to Definition of Done
How many Stories at the end of sprint didn't meet the definition of Done.
Helps by forcing team members to focus on getting fewer stories to truly done every sprint.
By splitting stories into smaller chunks, teams are less likely to have unfinished work. This usually results in greater flexibility for the Product Owner and better throughput - so gaming this measure is a good idea.

Stories that have been Deployed
How many Stories have been deployed?
It forces team members to focus on getting small chunks of valuable work to production where we make money.

As Nassim Taleb points out, the best measures still won't measure your biggest risks. Risk registers are popular, but since their construction isn't scientific, they suffer from cognitive biases[[3](https://agilepainrelief.com/notesfromatooluser/2016/09/measurement-for-scrum-what-are-appropriate-measures.html?utm_content=buffer2606d&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)][[4](https://agilepainrelief.com/notesfromatooluser/2016/09/measurement-for-scrum-what-are-appropriate-measures.html?utm_content=buffer2606d&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)].

Some guidelines to help with measurement:

  * Assume all measures will be gamed.
  * Measure the simplest things that might help.
  * Fewer measures create simpler systems and simpler systems create less complex solutions.
  * Usually the real story is hidden behind the measure, and the measure was just a hint about where to look. Use measures to hint about what questions to ask.
  * Don't measure performance, measure outcomes.
  * Assume all measures eventually stop delivering value and should be dropped.
  * Don't burden your team members to collect your measurements.

In general, Scrum favours qualitative over quantitative measures. Measurement doesn't replace watching and listening.

#### What other measures have you tried? What effect did they have and how could they have been gamed?

Other good articles on measurement:

<http://www.innolution.com/blog/team-performance-measures>  
<http://leankit.com/blog/2016/03/why-vanity-metrics-are-dangerous-holding-a-mirror-up-to-your-measures-of-success/>  
<http://martinfowler.com/articles/useOfMetrics.html>  
<http://fourhourworkweek.com/2009/05/19/vanity-metrics-vs-actionable-metrics/>  
<http://blog.crisp.se/2011/10/19/anderslaestadius/the-happiness-metric-and-a-few-others>  
Formally documents the use of happiness as a Metric in Retrospectives  
<https://sites.google.com/a/scrumplop.org/published-patterns/retrospective-pattern-language/scrumming-the-scrum>  
Happiness Bubble <https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/beyond-the-happy-bubble>
