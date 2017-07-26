# How to Shift Feedback Loops Farther Left in the Software Delivery Pipeline

_Captured: 2017-02-20 at 10:27 from [dzone.com](https://dzone.com/articles/how-to-shift-feedback-loops-farther-left-in-the-so?oid=twitter&utm_content=buffera451a&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

In response to Developers' and Operations' concerns, [Electric Cloud](http://www.electriccloud.com) has partnered with [Dynatrace](https://www.dynatrace.com/), enabling organizations to uncover end-user, performance, and operational costs that are impacting issues in cloud environments and enterprise software much earlier in the delivery pipeline.

This partnership addresses concerns like:

  * "We need to detect performance problems earlier in the lifecycle so they don't cause damage downstream."

  * "When performance problems occur in production, I want to be able to trigger an auto-rollback."

  * "I want to better track the effect deployment incidents have on performance."

The new bi-directional integration enables a closed feedback loop between DevOps and release pipelines and environments.

The integration allows users to detect performance issues earlier in the lifecycle, identify the root cause, have faster remediation and recovery, and prevent outages with automated policy-based rollback and self-healing. These enhance product quality, speed to market, and customer experience while giving Operations confidence in the Release and environments and deployments fidelity.

When ElectricFlow deploys an app to an environment, it also creates a deployment incident in Dynatrace. ElectricFlow passes relevant information to Dynatrace, and it gets captured in AppMon. This information includes app name, environment name, snapshot, link to ElectricFlow pipeline, and other supporting data. This information can be viewed within AppMon tools. And when an SLA Violation is detected by AppMon, ElectricFlow to Dynatrace integration triggers the auto-remediation (a.k.a. "self healing") process.

Additional benefits include:

  * **Cross-environment image fidelity. **Don't introduce new "monitoring agents" in Production.

  * **Cross-team tool fidelity.** When a problem occurs in either environment, all teams understand the tool and know how to jump in and help

  * **"Metrics that matter" fidelity. **Keep _all_ teams focused on _your_ key metrics.

"In a world where batch sizes are shrinking and the pace of releases is increasing, having automated policy-based control in the pre-production environment proactively reduces the chances of end-user, performance, and operational issues in production," said Steve Brodie, CEO at Electric Cloud. "Dynatrace, like Electric Cloud, was named a leader in a 2016 Gartner Magic Quadrant. The Application Performance Monitoring suite provides full-stack monitoring -- looking deeper than typical testing tools -- and allows ElectricFlow to automatically trigger the appropriate actions needed to bring the system back to a good state."

"This partnership between Dynatrace and Electric Cloud helps enterprises reduce the risk of end-users impacting production deployments by monitoring and looping feedback earlier in the application lifecycle, " said Andreas Grabner, DevOps Advocate at Dynatrace. "Customers will now be able to immediately see the potential impact of code changes, remediate, and fix poor app behavior earlier in the lifecycle. This greatly reduces time spent course-correcting in production and frees up more time for innovation."

The new Dynatrace plugin for ElectricFlow is available [here](http://electric-cloud.com/plugins/directory/p/dynatrace/).

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

### Like This Article? Read More From DZone

Opinions expressed by DZone contributors are their own.
