# Simpler syndication

_Captured: 2015-11-28 at 19:58 from [leancrew.com](http://leancrew.com/all-this/2015/11/simpler-syndication/)_

Once upon a time, reading the various site feeds I was subscribed to was simple. I just went to my account on [Bloglines](https://en.wikipedia.org/wiki/Bloglines) and read. Bloglines kept itself up to date, and because it was a web site I never had to worry about syncing--whatever computer I accessed it from, it knew which articles I'd already read and showed me only the newer ones.

At some point, I switched to [Google Reader](https://en.wikipedia.org/wiki/Google_Reader), also web-based and with the power of the almighty Google behind it. I stuck with Bloglines longer than most people did--I preferred Bloglines' layout--but eventually moved [because I had an iPhone](http://www.leancrew.com/all-this/2013/03/the-iphone-and-google-reader-hegemony/) and wanted to read my subscriptions on it.

Then came the Google Reader Apocalypse of 2013. Not only was the Reader web site shutting down, but so was its server backend, whose unofficial API had been powering just about every feed aggregator around. This took everyone by surprise.

New RSS sync services popped up to fill the vacuum left in Reader's absence, and in the last 2½ years we've been treated to an RSS smorgasbord. I've used the free trials of several of them and paid for the services of a couple, but none have been as good as that evil old Google. In particular, they tend to lag in serving new articles and in updating their feeds when an article has been revised. Google Reader was always astonishingly fast at both of those.

My subscription to my current RSS service is running out in a month or so, and as I considered which provider I wanted to use for the next year, I began to wonder if I'd be satisfied with any of them. How hard would it be for me to make my own service that always serves updated versions of the most recent articles on the sites I subscribe to? After all, RSS is a distributed protocol. Just because we've all gotten used to accessing it through centralized services, that doesn't mean we have to.

So I wrote a short script that goes through my subscriptions, plucks out the articles published (or updated) today, and creates a simple web page with all of them displayed in reverse chronological order. It looks like this on my iPhone

![Today’s RSS on iPhone](http://leancrew.com/all-this/images2015/20151125-Todays%20RSS%20on%20iPhone.png)

> _and like this on my MacBook Air_

![Today's RSS on computer](http://leancrew.com/all-this/images2015/20151125-Todays%20RSS%20on%20computer.png)

> _Today's RSS on computer_

The display is basic and deliberately so. This is more of an experiment than a finished product, and I didn't want to waste time on frosting if it turns out that the cake is no good. I've been using it for a week and have been pretty happy with it, but that doesn't mean I'll stick with it.

The script (which we'll get to in a bit) runs every 10 minutes and puts a new version of the page on my server, so the web address remains the same but the content is updated continually throughout the day. I decided against trying to implement syncing because

  1. Syncing would involve much more work than I wanted to do for something that may be abandoned in a few weeks.
  2. The reverse chronological order of the articles has something like the effect of syncing; as with the blogs themselves, I know to stop when I get down to posts I've already read.

Here's the script itself, called `dayfeed`:
    
    
      1  #!/usr/bin/env python
      2  # coding=utf8
      3  
      4  import feedparser as fp
      5  import time
      6  from datetime import datetime, timedelta
      7  import pytz
      8  
      9  subscriptions = [
     10    'http://feedpress.me/512pixels',
     11    'http://www.leancrew.com/all-this/feed/',
     12    'http://ihnatko.com/feed/',
     13    'http://blog.ashleynh.me/feed',
     14    'http://www.betalogue.com/feed/',
     15    'http://bitsplitting.org/feed/',
     16    'http://feedpress.me/jxpx777',
     17    'http://kieranhealy.org/blog/index.xml',
     18    'http://blueplaid.net/news?format=rss',
     19    'http://brett.trpstra.net/brettterpstra',
     20    'http://feeds.feedburner.com/NerdGap',
     21    'http://www.libertypages.com/clarktech/?feed=rss2',
     22    'http://feeds.feedburner.com/CommonplaceCartography',
     23    'http://kk.org/cooltools/feed',
     24    'http://danstan.com/blog/imHotep/files/page0.xml',
     25    'http://daringfireball.net/feeds/main',
     26    'http://david-smith.org/atom.xml',
     27    'http://feeds.feedburner.com/drbunsenblog',
     28    'http://stratechery.com/feed/',
     29    'http://www.gnuplotting.org/feed/',
     30    'http://feeds.feedburner.com/jblanton',
     31    'http://feeds.feedburner.com/IgnoreTheCode',
     32    'http://indiestack.com/feed/',
     33    'http://feedpress.me/inessential',
     34    'http://feeds.feedburner.com/JamesFallows',
     35    'http://feeds.feedburner.com/theendeavour',
     36    'http://feed.katiefloyd.me/',
     37    'http://feeds.feedburner.com/KevinDrum',
     38    'http://www.kungfugrippe.com/rss',
     39    'http://lancemannion.typepad.com/lance_mannion/rss.xml',
     40    'http://www.caseyliss.com/rss',
     41    'http://www.macdrifter.com/feeds/all.atom.xml',
     42    'http://mackenab.com/feed',
     43    'http://hints.macworld.com/backend/osxhints.rss',
     44    'http://macsparky.com/blog?format=rss',
     45    'http://www.macstories.net/feed/',
     46    'http://www.marco.org/rss',
     47    'http://merrillmarkoe.com/feed',
     48    'http://mjtsai.com/blog/feed/',
     49    'http://feeds.feedburner.com/mygeekdaddy',
     50    'http://nathangrigg.net/feed.rss',
     51    'http://onethingwell.org/rss',
     52    'http://schmeiser.typepad.com/penny_wiseacre/rss.xml',
     53    'http://feeds.feedburner.com/PracticallyEfficient',
     54    'http://robjwells.com/rss',
     55    'http://www.red-sweater.com/blog/feed/',
     56    'http://feedpress.me/sixcolors',
     57    'http://feedpress.me/candlerblog',
     58    'http://inversesquare.wordpress.com/feed/',
     59    'http://themindfulbit.com/feed',
     60    'http://joe-steel.com/feed',
     61    'http://feeds.veritrope.com/',
     62    'http://xkcd.com/atom.xml',
     63    'http://doingthatwrong.com/?format=rss']
     64  
     65  # Date and time setup. I want only posts from "today," 
     66  # where the day lasts until 2 AM.
     67  utc = pytz.utc
     68  homeTZ = pytz.timezone('US/Central')
     69  dt = datetime.now(homeTZ)
     70  if dt.hour < 2:
     71    dt = dt - timedelta(hours=24)
     72  start = dt.replace(hour=0, minute=0, second=0, microsecond=0)
     73  start = start.astimezone(utc)
     74  
     75  # Collect all of today's posts and put them in a list of tuples.
     76  posts = []
     77  for s in subscriptions:
     78    f = fp.parse(s)
     79    try:
     80      blog = f['feed']['title']
     81    except KeyError:
     82      continue
     83    for e in f['entries']:
     84      try:
     85        when = e['updated_parsed']
     86      except KeyError:
     87        when = e['published_parsed']
     88      when =  utc.localize(datetime.fromtimestamp(time.mktime(when)))
     89      if when > start:
     90        title = e['title']
     91        try:
     92          body = e['content'][0]['value']
     93        except KeyError:
     94          body = e['summary']
     95        link = e['link']
     96        posts.append((when, blog, title, link, body))
     97  
     98  # Sort the posts in reverse chronological order.
     99  posts.sort()
    100  posts.reverse()
    101  
    102  # Turn them into an HTML list.
    103  listTemplate = '''<li>
    104    <p class="title"><a href="{3}">{2}</a></p>
    105    <p class="info">{1}<br />{0}</p>
    106    <p>{4}</p>\n</li>'''
    107  litems = []
    108  for p in posts:
    109    q = [ x.encode('utf8') for x in p[1:] ]
    110    timestamp = p[0].astimezone(homeTZ)
    111    q.insert(0, timestamp.strftime('%b %d, %Y %I:%M %p'))
    112    litems.append(listTemplate.format(*q))
    113  ul = '\n<hr />\n'.join(litems)
    114  
    115  # Print the HTMl.
    116  print '''<html>
    117  <meta charset="UTF-8" />
    118  <meta name="viewport" content="width=device-width" />
    119  <head>
    120  <style>
    121  body {{
    122    background-color: #444;
    123    width: 750px;
    124    margin-top: 0;
    125    margin-left: auto;
    126    margin-right: auto;
    127    padding-top: 0;
    128  }}
    129  h1 {{
    130    font-family: Helvetica, Sans-serif;
    131  }}
    132  .rss {{
    133    list-style-type: none;
    134    margin: 0;
    135    padding: .5em 1em 1em 1.5em;
    136    background-color: white;
    137  }}
    138  .rss li {{
    139    margin-left: -.5em;
    140    line-height: 1.4;
    141  }}
    142  .rss li pre {{
    143    overflow: auto;
    144  }}
    145  .title {{
    146    font-weight: bold;
    147    font-family: Helvetica, Sans-serif;
    148    font-size: 110%;
    149    margin-bottom: .25em;
    150  }}
    151  .title a {{
    152    text-decoration: none;
    153    color: black;
    154  }}
    155  .info {{
    156    font-size: 85%;
    157    margin-top: 0;
    158    margin-left: .5em;
    159  }}
    160  img {{
    161    max-width: 700px;
    162  }}
    163  @media screen and (max-width:667px) {{
    164    body {{
    165      font-size: 200%;
    166      width: 650px;
    167      background-color: white;
    168    }}
    169    .rss {{
    170      padding-right: 0;
    171    }}
    172    .rss li {{
    173      line-height: normal;
    174    }}
    175    img {{
    176      max-width: 620px;
    177    }}
    178  }}
    179  </style>
    180  <title>Today’s RSS</title>
    181  <body>
    182  <ul class="rss">
    183  {}
    184  </ul>
    185  </body>
    186  </html>
    187  '''.format(ul)
    
    

OK, it's 187 lines, but most of that is the list of feeds, Lines 9-63, and the HTML/CSS template for the page, Lines 116-187\. That leaves only 60 lines for the working part of the code.

Two nonstandard modules are imported, `[feedparser`](https://pypi.python.org/pypi/feedparser) for downloading and parsing the feeds, and `[pytz`](https://pypi.python.org/pypi/pytz/) for manipulating time zone info.

As the purpose of the script is to display all of today's articles, I need to define what "today" is. That's the purpose of Lines 67-73\. First, since I live in the Chicago area, my day isn't aligned with the UTC day that RSS feeds using for timestamps. Lines 67 and 68 define these two timezones so feed times can be converted to my time. And since it's common for me to be awake and browsing my subscriptions after midnight, I decided to make "today" run from midnight to 2 AM of the following day. Lines 69-72 work out the beginning of "today" in my time zone; Line 73 converts it to UTC and puts it in the variable `start`.

Lines 76-96 is the meat of the script. It loops through the subscription list, parses the feeds, filters out those that were published or updated before `start`, and puts a tuple of the date, blog name, title, URL, and content of each of today's posts into a new list called `posts`. There's some jiggering around with `try` blocks because

  1. Some feeds supply an `updated_parsed` date field while others supply only a `published_parsed` field.
  2. Some feeds supply a `content` field, while other supply only a `summary` field.

Luckily, the feeds of the sites I subscribe to are fairly regular. If I were foolish enough to try to write a general purpose feed reader, the number of variations and special cases would probably make this section of the script much longer and drive me crazy.

Because I put the date field at the beginning of each tuple (Line 96), sorting the `posts` list in reverse chronological order is simple: Lines 99 and 100 do the trick.

Lines 103-113 then creates an `<li>` element for each item in `posts` and joins them together with a horizontal rule between them. The various subparts of each list item are assigned classes for styling via CSS.

Finally, Lines 116-187 print out a self-contained HTML/CSS file. I'm sure my CSS is amateurish, but it works. I'll improve it if I decide this really is the way I want to read my subscriptions.

This script gets run every 10 minutes between 6 AM and 2 AM via a `[cron`](http://man7.org/linux/man-pages/man8/cron.8.html) job, creating an HTML file each time that overwrites the previous version. Because the script can take up to a minute to run (depending on the responsiveness of the various servers it calls), a simple command line call of
    
    
    dayfeed > todaysrss.html

won't do, because the probability I'd be requesting the file while the command is running (and would end up with an empty HTML file) could be as much as 10%. Instead, I have `cron` set up to run a two-line shell script:
    
    
    dayfeed > temprss.html
    mv temprss.html todaysrss.html

With this setup, `todaysrss.html` is, for all practical purposes, never empty. I suppose I could run into trouble if I request it during the `mv`, but that command is so fast I'm willing to take my chances.

My first week of use has been encouraging, but it's entirely possible that I'll find something I hate about it and will go sign up for Feedly or Feedbin. I like the do-it-yourself aspect of this setup--and I think it's more in line with Dave Winer's conception of RSS--but I won't cling to it if it doesn't work well over the long haul.

This work is licensed under a [Creative Commons Attribution-Share Alike 3.0 Unported License](http://creativecommons.org/licenses/by-sa/3.0/).
