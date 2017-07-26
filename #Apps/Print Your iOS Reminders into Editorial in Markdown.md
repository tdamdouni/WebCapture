# Print Your iOS Reminders into Editorial in Markdown

_Captured: 2015-09-28 at 23:46 from [myword.jeffreykishner.com](http://myword.jeffreykishner.com/users/kishner/essays/027.html)_

[Home](http://jeffreykishner.com)

Earlier today I complained about [the difficulty in exporting iOS reminders into text format](http://myword.jeffreykishner.com/users/kishner/essays/026.html) and @pslobo wrote the following:

I don't know python but after reviewing the [Editorial](http://omz-software.com/editorial/) modules for [reminders](http://omz-software.com/editorial/docs/ios/reminders.html#module-reminders) and [editor](http://omz-software.com/editorial/docs/ios/editor.html#module-editor) and looking at some other python scripts, I hacked together a workflow to import the list items from lists called 'tv' and 'movies' into a text file in Markdown format.

To make it work, [import this workflow](http://www.editorial-workflows.com/workflow/5319972381261824/PMQPGH2j7iE). Then just create a new file in Editorial and tap on the workflow.

You can edit this to include your own list names. For example, you can change 'tv' to 'bills' after `if calendar.title ==`.
