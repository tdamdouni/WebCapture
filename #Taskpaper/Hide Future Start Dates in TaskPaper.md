# Hide Future Start Dates in TaskPaper

_Captured: 2015-10-18 at 21:18 from [imissmymac.com](http://imissmymac.com/hide-future-start-dates-in-taskpaper/)_

I was recently listening to the [Generational](http://www.70decibels.com/generational/2013/1/26/019-tasks-contexts-and-projects-with-jeff-hunsberger.html) podcast in which Gabe Weatherhead talks with Jeff Hunsberger about task management. Their preferred task management app is [Omnifocus](http://www.omnigroup.com/omnifocus), and they were discussing how Omnifocus hides tasks before their start dates. (For example, if you have a project you don't even need to start thinking about until 2 months from now, you enter the start date as such, and Omnifocus won't show you those tasks until that date hits.)

I have been using [TaskPaper](http://www.hogbaysoftware.com/products/taskpaper), and started thinking about how this can be accomplished using the app's query language. (I can't find the iOS user manual online, but here's the [Mac app user guide](http://imissmymac.com/wp-content/uploads/2013/02/TaskPaper-Users-Guide.pdf). The section about searching TaskPaper starts on page 14.)

TaskPaper supports tags with values in parentheses. So if I have a tag `@start` I can include a date: `@start(2013-05-01)`. (Here I am using the date format YEAR-MONTH-DAY: YYYY-MM-DD. This is useful for search because 2013-02-04 is < 2013-04-01.)

Let's say I have a bunch of tasks in TaskPaper, only some of which I want to have start dates. I want to create a "perspective" in which I don't see tasks that have a start date later than today. That should include all tasks without a start date, and all tasks with a start date of today or earlier. ("Today" is February 4, 2013.)

**Before Query:**
    
    
    - task 1
    - task 2 @start(2013-04-01)
    - task 3 @start(2013-02-04)
    

To exclude start dates later than today, I would include the following query in search: `(@start <= 2013-02-04) or not @start`, i.e., search for tasks that are tagged @start that have values that are less than or equal to today, as well as tasks that are not tagged @start.

**After Query:**
    
    
    - task 1
    - task 3 @start(2013-02-04)
    

If you're on your iPhone, this is a pain to type out. Fortunately, TaskPaper supports [TextExpander Touch](http://smilesoftware.com/TextExpander/touch/index.html), which allows you to type a small snippet which expands into a full string. TextExpander supports [Unicode Date Format](http://smilesoftware.com/textexpander/faq.html) so it's easy to create a snippet that always expands to today's date. The way I format my dates, that would be `%Y-%m-%d`.

I've created a snippet whose abbreviation is _nst_ (for "no start") but you can call it whatever you want. Here is the content you want to enter into TextExpander:
    
    
    (@start <= %Y-%m-%d) or not @start
    

Next time you want to review all your tasks that are currently actionable, just type _nst_ into TaskPaper search and you'll see just what you want to see.

## Addendum (Added 2013-02-05)

Just realized that the above snippet doesn't exclude the archive. Updated:
    
    
    ((@start <= 2013-02-05) or not @start) and not @done
    

## Buy These in the App Store
