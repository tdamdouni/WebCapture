# Modular URL shortening TextExpander snippets

_Captured: 2015-09-26 at 02:38 from [www.leancrew.com](http://www.leancrew.com/all-this/2014/08/modular-url-shortening-textexpander-snippets/)_

Yesterday, John Flavin pointed out that my [TextExpander](https://itunes.apple.com/us/app/textexpander-for-mac/id405274824?mt=12&uo=4&at=10l4Fv) snippets for [getting Google-shortened URLs](http://www.leancrew.com/all-this/2014/08/automatic-shortened-urls-via-google/) could be built better:

He's right. Although I was thinking my snippets had to be self contained, they can call other snippets and incorporate the results--even if the snippet that's doing the calling is a shell script or AppleScript snippet. TextExpander does the expansion first and then runs the script. So I refactored my snippets this way:

First, there's my old snippet for getting the (unshortened) URL of the active browser tab, `;furl`. It's an AppleScript snippet with the following content:
    
    
     1  tell application "System Events"
     2    set numSafari to count (every process whose name is "Safari")
     3    set numChrome to count (every process whose name is "Google Chrome")
     4  end tell
     5  
     6  if numSafari > 0 then
     7    tell application "Safari" to get URL of front document
     8  else
     9    if numChrome > 0 then
    10      tell application "Google Chrome" to get URL of active tab of front window
    11    end if
    12  end if
    
    

(Note that I'm now using Vitor Galvao's one-liner for Chrome.)

Next, I have a Python script, `gshorten`, that's structured like [the Pythonista script](http://www.leancrew.com/all-this/2014/08/automatic-shortened-urls-via-google/) I use for shortening URLs on iOS, except that it takes the original URL from the command line and returns the shortened URL to standard output. It's saved in my `~/Dropbox/bin` folder. Here it is:
    
    
     1  #!/usr/bin/python
     2  
     3  import requests
     4  import json
     5  import sys
     6  
     7  # Build the request.
     8  shortener = "https://www.googleapis.com/urlshortener/v1/url"
     9  longURL = sys.argv[1]
    10  headers = {'content-type': 'application/json'}
    11  payload = {'longUrl': longURL}
    12  
    13  # Get the shortened URL and print it.
    14  r = requests.post(shortener, headers=headers, data=json.dumps(payload))
    15  sys.stdout.write(r.json()['id'])
    
    

The snippet I use to shorten the URL of the front browser tab uses both of these. It's a shell script snippet with abbreviation `;surl` and this content:
    
    
    #!/bin/bash
    ~/Dropbox/bin/gshorten '%snippet:;furl%'

It runs the `;furl` snippet and uses the result as the argument to `gshorten`. What's nice about this solution is that it's using AppleScript for what it's good for (communicating with applications) and Python for what it's good for (everything else).

Finally, the snippet I use to shorten a URL on the clipboard has the abbreviation `;scurl` and this content:
    
    
    #!/bin/bash
    ~/Dropbox/bin/gshorten '%clipboard'

It's basically the same as `;surl` except that it uses the clipboard as the argument to `gshorten`.

Splitting things up this way makes my system a bit more complicated, but there's less repetition and, more important, each component does one thing. If I need to change the code for getting the front tab's URL (to add another browser, for example, or if a browser changes its AppleScript library), I only have to change the code in `;furl`. Similarly, if Google changes its API, I only have to fix the code in `gshorten`.

Someone my age should know enough to use modular design in the first place. Thanks to John for straightening me out.
