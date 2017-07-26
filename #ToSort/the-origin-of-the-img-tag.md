# The Origin of the IMG Tag

_Captured: 2017-03-09 at 19:13 from [thehistoryoftheweb.com](http://thehistoryoftheweb.com/the-origin-of-the-img-tag/)_

![](http://thehistoryoftheweb.com/wp-content/uploads/1993/04/Mosaic-wmosaic-logo-smaller-800x693.jpg)

NCSA Mosaic was one of the first cross-platform web browsers on the market. It was met with a kind of awe. Within months of its release in the summer of '93, Mosaic had changed the way people thought not only of browsers, but of the World Wide Web in general. Gary Wolfe wrote in _Wired _that Mosaic "gave an intense illusion, not of information, but of personality."

Mosaic made the web more approachable for hundreds of thousands of users who would soon come online for the first time. Sure, Mosaic was easy to install on any operating system. And it was incredibly user friendly. But a big part of this shift just had to be the `img` tag.

Of course, a few months before its release no one knew how successful the browser would be. Mosaic was developed by NCSA at the University of Illinois, spearheaded by the tenacious Marc Andreessen, still an undergraduate there, alongside Eric Bina, an NCSA employee. Andreessen had been interested in the web since it had first been introduced a couple of years earlier.

While developing the first version of Mosaic, he and Bina had lots of ideas. They believed that the future of the web depended on more complete graphics support. At the time, users could access images solely through links. If an image was displayed in a webpage, a user would click on the link and images would open in a new window. Andreessen and Bina imagined a browser where images were inline, right alongside text in web documents. No extra click necessary.

At the time, there were only around 18 HTML elements. And none fit Andreessen's purpose. So in February of 1993, Andreessen popped on to the www-talk mailing list, a popular destination for developers of the web. He [posted a thread](http://1997.webhistory.org/www.lists/www-talk.1993q1/0182.html), and casually suggested a new HTML element:

> I'd like to propose a new, optional HTML tag:
> 
> IMG
> 
> Required argument is SRC="url".

This may seem cavalier to some, and it was. But this was how the web was pushed forward. The web is open after all, isn't it? Even though standards are developed by the W3C, contributions are (in theory) welcome from all.

Still, Andreessen's new `img` tag was met with some opposition. Some worried that arbitrary tags opened the floodgates, and it wouldn't be long before we had an element for every media type, like an `aud` tag for audio (or a `video` tag maybe? That would be just too much).

Tim Berners-Lee, the creator of the World Wide Web, was hesitant too. He suggested that Andreessen instead use the `anchor` tag to display inline images instead of creating something entirely new. This would allow users to set their own preferences for how images should be handled. He saw the web as a customizable experience, and envisioned a world where users would tinker with their browsers to display webpages based on personal preferences. A rigid `img` tag ran against that vision.

Tony Johnson, the sole creator of competing browser _Midas_, had a much simpler objection. He wondered, why should we use the abbreviated version? Wouldn't `image` be just as effective as `img` without the syntactical confusion? He also included a request for a text alternative to images, an early version of what would eventually become the `alt` attribute.

But things didn't end there. As it turns out, Andreessen's email was less of a _suggestion _and more a simple _announcement. _Bina and Andreessen had already planned on including the `img` tag in their release, and had no plans on changing syntax or support. Inline images were a top priority for the browser, and nothing was going to change that.

Once Mosaic went out later in '93, and users and designers alike could start experimenting with inline images, the `img` tag gathered momentum, and fast. The media, and the public, were sold.

HTML Standards caught up eventually. The `img` tag was included in the HTML 2.0 specification released in 1995 by the W3C. Some alternatives were proposed, like the `fig` tag that included the much needed `alt` attribute for users unable to see images. But by that point, `img` had already won.

And it was hard to change its implementation. Even though the new standard added `alt` to `img` elements, Mosaic (by then renamed Netscape) continued to treat `img` as an exclusively visual element. In early implementations, the `alt` attribute even doubled as the tooltip shown to users when they hovered over images. This prompted developers to use the text to tell users what they wanted them to do ("Click Me!") rather then describe the image ("A Horse"). Once the `title` attribute was added to images, they became far more accessible.

So if you're ever wondering why we use `img` and `src` instead of `image `and `source`, and where it all began, you can blame the persistence of the Mosaic engineers. That's why we got the `img` tag, warts and abbreviations and all. Andreessen was first to market, and it's just plain hard to argue with success. It wasn't long before this become a tradition for browsers and standards. Browsers rush to implement first, then standards eventually catch up.This had some pretty serious implications during the "Browser Wars," and since then has had its typical ebbs and flows. But it's a tradition that persists to this day. All because of the humble `img` tag.

### Added to the Timeline

**November 24, 1995 - HTML 2.0**

HTML 2.0 is published as IETF RFC 1866, and includes elements from previous iterations of HTML specifications, as well as some that are brand new. It was seen as the specification from which other implementations should emerge from, and still influences HTML today.

[View the Full Timeline](http://thehistoryoftheweb.com/timeline/)

### Sources

  * Michael Calore. "April 22, 1993: Mosaic Browser Lights Up Web With Color, Creativity." Wired. April 4, 2010. <https://www.wired.com/2010/04/0422mosaic-web-browser/>
  * Mark Pilgrim. "Why do we have an IMG element?." Dive Into Mark. November 11, 2009. <https://web.archive.org/web/20100306055257/http://diveintomark.org/archives/2009/11/02/why-do-we-have-an-img-element>
  * Nathan Zeldes. "A glimpse of the venerable NCSA Mosaic browser." CommonSense Design. May 5, 2008. <http://designblog.nzeldes.com/2008/05/a-glimpse-of-the-venerable-ncsa-mosaic-browser/>
  * Jukka "Yucca" Korpela. "Guidelines on alt texts in img elements." IT and communication. September 1998. <http://www.cs.tut.fi/~jkorpela/html/alt.html#tooltip>
  * Dave Raggett. "A history of HTML." W3. 1998. <https://www.w3.org/People/Raggett/book4/ch02.html>
  * Gary Wolfe. "The (Second Phase of the) Revolution Has Begun." Wired. October 10, 1994. <https://www.wired.com/1994/10/mosaic/>
  * Marc Andresson. "proposed new tag: IMG." WWW-Talk Mailing List. February 2, 1993. <http://1997.webhistory.org/www.lists/www-talk.1993q1/0182.html>
