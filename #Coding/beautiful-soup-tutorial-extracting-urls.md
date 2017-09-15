# Beautiful Soup Tutorial #2: Extracting URLs

_Captured: 2017-08-31 at 10:00 from [python.gotrained.com](http://python.gotrained.com/beautifulsoup-extracting-urls/?ref=quuu&utm_content=buffer9affa&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

After [installing the required libraries: BeautifulSoup, Requests, and LXML](http://python.gotrained.com/install-beautifulsoup/), let's learn how to extract URLs.

I will start by talking informally, but you can find the formal terms in comments of the code. Needless to say, variable names can be anything else; we care more about the code workflow.

So we have 5 variables:

  1. url: It is the website/page you want to open.
  2. response: Great! Your internet connection works, your URL is correct; you are allowed to access this page. It is just like you can see the web page now in your browser.
  3. data: It is like you are using copy-paste to get the text, namely the source code, of the page into memory, but it is rather into a variable.
  4. soup: You are asking BeautifulSoup to parse text; i.e. to extract text out of tags.
  5. tags: You are now extracting specific tags like tags for links into a list so that you can loop on them later.

Extracting URLs is something you will be doing all the time in web scraping and crawling tasks. Why? Because you need to start by one page (e.g. book list) and then open sub-pages (e.g. the page of each book) to scrape data from it.

Now, here is the code if this lesson. It extracts all the URLs from a web page.

123456789101112131415161718192021
from bs4 import BeautifulSoupimport requestsurl = "http://www.htmlandcssbook.com/code-samples/chapter-04/example.html"# Getting the webpage, creating a Response object.response = requests.get(url)# Extracting the source code of the page.data = response.text# Passing the source code to BeautifulSoup to create a BeautifulSoup object for it.soup = BeautifulSoup(data, 'lxml')# Extracting all the <a> tags into a list.tags = soup.find_all('a')# Extracting URLs from the attribute href in the <a> tags.for tag in tags:print(tag.get('href'))

Read the code carefully and try to run it. Even try to change the "url" to other web pages. Let me know if you have questions.

If you want to learn more about web scraping, you can join this online video course:

**[Web Scraping with Python: BeautifulSoup, Requests & Selenium](https://www.udemy.com/web-scraping-with-python-beautifulsoup/?couponCode=SITE-BS-URLS) **
