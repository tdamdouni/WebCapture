# Git: To Squash or Not to Squash?

_Captured: 2017-09-08 at 14:37 from [dzone.com](https://dzone.com/articles/git-to-squash-or-not-to-squash?edition=324395&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202017-09-08)_

[Download the blueprint](https://dzone.com/go?i=228233&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) that can take a company of any maturity level all the way up to enterprise-scale continuous delivery using a combination of Automic Release Automation, Automic's 20+ years of business automation experience, and the proven tools and practices the company is already leveraging.

Until recently, I told my team to squash all of their commits on a given feature branch to just one commit. Every feature branch consisted of just this one commit and could be integrated into develop so that develop reads just like a sequence of features. After further consideration, I changed that. Here are reasons for both approaches:

## Pro-Squash

  1. Clean timeline: Development of features is clearly visible because every commit is a feature.
  2. Commits representing work in progress (WIP) broke builds on CI-server.
  3. WIP-commits prevented "jumping a month into the past" for debugging and exploratory purposes because they are potentially broken (compile errors, failing tests).

## Anti-Squash

  1. If feature branches are merged, a merge commit is created that represents the development of a feature.
  2. Tools like Git Bisect are much more powerful when dealing with small commits.
  3. In IDEs like IntelliJ IDEA, feature branches in the Git history can be collapsed to provide a better overview.
  4. Small tasks are better visible. For example, small bugfixes tended to be fixed in bigger feature branches, just to be never found again. "Yeah, this got fixed somewhere, but I don't know where"-syndrome.
  5. Every commit causes the CI-server to build. The more (pushed) commits, the more builds, the faster feedback if something went wrong.

To get the most out of the new strategy, each commit must

  1. Compile and run green (all tests), AND

Furthermore, really small commits may be merged with a fast-forward-merge/rebased onto develop.

Also, commits that represent a quick-WIP-save have to be edited in retrospect and provided with a good commit message. This is the last remaining situation in which a squash is allowed.

[Download](https://dzone.com/go?i=228234&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) the 'Practical Blueprint to Continuous Delivery' to learn how Automic Release Automation can help you begin or continue your company's digital transformation.
