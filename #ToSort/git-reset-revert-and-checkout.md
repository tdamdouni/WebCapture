# Git Reset, Revert and Checkout

_Captured: 2018-06-27 at 19:05 from [dzone.com](https://dzone.com/articles/git-reset-revert-and-checkout?edition=383268&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-27)_

DON'T STRESS! Assess your OSS. [Get your free code scanner from Flexera](https://dzone.com/go?i=294429&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-security-banner%26utm_campaign%3Ddzone-fnca-security-banner-may2018%26id%3Ddzone-fnca-security-banner-May2018). [FlexNet Code Aware](https://dzone.com/go?i=294429&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-security-banner%26utm_campaign%3Ddzone-fnca-security-banner-may2018%26id%3Ddzone-fnca-security-banner-May2018) scans Java, NuGet, and NPM packages.

Git toolbox provides multiple unique tools for fixing up mistakes during your development. Commands such as `git reset`, `git checkout`, and `git revert` allow you to undo erroneous changes in your repository.

Because they perform similar operations, it is _very_ easy to mix them up. There are a few guidelines and rules for when each command should and should not be used. Let's take a look!

> Be careful! You can't always redo after an [undo](https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things). This is one of the few areas in Git where you may lose some work if you do it wrong.

## Undoing with Git Commands

We will start off by clarifying the main differences between these three commands.

### Checkout:

  * Use this to move the [HEAD pointer](https://kolosek.com/git-branches/) to a specific commit or **switch** between branches.
  * It **rollbacks** any content changes to those of the specific commit.
  * This will **not** make changes to the commit history.
  * Has potential to **overwrite** files in the working directory.

### Revert:

  * **Rollback changes** you have committed.
  * Creates a **new commit** from a specified commit by inverting it. Hence, adds a new commit history to the project, but it does not modify the existing one.
  * Has the potential to overwrite files in the working directory.

### Reset:

  * Use this to **return** the _entire_ working tree to the last committed state. This will discard commits in a private branch or throw away uncommitted changes!
  * Changes which commit a branch HEAD is currently pointing at. It alters the existing commit history.
  * Can be used to **unstage** a file.

[Every command](https://kolosek.com/git-commands-tutorial-part1/) lets you **undo** some kind of change in your repository, only checkout and reset can be used to manipulate either commits or individual files.

## Using the Commands

There are many different ways you can **undo your changes**, it all depends on the current scenario. Selecting an appropriate method depends on whether or not you have committed the change by mistake, and if you have committed it, whether you have shared it or not.

### Undo Public Changes

_Scenario:_ Image that you did in hotfix branch for commits you didn't want to make yet.

_Solution:_ The safest way to fix this is by **reverting** your changes since it doesn't re-write the commit history.

_Result:_ You have successfully undone committed changes! Everything that was changed in the old commit will be reverted with this new commit. Git forces you to commit or [stash](https://kolosek.com/git-stash/) any changes in the working directory that will be lost during the checkout.

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/782bf25d88e360df15ef96d84d872181/git-revert.png)

> You can think of `git revert` as a tool for undoing **committed** changes, while `git reset HEAD` is for undoing **uncommitted** changes.

### Undo Local Changes

_Scenario:_ You started working on a feature, but you didn't like the end result. These changes haven't been **shared** with anyone else.

_Solution:_ You want to **undo everything** in that files to the previous state, just the way it looked in the last [commit](https://kolosek.com/git-commands-tutorial-part2/).

_Result:_ File `file_name.rb` has been **reverted** to a state previously known to Git. Note that this removes all of the subsequent changes to the file!

> You can use `git checkout branch_name` to switch between branches. Git forces you to commit or stash any changes in the working directory that will be lost during the checkout operation.

### Undo Private Changes

_Scenario:_ You've made some commits locally in the [hotfix branch](https://kolosek.com/git-branches/) but everything is terrible! You want to remove the last two commits from the current branch.

_Solution:_**Reset** the hotfix branch backward by two commits as if those commits never happened.

_Result:_ Our git repository has been **rewinded** all the way back to the specified commit. Those left out commits are now **orphaned** and will be removed the next time Git performs a **garbage collection**. For now, then their contents are still on disk.

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/f0ae16e339631560090233b4c5850990/git-reset.png)

You can tell Git what to do with your **index** (set of files that will become the next commit) and **working directory** when performing by using one of the parameters:

  * `\--soft`: Tells Git to reset HEAD to another commit, so index and the working directory will _not be altered_ in any way. All of the files changed between the original HEAD and the commit will be staged.
  * `\--mixed`: Just like the soft, this will reset HEAD to another commit. It will also reset the **index** to match it while working directory will not be touched. All the **changes** will stay in the working directory and appear as modified, but not staged.

> The main difference between `\--mixed` and `\--soft` is whether or not your index is also modified. Check more on [git-reset-guide](https://gist.github.com/tnguyen14/0827ae6eefdff39e452b).

## Tips and Tricks

We will cover two additional things that can come in handy during your Git adventures.

### Fix the Previous Commit Message

_Scenario:_ Everyone makes typo mistakes when writing commits and this is completely fine! It can be easily fixed before you do a `git push`.

_Solution:_ Just run `git commit --amend` or `git commit --amend -m 'The new message'`. This will update and replace the most recent commit with a new commit.

### Redo After Undo

_Scenario:_ You have done a `git reset --hard` for some unwanted changes, but then you realized that you actually needed them.

_Solution:_`git reflog` comes to your rescue! It is an amazing command for recovering project history and it can recover _almost_ anything.

_Hope this three tools will help you whenever you need to undo your recent changes. _**Subscribe and stay tuned for the upcoming articles!**

[Try FlexNet Code Aware Today](https://dzone.com/go?i=294430&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-security-banner%26utm_campaign%3Ddzone-fnca-security-banner-may2018%26id%3Ddzone-fnca-security-banner-May2018)! A [free scan tool](https://dzone.com/go?i=294430&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-security-banner%26utm_campaign%3Ddzone-fnca-security-banner-may2018%26id%3Ddzone-fnca-security-banner-May2018) for developers. Scan Java, NuGet, and NPM packages for open source security and license compliance issues.
