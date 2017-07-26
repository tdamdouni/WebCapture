# DevOps in Action – Ops on Dev Teams

_Captured: 2017-05-16 at 20:00 from [dzone.com](https://dzone.com/articles/devops-in-action-ops-on-dev-teams?utm_content=buffer84c7d&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

### DevOps stems from the idea that developers and operations need to connect and work together. What better way than to put an ops liaison on the dev team?

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

The term "DevOps" was coined by Patrick Debois back in 2009 to communicate the idea that developers and operations people need to connect with each other and work together. Indeed, in the intervening 7-plus years, along with creating great tools and addressing Flow, Feedback, and Continuous Learning & Experimentation in our practices, the DevOps community has put a lot of effort into the human side of the equation - how to actually connect Dev and Ops.

In this article, we will explore one particularly radical idea for making this connection: Inserting Ops people onto Dev teams.

## Who Is the Product Owner?

The Agile methods introduced a similarly radical idea over 16 years ago; that the customer for whom the team is building the software should operate as a full member of the development team. Scrum calls this person the Product Owner (and most Agile teams use this term) because this is the team member who owns the responsibility for ensuring that the team builds the right product. The Product Owner owns the Product Backlog (User Stories), sets the development priorities, and decides if what the team builds is acceptable or not.

Many organizations have found this to be a challenging role to fill (for a wide variety of reasons), and many have compromised on this point. But Agile teams that have a true Product Owner are more likely to be successful because this person brings knowledge and insights that the technical members of the team are almost guaranteed to lack. A true Product Owner and a competent technical team can negotiate the details of the software so that the resulting product is technically excellent and fully meets the business need.

## The Third Dimension - Operations

But being technically excellent and fully meeting the business need are only two dimensions. DevOps has taught us that there is a third dimension that must be considered: the operational dimension. The product must be deployed into production, operated on a day-to-day basis, and supported by the help-desk. It must make efficient use of the infrastructure, and be secure and reliable. And the Ops team will need to be able to trouble-shoot to determine if an incident is being caused by the operational environment or by a problem with the software.

Most development teams have limited insight into the operational dimension. (And it is a near certainty that the Product Owner doesn't have a clue about it!) This leaves the team with a blind spot that can result in their best efforts falling short when the product is deployed. Just as a development team needs the Product Owner to bring the customer perspective; they need someone to bring the Ops perspective as well.

Let's take a look at some of the ways an Operations person can add value as a member of a development team.

## Ops Stories

An Agile Product Backlog consists primarily of User Stories, because the majority of the development work is focused on meeting the needs of the users. But the users are not the only people who work with the software; the operations team does too.

So the first role of the Ops member of the team is to articulate the Ops Stories, which describe all of the interactions that the operational staff will have with the software. For example:

  * As an operator, I need to start up the system, so users can use it.
  * As a Help-Desk analyst, I need to login as a user, so I can walk him/her through a problem.
  * As an Incident responder, I need to see key statistics, so I can troubleshoot an Incident.
  * As a Security Analyst, I need to be notified when certain patterns show up in the failed login statistics, so I can identify potential hacker activity.

In addition to writing Ops Stories the Ops member of the team mirrors the Product Owner in these other ways:

![Image title](https://dzone.com/storage/temp/5262383-screen-shot-2017-05-11-at-50438-pm.png)

## Architecture and System Design

Many of the technical decisions that a development team makes have material impacts on the operations team. So a second way for an Ops member to contribute to the dev team is to participate in the team's architecture and design discussions.

The development members of the team will want to structure the software to make development straightforward, to enhance its maintainability, and to enable future changes and extensions. These priorities need to share space with operational priorities like ease of tuning and scaling, ability to control resource usage and accommodate resource limitations while maintaining service, and visibility into the software that will enable quick and accurate Incident resolution.

With both Ops and Dev involved in these decisions, system designs can usually be optimized for both groups. And when the Dev and Ops priorities clash, the impacts to both can be examined as the team negotiates their way to the most advantageous software structure over-all.  
Testing from an Operational Perspective  
A third way the Ops person can contribute is to participate in the team's testing during their sprints. This participation can take several forms. The Ops person can ensure that:

  1. Testing is indeed being done in a production-like environment,
  2. All operational considerations are included in the set of test scenarios and test cases,
  3. Production-like monitoring is turned on and is generating logs, statistics, and alerts, and
  4. Those logs, statistics, and alerts are being analyzed for insights into software behavior that may not be obvious from the functional test results; things like:
  * Growing memory demand that could indicate memory leaks,
  * Unexpected network activity that could foreshadow slowdowns in production, or
  * Behavior that could be exploited by hackers to gain unauthorized control of the system or its data.

## Operational Support for the Dev Team

In addition to the benefits of an Ops perspective in development, inserting an Ops person into Dev teams will result in better operational support for Dev teams, too. It starts with the obvious: the Ops person is a dedicated resource for the Dev team enabling them to get the support they need more quickly and easily.

But that is only the beginning. The Ops people who work in this mode will gain a good understanding of Dev teams' needs and challenges. This knowledge will enable the Ops organization to tailor their services to better meet Dev's needs, including identifying opportunities to enable self-service for Dev Teams (e.g. to set up a test environment), or ways to make the Deployment Pipeline flow more smoothly.

## Ops Person on the Dev Team

A dedicated Ops person for each Dev team may not be achievable in the short term, but it is clearly worth experimenting with on at least a limited basis. One option is to establish an Ops Liaison for each Dev team - a person who is not fully embedded in the Dev team, but is available to them as needed.

As compelling as the benefits described here are, they are probably not the only ways that an Ops person on a Dev team can bring value to the organization. This is a new concept, and as we gain more experience with it, there is no doubt that we will find more ways to gain value from it. This radical idea is worth exploring as we work our way up the DevOps maturity scale.

## Turnabout is Fair Play

Of course, if Ops should have a seat on Dev teams, what about the converse? Should Dev have a seat in Ops? We'll explore that in our next article. Stay tuned!

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

### Like This Article? Read More From DZone
