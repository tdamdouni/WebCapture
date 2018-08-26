# What's in the Metrics?

_Captured: 2018-06-05 at 20:11 from [dzone.com](https://dzone.com/articles/whats-in-the-metrics?edition=379233&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-05)_

**The Agile Zone is brought to you in partnership with [Techtown Training](https://dzone.com/go?i=275424&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddzone%26utm_medium%3Dfooter). Learn how DevOps and SAFe® can be used either separately or in unison as a way to make your organization more efficient, more effective, and more successful in our [SAFe® vs DevOps eBook](https://dzone.com/go?i=275424&u=http%3A%2F%2Fpages.aspeinc.com%2FSAFe-vs-DevOps.html%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_campaign%3Dsafe_vs_devops%26utm_content%3Debook).**

Everyone's supervisor wants to know the metrics behind their Agile journey.

Some of the most frequently-asked questions during Agile Scrum training are:

  * "There are a lot of metrics to measure. Which one I should pick up to track the progress of my team?"

  * "I use both the methodologies Scrum & Kanban within our iterations and I don't want to confuse my team members with different metrics from time to ntime."

  * "I thought my daily stand-ups are effective, but many times the last-minute spill-over surprises me."

  * "My manager keeps telling me constantly to "raise the bar" to build a high-performing team. I am not even sure where we are today to consider the next level"

Scrum espouses principles of "transparency, inspection, adaption," Kanban's philosophy involves "visualization, limiting WIP & enhancing flow," and Extreme Programming values "communication, simplicity & feedback." But the common theme revolves around visibility of work inclusive of blockers for the team, not only to understand where we are but also to do course correction.

Throughput and cycle time of the deliverables are two vital parameters to understand the progress as well as the projection of completion based on the current timeline.

While there are different charts and measurements that help in understanding throughput and cycle time - burn-up or burn-down in Scrum, visual flow in Kanban, velocity in extreme programming - cumulative flow diagram is one powerful chart that works effectively irrespective of the Agile methodologies the team operates in.

> "The greatest value of a picture is when it forces us to notice what we never expected to see." _- John W. Tukey_

Let me explain the power of a cumulative flow diagram as compared to other charts in understanding the flow better for actionable outcomes.

Below is the summary of the work planned and achieved by the team over 10 days:

![Image title](https://dzone.com/storage/temp/9319564-table-pic.jpg)

Let us explore a simple burn-down chart that depicts the ideal work remaining vs. actual work remaining:

![Image title](https://dzone.com/storage/temp/9319565-cf1.jpg)

Burn-down helps in understanding if we are on target or behind in comparison with ideal work remaining. It doesn't directly reflect the change though.

Now, let us the same through burn-up chart:

![Image title](https://dzone.com/storage/temp/9319581-cfd-3.jpg)

While this also helps in understanding work remaining, we can see the change in scope after Day-5.

Both the burn-up and burn-down charts focus on work completed and work remaining from customer perspective. While these are great measures, we also need to understand the intermediate flow (movement from one state to another) to be able to understand blockers and impediments.

Let us represent the above with a simple stacked bar chart:

![Image title](https://dzone.com/storage/temp/9319587-cfd-4.jpg)

Much better, isn't it? This depicts the progress through various stages as well as the scope change (the spike on Day 6).

It's time to covert the stacked bar chart into stacked area chart.

![Image title](https://dzone.com/storage/temp/9319589-cfd-5.jpg)

Bingo! Here comes our superhero cumulative flow diagram to our rescue to be able to deep dive further. Each colored area represents the flow (in the above, it is "Yet to Start", "In Progress", "Done," and "Shipped") and shift from one to another depicts throughput.

There are several important key takeaways from this chart which helps in further inspection & adaption:

  * **Scope Change:** Change in overall horizontal line. In the above chart, the change occurred on Day 6 and is stable after that.
  * **Thin Flow:** Thin flow represents a quicker process. "Done" flow is faster compared to "In Progress". If we need to lean overall throughput, then our focus should be on the "In Progress" flow.
  * **Average Lead Time:** The horizontal shift from "Yet to Start" to "Shipped"
  * **Cycle Time:** The horizontal shift from one state to another. For example, "In Progress" to "Done" will provide the cycle time.
  * **WIP**: It's important to measure the work-in-progress since limiting WIP expedites the progress. The vertical line within one state provides the number of items that are being processed (a.k.a) WIP.

It's a myth that the cumulative flow diagram is only for Kanban methodology. It provides immense value across the board. Cumulative flow diagram can be plotted for stories/tasks within an iteration. Hence is a great value addition in Scrum as well. It can also be expanded for features at program level and epics at the portfolio level. Thus, it provides benefits at various persona levels: Scrum master, program manager, product manager and business stakeholders. This is applicable not just in information technology; this visual representation helps in understanding and taking action in any day-to-day activity that we would like to optimize the overall experience/flow of.

It's a great tool, not just to track and troubleshoot development projects, but also for maintenance and operation projects. You gain better insights using a cumulative flow design, and it helps in driving meaningful retrospection.

**Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=266427&u=http%3A%2F%2Fpages.techtowntraining.com%2FDevOpsRoadmapDzone_DevOpsTransformationRoadmap.html%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_campaign%3Ddevops-transformation), brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266427&u=http%3A%2F%2Fwww.techtowntraining.com%2F). **

Topics:

agile metrics ,lean ,cycle time ,throughput ,productivity ,flow ,agile

Opinions expressed by DZone contributors are their own.
