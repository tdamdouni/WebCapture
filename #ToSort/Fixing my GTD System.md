# Fixing my GTD System

_Captured: 2015-12-19 at 22:13 from [mygeekdaddy.net](http://mygeekdaddy.net/2014/03/03/fixing-my-gtd-system/)_

That's it, I've had it. I've declared GTD bankruptcy and I'm starting over.

Why?

I've slowly realized that I've started doing things wrong. For quite some time the backbone of my GTD system has been OmniFocus. But with the recent buzz about using text file based systems, like TaskPaper, to manage task and project lists, I decided maybe I needed to look at my own system again. As I started taking a look at what I was doing I realized I wasn't prescribing to David Allen's "clean edges" mentality. David's idea is that where and how you manage information should be handled with distinct categories. Looking at my system I began to realize I was mixing my categories in order to fit everything into OmniFocus.

Actually… my system was an utter mess.

#### Right tool, right task

In my old system, the idea was OmniFocus would be just for tasks. This may seem like a no brainer but over time I started mixing my inboxes. OmniFocus became my task list, my thought collector, and my project planning app. While those three are related, mixing them all into OmniFocus caused problems in actually getting things done. I'd put due dates on ideas I wanted to think about, but didn't have any actionable steps. I'd have an actual project named so similar to a project I was planning, because I put all my ideas into OmniFocus, that tasks would get inter-mingled.

I finally sat back and looked at the three phases I have in my work:

  * Actual project tasks and action lists
  * Project planning/staging
  * Ideas and thought collections

These were three distinct phases of how I wanted to get things done for me so I looked at having three distinct apps to keep "clean edges". I ended up with the following setup:

  * OmniFocus - Action Lists: OmniFocus continues to be where I put my active projects and action lists. If I have something I have to get started this week (Start By) or needs to be finished by next Wed (Due By), these action lists are in OmniFocus. This allows me to put other to do items, like shopping lists or geo-fenced actions in OmniFocus as well. OmniFocus is where I go for my next action, or wonder what I should being doing next, and know I will find only actionable items.
  * Evernote - Project Planning - Evernote is where I keep ideas and reference information of current projects or a project I _may_ do in the future. This was the number one problem with my previous system. Previously I would dump my "need to do" actions in with my "some day/maybe" stuff. Evernote is now my repository of "stuff" I may do some day, but not feel guilty about not looking at as part of my weekly review. 
  * Drafts - Thought Collection: Drafts is where I will collect any thoughts or ideas for further processing at a later time. I have Drafts setup on all my iOS devices and so I'm quickly able to grab ideas as they come to me. From Drafts I can move the idea if it's actionable to OmniFocus or part of a larger project plan/long term process to Evernote. Or it could sit in Drafts until the idea has percolated to the point it can be moved or completely dropped.  


#### System of Tools

Beyond these three apps, I've looked at how I can further use the tools I have on hand right now to either automate or make my process more powerful. Some of the other apps or tools I use include:

  * [Dropbox](https://www.dropbox.com/): Notes and file sharing among iOS and OS X devices.
  * [iCloud](http://www.apple.com/icloud/): Syncs bookmarks across my iOS devices.
  * [Mail Drop](http://support.omnigroup.com/omnifocus-mail-drop): The Omni Group has a great service to send email to a predefined mail address and convert the message to an action in OmniFocus. 
  * [Pythonista](https://itunes.apple.com/us/app/pythonista/id528579881?mt=8&uo=4): Pythonista is slowly becoming the glue that holds all my GTD building blocks together. Read further on for an example.
  * [Editorial](https://itunes.apple.com/us/app/editorial/id673907758?mt=8&uo=4): As Pythonista has grown, so has my use of it's sister program Editorial. 
  * [Fantastical 2](https://itunes.apple.com/us/app/fantastical-2-calendar-reminders/id718043190?mt=8&uo=4): Fantastical is my _only_ calendar app now. The ease of entry with natural language and being able to select specific reminder lists from Drafts is what makes this app one of the best. In fact I use the iPhone version on my iPad because there isn't one available for iPad yet.

#### The glue that binds

As I previously mentioned, a lot of my processes are starting to revolve around using Pythonista. One of the core workflow processes uses just two simple steps. One is a simple javascript bookmark I put in my Safari favorites and the other is a script in Pythonista:

**JavaScript Bookmark:** This javascript is placed in a bookmark and used to collect information from a web page and run a Pythonista script.
    
    
    javascript:window.location='pythonista://ImportToDrafts?action=run&argv='+encodeURIComponent(document.title) +'&argv='+encodeURIComponent(document.location.href)
    

**Pythonista Script:** The script below is called upon by the bookmark above. When the script runs it takes the text I copied from the web page, the URL, and Title and formats the information into a clean note.
    
    
    import webbrowser
    import clipboard
    import urllib
    import sys
    
    title = sys.argv[1]
    url = sys.argv[2]
    note = clipboard.get()
    
    full_note = ''.join([title,'\n\n', url, '\n\n', note])
    full_note = urllib.quote(full_note.encode('utf-8'))
    
    webbrowser.open('drafts://x-callback-url/create?text=' + full_note)
    

For example: I want to take the highlighted text on the web page and put it into a Drafts note:

![](http://share.mygeekdaddy.me/_img_BLOGX_Fixing_my_GTD_system_2014_03_03_123958.png)

> _I would simply do the following:_

  1. Open the web page in Safari and highlight/copy the text.
  2. From either my short cuts or favorites, run the javascript bookmark to "Clip to Drafts". The javascript bookmark will collect the URL and web page title and pass it on to the Pythonista script "ImportToDrafts".
  3. Pythonista now takes the URL and Title values passed from the javascript and the clipboard contents to transform the text pieces into a new note.
  4. After the javascript and python scripts run, the new note is cleanly formatted and passed to Drafts.
![](http://share.mygeekdaddy.me/_img_BLOGX_Fixing_my_GTD_system_2014_03_03_124200.png)

Boom! Now I can make a choice to further push this into Evernote or OmniFocus, or simply hold onto the information as an idea for further processing at a later time.

#### iOS vs OS X
