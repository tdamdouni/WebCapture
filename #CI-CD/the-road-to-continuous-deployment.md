# The Road to Continuous Deployment

_Captured: 2017-09-03 at 13:01 from [dzone.com](https://dzone.com/articles/the-road-to-continuous-deployment?edition=322395&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-09-02)_

The Nexus Suite is uniquely architected for a DevOps native world and creates value early in the development pipeline, provides precise contextual controls at every phase, and accelerates DevOps innovation with automation you can trust. [Read how in this ebook](https://dzone.com/go?i=222229&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

We have all heard the excuses: management won't go for it; the code is a jumbled mess; it's too large; too many regulatory hurdles. The trek to Continuous Integration/Continuous Deployment has stumbled for many enterprises, but many more each day have made it.

[Michiel Rook](https://www.linkedin.com/in/michieltcs/) spoke at the 2016 [All Day DevOps conference](http://alldaydevops.com/) about his road to Continuous Deployment. He used an example he worked on for De Persgroep Employment Solutions, which operates a number of job portals. This specific project was called the San Diego Project, but it was known internally as the Big Ball of Mud because the code base was such a mess. The image below diagrams the legacy system - the beginning of the road.

![rook.png](https://www.alldaydevops.com/hs-fs/hubfs/rook.png?t=1503581924816&width=1920&name=rook.png)

The project was burdened with infrequent, manual releases, fragile tests, frequent outages and issues, a frustrated team of about 16 people, and low-confidence modifying existing code. Sound familiar? Yep, you were not alone.

The team knew something needed to be done, so they set some goals, including:

  * Reduce issues,

  * Reduce cycle time,

  * Increase productivity, and

  * Increase motivation.

Their approach was to take the monolith, build a proxy and add a service, and then keep adding services until the monolith could be thrown away.

![rook2.png](https://www.alldaydevops.com/hs-fs/hubfs/rook2.png?t=1503581924816&width=1920&name=rook2.png)

> _Of course, this is a simple explanation; much more went into the trek._

So, in this article, we are going to dig deeper, as Michiel also does in his [full talk](https://www.youtube.com/watch?v=HSYpWXz3O64&__hstc=31049440.6325613bfa5f684c3c47d140220f1453.1496940254734.1499978930164.1500495641918.28&__hssc=31049440.6.1500495641918&__hsfp=2042285363).

They started with a foundation of principles to guide their journey:

  * Apply the strangler pattern.

  * Use API first methodology.

  * Set one service per domain object (job, jobseeker, etc.).

  * Migrate individual pages.

  * Establish services behind load balancers.

  * Access legacy databases.

  * Implement continuous deployment.

  * Utilize Docker containers.

  * Develop frontends as services.

This all culminates to continuously deliver value, something Michiel calls "Continuous Everything."

It starts with Continuous Integration: developing and building/testing, resulting in an artifact each time. Then, Continuous Delivery: building/testing-->acceptance-->production; going into production is a manual process, but the code is always deployable. Finally, you reach Continuous Deployment when the whole process is automated.

Continuous Deployment is advantageous because it offers the following:

  * Small steps.

  * Early feedback.

  * Reduced cycle time.

  * Reduced risk.

  * Room to experiment.

![rook3.png](https://www.alldaydevops.com/hs-fs/hubfs/rook3.png?t=1503581924816&width=1920&name=rook3.png)

Now that Michiel's project is behind him, he offered the following key aspects of any road trip to continuous deployment:

  * **Only Commit to Master**. No branches. You don't want to delay integration and abuse version control for functional separation. Plus, everything on a branch increases the risk of conflicts and delays integration.

  * **Every Commit Goes to Production.**

  * **Use pair programmingfor code review.** This will require discipline, but all development needs to be paired. Mix and match experienced developers.

  * **Quality Gates. **Ensure a substantial amount of tests and code coverage.

  * **Feature Toggles and A/B Tests. **Determine which version people can/can't see and facilitate A/B testing. But, be sure to keep the number in check.

  * **Dashboards.** Display is essential for deployments. Measure everything: KPIs, build times, page load times, number of visitors, results of A/B tests, etc.

  * **DevOps**. Mentality is a culture; no more walls between dev and ops. Ownership lies within the team for everything, but this doesn't mean everyone knows everything.

  * **Automate Repeatable Things.** If you need to do something twice, you have done it too many times.

  * **Continuous Testing**. Use unit tests and smoke tests to see if a service is live, and always monitor. Exploratory testing is important because you continue to test the most critical paths.

![rook4.png](https://www.alldaydevops.com/hs-fs/hubfs/rook4.png?t=1503581924816&width=1920&name=rook4.png)

  * **Pipeline as Code. **Automate the pipeline. In the end, the deployment looks like this:

![rook5.png](https://www.alldaydevops.com/hs-fs/hubfs/rook5.png?t=1503581924816&width=1920&name=rook5.png)

  * **Feedback - **DevOps is built on the importance of feedback. One example Michiel had on this project was a large, red flashing light that signaled a build failure. Whenever it went off, that became the number one thing people started working on.

Michiel's project spanned over one year. In the end, they reduced the total build time per service to less than 10 minutes, significantly improved page load times, increased confidence and velocity, and more. The universal truths of the importance of team acceptance and that change is hard were seen. They also learned, among other things, that the alignment with business priorities is key, ensuring you have the necessary experience on staff is essential, and limiting feature toggles is crucial.

Overall, Michiel and his team made it to Continuous Deployment. At the end of his [talk](https://youtu.be/HSYpWXz3O64), Michiel did report that, to his dismay, the legacy system they are seeking to replace is also still in service. The road is long, but worth the trip.

If you missed any of the other 30-minute long presentations from 2016 All Day DevOps, they are easy to find and available free-of-charge [here](https://www.alldaydevops.com/addo-on-demand). Finally, be sure to register you and the rest of your team for the 2017 All Day DevOps conference [here](https://www.alldaydevops.com/register). This year's event will offer 96 practitioner-led sessions (no vendor pitches allowed). It's all free and online on October 24th.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. See how the Nexus platform infuses precise open source component intelligence into the DevOps pipeline early, everywhere, and at scale. [Read how in this ebook](https://dzone.com/go?i=222230&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

Topics:

devops ,addo ,continuous deployment ,continuous integration ,ci/cd ,all day devops
