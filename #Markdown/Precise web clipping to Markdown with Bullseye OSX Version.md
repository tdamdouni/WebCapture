# Precise web clipping to Markdown with Bullseye

Jul 30th, 2013 [ : ** : [nvALT][1]**]

[GrabLinks][2] went over pretty well, so I've been motivated to finish up a similar project I had going. It's called Bullseye, and it lets you click a section of a webpage and ["Markdownify"][3] just that content. It's like [Readability][4], but you get to just tell it which part is the good stuff.

I improved the rollover highlighting so that it doesn't highlight every parent element, just the one it's actually going to grab. I added this fix to GrabLinks as well, so if you have that installed you should already be seeing the improvement. Like GrabLinks, Bullseye loads from [a GitHub Gist][5] and will "auto-update" when I make changes. No need to keep reinstalling it.

I also improved the relative-url-to-absolute tricks, so images in the page that are locally linked will still work when you preview the Markdown elsewhere. It does some basic stripping of Twitter and App.net share links as well, but nothing terribly complete.

### Installation

Just drag the link below to your bookmarks bar. If that causes trouble, just right click it and copy the link, then create a new bookmark and paste it in as the link.

[Bullseye][6]

### Using Bullseye

Making use of it is simple. On a page containing content you'd like to clip for later or archiving, just click the Bullseye bookmarklet in your menu bar and then hover over the page. Once it loads, you'll see red outlines follow your cursor around. Position your mouse so that the red outline surrounds the content you want (and nothing beyond it), then click. A second later you'll be looking at a Markdown version, ready to copy and paste. If you're using nvALT, just open it and type V to create a new note.

### Technical details

It's kind of a cool trick. I was running into really messy situations just grabbing innerHTML from the clicked elements, mostly because of the dynamic nature of the web and the amount of crud stuck in the DOM. I needed the raw source code for that element. I ended up parsing up the tree and generating a selector for the target element using available ids, classes, tag names and indexes translated to `:nth-of-type` or `:first`. Then I just pass that to jQuery.load and get the source fragment I need. On the off chance that that fails or the site's content is Ajax-loaded and not in the source, it falls back to innerHTML.

I originally planned this to be Ajax and not leave the page (like GrabLinks), but the request URIs got too large in many cases and I had to switch to generating a temporary form, filling in the values and submitting it to Marky. It works.

### Future

I need to add a couple parameters to the Marky API to allow passing a title manually. It usually extracts them from the source, but that's useless when sending HTML snippets. I should be able to stick that in soon and will update the bookmarklet at that point.

Marky can also return and optionally execute nvALT urls, so I'd like a version of Bullseye that just put notes straight into nvALT with the right titles. That's next after actually getting the right titles.

Follow the author on [Twitter][7] and [App.net][8].
This content is [supported by readers like you.][9]

Topics: [bookmarklet][10], [javascript][11], [markdown][12]

## Related posts:

* [Bullseye 0.3][13]
* [Marker, Grablinks, and Bullseye fixes][14]
* [Marker: Web selections to Markdown][15]
* [Bookmarklet: Clean highlighted code for copying][16]
* [Similarity bookmarklet update][17]
* [Grab sibling links with the Similarity bookmarklet][18]

[1]: http://brettterpstra.com/2013/07/30/precise-web-clipping-to-markdown-with-bullseye/# "Add Precise web clipping to Markdown with Bullseye to nvALT"
[2]: http://brettterpstra.com/2013/07/04/grablinks-bookmarklet-2-dot-0/
[3]: http://brettterpstra.com/2012/06/20/marky-the-markdownifier-reintroductions/
[4]: http://lab.arc90.com/2009/03/02/readability/
[5]: https://gist.github.com/ttscoff/6109434
[6]: http://brettterpstra.com/2013/07/30/precise-web-clipping-to-markdown-with-bullseye/javascript:(function(){var p=document.createElement("p");p.innerHTML="Loading…";p.id="loadingp";p.style.padding="20px";p.style.background="#fff";p.style.left="20px";p.style.top=0;p.style.position="fixed";p.style.zIndex="9999999";p.style.opacity=".85";document.body.appendChild(p);document.body.appendChild(document.createElement("script")).src="//d2z4mgf8zqkbu2.cloudfront.net/bookmarklets/bullseye.js?x="+(Math.random());})();
[7]: http://twitter.com/ttscoff/
[8]: http://alpha.app.net/ttscoff/
[9]: http://brettterpstra.com/support
[10]: http://brettterpstra.com/topic/bookmarklet/
[11]: http://brettterpstra.com/topic/javascript/
[12]: http://brettterpstra.com/topic/markdown/
[13]: http://brettterpstra.com/2013/08/01/bullseye-03/
[14]: http://brettterpstra.com/2014/06/23/marker-grablinks-and-bullseye-fixes/
[15]: http://brettterpstra.com/2013/12/22/marker-web-selections-to-markdown/
[16]: http://brettterpstra.com/2015/12/01/bookmarklet-clean-highlighted-code-for-copying/
[17]: http://brettterpstra.com/2015/09/29/similarity-bookmarklet-update/
[18]: http://brettterpstra.com/2015/09/28/grab-sibling-links-with-the-similarity-bookmarklet/
