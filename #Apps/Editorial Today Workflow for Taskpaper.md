# Editorial Today Workflow for Taskpaper

_Captured: 2015-09-26 at 21:22 from [www.movingelectrons.net](http://www.movingelectrons.net/blog/2015/06/20/Editorial-Today-Workflow.html)_

[Editorial 1.2](https://geo.itunes.apple.com/us/app/editorial/id673907758?mt=8&uo=6&at=11lqkH) is out and it brought a plethora of improvements to a text editor that was already - in my opinion - the best one for iOS. Out of the box, is beautifully designed and stable enough to be used as your primary text editor. If you dig deeper, you will find advanced features like Workflows (using built-in actions and/or Python scripts), templates, GUI design, Taskpaper support, [Dropbox](https://db.tt/LdFyqgz2) syncing and complete markdown support, just to name a few features. It's so powerful that calling it a text editor is truly an understatement.

In addition to being my text editor of choice, I use it as my Todo list management app. Editorial has supported the **Taskpaper** format since the last iteration. However, it was up until this version that the `Fold Lines Containing...` action was introduced. I had the privilege of using the beta version of this release for a while and put together this workflow I think other people may find useful.

## Due Today Workflow

If you are not familiar with Taskpaper, go [here](http://imissmymac.com/wp-content/uploads/2013/02/TaskPaper-Users-Guide.pdf) and read about it. It's a really simple and effective way of managing Todo lists and projects.

This workflow goes over your currently open Taskpaper file and folds all lines that **don't** contain the `@today` tag or that are due either today or before today. That last part is achieved by parsing tags in the form `@due(YYYY-MM-DD)`. It's a fairly simple workflow that can be downloaded from [here](http://www.editorial-workflows.com/workflow/5774648289525760/10TL_XlMVBY).

Thus, given a Taskpaper file like this one:

![Editorial Today Workflow - Before](http://www.movingelectrons.net/images/Editorial-Today-Workflow-Before.png)

> _We would get the following assuming today is June 20, 2015:_

![Editorial Today Workflow - After](http://www.movingelectrons.net/images/Editorial-Today-Workflow-After.png)

> _Editorial Today Workflow - After_

The key part is the Python script embedded in the workflow. It can be easily revised to also list tasks that are due the following day (I have included comments on how to do so inside the script). If you prefer having a separate workflow to check on those tasks (as I do), [here](http://www.editorial-workflows.com/workflow/5854361607471104/OtCa4qrtnCI) is the one I put together.

**Update**

I have revised the Python script and actions to also list _Project Names_ in the resulting list of tasks for both the [Today](http://www.editorial-workflows.com/workflow/5774648289525760/10TL_XlMVBY) Workflow and the [Tomorrow](http://www.editorial-workflows.com/workflow/5854361607471104/OtCa4qrtnCI) Workflow.
