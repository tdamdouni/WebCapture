# Using Editorial with Taskpaper files

_Captured: 2015-11-22 at 15:48 from [dfay.fastmail.fm](http://dfay.fastmail.fm/et/)_

For the last few years, I have been using [Taskpaper](http://hogbaysoftware.com/products/taskpaper) to manage my to-do lists. While there is an iPad client, I have never been that comfortable with the many ways in which its UI departs from the Mac client's roots as a text editor. So I decided to add a few workflows to Editorial, which together cover probably 98% of what I do in Taskpaper.

Displays a drop-down list with all the projects in the document, & navigates to the chosen project, selecting the project name in the document.

[Select Tag…](http://editorial-app.appspot.com/workflow/4717248480542720/rSY1zx34brg)

Displays a drop-down list with all the tags in the document, & copies the chosen tag to the clipboard, ready for pasting into Editorial's search field.

[Mark Due](http://editorial-app.appspot.com/workflow/6669706253565952/t70KadTUWUQ)

Insert a @due(yyyy-mm-dd) tag at the current cursor location. Opens an input box with the current year and month auto-filled and the cursor ready to type the day.

Insert a @done(yyyy-mm-dd) tag at the current cursor location, pre-filled with the current date & time.

I have Editorial's bookmark bar set up with these commands on the left, and frequently used Taskpaper files on the right:

Open the current editorial document in Taskpaper. It passes just the current file name via [Taskpaper's URL scheme](https://groups.google.com/forum/#!topic/taskpaper/7Aui8CygeMw), so the current document must be in the same directory that TP for iOS is configured to use.

Sends the currently selected text to Fantastical 2, converting TaskPaper @due(YYYY-MM-DD) tags to plain text for Fantastical to parse as a Reminder. I have also written a [script for Pythonista to do the same when called from Drafts](https://gist.github.com/derickfay/10012120)

[Sort by @due](http://www.editorial-workflows.com/workflow/6662140131803136/L2psBi_7E9k)

Sort selected text by the dates in @due(YYYY-MM-DD) tags. (I also have an equivalent [python script](https://gist.github.com/derickfay/8891099) which can be set up as an OS X Service via Automator.)Alessandro

I have Editorial's bookmark bar set up with some of these commands on the left, and frequently used Taskpaper files on the right:

![Workspace](http://dfay.fastmail.fm/et/workspace.png)
