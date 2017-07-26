# Update to Editorial Workflow "List Your Reminders" to Allow for Input in URL Scheme

_Captured: 2015-09-28 at 23:49 from [myword.jeffreykishner.com](http://myword.jeffreykishner.com/users/kishner/essays/029.html)_

[Home](http://jeffreykishner.com)

This is a small update to [the script I wrote this morning](http://myword.jeffreykishner.com/users/kishner/essays/028.html) to print out a list of iOS reminders in Editorial, just for power users who like URL Schemes.

Use [this workflow instead](http://www.editorial-workflows.com/workflow/5846552014749696/lWmE07l_n0Y) \-- you can manually remove the "2" from "List Your Reminders 2."

If you prefer not to import a new workflow, just [go to the original](http://www.editorial-workflows.com/workflow/5012964226629632/_BycaAdg3Vg) and add a conditional block (if...end if ) and drag the first two workflow elements in between.

Then if you want to include a specific list name as an input parameter, you can create an URL action like this

`editorial://new/lists.md?command=List%20Your%20Reminders&input=bills`

This will open Editorial, create a new markdown file called "lists," and then immediately output all the incomplete items in an iOS reminders list called "bills."
