# New Editorial Workflow: List Your Reminders

_Captured: 2015-09-28 at 23:46 from [myword.jeffreykishner.com](http://myword.jeffreykishner.com/users/kishner/essays/028.html)_

[Home](http://jeffreykishner.com)

Yesterday I wrote an [Editorial workflow to list incomplete reminders from pre-defined lists](http://myword.jeffreykishner.com/users/kishner/essays/027.html). This morning I have iterated upon that workflow. The [new one](http://www.editorial-workflows.com/workflow/5012964226629632/_BycaAdg3Vg) presents a popup list of _all_ your iOS reminders lists.

    
    #coding: utf-8
    import workflow
    import reminders
    import editor
    
    all_calendars = reminders.get_all_calendars()
    cal = ''
    for calender in all_calendars:
        cal = cal + calender.title + '\n'
    
    
    workflow.set_output(cal)
    

After you choose a list, the workflow creates a markdown header in your text file, followed by a list of all incomplete reminders for that list.

    
    import reminders
    import editor
    import workflow
    
    list = workflow.get_variable('list')
    
    editor.insert_text('# '+list) 
    editor.insert_text('\n\n')
    
    cals = reminders.get_all_calendars()
    
    for calendar in cals:
            if calendar.title == list:
                    tvs = reminders.get_reminders(calendar,completed=False)
                    for x in tvs:
                            editor.insert_text('* ' + x.title) 
                            editor.insert_text('\n')
    
    editor.insert_text('\n')
    

A new line is inserted after the list, so that if you run the workflow again in the same document, a new subheader and list will print right below the first list.

**[Import the Workflow**](http://www.editorial-workflows.com/workflow/5012964226629632/_BycaAdg3Vg)

## Use an URL Scheme for This Workflow

If you want to create a new markdown file called "lists" and run the workflow from [Launch Center Pro](http://contrast.co/launch-center-pro/), you can use this URL action:

`editorial://new/lists.md?command=List%20Your%20Reminders`
