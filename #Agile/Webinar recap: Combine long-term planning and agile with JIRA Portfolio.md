# Webinar recap: Combine long-term planning and agile with JIRA Portfolio

_Captured: 2015-06-14 at 12:35 from [blogs.atlassian.com](http://blogs.atlassian.com/2015/06/webinar-recap-combine-long-term-planning-agile-jira-portfolio/)_

Every quarter, the JIRA Portfolio team does their full roadmap review and long-term planning. This quarter, we were able to convince Martin Suntinger, the Principal Product Manager for JIRA Portfolio, to give us a sneak peak into what goes down.

Watch the webinar below to see how our planning experts use JIRA Portfolio to combine both long-term planning and agile.

## Watch the webinar now

## Takeaway tips

  * Work "backwards" - set the goals first to avoid being biased
  * Start with the "big ticket items" - define the key initiatives
  * Prepare one single filter to pick up new issues regularly
  * Choosing the parent epic or initiative directly upon import is the most efficient
  * To plan quickly, use default estimates first, and refine estimates later
  * Release streams are a great way to route work automatically to teams
  * Be prepared for surprises; seeing realistic roadmaps can be painful!
  * Create different versions of a plan for scenarios by exporting and creating a copy from the export
  * Comparing the original goals to the latest plan helps to stay focused
  * JIRA Portfolio can be used as a staging environment until things are ready to implement

## Top Q&A

Here, Martin selected some of the most common questions from the Q&A session across the three timezones.

  * **Do I need to use themes at all? They don't seem to map to the way we work in a service-oriented organization doing customer projects. **

No, themes are completely optional so all planning can be done without using themes. However, we have found them very useful in various types of organizations to track business goals or investment categories. For example, in a service-oriented organization you could use a theme like "customer-facing" or "internal" with a goal to spend at least 80% in customer-facing projects. Themes are a very flexible concept for tagging the items in the backlog and for getting an overview on the allocation of effort amongst them.

  * **It seemed from the demo you don't use stages and skills? What is your recommendation and experience there?**

With the JIRA Portfolio team, we currently plan using story points and an overall team velocity. We don't make use of stages and skills in our main roadmap plan. Generally, the recommendation is to keep it simple, and model explicit skills (like, for example, frontend development, or backend development), and stages (like design, implementation, test), only when it is relevant to get the capacity planning right, and these specializations in the teams otherwise cause bottlenecks if not planned out in detail. If a team is mostly cross-functional, and the different skills typically "even-out" and balance well, there is no need to model them in the tool just for the sake of planning. There is no right or wrong here, go just as detailed as needed to plan realistically, even if that means just deleting all the stages and skills that come with some of the plan templates from the beginning.

  * **How do you avoid picking up the same issues and importing them as duplicates using the saved filter?**

In the import issues dialog, there is an option called "Exclude already linked (issues)" at the top. If this is checked, then issues that are already imported will not be loaded again and double-imported.

  * **Is it possible to change the team velocity for a future release? (e.g. a contractor decided to not extend a contract and the end date is known)**

Yes, it is possible to dynamically adjust the velocity forecast based on available hours. When modeling for the particular contractor who is only available until date X, the overall team velocity will be adjusted proportionally from that date onward. For example, if the team has five defined members and a velocity of 50 points per sprint, if one member is modeled to be available only until date X, after that date, the velocity will be adjusted to 40. This is not bound to releases generally, but rather to the availability timeframes of the team members.

  * **Is there a way to compare multiple plans?**

No, there is currently no side-by-side comparison of plans, the only option is to open them in different windows/tabs and compare manually.

  * **Is it possible to schedule the re-imports?**

No, this can currently only be done manually via the user interface.

  * **It appears that in order to use the tool, stories and epics already need to be set up in JIRA, is this correct? If so, what level of detail is needed to make the portfolio tool useful?**

In this webinar, we've just shown one very common scenario, with existing epics and stories already available. However, it's also possible to start out straight in JIRA Portfolio, create initiatives, epics, and stories there while planning, and later "push" these issues into one or multiple JIRA projects (by using "Create and link new issues"). JIRA Portfolio requires at least epic-level granularity for higher-level roadmap planning. This means it is possible to plan with only epics and giving them a rough estimate, without any detailed child stories. Also, on the team level, it's perfectly fine to start out with just the overall team velocity, or putting in a placeholder resource that represents the whole team without modeling the individual team members.

  * **Is the current JIRA Portfolio functionality available to JIRA Cloud? Are future features rolled out to Cloud after the standard server? Or are they simultaneous releases?**

Yes, the latest version of JIRA Portfolio is available for both Server and Cloud. Generally, we aim to release for both platforms concurrently.

  * **Can the tool address dependencies among streams?**

Yes, dependencies can be set between epics and stories both within a stream or across multiple streams, which is a common case if different independent deliverables need to come together for a joint release.

  * **When you auto calculate velocities for teams based on their recent sprints, will this update dynamically or should it be updated manually as new sprints are completed?**

The velocity taken from the agile board based on recent sprints does not update dynamically, but you can bring up the same dialog again to set a new suggested value. In practice, we found that quite often the exact average of recent sprints is not perfect. We end up rounding it, or we know it is slightly higher or lower than what we plan with because of unexpected events in a previous sprint, so we regularly double check and adjust this.

  * **Is it possible to define team capacity without defining individual team members?**

Yes - in the case of using story points, it is sufficient just to enter a value for each team's velocity. In case of time-based planning in days or hours, technically, at least one placeholder resource needs to be entered for a team. This can be done easily by adding a so-called virtual user to the team. If the team is, for example, seven people working full-time, the minimum needed for time-based planning is to add the team and add one virtual placeholder resource with 7*40 = 280 weekly hours to get the right overall capacity. Beyond that, entering team members allows for planning individual absences, varying availabilities, different skill sets etc. to refine the capacity plan and get it to be more realistic.

  * **How do you suggest releases if your company is releasing multiple times a week? Should each release be entered into the stream?**

This of course depends on the individual needs for planning, but generally, I would rather recommend not to represent all these releases separately in JIRA Portfolio. The releases in JIRA Portfolio are mainly useful when having to manage exact cut-off dates, or planning towards a desired scope of a deliverable. In case of multiple releases per week, you'd rather want to plan the work on a continuous basis, and ship whenever particular stories or epics are ready. Planning should be focused on the priority order in which things will be done, and they are shipped when completed. I recommend to use releases in this context only for larger deliverables, or for bigger milestones, or broader time intervals like one release per month or quarter to roughly slate what is planned when, independent from the deployment frequency.

Notify me of follow-up comments by email.

Notify me of new posts by email.
