# Define, Measure, Analyse, Improve, Control

_Captured: 2018-04-03 at 18:50 from [dzone.com](https://dzone.com/articles/define-measure-analyse-improve-control)_

**The Agile Zone is brought to you in partnership with [Techtown Training](https://dzone.com/go?i=275424&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddzone%26utm_medium%3Dfooter). Learn how DevOps and SAFe® can be used either separately or in unison as a way to make your organization more efficient, more effective, and more successful in our [SAFe® vs DevOps eBook](https://dzone.com/go?i=275424&u=http%3A%2F%2Fpages.aspeinc.com%2FSAFe-vs-DevOps.html%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_campaign%3Dsafe_vs_devops%26utm_content%3Debook).**

## D.M.A.I.C.

Anyone who has heard of Lean Six Sigma has heard of DMAIC. It's a method of root cause analysis for solutions that are not already known.

Regardless of what you think of Lean Six Sigma, I think the tools are worthwhile having in my mental toolbox.

For some reason, L6S (Lean Six Sigma) likes its acronyms. You have DOWNTIME for waste and SIPOC for Suppliers, Inputs, Outputs and Customers, but today I'd like to talk about DMAIC. DMAIC is another variation of a feedback loop, much like the OODA loop, PDCA, and the Lean Startup Loop.

DMAIC Stands for (if you haven't got it from the title)

  * **Define** - Define the problem

  * **Measure** - Work out how you are going to measure the problem and its variation then get a baseline measurement.

  * **Analyse** - Analyse the process that the problem is under. Collect the data and determine the root cause, the defect or any other form of problem such as waste.

  * **Improve** - Develop and implement a solution to remove or diminish the problem. Confirm your improvement with data using the method determined in the Measure phase.

  * **Control** - Maintain the gains. This can be done by documenting the improved process and continuously monitoring to make sure that the problem doesn't surface again.

Lets go into these in a little more detail.

### Define

In the define phase, you try to gain a little more clarity on the problem that is occurring and what you are trying to improve. This helps determine the focus of the improvement efforts.

Here you write down exactly what you want to achieve. In L6S, they recommend doing what they call a Project Charter. I'm not going to focus on this. I'm just going to focus on the basics.

The first thing that I think is important is to state your problem. Now, a good problem statement does not propose a root cause or a solution. So for example, "Implement Automated testing" is not a good problem statement. Nor should you blame anyone for the problem. "John continuously makes more errors that Jane," for example.

A good problem statement will answer the following questions.

  * What is the problem or issue?
  * What is the measure that you are trying to impact?

So a poor problem statement may be:  
_"We have too many defects during the development process."_

A better one may be:  
_"Since the project began _(when)_, we have an average of 15 defects _(Magnitude)_ per sprint that cause significant delays to the delivery of the product." _(Impact)

As you can see, I have used 3 terms to put into context the problem: _When_, _Magnitude_ and _Impact_.

The next thing to try to determine is a goal. Using our defect example, a goal may be:  
_To Decrease _(verb)_ the defect _(what)_ rate from an average of 15 per sprint down 50% to 7 per sprint (_improvement_) within the next 2 sprints _(timeline)_._

Again, I have highlighted sections of the statement. The _verb_, to describe what you are trying to achieve. The _what_ you are focusing on, the _improvement_, or expected results, and finally a _timeline_ that this "experiment" will take place.

There are a few more sections that are part of a problem statement from L6S, but I'm not going to go through them here.

### Measure

The measure phase is where you determine how you are going to measure the current state and the effect.

Here you determine if the problem actually exists by gaining a baseline measurement and try to understand exactly what is happening.

By using the same methods that you used to determine the baseline, you are able to determine the amount of improvement that has occurred and whether or not you have reached your target.

So what can be measured?

In our example, we are just using "defects", but you could also use

  * Cycle time
  * Days
  * Size
  * Currency (Such as Dollars, Pounds, Pesos etc)
  * Any other type of measurement relevant to the problem.

The key here is to collect meaningful data that will help you understand the problem and help you determine if you have made an impact during your "Improvement" phase.

Some questions that may help you determine a measurement may be:

  * What are you trying to measure?
  * Why do you need it?
  * Where in the process does the measurement exist?
  * How would you define the measure?
  * Where is the data sourced from?
  * How will the data be collected?
  * When will the data be collected?
  * How will you make sure that the data is valid?

We then may want to graph the data in a histogram for example to get a visual idea on the problem.

### Analysis

In the Analysis phase, we have had our measurements going, now its time to determine the root cause. Given the data retrieved through the Measurement phase, we use techniques determine the root cause. This requires investigation. Probing the data, playing around with the data. Trying different things to see the effect. These can be determined by using techniques such as process mapping, brainstorming, the [fishbone](http://www.beanietech.com/blog/407/) diagram, [5 whys](http://www.beanietech.com/blog/why-why-why-why-why-is-current-reality-a-tree/), even Trial and Error. Basically any problem analysis tool.

The whole idea of the Analysis phase is to prove the root cause rather than jumping to conclusions.  
Sometimes you need to think outside the box to find the root cause. Something what seems obvious, may only be a symptom. Its worth while digging deeper just in case.

Determine a hypothesis for the root cause. This is a theory, opinion or guess as to what the problem is. Then research your hypothesis and prove it with data, but don't get caught in "Analysis Paralysis" where you continuously analyse without actually doing anything. You have to stop sometime and giving yourself a time box can help with that.

Questions you can ask yourself after the analysis phase is:

  * Has the root cause been verified by process analysis and data analysis?
  * Has enough been targeted?
  * Would additional analysis cost more that what it is worth?

### Improvement

The improvement phase is where you address the root cause and try to correct it.

The improvement may not be implemented straight away. You may decide to run a pilot or Proof Of Concept to determine if the solution actually fixes the problem, but ultimately the problem should be fixed or reduced.

Using the techniques developed during the Measurement phase, you can determine whether or not the improvement has actually worked and whether or not you have reached the target. This is important as this is part of the feedback loop. We have a tendency to implement "improvements" and not verify them. "They are in - great! now move onto the next thing." The problem with this thinking is that you do not know if the improvement actually worked or not. This is common sense, but common sense is rarely implemented.

If you have reached or exceeded your target - excellent! If not, then maybe you need to tweak or rethink your solution and try again.

### Control

The control phase is making sure that your improvement remains. Here you need to determine a clear plan for maintaining the process. The system will need to be monitored to make sure that the problem doesn't surface again and if it does, what countermeasures will be needed. This is to determine long term success.

We do not need to have the same degree of measurement that we had during the previous phases as the root cause has been determined (we are no longer fishing for the problem) we just need enough information to determine that all is well.

Questions that should be answered are:

  * What is to be measured?
  * How will the measurement be checked?
  * How often will the measurement be collected?
  * Who is responsible for gathering the data?

You may also want to document the process taken for the improvement plan showing the problem, the root cause analysis, the improvement taken and what controls are in place to prevent the problem from happening again. This could be used for future reference.

## In Closing

The DMAIC process seems intensive; it is. There is also quite a bit of the DMAIC process that I haven't covered in this post, but it does formalise the problem solving process and its implementation of the resolution and for that, I think it is worth trying. Even just for an experiment.

For more information on Lean Six Sigma, I recommend doing the free Yellow Belt Training at [Go Lean Six Sigma](https://goleansixsigma.com/yellow-belt/).  
In order to get the "certification" you need to pay and take the test, but the training itself is free and free education is always good.

**Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=266427&u=http%3A%2F%2Fpages.techtowntraining.com%2FDevOpsRoadmapDzone_DevOpsTransformationRoadmap.html%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_campaign%3Ddevops-transformation), brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266427&u=http%3A%2F%2Fwww.techtowntraining.com%2F). **

### Like This Article? Read More From DZone
