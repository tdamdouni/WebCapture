# Git Strategies for Software Development: Part 2 - DZone DevOps

_Captured: 2019-07-25 at 08:30 from [dzone.com](https://dzone.com/articles/git-strategies-for-software-development-part-2?edition=507293&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202019-07-23)_

Please go through the [earlier article](https://dzone.com/articles/git-strategies-for-software-development) before reading this article. I will assume the strategy defined in first article is clear before reading ahead. This article will focus on multiple releases in parallel. A software team working on two or more releases at a time may refer to this strategy.

![Screen Shot 2019-07-16 at 1.11.36 AM](https://purviews.files.wordpress.com/2019/07/screen-shot-2019-07-16-at-1.11.36-am.png?w=736)

Let’s consider two releases starting in parallel from today.

  * _Release1: 1-month release date from today._

  * _Release2: 2-month release date from today._

First, we should create two release branches from production deployed codebase.

_Release1: Branch1 is the branch for Release1._

_Release2: Branch2 is the branch for Release2._

For simplicity, obvious branch names are used. Typically you will define a naming convention for branches based on your project needs, but a sample name convention can be _“ProjectName_ReleaseName_Year_Month_date_Version.”_

Once branches are created for release, the development team can start development on features specific to each release by creating a feature branch from the release branch and following a merge strategy as mentioned in [single release development.](https://dzone.com/articles/git-strategies-for-software-development)

A key point to note is that we have to regularly pull changes from the master branch to get any production fixes done during the release development time.

Once feature development is complete, we have to get it merged to the release branch after the review cycle.

The merged release branch should get tested by the QA team by creating a release tag from the release branch. Normally we would have multiple QA tags created to test all the features going in a release. Once QA team validation is complete, the release team or QA team should create a final release tag.

_Note: We should avoid having the development team create tags from the release branch. The release team should handle such task; if you don’t have a release team, QA can pitch in. _

_TagR1_ is final release tag created for Release1 from Release1-Branch1. Release1 should be released in production from tag “TagR1.”

Post-release, we have to merge the “TagR1” code to the Master branch to keep the Master branch up to date with production code. “TagR1” should be used for any production fix, after Release1, if needed.

Once Release1 is complete and the code for Release1 is moved to Master branch, “Release2-Branch2” branch will get all the changes done in production through a regular pull request from the Master branch.

Release 2 can follow the same approach done in Release1 for feature development.

Create a final release tag, “TagR2,” and move the code to production, and after release, merge Release2 code to production.

This approach will give us the flexibility to run multiple releases in parallel and handle any changes in the release plan.  In conclusion, here are a few points to remember during the release cycle

  1. Define proper naming conventions for branch and tags best suited for your project. 
    1. The branch name can be “_ProjectName_ReleaseName_Year_Month_date_Version_”
    2. The tag name can be “_Release_Year_Month_date_version_”
  2. Post-release activities like marking a tag as released, merging the final tag code to the Master branch, and margining all development branch code with new production code, should be done without fail to avoid any confusion.
  3. The development team should refrain from creating tags, maintaining branches or any release activities. It is advisable to have a release team for such activities.
  4. Follow the proper branch creation and merging process even for small changes in the codebase.

Finally, please refer [to this page](https://github.com/DharmendraRathor/gitCommands) for useful git commands.

Thanks for reading. Please leave a comment or advice for this or future write-ups.
