# Git Commands Tutorial - Part 1

_Captured: 2018-04-05 at 20:20 from [dzone.com](https://dzone.com/articles/git-commands-tutorial-part-1?edition=371217&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-04-05)_

[Learn how](https://dzone.com/go?i=282429&u=https%3A%2F%2Fcraftersoftware.com%2Fresources%2Fwhite-papers%2Ffive-reasons-you-need-a-git-based-cms%3Fdzone) Crafter's Git-based content management system is reinventing modern digital experiences.

There are many different ways to use Git. The most common are the original **command line** tools and **GUI** ( **G**raphical **U**ser **I**nterfaces). Here, we will cover the most important commands you should know about when you are working with Git.

> _The command line is the only place you can run all Git commands. If you know how to run the command-line version you can probably also figure out how to run the GUI version. Also, while your choice of graphical client is a matter of personal taste, all users will have the command-line tools installed and available._ You can read more on [git's official online book](https://git-scm.com/).

Before we start, be sure to _know_ how to use the Terminal in Mac or Command Prompt or Powershell in Windows and have [git installed](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) on your system.

## Introduction

First, you might ask yourself what is **Git** actually and what can you do with it? Git is a fast, scalable, distributed **revision control system** with a rich command set that provides both high-level operations and full access to internals.

At Kolosek (where I work), we use **Git** for every application we create, including [Ruby on Rails projects](https://kolosek.com/rails-join-table/), to make it easier to work as a team and achieve our goal.

You can learn a lot about individual Git commands by the running `$git help` command in the terminal. This should appear:

![](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/705193677f876525ff33c6a7eaca4901/git-help-command.png)

> _Everything can be added to your git repositories, even your Controller tests!_

## Git Options

We will cover the most commonly used command lines, starting from **Git options**. This will explain everything you need to know about Git on your local machine:

  * **`$git --version`**: Find out your current **Git suite version** using this command.
  * **`$git --help`**: Every [good programmer](https://kolosek.com/tag/good-programmers/) should know about this option, it will show you the **most used Git Commands**, and it can also print _all available_ commands with `\--all` or `-a`.
  * **`$git -C <path>`**: Instead of running Git from the **current working directory**, you can run it from the given `<path>` instead.

> `-C <path>` command affects other options that expect path names like `\--git-dir` and `\--work-tree` because their path names would be made relative to the working directory caused by the `-C` option.

  * **`$git -c <name>=<value>`**: You can very easily **override values** from your configuration files. The `<name>` has to be in the same format as listed by _git config_, while the `<value>` is your new parameter value.
  * **`$git --exec-path[=<path>]`**: This command helps you find the path where your core **Git programs are installed**. Another way to do this is by setting the `GIT_EXEC_PATH` environment variable.
  * **`$git --git-dir=<path>`**: Always use this option, whenever you need to set a path to the **repository** or set the `GIT_DIR` environment variable.

And, that's it! For now, at least.

This was only the first part of the tutorial! In the next one, we will cover all the other Git commands, be sure to stay tuned.

Crafter CMS is a modern Git-based platform for building innovative websites and content-rich digital experiences. [Download this white paper now](https://dzone.com/go?i=282430&u=https%3A%2F%2Fcraftersoftware.com%2Fresources%2Fwhite-papers%2Ffive-reasons-you-need-a-git-based-cms%3Fdzone).
