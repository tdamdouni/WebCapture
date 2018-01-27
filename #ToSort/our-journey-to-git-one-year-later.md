# Our Journey to Git—One Year Later

_Captured: 2017-12-06 at 20:07 from [dzone.com](https://dzone.com/articles/our-journey-to-gitone-year-later?edition=343098&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-06)_

[Learn more](https://dzone.com/go?i=250324&u=http%3A%2F%2Fblog.scalyr.com%2F2017%2F08%2Fcareerbuilder-resolves-customer-issues-5x-faster-scalyr%2F) about how CareerBuilder was able to resolve customer issues 5x faster by using Scalyr, the fastest log management tool on the market.

In my last [blog post](https://www.cqse.eu/en/blog/our-journey-to-git/), I outlined the obstacles we had to master when moving from Subversion to Git. Since then more than one year has passed and several of the assumptions we have once made no longer hold. This post describes what changes we had to make in our development process and build & deployment infrastructure due to migrating to Git and which improvements we gained.

## Development Process

### Feature Branches

In the beginning, we intended to continue development on Git as we did with Subversion: Having a master branch where all the development activity goes on and release branches that went through a stabilization phase. The release branches receive bugfixes only and are used for hotfixes after release.

However, in the last status meeting before the migration, we decided to perform a rather radical change and introduce feature branches on-top of the release-branch strategy. And we are quite strict with that: All bug-fixes and features must be developed on separate branches and reviewed before merge. My colleague Martin has already outlined [why we made this move](https://www.cqse.eu/en/blog/feature-branch-based-development/) and what benefits we gained.

As my colleague Elmar described, we have a [review process](https://www.cqse.eu/en/blog/change-based-vs-file-based-reviews/) that is tied to tickets in our issue tracker and covers all files that were touched during the development of a ticket. In order to track which files were already reviewed, we _rated_ them with a home-grown IDE plugin that persisted the review state (dirty, ready for review, reviewed) together with a checksum of the file content at the time of rating in the file header, so no files slip through review.

With the advent of feature branches, we suddenly faced lots of merge conflicts due to the review checksum being changed on multiple branches that are to be merged into master. Moreover, the per-file review status tracking is somewhat superfluous with feature branches as all changes that are to be reviewed are encapsulated on a branch.

We decided soon to ditch the file-based status tracking altogether with our home-grown Eclipse plugins. Instead, we are now using GitLab [Merge Requests](https://docs.gitlab.com/ee/user/project/merge_requests/) to track and review file changes for each branch (and thus each issue). Merging back to the master branch and also integration of master in a feature branch is now seamless most of the time with no unnecessary conflict interruptions. In addition, GitLab Merge Requests support our developers by showing the success of build and test execution and provide a one-click solution for merging the feature branch back to master.

The benefit of feature branches and reviews with merge requests is a master branch that is always ready for production as it contains only finished and reviewed features. We used this to change our release process as well. Previously we negotiated the features that have to go in a specific version and started implementing on _trunk_ until all features were finished. After the hot implementation phase, we stabilized _trunk_ for a few weeks.

Nowadays we have a fixed release cycle of six weeks. Features that are not implemented and reviewed after the six-week implementation period will simply be shifted to the next release. My colleague Martin already gave a good [summary of the rationale behind this decision](https://www.cqse.eu/en/blog/feature-branch-based-development/).

From an employee perspective, the biggest benefit is this fixed six-week schedule one can rely on. We aligned regular meetings and activities to this schedule and packed them on one day. So in one week, we spend Wednesday in planning meetings and in the following week we spend the day within maintenance groups to further improve our codebase. This leaves room for focused working without meeting-interruptions on other days.

## Development Infrastructure

Besides social and process related aspects we also had to change a lot in our development infrastructure.

At the time we migrated to Git we were still using Jenkins 1. We were setting up builds for our master branch, release branches and one build for all the feature branches (which are all prefixed with `cr/`). While we were able to tell which commit broke a test on master or a release branch, it was quite hard to tell on the feature branches, as builds were scheduled as commits were pushed. This left quite some burden on the shoulders of our developers to monitor Jenkins before merging branches to master and watch out for the _interesting_ build failure mail and ignore the ones from other branches.

Soon we decided to annotate the build status from Jenkins to GitLab via an API call. So we had at least a binary indicator whether build and tests pass. Moreover, GitLab also neatly visualizes this information on merge requests.

Still, we had no good way to distinguish whether a build fails due to compile errors or test failures. With the advent of build pipelines, we wanted to get a much better overview. Hence, we settled out to set up a fresh instance of Jenkins 2 with all these fancy new features: Separate builds for each branch, separation between compile, unit test, user interface test, and packaging.

Splitting the monolithic build into separate steps was no big issue - configuring Jenkins, however, was! There was still a lack of documentation of the new `Jenkinsfile` specification: Sending emails for build failures worked only with `try ... catch ...` blocks in the build script, annotating the build status to GitLab was failing due to some [classpath issue](https://github.com/jenkinsci/gitlab-plugin/issues/430) and almost every feature required a new plugin for Jenkins.

In the meantime, I was playing with the integrated GitLab CI solution for our in-house time and project management solution and I was quite satisfied with its simplicity. I convinced my colleagues to pilot GitLab CI for Teamscale continuous integration alongside Jenkins. After spending half a day we were already at the same level than with the Jenkins 2 setup, however, with no mail sending issues and the build status is (of course) automatically displayed in GitLab merge requests.

Still, there was a longer migration phase of moving all parts from the Jenkins build infrastructure as GitLab CI focuses on a simple approach. Nowadays, we even manage parametric builds and scheduled performance tests in GitLab. In fact, I've migrated the last bits of infrastructure jobs (website build, Slack bots) away from Jenkins and pulled the plug in the week of writing this post.

We use GitLab CI fully dockerized, this means each build is running in a separate Docker container. Setting this up just required to create several docker images that contain the required build tools (compile Java, compile C#, user interface testing, …). From this, we gained much larger reproducibility of test results and can ensure concurrent builds are not interfering with each other.

On the other side, we can use the Docker infrastructure to provide third-party systems for integration tests. We no longer need to host a test instance of, e.g., Redmine to test our connectors with, but can spin up a pre-configured instance in a container along with the main build container. Again, the gain is separating things that may otherwise conflict with each other. It further allows modification of the test container even for single branches.

## Summary

With the advent of Git, we changed not only our version control system. It changed--and gave us the freedom to change--the way we develop and build software. These changes were needed to maintain stability and quality of our software with a growing team of contributors. Looking back I doubt that all technical and social changes would have been possible with our old infrastructure--at least not without heavy burdens.

**[Find out more](https://dzone.com/go?i=250325&u=http%3A%2F%2Fblog.scalyr.com%2F2014%2F05%2Fsearching-20-gbsec-systems-engineering-before-algorithms%2F) about how Scalyr built a proprietary database that does not use text indexing for their log management tool.**
