# Python – The datefinder package

_Captured: 2016-02-19 at 12:37 from [www.blog.pythonlibrary.org](http://www.blog.pythonlibrary.org/2016/02/04/python-the-datefinder-package/)_

Earlier this week, I came across another fun package called [datefinder](https://github.com/akoumjian/datefinder). The idea behind this package is that it can take any string with dates in it and transform them into a list of Python datetime objects. I would have loved this package at my old job where I did a lot of text file and database query parsing as there were many a time when finding the date and getting it into a format I could easily use was quite the nuisance.

Anyway, to install this handy package all you need to do is this:

`pip install datefinder`

I should note that when I ran this, it ended up also installing the following packages:

  * PyYAML-3.11 
  * dateparser-0.3.2
  * jdatetime-1.7.2
  * python-dateutil-2.4.2
  * pytz-2015.7
  * regex-2016.1.10
  * six-1.10.0
  * umalqurra-0.2

Because of all this extra stuff, you might want to install this package into a virtualenv first. Let's take a look at some code. Here's a quick demo I tried:
    
    
    >>> import datefinder
    >>> data = '''Your appointment is on July 14th, 2016. Your bill is due 05/05/2016'''
    >>> matches = datefinder.find_dates(data)
    >>> for match in matches:
    ... 	print(match)
    ... 
    2016-07-14 00:00:00
    2016-05-05 00:00:00

As you can see, it worked quite well with these two common date formats. Another format that I used to have to support was the fairly typical [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date format. Let's see how datefinder behaves with that.
    
    
    >>> data = 'Your report is due: 2016-02-04T20:16:26+00:00'
    >>> matches = datefinder.find_dates(x)
    >>> for i in matches: 
    ...     print(i)
    ... 
    2016-02-04 00:00:00
    2016-02-04 20:16:26

Interestingly, this particular version of the ISO 8601 format causes datefinder to return two matches. The first is just the date while the second has both the date and the time. Anyway, hopefully you'll find this package useful in your projects. Have fun!

  


This week we welcome Chris Withers as our PyDev of the Week! Chris has been using Python for quite a while. I think the first packages I used of his were the excellent xlrd and xlwt packages, used for reading and writing Excel files. You can get an idea of his contributions to Python on his [github profile](https://github.com/cjw296). Let's take some time and get to know him better.

**Can you tell us a little about yourself (hobbies, education, etc):**

_I grew up in Zimbabwe and now like in the UK, but have ended up with two passports, both for countries I've never lived in._  
_  
When I'm not coding, I'm either umpiring for field hockey matches or doing things with dance music._
