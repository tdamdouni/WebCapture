# 5 Elements of a Perfect Pull Request

_Captured: 2017-07-29 at 20:00 from [dzone.com](https://dzone.com/articles/5-elements-of-a-perfect-pull-request?edition=311401&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-07-29)_

Learn how our [document data model](https://dzone.com/go?i=225226&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-3%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3D1%26jmp%3Ddzone-ad) can map directly to how you program your app, and native database features like secondary indexes, geospatial and text search give you full access to your data. Brought to you in partnership with [MongoDB](https://dzone.com/go?i=225226&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-3%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3D1%26jmp%3Ddzone-ad).

Raise your hand if you remember the days of in-person code reviews. You may recall entire afternoons spent checking out changes from SVN, running them locally, and making notes of areas that could be improved. Next, you'd spend another hour or two in a room with your team discussing suggestions live. Once changes were incorporated, the whole process would begin again until it was finally time to merge. Ah merging… never fun and often times a total nightmare.

Quality time with the team is great and all, but we sure are glad those days are over. Thanks to the rise of distributed version control (DVCS), like [Git](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content), the peer feedback process has vastly improved. [Git's ability to branch and merge easily](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) has made it possible to review smaller sets of changes more often. This type of code review is based on a concept known as pull requests. Pull requests provide a forum to discuss proposed changes to your codebase before they're merged into shared branches (e.g. before merging a feature branch into master).

![bitbucket411-blog-1200x-branches2](https://atlassianblog.wpengine.com/wp-content/uploads/bitbucket411-blog-1200x-branches2.png)

The popularity of [Git](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) and pull requests have been growing exponentially with no signs of slowing down. The benefits of peer review - higher quality code, shared team knowledge, shared sense of ownership - and [flexible workflows in Git](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) have lured teams of all sizes. Amadeus, one of our largest customers, employs over 5,000 developers. Since they made the switch from SVN to Git three years ago, pull requests have become an invaluable tool to protect against poor quality code.

With development speed and code quality at stake, it's no surprise that pull requests have become a key selling point for [Git management tools.](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) Of course, other factors are at play, like security, scalability, and deployment flexibility, but when it comes to developer productivity it's the pull request experience that will set one tool apart from the others. We believe the pull request experience is THE most important deciding factor when selecting a version control solution. They are the best way ensure you're releasing the highest quality code possible.

In talking with teams among our 60,000 customers, and of course our experience as developers, we have found that pull requests work best when five key pieces of functionality are in place. Let's take a look at these areas and how [Bitbucket Server](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) provides them.

## **1\. Assigned Reviewers**

In their most basic form, pull requests are simply a request to merge changes into a destination branch or fork. Once you introduce the idea of adding reviewers, they become much more than that - a forum for open discussion around code. When you're looking at a tool to manage your Git repositories, the ability to explicitly add your team members as reviewers is the basis for a sound review workflow. How else will your team know they need to review your changes?

In [Bitbucket Server](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content), we make the process even smoother by giving you the option to set up default reviewers for specific types of branches (i.e. feature, hotfix, or bugfix). You also have the ability to use Marketplace add-ons for additional functionality, like the [Bitbucket Server Reviewer Suggester](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content).

![bitbucket411-blog-1200x-reviewers-1](https://atlassianblog.wpengine.com/wp-content/uploads/bitbucket411-blog-1200x-reviewers-1.png)

## 2\. Comment on ALL THE THINGS 

What good would a code review be without the comments? Capturing feedback in-context gives pull request authors a reference point for enhancements. Reviewers can make suggestions for changes, or congratulate their team member on a brilliant piece of logic.

In [Bitbucket Server](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) you have the option to leave all types of comments: on the entire pull request, commit by commit, on a particular file, or on specific lines of code in a file. Every developer has their preferred way to read and review code, so your tool should cater to everyone.

![bitbucket411-blog-1200x-comments](https://atlassianblog.wpengine.com/wp-content/uploads/bitbucket411-blog-1200x-comments.png)

**Pro tip**: Need a second opinion on a specific section of code? In [Bitbucket Server](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content), you can use an @mention on a particular line to bring in a busy specialist (e.g. front-end ninja, performance engineer, security expert) to review something in particular without saddling them with the whole review.

## 3\. Iterative Review

Pull requests create a feedback loop - you write some code, your team reviews, you incorporate changes, your team reviews and approves them, you merge, and then you're done. If your [Git management tool](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) doesn't provide a mechanism to capture reviewer status or review iterations, how are you supposed to keep track?

In [Bitbucket Server](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content), we solve this problem by providing status buttons for reviewers (i.e. if the author needs to make changes you can click "Needs Work"). Once changes have been incorporated, reviewers can easily find what's new via iterative review, a mechanism allowing you to constrain the diff to only new changes since you last reviewed. No need to hunt through files for changes or re-review old code. If your team cares about spending their time wisely, then iterative review is a [Git](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) tool must-have.

![bitbucket411-email-1160x600-iterative](https://atlassianblog.wpengine.com/wp-content/uploads/bitbucket411-email-1160x600-iterative.png)

## 4\. Workflow Flexibility

The creation of a development workflow involves a lot of factors. For example: Do you work in a highly regulated industry? Who should have access to your codebase? What types of quality checks do you need? The list goes on. This is why workflow flexibility is so important; no two development teams are exactly alike.

In [Bitbucket Server](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) we give you the freedom to pick _how _a pull request is merged (available merge strategies include merge commit, fast forward only, and squash) and _when _it is merged with merge checks (e.g. only allow merges if there are 2 approvals and a passing build). No other Git tool rivals the flexibility found in [Bitbucket Server](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content). We give you the power to decide how you want to work, not the other way around.

![bitbucket411-blog-1200x-merge](https://atlassianblog.wpengine.com/wp-content/uploads/bitbucket411-blog-1200x-merge.png)

## 5\. Integrations

Finally, before purchasing a brand new [Git management tool](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content), consider how it will fit in with the rest of your toolchain. Development is way more fun when you don't have to jump between tools to report on pull request status. With thoughtful integrations like smart commits, the ability to transition JIRA issues via commit messages, [Bitbucket Server](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) handles the overhead for you. Save time and keep everyone up to date with first-class JIRA Software, HipChat, and Bamboo integrations. Using other tools? [Atlassian provides a Marketplace full of additional integrations and functionality through add-ons](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=5-pull-request-must-haves&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content). Why settle for a "jack-of-all-trades" tool when you can combine the power of best of breed tools that work for you?

![bitbucket411-blog-1200x-devpanel](https://atlassianblog.wpengine.com/wp-content/uploads/bitbucket411-blog-1200x-devpanel.png)

## The Right Choice for Your Team

Peer feedback reduces the number of bugs in your code. It's a safety net for developers, a way to ensure you're putting out the highest quality code you can. At the end of the day, your customers only care if your product works for them or not. That's why code review and pull requests are so important when selecting a Git management tool. This process cannot fail you.

Discover when your data grows or your application performance demands increase, [MongoDB Atlas](https://dzone.com/go?i=225227&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-3%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3D2%26jmp%3Ddzone-ad) allows you to scale out your deployment with an automated sharding process that ensures zero application downtime. Brought to you in partnership with [MongoDB](https://dzone.com/go?i=225227&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-3%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3D2%26jmp%3Ddzone-ad).
