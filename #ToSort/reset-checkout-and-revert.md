# Reset, Checkout, and Revert

_Captured: 2017-04-23 at 21:23 from [dzone.com](https://dzone.com/articles/reset-checkout-and-revert?edition=292909&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-23)_

[Bitbucket](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

The `git reset`, `git checkout`, and `git revert` commands are some of the most useful tools in your Git toolbox. They all let you undo some kind of change in your repository, and the first two commands can be used to manipulate either commits or individual files.

Because they're so similar, it's very easy to mix up which command should be used in any given development scenario. In this article, we'll compare the most common configurations of `git reset`, `git checkout`, and `git revert`. Hopefully, you'll walk away with the confidence to navigate your repository using any of these commands.

![The main components of a Git repository](https://wac-cdn.atlassian.com/dam/jcr:0c5257d5-ff01-4014-af12-faf2aec53cc3/01.svg?cdnVersion=ed)

It helps to think about each command in terms of their effect on the three main components of a Git repository: the working directory, the staged snapshot, and the commit history. Keep these components in mind as you [read through this article.](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=resetting-checking-out-and-reverting&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content)

## Commit-Level Operation

The parameters that you pass to `git reset` and `git checkout` determine their scope. When you _don't_ include a file path as a parameter, they operate on whole commits. That's what we'll be exploring in this section. Note that `git revert` has no file-level counterpart.

### Reset

On the commit-level, resetting is a way to move the tip of a branch to a different commit. This can be used to remove commits from the current branch. For example, the following command moves the `hotfix` branch backwards by two commits.

The two commits that were on the end of `hotfix` are now dangling commits, which means they will be deleted the next time Git performs a garbage collection. In other words, you're saying that you want to throw away these commits. This can be visualized as the following:

![Resetting the hotfix branch to HEAD~2](https://wac-cdn.atlassian.com/dam/jcr:df153bec-e735-4abf-a581-826c43dde64f/02.svg?cdnVersion=ed)

This usage of `git reset` is a simple way to undo changes that haven't been shared with anyone else. It's your go-to command when you've started working on a feature and find yourself thinking, "Oh crap, what am I doing? I should just start over."

In addition to moving the current branch, you can also get `git reset` to alter the staged snapshot and/or the working directory by passing it one of the following flags:

  * `\--soft` - The staged snapshot and working directory are not altered in any way.
  * `\--mixed` - The staged snapshot is updated to match the specified commit, but the working directory is not affected. This is the default option.
  * `\--hard` - The staged snapshot and the working directory are both updated to match the specified commit.

It's easier to think of these modes as defining the scope of a `git reset` operation:

![The scope of `git reset`’s modes ](https://wac-cdn.atlassian.com/dam/jcr:2528918b-5c1a-4ab5-8454-88c3a66b14d1/03.svg?cdnVersion=ed)

These flags are often used with `HEAD` as the parameter. For instance, `git reset --mixed HEAD` has the affect of unstaging all changes, but leaves them in the working directory. On the other hand, if you want to completely throw away all your uncommitted changes, you would use `git reset --hard HEAD`. These are two of the most common uses of `git reset`.

Be careful when passing a commit other than `HEAD` to `git reset`, since this re-writes the current branch's history. As discussed in The Golden Rule of Rebasing, this a big problem when working on a public branch.

### Checkout

By now, you should be very familiar with the commit-level version of `git checkout`. When passed a branch name, it lets you switch between branches.

Internally, all the above command does is move `HEAD` to a different branch and update the working directory to match. Since this has the potential to overwrite local changes, Git forces you to commit or stash any changes in the working directory that will be lost during the checkout operation. Unlike `git reset`, `git checkout` doesn't move any branches around.

![Moving `HEAD` from `master` to `hotfix` ](https://wac-cdn.atlassian.com/dam/jcr:aa84ece9-179f-4af1-8171-eef20993c078/04.svg?cdnVersion=ed)

You can also check out arbitrary commits by passing in the commit reference instead of a branch. This does the exact same thing as checking out a branch: it moves the `HEAD` reference to the specified commit. For example, the following command will check out out the grandparent of the current commit:

![Moving `HEAD` to an arbitrary commit ](https://wac-cdn.atlassian.com/dam/jcr:3034be0a-fc7b-4c64-b9cd-3ebc8abf3833/05.svg?cdnVersion=ed)

This is useful for quickly inspecting an old version of your project. However, since there is no branch reference to the current `HEAD`, this puts you in a `detached HEAD state`. This can be dangerous if you start adding new commits because there will be no way to get back to them after you switch to another branch. For this reason, you should always create a new branch before adding commits to a detached `HEAD`.

### Revert

Reverting undoes a commit by creating a _new_ commit. This is a safe way to undo changes, as it has no chance of re-writing the commit history. For example, the following command will figure out the changes contained in the second-to-last commit, create a new commit undoing those changes, and tack the new commit onto the existing project.

This can be visualized as the following:

![Reverting the 2nd to last commit](https://wac-cdn.atlassian.com/dam/jcr:73d36b14-72a7-4e96-a5bf-b86629d2deeb/06.svg?cdnVersion=ed)

Contrast this with `git reset`, which _does_ alter the existing commit history. For this reason, `git revert` should be used to undo changes on a public branch, and `git reset` should be reserved for undoing changes on a private branch.

You can also think of `git revert` as a[ tool](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=resetting-checking-out-and-reverting&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) for undoing _committed_ changes, while `git reset HEAD` is for undoing _uncommitted_ changes.

Like `git checkout`, `git revert` has the potential to overwrite files in the working directory, so it will ask you to commit or stash changes that would be lost during the revert operation.

## File-Level Operations

The `git reset` and `git checkout` commands also accept an optional file path as a parameter. This dramatically alters their behavior. Instead of operating on entire snapshots, this forces them to limit their operations to a single file.

### Reset

When invoked with a file path, `git reset` updates the _staged snapshot_ to match the version from the specified commit. For example, this command will fetch the version of `foo.py` in the 2nd-to-last commit and stage it for the next commit:

As with the commit-level version of `git reset`, this is more commonly used with `HEAD` rather than an arbitrary commit. Running `git reset HEAD foo.py` will unstage `foo.py`. The changes it contains will still be present in the working directory.

![Moving a file from the commit history into the staged snapshot](https://wac-cdn.atlassian.com/dam/jcr:1a010f5a-c90d-49ee-a0e6-31054433e2d4/07.svg?cdnVersion=ed)

The `\--soft`, `\--mixed`, and `\--hard` flags do not have any effect on the file-level version of `git reset`, as the staged snapshot is _always_ updated, and the working directory is _never_ updated.

### Checkout

Checking out a file is similar to using `git reset` with a file path, except it updates the _working directory_ instead of the stage. Unlike the commit-level version of this command, this does not move the `HEAD` reference, which means that you won't switch branches.

![Moving a file from the commit history into the working directory](https://wac-cdn.atlassian.com/dam/jcr:cc252fc0-fc76-4740-8458-9c0d7af94bca/08.svg?cdnVersion=ed)

For example, the following command makes `foo.py` in the working directory match the one from the 2nd-to-last commit:

Just like the commit-level invocation of `git checkout`, this can be used to inspect old versions of a project--but the scope is limited to the specified file.

If you stage and commit the checked-out file, this has the effect of "reverting" to the old version of that file. Note that this removes _all_ of the subsequent changes to the file, whereas the `git revert` command undoes only the changes introduced by the specified commit.

Like `git reset`, this is commonly used with `HEAD` as the commit reference. For instance, `git checkout HEAD foo.py` has the effect of discarding unstaged changes to `foo.py`. This is similar behavior to `git reset HEAD --hard`, but it operates only on the specified file.

## Summary

You should now have all the tools you could ever need to undo changes in a [Git repository.](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=resetting-checking-out-and-reverting&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) The `git reset`, `git checkout`, and `git revert` commands can be confusing, but when you think about their effects on the working directory, staged snapshot, and commit history, it should be easier to discern which command fits the development task at hand.

The table below sums up the most common use cases for all of these commands. Be sure to keep this reference handy, as you'll undoubtedly need to use at least some them during your [Git career.](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=resetting-checking-out-and-reverting&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content)

Command
Scope
Common use cases

git reset
commit-level

Discard commits in a private branch or throw away uncommited changes

git reset
file-level

Unstage a file

git checkout
commit-level

Switch between branches or inspect old snapshots

git checkout
file-level

Discard changes in the working directory

git revert
commit-level

Undo commits in a public branch

git revert
file-level
(N/A)

[Bitbucket is the Git solution](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)
