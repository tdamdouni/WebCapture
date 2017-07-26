# Cracking the Code Review, Part 2: Tips for Reviewers

_Captured: 2017-03-14 at 18:44 from [dzone.com](https://dzone.com/articles/cracking-the-code-review-part-2-tips-for-reviewers?edition=283881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-14)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

[Previously](https://www.lucidchart.com/techblog/2017/02/08/cracking-the-code-review-part-1-preparing-your-code-review/), we discussed ways that you can maximize the success of the code reviews you request from your peers. However, preparing a good code review is only half of the story. There is a lot you can do as a reviewer of code reviews to make your review as helpful as possible.

## 1\. Be Timely in Handling Reviews

Performing a review is time-consuming, so it's understandable why we might prefer to procrastinate and stay focused on our own work for a time. However, the feedback cycle of code reviews can take a long time, and the last thing you want is to be the bottleneck in that process. Delaying a review can make the developer have to do their own context-switching when you do finally point out things to change. If it takes too long, the changes could start to become less and less in sync with the target branch. We're all busy, but we also owe it to each other to be responsive when giving code reviews.

Key habits:

  * Begin leaving feedback within 24 hours, even if you can't review everything in one sitting.
  * Strive for "Inbox Zero" days when all pull requests have been reviewed.

## 2\. See the Code in Action

Remember, the computer is a better compiler than your mind will ever be. Let your build tools have a pass over the developer's code to catch any regressions or tedious errors. If reasonable, check out the code yourself and toy around with it for a bit. Ask the developer what specific features you should be testing and interacting with if you are not familiar with the changes.

Key habits:

  * Ensure builds pass.
  * Check out the branch and test locally.
  * Ask for in-person demos or reviews for complex pull requests.
![](https://d2slcw3kip6qmk.cloudfront.net/marketing/blogs/chart/image01.jpg)

_Always make sure the code works as part of your review. To save time, you can review it on the original developer's machine so you don't have to switch branches._

## 3\. Don't Be Afraid to Hold the Developer Accountable for Quality

Every organization has standards in their code and software. As the reviewer, you are just as responsible as the developer for ensuring that those standards are understood and adhered to. Pay attention to these details and don't be afraid to point out the tiny errors in the code. Help your fellow developers learn to become familiar with and follow coding guidelines. Consider utilizing automated methods to enforce quality, such as automated code linters.

Key habits:

  * Ensure code is self-documenting and stylistically accurate.
  * Pay attention to security concerns.
  * Ask the developer to write unit tests.
  * Check if the upstream branch has been merged into the development branch recently.
  * Encourage the use of helpful debugging statements.
![](https://d2slcw3kip6qmk.cloudfront.net/marketing/blogs/chart/image00.jpg)

_Become familiar with your company's quality and style guides so that you can catch common errors in the code you review._

## 4\. Be the Reviewer You Wish You Could Have

Remember, you are reviewing code, not developers. Leave critiques and ask for changes, but don't attack the coder. Be polite and helpful. Be thorough in your reviews and leave good feedback. Strive to be someone whom people look forward to having reviewed their code.

Key habits:

  * Leave helpful feedback in addition to pointing out bugs.
  * Ask questions; prompt discussion and thoughtful analysis.
  * Don't rush your reviews.

With a bit more effort, we can all do our part to give more helpful code reviews, regardless of what our role is in the process. What best practices have you learned about code reviews from giving and receiving reviews?

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
