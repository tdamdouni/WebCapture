# Managing Websites with Git

_Captured: 2015-10-25 at 13:12 from [jblevins.org](http://jblevins.org/log/managing-websites-with-git)_

Let's say you have a local Git repository on your workstation containing the source for a statically-generated website. You also have the `origin` repository stored on a server somewhere that also serves the website. The goal is to be able to edit files on the workstation and have the website update automatically once changes are pushed to the server.

For the sake of concreteness, I'll describe the setup I currently use for maintaining this site (let's call it `$SITENAME`). I have a content repository which contains (mostly) plain-text Markdown formatted source files. There is also a Perl script which reads some basic metadata from the Markdown files, applies Markdown and any other required text filters, and applies templates to generate XHTML files (lets call this step `$BUILD`). The site is hosted by a server, `$SERVERNAME`, which also serves as the `origin` remote for the Git repository. I edit the Markdown files on my workstation or laptop, commit the changes, and push them to the server which then rebuilds the site.

If the `content` repository for the site exists already and you want to create a bare repository on the server you can do the following:
    
    
    $ ssh $SERVERNAME
    $ cd /srv/git/$SITENAME
    $ mkdir content.git
    $ cd content.git
    $ git init --bare
    

Then, on the workstation, edit `content/.git/config` and add the `origin` remote:
    
    
    [remote "origin"]
        url = ssh://$SERVERNAME/srv/git/$SITENAME/content.git
        fetch = +refs/heads/*:refs/remotes/origin/*
    

You probably also want to configure Git to pull from the remote and merge with the `master` branch:
    
    
    [branch "master"]
        remote = origin
        merge = refs/heads/master
    

Now, push everything to the server with
    
    
    $ git push --all origin
    

To check to see if you can pull from it, run
    
    
    $ git pull
    

The server now has a bare repository with all of your revisions but there is no working copy containing the source files that will be needed to build the site. Create a clone of the repository with a working copy as follows:
    
    
    $ cd /var/www/$SITENAME
    $ git clone /srv/git/$SITENAME/content.git
    

The directory `/var/www/$SITENAME/content` now contains the source files. This working copy will be used to rebuild the site. There is however, a new problem: in addition to triggering a website rebuild, we need to make sure the working copy is kept up to date. We'll tackle both of these simultaneously.

I'm assuming there is some command you can run that will build the website. It may be a make rule or a Perl script, for example. Let's call this command `$BUILD`. I actually have more of a `$REFRESH` and `$REBUILD` system but the general idea is the same: `$BUILD` needs to be called on the server when something in the `content` repository changes.

Git provides several hooks that run before or after various events. Each hook is a shell script in the `.git/hooks/` directory:
    
    
    $ ls .git/hooks
    applypatch-msg  post-commit   post-update     pre-commit          pre-rebase
    commit-msg      post-receive  pre-applypatch  prepare-commit-msg  update
    

Git's `post-update` hook is exactly what we're looking for. On the server, do the following:
    
    
    $ cd /srv/git/$SITENAME/content.git/hooks
    $ $EDITOR post-update
    

By default, the file contains only a call to `git-update-server-info`:
    
    
    #!/bin/sh
    #
    # An example hook script to prepare a packed repository for use over
    # dumb transports.
    #
    # To enable this hook, make this file executable by "chmod +x post-update".
    
    exec git-update-server-info
    

We want to add commands to update the working copy in `/var/www/$SITENAME/content` and rebuild the site. **Before** the `exec` line, add something like the following (modify to suite your situation):
    
    
    # Update the working copy
    WORKDIR="/var/www/$SITENAME/content"
    exportGIT_DIR=$WORKDIR/.git
    pushd$WORKDIR> /dev/null
    git pull
    popd> /dev/null
    
    # Build the website
    $BUILD
    

The first section changes to the `$WORKDIR` containing your working copy and pulls the new changes. The second section simply runs your `$BUILD` command.

**It is important** that you be careful if you make changes to the working copy on the server. If you do, make sure you push them to the bare `origin` repository. Otherwise, when you push from the workstation there may be merge conflicts.

To active the hook, simply make it executable:
    
    
    $ chmod +x post-update
    

Now, when you run `git push` on the workstation, your changes are pushed to the repository on the server which in turn updates the working copy and triggers a rebuild.
