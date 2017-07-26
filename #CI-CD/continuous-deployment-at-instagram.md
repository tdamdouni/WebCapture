# Continuous Deployment at Instagram

_Captured: 2017-03-09 at 21:09 from [engineering.instagram.com](https://engineering.instagram.com/continuous-deployment-at-instagram-1e18548f01d1#.4xi9m9lgo)_

At Instagram, we deploy our backend code 30-50 times a day… whenever engineers commit changes to master… with no human involvement in most cases. This may sound crazy, especially at our scale, but it works really well. This post talks about how we implemented this system and got it working smoothly.

### Why do it?

Continuous deployment has a number of advantages for us:

  1. It lets our engineers move really fast. They aren't limited to a few deployments per day at fixed times; instead, they can get code deployed whenever they want. This means that they waste less time and can iterate on changes very quickly.
  2. It makes it much easier to identify bad commits. Instead of having to dig through tens or hundreds of commits to find the cause of a new error, the pool is narrowed down to one, or at most two or three. This is also really useful when you identify a problem later and go back to debug. The metrics or data that indicate the problem can be used to identify an accurate start time, and from there we can find which commits were deployed at that time.
  3. Bad commits get detected very quickly and dealt with, which means that we don't end up with an undeployable mess in master and cause significant delays for other unrelated changes. We're always in a state where we can get important fixes out quickly.

### Implementation

The success of this implementation can largely be attributed to its construction's iterative approach. Instead of building this system on the side and suddenly switching over, we evolved the current mechanisms until they became continuous deployment.

#### **How it worked before**

Before continuous deployment, engineers deployed changes on an ad-hoc basis. They'd land changes, and if they wanted them deployed soon, they'd run a rollout. Otherwise they'd wait for another engineer to come along and do so. Engineers were expected to know how to do a small scale test beforehand: they would do a rollout targeting one machine, log into that machine and check the logs, and then run a second rollout targeting the entire fleet. This was all implemented as a Fabric script, and we had a very basic database and UI called "Sauron" which stored a log of rollouts.

#### **Canary and testing**

The first step was adding canarying, which was initially simply scripting what engineers were already expected to do. Instead of running a separate rollout targeting one machine, the script deployed to the canary machine, tailed the logs for user, and asked whether it should continue to the full deploy. Next came some basic analysis of the canary machine: a script collected the HTTP status codes for each request, categorized them, and applied hard-coded percentage thresholds (e.g. less than 0.5% 5xx, at least 90% 2xx). However, this would only warn the user if the thresholds failed.

We already had a test suite, but it was only run by engineers on their development machines. Code reviewers had to take the author's word that the tests passed, and we didn't know the test status of the resulting commit in master. So we setup Jenkins to run tests on new commits in master and report the result to Sauron. Sauron would keep track of the latest commit which had passed tests, and when doing a rollout this commit would be suggested instead of the latest commit.

Facebook uses Phabricator (http://phabricator.org/) for code reviews, and has a Continuous Integration system called Sandcastle which integrates well with Phabricator. We got Sandcastle to run tests whenever a diff was created or updated, and report the result to the diff.

#### **Automate**

To get to automation, we first had to lay some groundwork. We added states to rollouts (running, done, error), and made the script warn if the previous rollout was not in "done" state. We added an abort button in the UI which would change the state to "abort," and got the script to check the state occasionally and react. We also added full commit tracking; instead of Sauron only knowing the latest commit which had passed tests, it now had a record for every commit in master, and knew the test status of each specific one.

Then we automated the remaining decisions which humans needed to make. The first decision was which commit to roll out. The initial algorithm was to always select a commit which had passed tests and select as few commits as possible -- never more than three. If every commit had passed tests, it would select one new commit each time, and there could be at most two consecutive commits with non-passing test runs. The second decision was whether the rollout was successful. If more than 1% of hosts failed to deploy, it would be considered failed.

At this point, doing a rollout when things were normal simply consisted of answering "yes" a couple times (accepting the suggested commit, starting the canary, and continuing to the full deploy). So we allowed these questions to be answered automatically, and got Jenkins to run the rollout script. At first engineers implementing this only enabled Jenkins when they were at their desks supervising, until they didn't need to supervise it anymore.

While we were doing continuous deployment at this stage, it wasn't completely smooth yet. There were a couple kinks to work out.

#### **Test failures**

Engineers would often land diffs that broke tests, which would cause all subsequent master commits to also fail tests, and thereby prevent anything from being deployed. The oncall would need to notice this, revert the offending commit, wait for tests to pass on the revert, and then manually roll out the entire backlog before the automation could continue. This defeated one of the main advantages of continuous deployment, which was deploying very few commits per rollout. The problem here was that tests were slow and unreliable. We made various optimizations to get tests running in five minutes instead of 12-15 minutes, and fixed the test infrastructure problems that were causing them to be unreliable.

#### **Backlogs**

Despite these improvements, we still regularly have a backlog of changes that need to be deployed. The most common cause is canary failures (both false and true positives), but there are occasionally other breakages. When the cause was resolved, the automation would pick up and deploy one commit at a time, so it would take a while to clear the backlog and cause significant delays for newly landed diffs. The oncall would usually step in and deploy the entire backlog at once, which defeats one of the main advantages of continuous deployments.

To improve this, we implemented backlog handling in the commit selection logic, which made the automation deploy multiple commits when there was a backlog. The algorithm is based on setting a time goal in which to deploy every commit (30min). For each commit in the queue, it calculates the time remaining to meet the goal, the number of rollouts that can be done in that time (using a hard-coded value), and the number of commits that would have to be deployed per rollout. It takes the maximum commits/rollout value, but caps it at three. This allows us to do as many rollouts as possible, while getting every commit out in a reasonable time.

One specific cause of backlogs was that rollouts got slower as the size of our infrastructure increased. We got to a point where ssh-agent pegged an entire core authenticating SSH connections, and the fab master process also pegged a core managing all the tasks. The solution here was to switch to Facebook's distributed SSH system.

### Guiding principles

So what do you need in order to implement something similar to what we've done? There are a few key principles which make our system work well, which you can apply to your own.

  1. **Tests:** The test suite needs to be fast. It needs to have decent coverage, but doesn't necessarily have to be perfect. The tests need to be run often: during code review, before landing (and ideally blocking lands on failure), and after landing.
  2. **Canary:** You need an automated canary to prevent the really bad commits from being deployed to the entire fleet. It doesn't need to be perfect, however -- even a very simple set of stats and thresholds can be good enough.
  3. **Automate the normal case:** You don't have to automate every situation; just automate the known, normal situations. If anything is abnormal, make the automation stop and let humans step in.
  4. **Make people comfortable:** I think that a big barrier to this kind of automation is when people feel disconnected and out of control. To address this, the system needs to provide good visibility into what it has done, is doing, and (preferably) is about to do. It also needs good stop mechanisms.
  5. **Expect bad deploys:** Bad changes will get out, but that's okay. You just need to detect this quickly, and be able to roll back quickly.

This is something that many other companies can implement. Continuous deployment systems don't need to be complex. Start with something simple that focuses on the principles above, and refine it from there.

### What's next

This system is working well for us at the moment, but there are further challenges which we will face and improvements we'd like to make.

  * **Keeping it fast:** Instagram is growing quickly, and as such the commit rate is going to continue to increase. We need to keep the rollout fast in order to maintain very few commits per rollout. One possibility here is to split the rollout into multiple stages and implement pipelining.
  * **Adding canarying:** As the commit rate increases, canary failures and backlogs are going to impact more and more developers. We want to stop more bad commits from getting into master and blocking deployment, and so we're implementing canarying as part of Landcastle. After tests pass, Landcastle will test the change with production traffic and fail the land if it doesn't pass the canary thresholds.
  * **More data:** We want to improve the canary's detection capabilities, so we're planning to collect and check more stats like per-view function response codes. We're also experimenting with collecting stats from a set of control machines and comparing those to the canary stats, instead of the current static thresholds.
  * **Improving detection:** It would be good to reduce the impact of bad commits not being caught by the canary. Instead of testing on one machine and then deploying to the entire fleet, we could add more stages in between (a cluster or a region), checking metrics at that level before continuing.
