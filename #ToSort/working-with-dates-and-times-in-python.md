# Working With Dates and Times in Python

_Captured: 2017-06-20 at 19:40 from [dzone.com](https://dzone.com/articles/python-101-working-with-dates-and-time?edition=305104&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-19)_

Find your next Big Data job at [DZone Jobs](https://dzone.com/go?i=219248&u=https%3A%2F%2Fjobs.dzone.com%2Fjobs%2Fsearch%3Futf8%3D%2525E2%25259C%252593%26q%3DBig%2BData). See [jobs focused on Big Data](https://dzone.com/go?i=219248&u=https%3A%2F%2Fjobs.dzone.com%2Fjobs%2Fsearch%3Futf8%3D%2525E2%25259C%252593%26q%3DBig%2BData) or [create your profile](https://dzone.com/go?i=219248&u=https%3A%2F%2Fjobs.dzone.com%2Fprofiles%2Fsign_up) and have the employers come to you!

Python gives the developer several tools for working with dates and time. In this article, we will be looking at the `datetime` and `time` modules. We will study how they work and some common uses for them. Let's start with the `datetime` module!

## The datetime Module

We will be learning about the following classes from the `datetime` module:

  * `datetime.data`
  * `datetime.timedelta`
  * `datetime.datetime`  


These will cover the majority of instances where you'll need to use `date` and `datetime` object in Python. There is also a `tzinfo` class for working with time zones that we won't be covering. Feel free to take a look at the Python documentation for more information on that class.

### datetime.date

Python can represent dates several different ways. We're going to look at the `datetime.date` format first as it happens to be one of the simpler date objects.
    
    
      File "<string>", line 1, in <fragment>

This code shows how to create a simple `date` object. The date class accepts three arguments: the year, the month and the day. If you pass it an invalid value, you will see a `ValueError`, like the one above. Otherwise, you will see a `datetime.date` object returned. Let's take a look at another example:

Here we assign the date object to the variable `d`. Now we can access the various date components by name, such as `d.year` or `d.month` . Now let's find out what day it is:

This can be helpful whenever you need to record what day it is. Or perhaps you need to do a date-based calculation based on today. It's a handy little convenience method though.

### datetime.datetime

A `datetime.datetime` object contains all the information from a `datetime.date` plus a `datetime.time` object. Let's create a couple of examples so we can better understand the difference between this object and the `datetime.date` object.
    
    
    >>> datetime.datetime(2014, 3, 5, 12, 30, 10)
    
    
    datetime.datetime(2014, 3, 5, 12, 30, 10)
    
    
    >>> d = datetime.datetime(2014, 3, 5, 12, 30, 10)

Here we can see that `datetime.datetime` accepts several additional arguments: year, month, day, hour, minute and second. It also allows you to specify microsecond and timezone information too. When you work with databases, you will find yourself using these types of objects a lot. Most of the time, you will need to convert from the Python date or `datetime` format to the SQL `datetime` or `timestamp` format. You can find out what today is with `datetime.datetime` using two different methods:
    
    
    datetime.datetime(2014, 3, 5, 17, 56, 10, 737000)
    
    
    >>> datetime.datetime.now()
    
    
    datetime.datetime(2014, 3, 5, 17, 56, 15, 418000)

The `datetime` module has another method that you should be aware of called `strftime`. This method allows the developer to create a string that represents the time in a more human readable format. There's an entire table of formatting options that you should go read in the Python documentation, section 8.1.7. We're going to look at a couple of examples to show you the power of this method:
    
    
    >>> datetime.datetime.today().strftime("%Y%m%d")
    
    
    >>> today = datetime.datetime.today()
    
    
    >>> today.strftime("%m/%d/%Y")
    
    
    >>> today.strftime("%Y-%m-%d-%H.%M.%S")

The first example is kind of a hack. It shows how to convert today's `datetime` object into a string that follows the _YYYYMMDD_ (year, month, day) format. The second example is better. Here we assign today's `datetime` object to a variable called `today` and then try out two different string formatting operations. The first one adds forward slashes between the `datetime` elements and also rearranges it so that it becomes _month, day, year_. The last example creates a timestamp of sorts that follows a fairly typical format: _YYYY-MM-DD.HH.MM.SS_. If you want to go to a two-digit year, you can swap out the `%Y` for `%y` .

### datetime.timedelta

The `datetime.timedelta` object represents a time duration. In other words, it is the difference between two dates or times. Let's take a look at a simple example:
    
    
    >>> now = datetime.datetime.now()
    
    
    datetime.datetime(2014, 3, 5, 18, 13, 51, 230000)
    
    
    >>> then = datetime.datetime(2014, 2, 26)

We create two `datetime` objects here. One for today and one for a week ago. Then we take the difference between them. This returns a `timedelta` object which we can then use to find out the number of days or seconds between the two dates. If you need to know the number of hours or minutes between the two, you'll have to use some math to figure it out. Here's one way to do it:
    
    
    >>> seconds = delta.total_seconds()

What this tells us is that there are 186 hours and 13 minutes in a week. Note that we are using a double forward slash as our division operator. This is known as floor division.

Now we're ready to move on and learn a bit about the `time` module!

## The time Module

The `time` module provides the Python developer access to various time-related functions. The time module is based on what it known as an epoch, the point when time starts. For Unix systems, the epoch was in 1970. To find out what the epoch is on your system, try running the following:
    
    
    time.struct_time(tm_year=1970, tm_mon=1, tm_mday=1, tm_hour=0, tm_min=0, 
    
    
                     tm_sec=0, tm_wday=3, tm_yday=1, tm_isdst=0)

I ran this on Windows 7 and it too seems to think that time began in 1970. Anyway, in this section, we will be studying the following time-related functions:

  * `time.ctime`
  * `time.sleep`
  * `time.strftime`
  * `time.time`

Let's get started!

### time.ctime

The `time.ctime` function will convert a time in seconds since the epoch to a string representing local time. If you don't pass it anything, then the current time is returned. Let's try out a couple of examples:

Here, we show the results of calling `ctime` with nothing at all and with a fairly random number of seconds since the epoch. I have seen sort of thing used when someone saves the date as seconds since the epoch and then they want to convert it to something a human can understand. It's a bit simpler to save a big integer (or long) to a database then to mess with formatting it from a `datetime` object to whatever date object the database accepts. Of course, that also has the drawback that you do need to convert the integer or float value back into a string.

### time.sleep

The `time.sleep` function gives the developer the ability to suspend execution of your script a given number of seconds. It's like adding a pause to your program. I have found this personally useful when I need to wait a second for a file to finish closing or a database commit to finish committing. Let's take a look at an example. Open a new window in IDLE and save the following code:

Now run the code in IDLE. You can do that by going to the **Run** menu and then choose the **_Run module_** menu item. When you do so, you will see it print out the phrase *Slept for 2 seconds* five times with a two-second pause between each print. It's really that easy to use!

### time.strftime

The `time` module has a `strftime` function that works in pretty much the same manner as the `datetime` version. The difference is mainly in what it accepts for input: a tuple or a `struct_time` object, like those that are returned when you call `time.gmtime()` or `time.localtime()`. Here's a little example:

This code is quite similar to the timestamp code we created in the `datetime` portion of this chapter. I think the `datetime` method is a little more intuitive in that you just create a `datetime.datatime` object and then call its `strftime` method with the format you want. With the time module, you have to pass the format plus a time tuple. It's really up to you to decide which one makes the most sense to you.

### time.time

The `time.time` function will return the time in seconds since the epoch as a floating point number. Let's take a look:

That was pretty simple. You could use this when you want to save the current time to a database but you didn't want to bother converting it to the database's `datetime` method. You might also recall that the `ctime` method accepts the time in seconds, so we could use `time.time` to get the number of seconds to pass to `ctime`, like this:

If you do some digging in the documentation for the time module or if you just experiment with it a bit, you will likely find a few other uses for this function.

## Wrapping Up

At this point, you should know how to work with dates and time using Python's standard modules. Python gives you a lot of power when it comes to working with dates. You will find these modules helpful if you ever need to create an application that keeps track of appointments or that needs to run on particular days. They are also useful when working with databases.

Find your next Big Data job at [DZone Jobs](https://dzone.com/go?i=219249&u=https%3A%2F%2Fjobs.dzone.com%2Fjobs%2Fsearch%3Futf8%3D%2525E2%25259C%252593%26q%3DBig%2BData). See [jobs focused on Big Data](https://dzone.com/go?i=219249&u=https%3A%2F%2Fjobs.dzone.com%2Fjobs%2Fsearch%3Futf8%3D%2525E2%25259C%252593%26q%3DBig%2BData) or [create your profile](https://dzone.com/go?i=219249&u=https%3A%2F%2Fjobs.dzone.com%2Fprofiles%2Fsign_up) and have the employers come to you!
