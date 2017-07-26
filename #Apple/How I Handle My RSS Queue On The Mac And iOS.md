# How I Handle My RSS Queue On The Mac And

_Captured: 2015-09-30 at 18:11 from [rocketink.net](http://rocketink.net/2013/12/rss-filing.html#requirements)_

![How I Handle My RSS Queue On The Mac And iOS → via @_patrickwelker](http://rocketink.net/uploads/2013/12/2013-12-22-qq-rss.png)

> _How I Handle My RSS Queue On The Mac And iOS -> via @_patrickwelker_

Anyway, the topic here is _filing away RSS posts you want to check out later to a certain location_. For me, in this scenario, plain text is the clear winner.

### 1.3 Requirements

Here's a list of tools that make my system run smooth:

**iPad apps:**

App Task

[Mr. Reader](http://www.curioustimes.de/mrreader)
The only RSS reader that has the feature and x-callback-url support that gives me the freedom of choice when it comes to organize my findings.

[Drafts](http://agiletortoise.com/drafts/)
The action hub for filing most posts to the correct destination.

[Pythonista](http://omz-software.com/pythonista/)
For prompting me to enter some additional text.

Miscellaneous
[Pinboard](http://pinboard.in) and read later apps.

**Mac apps:**

App Task

[ReadKit](http://readkitapp.com/)
It's not Mr. Reader but it gets the job done thanks to the sharing features it offers.

[Keyboard Maestro](http://www.keyboardmaestro.com)
For filing most posts to the correct destination.

Lastly, since we're dealing with "filing stuff away" I eat my own dog food, c.f. [this](http://rocketink.net/2013/12/updated-notes-filing.html) and [that](http://rocketink.net/2013/12/evernote-filing-suite.html).

### 1.4 Destinations

The easiest way to show you all my the destinations where I file posts to is a mind map.[1](http://rocketink.net/2013/12/rss-filing.html)

![mindmap](http://rocketink.net/uploads/2013/12/2013-12-07-destinations-mindmap-640px.png)

Before moving to plain text files I had a single-action lists in OmniFocus, an idea I borrowed from David Sparks screencast series. David has a "[Bugs me" single-action List](http://macsparky.com/omnifocus-screencasts/) for stuff that he wants to fix on his Mac. I soon realized that I need more locations like this and ended up with three of those locations. One for organizational purposes[2](http://rocketink.net/2013/12/rss-filing.html), the other two for automation related material on the Mac and iOS. Giving the fact that I like to tinker these had become quit crowded. Switching to a sequential list didn't help the _review problem_ but moving them out of OmniFocus certainly did.

#### 1.4.1 About Evernote

I'm not 100% sold on the idea of using Evernote, but Federico Viticci with his contagious Evernote posts on MacStories and Sean Korzdorfer with his great [workflow outline](http://www.seankorzdorfer.com/open_notebook/tips%20for%20digital%20note-taking%20with%20day%20one%20and%20evernote.html#section-en) both try their best to convince me. I'm really sitting on the fence when it comes to using Evernote more for my lists.

The benefits of being able to collaborate and having a preview that not relies on Markdown previewing to look nice are there, I can't deny it. Especially on iOS it is nice to have everything under one roof and it just makes even more sense when you keep the [excellent searching capabilities](https://github.com/ChewingPencils/evernote_alfred_workflows/blob/master/ReadMe.md) of Evernote in mind. I have [everything setup](http://rocketink.net/2013/12/evernote-filing-suite.html) to use it for some of my lists and also to migrate more Markdown lists to it effortlessly. The big "but" is: plain text works fine for me, so the purge is postponed. FoldingText has me covered on the Mac with an clean preview of my files and I don't need a collaboration feature for my lists. When it comes to iOS can always use the folder feature of [1Writer](http://1writerapp.com/) to have a separate app for my lists and tasks.[3](http://rocketink.net/2013/12/rss-filing.html)

The wiki is my latest _idee fixe_ and currently I'm more into exploring Evernote - we're having a bit of an Indian summer[4](http://rocketink.net/2013/12/rss-filing.html) \- then exploring the endless possibilities and the usefulness of a personal wiki. Nothing is set in stone and I'd rather take one step at a time hoping that I won't tear down my digital skyscrapers and starting to reconstruct my plain text database.

## 2\. Filing Away RSS Feed Posts On The iPad With Mr. Reader

Mr. Reader does a fantastic job for me at filing my findings away.

![mr-reader-actions](http://rocketink.net/uploads/2013/12/mr-reader-actions.png)

I won't bother you with every service I've set up, but here are some core examples.

### 2.1 Todo's And Running Lists In nvALT

I have services in Mr. Reader for all my todo lists. I choose to prepend them because I think it works better when using the TaskPaper format. The lists I keep in nvALT have the same format, but I append the post that gets added to them.

**IF** the post is a todo THEN prepend to the corresponding TaskPaper file.

Format: `%TAB% - [TITLE](URL) @added(YYYY-MM-DD)`

Here's the decoded Mr. Reader service:
    
    
    drafts://x-callback-url/create?text=	- [{[TITLE]}]{([URL])}&action=TASKPAPER-TODO&x-success=mrreader://
    

To use it we have to encode[5](http://rocketink.net/2013/12/rss-filing.html) it:
    
    
    drafts://x-callback-url/create?text=%09-%20%5B{[TITLE]}%5D{([URL])}&action=TASKPAPER-TODO&x-success=mrreader://
    

The all-caps `TASKPAPER-TODO` is the name of the Drafts Dropbox action that is called. In the example below it's the post get's add to my "@todo iOS Automation" TaskPaper file:

![draftstodo](http://rocketink.net/uploads/2013/12/2013-12-09-draftstodo.png)

### 2.2 Other Lists

The format for the other lists varies, for instance for my scratch file I use a date-centered approach:
    
    
    ### [[M/D/YY, T:M am/pm]]
    [TITLE](URL)  
    [SELECTED-TEXT]
    

Some of the services also save the posts into Evernote or my Markdown Wiki via Drafts.

Those of you who want to read more about Mr. Reader or the endless possibilities of services in Mr. Reader should check out what Gabe Weatherhead and Federico Viticci have to say about the topic:

### 2.3 RocketINK Link List

My [link lists](http://rocketink.net/tags/linklist/) are formatted like this:
    
    
    - [Title](URL)
        - Comment.
    

If I want to add a post a link to an article, I use this Pythonista to script to prompt me for a comment.
    
    
    # -*- coding: utf-8 -*-
    # Ask for input and sets the text to your clipboard
    # By Patrick Welker <http://rocketink.net>
    # Imports
    import console
    import clipboard
    import urllib
    import sys
    import console
    import webbrowser
    # Prepares the console to look nice and let the user know that something is happening
    console.clear()
    console.show_activity()
    # Set variables for the JavaScript bookmarklet arguements 
    title = sys.argv[1]
    url = sys.argv[2]
    # Prompts the user to input a comment
    comment = console.input_alert("Link List","Insert a comment")
    # Formats the Link List entry
    output = ''.join(['- [', title, '](', url, ')', '\n\t- ', comment])
    # Uncomment the next line to print the reformatted output to the console
    #print ''.join(['The Markdown Link and the comment are processed.', '\n\n', 'This is what your Link List entry looks like:', '\n\n', output])
    # Sets the output to the clipboard
    clipboard.set(output)
    # Setup x-callback url actions
    # Passes the output to Drafts where it will get appended to a Dropbox file
    drafts = 'drafts://x-callback-url/create?text='
    actions = '[[draft]]&action=Clipboard%20to%20Link%20List&afterSuccess=Delete'
    #delete = '&afterSuccess=Delete'
    success = '&x-source=Mr.%20Reader&x-success=mrreader://'
    webbrowser.open(drafts + actions + success)
    

**Update:** After that setup a simple Drafts action like this one:

![drafts-prompt](http://rocketink.net/uploads/2013/12/2013-12-09-drafts.png)

Pythonista only offers a small text input field, but it's good enough for me.[6](http://rocketink.net/2013/12/rss-filing.html) Afterwards Pythonista sends the link and comment to drafts which adds them to my Dropbox file.

## 3\. RSS Reading On The Mac

On the Mac I use ReadKit. It has been progressing by leaps and bounds from a simple read later client to a complete reading management software.

Like the introduction already told you I use two of my Keyboard Maestro macros to file posts to plain text notes or add them Evernote.

If you have everything setup from the previous posts all you need are these three macros:

**[DOWNLOAD**](http://cl.ly/T9Dy)

Like I said, there's very little to edit if you have already the filing macros running _(if you're an Evernote user you have to set your target notebooks manually in the macro once - the first comment in the "00)Evernote Locations" macro)_. Otherwise you're all set.

The result in FoldingText looks like this:

![foldingtext](http://rocketink.net/uploads/2013/12/foldingtext.png)

The macro supports selections, but I tend not to use them. Like outlined in the "Notes Palette Filing Macro" this macro grabs the URL, gets a title, adds the date and all of the above to your selected plain text list.

The same happens with Evernote:

![readkit2en](http://rocketink.net/uploads/2013/12/readkit2en.png)

## 4\. RSS Reading On The iPhone

It's literally one minute before 2014 and still have no satisfying way to manage my RSS reading on the iPhone.

![mrreader-iphone](http://rocketink.net/uploads/2013/12/mrreader-iphone.jpg)

I use Reeder but feels underpowered and has zero support for x-callback-url's. What I tend to do is copy the url, head over to Drafts and just send the link to one of my lists.

It's no wonder that on Shawn's [The Sweet Setup](http://thesweetsetup.com/) there is no entry for the best RSS client, yet.

## 5\. Conclusion

Whether it's plain text or Evernote, both work for me and the workflow outlined here is how I progress most of the articles I find interesting - the one exception are videos which go into [Pocket](http://getpocket.com/).

**Mr. Reader and ReadKit rule and they rock my world.**

To view those lists I've setup 4 shortcuts:

  1. `⇧⌥⌘⌃+F2` for my scratch file.
  2. `⇧⌥⌘⌃+F3` for my TaskPaper files.
  3. `⇧⌥⌘⌃+F4` for my running lists.
![lists](http://rocketink.net/uploads/2013/12/lists.png)

They open the respective note in FoldingText which I dearly love for it's infamous talent of hiding most Markdown syntax elements.

In addition to that I have macros for nvALT to navigate to the notes and some smart folders in Finder which display the tagged files.

**What's missing:**

  * FoldingText for iOS for a _cleaner_ Markdown experience.
  * Mr. Reader for iPhone.

**Shortcomings:** You need a data connection for most Draft actions so that your Dropbox note files get updated. Same goes for the Mac macros since we need to fetch the title for the URL's.

  1. Hopefully, I'll update my blog next year so that viewing large images becomes easier - "it's is on the list". [↩](http://rocketink.net/2013/12/rss-filing.html)

  2. In my case all notes (including running lists and task lists) live inside my nvALT folder located in Dropbox. I can use [Unison](http://www.cis.upenn.edu/~bcpierce/unison/) on my server or Mac to sync the changes in my list automatically to individual folders. This works but at the moment I reverted to using [Listacular](http://www.bloomingsoft.com/listacular/) and [Notesy](http://notesy-app.com/). I have no special reason for this and might use 1Writer again at one point. [↩](http://rocketink.net/2013/12/rss-filing.html)

  3. If you need two field you could abuse `console.login_alert` for that purpose. I haven't really tried to use [Launch Center Pro](http://contrast.co/launch-center-pro/) for the prompt since sometimes I get a small delay when starting it. This is enough for me to dismiss it for this use-case and stick with Pythonista. [↩](http://rocketink.net/2013/12/rss-filing.html)
