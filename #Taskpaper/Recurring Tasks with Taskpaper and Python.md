# Recurring Tasks with Taskpaper and Python

_Captured: 2015-06-11 at 23:47 from [www.movingelectrons.net](http://www.movingelectrons.net/blog/2015/05/03/recurring-tasks-with-taskpaper-and-python.html)_

I have tried not less than 20 project/task management applications and services. From web based to desktop applications in both Mac and Windows. I have also read many reviews, including [this one](http://www.macdrifter.com/2012/12/a-task-management-vision-quest.html) by [Gabe Weatherhead](https://www.twitter.com/macdrifter), which I consider the mother of all reviews when it comes to task management services.

It has been very difficult to find a service fitting my needs, which I thought were not that hard to begin with. Here are my requirements for the ideal task management system:

  * Multi-platform.
  * Capable of being accessed from mobile devices.
  * Offline capabilities in both desktop and mobile versions.
  * Fast interaction.
  * Easy integration with other apps and services.

After much trial and error, I settled for one of the most basic systems: text files. Specifically the **Taskpaper** format. You can read about it [here](http://www.hogbaysoftware.com/products/taskpaper). The beauty of this system is that it's ubiquitous and tremendously flexible.

The Taskpaper format is simple, yet effective. However, that simplicity derives in some inherent limitations like the lack of a reminding system and the challenge that represents working with recurring tasks. For the former, there are some scripts ([here](https://macintoshguy.wordpress.com/2013/01/09/taskpaper-to-reminders-applescript-version-two/) and [here](http://www.hogbaysoftware.com/wiki/AddTaskToReminders)) tackling the problem. However, I'm more interested in the latter as I deal with recurring tasks for both personal and work projects. Putting these tasks in the Reminders app or the Calendar app would be a solution. However, I prefer having all tasks associated to a project in one place. Also, these tasks don't necessarily have to have a specific time associated to them. So, for my user case, there is no point in creating reminders.

I came up with a simple system to work with recurring tasks on Taskpaper files. It makes use of a specific syntax and a python script that runs behind the scenes.

## Recurring Syntax

A recurring task is assigned a `@freq` tab indicating how frequently that task needs to be done in **days, weeks, months or years**. For example, if I wanted to mow my lawn every two weeks beginning on May 1st, 2015, this is how the task would look like:

`\- Mow lawn @freq(2w) @due(2015-05-01)`

And if I wanted to change the A.C. filters every three months:

`\- Change A.C. filters @due(2015-05-01) @freq(3m)`

Pretty easy, right?. Now, let's say that last task is completed the same day. It would look like this in the Taskpaper file:

`\- Change A.C. filters @due(2015-05-01) @freq(3m) @done(2015-05-91)`

This is where the script comes into play.

## About the Script

The script is not tied to a specific application, it's simply meant to be run on a machine (i.e. Mac, PC or Linux) with Python installed. On my Mac, I just created an [Alfred](http://www.alfredapp.com/) workflow to run it. The Workflow actually runs another script at the same time to put together a _Today View_ similar to [this one](http://www.movingelectrons.net/blog/2013/12/2/todolist), but associated to the Taskpaper file (leave a comment below if you want to check that one out). To run the script on a windows machine, I created a batch file which I call from [Launchy](http://www.launchy.net/).

This script takes the taskpaper file passed as an argument and reschedules completed recurring tasks (like the one in the example above) based on their **due date, done date and recurring frequency**. The task is put back in the project it was completed on, even if it has already been moved to the _archive_ section at the end of the file. This, the script looks for the following tags:

  * `@due(YYYY-MM-DD)`
  * `@done(YYYY-MM-DD)`. If the done tag is not included, _the script won't register that task as completed_.
  * `@freq(nF)`. This is the recurring frequency, where `n` is an integer and `F` can be `d` (days), `w` (weeks), `m` (months) or `y` (years). 

**Note:** If a task is completed _before_ its due date, it will be put at the top of the file with the unmodified due date for further manual processing.

Find below the actual Python code. You can also check it out on GitHub through [this](https://gist.github.com/Moving-Electrons/05aacf1766dc98092922) link.
    
    
    #!/usr/bin/python2.7
    
    import re
    import shutil
    import os
    import sys
    from datetime import date, timedelta
    
    ''' This script takes the taskpaper file passed as an argument and reschedules completed    recurring tasks based on their 
    due date, done date and recurring frequency. The task is put in the project it was completed    on, even if it has been 
    archived at the end of the file. The script looks for the following tags:
    
    - @due(YYYY-MM-DD) e.g. @due(2015-04-17)
    - @done(YYYY-MM-DD) e.g. @done(2015-04-17). If the done date is not included, the script    won't register that task as completed.
    - @freq(nF). This is the recurring frequency, where n is an integer and F can be d (days), w (  weeks), m (months) or y (years). 
    e.g. if @freq(2m) the task will be done every two months.
    
    Note: If a task is completed before its due date, it will be put at the top of the file with    the unmodified due date for further
    manual processing.
    '''
    
    # Constant definition
    tpFile = sys.argv[1] # taskpaper file
    def WriteToTaskpaper(tskList,tskFile):
    
        with open('tmpFile', 'w') as tmpFile:
    
            print 'Writing to file...'
            for line in tskList:
                tmpFile.write(line)
    
        print 'Copying and removing temp file.'
        shutil.copy('tmpFile',tskFile)
        os.remove('tmpFile')
    
    def AddTask(newTask):
    
        '''
        Adds the newly formatted task to the global list 'pendingTaskList' which holds all the  pending
        tasks that will be written to the final Taskpaper file. The task is added after the item    with 
        the project name contained within the tag @project() in the task.
    
        If the Project name is 'None' or can't be found in the list of tasks, the task is added to
        the top of the lists.
        '''
    
        projectFlag = False #flag to be raised when the line where the project name is found
        index = 0
        projectPattern = '\@project\((.*?)\)'
        projectRegex = re.search(projectPattern, newTask)
    
        if projectRegex: pName = projectRegex.group(1)
        else: pName = 'None'
        print 'Project Name from Task ----> '+pName
    
        newTask = re.sub(projectPattern, '', newTask)
    
        for item in pendingTaskList:
            index += 1
            projectFound = re.search(pName, item)
    
            if projectFound: 
                projectFlag = True
                break
    
        if projectFlag == False or pName == 'None' : index = 0
    
        pendingTaskList.insert(index, newTask)
    
    
    def DateFromPattern(pattern, line):
        '''
        Returns a Date object based on the arguments, which are:
        1. Pattern to look for in the form of @tag(xdate). Only group 1 from the pattern will be    used.
        2. Line of text to look for the pattern 
        '''
    
        dateRegex = re.search(pattern, line)
        dateList = dateRegex.group(1).split('-')
        dateObj = date(int(dateList[0]), int(dateList[1]), int(dateList[2]))
        return dateObj
    
    def RescheduleTask(dueDt, freq):
        '''
        This function takes a date object and a frequency as arguments and returns the  rescheduled date
        object. If there is an error in the frequency formatting, it returns a string with the  error instead.
    
        Notes:
    
        - Frequencies are not case sensitive (e.g. d or D for day intervals can be used).
        - Time/date intervals should be entered as integers. e.g. '3d'
        - The function can also take negative frequencies as arguments and adjust the due date  accordingly (e.g. '-1y')
        '''
    
        dPattern = '(.+)[d|D]'
        dFreq = re.search(dPattern, freq)
    
        mPattern = '(.+)[m|M]'
        mFreq = re.search(mPattern, freq)
    
        yPattern = '(.+)[y|Y]'
        yFreq = re.search(yPattern, freq)
    
        wPattern = '(.+)[w|W]'
        wFreq = re.search(wPattern, freq)
    
        try:
            if dFreq:
                baseTime = timedelta(days=+1)
                newDt = dueDt + baseTime*int(dFreq.group(1))
    
            elif mFreq:
                baseTime = timedelta(days=+31)
                newDt = dueDt + baseTime*int(mFreq.group(1))
                newDt = newDt.replace(day = dueDt.day)
    
            elif yFreq:
                baseTime = timedelta(days=+365)
                newDt = dueDt + baseTime*int(yFreq.group(1))
                newDt = newDt.replace(day = dueDt.day)
    
            elif wFreq:
                baseTime = timedelta(weeks=+1)
                newDt = dueDt + baseTime*int(wFreq.group(1))
        except ValueError:
            print 'Alert: wrong frequency format.'
            newDt = 'Error in Frequency Provided'
    
        return newDt
    
    if __name__ == "__main__":
    
        duePattern = '@due\((.*?)\)'
        freqPattern = '@freq\((.*?)\)' 
        donePattern = '@done\((.*?)\)'
        projPattern = '^(.+?)\:$'
    
    
        doneTaskList = []
        pendingTaskList = []
        ProjectName = 'None'
    
    
        with open(tpFile, 'r') as infile:
            contents = infile.readlines()
    
        for line in contents:
    
            dueTag = re.search(duePattern, line)
            freqTag = re.search(freqPattern, line)
            doneTag = re.search(donePattern, line)
            projectFlag = re.search(projPattern, line)
    
            if projectFlag: ProjectName = projectFlag.group(1)
    
            if dueTag and freqTag and doneTag:
    
                line = line.strip('\r\n')
                doneTaskList.append(line+'@project('+ProjectName+')\n')
    
            else:
                pendingTaskList.append(line)
    
    
        for task in doneTaskList:
    
            doneDate = DateFromPattern(donePattern, task)
            dueDate = DateFromPattern(duePattern, task)
    
            freqPeriod = re.search(freqPattern, task).group(1) # Getting the recurrence interval    from the @freq tag. e.g: 4w
    
            if doneDate >= dueDate:
    
                newTask = re.sub(duePattern+'|'+donePattern, '', task) # Gets rid of the @done( XXXX-XX-XX) and @due(XXXX-XX-XX) tags.
                newTask = newTask.strip('\r\n')
                newDueDate = RescheduleTask(dueDate, freqPeriod)
    
                newTask = newTask+'@due('+newDueDate.isoformat()+')\n'
    
                print 'Old Task > '+task
                print 'New Task > '+newTask
    
                AddTask(newTask)
    
    
            else:
                print 'Task done before Due Date. Adding to the top of the list.'
                pendingTaskList.insert(0, task)
    
        WriteToTaskpaper(pendingTaskList, tpFile)
    

Sometimes I asked myself, was all that worth it?. After all, those lines of code only change this…

![Reschedule Before Image](https://farm8.staticflickr.com/7720/17358337942_9e5de75081_o.png)

> _Reschedule Before Image_

… Into this:

![Reschedule After Image](https://farm9.staticflickr.com/8773/17174045499_9a16bde414_o.png)

> _Reschedule After Image_

The answer is always the same: Yep, It was worth it.

Drop me a line if you have questions and feel free to improve my code in GitHub. After all, I'm pretty sure it looks like [this](http://imgs.xkcd.com/comics/code_quality.png) to real programmers.
