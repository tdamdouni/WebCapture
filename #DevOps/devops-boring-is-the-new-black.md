# DevOps: Boring Is the New Black

_Captured: 2018-02-03 at 20:41 from [dzone.com](https://dzone.com/articles/boring-is-the-new-black?edition=358115&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-03)_

[Download the blueprint](https://dzone.com/go?i=228233&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) that can take a company of any maturity level all the way up to enterprise-scale continuous delivery using a combination of Automic Release Automation, Automic's 20+ years of business automation experience, and the proven tools and practices the company is already leveraging.

99.99% uptime is so last decade. Agile was sexy for a while. Now DevOps and DevSecOps are becoming all the rage for organizations that value the operational boredom they promote to send new features and capabilities down the runway with an always-on continuous delivery at a customer-pleasing pace.

## Why Boring?

Think about it. Are you on a _multi-week/month_ deployment cadence (already a problem)? Are your deployments exciting? Is your operations team putting in extra long shifts as they scramble like smoke jumpers to put out a forest fire? Do your post-mortems result in more finger pointing than _Gunfight at the OK Corral?_

So, what does exciting get you? Your operations team probably feels under-appreciated for all of the great work they're doing to keep the service up and your customers happy. They're probably also asking for fewer product changes and higher headcounts if you hope to keep the business afloat. Hardly a recipe for growth.

Contrast this with fashion-forward DevOps practices from businesses like Netflix, Amazon, and Walmart. As successful as these businesses are, they push out dozens of production deployments each day and can't possibly afford to be fighting fires all the time. Their ability to maintain a hands-off automated approach to infrastructure and deployment management is key to their success. For these companies, infrastructure has become another development specialty where developers spend their days (not nights) working to deliver increased value to the business.

**Bottom line: **_boring =/= fas_t, _boring =/= efficient_ and boring makes for happy customers.

## How to Be Boring

As long as your organization has some form of continuous improvement methodology in place in some part of your technical organization, the chance that you will succeed at making your journey from exciting to boring are pretty good. It won't be easy and it won't happen overnight, but if you consider the following, you should be able to get there.

  * Get everyone on the same page with shared Goals and KPIs
  * Build a Roadmap to Automating Everything
  * Assemble multi-disciplinary teams
  * Design and build the telemetry you'll need to succeed
  * Send the pager to where it will do the greatest good
  * Start converting pets into cattle
  * Refactor testing and pipelines to enable finer granularity and rollback for deployments

### Shared Goals and KPIs

Shared goals and measurable key performance indicators are critical success factors for organizations seeking benefits from DevOps.

A sure-fire recipe to make operation and delivery of your services exciting is to choose the wrong metrics and apply them in ways that guarantee that your organizations will not work together. Uptime is typical of this kind of failure.

Using uptime as your marquis key performance indicator applied exclusively to your operations team guarantees that your operations team will be hyper-focused on watching for and responding to incidents. There's no incentive to improve systems to preempt failure and the development organization has absolutely no skin in the game: they're busy building features that only need to make it through testing.

A successful recipe, on the other hand, is dependent on senior leadership's ability to develop and champion shared goals that support a DevOps/DevSecOps effort with measurable metrics. Once a baseline has been measured, a sure way to get everyone's attention is to make it clear that individual performance evaluations will be tied to meeting or exceeding metric targets. It's amazing how cooperative people become once shared responsibility is a requirement.

A lot has been written about DevOps metrics. The article, [Why Metrics Must Guide Your DevOps Initiative](https://dzone.com/articles/why-metrics-must-guide-your-devops-initiative-blog), takes a look at Gartner's DevOps pyramid with metrics that span development, operations and most importantly, the business. Other articles focus on a subset of generally agreed upon metrics. [The DevOps Scorecard](https://devops.com/devops-scorecard/) is a good example.

These metrics include:

**Deployment frequency:** once a month or 30 times a day are examples.

**Change volume:** the number of features/lines of code/stories per deployment.

**Lead time (from Dev to Deployment):** average time to make it from development through to production.

**Percentage of failed deployments:** what percentage of deployments cause an outage, partial outage or negative user effect.

**Mean time to recovery:** How long, on average does it take to recover from a failure. Consider also measuring mean time to discovery.

**Customer Ticket Volume:** The number of tickets should indicate some sort of service issue.

**Availability:** uptime still matters!

**Performance (Response time):** service response times should remain stable across demand.

### Roadmap

A journey begins with a single step, but you're going to need a map with waypoints that can be shared so everyone knows where you're going and what they can expect to achieve along the way. Failure to communicate the journey and address fears and concerns will result in confusion, de-motivate staff and could drive some good people to resign.

While it doesn't pay to get too far into the weeds when developing a roadmap, it should cover enough to remain evergreen throughout the effort and have senior leadership and stakeholder buy-in if it is to succeed.

A typical roadmap might include:

  * Business drivers - i.e. Why are we doing this?

  * Relative priorities and milestones for the transition.

  * Triggers for the adoption of the new Goals and KPIs.

  * A clear diagram, or dashboard that summarize key priorities and status to increase understanding and engagement with the process.

### Multi-Disciplinary Teams

Wouldn't it be great if all technical staff were interchangeable? Probably not. People bring a multitude of different skills and knowledge necessary to make the transition from walled gardens to DevOps. A developer and an operations sysadmin may share some skills, but their perspectives and much of their skill sets have been shaped by their roles. Your operations person may be weak on programming, or developing architecture, while a developer is likely weak on many of the requirements that a production ready system needs.

All organizations are different, so the inclusion of different roles within a team may depend on roles and expectations that already exist. In some organizations, development teams are responsible for their own pipelines and test generation while in others these have been organized into external teams.

Team makeup and member engagement will also depend on the kind of development that the team is accomplishing. An infrastructure team that is building new automation features to support the product will need far more operations savvy engagement than a line-of-business team. Regardless, a DevOps team should include the expertise needed to address all aspects of feature delivery from story generation to production.

### Telemetry

Peter Drucker said, "if you can't measure it, you can't improve it." Designing and implementing your telemetry infrastructure is what make this possible and will be key to your ability to measure progress, identify and address issues. There are many solutions in this space to address logging, monitoring, application traffic, networking, and security. Your choices will depend on the nature of your business need.

_Logging requirements:_

  * Scale to an organization's need for distribution, filtering, and aggregation.
  * Identify application and system issues, their nature and source and location.
  * Provide time-series analysis.
  * Queryable without requiring application changes.

_Typical enterprise logging solutions include:_

_Monitoring requirements_

  * Support system, security, and application health.

  * Scale to handle the number of clusters, nodes, and logs generated by the enterprise.

  * Offer federation of data in order to pull together metrics from disparate sources and locations.

  * Support the ability to build dashboards independently of metric collection to enable teams to build views based on their own needs.

  * Offer rules-based alerting on time-series data.

  * Offer the ability to integrate actions to respond to alert conditions.

_Typical enterprise monitoring solutions include:_

### Pager Duty

_Who gets paged?_ Is a key question when determining the maturity of a DevOps organization. In traditional operations, it is operations that plays point on everything. This creates a grind that generates tremendous wear and tear on the operations team making it appear as though crisis is the norm. It also guarantees that it will take longer to find the root cause and fix.

Tools like [VictorOps](https://victorops.com/) and [PagerDuty](https://www.pagerduty.com/) have been around for a while and make it possible to route issues to the right people, track issues, build ad-hoc teams and manage post mortems. Integration of smart notifications that brings the right people together to solve your production problems is a must for success!

### From Pets to Cattle

We love our pets, they are unique, we take special care of them and have a long history with them. Cattle, on the other hand, are a commodity where one is just as useful as the next. It's one thing when the pet is your beloved dog and entirely another when it's a server whose configuration is impossible to recreate because it has evolved over time.

_Replacing your pets with cattle is a key component to creating boredom in an enterprise._

Transforming pets into cattle can be a big undertaking and requires your organization to commit to building all of your infrastructure as code that is under configuration control. This doesn't mean that your operations team has a few _bash scripts_ it runs on a machine when it wants to build something. It means that infrastructure gets treated exactly the same way as your organization's service software.

With cattle:

  * Any resource can be easily deployed, replaced, upgraded or scaled.

  * There is no need to log into a production instance.

  * Progress can be planned, prioritized, designed, implemented and tested.

  * Infrastructure can be observably consistent with anomalies detected and repaired.

  * Alerts can be de-escalated as resources are automatically replaced or repaired.

### Pipeline Improvement

The process of transforming your infrastructure through code and integrating operations and security thinking into development will rely heavily on your Agile roots. Your new approach essentially takes agile and widens it to include configuration management, monitoring, metrics, virtualization, and orchestration.

Where your old agile practice ended with Test, your new cross-functional operations approach looks something like this...

![](https://media.licdn.com/mpr/mpr/AAMAAgDGAAgAAQAAAAAAAA4kAAAAJGI0MDA5NDBkLWMwNDgtNGI5Ny04YjE4LTkxNzYwZGM2YzRhNQ.png)

To build this feedback loop you'll need to extend and enhance your pipelines and configuration control to automate the entire process into one virtuous cycle.

With improved pipelines and more automation, it becomes possible to break software down into smaller chunks that can be released and deployed as features become ready. This enables features to come out faster and reduces the impact of problems when they occur; rollbacks are possible and smaller releases mean that less value is lost when a release is rolled back.

Finally, armed with this new virtuous DevOps cycle, you'll begin to roll out infrastructure and applications that are completely automated and are a whole lot less exciting to operate. The more you accomplish towards making things more boring, the more you will be able to accomplish. Here's hoping you do!

[Download](https://dzone.com/go?i=228234&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) the 'Practical Blueprint to Continuous Delivery' to learn how Automic Release Automation can help you begin or continue your company's digital transformation.
