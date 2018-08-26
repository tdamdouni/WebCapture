# Technical Debt and Supporting Prior Decisions

_Captured: 2018-08-22 at 09:36 from [dzone.com](https://dzone.com/articles/technical-debt-amp-supporting-prior-decisions?edition=385398&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202018-08-21)_

**Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=291448&u=http%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fagile-test-data-management-the-new-must-have.html%3Fcid%3DNA-DSP-CD-AGJ-000195-00001461-000001106%26utm_source%3Donline_ads%26utm_medium%3Ddzone%26utm_campaign%3Dtdm_acquire%26utm_content%3Dagile_tdm_report-pre_roll). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=291448&u=http%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fagile-test-data-management-the-new-must-have.html%3Fcid%3DNA-DSP-CD-AGJ-000195-00001461-000001106%26utm_source%3Donline_ads%26utm_medium%3Ddzone%26utm_campaign%3Dtdm_acquire%26utm_content%3Dagile_tdm_report-pre_roll). **

Recently, I was asked to attend a session at a large corporation. The room was filled with technology-based executives, development managers, and enterprise architects. Also in attendance were a few of my peers from

Upon leaving this discussion, I found myself wondering just how many other corporations are facing this same dilemma.

## The Situation

The company supports development organizations from multiple business lines. While they saw a significant amount of success in one aspect of their business initially, their focus and profitability have migrated to other aspects of the business, each operating as their own division. These divisions have spawned their own technology component, often utilizing different frameworks to meet the needs of their customers.

Over time, this has led to a heavy burden being placed on the Production Support group within Information Technology. On the web-application support side of the centralized service, the following frameworks are currently being supported: [Apache Struts](https://en.wikipedia.org/wiki/Apache_Struts_1), [JBoss Seam](https://en.wikipedia.org/wiki/JBoss_Seam), [Spring/Spring MVC](https://en.wikipedia.org/wiki/Spring_Framework), [IBM WebSphere Portal](https://en.wikipedia.org/wiki/WebSphere_Portal), [AngularJS](https://en.wikipedia.org/wiki/AngularJS), [Angular.io](https://en.wikipedia.org/wiki/Angular_\(application_platform\)), [ReactJS](https://en.wikipedia.org/wiki/React_\(JavaScript_library\)), [Ember.js](https://en.wikipedia.org/wiki/Ember.js) and a few frameworks that I had not even heard of before the meeting. Clearly, Production Support staff currently feel overwhelmed with trying to keep their skills sharp to support all of these web frameworks.

What further complicates this model is their inability to maintain these solutions, as components require periodic updates or conversions to alternative solutions as a result of end-of-life deadlines. As an example, known vulnerabilities behind Apache Struts (as noted in my "[Equifax Issues Continue -- Technical Debt at the Core](https://dzone.com/articles/equifax-issues-continue-technical-debt-at-the-core)" article) which led to the Equifax corporation situation, are likely exposed at this particular organization.

## Their Suggestion

One of the team members at the host corporation brought up the model employed by [Salesforce](https://en.wikipedia.org/wiki/Salesforce.com) as something that was of great interest to their group. With Salesforce, there are three scheduled releases per year, which are forced upon users of the platform-based service offering. Their hope is that they could utilize the Salesforce platform and the Community Cloud offering as their primary development framework going forward. The thought was to do more configuration than development.

Their suggestion sounded valid, until we started asking questions about the data supporting these applications. While the host company utilizes Salesforce, their usage is somewhat small in comparison to other Salesforce clients CleanSlate Technology Group maintains. Additionally, the applications they were targeting did not have any data within the Salesforce platform. As a result, the Salesforce Community Cloud solution would be acting almost as a proxy to reach out and utilize the necessary data and services required to meet the needs of the business.

## Lotus Notes Flashback

The recommendation reminded me back to the popularity of [Lotus Notes](https://en.wikipedia.org/wiki/IBM_Notes) in the 1990s and early 2000s. At the time, Lotus Notes maintained a majority of the market for email and calendaring. When corporations realized that Lotus Notes had the ability to create databases/applications -- they jumped on the opportunity. After all, there wasn't a difference in licensing costs, the applications were quick and easy to build/deploy, and a web-based front-end was easy to add when browser-based usage became more popular.

Like all technology products, the [Gartner](https://en.wikipedia.org/wiki/Gartner)[Hype-Cycle](https://en.wikipedia.org/wiki/Hype_cycle) effect was employed and by the end of the early 2000s, Lotus Notes popularity exceeded the "Plateau of Productivity" phase.

![Image title](https://upload.wikimedia.org/wikipedia/commons/9/94/Gartner_Hype_Cycle.svg)

At this point, corporations found themselves with a significant number of Lotus Notes applications that needed to be converted to an alternative platform -- without an easy migration path. My worry is that taking the Salesforce Community Cloud approach could leave them in a similar state -- which a challenge of trying to migrate away from the proprietary solution.

## Recommendations

In the end, our team didn't feel comfortable that Salesforce Community Cloud was the right approach to meet their needs. Without going into a lot of details, our discussion quickly pointed out aspects that didn't align well with their expectations -- which would lead to a great deal of customization and maybe even some hacked-based code to meet their needs. To me, taking this approach would lead to an even deeper level of issues by forcing an application to be something it is not intended to be.

Instead, I felt like some changes really need to be made within the organization as a whole with respect to their applications:

  1. **Technical Debt Needs To Be Addressed -- **The successful Agile teams I have been a member of has always set aside 20% of every sprint cycle to address technical debt. What many don't realize is that the technical debt does not have to be related to the application responsible for the other 80% of the sprint workload. In the case of the client, they could focus their efforts on migrating legacy applications to an updated and standardized framework. While this may take more time to complete, it does allow progress to be made when there is no budget to wholesale convert existing applications.

  2. **Governance & Standards** -- Going forward, I recommended that the client organize some level of governance and application standards. While it might be new and exciting to chase the latest frameworks, there is a huge burden being placed on those who have to support differing frameworks. In the case of this client, they could leverage their extensive Java knowledge to handle their API design and focus on a single JavaScript framework for the needs of the front-end client.

  3. **Eat Your Own Dog Food** -- In the current support mode, applications are developed and then passed over to Production Support to handle. There is a preverbal line in the sand to where once the application is deployed to Production, it is out of the hands of the original developers. I have found when a given development team is ultimately responsible for the application they architect and build, the decisions they make around tooling and technologies employed are far more sound than when they are only involved in the initial development effort. For years this has been referred to as "[eating your own dog food](https://en.wikipedia.org/wiki/Eating_your_own_dog_food)" and feel like this client could benefit from such an approach.

## Conclusion

During the on-site meeting there was a comment from a representative from the host company, confessing that they are "_not a software development company_." I have heard this statement many times over the last six months, by three of my current clients. While I understand the rationale for making the statement, I am not convinced that a corporation should avoid maintaining Information Technology staff to handle the needs of the business lines.

In the session I attended, there was talk about making compromises in order to fit into the Salesforce Community Cloud box. However, within that same conversation required features quickly began to explain why a configurable platform was not going to be a valid fit. This is the very reason why frameworks (like Spring, Angular or React) exist in order to meet the needs of unique business models without requiring a great deal of boilerplate code to be created.

Instead of trying to take an extreme case of walking away from custom development, I feel like setting standards and focusing on a given framework will lead the host corporation to better pathway over time. By allocating at least 20% of all development iterations toward migration away from legacy platforms, the catalog of supported applications will slowly begin to diminish. If this timeline is too long, IT staff can seek to procure dedicated funds to expedite the conversion process.

Have a really great day!

**[See how three solutions work together](https://dzone.com/go?i=291449&u=https%3A%2F%2Fwww.ca.com%2Fus%2Ftrials%2Fca-agile-requirements-designer.register.html%3Fcid%3DNA-DSP-CD-AGJ-000195-00001462-000001108%2520%26utm_source%3Donline_ads%26utm_medium%3Ddzone%26utm_campaign%3Dard_acquire%26utm_content%3Dard_trial) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=291449&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=291449&u=https%3A%2F%2Fwww.ca.com%2Fus%2Ftrials%2Fca-agile-requirements-designer.register.html%3Fcid%3DNA-DSP-CD-AGJ-000195-00001462-000001108%2520%26utm_source%3Donline_ads%26utm_medium%3Ddzone%26utm_campaign%3Dard_acquire%26utm_content%3Dard_trial). **

Topics:

agile adoption ,technical debt ,salesforce ,application configuration ,custom development ,javascript frameworks ,api development ,agile
