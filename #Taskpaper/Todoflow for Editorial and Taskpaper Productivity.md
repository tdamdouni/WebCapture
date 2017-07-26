# Todoflow for Editorial and Taskpaper Productivity

_Captured: 2015-10-18 at 21:17 from [www.macdrifter.com](http://www.macdrifter.com/2015/06/todoflow-for-editorial-and-taskpaper-productivity.html)_

I mentioned [Todoflow](https://github.com/bevesce/TodoFlow), a python module for working with Taskpaper files, back when [I first started](http://www.macdrifter.com/2014/02/the-taskpaper-rd-notebook.html) using the system full time. It has a lot of the core query support of TaskPaper right from Python.

Now, the [same module is available through an Editorial workflow](http://www.editorial-workflows.com/workflow/5904847807184896/srCpxXVBZEY). The workflow automatically installs the module if needed and supports advanced queries and result folding. It adds some minor enhancements to the TaskPaper query syntax (like a "today" term) but does not support parenthetical (nested) expressions.[1](http://www.macdrifter.com/2015/06/todoflow-for-editorial-and-taskpaper-productivity.html)

![Todoflow in Editorial](http://www.macdrifter.com/uploads/2015/06/_23_06-24-15%2C_6_50_03_AM.png)

> _Todoflow in Editorial_

Enter a query like this:
    
    
    @start <= {today} or @start and not @done
    

To see all tasks that start before tomorrow that have not been completed. The workflow includes a couple of predefined queries but add your own to the list for quick access.

While the query expression support in Todoflow is not as powerful as [Taskmator](https://itunes.apple.com/us/app/taskmator-taskpaper-compatible/id806250172?mt=8&uo=4&at=11I5Ug&ct=blog), it's pretty good. Another downside is that TextExpander is not supported in the text entry box of Editorial so a lot of my old snippets will not function in this workflow. Check out [the other Editorial workflows](http://www.editorial-workflows.com/workflows/search?q=todoflow) with Todoflow support.
