# Subdirectory Checkouts with git sparse-checkout

_Captured: 2016-03-01 at 23:48 from [jasonkarns.com](http://jasonkarns.com/blog/subdirectory-checkouts-with-git-sparse-checkout/)_

[8](http://jasonkarns.com/blog/subdirectory-checkouts-with-git-sparse-checkout/#comments)

If there is one thing I miss about SVN having switched to git (and trust me, it's the only thing), it is the ability to checkout only a sub-tree of a repository. As of version 1.7, you can check out just a sub-tree in git as well! Now not only does git support checking out sub-directories, it does it better than subversion!

## New Repository

There is a bit of a catch-22 when doing a sub-tree checkout for a new repository. In order to only checkout a sub-tree, you'll need to have the core.sparsecheckout option set to true. Of course, you need to have a git repository before you can enable sparse-checkout. So, rather than doing a git clone, you'll need to start with git init.

  1. Create and initialize your new repository:
    
        mkdir <repo> && cd <repo>
    git init
    git remote add –f <name> <url>

  2. Enable sparse-checkout:
    
        git config core.sparsecheckout true

  3. Configure sparse-checkout by listing your desired sub-trees in .git/info/sparse-checkout: 
    
        echo some/dir/ >> .git/info/sparse-checkout
    echo another/sub/tree >> .git/info/sparse-checkout

  4. Checkout from the remote:
    
        git pull <remote> <branch>

## Existing Repository

If you already have a repository, simply enable and configure sparse-checkout as above and do git read-tree.

  1. Enable sparse-checkout:
    
        git config core.sparsecheckout true

  2. Configure sparse-checkout by listing your desired sub-trees in .git/info/sparse-checkout: 
    
        echo some/dir/ >> .git/info/sparse-checkout
    echo another/sub/tree >> .git/info/sparse-checkout

  3. Update your working tree:
    
        git read-tree -mu HEAD

## Modifying sparse-checkout sub-trees

If you later decide to change which directories you would like checked out, simply edit the sparse-checkout file and run git read-tree again as above.

Be sure to read the [documentation on read-tree/sparse-checkout](http://schacon.github.com/git/git-read-tree.html#_sparse_checkout). The sparse-tree file accepts file patterns similar to .gitignore. It also accepts negations--enabling you to specify certain directories or files to **not** checkout.

Now there isn't _anything_ that svn does better than git!
