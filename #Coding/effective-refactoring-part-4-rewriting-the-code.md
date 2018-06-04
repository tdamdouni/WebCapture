# Effective Refactoring, Part 4: Rewriting the Code

_Captured: 2018-05-10 at 15:59 from [dzone.com](https://dzone.com/articles/effective-refactoring-part-4-rewriting-the-code?edition=376277&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202018-05-10)_

_This is the final part of a 4 part series on effective refactoring._

  * **_Part 4: Rewriting the Code_**

You put together a plan, selected a task to work on, wrote the tests, and now you're ready to clean up some code. It's about time! You'll be tempted to open up a file and start changing variable names or clean up the contents of a folder that has been driving you nuts. Before you start digging into the codebase, however, there are a few concepts you should familiarize yourself with to ensure the refactoring goes smoothly.

In the final part of this series, I'm going to cover some of the common pitfalls that you may encounter over the course of a rewrite. I'll also present techniques for expediting some of the more tedious tasks. I won't be covering the specific mechanics, definitions, or processes associated with refactoring; if you're interested in learning more about that topic, check out these great resources:

## Identify Opportunities to Automate

There's a very good chance that you'll have some project tasks that will be tedious. One of the biggest culprits I encountered was moving files. For example, the application I refactored had the Redux actions, reducers, and selectors in their own separate folders. One of my project tasks was to group the Redux files by module (e.g. `appActions.js`, `appReducer.js` , and `appSelectors.js` ). I could have run a `git mv` command to move `/actions/app.js` to `/redux/app/appActions.js`, then do the same for `/reducers/app.js` and `/selectors/app.js`, but that only takes care of the app module. There were 11 modules in this project, so I'd have to type out 33 `git mv` commands just for the Redux elements. You may have to run `git mv` 150 more times to get the React containers and components in the right folder location!

You'll find that this situation can quickly become untenable. Rather than type out all those commands, I wrote a script to do it for me using JavaScript and Node.js:

You can either go into the files and update the relative paths after running the script, or you can write a script to update the paths using string manipulation. Automation can get pretty fancy, but know when to draw the line: it wouldn't make sense to spend 20 hours writing a script to save one hour of manual work. Most codebases are unique and have specific structures, which means you probably won't be able to reuse these scripts.

## Commit Often

Making significant changes to a file or set of files can break your app and cause tests to fail. This is to be expected. If you've made a bunch of changes and everything works, commit the changes. If you've only made a few minor updates and everything still works, commit the changes. Making commits is cheap. Here are some metrics for the app I refactored:

  * **1,747** commits.

  * **378** closed pull requests.

  * **42,017** total lines of text across **169** Jest snapshot files.

  * **13,555** total lines of text across **181** test files.

  * **24,261** total lines of text across **2** fixture files (`responses.js` and `state.js`).

  * **16,685** total lines of text across **198** JavaScript files.

  * **3,823** total lines of text across **111** Sass files.

That's **76,080** lines of code across **659** files, and the repository size is only **10MB**. Make all the commits you want -- git can handle it. You can always [squash them later](https://davidwalsh.name/squash-commits-git) if you want to clean up your history. I urge you to commit as frequently as possible; when refactoring a large app you'll very quickly realize how difficult it can be to track down small, breaking issues.

Imagine making changes to 10 files, verifying your app still works, and feeling generally happy with the code. You decide not to commit your changes, and after another half-hour of refactoring you break something. You can either spend three hours tracking down the bug or just discard all of your changes and start from scratch. Since you didn't commit the changes to those 10 files, you lost perfectly good code!

I'm not saying it's impossible to determine if you need to reset those files, but why waste time and energy when you **know** you can jump back to the last commit and go from there. Try to limit the changes on commits to only a few files at a time, and commit often so you have reliable "save points" to fall back on.

## Avoid Temptation

Avoid the urge to clean up code that's out of the scope of the task at hand. This is one of the most difficult aspects of refactoring. Let's say you were working on a task called Standardize Redux Selector Names that involved updating the names of the selectors to ensure all of them were prepended with the word `select`. As a relatively simple task with low risk and well-defined scope, it should go smoothly; you just need to update the selector names (along with any files that reference these selectors) to accommodate the change (and don't forget about the tests!).

Let's say you come across a selector that's using `[Object.assign()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)`, and one of your future tasks is to update the code to utilize some of the newer ESNext features like the [spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax). You may be tempted to update that code, but don't!

It is imperative that you don't deviate from the current task. Even the most trivial change can set you on the wrong path. Even though the concept of a [slippery slope](https://en.wikipedia.org/wiki/Slippery_slope) is a logical fallacy, a less hyperbolic situation will often occur. You start changing `Object.assign()` statements and before you know it, four hours have elapsed and you've only updated two selector names!

As I progressed through my refactoring tasks, I became much less susceptible to this type of behavior. I added a `// REFACTOR: Fix this later` comment in the code and checked my project to ensure I had a task to cover the change, then I moved on.

## Be Methodical With Pull Requests

Pull requests are an excellent tool in refactoring projects for a number of reasons, they:

  * Provide a record of changes that correspond with a project task.

  * Define a rollback point if new bugs are introduced.

  * Enable peers to review your code and look for potential bugs.

  * Offer the opportunity to explain why you made certain changes.

If you spend a large chunk of time cleaning up a section of the codebase, it can be difficult to step back and evaluate the quality of your changes. Pull requests give your colleagues the opportunity to review your changes and determine whether they add value and improve the existing code.

When you're submitting pull requests, be as descriptive as possible in the summary. Put together a template and include it in your repository. If you're using GitHub, this [template will be pulled in automatically](https://help.github.com/articles/creating-a-pull-request-template-for-your-repository/) for new PRs. Try to include a title, high-level description, a section for important notes, and a bulleted list of changes. The list of changes doesn't have to be extensive and wordy, but it should cover important changes that reviewers should focus on.

One metric that you need to be cognizant of is the quantity of changes associated with a pull request. Try to limit the amount of changes to +/-500 lines of code. Adding Jest snapshot files can easily add thousands of lines to a pull request, so be sure to include a note about this in the summary. If you can't minimize the quantity of changes, strive to reduce the complexity. If you're just reordering import statements, exceeding 2,000 lines of code is acceptable as long as the changes are not overly complex. Try to isolate that change in a single PR and ensure that you describe the nature of the change in the summary. It helps to include a bold note at the beginning of the summary with something like "No logic changes were made" so the reviewer has proper context.

_Try not to be this guy (me, that guy is me)_

By writing descriptive summaries in your pull requests and ensuring that the scope of changes corresponds to the project tasks, you'll make life much easier for reviewers. I'll admit that I wasn't always able to follow my own advice (I still owe some of my coworkers a lunch or 10), but I made sure I responded to inquiries and addressed concerns quickly.

## Wrap Up

That's it for the refactoring series! I hope the collective nuggets of wisdom I presented will contribute to the success of your refactoring project. Refactoring isn't as simple as rearranging files or renaming functions in your codebase, but if you [put together a solid plan](https://dzone.com/articles/effective-refactoring-part-2-formulating-a-plan), adhere to that plan, and update regularly then you'll be off to a good start. [Having a robust testing infrastructure](https://dzone.com/articles/effective-refactoring-part-3-the-imperative-role-o) will give you the confidence to make changes without breaking any functionality.

In terms of execution, automate as much as you can, commit often, and avoid temptation. Pull requests are an excellent documentation and review tool, so ensure they're detailed and limited in scope. In case you were wondering, here are the results of my refactoring project:

  * **40** tasks completed.

  * **12** tasks pending.

  * **1** Jira bug logged (directly related to the refactor).

  * **1,473** tests written across **181** test suites (**737** of which were snapshot tests).

  * **108,450** lines added and **44,241** lines removed.

  * **38** pull requests.

  * **99.84%** statement coverage.

  * **95.07%** branch coverage.

The lines added and removed don't really mean much, as most of them represented file moves, snapshots, and the test fixture files. The high test coverage should be taken with a grain of salt as well: I'm ignoring some of the chart components because it's difficult to test the HTML Canvas element. I added several features and fixed miscellaneous bugs over the course of the refactoring and, having high test coverage, caught several potential issues before they could be included in the release. Overall, I'd say the rewrite was **definitely** worth the effort.
