# Unresponsive

_Captured: 2015-11-24 at 23:21 from [leancrew.com](http://leancrew.com/all-this/2015/10/unresponsive/)_

[This post](http://www.mcelhearn.com/use-safaris-responsive-design-mode-in-el-capitan/) from last week by Kirk McElhearn and [this followup](http://mjtsai.com/blog/2015/10/04/safaris-responsive-design-mode/) today by Michael Tsai reminded me that Safari 9 has a new feature in the Develop menu: Responsive Design Mode. Unfortunately, it's not as smart as I'd hoped it would be. Or maybe I'm not.

The idea behind RDM is to let web designers see what a site looks like on smaller (Apple) screens without continually resizing windows or reloading pages on other devices. You can see how it looks by just clicking a button associated with the device of interest. And, unlike [pinned sites](http://www.macworld.com/article/2947543/browsers/hands-on-with-safari-9-in-el-capitan-little-changes-make-a-big-difference.html), this feature is available on Safari 9 even if you're still running Yosemite.

I'm not a web designer, but I am responsible for this site, and I do occasionally fiddle with its layout. I (finally!) made a mobile layout back in June, and it would have been much easier if I'd been able to see the results of my CSS changes immediately on my Mac as I made them.

But I soon found that RDM doesn't really emulate smaller devices. Here's what my site looks like on my iPhone 5s:

![iPhone 5s view](http://leancrew.com/all-this/images2015/20151004-iPhone%205s%20view.png)

> _And here's what it looks like in Safari RDM:_

![Safari Responsive Design Mode](http://leancrew.com/all-this/images2015/20151004-Safari%20Responsive%20Design%20Mode.png)

> _Not exactly a faithful representation. And it's no better in landscape._

![iPhone 5s landscape view](http://leancrew.com/all-this/images2015/20151004-iPhone%205s%20landscape%20view.png)

> _iPhone 5s landscape view_

![Safari RDM landscape](http://leancrew.com/all-this/images2015/20151004-Safari%20RDM%20landscape.png)

> _Safari RDM landscape_

I assume this is at least partially because I don't really know what I'm doing. I have two CSS files for the site: the original `style.css` that's meant for wider screens and `mobile.css` that's meant for narrower screens. The file used is controlled by these three lines in the `<head>`:
    
    
    <link rel="stylesheet" type="text/css" media="all and (max-device-width:480px) and (orientation:portrait)" href="resources/mobile.css" />
    <link rel="stylesheet" type="text/css" media="all and (max-device-width:480px) and (orientation:landscape)" href="resources/style.css" />
    <link rel="stylesheet" type="text/css" media="all and (min-device-width:480px)" href="resources/style.css" />

So I'm really choosing the style file on the basis of the device's width, not the view's width. This is a simple solution, and it works, even though it isn't fully responsive. If you're reading this on a phone and rotate it, the layout will change; but if you're reading this on a notebook or desktop computer and make the browser window narrow, the layout won't change.

I don't really want to mess with the site's layout again, and I certainly wouldn't do so just to get it to work in Safari's RDM, but there are two things that'll probably force me into it: iOS 9's Slide Over and Split View on iPads. I'm pretty sure those views don't change the `device-width`, and if I want the site to display its narrow layout when it's in those modes, I'll have to make it truly responsive.

Eventually. I'm not particularly responsive, either.
