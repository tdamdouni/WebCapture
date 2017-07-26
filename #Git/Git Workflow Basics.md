# Git Workflow Basics

_Captured: 2016-12-05 at 23:45 from [blog.codeminer42.com](https://blog.codeminer42.com/git-workflow-basics-d405746f6205#.cap0cm4z7)_

> This post is intended for beginners, but I assume you already know the basics of [Git usage](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository) (commit, push, pull, etc).

![](https://cdn-images-1.medium.com/freeze/max/30/1*ZUQfs6-kZYkSteBXhkls6A.png?q=20)![](https://cdn-images-1.medium.com/max/800/1*ZUQfs6-kZYkSteBXhkls6A.png)

You probably know how to use [Git](https://git-scm.com) on a daily basis. But knowing how to commit, push and pull isn't enough to **really** work with software development.

It doesn't matter if you use GitHub, Bitbucket, GitLab or Stash, one thing is true: you must follow a code review process to ensure your code has minimum quality standard.

This post will provide you a quick guide on how to use a "open source" workflow in your projects. As the name implies, it's the same workflow used on a whole bunch of open source projects out there.

Among the benefits of this workflow are the fact that your **work is completely isolated from everyone else's** and also the **reduction of error going to production**.

But hey:** use what works best for your team**. Some variations on this process are welcome as long as they improve your team's productivity.

### Working on Branches

Git allows you to work on branches. According to the [git documentation](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell):

> Branching means you diverge from the main line of development and continue to do work without messing with that main line.

In short, branches isolate the code you are currently working from the code your teammates are working. It's kinda a "parallel universe", or timeline.

> _the main line is your **master **branch (main code). See how each branch is isolated from the main code until a certain point_

To create a new branch, you just need to use the **_git checkout -b <branch_name> _**command:
    
    
    $ (master) git checkout -b my_new_branch
    
    
    > Switched to a new branch 'my_new_branch'

Once in a new branch, the workflow is the same. Create commits for your changes and push them to your repo (but **not** to master):
    
    
    [...] some commits [...]
    
    
    $ (my_new_branch) git push origin my_new_branch

The command above tells git: "hey dude, upload my local work (commits) on **my_new_branch** to the same branch on this remote (origin). If there is no **my_new_branch** there, create it". If you want your work to be uploaded to a different branch on your remote (other than **my_new_branch**), just use the command like this:
    
    
    $ (my_new_branch) git push origin my_new_branch:my_branch_on_remote

Ok, back on track. Now to move back to your **master** branch (or any other branch), you just need to use the git checkout command without the **_-b_** param:
    
    
    $ (my_new_branch) git checkout master
    
    
    > Switched to branch ‘master’
    
    
    $ (master) git checkout my_new_branch
    
    
    > Switched to branch ‘my_new_branch’

You can have more than one person working on the same branch as you, but that's not recommended. With one person per branch everyone can make their mess without worrying about disturbing someone else's work (like writing code that temporary breaks some part of the application, for example).

But someday you'll need to integrate your brand new feature back to your master right?

### Code review

Instead of merging your branch back to master right away, a good practice of software development is to request your new code to be reviewed by other team members before.

**This tends to increase the code quality of your app, since more people will take a look at it**, spotting improvements and even small bugs before it reaches production.

For beginners, this is an awesome way to learn new stuff from more experienced developers.

But how to get people to review your code? Ask them to pull your branch and look into every commit by hand? No way!

Most (if not all of) Git online repository services have a nice feature that makes code review be very easy.

#### Pull Requests

A pull request (or a merge request, if you use GitLab) can be defined as:

> Pull requests let you tell others about changes you've pushed to a repository on GitHub. Once a pull request is sent, interested parties can review the set of changes, discuss potential modifications, and even push follow-up commits if necessary.

**It's basically a way to allow your teammates to review the code of your branch on the web interface of your repo**. It allows them to make comments about the code that is about to be merged to the master.

You can learn how to create and mantain a pull request [here](https://help.github.com/articles/using-pull-requests/) (the same link I mentioned above). Each other service follows the same pattern, so there's no mystery involved.

Even after opening a pull request, you're still able to push new commits to your branch. You can use that to get early reviews of your code and keep working on some other part while people review what you've already uploaded.

And hey: **remember to review your own pull request** before asking for reviews of your teammates. You'll spot a lot of small things you didn't notice (style issues, typos, etc) and will allow your colleagues to focus on what really matters.

But again, your code isn't on the master branch yet, right? Hold on, we're almost there!

### Refactoring/ Fixing Stuff

If your teammates asks for reasonable changes in your code, you'll have to do it (for the sake of code quality). Let's take a look on a scenario that happens very often: adding new changes to a past commit.

So, this is your file_a.example (yeah, the typo is on purpose):
    
    
    [...]
    
    
    some_cool_function
    
    
    some_coler_function
    
    
    [...]

And this is your commit history (older commits on top):
    
    
    f7f3f6d create file_a class and methods  
    310154e improve SomeOtherClass code  
    a5f4a0d update changelog

Someone points out that your **_some_coler_function _**has a typo on its name and now you have to fix it.

You update the file and commit the fix. And now here's your new commit history:
    
    
    f7f3f6d create file_a class and methods  
    310154e improve SomeOtherClass code  
    a5f4a0d update changelog  
    **a412dbb fix typo on file_a**

But hey, you're fixing something that you just added on this pull-request (on the first commit, to be exact)… It would be nicer to have both the creation and the fix of file_a on only one commit, right?

Git is such a wonderful tool and has this killer command that **allows us to change previously stablished commits**: git interactive rebase.

So we need to merge the first commit (**f7f3f6d** with the last one **a412dbb**). And that's when the interactive rebase tools comes in hand.
    
    
    $ (some_branch) git rebase -i origin/master

The **_origin/master_** param is our start point. This basically is telling git: "hey, we want to change the history since the last commit origin/master", otherwise known as… your branch!

You can also use **_HEAD~4_** as a param, which works like: "hey, we want to change the history since 4 commits behind the current one". The [official docs](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History) has more details on this.

After executing the command, this will be your screen:
    
    
    pick f7f3f6d create file_a class and methods  
    pick 310154e improve SomeOtherClass code  
    pick a5f4a0d update changelog  
    pick a412dbb fix typo on file_a
    
    
    # Rebase 710f0f8..a412dbb onto 710f0f8  
    #  
    # Commands:  
    #  p, pick = use commit  
    #  r, reword = use commit, but edit the commit message  
    #  e, edit = use commit, but stop for amending  
    #  s, squash = use commit, but meld into previous commit  
    #  f, fixup = like "squash", but discard this commit's log message  
    #  x, exec = run command (the rest of the line) using shell  
    #  
    # These lines can be re-ordered; they are executed from top to bottom.  
    #  
    # If you remove a line here THAT COMMIT WILL BE LOST.  
    #  
    # However, if you remove everything, the rebase will be aborted.  
    #  
    # Note that empty commits are commented out

Now we just need to follow the instructions written there! We want to combine commits f7f3f6d and a412dbb. So we must reorder the lines to be like this:
    
    
    pick f7f3f6d create file_a class and methods  
    **pick a412dbb fix typo on file_a**  
    pick 310154e improve SomeOtherClass code  
    pick a5f4a0d update changelog

And we change the **pick** label on the a412dbb commit to a **fixup** (or **f**), to tell git: "hey, we want to combine this guy with the one above it":
    
    
    pick f7f3f6d create file_a class and methods  
    **fixup** a412dbb fix typo on file_a  
    pick 310154e improve SomeOtherClass code  
    pick a5f4a0d update changelog

Save your file and bang! Here's your new commit history:
    
    
    **b7c3f33** create file_a class and methods  
    **1b24ae9** improve SomeOtherClass code  
    **d5ffad3** updates changelog

(yeah, the hash of all commits changed due the rewrite of the history).

If you already pushed your branch to remote, remember to use -f next time you push, since you've rewritten the your commit history:
    
    
    $ (some_branch) git push -f origin some_branch

> Be warned: pushing with -f is a very dangerous thing. Proceed with caution and always be sure that you're pushing to the right branch.

And there you go!

Stuff like splitting a commit into different ones and some other crazy ways to change your history are described in the [official git documentation](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History).

> **Remember: NEVER rewrite the commit history of public branches (like master). This will truly mess your teammates work.**

Finally, it's time to…

### Integrating your code

Teams usually establish a minimum amount of reviews to get a pull request merged. Once you get the enough numbers of eyes on your code, designate someone to merge it! You can also merge yourself, but that's not the usual on most teams.

And that's it! Your code is now on your master branch, ready to ship to production.

Now you know how to use the workflow followed by thousands of teams of software development around the world!

With this workflow, you **prevent people from stepping on each others toes** while working and **ensure that the code that goes to production has been _approved_ by a minimum number of developers**.

If you are in a team that doesn't follow this pattern, propose this change to them. The benefits are crystal clear and the effort to achieve that is close to zero.

Happy gitting!
