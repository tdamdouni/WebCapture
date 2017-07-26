# Tasks Graph With Pandas

_Captured: 2016-03-29 at 13:30 from [www.movingelectrons.net](http://www.movingelectrons.net/blog/2016/01/01/tasks-graph-with-pandas.html)_

I have been using the [Taskpaper format](http://imissmymac.com/wp-content/uploads/2013/02/TaskPaper-Users-Guide.pdf) for both task and project management for a while now. Its deceiving simplicity is its greatest strength. You might think it's just text lines with task descriptions and _tags_, but that's exactly what makes it tremendously malleable. You can use it for either simple task lists or for building yourself a nerdy workflow involving automatically run Python scripts that rearrange and sort your project tasks. Paired with the wonderful [Editorial](https://itunes.apple.com/us/app/editorial/id673907758?mt=8&uo=4&at=11lqkH) text editor on iOS and [Dropbox](https://itunes.apple.com/us/app/editorial/id673907758?mt=8&uo=4&at=11lqkH), makes up a sturdy and reliable mobile project management system.

## The Problem I'm Trying to Solve

I wrote a couple of posts in the past on productivity, task management and Taskpaper ([here](http://bit.ly/1GzWBNe) and [here](http://bit.ly/1InsFr3)). Although this system was working perfectly fine for me, I was missing the _mid-term view_. Something that would tell me what my next week or two weeks would look like. I wasn't interested on detailed task description, just amount of tasks per day, so that I can organize my workload accordingly.

## The Solution

I knew the best way to have a mid-to-long term view would be through a graphical representation of the upcoming tasks. After some researching on tools that could accomplish this, I decided the best way to do it would be through a Python script. There are several libraries out these that can be used, but I decided to use a combination of [Pandas](http://pandas.pydata.org/) and [Seaborn](http://stanford.edu/~mwaskom/software/seaborn/). They are overkill for this small project, but I wanted to learn how to use them as I might be working with them in the near future. These libraries along with many others aimed at data analysis are bundled together in a nice and easy to install Python distribution called [Anaconda](https://www.continuum.io/why-anaconda), put together by [Continuum Analytics](https://www.continuum.io/). They have done an outstanding job including key libraries and all associated dependencies in one single bundle which is ready to install on pretty much any platform.

## The Script

Find below the script I use. I also uploaded it [here](https://gist.github.com/Moving-Electrons/eb55d919d5f56dc37c7a), in case you want to grab it and play with it. I have commented several lines to make it as readable as possible. I also included several `print`statements so you can see what's happening in the console as the script runs.
    
    
    import sys
    import re
    import datetime as dt
    from collections import Counter
    import pandas as pd
    import seaborn as sns
    
    '''
    This script takes the following arguments and returns a graph 
    showing the number of tasks due per day.
    
    1. Taskpaper filename
    2. Output image filename
    
    It doesn't account for overdue tasks. The number of days to be 
    presented in the graph can be defined in the header of the script.
    '''
    
    # Contants definition
    FILE = sys.argv[1] # .taskpaper file
    OUTPUT = sys.argv[2] 
    NUMBER_OF_DAYS = 20
    
    def Due_Dates_Dict(tasks):
        '''
        Takes the contents of a taskpaper file (passed as a list argument) 
        and returns a Dictionary with Due Dates (keys) and number of times 
        they repeat (values)
        '''
    
        today_date = dt.date.today()
        today_str = today_date.strftime("%Y-%m-%d")
    
    
        duePattern = '@due\((.*?)\)'
        donePattern = '@done\((.*?)\)'
        todayPattern = '.*(@today).*'
        DatesList = []
    
        for line in tasks:
    
            dueTag = re.search(duePattern, line)
            doneTag = re.search(donePattern, line)
            todayTag = re.search(todayPattern, line)
    
    
            if dueTag and not doneTag:
                DatesList.append(dueTag.group(1))
    
            if todayTag and not doneTag:
                DatesList.append(today_str)
    
    
        datesDict = Counter(DatesList)
        return datesDict
    
    
    if __name__ == "__main__":
    
        with open(FILE, 'r') as infile:
            contents = infile.readlines()
    
        dates = Due_Dates_Dict(contents)
        print "Dates List Created"
    
        today_date = dt.date.today()
        today_str = today_date.strftime("%Y-%m-%d")
    
        later_date = dt.date.today() + dt.timedelta(days=NUMBER_OF_DAYS)
        later_str = later_date.strftime("%Y-%m-%d")
        print "Initial Date: "+today_str+"\nEnd Date: "+later_str
    
        # Defining dataframe index as a Datetime object
        print 'Dates Parsed:', dates.keys()
    
        df_index = pd.to_datetime(dates.keys(), format='%Y-%m-%d')
    
        main_df = pd.DataFrame(dates.values(), columns = ['tasks'], index = df_index).sort(ascending=True)
    
        # Getting rid of overdue items and just including upcoming tasks:
        reduced_df = main_df[(main_df.index >= today_str) & (main_df.index < later_str)]
    
    
        # Defining new index to include all days from today to the final date sample.
        # If we don't do this, dates with 0 tasks assigned will not show up
        # in the graph.
        allDates_index = pd.date_range(start=today_str, periods=NUMBER_OF_DAYS, freq='D')
    
        reduced_df_allDays = reduced_df.reindex(index=allDates_index, fill_value=0)
    
        # Transforming the dataframe index (DatetimeIndex object) to a 
        # regular pd.Series so "apply" can be used.
        # The Pandas "apply" method is used in this case to apply an "anonymous" 
        # function (one we don't want to create a separate function for) to all 
        # the components of the DataFrame/Series
    
    
        weekday_series = pd.Series(reduced_df_allDays.index, index = reduced_df_allDays.index).apply(lambda x: x.strftime('%a'))
    
        # Adding another column with string objects representing weekdays.
        reduced_df_allDays['weekday'] = weekday_series
    
        # Setting a pre-defined style from Seaborn
        sns.set_context('notebook')
        # Pandas plotting
        line_plot = reduced_df_allDays.plot(legend=False, title='Tasks Distribution - Next '+str(NUMBER_OF_DAYS)+' Days', 
                                            y=['tasks'], kind='line')
        print "Generating Graph.."
        fig = line_plot.get_figure()
        fig.savefig(OUTPUT)
        print "Done."
    

As indicated above, the script takes two arguments: the Taskpaper file and the output file name. So, it's very easy to have it run for multiple task files. I personally have several bash scripts set up to do just that and then run them though a _launcher_ application like [Alfred](https://itunes.apple.com/us/app/alfred/id405843582?mt=12&uo=4&at=11lqkH) on Mac OS or [Launchy](http://www.launchy.net/) on Windows.

## The Final Product

Here is an example of the generated graph. I might revise the script to make the output look like a _heat map_ like the ones shown [here](https://stanford.edu/~mwaskom/software/seaborn/generated/seaborn.heatmap.html), I just need to find the time to do it. For now, it does exactly what I need.

![Script Output](http://www.movingelectrons.net/images/Tasks_Graph_With_Pandas_graph.png)

> _Feel free to post any questions or comments you may have below._
