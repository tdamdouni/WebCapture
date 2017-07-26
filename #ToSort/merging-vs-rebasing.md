# Merging vs. Rebasing

_Captured: 2017-04-11 at 19:50 from [dzone.com](https://dzone.com/articles/merging-vs-rebasing?edition=290882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-11)_

[Bitbucket](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

The `git rebase` command has a reputation for being magical Git voodoo that beginners should stay away from, but it can actually make life much easier for a development team when used with care. In this article, we'll compare `git rebase` with the related `git merge` command and identify all of the potential opportunities to incorporate rebasing into the typical [Git workflow.](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=merging-vs-rebasing&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content)

## Conceptual Overview

The first thing to understand about `git rebase` is that it solves the same problem as `git merge`. Both of these commands are designed to integrate changes from one branch into another branch--they just do it in very different ways.

Consider what happens when you start working on a new feature in a dedicated branch, then another team member updates the `master` branch with new commits. This results in a forked history, which should be familiar to anyone who has used [Git as a collaboration tool.](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=merging-vs-rebasing&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content)

![A forked commit history](https://wac-cdn.atlassian.com/dam/jcr:01b0b04e-64f3-4659-af21-c4d86bc7cb0b/01.svg?cdnVersion=dt)

Now, let's say that the new commits in `master` are relevant to the feature that you're working on. To incorporate the new commits into your `feature` branch, you have two options: merging or rebasing.

### The Merge Option

The easiest option is to merge the `master` branch into the feature branch using something like the following:

Or, you can condense this to a one-liner:

This creates a new "merge commit" in the `feature` branch that ties together the histories of both branches, giving you a branch structure that looks like this:

![Merging master into the feature branch](https://wac-cdn.atlassian.com/dam/jcr:e229fef6-2c2f-4a4f-b270-e1e1baa94055/02.svg?cdnVersion=dt)

Merging is nice because it's a _non-destructive_ operation. The existing branches are not changed in any way. This avoids all of the potential pitfalls of rebasing (discussed below).

On the other hand, this also means that the `feature` branch will have an extraneous merge commit every time you need to incorporate upstream changes. If `master` is very active, this can pollute your feature branch's history quite a bit. While it's possible to mitigate this issue with advanced `git log` options, it can make it hard for other developers to understand the history of the project.

### The Rebase Option

As an alternative to merging, you can rebase the `feature` branch onto `master` branch using the following commands:

This moves the entire `feature` branch to begin on the tip of the `master` branch, effectively incorporating all of the new commits in `master`. But, instead of using a merge commit, rebasing _re-writes_the project history by creating brand new commits for each commit in the original branch.

![Rebasing the feature branch onto master](https://wac-cdn.atlassian.com/dam/jcr:5b153a22-38be-40d0-aec8-5f2fffc771e5/03.svg?cdnVersion=dt)

The major benefit of rebasing is that you get a much cleaner project history. First, it eliminates the unnecessary merge commits required by `git merge`. Second, as you can see in the above diagram, rebasing also results in a perfectly linear project history--you can follow the tip of `feature` all the way to the beginning of the project without any forks. This makes it easier to navigate your project with commands like `git log`, `git bisect`, and `gitk`.

But, there are two trade-offs for this pristine commit history: safety and traceability. If you don't follow the Golden Rule of Rebasing, re-writing project history can be potentially catastrophic for your collaboration workflow. And, less importantly, rebasing loses the context provided by a merge commit--you can't see when upstream changes were incorporated into the feature.

### Interactive Rebasing

Interactive rebasing gives you the opportunity to alter commits as they are moved to the new branch. This is even more powerful than an automated rebase, since it offers complete control over the branch's commit history. Typically, this is used to clean up a messy history before merging a feature branch into `master`.

To begin an interactive rebasing session, pass the `i` option to the`git rebase` command:

This will open a text editor listing all of the commits that are about to be moved:

This listing defines exactly what the branch will look like after the rebase is performed. By changing the `pick` command and/or re-ordering the entries, you can make the branch's history look like whatever you want. For example, if the 2nd commit fixes a small problem in the 1st commit, you can condense them into a single commit with the `fixup` command:

When you save and close the file, Git will perform the rebase according to your instructions, resulting in project history that looks like the following:

![Squashing a commit with an interactive rebase](https://wac-cdn.atlassian.com/dam/jcr:fe6942b4-7a60-4464-9181-b67e59e50788/04.svg?cdnVersion=dt)

Eliminating insignificant commits like this makes your feature's history much easier to understand. This is something that `git merge` simply cannot do.

## The Golden Rule of Rebasing

Once you understand what rebasing is, the most important thing to learn is when _not_ to do it. The golden rule of `git rebase` is to never use it on _public_ branches.

For example, think about what would happen if you rebased `master` onto your `feature` branch:

![Rebasing the master branch](https://wac-cdn.atlassian.com/dam/jcr:1d22f018-b2c7-4096-9db1-c54940cf4f4e/05.svg?cdnVersion=dt)

The rebase moves all of the commits in `master` onto the tip of `feature`. The problem is that this only happened in _your_repository. All of the other developers are still working with the original `master`. Since rebasing results in brand new commits, Git will think that your `master` branch's history has diverged from everybody else's.

The only way to synchronize the two `master` branches is to merge them back together, resulting in an extra merge commit_and_ two sets of commits that contain the same changes (the original ones, and the ones from your rebased branch). Needless to say, this is a very confusing situation.

So, before you run `git rebase`, always ask yourself, "Is anyone else looking at this branch?" If the answer is yes, take your hands off the keyboard and start thinking about a non-destructive way to make your changes (e.g., the `git revert` command). Otherwise, you're safe to re-write history as much as you like.

### Force-Pushing

If you try to push the rebased `master` branch back to a remote repository, Git will prevent you from doing so because it conflicts with the remote `master` branch. But, you can force the push to go through by passing the `\--force` flag, like so:

This overwrites the remote `master` branch to match the rebased one from your repository and makes things very confusing for the rest of your team. So, be very careful to use this command only when you know exactly what you're doing.

One of the only times you should be force-pushing is when you've performed a local cleanup _after_ you've pushed a private feature branch to a remote repository (e.g., for backup purposes). This is like saying, "Oops, I didn't really want to push that original version of the feature branch. Take the current one instead." Again, it's important that nobody is working off of the commits from the original version of the feature branch.

## Workflow Walkthrough

Rebasing can be incorporated into your existing [Git workflow](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=merging-vs-rebasing&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) as much or as little as your team is comfortable with. In this section, we'll take a look at the benefits that rebasing can offer at the various stages of a feature's development.

The first step in any workflow that leverages `git rebase` is to create a dedicated branch for each feature. This gives you the necessary branch structure to safely utilize rebasing:

![Developing a feature in a dedicated branch](https://wac-cdn.atlassian.com/dam/jcr:6af9de07-088b-4f8b-97a7-b66569a9e4ac/06.svg?cdnVersion=dt)

> _Local Cleanup_

One of the best ways to incorporate rebasing into your [workflow](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=merging-vs-rebasing&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) is to clean up local, in-progress features. By periodically performing an interactive rebase, you can make sure each commit in your feature is focused and meaningful. This lets you write your code without worrying about breaking it up into isolated commits--you can fix it up after the fact.

When calling `git rebase`, you have two options for the new base: The feature's parent branch (e.g., `master`), or an earlier commit in your feature. We saw an example of the first option in the_Interactive Rebasing_ section. The latter option is nice when you only need to fix up the last few commits. For example, the following command begins an interactive rebase of only the last 3 commits.

By specifying `HEAD~3` as the new base, you're not actually moving the branch--you're just interactively re-writing the 3 commits that follow it. Note that this will _not_ incorporate upstream changes into the `feature` branch.

![Rebasing onto Head~3](https://wac-cdn.atlassian.com/dam/jcr:079532c4-2594-40ed-a5c4-0e3621b9edff/07.svg?cdnVersion=dt)

If you want to re-write the entire feature using this method, the `git merge-base` command can be useful to find the original base of the `feature` branch. The following returns the commit ID of the original base, which you can then pass to `git rebase`:

This use of interactive rebasing is a great way to introduce `git rebase` into your workflow, as it only affects local branches. The only thing other developers will see is your finished product, which should be a clean, easy-to-follow feature branch history.

But again, this only works for _private_ feature branches. If you're collaborating with other developers via the same feature branch, that branch is _public_, and you're not allowed to re-write its history.

There is no `git merge` alternative for cleaning up local commits with an interactive rebase.

### Incorporating Upstream Changes Into a Feature

In the _Conceptual Overview_ section, we saw how a feature branch can incorporate upstream changes from `master` using either `git merge` or `git rebase`. Merging is a safe option that preserves the entire history of your repository, while rebasing creates a linear history by moving your feature branch onto the tip of `master`.

This use of `git rebase` is similar to a local cleanup (and can be performed simultaneously), but in the process it incorporates those upstream commits from `master`.

Keep in mind that it's perfectly legal to rebase onto a remote branch instead of `master`. This can happen when collaborating on the same feature with another developer and you need to incorporate their changes into your repository.

For example, if you and another developer named John added commits to the `feature` branch, your repository might look like the following after fetching the remote `feature` branch from John's repository:

![Collaborating on the same feature branch](https://wac-cdn.atlassian.com/dam/jcr:0bb661aa-361d-47ba-8c7b-00b3be0546cb/08.svg?cdnVersion=dt)

You can resolve this fork the exact same way as you integrate upstream changes from `master`: either merge your local `feature`with `john/feature`, or rebase your local `feature` onto the tip of `john/feature`.

![Merging vs. rebasing onto a remote branch](https://wac-cdn.atlassian.com/dam/jcr:1896adb1-5d49-419a-9b50-3a36adac186c/09.svg?cdnVersion=dt)

Note that this rebase doesn't violate the _Golden Rule of Rebasing_because only your local `feature` commits are being moved--everything before that is untouched. This is like saying, "add my changes to what John has already done." In most circumstances, this is more intuitive than synchronizing with the remote branch via a merge commit.

By default, the `git pull` command performs a merge, but you can force it to integrate the remote branch with a rebase by passing it the `\--rebase` option.

### Reviewing a Feature With a Pull Request

If you use pull requests as part of your code review process, you need to avoid using `git rebase` after creating the pull request. As soon as you make the pull request, other developers will be looking at your commits, which means that it's a _public_ branch. Re-writing its history will make it impossible for Git and your teammates to track any follow-up commits added to the feature.

Any changes from other developers need to be incorporated with `git merge` instead of `git rebase`.

For this reason, it's usually a good idea to clean up your code with an interactive rebase _before_ submitting your pull request.

### Integrating an Approved Feature

After a feature has been approved by your team, you have the option of rebasing the feature onto the tip of the `master` branch before using `git merge` to integrate the feature into the main code base.

This is a similar situation to incorporating upstream changes into a feature branch, but since you're not allowed to re-write commits in the `master` branch, you have to eventually use `git merge` to integrate the feature. However, by performing a rebase before the merge, you're assured that the merge will be fast-forwarded, resulting in a perfectly linear history. This also gives you the chance to squash any follow-up commits added during a pull request.

![Integrating a feature into master with and without a rebase](https://wac-cdn.atlassian.com/dam/jcr:df39b1f1-2686-4ee5-90bf-9836783342ce/10.svg?cdnVersion=dt)

If you're not entirely comfortable with `git rebase`, you can always perform the rebase in a temporary branch. That way, if you accidentally mess up your feature's history, you can check out the original branch and try again. For example:

## Summary

And that's all you really need to know to start rebasing your branches. If you would prefer a clean, linear history free of unnecessary merge commits, you should reach for `git rebase` instead of `git merge` when integrating changes from another branch.

On the other hand, if you want to preserve the complete history of your project and avoid the risk of re-writing public commits, you can stick with `git merge`. Either option is perfectly valid, but at least now you have the option of leveraging the benefits of `git rebase`.

[Bitbucket is the Git solution](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)
