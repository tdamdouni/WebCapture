# Lesser Known Git Commands

_Captured: 2017-05-16 at 19:58 from [dzone.com](https://dzone.com/articles/lesser-known-git-commands?oid=twitter&utm_content=buffer53fd9&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Bitbucket](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

Git has a strong commitment to backwards compatibility: many powerful features are hidden behind options rather than exposed as default behavior. Fortunately, Git also supports _aliases_, so you can create your own commands that do all manner of Git magic. Here's a selection of the more useful (or at least entertaining) aliases defined in my _.gitconfig_:

## Git Please

Every developer has had the chat with their team lead about force pushing to a shared branch (i.e. don't do it). Rebasing, amending, and squashing. are all good fun right up until you rewrite some shared history and spill duplicate commits all over your repository. Fortunately, Git won't let you rewrite history on the server willy-nilly. You have to explicitly pass the _\--force _option to _git push_ to show you mean business. But force pushing is a bit heavy-handed: It stomps the upstream branch with your local version, and any changes that you hadn't already fetched are erased from history.

![](https://cdn-images-1.medium.com/max/800/1*rV0zYWOA8k5f_ixFXDF-aA.jpeg)_Quality meme courtesy of @tarkasteve_

Git's _\--force-with-lease _option is far more polite: it checks that your local copy of the ref that you're overwriting is up-to-date before overwriting it. This indicates that you've at least fetched the changes you're about to stomp. Since _git push --force-with-lease_ is rather a lot to type out each time, I've created a polite alias for it: _git please_

## Git Commend

Ever commit and then immediately realize you'd forgotten to stage a file? Fret no more! _git commend_ quietly tacks any staged files onto the last commit you created, re-using your existing commit message. So as long as you haven't pushed yet, no-one will be the wiser.

## Git It

The first commit of a repository can not be rebased like regular commits, so it's good practice to create an empty commit as your repository root. _git it_both initializes your repository and creates an empty root commit in one quick step. Next time you spin up a project, don't just add it to version control: _git it_!

## Git Staaash

_[git stash](https://www.atlassian.com/git/tutorials/git-stash/?utm_source=medium&utm_medium=blog&utm_campaign=lesser-git) _is one of the most delightful and useful Git commands. It takes any changes to tracked files in your work tree and _stashes_ them away for later use, leaving you with a clean work tree to start hacking on something else. However if you've created any _new_ files and haven't yet staged them, _git stash_ won't touch them by default, leaving you with a dirty work tree. Similarly, the contents of untracked or ignored files are not stashed by default.

I've created a few handy aliases to handle different variations of _git stash_, based on which bits of your work tree you need to stash:

If in doubt, the long one (_git staaash_) will always restore your worktree to what looks like a fresh clone of your repository.

## Git Shorty

I run _git status_ probably more than any other Git command. Git's inline help has gotten a lot more friendly over the years, which is excellent for beginners, but the output is overly verbose for those more familiar with Git. For example, _git status_ emits **18 lines** to tell me that I have a couple of staged, unstaged, and untracked changes:

_git shorty_ tells me the same thing in three lines:

(OK, so I actually have this aliased as _git st_ for brevity, but I couldn't resist.)

## Git Merc

If you're using a standard non-rebasing branching workflow, running a standard _git merge_ to combine feature branches with the master is actually not ideal. With no options, _git merge_ uses the _\--ff_ merge strategy, which will only create a merge commit if there are no new changes on the master branch, otherwise it simply "fast forwards" your master branch to point at the latest commit on your feature branch. Only _sometimes_ creating a merge commit makes it tricky to reason about which code was developed on which branches when looking through your git history.

![](https://cdn-images-1.medium.com/max/800/1*VYHiXlWZE6JIs4zEMxE4UQ.gif)

> _Git merc uses the --no-ff strategy, to always create a merge commit._

![](https://cdn-images-1.medium.com/max/800/1*0lNVIAH5g_MfMAloAnbyUQ.gif)

Incidentally, _\--no-ff_ is also what we use under the hood (by default) when merging pull requests in [Bitbucket.](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=lesser-known-git-commands&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content)

## Git Grog

My _git grog_ (or "**gr**aphical l**og**") alias has evolved over the years to the point where I'm no longer sure I understand exactly what it does. But it sure looks pretty:

![](https://cdn-images-1.medium.com/max/800/1*PgKTuG5-Qtrt_CqiCT35uw.png)

> _   
_

Here's the standard _git log_ for comparison:

![](https://cdn-images-1.medium.com/max/800/1*TFwMkiXknawT1N4cI0ycsw.png)

> _   
_

There are all sorts of pretty formats available, so fork the command above and make it your own!

## For the GUI Fans

If you're a Git GUI fan and using Mac or Windows, you might be using our free Git client: [Atlassian](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=lesser-known-git-commands&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) SourceTree. If so, you can take advantage of these aliases by creating a new _custom action -- _and optional keyboard shortcut -- in your SourceTree preferences:

![](https://cdn-images-1.medium.com/max/800/1*QKq8cnE1O9skf6ADYGc5lw.png)

Then you can access it via the _Actions_ -> _Custom Actions _menu, or your choice of keyboard shortcut:

![](https://cdn-images-1.medium.com/max/800/1*yIEAGTd_fhhvUOC9oaYbXA.png)

[Happy aliasing!](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=lesser-known-git-commands&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) If you have some neat Git aliases of your own, share them in the comments, or tweet me @kannonboy.

[Bitbucket is the Git solution](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

### Like This Article? Read More From DZone
