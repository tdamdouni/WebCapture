# How do I get a search box to appear in my site’s search results?

_Captured: 2015-10-21 at 00:25 from [vytm.in](http://vytm.in/F6V-vw#http://searchenginewatch.com/sew/how-to/2431095/how-do-i-get-a-search-box-to-appear-in-my-site-s-search-results)_

**I feel like I'm working through my first few articles on SEW in a rather logical manner. Answering the technical questions about search that are intriguing me as they come up.**

Last week I asked [how can I get sitelinks to appear in my site's search results?](http://searchenginewatch.com/sew/how-to/2430604/how-do-i-get-sitelinks-to-appear-in-my-site-s-search-results) The conclusion of which was as ambiguous as I suspected.

However during my investigation I realised there was something else missing from my site's search results… my very own search box within the sitelinks.

Like this one for Mashable...

![mashable-google-search](http://vytm.in/IMG/228/331228/mashable-google-search.png?1445286061)

> _Luckily the answer to this query is much more straightforward than the sitelinks problem._

### What does the sitelinks search box do?

The search box appears in the results when you search for certain brands or publishers, or when you add the word 'website' to a brand name ('sony website') or search for a brand with its top-level domain (.com, .co.uk etc.).

If the search box appears, you can then search within that site. Here I am searching for Mashable's articles on Instagram, which makes a change from my usual search for Gifs of kittens yawning.

![mashable-search-box-in-google-results](http://vytm.in/IMG/225/331225/mashable-search-box-in-google-results.png?1445281795)

> _However the results of this search leads to another page of Google results not, as you may expect, a page of results on the publisher's own website…_

![instagram-search-on-mashable](http://vytm.in/IMG/227/331227/instagram-search-on-mashable.png?1445282012)

### Why would I want this?

Hmm, good question. After all there's no guarantee that the searcher will find the articles they want in the listings above and may carry on with their Google research while never stepping a virtual muddy-boot in your website.

But of course we don't do this kind of thing to get traffic, we do this to improve the experience for the user. If they can't find a relevant article on your site, then they shouldn't be visiting you, and if they do, they'll bounce straight back out again.

However by serving these results, it increases the chances of a visit to your site as there are many more possible results, all of which are solely yours, without any organic or paid results from your nemesis competitor.

Moz did a little [research](https://moz.com/blog/sitelinks-search-box) and found that once the search box appeared in its branded results, there appeared to be a small rise in visits attributable to the box. 150 results per week, or 0.05% of all organic search sessions. Not an awful lot sure, but it's still not to be sniffed at.

There's also an psychological consideration to make. The search box perhaps adds a touch of extra legitimacy to your site; Google has deemed you worthy of your own search tool, so perhaps you are to be trusted.

However, Google isn't necessarily in charge of this addition, and here's where we get down to the technical aspects you've all been waiting for/skimmed through the last 12 paragraphs to get to...

### How do I get a search box to appear in my sitelinks?

As I discussed in last week's post on [whether it matters if you come first in search or not](http://searchenginewatch.com/sew/study/2430222/do-you-have-to-come-first-in-search-anymore), Schema markup gives you all kinds of options to make your search results stand out from other results; five star ratings, images, aggregated customer reviews and a search box.

In fact, according to [SimilarTech](https://www.similartech.com/categories/schema), a search box is the most used Schema markup for the top 10,000 websites.

To get your own search box, the only things you need are a website with a search tool of its own and the following piece of Schema code which you need to add to the HTML of your homepage…

< script type="application/ld+json">

{

"@context": "http://schema.org",

"@type": "WebSite",

"url": "https://www.example.com/",

"potentialAction": {

"@type": "SearchAction",

"target": "https://query.example.com/search?q={search_term_string}",

"query-input": "required name=search_term_string"

}

}

< /script>

Of course you'll have to change the "url" and "target" examples to your own URL.

To check it works, submit your site to the [structured data testing tool](https://developers.google.com/structured-data/testing-tool/) or for more detail check out the [Google Developers](https://developers.google.com/structured-data/slsb-overview) page.

Much like most things in search, there's no guarantee that Google will recognise your effort here, especially if your website doesn't receive much traffic from branded navigational search. However, like most things in search, it's worth a try.
