# Google has no plans to use publisher URLs for AMP, despite little speed gain 

_Captured: 2016-12-14 at 09:42 from [searchengineland.com](http://searchengineland.com/google-url-for-amp-265344)_

![google-amp-speed-race-fast-ss-1920](http://searchengineland.com/figz/wp-content/seloads/2015/12/google-amp-speed-race-fast-ss-1920.png)

One of the biggest disadvantages for publishers in using [AMP](http://searchengineland.com/library/google/google-amp-project) -- the accelerated mobile pages format -- is that Google will not show a publisher's actual URL when displaying AMP pages. Google says this is so AMP pages load quickly. However, using a publisher's URL might hardly slow a page down. In fact, using Google's URL might actually cause AMP pages to load more slowly.

## The Google cache: why AMP at Google uses Google URLs

To understand the issue, consider this search for "google tag manager amp" on Google:

![google amp example listing](http://searchengineland.com/figz/wp-content/seloads/2016/12/IMG_3652_PNG_and_IMG_3654_PNG-764x600.png)

You'll see a [Marketing Land](http://marketingland.com/) article that appears, one that's in the AMP format. If you click on this article, it loads quickly. But the URL isn't for our sibling-site Marketing Land. Instead, it's for Google:

![google amp urls point at google](http://searchengineland.com/figz/wp-content/seloads/2016/12/IMG_3653_PNG.png)

What's happening is that Google is serving the page from its cache. It does this, because Google claims that this means the page will load more quickly than serving from the publisher's site.

Would skipping the Google cache really hurt? What if Google didn't use its own cache? What if it sent people directly to a publisher's AMP page on the publisher's site. Would that really slow the experience down that much?

For instance, instead of loading the page in the example above from the Google cache URL here:

> <https://www.google.com/amp/marketingland.com/google-tag-manager-now-supports-amp-accelerated-mobile-pages-196062/amp>

Google could instead send people to where the AMP page lives on our own site:

> <http://marketingland.com/google-tag-manager-now-supports-amp-accelerated-mobile-pages-196062/amp>

I asked Google about this for this article. It never gave me an answer about what the speed savings was in using its own cache versus serving a publisher's URL directly. That left it to me to rely on some other methods of estimating.

## Testing shows Google's cache might slow AMP pages

Google own mobile-friendly testing [tool](https://testmysite.thinkwithgoogle.com/) wouldn't provide me with actual load times but it did give general speed estimates. When I compared the two URLs above -- cached versus non-cached -- the results were as follows for mobile speed:

> Cached: 88/100  
Non-Cached: 68/100

That suggests that a non-cached page is about 23% slower than a cached version, if I've done my math correctly. While that might seem huge, you have to also consider just how fast a cached page loads.

Google [has said](https://twitter.com/dannysullivan/status/745732303175835649) that AMP pages load in "two eye blinks," which translates into about 2/3 of a second. The non-cached page being 23% slower means it'll load in about a second. That's still super fast. It's so fast that I'd say most people wouldn't notice the difference.

Using the Pingdom page speed [tool](https://tools.pingdom.com) -- and testing both pages twice -- I got scores like this:

> Cached: 2.52 & 2.38 seconds  
Non-Cached: 554 & 492 milliseconds

With this tool, not using Google's cache actually served the AMP page up about five times faster.

Using another [tool](https://tools.keycdn.com/speed) from Keycdn -- and again testing both pages twice -- I got these scores:

> Cached: 779 & 492 milliseconds  
Non-Cached: 157 & 166 milliseconds

Once again, loading an AMP page through Google's cache seemed to actually slow it down. Not using the cache meant the page loaded two to four times faster.

## Time to ditch the cache?

I went back to Google twice with these findings, to make sure I wasn't missing some type of technical issue that invalidates them. The company never refuted them.

Given this, it's hard to understand why Google doesn't ditch the cache. My best guess is that it's mainly because most publishers haven't complained.

The issue drew some attention back in October after [this blog post](https://www.alexkras.com/google-may-be-stealing-your-mobile-traffic/) complained that Google was somehow stealing mobile traffic from publishers.

That's also went I began asking Google why it doesn't serve AMP pages with a publisher's URL. The concern largely died down, mainly I suspect because it's not like Google is actually stealing traffic. Even the post's original author Alex Kras updated to say he felt his original headline was incorrect.

If you have AMP pages properly configured with analytics, ads and other goodies you might want, the traffic remains essentially yours. The cached URL might be shown, but everything on the page remains in the publisher's control and is served from the publisher's own site. It is your page, except for the URL.

As for the URL, it will redirect to a publisher's site, if someone tries to go to it directly (though as a 302 "temporary" redirect, rather than a 301 "permanent," which I feel would be better). AMP pages themselves also carry a form of source attribution in their [canonical tags](http://searchengineland.com/canonical-chaos-doubling-duplicate-content-264078). Should someone share an article using options within the actual article, the publisher's URL is used.

Google also [said](https://twitter.com/cramforce/status/794585395056939009) in November that it was exploring changes that might mitigate publisher concerns, such as somehow showing a direct URL to a publisher's page.

Still, the URL issue remains. Direct links still haven't been implemented, making it difficult for those wanting to share or copy a direct URL to obtain it. It also remains worrisome that in the long-term, any bookmarked Google cache URLs could fail to redirect, if Google fails to support this in the future.

Yesterday, the editor-in-chief of [MacStories](https://www.macstories.net/) announced that his publication was abandoning AMP over these types of concerns:

> Today we removed AMP support from MacStories. Our site is already fast, but, more importantly, no one messes with my permalinks. Feels good.
> 
> -- Federico Viticci (@viticci) [December 12, 2016](https://twitter.com/viticci/status/808342804153954305)

## Why Google says it won't change

It's worth noting that if you're using Google's search app on iOS or through the built-in search feature on Android, a publisher's URL is shown, not the Google cache URL. But in a regular browser, it's not. This is something Google told me would be impossible for it to do, if the company wanted to continue to prerender AMP pages and to support features like swiping from one AMP story to the next.

I get why Google would want to make it easy for people to swipe through stories, but from what I can tell, this is something only supported for AMP stories that appear in Google's "[Top Stories](http://searchengineland.com/google-replaces-news-box-top-stories-desktop-264993)" box for news-related content, not with regular search listings. There's no reason I can see that it has to go with a Google cache URL for regular listings.

As for prerendering, as best I can tell, that just is another word for caching. That's Google saying in another way that it can't use a publisher's URL if it wants to serve AMP pages from its supposedly faster cache. But given that the cache either isn't that much faster or potentially slower, this feels odd.

## Why Google should offer a choice

In the end, I think Google should leave the choice to publishers.

Those who don't care about the URL that is shown can go with the Google cache and trust that Google says their pages will load more quickly.

For those who want their own URLs to show, Google should come up with mechanism within AMP allowing for this to be indicated, something similar to how meta tags [exist](https://support.google.com/webmasters/answer/35624?hl=en) to indicate if a publisher prefers their own page description over those from the Open Directory.

AMP on its own is super fast, even without caching. Giving publishers the choice would hardly impact speed, yet it would engender a great deal of trust among publishers who are wary of a Google-backed project that, on the face of it, seems to rob them of their own URLs.

Search Engine Land's [SMX West](http://marketinglandevents.com/smx/west/?utm_source=sel&utm_medium=module&utm_campaign=smx+west+2017&utm_content=expo+text) is returning to San Jose in 2017! We're celebrating 10 years of providing proven tactics, networking, industry-leading vendor solutions and demos, and top notch conference amenities to hard core SEOs and SEMs. If you're looking to feed your obsession with SEO and SEM, then make it a priority to attend SMX West in March. We [guarantee](http://marketinglandevents.com/smx/west/guarantee/?utm_source=sel&utm_medium=module&utm_campaign=smx+west+2017&utm_content=expo+text) your investment will be worth it. [Past attendees rave](http://marketinglandevents.com/smx/west/testimonials/?utm_source=sel&utm_medium=module&utm_campaign=smx+west+2017&utm_content=expo+text) about SMX West, and so will you! [Register today](http://marketinglandevents.com/smx/west/rates/?utm_source=sel&utm_medium=module&utm_campaign=smx+west+2017&utm_content=expo+text) to take advantage of super early bird rates, our lowest rates available.
