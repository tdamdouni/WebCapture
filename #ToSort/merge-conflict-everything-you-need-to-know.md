# Merge Conflict: Everything You Need to Know

_Captured: 2018-08-11 at 09:27 from [dzone.com](https://dzone.com/articles/merge-conflict-everything-you-need-to-know?edition=385359&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-08-10)_

Read why times series is the [fastest growing database](https://dzone.com/go?i=283423&u=https%3A%2F%2Fwww.influxdata.com%2Ftime-series-database%2F) category.

Previously, I wrote a [long-form post about merge conflict](https://rollout.io/blog/resolve-github-merge-conflicts/). This time, I'm going to mix things up with an FAQ on the subject. Many of these frequently asked questions could be their own standalone articles, but sometimes, it's good to have all the answers in one place so we get an overview of the landscape.

Without further ado, let's get going!

## When There's a Merge Conflict, in Which Branch Does the Conflict Take Place?

The term "merge conflict" obviously contains the word "merge," meaning that, to generate a merge conflict, you need to have a merge taking place. When merging changes from one branch (the source branch) to another branch (the destination branch), there's always the possibility that the merge will cause a conflict at the destination.

Since typically you have local and remote repositories, the following scenarios can occur:

  1. Merge incoming changes from remote branch to the local branch
  2. Merge outgoing changes from local branch to the remote branch
  3. Merge changes in one local branch to another local branch
  4. Merge changes in one remote branch to another remote branch

Regardless, the conflict happens at the destination branch of your merge.

## Why Does a Merge Conflict Happen?

This is easier to explain with an example. Imagine we have a local code repository like this:

![](https://rollout.io/blog/wp-content/uploads/sites/2/2018/07/M1-1-300x209.png)

And we have a single text file called **master.txt** in the master branch that simply says this:

In **branch1**, we change **master.txt** to read:

And in **branch2**, we change the original **master.txt** into this:

To recap:

The changes in **branch1** are from **a** to **a<new line>1** in **master.txt**.

And the changes in **branch2** are from **a** to **a<new line>2** in **master.txt**.

So when we merge **branch1** back to the **master** branch, the merge is successful. This is because the history for **branch1** is simply **adding 1 to the second line of master.txt**.

Now the **master.txt** in master branch looks like this:

Or, presented as a flow diagram, like this:

![](https://rollout.io/blog/wp-content/uploads/sites/2/2018/07/M2-1-300x262.png)

Now, if we want to merge **branch2** into **master, **we'll encounter a merge conflict:

![](https://rollout.io/blog/wp-content/uploads/sites/2/2018/07/M3-1-281x300.png)

Why? Because now both **master** and **branch2** have commits in their respective histories about adding a second line to **master.txt**. And yet both are changing the same line in the same file differently. Git is unable to determine whether

a) the incoming change from **branch2** should override the second line,  
b) the current change in **master** should override the incoming change, or  
c) there should be some kind of combination of both changes.

This merge conflict will also occur _even when you attempt the merge in the opposite direction,_ by merging **master** into **branch2**.

In summary, a merge conflict happens when you merge two separate branches that contain different changes on the same locations in the same file and it's unclear which change should take precedence or whether both should be combined.

## What Do "Incoming Changes" and "Outgoing Changes" Mean?

Recall the four different scenarios of merge conflict:

  1. Merge incoming changes from remote branch to the local branch
  2. Merge outgoing changes from local branch to the remote branch
  3. Merge changes in one local branch to another local branch
  4. Merge changes in one remote branch to another remote branch

When we say incoming or outgoing, we're taking the perspective of the **local branch** we're currently in. Changes committed on the local branch that we want to send out to another branch (usually on the remote repository) are known as "outgoing."

Any new changes we want to merge into the local branch are usually seen as "incoming."

## Why Does a Rebase and Merge Sometimes Generate Conflict, but a Merge on Its Own Doesn't?

Before I answer this, we need to first understand what rebase and merge really is.

Let's say we have the following:

![](https://rollout.io/blog/wp-content/uploads/sites/2/2018/07/M4-1-300x207.png)

When we try to rebase and merge the branch **rebase-back-to-master **into **master, ** this is what we're asking the commit history to be like:

![](https://rollout.io/blog/wp-content/uploads/sites/2/2018/07/m5-1-300x245.png)

If we're doing just a plain merge, we're asking the commit history to be more like this:

![](https://rollout.io/blog/wp-content/uploads/sites/2/2018/07/M6-1-300x208.png)

Using the example above, the merge conflict happens for rebase when the transition from commit F to D causes a conflict. But if you do a simple merge, Git will automatically create a brand new commit called G on the master branch. This G contains the differences between E and F before it's placed on the master branch.

It's hard to replicate this scenario on purpose, so I know this isn't the most concrete example. But this illustration gives you an idea of what you're trying to do in a rebase versus a simple merge.

## So How Do We Ensure That Our Rebase and Merge Back to the Master Branch Is Conflict-Free?

Before I can talk about how to reduce the chances of a conflict for rebase and merge, let me be clear:** I don't recommend rebasing the commits of your master branch on remote repositories.**

You can rebase the commits of your [feature branches](https://rollout.io/blog/pitfalls-feature-branching/) on remote repositories. When you do so, remember to force-update the same local feature branch back onto the remote repository.

Now that I've covered this caveat, let's proceed with the steps. Using the example from the previous question, my suggestion is to always pull changes from the destination branch first, before resolving any conflicts in your local branch.

Remember, this was the original situation, and we do want to rebase **rebase-back-to-master **back into **master:**

![](https://rollout.io/blog/wp-content/uploads/sites/2/2018/07/M7-1-300x207.png)

How do we do this? First, perform pull from the master with rebase at **rebase-back-to-master:**
    
    
    (rebase-back-to-master)$: git pull origin master --rebase

You'll definitely get a merge conflict, but your source branch is the best place to resolve this before you attempt to deploy the outgoing changes.

Second, solve merge conflict in the source branch:
    
    
    (rebase-back-to-master)$: git rebase --continue

Continue doing this until all issues are resolved. Then do this:

Don't commit anything! It will cause the conflict to return.

At the end, you should get something like this:

![](https://rollout.io/blog/wp-content/uploads/sites/2/2018/07/M8-1-300x263.png)

Now you can safely rebase and merge **rebase-back-to-master** into **master** with zero issues.

If necessary, you may need to do a force-update of the **rebase-back-to-master** branch on the remote repository:
    
    
    (rebase-back-to-master)$: git push -u origin rebase-back-to-master -f

## Conclusion

This post answered FAQs about why and on which branch a merge conflict typically occurs. We also discussed the two major sources of merge conflicts: one where it's simply due to a regular merge and another where it's due to rebase. And, we reviewed how to properly rebase your changes of a feature branch locally, so when you eventually rebase and merge the feature branch back onto the master branch in the remote repository, you minimize any conflict issues.

Is that everything you ever wanted to know about merge conflicts? If not, leave a comment and I'll answer more questions.

Learn how to get 20x more performance than Elastic by [moving to a Time Series database](https://dzone.com/go?i=283422&u=https%3A%2F%2Fwww.influxdata.com%2Fresources%2Fbenchmarking-influxdb-vs-elasticsearch-for-time-series%2F%3Futm_campaign%3Ddbzone%26utm_medium%3Dpartner%26utm_source%3Ddzone%26utm_content%3D%26utm_term%3D).
