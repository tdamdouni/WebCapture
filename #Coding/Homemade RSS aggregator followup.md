# Homemade RSS aggregator followup

_Captured: 2015-12-20 at 22:09 from [leancrew.com](http://leancrew.com/all-this/2015/12/homemade-rss-aggregator-followup/)_

It's been about a month since I started using my [homemade RSS feed aggregator](http://leancrew.com/all-this/2015/11/simpler-syndication/), and I haven't once missed [Reeder](https://itunes.apple.com/us/app/reeder-3/id697846300?mt=8&uo=4&at=10l4Fv) or [ReadKit](https://itunes.apple.com/us/app/readkit/id588726889?mt=12&uo=4&at=10l4Fv). That doesn't mean everything about my system has been perfect, but it does mean that it's worth the effort to improve it because I'm pretty sure I'll be sticking with it.

There have been four fundamental problems with the system. I've fixed three of them and am not sure whether fixing the fourth is worth it.

Let's start by showing you the current version of the entire `dayfeed` script, which is run periodically (on my server, via a `cron` job) to create an HTML page with all of today's articles from the site I subscribe to.
    
    
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
     59    'http://high90.com/feed',
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
     85        when = e['published_parsed']
     86      except KeyError:
     87        when = e['updated_parsed']
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
    122    background-color: #555;
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
    145  .rss li p {{
    146    overflow-wrap: break-word;
    147    word-wrap: break-word;
    148    word-break: break-word;
    149    -webkit-hyphens: auto;
    150    hyphens: auto;
    151  }}
    152  .title {{
    153    font-weight: bold;
    154    font-family: Helvetica, Sans-serif;
    155    font-size: 110%;
    156    margin-bottom: .25em;
    157  }}
    158  .title a {{
    159    text-decoration: none;
    160    color: black;
    161  }}
    162  .info {{
    163    font-size: 85%;
    164    margin-top: 0;
    165    margin-left: .5em;
    166  }}
    167  img {{
    168    max-width: 700px;
    169  }}
    170  @media screen and (max-width:667px) {{
    171    body {{
    172      font-size: 200%;
    173      width: 650px;
    174      background-color: white;
    175    }}
    176    .rss li {{
    177      line-height: normal;
    178    }}
    179    img {{
    180      max-width: 600px;
    181    }}
    182  }}
    183  </style>
    184  <title>Today’s RSS</title>
    185  <body>
    186  <ul class="rss">
    187  {}
    188  </ul>
    189  </body>
    190  </html>
    191  '''.format(ul)
    
    

In general outline, it's the same as it was a month ago, but with two small changes to address two of the four problems.

The first problem was with updates. When I wrote `dayfeed`, I thought it would be nice to track and sort on the `updated_parsed` element of each entry. That way, when older posts got updated, they'd float up to the top of the reverse chronological list of articles, and I'd see the updates. In practice, this turned out to be really annoying for some sites because they would update the `updated_parsed` element with every little edit to the article. So whenever the author would go back and fix a typo, the article would reappear at the top of my page, even though the substance of the article hadn't changed.

The section of the original version of `dayfeed` that set the date and time of an article was this:
    
    
    84      try:
    85        when = e['updated_parsed']
    86      except KeyError:
    87        when = e['published_parsed']
    88      when =  utc.localize(datetime.fromtimestamp(time.mktime(when)))
    
    

As you can see, it sets the date of the article (the `when` variable) according to the `updated_parsed` element if it exists and falls back to the `published_parsed` element if it doesn't. This fallback mechanism was necessary because some feeds don't include `updated_parsed`.

The solution to my update problem was to flip the order of the `try` and `except` parts. Now this section of `dayfeed` looks like this:
    
    
    84      try:
    85        when = e['published_parsed']
    86      except KeyError:
    87        when = e['updated_parsed']
    88      when =  utc.localize(datetime.fromtimestamp(time.mktime(when)))
    
    

I still keep `updated_parsed` in there because some feeds don't include `published_parsed`. Luckily, the sites I subscribe to that adjust the `updated_parsed` element with every edit also include a `published_parsed` element, .

(I should mention, I suppose, that neither `published_parsed` nor `updated_parsed` are actual RSS elements. They're derived elements [created by the `feedparser` module](https://pythonhosted.org/feedparser/date-parsing.html) by parsing the `<published>` [or `<pubDate>`] and `<updated>` date and time strings into standard Python `[struct_time`](https://docs.python.org/2/library/time.html#time.struct_time) tuples.)

The second problem had to do with formatting very long strings with no word breaks. Typically these are URLs, but one of the sites I subscribe to often uses a long string of underscores instead of an `<hr>` tag to separate sections of an article. With the original version of `dayfeed`, these long strings would cause the font size to shrink to accomodate their width. Which forced me to use a reverse pinch or double-tap to bring the text back up to a readable size.

I fixed this by following [these CSS-Tricks recommendations](https://css-tricks.com/snippets/css/prevent-long-urls-from-breaking-out-of-container/) and adding a new section to the CSS part of `dayfeed`:
    
    
    145  .rss li p {{
    146    overflow-wrap: break-word;
    147    word-wrap: break-word;
    148    word-break: break-word;
    149    -webkit-hyphens: auto;
    150    hyphens: auto;
    151  }}
    
    

These break up long lines as shown in the before and after screenshots below.

![Long line adjustment](http://leancrew.com/all-this/images2015/20151220-Long%20line%20adjustment.png)

> _Long line adjustment_

The third problem was with caching. To speed page loading, I have `leancrew.com` set up to use Apache's `[mod_expires`](https://httpd.apache.org/docs/2.2/mod/mod_expires.html) module with a default expiration of one month from the browser's access date. I liked how this worked for the blog as a whole, but not for the RSS feed page. Every time I'd open the RSS feeds page, Safari (mobile and desktop) would show me a cached version instead of the the most recent version.

I needed an exception for the RSS page, and I found the solution on [Stack Overflow](http://stackoverflow.com/questions/11532636/prevent-http-file-caching-in-apache-httpd-mamp). I now have an `.htaccess` file that includes these lines:
    
    
    <FilesMatch "rssfeed\.html$">
        FileEtag None
        <ifModule mod_headers.c>
            Header Unset ETag
            Header Set Cache-Control "max-age=0, no-store, no-cache, must-revalidate"
            Header Set Pragma "no-cache"
            Header Set Expires "Thu, 1 Jan 1970 00:00:00 GMT"
        </ifModule>
    </FilesMatch>

I'm sure some of these lines are unnecessary for Safari, but I'm too lazy to figure out which ones can be deleted.

The fourth problem is site-specific and was something I suspected might arise. For unexplained reasons, XKCD's feed doesn't get updated when the site does. So new comics appear in the feed with the correct publication date and time, but by the time they show up in the feed, it's the day after publication. And because I've set my system up to show me only "today's" articles, XKCD never makes it onto my feed page.

As I said, I had an inkling this might be a problem because I'd noticed quite some time ago that XKCD comics wouldn't show up in Reeder or ReadKit until the day after they were published. I suppose I could set up a special case, but for the moment, I've decided to take the easy way out and just follow [@xkcdComic](https://twitter.com/xkcdComic) on Twitter. It's not run by Randall Munroe, but it seems to be complete and not cluttered with extraneous tweets.

I didn't mean to imply in my original post that this sort of homemade aggregator was a new idea. Back when RSS was young, it was pretty for people to set up HTML pages that would tell them when their favorite sites had been updated. That sort of got lost when services like Bloglines and Google Reader got popular. For me, going back to RSS's roots, and not relying on the choices made by a third-party service, has been a pleasant experience.

This work is licensed under a [Creative Commons Attribution-Share Alike 3.0 Unported License](http://creativecommons.org/licenses/by-sa/3.0/).
