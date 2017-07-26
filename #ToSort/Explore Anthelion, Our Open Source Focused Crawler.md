# Explore Anthelion, Our Open Source Focused Crawler

_Captured: 2015-12-14 at 21:51 from [yahoolabs.tumblr.com](http://yahoolabs.tumblr.com/post/135196452221/explore-anthelion-our-open-source-focused-crawler)_

![](http://36.media.tumblr.com/6d885c1f5211232ab3300845df872716/tumblr_inline_nzcprdD4431rgj0aw_540.png)

> _The architecture of Anthelion_

By Petar Ristoski, [Peter Mika](https://labs.yahoo.com/researchers/pmika), [Roi Blanco](https://labs.yahoo.com/researchers/roi), and Robert Meusel

Would you like to collect large datasets from the Web? If so, then we have good news! Recently we publicly released [Anthelion](https://github.com/yahoo/anthelion), a focused crawler for semantic annotations in Web pages that steers in the direction of HTML pages-which are annotated with markup languages like RDFa, Microformats, and Microdata-to GitHub.

Anthelion can be targeted to crawl for specific pages; for example, those including markup describing movies with at least two different attributes such as the title of and actors in a movie. The system includes a ready-to-run extension for the [Apache Nutch Crawler](http://nutch.apache.org/) (nutch-anth), which can be run on a single machine as well as a Hadoop cluster. In addition, the GitHub project includes a testing environment for crawler simulations that makes it possible to measure the efficiency of the crawler in a controlled environment, as demonstrated in our research paper, "[Focused Crawling for Structured Data](https://labs.yahoo.com/publications/6702/focused-crawling-structured-data)."

With regard to methodology, the Anthelion system combines the benefits of online learning and a bandit-based selection strategy to adopt to the current crawling environment. Based on a given target function, each newly-discovered URL is classified, where the current crawled page is analyzed with respect to a target function and passed to the learner to further improve its quality. The final selection of what page to crawl next, is done by a bandit-based selection. The bandit chooses between exploration and exploitation (i.e., choosing between the most-promising page or a random page) based on a configuration parameter.

Experiments have shown that in comparison to a pure breadth-first search selection strategy, the number of retrieved relevant pages can be increased by a factor of three. In comparison to a pure online classification-based selection, the improvements are about 26%.

The complete code, which is released under Apache License 2.0, as well as a more comprehensive description can be found at the Yahoo GitHub repository: <https://github.com/yahoo/anthelion>

Have fun with the code and please let us know if you have any feedback!

Lots of thanks to:  
\+ the [Web Data Commons project](http://webdatacommons.org/structureddata/) and the [Common Crawl](http://commoncrawl.org/) project for providing their crawl data and extraction data  
\+ the [Any23 project](http://any23.apache.org/) for providing their great library of structured data parsers  
\+ the [Nutch project](http://nutch.apache.org/) for providing a great extendible crawling infrastructure
