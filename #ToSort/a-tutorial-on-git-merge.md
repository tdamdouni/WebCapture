# A Tutorial on Git Merge

_Captured: 2018-05-02 at 19:49 from [dzone.com](https://dzone.com/articles/a-tutorial-on-git-merge?edition=377199&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-05-02)_

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278435&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278435&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))

Isolating **features** into different branches is a crucial practice for any serious developer. By separating each feature, bugfix, or working experiment, you will avoid a lot of problems and keep your development branches clean.

At some point, a piece of code will reach a state where you'll want to integrate it with the rest of the project. This is where the **git merge** command comes in.

## Preparing to Merge

Let's assume that we want to [merge ](https://dzone.com/articles/git-commands-tutorial-part-2)**branch hotfix** into your **master branch**.

Before we start, how do you make sure that you are ready to merge your changes?

  1. Check if your local repository is up to date with the latest changes from your remote server with a `git fetch`.
  2. Once the fetch is completed, use the `git checkout master` command.
  3. Ensure the master branch has the latest updates by executing `git pull`.
  4. Checkout to the branch that should receive the changes, in our case that is master.

## Merging

Once the **preparations** are completed, you can start the merge with the `git merge hotfix` command.

### Fast Forward Merge

A **fast-forward merge** can occur when there is a linear path between [branches](https://dzone.com/articles/git-branches-1) that we want to merge. If a master has **not diverged**, instead of creating a new commit, it will just point the master to the latest commit of the hotfix branch. All commits from the hotfix branch are now available in the master branch.

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/f16f8fab3708f8cc7a3c05ffe237d87d/git-merge-fast-forward.png)

However, a **[fast-forward merge](https://sandofsky.com/images/fast_forward.pdf)** is not possible if the branches have diverged. In this case, you want to use a **Three-way merge**.

### Three-Way Merge

When there is not a linear path to the target branch, Git has no choice but to combine them via a **three-way merge**. This merge uses an extra commit to tie together the two branches.

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/05519eb0e9dfe087a82f55caa32d54d5/git-merge-three-way-merge.png)

> Test this out! Create your own project with an [RSpec test](https://dzone.com/articles/rails-rspec-setup-1) branch and at the same time edit the [Controller tests](https://dzone.com/articles/rspec-rails-controller-test) in master. Now, try to merge.

## How to Deal With Merge Conflicts

A **merge conflict** occurs when two branches you're trying to merge both changed the same part of the same file. When this happens, Git won't be able to figure out which version to use.

For example, if the file `example.rb` was edited on the same lines in different branches of the same Git repository or if the file was deleted, you will get a **merge conflict error** when you try to merge these branches. Before you can continue, the merge conflict has to be resolved with a **new commit**.

[Merge conflicts](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging) will only occur in the event of a 3-way merge.

  1. **Generate a list** of the files which need to be resolved: `git status`
  2. When the **conflicted line** is encountered, Git will edit the content of the affected files with **visual indicators** that mark both sides of the conflicting content. These visual markers are:
    * `<<<<<<<`\- **Conflict marker**, the conflict starts after this line.
    * `=======` \- **Divides** your changes from the changes in the other branch.
    * `>>>>>>>` \- End of the conflicted lines.
  3. Decide if you want to **keep** only your hotfix or master changes, or write a **completely new** code. Delete the conflict markers before merging your changes.
  4. When you're ready to merge, all you have to do is run the `git add`[command](https://dzone.com/articles/git-commands-tutorial-part-2) on the conflicted files to tell Git they're resolved.
  5. Commit your changes with `git commit` to generate the merge commit.

Hope this helped you get a better understanding how to merge your branches and deal with conflicts.

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278436&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278436&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))
