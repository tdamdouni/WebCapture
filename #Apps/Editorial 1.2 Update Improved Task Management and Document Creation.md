# Editorial 1.2 Update Improved Task Management and Document Creation

_Captured: 2015-06-15 at 19:15 from [www.macdrifter.com](http://www.macdrifter.com/2015/06/editorial-12-update-improved-task-management-and-document-creation.html)_

![Editorial](http://www.macdrifter.com/uploads/2015/06/EditorialIcon512_masked.png)

If you own an iOS device and use words a lot you probably have [Editorial](https://geo.itunes.apple.com/us/app/editorial/id673907758?at=11l5Ug) on your home screen. Hi, me too. Today we get to rejoice because it's the annual update of Editorial![1](http://www.macdrifter.com/2015/06/editorial-12-update-improved-task-management-and-document-creation.html)

![Tag Highlights](http://www.macdrifter.com/uploads/2015/06/IMG_20150613_074811.PNG)

> _Tag Highlights_

I'll save some general discussion about iOS text editors for the end because I think most people just come to find out what's new. If that catches your attention you might stick around to find out a bit more about how I use this stuff all day, every day.

### Task Support Gets Better

Now you can manage tasks in Editorial like a boss.[2](http://www.macdrifter.com/2015/06/editorial-12-update-improved-task-management-and-document-creation.html) Editorial provides built-in support for the TaskPaper format with handling of projects, tag highlighting and completing tasks for files saved with the .taskpaper extension. The iPhone version now has feature parity of the task management features, including check boxes and drag handles to move tasks up and down a list.

First, jump into the Editorial preferences and make a few tweaks. Editorial will highlight lines with user configured tags.

![Tag Configuration](http://www.macdrifter.com/uploads/2015/06/IMG_20150613_065608.PNG)

> _Tag Configuration_

Taskpaper files are easily differentiated in the Editorial file browser.

![File Browser](http://www.macdrifter.com/uploads/2015/06/IMG_20150613_070214.PNG)

> _File Browser_

The project view is very helpful. Open the list and tap a sub-project to instantly jump there in the document.

![Project List](http://www.macdrifter.com/uploads/2015/06/IMG_20150613_074820.PNG)

> _Project List_

New in version 1.2 is support for folding text blocks with folding and unfolding actions in the workflow collection. The Fold action works on either the current selection of a specified range. The Fold Lines Containing... action uses a regular expression to fold lines that match. The important thing to remember with these actions is that they are additive. You can fold based on one term and then fold other lines based on another term. You don't need some ferocious regular expression to do it all at once.

![Folding Action](http://www.macdrifter.com/uploads/2015/06/IMG_20150614_163517.PNG)

> _Folding Action_

There are also new python methods for folding text from within a script. If you're really adventurous you can take advantage of the new Reminders module reading or editing items in the iOS Reminders list. There's a lot to feast on in this update.

#### Script to Process Tags

This is an Editorial script that I use many times a day. I've added it as an action on almost all of my Taskpaper macros. The script processes every line of the Taskpaper looking for @due tags that contain dates with the format YYYY-MM-DD and evaluating those against today's date. If the date is equal to or less than today, it changes the tag to @today.

![Processing Due Tags](http://www.macdrifter.com/uploads/2015/06/IMG_20150614_100604.PNG)

> _Processing Due Tags_

Below is the python script that does the work. I've saved this as a custom action and add it to almost every script that interacts with taskpaper files. This way I'm continually checking my tasks to see if I've hit a due date.
    
    
    import editor
    import console
    import re
    import workflow
    import time
    
    #console.clear()
    
    #date format is YYYY-MM-DD like a sane person
    today_date = time.strftime('%Y-%m-%d')
    
    # lets go ahead and set a workflow variable. maybe it will be handy some day
    workflow.set_variable("todayDate", today_date)
    
    f=editor.get_text()
    
    #we will need the text length at the end when we replace the editor text
    f_count = len(f)
    
    #Looks for @due(YYYY-MM-DD) tags
    start_pattern = r'@due\((20[1-9][0-9]\-[0-1][0-9]\-[0-3][0-9])\)'
    
    term = start_pattern
    pattern = re.compile(term, flags=re.IGNORECASE)
    
    #general function to test a date string against today's date
    def past_date(tag_date):
        #print tag_date, ' vs ', today_date
        if time.strptime(tag_date, '%Y-%m-%d') <= time.strptime(today_date, '%Y-%m-%d'):
            return True
        else:
            return False
    
    # test the tag and date. set to @today if required
    def check_tag(eval_tag):
        match = re.search(pattern, eval_tag)
        # change tag if past the date otherwise leave it alone
        if past_date(match.group(1)):
            #print 'TODAY: ', str(match.group(0))
            return '@today'
        else:
            #print 'found: ',match.group(0)
            return match.group(0)
    
    new_text = re.sub(pattern, lambda m: check_tag(m.group(0)), f)
    
    editor.replace_text(0, f_count, new_text)
    

Here's an [Editorial workflow](http://www.editorial-workflows.com/workflow/5333020760342528/sz9-7vqOMo4) that combines the script with folding actions to create a next action view.

There's already [great work](http://www.editorial-workflows.com/workflow/5910135985668096/tH-KNGXpjyU) going on in the Editorial community to extend these new folding functions along with the Taskpaper support.[3](http://www.macdrifter.com/2015/06/editorial-12-update-improved-task-management-and-document-creation.html)

### Document Templates

At first, the new document template feature seems nice but simple. It's not. It's nice and very powerful. Document Templates in Editorial 1.2 are really just macros that execute before you open a document. Out of the box, there are some simple templates that create new documents with different file extensions. But this is the least a template can do.

![Document Templates](http://www.macdrifter.com/uploads/2015/06/IMG_20150614_080506.PNG)

> _Document Templates_

You build a document template as you would any other Editorial macro. All of the normal actions are available but you start with the "New Document" action already sitting there.

Here's a "basic" template that I use for general notes. This template asks for a document title and then creates a new file with a file name that includes a time stamp like 2015-06-14_074246. It also adds a couple header lines in the file and positions the cursor ready to type. Simple but helpful.

![Basic Template](http://www.macdrifter.com/uploads/2015/06/IMG_20150614_073249.PNG)

> _Basic Template_

This idea can be extended by a lot. For example here's a template that uses the clipboard contents to create a new document. There are no prompts and nothing to edit (thanks to that little toggle at the bottom of the action). The document is created and we're done.

![Clipboard Notes](http://www.macdrifter.com/uploads/2015/06/IMG_20150614_075111.PNG)

> _Clipboard Notes_

Document templates save me so much work, I actually prefer to start blog posts in Editorial. I get all of the YAML headers I need and the title is automatically inserted as Title Case.

![Blog Post Template](http://www.macdrifter.com/uploads/2015/06/IMG_20150614_080259.PNG)

> _Blog Post Template_

Here's a bit of a revelation: Document Templates do not need to create anything. They can be shortcuts to open files too.

Let's extend this a bit more. I have several list files where I track collections of things and notes about them. Book recommendations, movies I want to watch, even gifts I want to buy for people are all in these plain text files. Here's a New Document template that shows a list of lists to select from and then opens that file. The cursor is placed at the end of the list ready to add something new.

![Open Lists](http://www.macdrifter.com/uploads/2015/06/IMG_20150614_114227.PNG)

> _Open Lists_

It's a simple enough macro. Each line of the list action is an item to show in the selection list. Each item is followed by a tab and then the file name to open when that item is selected from the list.

![List of Lists](http://www.macdrifter.com/uploads/2015/06/IMG_20150614_114545.PNG)

> _List of Lists_

### Taskpaper Lists

I previously used plain old .txt files for these lists. However, using the .taskpaper extension means that Editorial gives me extra utility without any extra effort. I can check items off and add notes that look nice too. I've tried keeping these in Reminders.app but it just created clutter and Reminders sucks for adding notes and links.

Of course, templates are optional in Editorial 1.2. You can always configure it to use a default for new files instead.

![Template Picker Settings](http://www.macdrifter.com/uploads/2015/06/IMG_20150613_065701.PNG)

> _Template Picker Settings_

### More

There are a lot of changes throughout Editorial. From little improvements to manual syncing to large changes in the section viewer.

![Manual Sync](http://www.macdrifter.com/uploads/2015/06/IMG_20150613_070152.PNG)

> _Manual Sync_

The new tabbed view for accessory panels is nice but takes a bit of getting comfortable with on the iPhone. One huge advantage of the new design is accessing multiple documentation pages and Web sites at the same time.[4](http://www.macdrifter.com/2015/06/editorial-12-update-improved-task-management-and-document-creation.html) There's also integrated support for 1Password in the built in browser. How nice is that?

![Tabbed View](http://www.macdrifter.com/uploads/2015/06/IMG_20150614_205357.PNG)

> _Tabbed View_

There are several new modules in Editorial 1.2, including the previously mentioned support for Reminders. There's also a new twitter module and a new dialogs module for creating quick interactive workflows. There's also a broadly useful new action for creating PDFs.

You can now view [Critic Markup](http://criticmarkup.com) or [Fountain](http://fountain.io) files with beautiful formatting right in the Editorial editor.

![Critic Markup Support](http://www.macdrifter.com/uploads/2015/06/IMG_20150614_211629.PNG)

> _Critic Markup Support_

Syntax support is all around better in Editorial 1.2. While it's not intended to be a code editor, there's support for syntax highlighting of a variety of common formats.

![Syntax Support](http://www.macdrifter.com/uploads/2015/06/IMG_20150614_211300.PNG)

> _Syntax Support_

The new quick settings option in the editor view (tap the document title) is terrific too. Zoom text or just quickly turn on word count.

![Quick Settings](http://www.macdrifter.com/uploads/2015/06/_6_06-14-15%2C_9_09_00_PM.png)

> _Quick Settings_

### What's Missing

The obvious missing piece for this update are extensions. I'd love options for using Editorial as a general text extension. Apps like Workflow on iOS have really raised the bar. While I don't expect (or need) extensions for most apps, a text editor as powerful as Editorial would be a huge help.

I'd also love to see Editorial support additional document syncing options beyond Dropbox. I realize that's the de facto standard these days but I'd be thrilled to see a new trend. Amazon Cloud, WebDAV, SCP or even GitHub would be welcome as alternatives.

### Post-Amble

Editorial is irreplaceable to me. It's half of why I use my phone. It's a fantastic text editor, a superior task manager and a powerful scripting tool. Heck, it even has a terrific browser. Updates are not frequent but they are significant. Each iterations of Editorial feels almost like an entirely new application. As a beta tester of Editorial, it's gut wrenching when the version expires. I almost can't work.

Drawing a parallel to Drafts for iOS, Editorial is as simple or sophisticated as I want it to be. Without any customization it's a top tier text editor. With some elbow grease it's peerless.

Editorial doesn't replace [Drafts](https://geo.itunes.apple.com/us/app/drafts-4-quickly-capture-notes/id905337691?at=11l5Ug) for me. Drafts still provides that singular experience of opening the app to an empty page ready to write. Editorial is much more powerful and is where I keep things of substance and importance. Drafts is where I go when I don't know what I will need to do with some words. Editorial is where I go to work.

[Editorial](https://geo.itunes.apple.com/us/app/editorial/id673907758?at=11l5Ug) | Universal | $7

  1. I think very highly of Ole Zorn, the developer of Editorial and [Pythonista](https://geo.itunes.apple.com/us/app/pythonista/id528579881?at=11l5Ug). I think he is one of the very best iOS developers anywhere. His ideas are inspiring and his designs are impeccable. Each update of Editorial is like a complete rethinking of how humans can work with text, but there are long gaps between updates. I'm O.K. with it but I know it's something people ask about. It's obvious he loves this app and we're all lucky for that. [↩](http://www.macdrifter.com/2015/06/editorial-12-update-improved-task-management-and-document-creation.html)

  2. Earlier versions of Editorial laid the ground work for working with Taskpaper files. Version 1.2 extends that significantly. This is a highlight of using many of the features together. [↩](http://www.macdrifter.com/2015/06/editorial-12-update-improved-task-management-and-document-creation.html)

  3. There's a new URL scheme for opening links in the Editorial browser. Just prepend a URL with "editorial-" like this: editorial-http://www.macdrifter.com and it will open right up. [↩](http://www.macdrifter.com/2015/06/editorial-12-update-improved-task-management-and-document-creation.html)
