# What is Git Checkout Remote Branch? How It Works, When to Use It, and More

_Captured: 2017-05-10 at 00:41 from [dzone.com](https://dzone.com/articles/what-is-git-checkout-remote-branch-how-it-works-wh?edition=298034&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-09)_

### If you're wondering why you'd use this less-frequently used command, this is the post for you. Check it out and see if it can help you within your own teams.

Today's data climate is fast-paced and it's not slowing down. [Here's why your current integration solution is not enough.](https://dzone.com/go?i=188126&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fdata-inspired-future-e-guide%2F%3Futm_campaign%3DDZONE%26utm_medium%3DE-guide%25252520-%25252520Data-Inspired%25252520Future%26utm_source%3DDZONE) Brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=188126&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fdata-inspired-future-e-guide%2F%3Futm_campaign%3DDZONE%26utm_medium%3DE-guide%25252520-%25252520Data-Inspired%25252520Future%26utm_source%3DDZONE)

As developers, we work with Git often. Visit our [Git page](https://github.com/stackify), and you'll see that we have quite a few repositories going on. Like many developers and groups, we migrated our version control to a git-based system a few years back, so working with Git is a big part of our ongoing work. Thus, it's pretty important that developers understand how to work with Git and the various possibilities for working with repositories (like controlling the size of your reports -- an issue we talk about [here](https://stackify.com/the-seven-stages-of-grief-git-repo-maintenance-and-preventative-medicine/)) and code in Git. Along those lines, one thing you'll be doing at least periodically is checking out a remote branch, so we put together a brief tutorial to cover the ins and outs of working with remote branches in Git.

## Git Checkout Remote Branch Definition

Git checkout remote branch is a way for a programmer to access the work of a colleague or collaborator for the purpose of review and collaboration. There is no actual command called "git checkout remote branch." It's just a way of referring to the action of checking out a remote branch.

Git is a way for software developers to track different modifications of their code. It keeps all the various versions in a unique database. Git allows multiple developers to work on the same code simultaneously. Sometimes, a programmer will need to access a coworker's independent work, or "branch." The git checkout remote branch action makes this possible.

## Why Use Git Checkout Remote Branch?

In Git, a branch is a separate line of development. New branches are created with the [git branch](https://www.digitalocean.com/community/tutorials/how-to-use-git-branches) command.

When a programmer fixes a bug or adds a new feature, he or she creates a new branch to make the changes in a safe way, without threatening existing, working code.

Sometimes we need to access a branch that's not stored locally, but we don't want to create a new local branch or version. We actually want to work on the remote version. In this case, we need to use a git checkout remote branch method.

## How Does Git Checkout Remote Branch Work?

Git checkout remote branch lets us switch to (and work on) a remote branch, just like we'd switch to a local one. There are a couple of [ways to do this](https://makandracards.com/makandra/521-check-out-a-remote-branch-in-git).

First, fetch the remote branches:

`git fetch origin`

Next, checkout the branch you want. In this case, the branch we want is called "branchxyz."

`git checkout -b branchxyz origin/branchxyz`

Or you can use:

`git branch branchxyz origin/branchxyz`

With newer versions, you can simply use:

`git fetch`

`git checkout branchxyz`

## Examples of Git Checkout Remote Branch

Below are a couple of examples of checking out remote branches with Git.

In this one, we're simply checking out a remote branch called xyz:

`git fetch`

`git checkout xyz`

That's fine as long as we don't have a local branch that's also called "xyz." In that event, we'd confuse Git with the "git checkout xyz" command. We need to specify that we're referring to the remote branch like this:

`git fetch origin`

`git checkout -track origin/xyz`

If we've got multiple remotes, we need to use:

`Git checkout -b xyz /xyz`

## Benefits of Git Checkout Remote Branch

Git is an incredibly powerful way for programmers to [collaborate on coding projects](https://rogerdudler.github.io/git-guide/). Imagine having ten programmers all working on the same piece of code, all trying to make their own changes and then attempting to merge those changes without some sort of version tracking system.

With git checkout remote branch, multiple developers can work on a single piece of software, each making their own changes in a protected way, without adding unstable code to working software.

Git checkout remote branch makes it easy to review and collaborate with others in a failsafe way.

## Git Checkout Remote Branch Best Practices

Since the git checkout, remote branch methods listed above are a subset of Git as a whole, best practices for working with git checkout remote branch are the same, including:

  * **Commit often. **When we commit often, we keep our commits small and share our work more frequently. That makes it easier to avoid large merge conflicts.
  * **Don't commit unfinished work. **Break your feature's code into small but working chunks. Once you finish a chunk, test it, then commit it. This work method prevents the potential conflicts created by merging large bodies of code all at once. At the same time, it ensures we don't commit small snippets of non-working code.
  * **Before you commit, test. **Don't commit something until you've tested it. Shared code that isn't tested can create a lot of headaches and lost time for an entire team.
  * **Commit related changes. **Make your commits small, and confine them to directly related changes. When we fix two separate bugs, they should take the form of two different commits.
  * **Write clear commit messages. **Include a single-sentence summary of your changes. After that, explain the motivation for the change, and how it's different from the previous version.
  * **Use branches. **Branches are an excellent tool to avoid confusion and keep different lines of development separate.
  * **Agree on your workflow. **Your team should agree on a workflow before the project starts. Whether that's based on topic-branches, git-flow, long-running branches, or some other workflow will depend on the project.

## Additional Resources and Tutorials on Git Checkout Remote Branch

For further reading on using git checkout remote branch, including tutorials and other resources, check out the following links:

[Is iPaaS solving the right problems?](https://dzone.com/go?i=171134&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-ipaas-plus-e-guide%2F%3Futm_campaign%3DDZONE%26utm_source%3DDZONE%26utm_medium%3DeGuide%252520-%252520iPaaS%252520vs%252520iPaaS%252520%252520) Not knowing the fundamental difference between iPaaS and iPaaS+ could cost you down the road. Brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=171134&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-ipaas-plus-e-guide%2F%3Futm_campaign%3DDZONE%26utm_source%3DDZONE%26utm_medium%3DeGuide%252520-%252520iPaaS%252520vs%252520iPaaS%252520%252520)

Topics:

git checkout ,git ,commands ,tutorial ,integration ,branches ,software development
