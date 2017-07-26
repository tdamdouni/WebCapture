# Post to Pelican from Drafts

_Captured: 2016-04-10 at 13:25 from [robmalanowski.com](http://robmalanowski.com/post-to-pelican-from-drafts.html)_

This website runs on the excellent [Pelican static site generator](http://getpelican.com). The site is generated from a directory of markdown / plain text files. It's very lightweight - it does not require a database at all. It doesn't require PHP. In fact, the VPS that I host this site on doesn't even have MySQL or PHP installed. It's a very simple, very affordable server.

The benefits of static sites outweigh the drawbacks, at least for a site such as this one. One of the biggest drawbacks of a static site is the difficulty in making updates. Fortunately, this is a solvable problem. I store the folder of markdown files in a Dropbox folder. Using the [Dropbox CLI](https://www.dropbox.com/install?os=lnx) tool, I installed Dropbox on my VPS. After a bit of configuration, Pelican will look in the Dropbox folder for the content files. One line in the crontab, and my site rebuilds and updates automatically, every five minutes.[1](http://robmalanowski.com/post-to-pelican-from-drafts.html)

With this setup, any properly formatted markdown file in my Pelican folder automatically generates a new article on this site. I don't have to fuss around with FTP clients or any such nonsense. I write, then move the text file into the proper folder, and the syncing / update magic happens by itself.

### What about iOS?

As long as static site generators and iOS devices have been around, people have been trying to figure out ways to post on the go. Normally these methods involve keeping a Mac powered on at all times. That didn't fly for me, so I put together something much better.

Using the method I will explain below, you can post an article to your Pelican site using only your iPhone / iPad. You don't even need to _own_ a Mac, much less keep it running 24/7.

#### Step 1

Install [Notesy](https://itunes.apple.com/us/app/notesy-for-dropbox/id386095500). It's $5, and well worth it. It's important that you only use Notesy for this purpose. Set Notesy to sync to your Pelican folder - the folder filled with your Markdown files.

#### Step 2

Install this Drafts action that sends the article to Pythonista for processing:

`pythonista://Pelican?action=run&argv=[[title]]&argv=[[body]]`

Or, if you prefer, [click here](drafts://x-callback-url/import_action?type=URL&name=Post%20to%20Pelican&url=pythonista%3A%2F%2FPelican%3Faction%3Drun%26argv%3D%5B%5Btitle%5D%5D%26argv%3D%5B%5Bbody%5D%5D) to install the Drafts action automatically.

#### Step 3

Install this Pythonista script:

` import console import sys import webbrowser import datetime import urllib`

`console.clear()`

`
    
    
    #The Drafts action passes two variables to Pythonista - [[title]] and [[body]]
    #Use sys.argv[x] to call these variables. Remember, the script *name* takes sys.argv[0].
    
    print "Formatting the article.\n"
    
    articleTitle = sys.argv[1]
    articleBody = sys.argv[2]
    
    #Current date and time :
    now = datetime.datetime.now()
    now = now.strftime("%Y-%m-%d %H:%M")
    #URL Encode the date & time
    UAnow = urllib.quote(now, safe='')
    
    #Convert the title to lowercase and replaces any spaces with dashes. Use that as the slug.
    articleSlug = articleTitle.lower().replace(" ","-")
    
    #URL encode the title and body
    UEArticleTitle = urllib.quote(articleTitle, safe='')
    UEArticleBody = urllib.quote(articleBody, safe='')
    
    #The crazy looking URL below will format the Pelican metadata like so:
    
    #Title: UEArticleTitle
    #Date: now
    #Tags: 
    #Category: 
    #Slug: articleSlug
    #Author: Rob
    #Summary: 
    #Status: draft
    
    #UEArticleBody
    
    #This creates a Notesy note with the name specified (it will append to an existing note if applicable) and sets the text.
    #toNotesy = notesy://x-callback-url/append?name=whatever&text=[[draft]]
    
    toNotesy = 'notesy://x-callback-url/append?name=' + UEArticleTitle + '&text=Title%3A%20' + UEArticleTitle + '%0ADate%3A%20' + UAnow + '%0ATags%3A%20%0ACategory%3A%20%0ASlug%3A%20' + articleSlug + '%0AAuthor%3A%20Rob%0ASummary%3A%20%0AStatus%3A%20draft%0A%0A' + UEArticleBody
    
    #print toNotesy
    
    webbrowser.open(toNotesy)
    

`

Or, if you prefer, get it from [Github](https://github.com/rmalanowski/post-to-pelican/blob/master/Pelican.py).

### Now you can post to Pelican from Drafts

Write your article in Drafts. Your first line is the title of your article, and everything else is the article. When you're finished, tap the "Post to Pelican" link. Pythonista will automatically set up the metadata, add the date, and generate a URL slug for you. It will send the result, metadata and all, to Notesy.

Once you're in Notesy, add categories and / or tags as you see fit. When you are ready to post, simply remove the "Status: Draft" line from the metadata. The file will automatically be saved, synced to your VPS via Dropbox, and posted the next time cron runs.

### Notes

I am terrible at Python. I have been using this method for a few weeks now. I haven't noticed any problems / data loss / etc. For all I know, if you use it, the sun could go supernova and destroy us all. So, backup, and all that. Otherwise, enjoy. If you notice something that doesn't work right, please let me know so I can fix it. You can reach me on [Twitter](https://twitter.com/malanowski) or by [email](http://robmalanowski.com/pages/contact.html).
