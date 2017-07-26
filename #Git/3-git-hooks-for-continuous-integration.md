# 3 Git Hooks for Continuous Integration

_Captured: 2017-06-04 at 01:17 from [dzone.com](https://dzone.com/articles/3-git-hooks-for-continuous-integration?edition=304120&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-03)_

DevOps is a culture, a philosophy, that helps Dev and Ops teams collaborate better. Let [Atlassian](https://dzone.com/go?i=206136&u=https%3A%2F%2Fwww.atlassian.com%2Fdevops%2Fstart-your-journey%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dpre-roll_agile-devops%26utm_campaign%3Ddevops_fy17q4) guide you on your DevOps journey. [Start today!](https://dzone.com/go?i=206136&u=https%3A%2F%2Fwww.atlassian.com%2Fdevops%2Fstart-your-journey%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dpre-roll_agile-devops%26utm_campaign%3Ddevops_fy17q4)

If you've used Git for a while, you've probably heard of Git hooks. Maybe you've even played around with them a bit. Git hooks are awesome in the context of continuous integration, so in this article, I'll dive into three use cases and point you to ready-made hooks you can add to your workflow. If you're new to Git hooks, no worries: we'll start with the basics.

## Understanding Git Hooks

Hooks are Git's native mechanism for triggering custom scripts before or after operations like commit and merge. Think of them as Git's plugin system. If you look in the .git directory of any Git repository you'll see a directory named "hooks" which contains a set of example hook scripts.

Installing Git hooks is straightforward and well-documented, so I won't get into that here.

There are two broad classes of hooks: client-side and server-side. Client-side hooks run on your local workstation, while server-side hooks run on your Git server.

You can also classify hooks as pre- or post-. Pre-receive hooks are invoked before certain Git operations, and have the option to cancel an operation if needed. They act as bouncers guarding your repo from behind a velvet rope, preventing you and your teammates from committing faulty code. Post-receive hooks run after an operation has completed, and therefore don't have the option to cancel it. Instead, post-receive hooks automate pieces of your development workflow.

Using Git hooks is like having little robot minions to carry out your every wish (muwa-ha-haaaa!).

Git hooks automate things like…

  * Verifying that you included the associated JIRA issue key in your commit message.
  * Enforcing preconditions for merging.
  * Sending notifications to your team's chat room.
  * Setting up your workspace after switching over to a different branch.
![](https://wac-cdn-a.atlassian.com/dam/jcr:744af6c8-aecc-4a33-909c-3345b3a9da24/githooksgrid.png?cdnVersion=es)

## Enforcing Clean Builds on Feature Branches

Server-side pre-receive hooks are an especially powerful compliment to continuous integration because they can prevent developers from pushing code to master, unless the code meets certain conditions - like elite ninja guardians, protecting it from bad code.

Developers are generally conscientious enough not to merge to master when there are broken tests on their branch. But sometimes we forget to check. Or when we're sharing a branch with other people, sometimes more changes get made since we last checked the branch build… stuff happens.

So you can add a server-side hook that looks for incoming merges to master. When it finds one, the script checks the latest build on your branch, and if there are any failing tests, the merge is rejected. My colleague and Atlassian developer advocate Tim Petterson wrote a hook script for this, designed to work with Bamboo, and made it available on Bitbucket. You can grab it, customize it, and add it to your repo.

## Protecting Your Hard-Earned Code Coverage

Something I've seen lots of teams struggle with is maintaining code coverage. Often times they've had to retroactively cover their code base with tests, and it's really frustrating to see that hard-earned coverage slip away as more features get added without tests shoring them up. So Tim also wrote a pre-receive server-side hook to protect master from declining code coverage.

![](https://wac-cdn-a.atlassian.com/dam/jcr:37798a8d-c9e5-4e26-8f90-90a36eb862cf/githookscodecoverage.png?cdnVersion=es)

This hook also looks for incoming merges to master. It then calls out to the continuous integration server to check current code coverage on master, and coverage on the branch. If the branch has inferior coverage, the merge is rejected.

Most continuous integration servers don't expose code coverage data through their remote APIs, so the script pulls down the code coverage report. To do this, the build must be configured to publish the report as a shared artifact, both on master and on the branch build. Once published, you can grab the latest coverage report from master by calling the continuous integration server. For branch coverage, you fetch the coverage report either from the latest build, or for builds related to the commit being merged.

And just to be clear, this all assumes you already have code coverage running. The hook doesn't magically do that - it just looks for the coverage data in your build results. This one also works with Bamboo by default, as well as Clover ([Atlassian's](https://www.atlassian.com/continuous-delivery/git-hooks-continuous-integration?utm_source=dzone&utm_medium=paid-content&utm_campaign=devops_fy17q4_syn-content&utm_content=cd-git-hooks) code coverage tool for Java and Groovy). But it can be customized to integrate with any build server or code coverage tool.

## Checking the Status of Branch Builds

Friends don't let friends check out broken branches.

Here's a chance to play with client-side Git hooks: a post-checkout hook script that exposes branch build status right inside your terminal window, also from Tim. The script gets the branch's head revision number from your local copy, then queries the continuous integration server to see whether that revision has been built - and if so, whether the build succeeded.

![](https://wac-cdn-a.atlassian.com/dam/jcr:97ecbcdd-9129-4c78-b996-b1f3e1b755f9/githookpostcheckout.png?cdnVersion=es)

Let's say you want to branch from master. This hook will tell you whether the head commit on the master built successfully, which means it's a "safe" commit to create a feature branch from. Or, let's say the hook says the build for that revision failed, yet the team's wallboard shows a green build for that branch (or vice versa). This means your local copy is out-of-date. It'll be up to you to decide whether to pull down the updates or continue working on the local copy you have.

Using this hook has saved Atlassian developers from countless headaches. If you can't convince your team to adopt the server-side hooks discussed above, at least install this one on your local workstation. You won't regret it.

All the Git hooks for continuous integration that I've shown here [work with Bamboo, Clover, and Bitbucket](https://www.atlassian.com/continuous-delivery/git-hooks-continuous-integration?utm_source=dzone&utm_medium=paid-content&utm_campaign=devops_fy17q4_syn-content&utm_content=cd-git-hooks) by default, but remember that Git hooks are vendor-neutral, so you can customize them to work with whatever tool stack you have. Automation for the win!

[JIRA Software](https://dzone.com/go?i=206137&u=https%3A%2F%2Fwww.atlassian.com%2Fsoftware%2Fjira%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dpost-roll_agile-devops%26utm_campaign%3Ddevops_fy17q4) helps foster a culture of collaboration and trust among teams related to software development. [Try JIRA Software today!](https://dzone.com/go?i=206137&u=https%3A%2F%2Fwww.atlassian.com%2Fsoftware%2Fjira%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dpost-roll_agile-devops%26utm_campaign%3Ddevops_fy17q4)
