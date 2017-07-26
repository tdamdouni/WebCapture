# Editorial Workflows - Send TaskPaper Tasks to Reminders

_Captured: 2015-12-10 at 15:08 from [plobo.net](http://plobo.net/editorial-workflows-send-taskpaper-tasks-to-reminders/)_

With the advent of [Fantastical 2 for iPad](https://itunes.apple.com/us/app/fantastical-2-for-ipad-calendar/id830708155?mt=8&at=11l5Lz), I thought it would be as good a time as any to write about these two little [Editorial](https://itunes.apple.com/us/app/editorial/id673907758?mt=8&at=11l5Lz) Workflows I have. As I've mentioned before, I'm using Reminders to keep track of my time sensitive tasks. If something needs to be done on a certain day at a certain time, then it'll find it's way to Reminders.

When coming across such a task, I add the tag `@remind` with an optional date and time. When I trigger the workflow, it runs through the current TaskPaper document, identifies any task with that tag and recursively adds it to Reminders with the same method I covered in a previous [post](http://plobo.net/recursive-actions-with-launchcenterpro-and-pythonista).

They're still very raw and need much refinement, but given I've found some use for them in my daily workflow, you may too? In time, I'll no doubt improve on them to add more features, error testing and possibly some form `@done` status sync.

Currently, there are two workflows. One uses Fantastical 2 and the other GoodTask. Each workflow allows you to define a few settings:

  * **Notes** -- If you activate this, then any notes and tags that the TaskPaper task has will be added to the Reminder's body;
  * **Time** -- If no time is specified in the task's tag, then the script will use this time as the default;
  * **List** -- The Reminders list to which the task will be added;
  * **Tag** -- The tag used. You can choose which best suits your needs.

### Fantastical

Get the Fantastical workflow [here](http://editorial-app.appspot.com/workflow/5780982493872128/92wqsq7e3_c). Given that the script that does all the heavy lifting can't be seen on the Editorial Workflow site, I'm adding it here for clarities sake. You'll no doubt notice that the script for Fantastical is much simpler and versatile. That's thanks to Fantastical's excellent Natural Language Parsing engine
    
    
    #coding: utf-8
    import workflow
    import re
    import urllib2
    import datetime
    
    PARAMS = workflow.get_parameters()
    
    DEFAULT_TIME = PARAMS['Time']
    DEFAULT_LIST = PARAMS['List']
    ADD_NOTES = PARAMS['Notes']
    TAG = PARAMS['Tag']
    
    
    def stripTags(task):
        """Strip tags from a task item and return the resulting list.
        Will ommit the remind tag."""
    
        #Strip remind tag
        tp_task = re.sub('@remind(\(\d{4}-\d{2}-\d{2}\s*((|\d{2}:\d{2}))\)|)','',task,re.M)
    
        # Get list of remaining tags
        tp_task = re.finditer("\@\w+(\(\d{4}-\d{2}-\d{2}\s*((|\d{2}:\d{2}))\)|)", tp_task, re.M)
    
        return  [tags.group() for tags in tp_task]
    
    
    def taskTime(task):
        """Will processo the date/time value in the remind tag and create a proper
        date/time string to use when creating the task"""
    
        tp_task = re.search('(?<=@remind\().*(?=\))',task,re.M)
        dt = tp_task.group().split(" ")
    
        # Get the date
        try:
            date_str = datetime.datetime.strptime(dt[0],'%Y-%m-%d').strftime('%d-%m-%Y')
        except IndexError, errmsg:
            return "There is no valid date defined."
    
        # Get the time
        try:
            time_str = dt[1]
        except IndexError, errmsg:
            time_str =  DEFAULT_TIME
    
        return (date_str, time_str)
    
    def main():
        arg = workflow.get_input().encode('utf-8')
        tag_pattern = re.compile("((?!.*@done).*" + TAG +".*(\n*\t*(?!\w.*:$)\w.*)*)", re.M)
        task_pattern = re.compile('\s{1}@\w+(\(\d{4}-\d{2}-\d{2}\s*((|\d{2}:\d{2}))\)|)', re.M)
        notes_pattern = re.compile("^-.*\n*|\t")
    
        # Isolate tasks with @remind tag
        tp_remind = re.findall(tag_pattern, arg)
    
        # Iterate over every task tagged and process it.
        url_str = ''
        for match in tp_remind:
    
            # Process Task
            src_task = re.sub("- ","",re.search("^-.*", match[0].strip()).group())
            task = re.sub(task_pattern,'',src_task)
    
            # Process task time
            dt =  taskTime(src_task)
    
            # Prepate notes if Notes == True, else ommit notes from Reminder.
            if ADD_NOTES:
                # Get list of tags from task without remind tag
                tag_str = ' '.join([tag for tag in stripTags(src_task) if stripTags(src_task)])
    
                # Prepare Notes
                notes = (re.sub(notes_pattern,"", match[0].strip())).strip()
    
                # Create body of task
                if tag_str and notes:
                    notes_str = notes.strip()+'\n'+tag_str.strip()
                elif tag_str and not notes:
                    notes_str = tag_str.strip()
                elif notes and not tag_str:
                    notes_str = notes.strip()
                else:
                    notes_str = ''
    
            else:
                notes_str = ''
    
            # Add the task to Reminders.
            task_str = '%s on %s at %s /%s' %(task, str(dt[0]), str(dt[1]), DEFAULT_LIST)
    
            if url_str == '':
                url_str += 'fantastical2://x-callback-url/parse?sentence='+urllib2.quote(task_str,'')+'&notes='+urllib2.quote(notes_str)+'&reminder=1'
    
            else:
                url_str = 'fantastical2://x-callback-url/parse?sentence='+urllib2.quote(task_str,'')+'&notes='+urllib2.quote(notes_str,'')+'&reminder=1&x-success='+urllib2.quote(url_str,'')
    
        workflow.set_output(url_str)
    
    
    if __name__ == '__main__':
        main()
    

## GoodTasks

Get the GoodTask workflow [here](http://editorial-app.appspot.com/workflow/5888007441743872/tP3OjDdMQnk).

Once again, this workflow uses a custom action and therefore the script isn't visible on the workflow site, but you can get a glimpse here before downloading if you prefer.
    
    
    #coding: utf-8
    import workflow
    import re
    import urllib2
    import datetime
    
    PARAMS = workflow.get_parameters()
    
    DEFAULT_TIME = PARAMS['Time']
    DEFAULT_LIST = PARAMS['List']
    ADD_NOTES = PARAMS['Notes']
    TAG = PARAMS['Tag']
    
    
    def stripTags(task):
        """Strip tags from a task item and return the resulting list.
        Will ommit the remind tag."""
    
        #Strip remind tag
        tp_task = re.sub('@remind(\(\d{4}-\d{2}-\d{2}\s*((|\d{2}:\d{2}))\)|)','',task,re.M)
    
        # Get list of remaining tags
        tp_task = re.finditer("\@\w+(\(\d{4}-\d{2}-\d{2}\s*((|\d{2}:\d{2}))\)|)", tp_task, re.M)
    
        return  [tags.group() for tags in tp_task]
    
    
    def taskTime(task):
        """Will processo the date/time value in the remind tag and create a proper
        date/time string to use when creating the task"""
    
        tp_task = re.search('(?<=@remind\().*(?=\))',task,re.M)
        dt = tp_task.group().split(" ")
    
        # Get the date
        try:
            date_str = dt[0]
        except IndexError, errmsg:
            return "There is no valid date defined."
    
        # Get the time
        try:
            time_str = dt[1]
        except IndexError, errmsg:
            time_str =  DEFAULT_TIME
    
        return str(date_str)+' '+str(time_str)
    
    def main():
        arg = workflow.get_input().encode('utf-8')
        tag_pattern = re.compile("((?!.*@done).*" + TAG +".*(\n*\t*(?!\w.*:$)\w.*)*)", re.M)
        task_pattern = re.compile('\s{1}@\w+(\(\d{4}-\d{2}-\d{2}\s*((|\d{2}:\d{2}))\)|)', re.M)
        notes_pattern = re.compile("^-.*\n*|\t")
    
        # Isolate tasks with @remind tag
        tp_remind = re.findall(tag_pattern, arg)
    
        # Iterate over every task tagged and process it.
        url_str = ''
        for match in tp_remind:
    
            # Process Task
            src_task = re.sub("- ","",re.search("^-.*", match[0].strip()).group())
            task = re.sub(task_pattern,'',src_task)
    
            # Process task time
            dt =  taskTime(src_task)
    
            # Prepate notes if Notes == True, else ommit notes from Reminder.
            if ADD_NOTES:
                # Get list of tags from task without remind tag
                tag_str = ' '.join([tag for tag in stripTags(src_task) if stripTags(src_task)])
    
                # Prepare Notes
                notes = (re.sub(notes_pattern,"", match[0].strip())).strip()
    
                # Create body of task
                if tag_str and notes:
                    notes_str = notes.strip()+'\n'+tag_str.strip()
                elif tag_str and not notes:
                    notes_str = tag_str.strip()
                elif notes and not tag_str:
                    notes_str = notes.strip()
                else:
                    notes_str = ''
    
            else:
                notes_str = ''
    
            # Add the task to Reminders.
            task_str = 'goodtask://x-callback-url/add?text=%s&list=%s&due=%s&alarm=1&notes=%s' \
            %(urllib2.quote(task), DEFAULT_LIST, urllib2.quote(dt), urllib2.quote(notes_str))
    
    
            if url_str == '':
                url_str = task_str
    
            else:
                url_str = task_str+'&x-success='+urllib2.quote(url_str,'')
    
    
        workflow.set_output(url_str)
    
    
    if __name__ == '__main__':
        main()
    

I sincerely hope you too find the workflows useful and let me know if you come across any odd behavior.
