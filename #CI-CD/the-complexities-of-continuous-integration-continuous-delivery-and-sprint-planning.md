# The Complexities of Continuous Integration, Continuous Delivery, and Sprint Planning

_Captured: 2018-01-26 at 18:21 from [dzone.com](https://dzone.com/articles/the-complexities-of-continuous-integration-continu?edition=355142&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-01-26)_

[Learn more](https://dzone.com/go?i=250324&u=http%3A%2F%2Fblog.scalyr.com%2F2017%2F08%2Fcareerbuilder-resolves-customer-issues-5x-faster-scalyr%2F) about how CareerBuilder was able to resolve customer issues 5x faster by using Scalyr, the fastest log management tool on the market.

[This article is featured in the new DZone Guide to DevOps. Get your free copy for more insightful articles, industry statistics, and more! ](https://dzone.com/guides/devops-culture-and-process)

Continuous Integration (CI) and Continuous Delivery (CD) are complementary development processes that allow product teams to continuously release new software. Continuous Integration is the practice of frequently merging code to a central shared repository, triggering automated builds and tests. Similarly, Continuous Delivery is the practice of frequently releasing software in short cycles, typically by automating deployment builds and harnessing a CI pipeline. In practice, these development processes work together to allow teams to build, test, and deploy their code rapidly, reliably, and repeatedly.

The origins of both CI and CD can be traced back to Agile methodology, which is an iterative and incremental method of product development that focuses on collaboration and continuous releases. The backbone of Agile is the Scrum framework, a form of software development management that focuses on building products that fit business needs. Scrum breaks actions into time-boxed iterations called Sprints, which are timed intervals that break down work into manageable tasks. Sprint planning sessions are held to agree on the scope of work and includes work that needs to be completed for product backlog items. However, implementing CI and CD in an Agile-driven organization is one of the greatest challenges facing organizations.

As we have seen, the success of DevOps entirely depends on company culture. Internal teams must be able to adopt cross-functional methods to make sure software is iterated with a continuous cadence but also complements marketing and sales campaigns. Seeing how CI/CD are major components of the DevOps ecosystem, they are not excluded from this culture factor. The product that comes out of the CD pipeline needs to suit the needs of the organization. Otherwise, those who are not part of the deployment team will never support Continuous Integration efforts. This is where Sprint planning comes to the rescue.

## Sprint Planning

Sprint planning typically consists of fixed length Sprints of one, two, or four weeks. In these periods, teams set specific goals and tasks they wish to accomplish. This helps the organization and teams prioritize features to release. Teams can also parallelize feature development by allowing multiple teams to develop complementary features and then use CI/CD to merge, test, and deploy. CI and CD are development processes that free Sprint planning of artificial process constraints. For CI, code is merged frequently and errors are caught before deployment builds take place. For CD, production-ready code can run through automated deployment builds for fast releases and user testing. Both of these processes enable development teams to keep pace with their Sprint cadence.

## Best Practices

To ensure your CI and CD pipelines are properly configured, here are some best practices: An effective Continuous Integration pipeline embraces:

  * Everyone takes responsibility for the CI build.

  * Every team member knows how to check the CI build results.

  * If the CI build breaks, teams work together to figure out who should fix it.

A performant Continuous Delivery pipeline embraces:

  * Teams taking ownership of the process.

  * Monitoring and measuring.

  * Reacting to problems quickly.

A good Sprint planning meeting allows teams to:

  * Discuss problems and readjust for the next sprint cycle.

  * Build in time that allows teams to monitor and measure their progress.

  * Respect and listen, but also ask, "Why?"

## Regression Testing

Regression testing is one way of the best ways to tackle these best practices. Regression testing verifies that previously developed software still performs after being changed or interfaced with new software. Ideally, teams should perform regression testing every few Sprint cycles and not towards the end of a project. Teams should discuss during Sprint planning sessions when regression tests should occur in their Sprint process. Teams should find tools that allow them to create automated regression tests versus manually testing every few Sprint cycles. It's much less of a pain to maintain automated regression tests versus assigning team members to run manual tests during Sprint planning sessions.

## Challenges of Sprint Planning and Continuous Delivery

There are also many challenges teams face when conducting Continuous Delivery and Sprint planning together.

### 1\. Culture Adoption

To implement CD and CI, an organization needs to embrace co-ownership of the development process. Typically, there are three main obstacles for culture adoption: (1) resistance from the status quo, (2) resistance to the process, and (3) strict instead of adaptive implementation. CI/CD adoption should be scoped to the organization's needs; there isn't a one size fits all solution. To overcome this, organizations should ensure that their product and business leaders understand the benefits of CI/CD and how it powers better and faster software delivery. New leaders should be cultivated, not appointed.

### 2\. Projects With Ambiguous Scopes

Highly unknown projects can be difficult to deconstruct and prioritize in the development cycle. The risk profile has changed and the teams may not be aware of that. In these situations, good leadership is required to be able to plan for unknowns.

### 3\. External Teams

When working with an external team, your team's resources can be split and their ability to move quickly can be compromised. They may have to focus on other efforts that aren't in line with maintaining the build or properly planning the next Sprint cycle. It's important to maintain a team that manages the CI and CD pipeline when this occurs, making sure it stays optimal until teams that are interfacing with external resources can return. This requires teams to teach the rest of the culture the importance of maintaining CI builds so that whole teams aren't pulled away.

### 4\. Complex Technology Stack

Development stacks are highly complex, typically with multiple layers of software, processes, servers, and API layers. This can make it challenging to build a CD pipeline and Sprint planning structure that addresses these complexities. Frequent tool changes could also leave team members frustrated and constantly chasing dead ends. This lowers team morale, which can have negative impacts on culture. If you build using a tool that is going to be changed in the future, you could lose a lot of progress, which is another way to quickly lower morale.

## Conclusion

Sprint planning powers CD and CI processes by allowing teams to accurately plan and prioritize features that fit the business needs. CD and CI also enable development teams to keep pace with their Sprint cadence and create a product that serves the organization as a whole. To ensure adoption, teams must teach stakeholders the benefits of CI/CD. Sprint planning is one of the best ways to teach stakeholders the benefits of CI/CD by showing them how CD/CI processes help the business.

[This article is featured in the new DZone Guide to DevOps. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/devops-culture-and-process)

**[Find out more](https://dzone.com/go?i=250325&u=http%3A%2F%2Fblog.scalyr.com%2F2014%2F05%2Fsearching-20-gbsec-systems-engineering-before-algorithms%2F) about how Scalyr built a proprietary database that does not use text indexing for their log management tool.**

Topics:

devops ,continuous integration ,continuous delivery ,ci/cd ,sprint planning ,scrum
