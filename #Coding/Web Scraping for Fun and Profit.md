# Web Scraping for Fun and Profit

_Captured: 2015-12-05 at 10:53 from [seanmckaybeck.com](https://seanmckaybeck.com/web-scraping-for-fun-and-profit.html)_

[Show Me the Code](https://seanmckaybeck.com/index.html)

  * [Blog](https://seanmckaybeck.com/index.html)
  * [Archive](https://seanmckaybeck.com/archives.html)
  * [Tags](https://seanmckaybeck.com/tags.html)
  * [About](https://seanmckaybeck.com/about.html)

## Web Scraping

Web scraping is the practice (or art, in some cases) of extracting data from webpages on the internet. It is used for all sorts of purposes, such as getting tables of data or for marketing. It is not something difficult to do, given the right set of tools. It typically involves getting the raw HTML of a page and extracting the data, but it can be argued that using a site's API also qualifies. Using Python, I will give an example of how it can help you.

## The Problem

On Reddit there is a subreddit devoted to buying/selling/trading precious metals called [/r/pmsforsale](https://www.reddit.com/r/pmsforsale). Lots of different coins and bars are sold on there daily, and members of the community are quick to respond to postings. For me to get to a post first I would need to constantly refresh the page and look through every post to determine if it had anything of interest to me. This is impractical for me since I work all day and cannot spend the whole day on Reddit (shocking, I know). Occasionally Mercury Dimes and NORFED rounds are put up for sale, and being popular items they tend to be claimed quickly. If I ever want a chance at purchasing either of these items I need a better solution.

## The Solution

Using 109 lines of Python code (including whitespace and docstrings) we can create a solution to my problem. I can't constantly monitor new posts, but a bot sure can. A bot can't reach over and poke me when it sees something, but it can send an email.

Using the Reddit API via `praw` the bot grabs the newest 25 posts on the target subreddit and checks the title and text for the desired items. This is done every 30 seconds. To prevent the need to store every post the bot has seen, it only looks at posts that are new since the last time it checked. Target metals are specified in a YAML configuration file and notifications are sent via email using [Mailgun](https://www.mailgun.com/). Mailgun is a free service that allows you to send up to 10,000 emails in a month using their API. Using a simple HTTP POST request you can send an email to whoever you want.

The full code of the bot can be seen [on my Github repo](https://github.com/ThaWeatherman/scrapers/blob/master/reddit/pmsforsale.py) containing all of my web scrapers. An example configuration file is provided so users can easily get the bot running. It is also designed to be modular, meaning you can specify your own Reddit account and target any subreddit and search for any text. To run this bot, use Python 3.5 (it should work with Python 2.7 as well) and install `praw` and `pyyaml`. Run `python pmsforsale.py -h` for usage help.

I have managed to jump on a good NORFED deal since starting the bot, while passing on a few other Mercury Dime sales. This is a simple example of web scraping can be used to automate your life and make simple tasks easier for you. Check out all the other scrapers in that repository for more inspiration and examples.

This entry was tagged as [python](https://seanmckaybeck.com/tag/python.html) [web-scraping](https://seanmckaybeck.com/tag/web-scraping.html)
