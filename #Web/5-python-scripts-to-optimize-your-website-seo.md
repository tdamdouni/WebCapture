# 5 Python Scripts to Optimize Your Website SEO

_Captured: 2017-08-23 at 19:41 from [dzone.com](https://dzone.com/articles/5-python-scripts-to-optimize-your-website-seo?edition=319391&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-22)_

![](https://www.catswhocode.com/blog/wp-content/uploads/2017/08/python-snippets-seo.jpg)

Python is not only an amazing programming language, it's also very helpful when it comes to developing tools for SEO. In this article, I have compiled 5 of the best Python scripts to optimize your website SEO: Check broken links and indexed URLs, grab data from Mozscape, and more.

## Python SEO Analyzer

A small SEO tool that analyzes the structure of a site, crawls the site, counts words in the body of the site and warns of any general SEO related issues. The script requires Python 2.7+, BeautifulSoup4, minidom, nltk, numpy, and urllib2.

Info and download: <https://github.com/sethblack/python-seo-analyzer>

## Broken Link Checker

Google doesn't like sites with broken links, which is truly understandable. But how do you daily check all links your site has?

If you're using WordPress, the easiest way to do so would be to install the Broken Links Checker plugin, which really does wonders. But if your site isn't WordPress based, here's a great Python script to crawl your site and return broken links so you can edit them.

Info and download: <https://github.com/yushulx/crawl-404>

## Calculate Keyword Growth Using Google Trends and Python

When doing SEO for your site, Google Trends is extremely useful to determine if interest in keywords has grown over time or if they are slipping away into oblivion. But Google doesn't provide an API for easy bulk keyword growth research.

Thanks to Python, this can easily be done with a little script and a .csv file.

Info and download: <https://searchwilderness.com/google-trends-api-slope/>

## Get Google Webmaster Tools Data With Python

The Search Query report in Google Webmaster Tools is more important than ever, with the ominous mask hiding 25%-40% of referring keyword traffic in Google Analytics. Google recently made WMT data available through an open-source Python Library, making it easy to transfer that data straight into Google Docs or to your desktop, but setup and configuration aren't easy for most.

Here is a ready-to-use Python script to easily get Google Webmaster Tools data. Full instructions are provided on the related article.

Info and download: <https://www.seo.com/blog/tutorial-google-webmaster-tools-data-windows-python/>

## Pyscape: Grab Data From the Mozscape API

[Moz](https://moz.com/) crawls the web constantly, searching for new content and re-crawling existing content. Each URL and other interesting details about pages are saved: HTTP status code, page title, links, and other information.

Pyscape is an open-source Python library for accessing the [Mozscape API](https://moz.com/help/guides/moz-api/mozscape) and grabs the aforementioned data from Moz.
