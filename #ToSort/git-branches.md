# Git Branches

_Captured: 2018-04-26 at 15:48 from [dzone.com](https://dzone.com/articles/git-branches-1?edition=376204&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202018-04-26)_

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278435&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278435&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))

In the current era, most software development companies work in a **collaborative environment** where several developers contribute to the same source code. While some will be fixing bugs, others will be implementing new and different features. The problem arises, how do you maintain different versions of the same code base?

This is where the **branch function** shines! Branch allows each developer to **isolate** his/her work from others by creating a new branch from the original code base.

## What Is a Branch?

Branch is an independent line of development. It works as a **pointer** to your next commits. Whenever a [new branch](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging) is created, Git creates a new pointer while keeping the original code base untouched.

When you make your **first commit** in a repository, Git will automatically create a **master branch** by default. Every next commit you make will go to the master branch until you decide to create and switch over to another branch.

## Creating Branches

Let's start with [creating a new branch](https://kolosek.com/git-commands-tutorial-part2/): `git branch hello-world`.

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/e7024eeebf14e60d1ef085e26a54c7ff/git-branch.png)

> This only creates the **new branch**. To start working on it, you will need to switch to the branch with `git checkout`. Now, you are ready to use standard `git add` and `git commit` commands.

You can see two different branches pointing to the same commit. How does Git know which branch is currently checked out? This is where the **HEAD pointer** comes into play!

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/c67bce46b37a3ed035ab3578caae4721/git-branch-head-master.png)

**HEAD** always points to the currently checked out branch or commit. In our case, it is the master. Let's `git checkout hello-world` and see what happens.

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/2e1d719f1b70ee891cea0486f745d8ae/git-branch-head-hello.png)

As you can see, the HEAD is now pointing to the `hello-world` branch instead of master. The next step is to modify some files and [create a new commit](https://kolosek.com/git-branches/\(https://kolosek.com/git-commands-tutorial-part2/\)) with `git commit -m "commit message"`

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/0b7f7d3500d892133946f6f05109ebca/git-branch-new-commit.png)

A **new commit (C5)** was created in the branch `hello-world`. Pointers always move to the latest commit in that branch that we checked out. Changes in the `hello-world` branch did not affect any other branch. Branching enables you to isolate your work from others.

> _It is a common practice to create a new branch for **each task** (e.g. bug fixing, new features, etc), which is a good practice because it allows others to easily identify what **changes** to expect, and also for backtracking purposes to understand why a particular code change is implemented._ You can read more at [Git Beginner's Guide for Dummies](https://backlog.com/git-tutorial/stepup/stepup1_1.html).

Create your own **Ruby on Rails** project and try it out! Make [RSpec tests](https://dzone.com/articles/rails-rspec-setup-1) on a different branch and commit the changes.

## Detached HEAD

As we said before, HEAD always points to the currently checked out branch or commit. **Checkout** to a commit and see what happens with `git checkout C0`.

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/7cb2c78e7074fe052eb153b19907c4b2/git-branch-checkout-commit.png)

Now, the HEAD is pointing to `C0`. We are currently checked out to a remote branch. Is it possible to create a new commit while checked out to one? Time to find it out! `git commit -m "commit message"`

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/9088288889fb85fbf6a1c895bb2c53dc/git-granch-head-detached.png)

The HEAD is detached and moves together with each new commit created. The newly created commit `C6` is pointing to `C0`, that is now acting like a branch, but it is not.

> **Commits** that are not reachable by any branch or tag will be garbage collected and removed from the repository after 30 days.

To avoid this, we simply need to create a new branch for the newly created commit and checkout to it using the following command: `git checkout -b hotfix C6`.

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/d617a0d49810d7489e9a7cc75c59ab03/git-branch-hotfix.png)

Always use branches when you are solving new problems to avoid disturbing your co-worker's features!

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278436&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278436&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))
