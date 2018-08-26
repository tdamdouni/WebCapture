# Git Merge vs. Rebase

_Captured: 2018-05-31 at 19:41 from [dzone.com](https://dzone.com/articles/git-merge-vs-rebase?edition=380202&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-05-31)_

Sharing his pioneering insight on how organizations can transform their software development and delivery processes, Gary Gruver provides a tactical framework to implement DevOps principles in _Starting and Scaling DevOps in the Enterprise_. [Get your free copy](https://dzone.com/go?i=295422&u=https%3A%2F%2Fabout.gitlab.com%2Fresources%2Fscaling-enterprise-devops%2F%3Futm_medium%3Dwebsite%26utm_source%3Ddzone%26utm_campaign%3Dpreroll%2Bpostroll).

**Git merge** and **rebase** serve the same purpose - they combine multiple branches into one. Although the final goal is the same, those two methods achieve it in different ways. Which method to use?

## What Does Merge or Rebase Mean?

Here we have a sample repository that has two [diverging branches](https://kolosek.com/git-branches/): the master and the feature. We want to blend them together. Let's take a look how these methods can solve the problem.

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/fc73a41ce658a6a566e2a54d60534ade/git-flow.png)

### Merging

When you run `git merge`, your HEAD branch will generate a **new commit**, preserving the ancestry of each commit history.

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/673b91456bdc6fd454c5ad203f825568/git-merge-2.png)

[Fast forward merge](https://kolosek.com/git-merge/#fastforwardmerge) is a type of merge that doesn't create a commit, instead, it updates the branch pointer to the last commit.

### Rebasing

The **rebase** re-writes the changes of one branch onto another _without_ creating a new commit.

For every **commit** that you have on the [feature branch](https://kolosek.com/git-branches/) and not in the master, a new commit will be created on top of the master. It will appear as if those commits were written on top of master branch all along.

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/5ade4f7276bc6ad18dad4b6078950ac9/git-rebase.png)

## Merging Pros and Cons

### Pros

  * Simple to use and understand.
  * Maintains the original context of the source branch.
  * The commits on the source branch are separated from other branch commits. This can be useful if you want to take the feature and [merge](https://kolosek.com/git-merge/) it into another branch later.
  * Preserves your commit history and keeps the history graph semantically correct.

### Cons

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/c8b97f4dbb5f7d49fc3eb3624eafff79/london-tube-map-commit.png)

## Rebasing Pros and Cons

### Pros

  * Code history is simplified, linear and readable.
  * Manipulating a single commit history is easier than a history of many separate feature branches with its additional commits.
  * Clean, clear **commit messages** make it better to track a bug or when a feature was introduced. Avoid polluting the history with 20+ single-line commits!

### Cons

  * Lowering the feature down to a handful of commits can hide context.
  * Rebasing doesn't work with **pull requests**, because you can't see what minor changes someone made. Rewriting of history is bad for teamwork!

You need to be more careful with rebasing than when merging.

## Which Method to Choose?

When your team uses a feature based workflow or is not familiar with rebase, then `git merge` is the right choice for you:

  * It allows you to preserve the commit history for any given feature while not worrying about overriding commits and changing history. It helps you avoid unnecessary [git reverts or resets](https://kolosek.com/git-reset-revert-and-checkout/)!
  * Different features remain isolated and don't interfere with existing commit histories.
  * Can help you re-integrate a completed feature branch.

On the other hand, if you value more a clean, linear history then `git rebase` may be most appropriate. You will avoid unnecessary commits and keep changes more centralized and linear!

If you rebase incorrectly and unintendedly rewrite the history, it can lead to serious issues, so make sure you know what you are doing!

Sharing his pioneering insight on how organizations can transform their software development and delivery processes, Gary Gruver provides a tactical framework to implement DevOps principles in _Starting and Scaling DevOps in the Enterprise_. [Get your free copy](https://dzone.com/go?i=295423&u=https%3A%2F%2Fabout.gitlab.com%2Fresources%2Fscaling-enterprise-devops%2F%3Futm_medium%3Dwebsite%26utm_source%3Ddzone%26utm_campaign%3Dpreroll%2Bpostroll).
