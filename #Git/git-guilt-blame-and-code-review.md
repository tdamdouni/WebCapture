# Git Guilt, Blame, and Code Review

_Captured: 2017-02-25 at 20:24 from [dzone.com](https://dzone.com/articles/git-guilt-blame-and-code-review?edition=272905&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-25)_

[Bitbucket](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

I've been doing a bit of traveling lately on the second leg of the Getting Git Right tour. It's been a blast meeting so many devs from around the world. It's been particularly incredible to see how much git adoption has grown amongst attendees in the few months since we did the first leg of the tour. When we presented in July, almost all attendees raised their hand when we asked, _"Who's using git?"_

However, there is one low point during every evening that I've hosted: the moment after I ask the question _"Who's doing code review at work?"_

Typically less than half the audience sticks up their hand.

This makes me sad because code review has been incredibly valuable to me during my career. In fact, I would recommend code review over _any_ other practice or technology as the single most effective way to incrementally increase the quality of any given codebase. And the DVCS implementation of code review -- the _pull request_ -- is a particularly amazing tool.

Here are my top three reasons why:

## Better Code

The first reason is pretty obvious: Having developers with different levels of experience, different technical specializations, and different perspectives grokking your code means you have a far higher chance of catching bugs and stemming technical debt - before your code reaches your customers. If you're using pull requests, these issues are caught before your code even hits the main branch, so issues caught in review impact nobody at all. This means that the quality of your codebase and the product that you're shipping goes way up.

## Knowledge Sharing

The second reason is a bit more subtle. Those developers that are reviewing your code aren't just providing you a free service with no benefit to themselves - they're learning too! As a junior developer, sitting on code reviews taught me more about software patterns and libraries than any book that I've read or presentation that I've attended. As a senior developer, code reviews have unlocked a lot of tribal knowledge that is specific to a particular software project or team. Each application has its own stack, patterns, and idiosyncrasies that shape the best way to patch a bug or implement a feature. Code review does a really good job at spreading this information around the team.

## Communal Ownership

The third reason is the most overlooked, but arguably one of the most important for the long term health of your product. If you're a developer, you've probably shipped a bug to a customer at some point. It is a _terrible_ feeling. You see the bug report pop up in JIRA during a triage session, you read the oddly-familiar description with a sinking feeling and realize that the code that **you** authored and shipped is causing a customer (probably _multiple_ customers) a world of pain.

However -- and this is a dirty little secret -- if you're doing code review as part of your development process, that bug is _not your fault_! At least, not _just_ your fault. The formula for developer guilt looks like this:

`g = 1 / n + 1`

If **n** developers signed off on the review, you only feel **1 / n + 1** the shame when you ship a bug.

I am (sort of) kidding. But more practically speaking, if **n** developers have signed off on a review, then you have **n** developers who can jump in and fix the bug if the original author has left the company / is asleep in another timezone / whatever, while you have customers wide awake and screaming down the phone or on your issue tracker.

So those are the three top reasons why I think code review is good practice for a team of any size greater than one. This segues nicely into the main reason I'm writing this blog post! I recently released a little tool for making code review (with git) an easier process.

One of the tricky parts of creating a pull request is determining the perfect set of people to review your code. Sometimes it's obvious. If you work on a small team or you've been on the same team for a while, you know who the relevant domain expert is for the part of the codebase you've modified. But if you're new to a team, work with a large number of people or are contributing to a project outside of your regular work, the decision may be a little trickier.

## Introducing... Git-Guilt

`git-guilt` is a little tool I wrote that lets you see the transfer of blame in a repository caused by a range of commits. For example, if you wanted to see how blame shifted from one author to another during your last commit, you can run the command:

![Terminal — bash — 98×28 2014-07-17 18-17-48 2014-07-17 18-49-07](https://www.atlassian.com/dam/jcr:69e0439c-6b73-438b-aa7e-c92fbb8a0434/terminal-109.png)

The output indicates that in my last commit I added 239 lines of code, at the same time removing two lines previously attributed to Patrick, five lines from Seb, 13 lines from Anders, and a whole bunch of lines from JD. This is kind of fun if you're competitive by nature, but more practically speaking, the developers that appear in the output are good candidates to review the pull request that I'll create to merge these changes back to the master branch.

The logic behind this is that the developers whose code you're rewriting may have something to say about the matter.

`git-guilt` is named so because it shows the transfer of blame (or _guilt_) of a codebase between commits. Like other commands in the git suite, it can take any commit or ref as an argument. For example, using the `merge-base` command to determine the branch point, you can show the blame of an entire feature branch like this:

![Terminal](https://www.atlassian.com/dam/jcr:ea69c7a5-771c-47fc-aa06-57170e7b8ca0/terminal-157.png)

> _Or the blame change over a period of time:_

![terminal](https://www.atlassian.com/dam/jcr:0c4e34fe-f334-4c85-9a52-316cddb0d33e/terminal-600.png)

## Installation

`git-guilt` is packaged as an npm module, so installation is easy if you want to give it a whirl:

  * Make sure you have Git, Node.js and npm installed.
  * Run `npm install -g git-guilt` (you may need sudo).
  * Run `git-guilt HEAD~1` in any git repository to see the blame delta for the most recent commit. You can also easily install it as a `post-commit`hook, to show the live transfer of code blame as you create new commits locally. Just echo the following to `.git/hooks/post-commit`:

And make sure the file is executable:

The next time you commit, you'll see the git-guilt output showing how the blame has changed.

![Fix it profile](https://www.atlassian.com/dam/jcr:cc5b0f16-f2f1-43ed-be39-5ddead331e44/fix-it-profile.png)

The source is up on [Bitbucket](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=git-guilt-blame-and-code-review&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) if you'd like to peruse or contribute.

## Bitbucket Server fan?

If you find this useful and you're using [Bitbucket](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=git-guilt-blame-and-code-review&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) Server for git hosting, you may enjoy the free [Bitbucket](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=git-guilt-blame-and-code-review&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) Server Reviewer Suggester add-on that I built for a ShipIt competition a while back. It implements a similar algorithm for suggesting reviewers (with a couple of embellishments) and is nicely integrated in the [Bitbucket](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=git-guilt-blame-and-code-review&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) Server Pull Request creation UI.

## P.S. I'm Serious

If you're one of the 50% of developers that reads this that aren't practicing code review, **start today**. You won't regret it! You could have caught a bug (and saved multiple customers pain) _and_ learned various new things about your codebase in less time than it took to read this blog post.

[Bitbucket is the Git solution](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)
