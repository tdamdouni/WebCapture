# Git Strategies for Software Development: Part 1 - DZone DevOps

_Captured: 2019-07-25 at 08:31 from [dzone.com](https://dzone.com/articles/git-strategies-for-software-development)_

Git is a version control system for tracking changes in files and coordinating work on those files among multiple people. It is primarily used for source code management in software development. It is a distributed revision control system and is very useful to support software development workflows.

The Git directory on every machine is a full repository which has full version tracking capabilities and independent of network access. You can maintain branches, perform merges, and continue with development even when you are not connected to the network. For me, having a full repository on my machine and ease of use (creating a branch, merging branches, and maintaining branching workflows) are the biggest advantages of Git. It is a free and open-source software distributed under the terms of the GNU.

I will try to cover two common strategies that can be used to support software development in two articles. In this article, I will cover the single release development Git strategy. A software team working on one release at a time usually uses this strategy.

## **Single Release Development Strategy**

A software team working on one release at a time follows the following steps. I will try to add the git command/git UI steps to perform each step. The following diagram shows the strategy details:

![Image title](/storage/temp/9972047-singlestrategyversion1.png)

Create a release branch from the production code branch “master.”

The master has production code and “product-release1” is the new release branch.

Each dev member creates a feature branch from the release branch and works on feature development in that branch.

Each dev member has to work on the feature branch “product-release1-feature1.”

Everyone should take the latest updates from the release branch daily using the `merge` or `rebase` Git commands.

Let's say you are working on “product-release1-feature1” and you have to pull the latest changes form “product-release1.” This will make sure any changes that were moved to the release branch are available in the local feature branch. This also avoids conflicts or duplicate code while merging the feature branch to the release branch at feature completion time.

_Note: I would suggest using the `merge` option till you are very clear with  `rebase`._

Before doing this step, you should be only on your feature branch. Use the  `“git branch”` command to verify the branch name before doing a merge.

On completion of a feature, raise a pull request to merge the code to the release branch. This step can be done in the GitHub UI.

You can create and assign pull requests to a reviewer using the git UI. Refer to [this link](https://help.github.com/articles/creating-a-pull-request/) for the steps in the UI.

A code review will be performed on the pull request and changes will be done if needed. If everything is fine, the pull request will be approved by the reviewer. Refer to [this link](https://help.github.com/articles/approving-a-pull-request-with-required-reviews/) for the steps in the UI.

Create a tag from the release branch to the testing team for validation of the feature. We have to provide a tag to the testing team upon completion related features to be tested.

This should be done [in the Git UI](https://help.github.com/articles/creating-releases/).

Upon completion of all features planned in the release, the final tag can be provided to the testing team for validation. 

Once testing is complete, a software production release will be done from the final QA approved tag.

After the production release, merge the release branch code to the master so that the master has the production code. This step can be done using the Git UI by raising a merge from the release branch to the master.

Next, delete the feature branch upon completion of the feature and delete the release branch upon completion of the release.

Any post-production release fix can be done in a tag. Remember to move the code to the master and post any production fix release.

This command creates a new branch, “product-release1_prodfixticketNumber,” from the production release tag “product-release1_tag1.”

Create the next release branch from the master, as the master has the production code, and follow the same approach for development as described above.

In this approach, the master branch has the production code and releases are done from a tag. Each dev member can cut a branch from the release branch, work on a feature independently, and upon completion of the feature, can raise a merge pull request and get it approved. While doing development, each dev member should rebase the code from the release branch so that they have the latest code.

This approach works fine for projects where a team is working on a single release at a time. Most teams are working on multiple releases at a time, so they have to maintain more than one release branch active at a time.

Please read the next article for a possible approach to handling projects working on multiple releases in parallel.

### References

Useful git commands:

  * <https://github.com/DharmendraRathor/gitCommands>

  * <https://gist.github.com/DharmendraRathor>

GitHub Desktop tool: <https://desktop.github.com/>
