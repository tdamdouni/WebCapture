# The Definition of Done Is Key to Releasing Better Apps

_Captured: 2017-04-23 at 10:16 from [dzone.com](https://dzone.com/articles/definition-of-done-is-key-to-releasing-better-apps?edition=292908&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-22)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

Do you know what's in your definition of done? Do you have a shared understanding of what is needed by your team to scale DevOps? Do you know what your users expect before you call that feature complete?

## **The Goal: Move Fast, Close Well**

At the heart of app development is the user story, a discrete statement of a goal. User stories translate to capabilities, features, and eventually code changes. When written clearly, these stories can quickly transition from plan to product.

Velocity depends on how many stories you can ship, not how many you can start. Only code that is marked as 'done' can be released, and only code that is released impacts the user.

It doesn't matter if you are 'agile', whether you 'do DevOps' or practice lean principles; work management practices are only productive when they ensure that work is closed. Declaring a feature 'done-done' or 'ready for release' infers that it meets expected factors of completeness, but what are those factors?

## **The Problem: Incomplete Definition of Done Means Incomplete Work**

When a user story is unclearly written or incomplete, work can suffer. In a recent report, Gartner highlights the problem posed to team velocity by an incomplete definition of done:

"Unless there is a clear understanding of what needs to be completed in order for each story to be considered done, this system will break down. As a result, there may be insufficient visibility into how much work has been completed and the real state of the evolving product," says Nathan Wilson in "[Avoid Chaos in Agile Development by Defining When a Story Is 'Done.'"](https://www.gartner.com/doc/3664332?ref=AnalystProfile&srcId=1-4554397745)

When Agile teams don't carefully define which minimum, viable artifacts should result from user stories up front, velocity can suffer. Beyond simply slowing progress on new work commitments in daily standups, defects and rework can fall out of an incomplete definition of done.

## **The Impact: Visibility and Confidence Over Release Readiness**

As you read this, you may be relating this concept to feature-level work; however, reinforcing your definition of done also directly enables visibility over release readiness. Development and product managers who have confidence in the quality of work included in release-ready branches can more flexibly make decisions about when to ship.

A clear definition of done also helps teams to anticipate the need to exclude a feature from holding up a scheduled release when that work proves difficult to close on time.

## **The Strategy: Maturing Your Definition of Done**

Agile and DevOps teams work better when the team is aligned on goals and knows how to accomplish them. A predefined set of expectations over how to close work helps everyone maintain alignment and velocity measured in story points. To ensure that stories are complete, many software teams maintain a 'definition of done' which covers:

  * Functional, non-functional, and acceptance criteria.
  * Peer code review before merges.
  * Automated testing.
  * Deployment audit trail.
  * Documentation for users.

## **The Tactics: Lightweight Reinforcement Mechanisms**

Artifacts are only a way to measure the results of work; encouraging the right work to occur requires us to expand beyond the outcome-based view of a definition of done.

As stories are groomed by product owners and developers, work estimates must incorporate these outcomes or risk being inaccurate. To prevent this, embedding the right criteria in your stories ensures that teams agree to what 'done' means up front, before any code is cut. Here are a few examples:

#1: Add non-functional criteria to your user stories.

In a recent survey conducted jointly by Smith's Point Analytics and Perfecto, we found that high-velocity teams (releasing at least every few days) include performance criteria on 50% more stories than those of teams releasing much slower. A similar trend emerged related to acceptance criteria and UI testing, but the biggest theme was "state expectations up front to reinforce good work outcomes".

For instance, instead of leaving performance testing to a stabilization cycle, include a statement of expectation over latency in the story...something like: "As a sales manager, I want to retrieve lead contacts quickly so that I can reference their colleagues during calls."

The "quickly" should then be defined (for instance as "results appear in under 2 seconds") within the description of the story, thus requiring developers to prove that this criterion is met in their work before marking it as 'done'. For mature teams, this often means writing a performance assertion which can be automated, verified in regression testing, and even used in production monitoring.

#2: Ensure code flows through a safe promotion process.

Once code is developed and tested at an individual workstation, it is ready for production, right? Wrong. Many DevOps teams trigger validation, automated testing, and peer code reviews as part of the process of code promotion to production. Every team and product are different, so the timing and the depth of these checkpoints vary, but defining what is required in the process up front helps developers focus on code.

Feature work done on branches should be merged to a main development branch. This allows you to require peer code reviews at the right times, triggered by pull requests to merge work branches. Only after work on the development branch is fully approved for release should it be merged to a release branch.

This structure allows teams to work without fear and allows for a proper permissions scheme to ensure that no one developer unintentionally releases incomplete work.

#3: Define the timing and broadness of your feedback loops.

In [our prior research](http://info.perfectomobile.com/developers-primer.html), we highlight the need to fit test execution speeds to short development cycles to provide fast feedback loops to developers. Not everyone is set up to run every test on every build; in fact, sometimes less is more, in that getting the right feedback early can avoid disrupting later regression testing and delaying releases.

At the developer workstation, running unit and UI testing scoped to feature work can capture issues with individual contributions. When properly annotated, resulting automation tests can be used in sidelined processes like build verification testing triggered by code check-ins. An even broader set of tests can be run before and after merges. The point is, test execution depends on how many tests you run, not just how long the tests take to execute.

Many mobile and web app teams also define a limited set of devices and platforms to validate feature work on before committing code to a feature branch. A larger pool of devices is also defined for build verification testing in continuous integration. Finally, a complete coverage list is maintained for regression and manual acceptance testing cycles. Defining these sets of devices based on analytics and marketing data ensures that you catch the most impactful defects as early as possible.

## **The Next Step: Try, Learn, Adjust**

Take one tactic from above and put it into practice. Start small, think lean when including things in your definition of done; less is more with patterns that apply to each story. Apply it to a few feature branches across one or two releases so that you can measure retrospectively against other release lines. And don't forget to let us know how you fit it to your own process in the comments below. Also, check out this [whitepaper](https://www.perfectomobile.com/ni/resources/papers/cfp-ebk-expand-quality-build-cycle-ebook) on how using the Agile approach can help expand quality into your build cycle.

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
