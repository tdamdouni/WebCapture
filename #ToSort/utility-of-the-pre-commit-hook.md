# Utility of the Pre-Commit Hook

_Captured: 2018-03-09 at 17:13 from [dzone.com](https://dzone.com/articles/utility-of-the-pre-commit-hook?edition=366226&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-03-09)_

[Learn more](https://dzone.com/go?i=250324&u=http%3A%2F%2Fblog.scalyr.com%2F2017%2F08%2Fcareerbuilder-resolves-customer-issues-5x-faster-scalyr%2F) about how CareerBuilder was able to resolve customer issues 5x faster by using Scalyr, the fastest log management tool on the market.

Cook your application code and use the capabilities of "pre-commit linters" to do a baseline check before you commit your code and push it to the repository. So, I assume my readers would have the following questions:

  * What is a "hook"?
  * What is "Pre-commit"?
  * What is the problem statement that pre-commit resolves?
  * What are "Pre-commit hooks"?
  * What is a "linter"?

## What Is a "Hook"?

In programming, a hook is an application, a set of customized program code that helps to perform another functionality. This simplifies interoperability between two applications or platforms. In technical terms, it is a callback for an event or set of events triggered by certain actions, which might be clicking a button or running certain specific scripts.

## What Is "Pre-Commit"?

Pre-commit is a framework for managing and maintaining multi-language pre-commit hooks.

## What Is the Problem Statement That Pre-Commit Resolves?

Git hook scripts are very useful for identifying simple issues before submission to code review. We run these hooks on every commit to automatically point out issues in the code, such as missing semicolons, trailing whitespace, and debug statements. Pointing out these issues before code review allows a code reviewer to focus more on the architecture of the application rather than petty issues.

As we keep on creating more libraries and projects, it becomes complicated to share pre-commit hooks across projects. It is recommended that we always use the best industry standard linters.

## What Are "Pre-Commit Hooks"?

The pre-commit platform solves the hook issues. It is a multi-language package manager for pre-commit hooks. We specify a list of hooks we want and pre-commit manages the installation and execution of any hook written in any language before every commit. Pre-commit is specifically designed to not require root access. Pre-commit automatically handles downloading and building from packages without root.

## What Is a "Linter"?

A "linter" or "lint" is a tool or certain program/programs that analyze the source code to flag programming errors, bugs, style-based errors, and suspicious constructs. The term originated from a UNIX utility that examined C language source code.

## Installation

Installing pre-commit can be done in two ways:

**Using pip:**

**Using Home-Brew for MacOS:**

**For system level installation:**

**In a Python-based project:**

In a Python-based project, you can add the dependency to the `requirements.txt`

## Adding Pre-Commit Plugins to Your Project

Once you have pre-commit installed, adding pre-commit plugins to your project is done with the `.pre-commit-config.yaml` configuration file.

Add a file called `.pre-commit-config.yaml` to the root of your project. The pre-commit config file describes what repositories and hooks are installed.

A typical .pre-commit-config.yaml would look something like this:
    
    
    - repo: git://github.com/pre-commit/mirrors-yapf
    
    
      - repo: https://github.com/pre-commit/pre-commit-hooks

In the above example, I have included plugins for the Python linter, which is yapf; "**trailing-whitespace**" to remove trailing whitespace and "**check-merge-conflict**" to check for merge conflicts in the file.

You would also have to add a "**.style.yapf**" file, which would have the style standards defined within. The ".style.yapf" file would look something like this:

## Updating Hooks Automatically

You can update your hooks to the latest version automatically by running `pre-commit autoupdate`. This will bring the hooks to the latest sha on the master branch.

## Usage

You have to run `pre-commit install` to install pre-commit into your git hooks. pre-commit will now run on every commit. Every time you clone a project using pre-commit running `pre-commit install --install-hooks` should always be the first thing you do. Check the screenshot for reference.

![Screen Shot 2018-02-19 at 4.24.22 PM](https://soumyajit2016.files.wordpress.com/2018/02/screen-shot-2018-02-19-at-4-24-22-pm.png?w=1352)

If you want to manually run all pre-commit hooks on a repository, run `pre-commit run --all-files`. To run individual hooks, use `pre-commit run `.

The first time pre-commit runs on a file, it will automatically download, install, and run the hook. Note that running a hook for the first time may be slow. For example: if the machine does not have Node installed, pre-commit will download and build a copy of Node.

To get started with the pre-commit checks, just commit your code to see whether your codebase follows industry standards or not. Check the screenshot for reference.

![Screen Shot 2018-02-19 at 4.33.35 PM.png](https://soumyajit2016.files.wordpress.com/2018/02/screen-shot-2018-02-19-at-4-33-35-pm.png)

## Updating Hooks Automatically

You can update your hooks to the latest version automatically by running `pre-commit autoupdate`. This will bring the hooks to the latest sha on the master branch. Check the screenshot for reference.

![Screen Shot 2018-02-19 at 4.36.48 PM.png](https://soumyajit2016.files.wordpress.com/2018/02/screen-shot-2018-02-19-at-4-36-48-pm.png)

**[Find out more](https://dzone.com/go?i=250325&u=http%3A%2F%2Fblog.scalyr.com%2F2014%2F05%2Fsearching-20-gbsec-systems-engineering-before-algorithms%2F) about how Scalyr built a proprietary database that does not use text indexing for their log management tool.**

Opinions expressed by DZone contributors are their own.
