# How Remote Testers Should Work Together

_Captured: 2017-08-08 at 20:10 from [dzone.com](https://dzone.com/articles/how-remote-testers-should-work-together?edition=310396&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-24)_

"[Automated Testing: The Glue That Holds DevOps Together"](https://dzone.com/go?i=236222&u=http%3A%2F%2Finfo.saucelabs.com%2FAutomated_Testing_Glue_LP-DZone.html%3Futm_medium%3Dpre-roll_textlink%26utm_content%3Darticle) to learn about the key role automated testing plays in a DevOps workflow, brought to you in partnership with Sauce Labs.

Testing is a team sport. From gathering requirements to [prioritizing and planning ](https://testlio.com/blog/7-ways-to-prioritize-more-successfully-during-test-planning/)to dividing and conquering coverage, there are a lot of different people involved from different departments whose work contributes to overall cycle success.

Much has been said about the transition to remote work, and the [53 million American independent workers](https://blog.freelancersunion.org/2014/09/04/53million/). Gone is the idea that "remote" means incommunicado.

With so many collaboration tools on the market, high functioning, high-value remote teams are growing in number.

How does this global business and culture trend affect testing? The use of external software testing services is certainly growing. More testers are able to work remotely than ever before.

Whether you're a QA manager looking to improve collaboration in a remote environment or a tester wanting to up your teamwork skills, these pointers will help you adopt the right mentality and get the right frameworks in place.

## Use the Same Project Language

It's always important for QA and development teams to be using the same project language, but with remote work, it becomes all the more critical since most (or all) of the project communication is written. There's no in-person context. All you have are the words.

When issues are reported in a way that reflects the terminology used by the project and the product itself, then testers can easily search through various communication tools like Slack (and the test management platform) to learn what is being said about a particular feature or area.

QAMs need to clarify the project language up front, and testers need to stick to it. This way everyone can benefit from easily finding and requesting information.

## Avoid Duplicate Issues

A universal project language is very helpful when it comes to avoiding the creation of duplicate issues. Testers should be encouraged to include project terminology in titles and descriptions and to search for existing issues before creating new ones.

One of Testlio's general reporting guidelines is to include the section of the app affected in brackets in the issue title. This makes issues easy to search, and when issues can be found, then they won't be duplicated. When they _can't_ be found, duplication is much more likely.

Testers need to remember to search through closed issues too! Discovering what seems like a new bug may require that you reopen an issue.

## Have Project-Specific Reporting Guidelines

Everyone needs to be on board with the purpose of a test cycle. This is achieved by having a comprehensive test plan for testers to follow and by having a clear project scope that identifies the areas in need of the most attention.

Testlio testers include the following in every bug report:

  * Clear, specific title.
  * Necessary environment details.
  * Steps to reproduce.
  * Expected result.
  * Actual result.
  * Screen recording attachment.
  * Log file attachment.

In addition, we include reporting guidelines for every project. Examples of this would be to only log medium to high priority bugs, to include PNG screenshots of UI bugs in addition to screen recordings, or to include suggestions/requests for only one specific feature and nothing else.

Documenting and sharing these additional guidelines means that the end result of the cycle will be high-quality bugs that contribute to development goals.

## Encourage Collaboration and Sharing

When working together inside of one test management platform, it should definitely be easy for testers to see what issues have and haven't been logged yet. But collaboration during testing isn't just about bug finding.

Testers should also be able to freely discuss:

  * Technical tips and questions.
  * Comments and questions about project scope.
  * Big issues and the product areas/functions they might affect.
  * Strategies for digging deeper into problem areas.

Project-specific Slack channels can be a great place for open communication. So can unique chat rooms for each project, which is how the Testlio test management platform is organized.

![](https://testlio.com/wp-content/uploads/2017/07/project-chat.png)

Testers can help one another out and stay completely up to date on the status of the project. Having a place for open communication has the added benefit of keeping issue logs and their comments tightly focused.

## Make Reproducing Easier

To make sure issue reports are of the maximum use to developers, all of Testlio's logged issues undergo a reproduction attempt by at least one other tester.

When an issue can be reproduced, its root problem can be more quickly discovered by developers. We want to submit reproducible issues as much as possible.

Of course, the way to make issues easy for another tester to attempt to reproduce is to clearly write out the steps and to only include those steps that are relevant to that issue.

For example, a tester should only include a specific user login if that account's data is associated with the error. If the error is likely generic, then logging in as a specific user is a waste of time for the second tester. When in doubt, it's best to keep that additional step, as the second tester can attempt reproduction in different accounts.

We recently added a new commenting template which helps differentiate comments from reproduction attempts, so it's easier to scan through and review the status of those attempts.

![](https://testlio.com/wp-content/uploads/2017/07/issue-is-reproducible-1200x469.png)

## Create Guidelines for Sharing Test Accounts

Sometimes for reproducing purposes, testers need to share test accounts. While it's generally advisable that they only use shared test accounts for reproducing, there may be circumstances where they need to share their main test account because the associated data is necessary for another tester to be able to reproduce the bug.

It's good to have some sort of guidelines in place for sharing accounts so that testers don't trample over each other's hard work and make changes to the account that could affect other aspects of testing. One simple rule is to never make changes to someone else's account and to just log in, repro, and log out.

Whenever possible, it's helpful to have data-rich shared accounts that everyone can freely use.

Collaboration is the lifeblood of quality assurance. Any test cycle is a meeting of minds and requires continued communication to be executed successfully.

Making it easy for testers to work together and encouraging participation leads to higher quality bugs and faster testing. When testers aren't overlapping or duplicating one another unnecessarily, then there's more time for the deep diving that produces valuable testing results. And when they can share project comments and testing tips and tricks, then everyone can grow their skills, and of course…have fun!

[Learn about the importance of automated testing](https://dzone.com/go?i=236223&u=http%3A%2F%2Finfo.saucelabs.com%2FAutomated_Testing_Glue_LP-DZone.html%3Futm_medium%3Dpost-roll_textlink%26utm_content%3Darticle) as part of a healthy DevOps practice, brought to you in partnership with Sauce Labs.
