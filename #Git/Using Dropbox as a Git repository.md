# Using Dropbox as a Git repository

_Captured: 2015-10-26 at 17:12 from [rogerstringer.com](http://rogerstringer.com/2012/04/16/using-dropbox-as-a-git-repository)_

I use github heavily, but I have a couple projects that I like to work on across multiple machines, but don't necessarily want to share them on github, and I already use private repositories…

I decided to use Dropbox as a git server to work with multiple machines as it gives you that extra version control in that you have git and Dropbox's built-in control.

It turns out it is actually pretty easy to set it all up so here are the quick steps for anyone who is interested (these are only applicable to Macs).

This is actually a great way to work collaboratively and remotely with other developers, or simply keep project files in sync between two different computers. In my case when working from home I'm usually on the Mac Mini and on the road with the Macbook Air so this works really well and allows me to work on the same project from different computers without the hassle of remembering to copy files across etc

  1. Firstly make sure you have the Dropbox app and Git installed on your Mac. If not, you can get Dropbox from [here](http://dropbox.com/download) (direct download link) and the latest version of Git from [here](http://git-scm.com/download).
  2. With Dropbox and Git installed, you need to create a bare repository which will be shared with your Dropbox account. Open a Terminal window in your Mac and do the following:
    
    
    $ cd ~/Dropbox
    $ mkdir -p repos/your-repo-name
    $ git init --bare repos/your-repo-name
    Initialized empty Git repository in /Users/xxxxxx/Dropbox/repos/your-repo-name/
    

  1. Now with our bare repository created, head to your project folder and let's start a local git repo and link it with the Dropbox one. If you already have a local repo, skip to step 4:
    
    
    $ cd ~/ProjectFolder
    $ git init .
    Initialized empty Git repository in /Users/xxxxx/ProjectFolder/
    $ git add .
    $ git commit --all -m "Initial commit"
    $ git remote add dropbox /Users/xxxxx/Dropbox/repos/your-repo-name/
    $ git push dropbox master
    

Essentially what we've done here was initialise a local repo, add and commit all files within that folder to the local repo. We then add a new remote location using the handle "dropbox" to this repo and finally push all the local changes to the "remote" repo (i.e. your Dropbox repo folder).

The rest is done automatically by Dropbox - your folder will be synced with your account and accessible from anywhere. For instance, if you wanted to clone the repo to a different machine, all you need to do is make sure Dropbox is installed and the folders are synced - and then issue the following command:
    
    
        $ cd ~/Projects
        $ git clone -o dropbox /Users/xxxxx/Dropbox/repos/your-repo-name/
    

If everything goes right, you should have a local copy of your remote repo already configured with your dropbox remote. You can start making changes to your project and when ready, push them back to the remote:
    
    
        $ git commit --all -m "Changes made!"
        $ git push dropbox master
    

And finally, when you want to sync the remote repository with your local copy, you can:
    
    
        $ git pull dropbox master
    

_You can also use github for mac as your git client, despite the name, it's not just for github projects._

**Roger Stringer** spends most of his time solving problems for people, and otherwise occupying himself with being a dad, cooking, speaking, learning, writing, reading, and the overall pursuit of life. He lives in Penticton, BC.

Connect: [Twitter](https://twitter.com/freekrai) | [Google+](https://www.google.com/+RogerStringer)   
This content is [supported by readers like you.](http://rogerstringer.com/support)
