# Yahoo open-sources Anthelion web crawler for parsing structured data on HTML pages

_Captured: 2015-12-14 at 21:48 from [venturebeat.com](http://venturebeat.com/2015/12/14/yahoo-open-sources-anthelion-web-crawler-for-parsing-structured-data-on-html-pages/)_

![Yahoo billboard Daniel Spisak Flickr](http://venturebeat.com/wp-content/uploads/2015/12/Yahoo-billboard-Daniel-Spisak-Flickr-930x614.jpg)

> _Yahoo billboard Daniel Spisak Flickr_

Yahoo today announced that it has released the source code for its Anthelion web crawler designed for parsing structured data from HTML pages under an open-source license.

Web crawling is at the very core of Yahoo, even though it have many other applications, including Yahoo Mail, Yahoo Finance, Yahoo Messenger, Flickr, and Tumblr. For Yahoo to share code in an area as competitive as web search is significant.

Of course, it's coming at a time when Yahoo is planning a "[reverse spin-off"](http://venturebeat.com/2015/12/09/yahoo-confirms-its-suspending-its-alibabs-spin-off-plans-will-do-reverse-spin-off-instead/) of certain core business assets, but not its stake in Alibaba. Plus, [Yahoo chief executive Marissa Mayer](https://www.yahoo.com/tech/s/yahoo-ceo-gives-birth-twin-185036906.html) just had twins, so there's that. You could argue that that's irrelevant to web crawling technology, and I would probably concede that it is, too, and I would probably concede that it is too, but I can't bring myself to write about Yahoo's good news without mentioning the company's latest headlines. Anyway.

From VentureBeat

_**Ready to think outside the (ad) box? We've got the secret to successful F2P ad monetization and we're ready to spill the details - for free. [Sign up here.](https://www.brighttalk.com/webcast/12339/171365?utm_source=vb&utm_medium=boilerplate&utm_content=speedbump-tag&utm_campaign=dec-2-deltadna-webinar)**_

Last year, at the Conference on Information and Knowledge Management (CIKM) in Shanghai, Yahoo detailed Anthelion in a [paper](https://labs.yahoo.com/publications/6702/focused-crawling-structured-data).

"To the best of our knowledge, we are first to introduce the idea of a crawler focusing on semantic data, embedded in HTML pages using markup languages as microdata, microformats or RDFa," wrote authors Peter Mika and Roi Blanco of Yahoo Labs and Robert Meusel of Germany's University of Mannheim in the paper.

Microdata and RDFa are syntax formats for structured data about different topics. They're compatible with the [schema.org](http://venturebeat.com/2011/06/02/google-bing-and-yahoo-partner-for-web-tag-standards/) vocabulary for structured data, a project that the Google, Yahoo, and Bing search engines all work on.

The authors of the paper showed how an implementation of the crawling technology can offer a higher number of relevant results for certain search queries.

Now the code is available under an Apache license on [GitHub](https://github.com/yahoo/anthelion), as a plugin for the longstanding Apache Nutch open-source web crawler.

"Anthelion can be targeted to crawl for specific pages; for example, those including markup describing movies with at least two different attributes such as the title of and actors in a movie," Mika, Blanco, Meusel, and Yahoo Research intern Petar Ristoski wrote in a [Tumblr post](http://yahoolabs.tumblr.com/post/135196452221/explore-anthelion-our-open-source-focused-crawler) on the news.

More information:
