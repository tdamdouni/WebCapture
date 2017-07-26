# Python 3 web-scraping examples with public data

_Captured: 2016-11-06 at 08:25 from [blog.danwin.com](http://blog.danwin.com/examples-of-web-scraping-in-python-3-x-for-data-journalists/)_

Someone on the [NICAR-L listserv](https://www.ire.org/resource-center/listservs/subscribe-nicar-l/) asked for advice on the best Python libraries for web scraping. My advice below includes what I did for last spring's [Computational Journalism class](http://www.compjour.org/), specifically, the [Search-Script-Scrape](https://github.com/compjour/search-script-scrape) project, which involved 101-web-scraping exercises in Python.

See the repo here: <https://github.com/compjour/search-script-scrape>

### Best Python libraries for web scraping

For the remainder of this post, I assume you're using **Python 3.x,** though the code examples will be virtually the same for 2.x. For my [class last year](http://www.compjour.org), I had everyone install the [Anaconda Python distribution](https://www.continuum.io/downloads), which comes with all the libraries needed to complete the [Search-Script-Scrape exercises](https://github.com/compjour/search-script-scrape), including the ones mentioned specifically below:

The best package for **general web requests**, such as downloading a file or submitting a POST request to a form, is the simply-named [requests library](http://docs.python-requests.org/en/latest/) _("HTTP for Humans")_.

Here's an overly verbose example:
    
    
    import requests
    response = requests.get("https://en.wikipedia.org/robots.txt")
    txt = response.text
    print(txt)
    #
    # robots.txt for http://www.wikipedia.org/ and friends
    #
    # ...
    

The requests library even does JSON parsing if you use it to fetch JSON files. Here's an example with the [Google Geocoding API](https://developers.google.com/maps/documentation/geocoding/intro):
    
    
    import requests
    base_url = 'http://maps.googleapis.com/maps/api/geocode/json'
    my_params = {'address': '100 Broadway, New York, NY, U.S.A', 
                 'language': 'ca'}
    response = requests.get(base_url, params = my_params)
    results = response.json()['results']
    x_geo = results[0]['geometry']['location']
    print(x_geo['lng'], x_geo['lat'])
    # -74.01110299999999 40.7079445
    

For the **parsing of HTML and XML**, [Beautiful Soup 4](http://www.crummy.com/software/BeautifulSoup/bs4/doc/) seems to be the most frequently recommended. I never got around to using it because it was malfunctioning on my [particular installation of Anaconda on OS X](https://gist.github.com/dannguyen/72060a639a1ae7ec6204).

But I've found [lxml](https://github.com/lxml/lxml/) to be perfectly fine. I believe both lxml and bs4 have similar capabilities - you [can even specify lxml to be the parser for bs4](http://stackoverflow.com/questions/27790415/set-lxml-as-default-beautifulsoup-parser). I think bs4 might have a friendlier syntax, but again, I don't know, as I've gotten by with lxml just fine:
    
    
    import requests
    from lxml import html
    page = requests.get("http://www.example.com").text
    doc = html.fromstring(page)
    link = doc.cssselect("a")[0]
    print(link.text_content())
    # More information...
    print(link.attrib['href'])
    # http://www.iana.org/domains/example
    

The standard [urllib package](https://docs.python.org/3/library/urllib.html) also has a lot of useful utilities - I frequently use the methods from [urllib.parse](https://docs.python.org/3/library/urllib.parse.html#module-urllib.parse). Python 2 also has [urllib](https://docs.python.org/2/library/urllib.html) but the methods are arranged differently.

Here's an example of using the `urljoin` method to resolve the relative links on the [California state data for high school test scores](http://www.cde.ca.gov/ds/sp/ai/). The use of `os.path.basename` is simply for saving the each spreadsheet to your local hard drive:
    
    
    from os.path import basename
    from urllib.parse import urljoin
    from lxml import html
    import requests
    base_url = 'http://www.cde.ca.gov/ds/sp/ai/'
    page = requests.get(base_url).text
    doc = html.fromstring(page)
    hrefs = [a.attrib['href'] for a in doc.cssselect('a')]
    xls_hrefs = [href for href in hrefs if 'xls' in href]
    for href in xls_hrefs:
      print(href) # e.g. documents/sat02.xls
      url = urljoin(base_url, href)
      with open("/tmp/" + basename(url), 'wb') as f:
        print("Downloading", url)
        # Downloading http://www.cde.ca.gov/ds/sp/ai/documents/sat02.xls
        data = requests.get(url).content
        f.write(data) 
    

And that's about all you need for the majority of web-scraping work - at least the part that involves reading HTML and downloading files.

## Examples of sites to scrape

The [101 scraping exercises](https://github.com/compjour/search-script-scrape) didn't go so great, as I didn't give enough specifics about what the exact answers should be (e.g. round the numbers? Use complete sentences?) or even where the data files actually were - as it so happens, not everyone Googles things the same way I do. And I should've made them do it on a weekly basis, rather than waiting till the end of the quarter to try to cram them in before finals week.

The [Github repo lists each exercise](https://github.com/compjour/search-script-scrape#the-tasks) with the solution code, the relevant URL, and the number of lines in the solution code.

The exercises run the gamut of simple parsing of static HTML, to inspecting AJAX-heavy sites in which knowledge of the network panel is required to discover the JSON files to grab. In many of these exercises, the HTML-parsing is the trivial part - just a few lines to parse the HTML to dynamically find the URL for the zip or Excel file to download (via requests)…and then 40 to 50 lines of unzipping/reading/filtering to get the answer. That part is beyond what typically considered "web-scraping" and falls more into "data wrangling".

I didn't sort the exercises on the list by difficulty, and many of the solutions are not particulary great code. Sometimes I wrote the solution as if I were teaching it to a beginner. But other times I solved the problem using the style in the most randomly bizarre way relative to how I would normally solve it - hey, writing 100+ scrapers gets _boring_.

But here are a few representative exercises with some explanation:

I think [data.gov](http://catalog.data.gov/dataset) actually has an API, but this script relies on finding the easiest tag to grab from the front page and extracting the text, i.e. the `186,569` from the text string, `"186,569 datasets found"`. This is obviously not a very robust script, as it will break when data.gov is redesigned. But it serves as a quick and easy HTML-parsing example.

[Texas's death penalty site](https://www.tdcj.state.tx.us/death_row/index.html) is probably one of the best places to practice web scraping, as the HTML is pretty straightforward on the main landing pages (there are several, for [scheduled](https://www.tdcj.state.tx.us/death_row/dr_scheduled_executions.html) and [past executions](https://www.tdcj.state.tx.us/death_row/dr_executed_offenders.html), and [current inmate roster](https://www.tdcj.state.tx.us/death_row/dr_offenders_on_dr.html)), which have enough interesting tabular data to collect. But you can make it more complex by traversing the links to collect inmate data, mugshots, and final words. This script just finds the first person on the scheduled list and does some math to print the number of days until the execution (I probably made the datetime handling more convoluted than it needs to be in the [provided solution](https://github.com/compjour/search-script-scrape/blob/master/scripts/29.py))

The [analytics.usa.gov](https://analytics.usa.gov) site is a great place to practice AJAX-data scraping. It's a very simple and robust site, but either you are aware of AJAX and know how to use the network panel (and in this case, locate ie.json, or you will have no clue how to scrape even a single number on this webpage. I think the difference between static HTML and AJAX sites is one of the tougher things to teach novices. But they pretty much have to learn the difference given how many of today's websites use both static and dynamically-rendered pages.

There's actually no HTML parsing if you assume the URLs for the data files can be hard coded. So besides the nominal use of the **requests** library, this ends up being a data-wrangling exercise: download two specific zip files, unzip them, read the CSV files, filter the dictionaries, then do some math.

Another example with no HTML parsing, but probably the most complicated example. You have to download and parse [Sunlight Foundation's CSV of Congressmember data](https://sunlightlabs.github.io/congress/#legislator-spreadsheet) to get all the Twitter usernames. Then [authenticate with Twitter's API](http://www.compjour.org/tutorials/getting-started-with-tweepy/), then perform mulitple [batch lookups](https://dev.twitter.com/rest/reference/get/users/lookup) to get the data for all 500+ of the Congressional Twitter usernames. Then join the sorted result with the actual Congressmember identity. I probably shouldn't have assigned this one.

I included no-HTML exercises because there are plenty of data programming exercises that don't have to deal with the specific nitty-gritty of the Web, such as understanding HTTP and/or HTML. It's not just that a lot of public data has moved to JSON (e.g. the [FEC API](https://18f.gsa.gov/2015/07/08/openfec-api/)) - but that much of the [best public data is found in bulk CSV and database files](http://cjlab.stanford.edu/2015/09/30/lab-launch-and-data-sets/). These files can be programmatically fetched with simple usage of the **requests** library.

It's not that parsing HTML isn't a whole boatload of fun - and being able to do so is a useful skill if you want to _build_ websites. But I believe novices have more than enough to learn from in sorting/filtering dictionaries and lists without worrying about learning how a website works.

Besides [analytics.usa.gov](https://analytics.usa.gov), the [data.usajobs.gov API](https://data.usajobs.gov), which lists federal job openings, is a great one to explore, because its data structure is simple and the site is robust. Here's a [Python exercise](https://github.com/compjour/search-script-scrape/blob/master/scripts/4.py) with the USAJobs API; and [here's one in Bash](http://www.compciv.org/homework/assignments/usa-jobs-gov/).

There's also the [Google Maps geocoding API](https://developers.google.com/maps/documentation/geocoding/intro), which can be hit up for a bit before you run into rate limits, and you get the bonus of teaching geocoding concepts. The [NYTimes API requires creating an account](http://developer.nytimes.com/docs), but you not only get good APIs for some political data, but for content data (i.e. articles, bestselling books) that is interesting fodder for journalism-related analysis.

But if you want to scrape HTML, then the Texas death penalty pages are the way to go, because of the simplicity of the HTML and the numerous ways you can traverse the pages and collect interesting data points. Besides the [previously mentioned Texas Python scraping exercise](https://github.com/compjour/search-script-scrape/blob/master/scripts/29.py), here's one for [Florida's list of executions](https://github.com/compjour/search-script-scrape/blob/master/scripts/30.py). And here's a [Bash exercise that scrapes data from Texas, Florida, and California](http://www.compciv.org/homework/assignments/death-row-parsing/) and does a simple demographic analysis.

If you want more interesting public datasets - most of which require only a minimal of HTML-parsing to fetch - check out the [list I talked about in last week's info session on Stanford's Computational Journalism Lab](http://cjlab.stanford.edu/2015/09/30/lab-launch-and-data-sets/).
