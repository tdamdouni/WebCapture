# How is BeautifulSoup different from Scrapy?

_Captured: 2015-12-05 at 11:16 from [www.quora.com](https://www.quora.com/How-is-BeautifulSoup-different-from-Scrapy)_

**Scrapy** is a Web-spider or **web scraper framework**, You give Scrapy a root URL to start crawling, then you can specify constraints on how many number of Urls you want to crawl and fetch,etc., It is a complete framework for Web-scrapping or **crawling**.

While

**Beautiful Soup** is a **parsing** **library** which also does pretty job of fetching contents from Url and allows you to parse certain parts of them without any hassle. It only fetches the contents of the URL that you give and stops. It does not crawl unless you manually put it inside a infinite loop with certain criteria.

In simple words, with Beautiful Soup you can build something similar to Scrapy.  
Beautiful Soup is a** library **while Scrapy is a **complete framework**.
