# Get Started with Git and Github

_Captured: 2015-10-25 at 10:27 from [www.floraworley.com](http://www.floraworley.com/posts/learn_git_github/)_

………………………………………………………………………

## What is Git?

Git is a version control system (VCS)--a tool that allows individuals and teams to work on a project while retaining control over the evolution of its codebase over time.

  * Git is open sourced; development was led by Linus Torvalds, creator of Linux

  * Git is written in the C language, making it high-performing and very fast

  * Git is distributed: you, the developer, clone the entire repository--the whole history of your project's source code--instead of a snapshot of the latest version. This means that if there is a crash on the main server, there are many copies that survive.

  * This means that unlike other VCSs, Git allows you to work locally: you only need to communicate with your team's development server when you are ready to add your contribution to the source code or clone the source code to use locally (ie, "push", "pull", "fetch", or "clone").

  * Git generally only adds data, and it is very difficult to do anything that is undoable/lose data

  * Git's branching system supports many different types of workflows, including:

    * Subversion-Style: developers push directly to shared repository;

    * Integration Manager: developers push to their own repositories, which are then sent to gatekeeper to commit to main, "blessed" repository;

    * Dictator and Lieutenants: same as above, except for larger projects and with extra layer of gatekeepers assigned to individual parts of project   
  


## What is Github?

GitHub is a commercial, web-based service for hosting Git repositories. Github integrates the core features of Git with social and ancillary features. Github provides free accounts for hosting open-source projects, and premium accounts for private, proprietary projects.

  * Github was launched in SF in 2008 by Github, Inc (a company started by developers Chris Wanstrath, PJ Hyett, and Tom Preston-Werner)

  * Github is written in Ruby on Rails and Erlang

  * Github is the most popular open source code repository site in the world

  * Included under the Github umbrella are services Gist (code snippets), Speaker Deck (presentations), and Guages (web analytics)

  * There are client GUI apps for Mac, Windows, and Linux (though we'll use command line)

  * Two main Github methodologies:

    * Fork and Pull: Popular with open source projects, lets anyone fork an existing repo and push changes to their personal fork without granting access to source repo. Any changes must then be pulled into the source repo by the project maintainer.

    * Shared Repository Model: Popular with small teams and organizations collaborating on private projects, everyone is granted push access to a single shared repository and topic branches are used to isolate changes.   
  
  


## Git Structures

### I. The Tree Metaphor:

Most VCSs employ a tree metaphor to describe repositories (or "repos").

A _repository_ is the collection of files and directories that make up your project, as well as a list of changes to those files that are made over the life of your project.

_A repo can contain the following branches:_

**Master branch** (also sometimes referred to as the "trunk" or "production" branch):

  * the current state of files in your project
  * the "master copy" of your source code should reflect the most recent release of your project
  * automatically created at "git init"
  * is persistent through the life of your project.   


**Develop branch**:

  * a copy of the master that runs in parallel to it
  * optional, but common
  * allows teams to continue to develop in a separate branch, while maintaining the most recently released version of your software in the master
  * needs to be created manually in the origin (alongside, and not within, the master; see below)
  * and should remain persistent through the life of your project   


**Topic branches** (also called "feature branches," "release branches," "hotfix/bugfix branches" depending on content):

  * provide a way to break a project up into pieces to facilitate small-team and parallel development paradigms
  * also optional, but common
  * need to be created manually by branching off from the develop branch and will be merged back into the develop branch (or master, if not using a develop branch)
  * may be added and deleted throughout the life of your project.   
  


_Two contexts for project branches_:

**Local branch**: A branch that exists locally on your machine, such as a repo that you've created locally inside an existing project folder (using "git init") or one that you've cloned to your machine from a fork of another Github user's project.

**Remote branch/repo**: While it's fine to have working repos existing on your machine locally, it's really best to have a remote master for the safety of your code and to enable collaboration. A remote master is the copy of the repo that is hosted on a server that's accessible to other people--either Github's or your company's, most likely. This remote repo is referred to as the origin in order to differentiate its branches from copies that are held locally. Though beyond our purview here, you may have multiple remotes.

### II. The Three States:

_Git has three main states that your files can reside in on your machine_:

**Committed**: the data is safely stored in your local database

**Modified**: you have changed a file, but have not yet committed it to your db

**Staged**: you have marked a file in its current version to go into your next commit

_These three states correspond to three main sections of a git project:_

**Git directory** (repo): An essential part of Git, this directory stores the metadata and object database for your project; it is what is copied when you clone a project.

**Working directory**: a single "checkout" (or working copy) of one version of the project, these files are pulled out of the Git directory and placed on disk for you to use or modify.*

**Staging area** (also sometimes called the "index"): a simple file, generally contained in your Git directory, that stores information about what will go in your next commit.**

**Basic workflow**:

  1. Create Git directory

  2. Run "git init" and create branches

  3. Modify files in active/working directory

  4. Stage files to be committed

  5. Commit files to Git directory   
  


**Commit**: A commit is essentially a snapshot of all the files in your project at a particular point in time. After your first commit, Git will only save files that have changed.*** **Rule of thumb: Commit early and often!**

**Push**: Note that until you "push", everything you commit remains local on your machine--ie, committing just takes a snapshot to be moved in a push. To get code on Github, we need to connect your local repo to your Github account (see next section).

_* Files in your working directory can be in one of two states: tracked--files that were in your last commit--and untracked--everything else (not committed, not staged)._

_You may choose to skip the staged phase entirely; a reason not to skip this step is so you don't have to commit your entire working directory, just the parts that you've modified. Staging allows one to more easily divide small changes into separate commits so that you can more easily roll back changes if you need to without the performance drain of recommitting code over and over._

*_Warning: Git will do its best to compress files, but large files can cause your repo to become unwieldy. Try to avoid committing things like compressed files (.zips, etc), compiled code (object files, libraries, executables), database backups, and media files (psd, flv, etc)._

## Git Commands for Basic Use

### Getting Started

(Note: this section is based on the GitHub "Help" pages at the top of: <https://help.github.com/>)

#### Create a new remote repo:

If using Github for hosting your remote repo, begin by logging into your account online and then clicking on "New Repository." Fill out form and click "Create repository." That's it!

#### Fork an existing repo:

_If building off of or contributing to an already existing Github project._

  1. **Fork repo**: On the Github page for the project you want, find the "Fork" button near the top and click.   

  2. **Clone your fork**: While you have now forked the project, it still only exists on Github. In order to work on it, you will need to clone it to your local machine by running the following code. This will clone your fork of the repo into the current directory you are in in the Terminal:
    
        $ git clone https://github.com/username/project_name.git
    

  3. **Configure remotes**: When a repo is cloned, it has a default remote called origin that points to your fork on Github, not to the original repo it was forked from. To keep track of the original repo, you need to add another remote named "upstream":
    
        $ cd projectName
    # changes active directory in prompt to the newly cloned "projectName" directory
    
    $ git remote add upstream https://github.com/username/project_name.git
    # assigns the original repo to a remote called "upstream"
    
    $ git fetch upstream
    # pulls in any new changes not present in your local repo, without modifying your files
    

  4. **Go to work:**

**Create a local Git directory and a README file**:

README is a standard include for all projects that will describe your project; provide documentation for how to use/install it; and perhaps list contact information or whether you are looking for particular contributions, etc.

** If you are starting version control on an existing directory for a project already in progress, skip step 1 "mkdir" and cd into that project's directory **
    
        $ mkdir ~/projectName
    # Creates a directory for your project called “projectName” in your user directory
    
    $ cd ~/projectName
    # Changes working directory to your new project directory
    
    $ git init
    # Sets up the necessary git files in project file with a .git extension (ie, will create a projectName.git directory
    
    $ touch README
    # Create a file called “README” in your projectName directory
    

**Commit your README file**:
    
        $ git add README
    # stages the file, adding to the list of files to be committed`
    

**Push your commit**:
    
        $ git remote add origin https://github.com/username/projectName.git
    # Creates a remote repo named “origin” that points at your Github repo
    
    $ git push origin master
    # Sends your commits in the master branch to Github
    # Process is exactly the same if pushing to project owned by someone else (ie, related to pull requests)
    

  


### Branching and Merging

**Create new branch**:
    
    
    $ git branch branchName
    # Creates new branch
    

**Make active branch**:
    
    
    $ git checkout branchName
    # Makes working branch; also will switch you to a new branch to work in
    

Or, use:
    
    
    $ git checkout –b branchName
    # Create new branch and make working branch shorthand
    

**List branches**: in your Git directory
    
    
    $ git branch
    # lists all branches; current working branch is marked with a “*” (star)
    

**Switch between branches**: same as "Make active branch"

_When you switch between branches, the files that you work on (the "working copy") are updated to reflect the changes in the new branch. If you have changes you have not committed, Git will ensure you do not lose them. Git is also very careful during merges and pulls to ensure you don't lose any changes._

**Merge branches**: When you are finished working on a branch and are ready to merge it back into its parent (say the develop branch or the master branch). You must merge from within the parent branch.
    
    
    $ git checkout master
    # Makes “master” the active branch
    
    $ git merge branchName
    # Merges commits from branchName to master
    

**Delete a branch**: if/when done with it
    
    
    $ git branch –d branchName
    # deletes branchName branch
    

### Snapshotting, Tracking, and Updating Commands

**add**: Adds files to the staging area to be committed
    
    
    $ git add README
    # adds README to staging area
    
    $ git add .
    # specifies active directory to recursively add all files in a new project
    

**status**: Gives us the state of our project, such as whether files are tracked/untracked
    
    
    $ git status
    # will give the current status of current active file
    
    $ git status –s
    # gives basic info (A = added M=Modified D=Directory, and so on)
    

**diff**: Output a description of the changes that are staged or modified and unstaged.
    
    
    $ git diff
    # Display code that has been changed since last commit, but that has not yet been staged. Adding –-cached at the end will show you staged changes.
    # Diff can also be used to see the absolute changes b/t any two commits.
    
    $ git diff v0.9
    # Shows you what has changed since the last release (ie, since v0.9)
    

**commit**: Takes a snapshot of staging area to be pushed. Always incl. comment with -m!
    
    
    $ git commit –m ‘Latest change to foo function’
    # commits the staged changes in active file, along with the –m ‘message’
    

**push**: move/copy branches and data (commits) to remote repository
    
    
    $ git push remoteRepoAlias branchName
    # pushes changes in local branchName branch up to remoteRepoAlias repo
    # If you get an error, means branch pushing to has changed since you pulled it down. You will need to fetch and merge the remote branch and push again,
    

**remote**: list, add and delete remote repository aliases
    
    
    $ git remote
    # list your remote aliases
    
    $ git remote add
    # add a new remote repository for your project
    

**log**: Show the commit history of a branch
    
    
    $ git log
    # lists commit history of active branch; adding --graph will show topology graph
    

#### Other useful commands:

**reset**: Undo changes and commits

**rm**: Remove files from staging area

**stash**: Save changes made in current index and working directory for later

**tag**: tag a point in history as important

## Moving things around in Git (and clearing up some grey areas)

#### "Merge" vs "Rebase":

_There are two ways to combine branches--merge and rebase._

**merge**: Most of the time you'll be using "git merge", which takes the changes made on one branch and adds them to another. Merge will not only take care of additions and deletions, but is also very good with modifications. There are some situations that will cause merge conflicts that require our intervention to resolve--for example, if the same block of code is edited in two different branches. In such cases, you will receive an error message asking you to "fix conflicts and then commit the result."
    
    
    $ git checkout master
    # switch to branch to be merged into
    
    $ git merge branchName
    # merge in any changes from branchName branch
    

**rebase**: Sometimes merges create a messy situation in your Git history--for that situation, rebasing allows you to take all the changes that were committed on one branch and replay them on another one to preserve a linear history. However, DO NOT rebase commits that you have pushed to a public repository. Think of rebase as a useful way to clean up commits BEFORE YOU PUSH them, and never rebase commits that have been available publicly.
    
    
    $ git checkout branchName
    # Switch to branch to be rebased
    
    $ git rebase master
    # rebase branchName to master
    

#### "Pull" vs "Fetch":

_There are two ways to get commits from a remote repo or branch--fetch and pull._

**fetch**: This is particularly useful if you need to keep your repo up to date but are working on something that might break if you update your files. Fetch retrieves any commits from the target remote that you do not have, but does not merge them with your current branch. To integrate the commits into your local branch, you use "git merge," which combines the specified branches and prompts you if there are any conflicts.
    
    
    $ git fetch upstream
    # pulls in any new changes not present in your local repo without modifying your files
    

**pull**: in "git pull", git tries to do your work for you. It is context sensitive, so Git will merge any pulled commits into the branch you are currently working in. Because "git pull" automatically merges the commits without letting you review them first, if you don't closely manage your branches you may run into frequent conflicts.
    
    
    $ git pull upstream
    # pulls commits from 'upstream' and merges them in active branch
    

## Work Collaboratively and Git Social on Github

**Follow a friend**: once on page of someone you want to follow, click "Follow" button--that's it!

**Watch a Project**: Once you're on the project page, click the "Watch" button; when the project is updated, you will see an update on your dashboard.

**Contribute to a project--Forks and Pull Requests**: If you aren't creating your own project from scratch, you'll most likely start by creating a fork of an existing project (that is, creating a copy of the original repo on Github that will serve as the remote repo for your local clone).

Things you can do after forking:

  * Push commits

  * Pull in upstream changes (changes other people have already committed to original project):

`$ git merge upstream/master # merges any changes fetched into your working file`

  * Create branches

  * Submit pull requests (see below)

  * Unwatch the main repo (if you're getting unwanted updates about a repo; use button "Unwatch" on main repo page)

  * Delete your fork (if you no longer plan to work on the project):

Warning: deleting a **private** repo will delete all its forks as well*

  * go to settings page for the repo, and click "delete this repository"

  * read warnings and enter name of repo/fork you wish to delete

  * confirm by clicking "I understand…"

**Submit a Pull Request**: When you are ready to submit your changes to the project's owner/manager, it's time to submit a pull request by clicking the "Pull Request" button on the _original_ project's Github page. For details on submitting and/or handling pull requests, see <https://help.github.com/articles/using-pull-requests>.

**Report Issues**: When collaborating with other people on a project, you will inevitably come across problems that need to be fixed. To help you keep track of these problems, each Github repo has a section called Issues. To add to the list, just click "New Issue" button on this page.

**Organizations**: If you want to collaborate with multiple developers on one project, you can manage everyone with Organizations. With an organization you can establish teams with special permissions, have a public organization file, and keep track of activity.

### Sources and References

<http://git-scm.com/book/en>

<http://learn.github.com/p/intro.html>

<https://help.github.com/articles>

<http://www.sitepoint.com/the-designers-guide-to-git-or-how-i-learned-to-stop-worrying-and-love-the-repository/>

<http://gitref.org/branching/>

<http://nvie.com/posts/a-successful-git-branching-model/>

<http://stackoverflow.com/questions/9529497/what-is-origin-in-git>

<http://stackoverflow.com/questions/6802928/why-is-there-a-staging-process-in-git>

Tags: t u t o r i a l s
