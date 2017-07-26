# Deleting RSS Feed Items

_Captured: 2015-11-30 at 20:01 from [oleb.net](http://oleb.net/blog/2015/11/rss-feed-item-deletions/)_

A few months ago I accidentally hit the _Publish_ button on an article for this site too early. I ended up publishing a post that had a title but no other text. When a reader notified me about my mistake a few minutes later, I immediately deleted the page. That fixed things on my site, but unfortunately did not reverse all the damage. Several [feed aggregators](https://en.wikipedia.org/wiki/News_aggregator) had already fetched my [feed](https://en.wikipedia.org/wiki/Web_feed) while the empty article was up, and readers were seeing this:

[ ![Screenshot of ReadKit showing my empty article](http://oleb.net/media/readkit-screenshot-empty-article.png) ](http://oleb.net/media/readkit-screenshot-empty-article.png)

> _The empty article appeared in my readers' feed readers although it had long been deleted._

I hate when this happens because I value the quality of my feed. (For example, I make sure [my feed doesn't show old items](http://oleb.net/blog/2014/01/preserving-rss-feed-read-status/) when I switch to a new blogging system.)

# No good way to signal deletions to feed aggregators

The problem is that there is seemingly no good way to tell a news aggregator that a feed item has been deleted. [I tweeted at the time](https://twitter.com/olebegemann/status/644955305906937857) that aggregators could (should?) probably be smarter about this than they currently are:

> … I think it could be handled more intelligently. E.g. if the latest item vanishes but the one before that is still there it's very likely that the former got deleted. 

But it is a difficult problem. Simply removing an entry from the feed (as I had done by deleting the article) is not enough because feeds commonly only include the most recent posts, so 99.999% of the time the fact that an item is no longer in the feed does _not_ mean it has been deleted at the source.

# Quick fix

I ended up re-adding an entry for the empty article to my feed with an updated title and body text that made it clear to readers they should ignore this post. When you do this, it is important to use the same item ID as the deleted item and to specify an updated-at date so that feed aggregators parse it again.

To handle this state in my blog engine, [Middleman](https://middlemanapp.com), I introduced a new `status` field. Articles whose `status` is `deleted` are not published to the site but still included in the feed. The Markdown file for the deleted post looks like this:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    
    
    ---
    title: "[DELETED]"
    created_at: 2015-09-18 17:00:00 +02:00
    updated_at: 2015-09-19 22:14:00 +02:00
    author: "OleBegemann"
    status: "deleted"
    ---
    
    (This post was accidentally published and has now been deleted. Sorry.)
    

It's not a perfect solution, but way better than something that looks like a real article but 404s when readers follow the URL.

# A better solution

I later learned that there is in fact a standard for handling this exact situation, at least for [Atom](https://en.wikipedia.org/wiki/Atom_\(standard\)). [RFC 6721](https://tools.ietf.org/html/rfc6721) proposes a `deleted-entry` element as an extension to the Atom format. Consumers of the feed are expected to delete items whose `deleted-entry` date is later than the corresponding item's published or updated date. Importantly, the original `entry` element for the item remains in the feed so the feed remains backward compatible.

As far as I know, there exists no similar proposal for [RSS](https://en.wikipedia.org/wiki/RSS). And to my knowledge, no popular news aggregator service or app currently supports the Atom extension. Nonetheless, I added support for deleted entries to my feed. This is how it looks:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    
    
    <feed xmlns="http://www.w3.org/2005/Atom"
          xmlns:at="http://purl.org/atompub/tombstones/1.0"
          xml:base="http://oleb.net">
      …
      <at:deleted-entry
        ref="http://oleb.net/blog/2015/09/custom-pattern-matching-in-swift/"
        when="2015-09-19T20:14:00Z"/>
      …
    

And both NewsBlur and Feedbin at least [expressed interest](https://twitter.com/NewsBlurSupport/status/644967769390321664) in the idea [on Twitter](https://twitter.com/feedbin/status/644977704161312768). I'd love to see this catch on.
