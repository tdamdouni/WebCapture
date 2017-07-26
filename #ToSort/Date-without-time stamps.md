# Date-without-time stamps

_Captured: 2016-05-28 at 16:08 from [leancrew.com](http://leancrew.com/all-this/2016/05/date-without-time-stamps/)_

A while ago, I lost Eddie Smith's [Practically Efficient](http://www.practicallyefficient.com) blog from [my homemade RSS aggregator](http://leancrew.com/all-this/2015/12/homemade-rss-aggregator-followup/). At first, I thought it was because his feed URL had changed when [he switched from Squarespace to Jekyll](http://www.practicallyefficient.com/2016/04/03/static-and-free.html), but today I learned it was because of a more subtle change: the datestamps on his feed's new entries didn't include the time, and my aggregator was misinterpreting that and filtering them out. I've rewritten the datestamp filtering portion of the aggregator to fix this problem, which not only brought back not only Eddie's feed but also [XKCD's](http://xkcd.com/).

It's not that I stopped reading Practically Efficient during these past several weeks. Eddie always tweets a link to his latest post, so I was keeping up via Twitter, like all the cool kids do nowadays. But I really wanted him back in my RSS aggregator, so today I decided to dig in and find out what was keeping him out.

It wasn't, as I hinted above, because he'd changed his feed URL. I checked, and it's the same as it's been for years. So I used `[curl`](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/curl.1.html) to look at his feed directly:
    
    
    curl http://www.practicallyefficient.com/feed.xml

His feed includes entries for the last ten posts. The entry for today's post looks like this:
    
    
    <item>
      <title>Fear more</title>
      <description>&lt;p&gt;Focusing your time on a narrower set of priorities is the biggest gut check you can experience in business and life. It is a never-ending fight with your primal self. Feature bloat, mass marketing, and “do it all” are driven by fear, and the internet age enables that fear like no other medium devised by humanity.&lt;/p&gt;
    
    &lt;p&gt;Before you decide to spend time making &lt;em&gt;more&lt;/em&gt; instead of making something &lt;em&gt;better&lt;/em&gt;, ask yourself: what am I afraid of?&lt;/p&gt;
    
    </description>
      <pubDate>Wed, 11 May 2016 00:00:00 +0000</pubDate>
      <link>http://www.practicallyefficient.com/2016/05/11/fear-more.html</link>
      <guid isPermaLink="true">http://www.practicallyefficient.com/2016/05/11/fear-more.html</guid>
    
    
    </item>

The key to his disappearance from my aggregator is the `<pubDate>`, the contents of which are
    
    
    Wed, 11 May 2016 00:00:00 +0000

Did Eddie really post his article at midnight UTC? No, he posted it sometime on the 11th, and Jekyll (or maybe some other part of his publishing system) set the `pubDate` to the correct date but somehow defaulted to midnight for the time portion. If you look through all ten entries in Eddie's feed, you'll see that all of them have a time entry of
    
    
    00:00:00 +0000

This time stamp is why my aggregator was filtering out his posts. As I said in [my initial article](http://leancrew.com/all-this/2015/11/simpler-syndication/) about the aggregator script, it runs periodically on my server to create an HTML file with "today's" posts from the sites I subscribe to. To avoid missing articles published late in the evening, I define "today" as anytime after 10:00 pm US Central Time on the previous day. So whenever the script runs on May 11, it creates a page with every post published after 10:00 pm Central Time on May 10. Eddie's post for May 11 has a timestamp of midnight UTC, which in Central Time is 7:00 pm of May 10, so the script saw it as an older post and filtered it out. And that's what's been happening to every one of Eddie's posts for several weeks.

What to do? I could ask Eddie to change his publishing system to accommodate my aggregator, but that seems presumptuous. Better to rewrite the aggregator to handle this case, especially since his isn't the only feed that defaults to midnight UTC timestamps. XKCD does the same thing, and I'm sure there are others.

So here's the new aggregator script:
    
    
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
     34    'http://feeds.feedburner.com/theendeavour',
     35    'http://feed.katiefloyd.me/',
     36    'http://feeds.feedburner.com/KevinDrum',
     37    'http://www.kungfugrippe.com/rss',
     38    'http://lancemannion.typepad.com/lance_mannion/rss.xml',
     39    'http://www.caseyliss.com/rss',
     40    'http://www.macdrifter.com/feeds/all.atom.xml',
     41    'http://mackenab.com/feed',
     42    'http://hints.macworld.com/backend/osxhints.rss',
     43    'http://macsparky.com/blog?format=rss',
     44    'http://www.macstories.net/feed/',
     45    'http://www.marco.org/rss',
     46    'http://merrillmarkoe.com/feed',
     47    'http://mjtsai.com/blog/feed/',
     48    'http://feeds.feedburner.com/mygeekdaddy',
     49    'http://nathangrigg.net/feed.rss',
     50    'http://onethingwell.org/rss',
     51    'http://schmeiser.typepad.com/penny_wiseacre/rss.xml',
     52    'http://www.practicallyefficient.com/feed.xml',
     53    'http://robjwells.com/rss',
     54    'http://www.red-sweater.com/blog/feed/',
     55    'http://blog.rtwilson.com/feed/',
     56    'http://feedpress.me/sixcolors',
     57    'http://feedpress.me/candlerblog',
     58    'http://inversesquare.wordpress.com/feed/',
     59    'http://high90.com/feed',
     60    'http://joe-steel.com/feed',
     61    'http://feeds.veritrope.com/',
     62    'http://xkcd.com/atom.xml',
     63    'http://doingthatwrong.com/?format=rss']
     64  
     65  # Date and time setup. I want only posts from today,
     66  # where "today" starts at 10 PM of the previous day and
     67  # lasts until 2 AM of the following day.
     68  # Exception: if the entry's date is today with a timestamp
     69  # of exactly midnight (00:00:00), include that, too, even
     70  # if its timezone is UTC, as that probably represents a
     71  # datestamp of today without a real timestamp.
     72  utc = pytz.utc
     73  homeTZ = pytz.timezone('US/Central')
     74  mnToday = datetime.today().replace(hour=0, minute=0, second=0, microsecond=0)
     75  dt = datetime.now(homeTZ)
     76  if dt.hour < 2:
     77    dt -= timedelta(hours=48)
     78  else:
     79    dt -= timedelta(hours=24)
     80  start = dt.replace(hour=22, minute=0, second=0, microsecond=0)
     81  start = start.astimezone(utc)
     82  
     83  
     84  # Collect all of today's posts and put them in a list of tuples.
     85  posts = []
     86  for s in subscriptions:
     87    f = fp.parse(s)
     88    try:
     89      blog = f['feed']['title']
     90    except KeyError:
     91      continue
     92    for e in f['entries']:
     93      try:
     94        when = e['published_parsed']
     95      except KeyError:
     96        when = e['updated_parsed']
     97      when =  datetime(*when[:6])
     98      # This is the exception. Change it to midnight today, local time.
     99      if when == mnToday:
    100        when = homeTZ.localize(when).astimezone(utc)
    101      else:
    102        when = utc.localize(when)
    103      if when > start:
    104        title = e['title']
    105        try:
    106          body = e['content'][0]['value']
    107        except KeyError:
    108          body = e['summary']
    109        link = e['link']
    110        posts.append((when, blog, title, link, body))
    111  
    112  # Sort the posts in reverse chronological order.
    113  posts.sort()
    114  posts.reverse()
    115  
    116  # Turn them into an HTML list.
    117  listTemplate = '''<li>
    118    <p class="title"><a href="{3}">{2}</a></p>
    119    <p class="info">{1}<br />{0}</p>
    120    <p>{4}</p>\n</li>'''
    121  litems = []
    122  for p in posts:
    123    q = [ x.encode('utf8') for x in p[1:] ]
    124    timestamp = p[0].astimezone(homeTZ)
    125    q.insert(0, timestamp.strftime('%b %d, %Y %I:%M %p'))
    126    litems.append(listTemplate.format(*q))
    127  ul = '\n<hr />\n'.join(litems)
    128  
    129  # Print the HTMl.
    130  print '''<html>
    131  <meta charset="UTF-8" />
    132  <meta name="viewport" content="width=device-width" />
    133  <head>
    134  <style>
    135  body {{
    136    background-color: #555;
    137    width: 750px;
    138    margin-top: 0;
    139    margin-left: auto;
    140    margin-right: auto;
    141    padding-top: 0;
    142  }}
    143  h1, h2, h3, h4, h5, h6 {{
    144    font-family: Helvetica, Sans-serif;
    145  }}
    146  h1 {{
    147    font-size: 110%;
    148  }}
    149  h2 {{
    150    font-size: 105%;
    151  }}
    152  h3, h4, h5, h6 {{
    153    font-size: 100%;
    154  }}
    155  .rss {{
    156    list-style-type: none;
    157    margin: 0;
    158    padding: .5em 1em 1em 1.5em;
    159    background-color: white;
    160  }}
    161  .rss li {{
    162    margin-left: -.5em;
    163    line-height: 1.4;
    164  }}
    165  .rss li pre {{
    166    overflow: auto;
    167  }}
    168  .rss li p {{
    169    overflow-wrap: break-word;
    170    word-wrap: break-word;
    171    word-break: break-word;
    172    -webkit-hyphens: auto;
    173    hyphens: auto;
    174  }}
    175  .rss li figure {{
    176    -webkit-margin-before: 0;
    177    -webkit-margin-after: 0;
    178    -webkit-margin-start: 0;
    179    -webkit-margin-end: 0;
    180  }}
    181  .title {{
    182    font-weight: bold;
    183    font-family: Helvetica, Sans-serif;
    184    font-size: 120%;
    185    margin-bottom: .25em;
    186  }}
    187  .title a {{
    188    text-decoration: none;
    189    color: black;
    190  }}
    191  .info {{
    192    font-size: 85%;
    193    margin-top: 0;
    194    margin-left: .5em;
    195  }}
    196  img {{
    197    max-width: 700px;
    198  }}
    199  @media screen and (max-width:667px) {{
    200    body {{
    201      font-size: 200%;
    202      width: 650px;
    203      background-color: white;
    204    }}
    205    .rss li {{
    206      line-height: normal;
    207    }}
    208    img {{
    209      max-width: 600px;
    210    }}
    211  }}
    212  </style>
    213  <title>Today’s RSS</title>
    214  <body>
    215  <ul class="rss">
    216  {}
    217  </ul>
    218  </body>
    219  </html>
    220  '''.format(ul)
    
    

The new stuff starts on Line 74, with the variable `mnToday` being defined as a `datetime` object set to midnight today with no assigned time zone. Then Lines 99-102 check to see if the publication date of an entry (the value of `when`) matches `mnToday`.

If it matches `mnToday`, we assume the time portion has been set by default and should be considered somewhat fictional. We set it to midnight Central Time so it will be included in today's feed list and then convert it to UTC, because that's how all the other timestamps are handled. If the publication date of the entry doesn't match `mnToday`, it's taken as a legitimate UTC time and not adjusted.

So now I have Eddie back, and as a bonus, my aggregator is more robust than it was before. I think I've said this before: I understand why Brent Simmons got out of the RSS parsing business.
