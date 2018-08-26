# Debugging with Git

_Captured: 2018-06-22 at 21:50 from [dzone.com](https://dzone.com/articles/debugging-with-git?edition=383247&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-22)_

When you are working on a huge project, you may discover bugs in the code that prevent you from proceeding any further in your development.

To fix them, you can start by looking through your commit history by hand, but this would end up being a very tedious process. Thankfully, Git has multiple tools that can help you hunt for a bug or the culprit when things go wrong.

## Git Blame

`$ git blame <file_path/file_name>`  
The [command](https://kolosek.com/git-commands-tutorial-part2/) helps you find the commit that created the specific line of code that causes a bug in a specific file of a project. It also determines the author of the commit, making is easier to ask for more information about the code.

You can -L option to limit the line output range.
    
    
    $ git blame -L 11,21 new_file ^95d69a196b5c7 (Jhon Smith 2018-05-18 13:04:22 +0200 11) def new ^95d69a196b5c7 (Jhon Smith 2018-05-18 13:04:22 +0200 12) @article = Article.new ^95d69a196b5c7 (Jhon Smith 2018-05-18 13:04:22 +0200 13) end 3171aa2dbbce7 (David Smith 2018-05-16 18:21:30 +0200 14) def edit 3171aa2dbbce7 (David Smith 2018-05-16 18:21:30 +0200 15) @article = Article.find(params[:id]) 3171aa2dbbce7 (David Smith 2018-05-16 18:21:30 +0200 16) end ^95d69a196b5c7 (Jhon Smith 2018-05-18 13:04:22 +0200 17) def create 3171aa2dbbce7 (David Smith 2018-05-16 18:21:30 +0200 18) @article = Article.new(article_params) ^95d69a196b5c7 (Jhon Smith 2018-05-18 13:04:22 +0200 19) if @article.save ^95d69a196b5c7 (Jhon Smith 2018-05-18 13:04:22 +0200 20) redirect_to @article ^95d69a196b5c7 (Jhon Smith 2018-05-18 13:04:22 +0200 21) else

By following the partial SHA-1 of a commit you can easily see who, when and how was a specific line of code modified. Note that the `^` prefix shows lines that were created in the initial commit and have remained unchanged ever since.

> Use to figure out where snippets of code originally came from if they were copied from elsewhere. It tells you the original author and commits regardless of the refactoring done afterward.
> 
> `$ git blame -L -C 11,21 <file_path/file_name>`

`git blame` is helpful when you can assume the cause of the problem. What if you had no idea how to get back to a working state? This is where `git bisect` comes into play.

## Git Bisect

A is a [debugging tool](https://kolosek.com/rails-debugging/) used to find out which specific commit introduced a bug or a problem in the project by doing an [automatic binary search](https://labs.consol.de/development/git/2018/01/12/automated-debugging-with-git.html). You don't know what file in the project contains the bug.

If you don't know what is breaking, and there have been a bunch of commits since the last state where you know the code worked, you'll likely turn to `git bisect` for help.

![](https://kolosek.com/content/images/2018/05/git-bisect.png)

What `git bisect` does is, it divides the **[git commit tree](https://kolosek.com/git-branches/)** into "good", bug-free commits and "bad" commits by testing them with **binary search**. Based on the result of the tests, Git navigates through recent commits identifying them, until it finds the culprit. This is known as a binary search algorithm.

> If you have multiple bugs, you need to perform a binary search for each of the bugs.

### How Does This Work?

  1. First, let's start with the binary search mode to find a bug: `$ git bisect start`.
  2. Next, you need to look for a commit where everything was still working. To do so, let's examine the **commit history** to find what you need: `$ git log --oneline`.

\--oneline option shows only the names of git commits.

  1. **Tag** the oldest "good" commit SHA-1: `$ git bisect good 95d69a1`.
  2. After you have assigned the "good" tag, you need to find a **"bad" commit** to divide the commit tree where Git can apply the binary search algorithm. Since you know that the latest commit has the error, you will assign it as the "bad" commit: `$ git bisect bad f11c599`.
  3. Once you have assigned initial and final pointers for your search, Git walks you through the [commit history](https://kolosek.com/git-branches/) and tags "good" and "bad" commits.
  4. This process continues until you successfully find out the first "bad" commit, the cause of your problem. Now you can exit the git binary search mode by executing: `$ git bisect reset`.

## Git Grep

`$ git grep <keyword>`  
The [command](https://kolosek.com/git-commands-tutorial-part2/) allows you to efficiently and quickly search through your project for a string or regular expression in any of the files in your source code. It avoids searching through `.gitignore` files.

**Additional options:**

  * `-n` or `\--line-number`: Prints out the line numbers where Git has found matches.
  * `-i` or `\--ignore-case`: Ignores case differences between the searched keyword and the file.
  * `-c` or `\--count`: Shows the number of matches found in the file for the inputted keyword.
  * `-p` or `\--show-function`: Displays the context of the searched keyword.
  * `\--and`: Ensures multiple matches in the same line of text.

## Summary

`git blame` is a great tool if you know where the buggy code is located. On the other hand, if your repository is considerably large, with a huge commit history that makes it difficult to find the error, `git bisect` is the way to go. Or you could easily search through your project for a string or regular expression with `git grep`.

Three debugging tools with three different ways to fix your problems in their own unique ways. Which one did you encounter so far? Share your experience!
