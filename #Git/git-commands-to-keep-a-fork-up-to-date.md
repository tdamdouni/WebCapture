# Git Commands to Keep a Fork Up to Date

_Captured: 2018-09-01 at 09:24 from [dzone.com](https://dzone.com/articles/git-commands-to-keep-a-fork-up-to-date?edition=387238&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-31)_

###  If using Git intimidates you, just look at these commands to understand how to keep a fork up-to-date. 

Easily enforce open source policies in real time and reduce MTTRs from six weeks to six seconds with the Sonatype Nexus Platform. See for yourself - [Free Vulnerability Scanner.](https://dzone.com/go?i=290455&u=https%3A%2F%2Fwww.sonatype.com%2Fsoftware-bill-of-materials%3Futm_campaign%3Ddzone%252520-%252520AHC%26utm_source%3DDZone%252520-%252520AHC%2525202018%26utm_medium%3DDZone%252520-%252520AHC%2525202018)

I've seen the following tweet about git making its way around Twitter recently:

![Image title](https://dzone.com/storage/temp/10073314-screen-shot-2018-08-24-at-31535-pm.png)

And it's true, you _can_ do most of your work with those commands.

What if you want to fork and contribute to an open source project on GitHub, GitLab or BitBucket though? You're going to need a few more commands so that you can keep your fork up to date, namely `remote`, `fetch` and `merge`. Let's see how they are used.

## Fork Away

When you fork a project, you make a copy of it under your own namespace. To work with the project you then clone the repository to your own machine. Let's use a repo I have forked as an example: [Twilio's Node.js package](https://github.com/philnash/twilio-node). After forking, we clone the repo:

We can now see the first use case for `remote`. Run `git remote` in the `twilio-node` directory and we see the following:

OK, that's not too useful, it just shows we have one remote repo called "origin". Running it again with the `\--verbose` flag shows a bit more information:

That's better, this shows that the remote repository is the one we cloned and that we can fetch from and push to it.

## Making Changes

When contributing something back to the repo, it is easiest to do so on a branch. That keeps the master branch clean and makes it easy to keep up to date. Setting up your changes is covered by the six commands Cory listed in his tweet; you create a new branch with `branch`, `checkout` the branch, make the changes you want, `commit` as many times as necessary and finally `push` the branch to the origin, your fork. Then you can create your pull request and hope it gets accepted.

Sometime later down the line you find you want to make another pull request, but the original repo has moved on. You need to update your fork so that you're working with the latest code. You could delete your fork and go through the process of forking and cloning the repo again, but that's a lot of unnecessary work. Instead, add the upstream repository as another remote for the repo and work with it from the command line.

## Adding the Upstream

To do this, we use the `remote` command again, this time to `add` a new remote. Find the original repo's URL and add it as a new remote. By convention this remote is called "upstream" though you can call it whatever you want.

Now if we inspect the repo's remotes again, we will see both the origin and the upstream. You can use `-v` as a shortcut for `\--verbose`.

## Fetching the Latest

To bring the repo up to date, we can now `fetch` the latest from the upstream repo. It looks like this:

`git fetch` downloads objects and refs from the repository, but doesn't apply it to the branch we are working on. We want to apply the updates to the master branch, so make sure it is checked out.

## Merging It All Together

To bring the master branch up to date with the remote `merge` the remote's master branch into our own, like so:

If you have kept your work off the master branch this will go ahead smoothly. Finally `push` these updates to the fork so that it is up to date too.

Now everything on the master branch of the fork is up to date. If you need to update a different branch, substitute the branch name master for the branch you are working with.

## Shortcuts

If you have been working with `git pull` then you may have already seen a potential shortcut. `pull` is the combination of `fetch` and `merge`, so to perform these two actions in one command you can run:

## Fork Happy

That's all you need to know for keeping your fork up to date when contributing to open source. Add the upstream as a new `remote` repo, `fetch` the upstream repo and `merge` the branch you want to update.

For more detail on the various commands here, take a look at "[Working with Remotes" from the Pro Git book](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes).

And remember, if you get stuck with something with git, check out [Oh shit, git!](http://ohshitgit.com/) for all your expletive based ways to save yourself.

Happy forking!

Automate open source governance at scale across the entire software supply chain with the Nexus Platform. [Learn more.](https://dzone.com/go?i=290456&u=https%3A%2F%2Fwww.sonatype.com%2Fwp-enforce-open-source-policies-with-confidence)
