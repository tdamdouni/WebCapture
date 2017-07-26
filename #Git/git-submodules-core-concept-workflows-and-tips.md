# Git Submodules: Core Concept, Workflows, And Tips

_Captured: 2017-02-22 at 19:11 from [dzone.com](https://dzone.com/articles/core-concept-workflows-and-tips?edition=271915&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-22)_

### Submodules are an essential part of Git development, so it's important to know exactly how they work and some best practices in using them.

[Bitbucket](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

Including submodules as part of your [Git development](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=core-concept-workflows&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) allows you to include other projects in your codebase, keeping their history separate but synchronized with yours. It's a convenient way to solve the vendor library and dependency problems. As usual with everything `git`, the approach is opinionated and encourages a bit of study before it can be used proficiently. There is already good and detailed information about `submodules` out and about so I won't rehash things. What I'll do here is share some interesting things that will help you make the most of this feature.

## Core Concept

First, let me provide a brief explanation on a core concept about submodules that will make them easier to work with.

**Submodules are tracked by the exact _commit_ specified in the parent project, not a branch, a ref, or any other symbolic reference.**

They are _never_ automatically updated when the repository specified by the submodule is updated, only when the parent project itself is updated. As very clearly expressed in the Pro Git chapter mentioned earlier:

When you make changes and commit in that [submodule] subdirectory, the superproject notices that the HEAD there has changed and records the exact commit you're currently working off of; that way, when others clone this project, they can re-create the environment exactly.

Or in other words :

[...] git submodules [...] are static. Very static. You are tracking specific commits with git submodules - not branches, not references, a single commit. If you add commits to a submodule, the parent project won't know. If you have a bunch of forks of a module, git submodules don't care. You have one remote repository, and you point to a single commit. Until you update the parent project, nothing changes.

## Possible Workflows

By remembering this core concept and reflecting on it, you can understand that `submodule` support some workflows well and less optimally others. There are at least three scenarios where submodules are a fair choice:

  * When a component or subproject is changing too fast or upcoming changes will break the API, you can lock the code to a specific commit for your own safety.
  * When you have a component that isn't updated very often and you want to track it as a vendor dependency. I do this for my vim plugins for example.
  * When you are delegating a piece of the project to a third party and you want to integrate their work at a specific time or release. Again this works when updates are not too frequent.

Credit to _finch_ for the well-explained scenarios.

## Useful Tips Incoming

The submodule infrastructure is powerful and allows for useful separation and integration of codebases. There are however simple operations that do not have a streamlined procedure or strong command line user interface support.

If you use git submodules in your project you either have run into these or you will. When that happens you will have to look the solution up. Again and again. Let me save you research time: Instapaper, Evernote or old school bookmark this page, and you will be set for a while.

So, here is what I have for you:

## How to Swap a Git Submodule With Your Own Fork

This is a very common workflow: you start using someone else's project as submodule but then after a while, you find the need to customize it and tweak it yourself, so you want to fork the project and replace the submodule with your own fork. How is that done?

The submodules are stored in `.gitmodules`:
    
    
    $ cat .gitmodules [submodule "ext/google-maps"] path = ext/google-maps url = git://git.naquadah.org/google-maps.git

You can just edit the URL with a text editor and then run the following:

This updates `.git/config`, which contains a copy of this submodule list (you could also just edit the relevant `[submodule]` section of `.git/config` manually).

## How Do I Remove a Submodule?

It is a fairly common need but has a slightly convoluted procedure. To remove a submodule you need to:

  1. Delete the relevant line from the `.gitmodules` file.
  2. Delete the relevant section from `.git/config`.
  3. Run `git rm --cached path_to_submodule` (no trailing slash).
  4. Commit and delete the now untracked submodule files.

## How Do I Integrate a Submodule Back Into My Project?

Or, in other words, how do I un-submodule a git submodule? If all you want is to put your submodule code into the main repository, you just need to remove the submodule and re-add the files into the main repo:

  1. Delete the `.gitmodules` file **or** if you have more than one submodules edit this file removing the submodule from the list: 
  2. Remove the `.git` metadata folder (**make sure you have backup of this**): 
  3. Add the `submodule` to the main repository index: 

**NOTE:** The procedure outlined above is _destructive_ for the history of the submodule, in cases where you want to retain a congruent history of your submodules you have to work through a fancy "merge". For more details, I refer you to [this very complete Stack Overflow reference](http://stackoverflow.com/questions/1759587/un-submodule-a-git-submodule).

## How to Ignore Changes in Submodules

Sometimes your `submodules` might become `dirty` by themselves. For example if you use git `submodules` to track your vim plugins, they might generate or modify local files like `helptags`. Unfortunately, `[git status`](https://www.atlassian.com/git/tutorials/inspecting-a-repository/git-status) will start to annoy you about those changes, even though you are not interested in them at all, and you have no intention of committing them.

The solution is very simple. Open the file `.gitmodules` at the root of your repository and for each submodule you want to ignore add `ignore = dirty`, like in this example:
    
    
    [submodule ".vim/bundle/msanders-snipmate"] path = .vim/bundle/msanders-snipmate url = git://github.com/msanders/snipmate.vim.git ignore = dirty

## Danger Zone! Pitfalls Interacting with Remotes

As the [Git Submodule Tutorial](https://git.wiki.kernel.org/index.php/GitSubmoduleTutorial) on kernel.org reminds us, there are a few important things to note when interacting with your remote repositories.

The first is to **always publish the submodule change before publishing the change to the superproject that references it**. This is critical, as it may hamper others from cloning the repository.

The second is to always **remember to commit all your changes before running `git submodule update`** as if there are changes they will be overwritten!

## Conclusions

Armed with these notes you should be able to tackle many common recurring workflows that come up when using submodules. In a future post, I will write about alternatives to `git submodule`.

Follow me @durdn and the awesome @AtlDevtools team for more DVCS rocking.

[Bitbucket is the Git solution](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)
