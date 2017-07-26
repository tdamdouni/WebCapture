# Editorial workflow installer

_Captured: 2015-11-29 at 12:32 from [www.robertvojta.com](http://www.robertvojta.com/2015/05/16/editorial-workflow-installer/)_

I wrote several Editorial workflows for [Jekyll & GitHub Pages blogging](http://www.robertvojta.pro/2015/05/12/editorial-workflows-for-jekyll-blogging/) few days ago. Then I removed them from my iPad to test fresh installation and found two problems:

  * dependencies,
  * lost sharing state.

Workflow can run another workflow (= subworkflow). User can include subworkflow in the main workflow (copy) or it can be referenced by name. Running main workflow without installed subworkflow referenced by name leads to an error. Editorial itself doesn't help here, because it installs main workflow without dependencies, without warning, … It looks like that everything's allright and it isn't. Not a big issue for experienced Editorial users, but even I do not want to remember all dependencies. Would like to have it automated.

Second problem is sharing state. User can create workflow and share it at [editorial-workflows.com](http://www.editorial-workflows.com/). Editorial offers _Share_ or _Update_ if user tries to share the same workflow again. But sharing state is lost whenever user decides to delete workflow and install it again. Like me when I was testing it.

I learned how workflows are stored locally, but wasn't able to figure out how to restore sharing state. Asked [Ole](http://omz-forums.appspot.com/editorial/post/5800582476464128) and he quickly provided [Restore Shared Workflow…](http://www.editorial-workflows.com/workflow/5800966574047232/D0MZnxumf5U) workflow. Ole's workflow is nice, but I wanted to have it working other way - do not list shared workflows and install them, but list all available workflows and restore sharing state if possible.

To be precise - sharing state isn't lost. Sharing state is being kept in _SharedWorkflows.sqlite_ database. Problem is with installation, because installation of workflow **always** generates new _UUID_, which doesn't match previously used _UUID_.

What now? Editorial, iPad, external keyboard and here's the solution - [RV: Workflow Installer](http://www.editorial-workflows.com/workflow/5208290749317120/vPQA17J5z5c).

You can browse recent workflows remotely fetched from [editorial-workflows.com](http://www.editorial-workflows.com/).

![](http://www.robertvojta.com/public/images/workflow-installer-recent-workflows.jpg)

> _You can check installation status and dependencies._

![](http://www.robertvojta.com/public/images/workflow-installer-workflow-detail.jpg)

> _Installed workflows are skipped._

![](http://www.robertvojta.com/public/images/workflow-installer-workflow-detail-installed.jpg)

> _You can search for workflows available at editorial-workflows.com._

![](http://www.robertvojta.com/public/images/workflow-installer-search.jpg)

You can check what's going on during installation of workflow and dependencies.

![](http://www.robertvojta.com/public/images/workflow-installer-installation-log.jpg)

Problems solved. Workflows can be installed with dependencies and sharing state is preserved.

Be aware of one thing. Sharing state can be restored only on the device from which you did share your workflow for the first time. That's because of locally stored _SharedWorkflows.sqlite_ database.

Enjoy!
