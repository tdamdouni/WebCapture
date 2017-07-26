# Oh shit, git!

_Captured: 2017-02-10 at 11:06 from [ohshitgit.com](http://ohshitgit.com/)_

## [Oh shit, I did something terribly wrong, please tell me git has a magic time machine!?!](http://ohshitgit.com/)
    
    
    git reflog
    # you will see a list of every thing you've done in git, across all branches!
    # each one has an index HEAD@{index}
    # find the one before you broke everything
    git reset HEAD@{index}
    # magic time machine

You can use this to get back stuff you accidentally deleted, or just to remove some stuff you tried that broke the repo, or to recover after a bad merge, or just to go back to a time when things actually worked. I use `reflog` A LOT. Mega hat tip to the many many many many many people who suggested adding it!
    
    
    # make your change
    git add . # or add individual files
    git commit --amend
    # follow prompts to change or keep the commit message
    # now your last commit contains that change!

This usually happens to me if I commit, then run tests/linters... and FML, I didn't put a space after the equals sign. You could also make the change as a new commit and then do `rebase -i` in order to squash them both together, but this is about a million times faster.
    
    
    git commit --amend
    # follow prompts to change the commit message

Stupid commit message formatting requirements.

## [Oh shit, I accidentally committed something to master that should have been on a brand new branch!](http://ohshitgit.com/)
    
    
    # create a new branch from the current state of master
    git branch some-new-branch-name
    # remove the commit from the master branch
    git reset HEAD~ --hard
    git checkout some-new-branch-name
    # your commit lives in this branch now :)

Note: this doesn't work if you've already pushed to origin, and if you tried other things first, you might need to `git reset HEAD@{number}` instead of `HEAD~`. Infinite sadness. Also, many many many people suggested an awesome way to make this shorter that I didn't know myself. Thank you all!
    
    
    # undo the last commit, but leave the changes available
    git reset HEAD~ --soft
    git stash
    # move to the correct branch
    git checkout name-of-the-correct-branch
    git stash pop
    git add . # or add individual files
    git commit -m "your message here"
    # now your changes are on the correct branch

A lot of people have suggested using cherry-pick for this situation too, so take your pick on whatever one makes the most sense to you!
    
    
    git checkout name-of-the-correct-branch
    # grab the last commit to master
    git cherry-pick master
    # delete it from master
    git checkout master
    git reset HEAD~ --hard
    
    
    git diff --staged

Git won't do a diff of files that have been `add`-ed to your staging area without this flag. File under ¯\\_(ツ)_/¯ (yes, this is a feature, not a bug, but it's baffling and non-obvious the first time it happens to you!)
    
    
    cd ..
    sudo rm -r fucking-git-repo-dir
    git clone https://some.github.url/fucking-git-repo-dir.git
    cd fucking-git-repo-dir

Thanks to [@viaz66](https://twitter.com/viaz66) for this one.
