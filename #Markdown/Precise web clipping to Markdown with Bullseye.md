# Precise web clipping to Markdown with Bullseye

_Captured: 2015-09-30 at 22:18 from [brettterpstra.com](http://brettterpstra.com/2013/07/30/precise-web-clipping-to-markdown-with-bullseye/)_

[GrabLinks](http://brettterpstra.com/2013/07/04/grablinks-bookmarklet-2-dot-0/) went over pretty well, so I've been motivated to finish up a similar project I had going. It's called Bullseye, and it lets you click a section of a webpage and "[Markdownify"](http://brettterpstra.com/2012/06/20/marky-the-markdownifier-reintroductions/) just that content. It's like [Readability](http://lab.arc90.com/2009/03/02/readability/), but you get to just tell it which part is the good stuff.

I improved the rollover highlighting so that it doesn't highlight every parent element, just the one it's actually going to grab. I added this fix to GrabLinks as well, so if you have that installed you should already be seeing the improvement. Like GrabLinks, Bullseye loads from [a GitHub Gist](https://gist.github.com/ttscoff/6109434) and will "auto-update" when I make changes. No need to keep reinstalling it.

I also improved the relative-url-to-absolute tricks, so images in the page that are locally linked will still work when you preview the Markdown elsewhere. It does some basic stripping of Twitter and App.net share links as well, but nothing terribly complete.

### Installation

Just drag the link below to your bookmarks bar. If that causes trouble, just right click it and copy the link, then create a new bookmark and paste it in as the link.

### Using Bullseye

Making use of it is simple. On a page containing content you'd like to clip for later or archiving, just click the Bullseye bookmarklet in your menu bar and then hover over the page. Once it loads, you'll see red outlines follow your cursor around. Position your mouse so that the red outline surrounds the content you want (and nothing beyond it), then click. A second later you'll be looking at a Markdown version, ready to copy and paste. If you're using nvALT, just open it and type V to create a new note.

### Technical details

It's kind of a cool trick. I was running into really messy situations just grabbing innerHTML from the clicked elements, mostly because of the dynamic nature of the web and the amount of crud stuck in the DOM. I needed the raw source code for that element. I ended up parsing up the tree and generating a selector for the target element using available ids, classes, tag names and indexes translated to `:nth-of-type` or `:first`. Then I just pass that to jQuery.load and get the source fragment I need. On the off chance that that fails or the site's content is Ajax-loaded and not in the source, it falls back to innerHTML.

I originally planned this to be Ajax and not leave the page (like GrabLinks), but the request URIs got too large in many cases and I had to switch to generating a temporary form, filling in the values and submitting it to Marky. It works.

### Future

I need to add a couple parameters to the Marky API to allow passing a title manually. It usually extracts them from the source, but that's useless when sending HTML snippets. I should be able to stick that in soon and will update the bookmarklet at that point.

Marky can also return and optionally execute nvALT urls, so I'd like a version of Bullseye that just put notes straight into nvALT with the right titles. That's next after actually getting the right titles.
