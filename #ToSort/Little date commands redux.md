# Little date commands redux

_Captured: 2016-04-26 at 13:25 from [leancrew.com](http://leancrew.com/all-this/2015/03/little-date-commands-redux/)_

[Back in December](http://www.leancrew.com/all-this/2014/12/two-little-date-commands/), I wrote a short utility called `ago`, which calculated the number of days between a date given on the command line and today. It's been useful, but too often I've found myself giving it input in the wrong format. Rather than retrain myself to match `ago`'s expectations, I rewrote `ago` to match mine.

As originally written, `ago` wanted two or three arguments: the month, day, and (optionally) year of the date. These were to be given as space-separated numbers, e.g.
    
    
    ago 8 30 14

to get the number of days since August 30, 2014, or
    
    
    ago 2 5

to get the number of days since February 5 of this year. The problem was the spaces. My natural inclination in writing a date is to use slashes or dashes between the numbers, e.g.
    
    
    ago 8/30/14

or
    
    
    ago 2-5

Using spaces was the lazy way out. Because Unix automatically parses arguments based on space separation, I didn't have to write a date parser in `ago`. But after a few months of use, I realized that the time I saved by not including a parser was eaten up by the time I spent rerunning `ago` after giving it the wrong input.

And I didn't even have to write a date parser. Although the Python standard library doesn't include the kind of forgiving parser that would allow both slashes and dashes as separators, the well-established `[dateutil` library](https://labix.org/python-dateutil) by Gustavo Niemeyer does. It also allows dot separators and text, like `feb 5`. Using it even shortened `ago`'s code. And the best news is that even though `dateutil` isn't in the standard library, it is included by default in OS X.

Here's the new version of `ago`:
    
    
     1  #!/usr/bin/env python
     2  
     3  from datetime import datetime
     4  from dateutil.parser import parse
     5  import sys
     6  
     7  # The date is given on the command line in American format.
     8  then = parse(sys.argv[1], dayfirst=False, yearfirst=False)
     9  now = datetime.today()
    10  
    11  ago = now - then
    12  
    13  if sys.argv[0].split('/')[-1] == 'til':
    14    print -ago.days
    15  else:
    16    print ago.days
    
    

The `parse` function in Line 8 returns a `[datetime` object](https://docs.python.org/2/library/datetime.html#datetime-objects), as does the `today` function in Line 9. The subtraction in Line 11 returns a `[timedelta` object](https://docs.python.org/2/library/datetime.html#timedelta-objects), from which we return the `days` attribute in Line 14 or 16.

Because the `ago` code can also count days until a future date, I made a hard link to `ago` called `til`.
    
    
    ln ago til

The logic of Lines 13-16 flips the sign of the result so I don't get negative numbers if I use `til` to inquire about a date in the future. Instead of using
    
    
    ago 12/25

and getting -284 as the result, I can use
    
    
    til 12/25

and get 284. Not a big deal, but a cute little affordance.

I should mention that the rules `parse` uses for two-digit years are a little different from what I used in the original version of `ago`. From the `dateutil` documentation:

> When a two digit year is found, it is processed considering the current year, so that the computed year is never more than 49 years after then current year, nor 50 years before the current year. In other words, if we are in year 2003, and the year 30 is found, it will be considered as 2030, but if the year 60 is found, it will be considered 1960.

Now that it's 2015, a year of 60 is considered 2060, not 1960.

With a rewritten `ago` under my belt, I decided to write a similar little utility that I've sometimes wished for: a quick way to get the difference in days between two dates. I call this script `between`. It's used as you might expect:
    
    
    between 8/23/1960 5/27

to get the number of days between August 23, 1960 and May 27 of this year. This is, as I mentioned in the post back in December, the day I become 20,000 days old. Jiminy.

The source code for `between` is
    
    
     1  #!/usr/bin/env python
     2  
     3  from dateutil.parser import parse
     4  import sys
     5  
     6  # The dates are given on the command line in American format.
     7  day1 = parse(sys.argv[1], dayfirst=False, yearfirst=False)
     8  day2 = parse(sys.argv[2], dayfirst=False, yearfirst=False)
     9  
    10  between = day2 - day1
    11  print between.days
    
    

There's nothing in `between` that isn't already in `ago`. I could, I suppose, modify `between` to act like `ago` when only one argument is given, but I think of the commands as distinctly different, so I don't mind the redundancy.

If the second argument is earlier than the first, `between` will return a negative number. I could've added some logic to always return a positive number, but I didn't see any value in that.

Back when Perl was my main language, I used its `[Date::Manip` module](http://search.cpan.org/~sbeck/Date-Manip-6.49/lib/Date/Manip.pod) for all kinds of date parsing and arithmetic. It was a huge module, and its load time was detectable--there was always a delay after issuing a command that used `Date::Manip`. But it was a remarkably full-featured library, and its parser was far more flexible and forgiving than `dateutil`'s. But `dateutil` is plenty good for what I need in these scripts and it doesn't hesitate before giving me the answer.
