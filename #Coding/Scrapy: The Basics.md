# Scrapy: The Basics

_Captured: 2015-12-05 at 10:46 from [seanmckaybeck.com](https://seanmckaybeck.com/scrapy-the-basics.html)_

[Show Me the Code](https://seanmckaybeck.com/index.html)

  * [Blog](https://seanmckaybeck.com/index.html)
  * [Archive](https://seanmckaybeck.com/archives.html)
  * [Tags](https://seanmckaybeck.com/tags.html)
  * [About](https://seanmckaybeck.com/about.html)

## Web scraping

Did you ever want an easy way to collect all those posts from that cool blog you read? Or maybe you want to keep track of new posts to a favorite website? Well you can do all of that web scraping. It is a practice employed by normal developers and large companies. Google uses it to do all of their indexing for search. This guide will walk you through how to do it for yourself. As an example we will crawl [/r/learnpython](https://reddit.com/r/learnpython) for new posts.

## Scrapy

Scrapy is a Python framework for making web spiders. So-called spiders are the basis for crawling the web. Scrapy makes it easy to create a spider in just a few lines of code. Unfortunately, it only works with Python 2.7, so make sure you have a version of 2.7 installed. I used Python 2.7.10 to make this example spider.

### Installation

You should always start with a virtual environment for your projects. I keep all of mine is a folder called `venvs`. You do not have to do the same, although it keeps them separated from everything else. Ensure that `virtualenv` is installed for your system before continuing.
    
    
    $ virtualenv-2.7 venvs/scrapy
    # this creates your virtual environment
    $ source venvs/scrapy/bin/activate
    (scrapy)$ pip install scrapy service_identity
    $ 
    

The `service_identity` package fixes an OpenSSL issue I was having. It's possible you might get it as well, so install it just in case.

### Project creation

Scrapy provides an excellent and easy way to create a project. Scrapy will build a whole directory tree of everything you need just by supplying it with a project name. However, for a simple spider, like the one we are making, none of that is necessary. But just so you are aware, if you wanted to start a project in this manner you would run `scrapy startproject myspider`. You can follow a full tutorial in that manner using the [Scrapy docs](http://doc.scrapy.org/en/latest/intro/tutorial.html).

## Our spider

We just need something simple. Our spider will be 34 lines of code, although by stripping out white space is would be smaller. We will be crawling `/r/learnpython`, which only has text posts. However, the data we scrape can be gathered from any subreddit.

### Scraped data

Scrapy provides an object called an `Item` for storing scraped data. We must start our spider by defining our `Item`. Let's call it `TextPostItem`. We create our own class that inherits from the base class `Item` and define the fields we wish it to store.
    
    
    from scrapy.item import Item, Field
    
    class TextPostItem(Item):
        title = Field()
        url = Field()
        submitted = Field()
    

Put this in a file called `spider.py` (note that it does not matter what you name the file).

### The spider

That was easy, wasn't it? 6 lines and we have a nice little container for our scraped data. Now we need to build our spider. Scrapy provides many different kinds of spiders each of which serves a specific purpose. We want to recursively crawl through pages of our target subreddit, not just the first page. To do this we use a `CrawlSpider`. This kind of spider will allow us to easily crawl through multiple pages and get all that juicy data we need.

Let's start by creating our spider class and giving our spider a name.
    
    
    from scrapy.spiders import CrawlSpider
    
    class RedditCrawler(CrawlSpider):
        name = 'reddit-crawler'
        allowed_domains = ['reddit.com']
    

Now it has a name and also a list of the domains it is allowed to crawl. If it accidentally ends up with a link to some other site, our spider will obey these rules and ignore that site. We also need to tell our spider where to start crawling and give it certain settings to prevent spamming our target site. Most websites do not like it when users send requests in quick succession, and they will rate-limit you if you do so. So let's tell our spider to play nice.
    
    
    from scrapy.spiders import CrawlSpider
    
    class RedditCrawler(CrawlSpider):
        name = 'reddit-crawler'
        allowed_domains = ['reddit.com']
        start_urls = ['https://www.reddit.com/r/learnpython/new']
        custom_settings = {
                'BOT_NAME': 'reddit-scraper',
                'DEPTH_LIMIT': 7,
                'DOWNLOAD_DELAY': 3
            }
    

The `custom_settings` are things that would normally be specified in `settings.py` when you make a crawler using the `startproject` command. The `DEPTH_LIMIT` restricts the number of page links we follow. The `DOWNLOAD_DELAY` is the number of seconds to wait between requests. I set it at 3 seconds, but you could get away with 1.

All we have left is to define our scraping method. This is more complicated than everything else, but still is relatively straight-forward. There are two methods we can override in our spider that can accomplish this task. For our purposes we will override the `parse` method. This parse method is a generator. If you do not know how Python generators work then go read up on them: they are very helpful.

The most difficult part of getting the `parse` method working is your Xpath selectors. Xpath allows you to parse the html response from webpages based on html elements. To keep you sane I will provide each of the necessay xpaths for extracting our data from the reddit pages. If you are using this as a reference, note that an easy way to find xpaths is to use the Chrome developer console. Right-click on the target element on the page, then select `Inspect element`. This will pull up the console and highlight the target element. Now, right-click the highlighted element and select the option for the xpath.

For our xpaths we must grab the `div` containing all of the posts, and then we must select each of the desired items from those. We use the `Selector` class provided by Scrapy to wrap the html response and do our dirty work.
    
    
    from scrapy.selector import Selector
    
    def parse(self, response):
        s = Selector(response)
        next_link = s.xpath('//span[@class="nextprev"]//a/@href').extract()[0]
        if len(next_link):
            yield self.make_requests_from_url(next_link)
        posts = Selector(response).xpath('//div[@id="siteTable"]/div[@onclick="click_thing(this)"]')
        for post in posts:
            i = TextPostItem()
            i['title'] = post.xpath('div[2]/p[1]/a/text()').extract()[0]
            i['url'] = post.xpath('div[2]/ul/li[1]/a/@href').extract()[0]
            i['submitted'] = post.xpath('div[2]/p[2]/time/@title').extract()[0]
            yield i
    

The first `yield` is for the next page link. It returns a Scrapy `Request` object to use for crawling the next page. We then grab all of the posts on the page and iterate over them. For each post we create one of our `TextPostItem` objects and populate it with the post url, title, and the time it was submitted.

When we run this spider, Scrapy will print each `TextPostItem` out as a dictionary to `stdout`. For an initial run this is fine, but eventually you might want this saved to a file. This is also possible.

To run our spider, we execute `scrapy runspider spider.py`. There will be lots of debugging information printed out along with our scraped data. To save this all to a file, run `scrapy runspider spider.py -o items.json -t json`. This will save your scraped data as JSON to a file called `items.json`, which you can then use for whatever purposes you desire.

### Final product

Your final spider should look like the following.
    
    
    # -*- coding: utf-8 -*-
    from scrapy.spiders import CrawlSpider
    from scrapy.selector import Selector
    from scrapy.item import Item, Field
    
    
    class TextPostItem(Item):
        title = Field()
        url = Field()
        submitted = Field()
    
    
    class RedditCrawler(CrawlSpider):
        name = 'reddit_crawler'
        allowed_domains = ['reddit.com']
        start_urls = ['https://www.reddit.com/r/learnpython/new']
        custom_settings = {
                'BOT_NAME': 'reddit-scraper',
                'DEPTH_LIMIT': 7,
                'DOWNLOAD_DELAY': 3
                }
    
        def parse(self, response):
            s = Selector(response)
            next_link = s.xpath('//span[@class="nextprev"]//a/@href').extract()[0]
            if len(next_link):
                yield self.make_requests_from_url(next_link)
            posts = Selector(response).xpath('//div[@id="siteTable"]/div[@onclick="click_thing(this)"]')
            for post in posts:
                i = TextPostItem()
                i['title'] = post.xpath('div[2]/p[1]/a/text()').extract()[0]
                i['url'] = post.xpath('div[2]/ul/li[1]/a/@href').extract()[0]
                i['submitted'] = post.xpath('div[2]/p[2]/time/@title').extract()[0]
                yield i
    

## Further possibilities

With Scrapy the possibilities are endless (not literally). If you would like to scrape multiple subreddits, simply add links to the `start_urls` list. If you want to scrape other sites you can do that as well. Maybe there is an Atom RSS feed that interests you. Well, you can scrape that too.

Play with this spider and tweak it to your liking. Try adding fields to the `TextPostItem` such as one for the post author or for the number of upvotes the post has received. Once you are comfortable with how this spider works, try writing your own! You have the tools, so go out there and scrape!

This entry was tagged as [python](https://seanmckaybeck.com/tag/python.html) [scrapy](https://seanmckaybeck.com/tag/scrapy.html) [web-scraping](https://seanmckaybeck.com/tag/web-scraping.html)
