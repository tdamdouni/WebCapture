# ExtraInfo+ for TaskPaper, now with Wiki Links

_Captured: 2015-08-11 at 16:30 from [brettterpstra.com](http://brettterpstra.com/2015/08/11/extrainfo-plus-for-taskpaper-now-with-wiki-links/?utm_medium=App.net+Broadcast&utm_source=PourOver)_

![](http://cdn3.brettterpstra.com/uploads/2015/08/extrainfowikilinks.jpg)

I published my version of Pedro Lobo's [Extra Info](http://www.hogbaysoftware.com/wiki/TaskPaperExtendedNotes) script for TaskPaper [a couple of years ago](http://brettterpstra.com/2013/08/24/scripting-taskpaper-extra-info-plus/). ExtraInfo+ is a script that reads tags such as `@note` and `@map` in my TaskPaper tasks, and the tag value creates a link to an external note, mind map, outline, or whatever I need in order to expand on the topic. I trigger it with [FastScripts](https://red-sweater.com/fastscripts/) and my brainstorming and extra details for the currently-selected TaskPaper item open instantly.

I still use it almost every day, as it allows me to keep my coding projects in TaskPaper clean and readable, with all references, notes, and brainstorms externally linked.

I also make a lot of use of `[[wiki linking]]` in my notes and tasks, and then use services like [nvWikiLinker](http://brettterpstra.com/2012/09/28/external-linking-for-nvalt-notes-part-1/) to connect to notes in nvALT. I love the double bracket syntax because it's easy to use, and works in any app I can run a service in (I do it in my OmniFocus notes, too). I decided to combine the functionality into ExtraInfo+.

I like to keep certain TaskPaper files in nvALT as well, so there's the added bonus that when I view them in nvALT, all of the wiki links are clickable.

With the new version, you can put `[[Name of the note]]` anywhere in the text of a task and it will be found when you trigger ExtraInfo+. That note pops open in nvALT (or whatever note/editor app you specify as the first option). If the note doesn't exist yet, it's created from a template.

Also, it uses Notification Center for messages if Growl isn't running, which is a step up from `display dialog`.

The new version of ExtraInfo+ is [up on GitHub](http://ttscoff.github.io/ExtraInfoPlus/), and you can find usage instructions there as well. Note that there's a new (and not-yet-documented) property called `baseFolder` which you can set to the common root of all configured paths. Then just use relative paths to the base in other variables.

_P.S._

The routine for finding the WikiLinks is really simple, and a good chunk of code to keep around if you're still using AppleScript. It would be more fun in JavaScript, but I have a LOT of old AppleScripts around…
    
    
    on findBetween(startTag, endTag, theString)
    	set atid to text item delimiters
    	set text item delimiters to startTag
    	set _output to ""
    	set textItems to text items of theString
    	if (count of textItems) > 1 then
    		set _right to item 2 of textItems
    		set text item delimiters to endTag
    		set textItems to text items of _right
    		if (count of textItems) > 1 then
    			set _output to item 1 of textItems as string
    		end if
    	end if
    	set text item delimiters to atid
    	return _output
    end findBetween
    

Just pass it the left and right patterns, and it will return whatever is between them (or an empty string if not located). Example usage:
    
    
    my findBetween("[[","]]",sourceText)
    

Or…
    
    
    my findBetween("<title>","</title>",sourceText)
    
