# Oh, Git Configurations! Let's Simplify It

_Captured: 2018-03-28 at 20:31 from [dzone.com](https://dzone.com/articles/oh-git-configurations-lets-simplify?edition=369206&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-28)_

## Oh, Git Is Complex!

Git is a complex system. To see the proof, check out:

To mitigate that, **we are going to get inside the head of Linus Torvalds! **(Just a little bit - maybe into a single neuron). In this part, we will focus on configurations. I always thought that to understand a system, I needed to understand its configurations (or even better, its installation).

When I get to a new company, the first thing I try to figure out is:

  1. How do I install this?
  2. How do I configure this?

## How Does Linus Torvalds Think?

> "Everything is a file."

**Yes, this is how Linus thinks: everything is a file.**

As Linus loves this idea that everything is a file, you can just view git configurations as a file.

**So, if we manage to learn which files Linus uses in git, we might be able to penetrate oh-my-complex-git!**

## 3 Fallback Layers of Config

  1. System - Your OS git config - `git config --system`
  2. Global - Your User git config - `git config --global`
  3. Local - Your Repository git config - `git config --local`

Git first reads the git config from .git/config -> [fallback to] ~/.gitfconfig -> [fallback to] /etc/gitconfig.

## Email per Repo

If you have different email addresses for different repositories, this goes into `.gitconfig == git config --local`

### **Get the Global Config With `git config --list --global`**

Would that be the same as `cat ~/.gitconfig`? What do you think?

Yes and no! It's a different notation, but generally the same!

### **Get the Merged Config With `git config --list`**

The merged config is the combination of all configs with the hierarchy. Let's see it on my machine:
    
    
    alias.au=!git add -u . && git status
    
    
    alias.aa=!git add . && git add -u . && git status
    
    
    alias.ll=log --stat --abbrev-commit
    
    
    alias.alias=!git config --list | grep 'alias\.' | sed 's/alias\.\([^=]*\)=\(.*\)/\1\     => \2/' | sort

That was it - **all** the git config on my machine! I hope I didn't put any passwords in there! If I did please, let me know - code review is important, guys!

### Git Config --local/global/system user.name - Get a Single Config

Ask layer by layer for a config:

Aha! So it's coming from the global (user) config!

Note that in the file, it's with `[user]` and the name, and the git config returns the combined name `user.name`.

If you need a hierarchy larger than three, then in the file, it will look like this:

So, this one should be `branch.gke.remote`. Let's verify this:

### Set a New Config With `git config mysection.mykey myvalue`

So, we were able to set it. Let's look at the file:

## Summary

You now know exactly where your git config files are. This is very helpful and much more explainable than using the git commands. I'm not sure I was able to simplify it, but it makes at least some sense at the end of the day for us programmers!

## Resources
