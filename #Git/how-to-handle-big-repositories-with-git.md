# How to Handle Big Repositories With Git

_Captured: 2017-03-03 at 19:31 from [dzone.com](https://dzone.com/articles/how-to-handle-big-repositories-with-git?edition=273883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-03)_

`[git` is a fantastic choice for tracking the evolution of your code base](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=how-to-handle-big-repos&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) and to collaborate efficiently with your peers. But what happens when the repository you want to track is **really** huge?

In this post, I'll try to give you some ideas and techniques to deal properly with the different categories of **huge**.

## Two Categories of Big Repositories

If you think about it there are broadly two major reasons for repositories growing massive:

  * They accumulate a very very long history (the project grows over a very long period of time and the baggage accumulates)
  * They include huge binary assets that need to be tracked and paired together with code.
  * Both of the above.

So a repository can grow in two _orthogonal_ directions: The size of the working directory -- i.e. the latest commit -- and the size of the entire accumulated history.

Sometimes the second category of problem is compounded by the fact that old deprecated binary artifacts are still stored in the repository, but for that has a moderately easy -- if annoying -- fix, see below.

For the above two scenarios the techniques and workarounds are different -- though sometimes complementary -- and so let me cover them separately.

## Handling Repositories With Very Long History

Even though the bounds that identify a repository as **massive** are pretty high - for example the latest Linux kernel clocks at 15+ million lines of code but people seem happy to peruse it in full - very old projects that for regulatory/legal reasons have to be kept intact can become a pain to clone (Now to be transparent the Linux kernel is split in a historical repository and a more recent one, and requires a simple grafting setup to have access to the full unified history).

### Simple Solution Is a Shallow Clone

The first solution to a fast clone and to saving developers and systems time and disk space is to perform a `shallow clone` using git. A shallow clone allows you to clone a repository keeping only the latest `n` commits of history.

How do you do it? Just use the `\- -depth` option, for example:

Imagine you accumulated ten or more years of project history in your repository - for example for JIRA we migrated to `git` an 11 years old code base -, the time savings can add up and be very noticeable.

The full clone of JIRA is 677MB with the working directory being another 320+MB , making up for more than 47,000+ commits. From a quick check on the JIRA checkout a shallow clone took `29.5 seconds` compared to the `4 minutes 24 seconds` of a full complete clone with all the history. The disparity grows also proportionally to how many binary assets your project has swallowed over time. In any case build systems can greatly profit from this technique too.

#### Recent Git Has Improved Support for Shallow Clones

Shallow clones used to be somewhat impaired citizens of the `git` world as some operations were barely supported. But recent versions (1.9+) have improved the situation greatly and you can properly `pull` and `push` to repositories even from a shallow clone now.

### Partial Solution Is Filter-branch

For the huge repositories that have big binary cruft committed by mistake or old assets not needed anymore a great solution is to use `filter-branch`. The command allows to walk through the entire history of the project filtering out, _massaging_, modifying, skipping files according to predefined patterns. It is a very powerful tool in your `git` arsenal. There are already helper scripts available to identify big objects in your git repository, so that should be easy enough.

Sample usage of `filter-branch` (credit):

`filter-branch` has a minor drawback: Once you use `filter-branch`, you effectively rewrite the entire history of your project. All commit ids change. This requires every developer to re-clone the updated repository.

So in case you're planning to carry out a cleanup action using `filter-branch`, you should alert your team, plan a short freeze while the operation is carried out and then notify everyone that they should `clone` the repository again.

### Alternative to Shallow-Clone: Clone Only One Branch

Since `git 1.7.10`, of April 2012 you can also limit the amount of history you clone by cloning a single branch, like the following:

This specific hack would be useful for long running and divergent branches or if you have many branches. If you only have a handful of branches with very few differences you probably won't see a huge difference using this.

[Stack Overflow reference](http://stackoverflow.com/questions/1778088/how-to-clone-a-single-branch-in-git).

## Handling Repositories With Huge Binary Assets

The second category of big repositories is made up from code bases that have to track **huge binary assets**. Gaming teams have to juggle around huge 3D models, Web development teams might need to track raw image assets, CAD teams might need to manipulate and track the status of binary deliverables. So there are different categories of software team that run into this issue with `git`.

Git is not especially bad at handling binary assets, but it's not especially good either. By default `git` will compress and store all subsequent full versions of the binary assets, which is obviously not optimal if you have many.

There are some [basic tweaks that improve the situation](http://thread.gmane.org/gmane.comp.version-control.git/146957/focus=147598), like running the garbage collection `git gc`, or tweaking the usage of `delta` commits for some binary types in `.gitattributes`.

But it's important to reflect on the nature of you project's binary assets as the winning approach may vary. For example here are three points to check (thanks to [Stefan Saasen](https://twitter.com/stefansaasen) for the remarks):

  * For binary files that change significantly - and not just some meta data headers - the delta compression is probably going to be useless so the suggestion is to turn `delta off` for those files to avoid the unnecessary delta compression work as part of the repack
  * In the scenario above it's likely that those files don't zlib compress very well either so you could turn compression off with `core.compression 0` or `core.loosecompression 0`; That's a global setting that would negatively affect all the non-binary files that actually compress well so the suggestion makes sense if you split the binary assets in a separate repository.
  * It's important to remember that `git gc` turns the "duplicated" loose objects into a single pack file but again unless the files compress in any way that probably doesn't make any significant difference in relation to the resulting pack file.
  * Explore the tuning of `core.bigFileThreshold`. Anything larger than `512 MiB` won't be delta compressed anyway - without having to set `.gitattributes` \- so maybe that's something worth tweaking.

### Technique 1: Sparse Checkout

A mild help to the binary assets problem is [sparse checkout](http://schacon.github.io/git/git-read-tree.html#_sparse_checkout) (available since Git `1.7.0]`). This technique allows us to keep the working directory clean by explicitly detailing which folders you want to populate. Unfortunately, it does not affect the size of the overall local repository but can be helpful if you have a huge tree of folders.

What are the involved commands? Here's an example ([credit](http://vmiklos.hu/blog/sparse-checkout-example-in-git-1-7)):

  * Clone the full repository once: `git clone <repository-address>`
  * Activate the feature: `git config core.sparsecheckout true`
  * Add folders that are needed explicitly, ignoring assets folders:
* Read the tree as specified: `git read-tree -m -u HEAD`

After the above you can go back to use your normal `git` commands, but your work directory will only contain the folders you specified above.

### Technique 2: Use of Submodules

Another way to handle huge binary asset folders is to split those into a separate repository and pull the assets in your main project using [submodules](http://git-scm.com/book/en/Git-Tools-Submodules). This gives you a way a way to control when you update the assets. See more on submodules in these posts: [core concept and tips](https://blogs.atlassian.com/2013/03/git-submodules-workflows-tips/?_ga=1.256555208.213145851.1487618490) and [alternatives](https://blogs.atlassian.com/2013/05/alternatives-to-git-submodule-git-subtree/?_ga=1.256555208.213145851.1487618490).

If you go the way of the `submodules` way you might want to checkout the complexities of handling [project ](https://blogs.atlassian.com/2014/04/git-project-dependencies/?_ga=1.256555208.213145851.1487618490)[dependencies](https://blogs.atlassian.com/2014/04/git-project-dependencies/?_ga=1.256555208.213145851.1487618490), since some of the possible approaches to the huge binaries problem might be helped by the approaches I mention there.

### Technique 3: Use Git Annex or Git-Bigfiles

A third option for handling binary assets with `git` is to rely on an apt third party extension.

The first one I mention is [git-annex](https://git-annex.branchable.com/), which allows managing binary files with git without checking the file contents into the repository. `git-annex` saves the files in a special key-value store and only symbolic links are then checked into git and versioned like regular files. It is straightforward to use and the [examples are self-explanatory](https://git-annex.branchable.com/git-annex/).

The second one is [git-bigfiles](http://caca.zoy.org/wiki/git-bigfiles), a `git` fork that hopes to _make life bearable for people using Git on project hosting very large files_.

## Conclusions

[Don't give up the fantastic capabilities of `git` just because you have a huge repository history or huge assets. There are workable solutions to both problems.](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=how-to-handle-big-repos&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content)

Follow me @durdn and the awesome @AtlDevtools team for more DVCS rocking.
