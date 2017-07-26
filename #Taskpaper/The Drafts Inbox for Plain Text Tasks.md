# The Drafts Inbox for Plain Text Tasks

_Captured: 2015-11-25 at 11:59 from [www.macdrifter.com](http://www.macdrifter.com/2015/01/the-drafts-inbox-for-plain-text-tasks.html)_

Using plain text to manage my projects means I have a lot of flexibility for viewing, editing and adding new entries. When I'm on my phone, I mostly lean on quick viewing and adding. I will occasionally review a project but my phone is primarily a way to input tasks. I use [Drafts for iOS](https://itunes.apple.com/us/app/drafts-4-quickly-capture-notes/id905337691?mt=8&uo=4&at=11l5Ug), of course.

### The Inbox

I have a different TaskPaper file for each area of my work:

  * Home
  * Work
  * Blog
  * Gravity Well Group (my joint venture that produced [TapCellar](http://tapcellar.com))

The top of each file acts as an Inbox. I like this setup because the inbox is immediately visible when the file is opened. By separating the areas of my work, I can quickly focus. I share the "Gravity Well Group" task file with my partner so that we can both add and complete tasks in the same list.[1](http://www.macdrifter.com/2015/01/the-drafts-inbox-for-plain-text-tasks.html)

Here's the directory structure I use for my tasks:
    
    
    Dropbox -> Notes -> Tasks -> GWG
    

I only share the GWG directory. The advantage to nesting these locations is that I can do [useful things](http://www.macdrifter.com/2014/02/alfred-workflow-for-opening-taskpaper-files.html) to quickly open files and also perform reasonably good [search across my notes and my tasks](http://www.macdrifter.com/2015/01/nvalt-quick-search-in-the-finder.html). I name my task files with the TaskPaper extension to enable fancy features in applications like Editorial for iOS.

When I'm on my phone, I open Drafts, type up some tasks and then fire off an action to prepend the text to the appropriate file in Dropbox. Up until a few days ago, my Drafts action added a hyphen and space to the front of every line.[2](http://www.macdrifter.com/2015/01/the-drafts-inbox-for-plain-text-tasks.html) When I'm quickly adding tasks I don't like to bother with hyphens, which is what I tell myself when I forget to add hyphens.

### Drafts Action

Leveraging the JavaScript support in Drafts, I created a new action that does the prefixing more intelligently. It removes extra blank lines and prefixes tasks with a hyphen and a space. The "intelligent" part was the difficult bit. This script respects indentation and also projects.

Any line that ends with a : is left alone since that designates a project. Hyphens are added **after** tabs on a task line. This is how tasks are nested in TaskPaper and a hyphen before the indentation breaks the nesting.[3](http://www.macdrifter.com/2015/01/the-drafts-inbox-for-plain-text-tasks.html)

![](http://www.macdrifter.com/uploads/2015/01/_11_01-18-15%2C_8_34_50_PM.png)

This script uses the [Drafts JS methods](https://agiletortoise.zendesk.com/hc/en-us/articles/202771590-Action-Step-Script) for getting and setting text in the current view.
    
    
    //   Function to remove multiple line breaks
    function removeBlanks(txt){
        txt = txt.replace(/(\r\n|\r|\n)+/g, '$1')
        return txt;
    }
    // Function to Prefix each line of a text block
    function textPrefix(textStr, preFix){
    var i= 0;                
    var array1 = textStr.split("\n");
    // Regex for one or more tabs
    re = /^\t{1,}/;
    // Split the text into lines stored in an array
    for ( i = 0; i < array1.length; i++) {
        // Skip lines that are just blank
        if (array1[i] !== ""){
            taskString = array1[i];
            var tabPrefix = "";
            // Find the tabs
            var tabMatches = re.exec(taskString);
            if (tabMatches){
                tabPrefix = tabMatches[0];
                // Temporarily remove the tabs so we can prefix it
                taskString = taskString.replace(/^\t{1,}/, '')
            }
            // Check to see if it's a project
            var projMatches = removeBlanks(array1[i]).match(/:$/);
    
            if (projMatches == null){
                // If it's not a project then add the hyphen and tabs
                array1[i] = tabPrefix + preFix + taskString;
            } else{
                // Otherwise just put the tabs back
                array1[i] = tabPrefix + taskString;
            }
        }
    }
    // Put all the lines back together
    val = array1.join("\n");
    return val;
    }
    // This is how we change the content in Drafts
    var sel = draft.content;
    // Call the function with a prefix for TaskPaper tasks
    draft.content = (textPrefix(removeBlanks(sel), "- "));
    commit(draft);
    

I've tried to make this a bit modular, mostly because I will reuse the functions in other ways. For example, in task files that I share, I want to add a tag that indicates I'm the person that added the task. I use the @added(GSW 2015-01-18) to indicate I'm to blame and the date that I inserted the new task.

Here's a general tip about actions in Drafts. They're not just for sending text somewhere. Script steps, like the one above, can manipulate text in the current Draft. They can be combined with other actions, but they work well on their own. My Drafts keyboard row is getting cramped. I still have space in the actions menu.

  1. To share a task file, I place it in a sub-directory on Dropbox. I then share that entire directory and Dropbox takes care of the rest, including versioning and collision control. It works really well. [↩](http://www.macdrifter.com/2015/01/the-drafts-inbox-for-plain-text-tasks.html)

  2. This is the TaskPaper syntax for a task. [↩](http://www.macdrifter.com/2015/01/the-drafts-inbox-for-plain-text-tasks.html)

  3. I use tabs and not spaces, like a gentleman. Feel free to modify the script to handle any bastardization that fits your life choices. [↩](http://www.macdrifter.com/2015/01/the-drafts-inbox-for-plain-text-tasks.html)
