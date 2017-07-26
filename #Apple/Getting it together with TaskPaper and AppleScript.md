# Getting it together with TaskPaper and AppleScript

_Captured: 2015-12-10 at 22:26 from [ashuttleworth.com](http://ashuttleworth.com/2014/06/getting-it-together-with-taskpaper-and-applescript/)_

I've been searching for years for the right system for tracking everything I need to do. At one time or another, I've tried living with paper notes (with or without "[the circle"](http://font.is/the-circle-a-simple-todo-system-to-get-more-things-done/)), index cards, [Things](https://culturedcode.com/things/), [The Hit List](http://www.karelia.com/products/the-hit-list/mac.html), [Remember the Milk](https://www.rememberthemilk.com/), [TaskPaper](http://www.hogbaysoftware.com/products/taskpaper), [Todoist](http://todoist.com), [OmniFocus](https://www.omnigroup.com/omnifocus), [Flow](http://www.getflow.com/), [GitHub Issues](http://github.com/features), [Wunderlist](http://wunderlist.com), [TeuxDeux](https://teuxdeux.com/), [Todo Cloud](http://www.appigo.com/todo-cloud-collaborative-to-do-app-service.html), [Clear](http://realmacsoftware.com/clear), [Basecamp](http://basecamp.com/), [Producteev](http://producteev.com), [Evernote](http://evernote.com), [Simplenote](http://simplenote.com/), Apple's Reminders, and more I'm sure I've forgotten. I've downloaded more iOS apps that have a checkmark for an icon than I can possibly remember.

I never stuck with any one of these systems for more than a few months at a time before I'd find something to hate about it and go looking for another one. And there are things to love and hate about every one of them: The Hit List is beautiful on the Mac, but hasn't been updated in ages, and the iOS app in particular is showing its age.[1](http://ashuttleworth.com/2014/06/getting-it-together-with-taskpaper-and-applescript/) OmniFocus is powerful, but overengineered for my way of thinking, and inconsistent across platforms. Paper notes are good for the brain, but easily lost, not searchable, and impossible to always have with you. TaskPaper is brilliant on the desktop, but doesn't have a great mobile component.[2](http://ashuttleworth.com/2014/06/getting-it-together-with-taskpaper-and-applescript/) (Gabe Weatherhead is a kindred spirit in this - check out his "[task management vision quest](http://www.macdrifter.com/2012/12/a-task-management-vision-quest.html)" for much more of this kind of thing.)

Well, I've finally hit on a system that works for me, and it's been more or less stable for the past year now, which is a personal record. For anyone out there who, like me, is a Mac and iOS user who's comfortable with tinkering and wants things to work in a very particular way, I thought I'd share. Maybe it'll give you an idea or two you might want to incorporate into your own system.

Here's the short version:

  1. TaskPaper on the Mac, enhanced by TextExpander
  2. Apple iCloud Reminders on iOS
  3. Everything synced just the way I want it with AppleScript
  4. _Bonus:_ Logging of done tasks to Day One

Let me break that down.

### Part 1: TaskPaper + TextExpander on my Mac

TaskPaper is such a great idea. Because it's essentially plain text, it has a lot of the same benefits as real paper: the straightforwardness with which it allows you to get thoughts out of your brain - the way you can outline your tasks in whatever hierarchy you like - the way you can jot down notes freely among your tasks while keeping them distinct from the tasks themselves. And its query syntax is, of course, a million times more useful than anything paper can do. (Plus, it was [made in Bangor, Maine](http://www.hogbaysoftware.com/about), just like me.) I love it.

There's no real mobile interface for it [anymore](http://simplicitybliss.com/blog/taskpaper-for-ios-ceased), and the old one wasn't particularly good anyway. That had been holding me back from using it for a long time, until I realized that I was almost entirely managing my tasks while sitting in front of my Mac - and that I could make my own mobile interface for it with AppleScript if I wanted to.

I don't think I'm doing anything particularly novel inside my TaskPaper file itself. I use a basic structure of projects and some pretty typical tags (`@next`, `@today`, `@overdue`, `@start()`, `@due()`) to organize and filter my tasks, and I use a slightly customized version of the excellent [Transparent Blue](https://github.com/dataduke/mac-taskpaper/blob/master/Themes/Transparent%20Blue.taskpapertheme) theme. (My version is [here](https://gist.github.com/ashuttl/52fd642bc979ec607c05).)

#### TextExpander

The most novel thing I'm doing is probably using [TextExpander](http://textexpander.com) to handle some common queries. Here are some of those, inspired again by [Gabe](http://www.macdrifter.com/2014/02/the-taskpaper-rd-notebook.html). Note that these take advantage of TextExpander's ability to manipulate dates.

Shortcut Meaning Expands to…

**;avail**
Tasks available to be worked on in the office
`(@start < %Y-%m-%d or not start) and not (@done or @weekend) and not project future and not project discuss`

**;now**
Tasks to be worked on (or filed from the inbox) right now
`not @done and (project contains inbox or (@today or @overdue or @due or @next or @focus or @due <= %Y-%m-%d or @start <= %Y-%m-%d))+d`

**;done**
Tasks I've completed in the past week
`@done > %@-7D%Y-%m-%d`

I also use TextExpander in the document itself to help add certain kinds of tags quickly, like these:

**;defer**
Start this task tomorrow
`@start(%@+1D%Y-%m-%d)`

**;today**
Make this task due today
`@due(%Y-%m-%d)`

### Part 2: Apple Reminders on my iPhone and iPad

The Apple Reminders system has really only one thing going for it: flawless, transparent background syncing via iCloud. The reminders are always there, on all my devices, always magically up to date. But the user interfaces for dealing with Apple Reminders are so ugly and laborious that these were never going to become my primary task management venue.

The great eureka moment for me around all this was when I realized I didn't need my mobile interface to be able to do everything my desktop interface could. Away from my Mac, all I really need to do is enter tasks quickly and view my high-priority tasks or tasks due today, and maybe check off tasks as I do them. Wouldn't it be wonderful, I thought, if Apple Reminders always knew about the right subset of tasks from my TaskPaper list, the subset I might need to refer to in a flash? And wouldn't it be great if I could add tasks using Apple Reminders (and, by extension, Siri) and have them automatically appear in my TaskPaper list's "Inbox" project? And thanks to Jesse Grosjean and AppleScript, couldn't I make that happen myself?

Yep. I now have five iCloud Reminders lists:

  1. **Inbox**. This is an input channel only. It's where I enter new tasks on the go. The tasks I enter here are automatically added to my TaskPaper file, and deleted from this list, by AppleScript. Unless I've just entered something, this list is empty.
  2. **Now**. Stuff I need to be working on right now. This is automatically populated from my TaskPaper file by AppleScript.
  3. **Scheduled**. Occasional tasks I have to do at a particular time and/or place. TaskPaper doesn't have a time- or location-based reminders feature, and iCloud and iOS have a pretty good one, which I take advantage of when I need to using this list.
  4. **To Buy**. Stuff we need for the house. Shared via iCloud with my wife. This prevents us from having to text each other "I'm at Duane Reade. Do we need anything?" twice a week. We can just check the list instead.
  5. **Wishlist**. Things I want to buy myself, like "good earphones for running." Having these items in their own place helps me make less impulsive decisions about how to spend my money.

### Part 3: The AppleScript glue

Here's the part that feels like magic: iCloud Reminders lists #1 and #2 above are managed automatically by AppleScripts running on my Mac.

I use [Lingon](http://www.peterborgapps.com/lingon/) to do the work of scheduling these scripts. I'd like to have them running on a colocated Mac Mini [somewhere](http://macminicolo.net) so they don't depend on my laptop, but I haven't gotten around to it, and this setup has been good enough so far.

Here are the scripts as they stand right now.

#### Taskpaper-Reminders sync

This script runs every half hour while my laptop is on. It does three things:

  1. Clears out my iCloud "Inbox" list and moves it to the Inbox project of my TaskPaper file.
  2. Looks to see if I've checked off any tasks in my iCloud "Now" list, and if I have, tags the corresponding items in my TaskPaper file with `@done`. Clears this list.
  3. Moves tasks matching my `;now` TextExpander query (actually a slight variation of it) into my iCloud "Now" list. Not all my tasks, mind - that wouldn't be useful. Just the ones that need to be top of mind.

That last step contains a few little niceties that I'm rather pleased about. First, task names in the iCloud list include the name of their containing project. This even works up to a second level of nesting. That means that this TaskPaper syntax:
    
    
    Personal:
      — Call the landlord
      — Fix the cabinet lights
    Websites:
      — Review project plans
      Lincoln Center Festival:
        — Redo sitemap
      Midsummer Night Swing:
        — Check analytics
        — Remove volunteer signup form
    

would be turned into these iCloud Reminders:
    
    
    ☐ Personal: Call the landlord
    ☐ Personal: Fix the cabinet lights
    ☐ Websites: Review project plans
    ☐ Websites/Lincoln Center Festival: Redo sitemap
    ☐ Websites/Midsummer Night Swing: Check analytics
    ☐ Websites/Midsummer Night Swing: Remove volunteer signup form
    

This gives me crucial context when I'm looking at the list in Reminders.app.

One more nicety: if a task is tagged with `@overdue`, it's marked as high priority in Reminders.app, which gives it a little exclamation mark.

Here is the code. I cobbled this together with the help of the [TaskPaper AppleScript wiki](http://www.hogbaysoftware.com/wiki/TaskPaperAppleScripts) and too many Stack Overflow posts to remember, but many thanks go those whose code this is based on.

If you wanted to modify this for your own use, you'd want to change lines 38, 59, and 107 and to include the filename of your TaskPaper document. You might also want to change the query in line 61 to get just the right subset of tasks for the way you use TaskPaper.

    
    # Helper functions
    tell (current date) as «class isot» as string to set current_date to text 1 thru 10
    to joinList(aList, delimiter)
      set retVal to ""
      set prevDelimiter to AppleScript's text item delimiters
      set AppleScript's text item delimiters to delimiter
      set retVal to aList as string
      set AppleScript's text item delimiters to prevDelimiter
      return retVal
    end joinList
    to splitString(aString, delimiter)
      set retVal to {}
      set prevDelimiter to AppleScript's text item delimiters
      log delimiter
      set AppleScript's text item delimiters to {delimiter}
      set retVal to every text item of aString
      set AppleScript's text item delimiters to prevDelimiter
      return retVal
    end splitString
    
    # See if any tasks in Reminders.app "Now" list are completed
    # Mark those that are as @done in TaskPaper
    # Delete tasks currently in Reminders.app "Now" list
    tell application "TaskPaper" to run
    tell application "Reminders"
      run
      tell account "iCloud"
        tell list "Now"
          set tasks to get reminders
          repeat with k from 1 to length of tasks
            set this_task to item k of tasks
            set is_completed to get completed of this_task
            if is_completed is true then
              set this_task_name_and_project to get name of this_task
              set tmp to my splitString(this_task_name_and_project as text, ": ")
              set this_task_name to item 2 of tmp
              tell application "TaskPaper"
                tell document "Active.txt"
                  repeat with each in search with query this_task_name
                    tell each
                      if entry type of each is not project type then
                        make tag with properties {name:"done", value:current_date}
                        exit repeat
                      end if
                    end tell
                  end repeat
                end tell
              end tell
            end if
          end repeat
          delete reminders
        end tell
      end tell
    end tell
    
    # Move "Now" tasks from TaskPaper to Reminders.app
    tell application "TaskPaper"
      run
      tell document "Active.txt"
        set debug to ""
        repeat with each in search with query "((@today or @focus or @overdue or @next or @due <= " & current_date & " ) and not @done)+d"
          if (containing project of each is not missing value) and (entry type of each is not project type) then
            set containing_project to name of containing project of each
            if containing project of (containing project of each) is not missing value then
              set containing_project to (name of containing project of containing project of each) & "/" & name of containing project of each
            end if
            set the_task to containing_project & ": " & name of each
            set the_priority to 0
            if name of every tag of each contains "overdue" then
              set the_priority to 3
            end if
            tell application "Reminders"
              run
              tell account "iCloud"
                tell list "Now"
                  set newremin to make new reminder
                  set name of newremin to the_task
                  set priority of newremin to the_priority
                end tell
              end tell
            end tell
          end if
        end repeat
      end tell
    end tell
    
    # Move Reminders.app inbox to TaskPaper
    # Include the due date, if there is one
    tell application "Reminders"
      tell account "iCloud"
        tell list "Inbox"
          set inbox_contents to (get reminders)
          if length of inbox_contents is greater than 0 then
            repeat with k from 1 to length of inbox_contents
              set this_todo to item k of inbox_contents
              set inbox_item to "- " & (get name of this_todo)
              set due_date to (get due date of this_todo)
              set due_date_string to ""
              if due_date is not missing value then
                set y to text -4 thru -1 of ("0000" & (year of due_date))
                set m to text -2 thru -1 of ("00" & ((month of due_date) as integer))
                set d to text -2 thru -1 of ("00" & (day of due_date))
                set due_date_string to " @due(" & y & "-" & m & "-" & d & ")"
              end if
              set inbox_item to inbox_item & due_date_string
              tell application "TaskPaper"
                tell document "Active.txt"
                  tell project "Inbox"
                    make new entry with properties {name:inbox_item}
                  end tell
                  save
                end tell
              end tell
              delete this_todo
            end repeat
          end if
        end tell
      end tell
    end tell
    tell application "Reminders" to quit
    

#### Stripping tags

About once per week, I methodically go through my TaskPaper list to check in on the status of my various projects. I think the idea behind this ritual is similar to the one behind OmniFocus's "Review mode": it's a time to reflect on where everything is and to make sure I'm not letting anything slip through the cracks. In practice, this often means reprioritizing certain tasks, or more precisely, updating my TaskPaper document to reflect reprioritization that happened elsewhere. At some point during the previous week, I may have put `@next` or `@today` tags on certain tasks that then got postponed or superseded for one reason or another, and among other things, this is my time to fix that.

To facilitate this ritual, I wrote this simple script that removes all the existing `@next` or `@today` tags, so that I can go through the entire list manually and decide again what actually needs to be done next or today. When you run it, the script gives you a chance to select different tags to remove, if `@next` and `@today` don't make sense for your workflow.

I run this script manually. Here's the code:

    
    set userCanceled to false
    
    set prompt to "What tags would you like me to remove? Separate multiple tags with a space."
    
    tell application "TaskPaper"
      try
        set dialogResult to display dialog prompt buttons {"Cancel", "OK"} default button "OK" cancel button "Cancel" default answer "today next" with icon 1
        set tagsToRemove to text returned of dialogResult
      on error number -128
        set userCanceled to true
      end try
    end tell
    
    if userCanceled then
    else
      
      set tagCount to count words of tagsToRemove
      set i to 1
      repeat tagCount times
        
        set tagToRemove to word i of tagsToRemove
        
        tell application "TaskPaper"
          tell front document
            repeat with each in entries
              tell each
                if not (exists tag named "done") then
                  if exists tag named tagToRemove then delete tag named tagToRemove
                end if
              end tell
            end repeat
          end tell
        end tell
        
        set i to i + 1
      end repeat
    end if
    

#### Completed task logging to Day One

This last one is a bonus and a little bit of an experiment. Motivated by [articles about](http://99u.com/workbook/24647/labrat-are-daily-logbooks-worth-the-work) [the importance](http://www.lifehack.org/articles/productivity/how-logging-your-day-can-lead-to-higher-effectiveness.html) [of logging](http://brettterpstra.com/projects/doing/) [what you've done](https://coderwall.com/p/bcthew), the satisfaction of [Todoist's "karma" graph](https://todoist.com/karma), and my own deteriorating memory, I decided to start taking tasks `@done` in my TaskPaper "Archive" project and logging them in my [Day One](http://dayoneapp.com) journal. The script then deletes these tasks from my TaskPaper document. I don't use Day One ritually yet, so, I reasoned, this might make my journal a somewhat more useful representation of my life even when I'm not actively writing in it.

If the task has a date in the `@done` tag - like `@done(2014-06-22)`, as tasks automatically do when being marked as done in TaskPaper - it will be automatically logged under that date in Day One. (If the `@done` tag has no date, the task is logged in Day One under today's date.) This means that I can look through my Day One journal to see at a glance what tasks I completed on that date, and that I don't need to run this script every day to do so. It also means that I can manually backdate `@done` tags if I did something but didn't tag it as `@done` until the next day.

This is handy for reporting to my boss about what I've been up to, but even more importantly than that, it shows the promise of giving me a sense of context and personal history. I'll be interested in reexamining the importance of this logging in a year or so.

At the moment, since this is still an experiment for me, I only run this script manually. If and when I promote it to something that happens automatically, I might schedule it for once every other Sunday or something similarly infrequent.

Here's the code as it stands now. Note that this script requires the [Day One command line interface](https://dayone.zendesk.com/hc/en-us/articles/200258954-Day-One-Tools) to be installed.

    tell application "TaskPaper"
      run
      delay 2
      tell document "Active.txt"
        set done_dates to {}
        repeat with |entry| in search with query "@done"
          tell |entry|
            if (entry type is not project type) then
              if (value of tag "done" is not missing value) and (value of tag "done" is not in done_dates) then
                set done_dates to done_dates & (get value of tag "done")
              end if
            end if
          end tell
        end repeat
        repeat with |date| in done_dates
          set this_date to |date| as string
          set done_on_this_date to ""
          repeat with |entry| in search with query ("project = Archive and @done = " & |date|)
            tell |entry|
              try
                if entry type is not project type then
                  set this_entry to text content
                  if tag "project" exists then
                    set this_entry to (value of tag "project") & ": " & this_entry
                  end if
                  if done_on_this_date is equal to "" then
                    set done_on_this_date to "TaskPaper log:
    " & this_entry
                  else
                    set done_on_this_date to done_on_this_date & "
    " & this_entry
                  end if
                  delete |entry|
                end if
              end try
            end tell
          end repeat
          set shell_text to "echo " & quoted form of done_on_this_date & " | /usr/local/bin/dayone -d='" & this_date & "' new"
          do shell script shell_text
        end repeat
      end tell
    end tell
    

#### My backlog

I have a backlog of new scripts and improvements to these ones that I'd like to work on when I find the time. Some of those:

  * Automatically adding `@today` or `@overdue` tags based on existing `@due()` dates.
  * Logging my GitHub commits and/or closed issues into DayOne.
  * Moving DayOne-logged tasks into a separate "Archive" TaskPaper file instead of just deleting them.
  * Find a way to make it so that my scheduled Reminders-TaskPaper sync script doesn't move me to Desktop 1 when it runs while I'm using an app in full screen mode (or just have this run on a server instead of my primary Mac).

### Conclusion

I realize this must seem impossibly intricate and fiddly, and I guess it probably is. But it's stood up to the test of time for me so far, and it's now at the point where it _just works_. I also don't think it's an overstatement to say that this setup has measurably improved my quality of life. It sounds crazy, but I am happier and more relaxed, and a better employee for Lincoln Center, thanks to TaskPaper and all this AppleScript.

If you have thoughts on TaskPaper, questions about these scripts, ideas about how I could do this better, I want to know about them. Hit me up below or at [@ashuttl](http://twitter.com/ashuttl) or [hello@shuttleworth.is](mailto:hello@shuttleworth.is).

  1. The best things around right now for this are probably [Listacular](http://www.bloomingsoft.com/listacular/) and [Editorial](http://omz-software.com/editorial/), but they lack support for the most important part of TaskPaper: [its query syntax](http://www.macdrifter.com/2014/02/the-taskpaper-rd-notebook.html). [↩](http://ashuttleworth.com/2014/06/getting-it-together-with-taskpaper-and-applescript/)

  2. My idea for this: I'll set up a separate TaskPaper document that will contain the repeating tasks. Those tasks will have a special tag, `@repeat()`, for managing how often they repeat (`@repeat(monday)` means I have to do that every Monday, `@repeat(d15)` means I have to do it on the 15th day of every month, etc.). A new AppleScript will cycle through this document every night and add copies of the repeating tasks to my primary TaskPaper document as appropriate. [↩](http://ashuttleworth.com/2014/06/getting-it-together-with-taskpaper-and-applescript/)
