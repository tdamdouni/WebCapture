# I Left My System Fonts in San Francisco

_Captured: 2015-12-09 at 12:23 from [furbo.org](http://furbo.org/2015/07/09/i-left-my-system-fonts-in-san-francisco/)_

Apple is working on a lovely new system font for both iOS and OS X. We first saw the San Francisco font on the Apple Watch: we'll soon be seeing it on [all of Apple's devices](https://developer.apple.com/fonts/).

As a developer, there are often cases where we need to use the system font on web pages. Many times these pages are embedded in our apps and manage things like remote settings or documentation. In these contexts, matching the content to what the customer sees in their surrounding environment makes a big impact on the user experience. Think about how out of place an app feels when it displays Sparkle release notes in Lucida Grande while running on Yosemite.

We'll soon be faced with a lot of surrounding content that's displayed in San Francisco and will need ways to specify that same font in our CSS. It turns out that's not a simple thing to do.

Traditionally, we've specified fonts explicitly. Something like this could be used to get San Francisco:
    
    
    body {
      font-family: "San Francisco", "Helvetica Neue", "Lucida Grande";
    }
    

Unfortunately, on a fresh install of OS X 10.11 (El Capitan) there's no San Francisco font installed:

![All Fonts on El Capitan](http://furbo.org/wp-content/uploads/2015/07/All-Fonts-ElCap.png)

> _But it's the system font, so how is this possible?_

Apple has started abstracting the idea of a system font: it doesn't have a publicly exposed name. They've also stated that any private names are subject to change. These private names all begin with a period: the Ultralight face for San Francisco is named ".SFNSDisplay-Ultralight". To determine this name, you need to dig around in the font instances returned by NSFont or UIFont; it's not easy by design.

The motivation for this abstraction is so the operating system can make better choices on which face to use at a given weight. Apple is also working on font features, such as selectable "6″ and "9″ glyphs or non-monospaced numbers. It's my guess that they'd like to bring these features to the web, as well.

As a part of this abstraction, there's now a new generic family name: `-apple-system`. The markup looks like this:
    
    
    body {
      font-family: -apple-system, "Helvetica Neue", "Lucida Grande";
    }
    

Unfortunately, it's very poorly documented. Most of the information I've found about this name comes from the [WebKit source code](https://github.com/WebKit/webkit/blob/master/Source/WebCore/platform/graphics/ios/FontCacheIOS.mm). It certainly feels like work-in-progress.

Another disappointment is that this generic family name only works in Safari. Of course you wouldn't expect Google to support an "-apple" prefix, but the WebKit source also shows a `-webkit-system-font`. Since the latest version of Chrome is based on a fork of WebKit, it's not surprising that it's ignored by Blink.

Adding to the confusion, Safari on iOS has added system font styles that match the Dynamic Type feature. These keywords can be used on iOS 7 and later:
    
    
    -apple-system-headline1
    -apple-system-headline2
    -apple-system-body
    -apple-system-subheadline1
    -apple-system-subheadline2
    -apple-system-footnote
    -apple-system-caption1
    -apple-system-caption2
    -apple-system-short-headline1
    -apple-system-short-headline2
    -apple-system-short-body
    -apple-system-short-subheadline1
    -apple-system-short-subheadline2
    -apple-system-short-footnote
    -apple-system-short-caption1
    -apple-system-tall-body
    

Since OS X doesn't have a way to adjust type dynamically, these keywords are unavailable on the desktop ([source](https://github.com/WebKit/webkit/blob/88c1510b3a4f3993307f404b1893426951ac05de/Source/WebCore/css/CSSValueKeywords.in)). Of course, there's no support in Chrome either.

Also note that these keywords won't work in your `font-family` definitions; they only work when used with `font`. If you'd like to learn more about this functionality, these tutorials by the [ChocolateScript developers](http://wobbabits.tumblr.com/post/100005780037/dynamic-fonts-for-ios-web-apps) and [Thomas Fuchs](http://mir.aculo.us/2013/09/16/how-to-create-a-web-app-that-looks-like-a-ios7-native-app-part-1/) are very helpful.

If you're a designer or developer who works on Apple devices, chances are good that you've installed the San Francisco font manually. Don't get fooled like I did: most of the folks that visit your site won't have these fonts installed. Also, Apple's license for San Francisco limits redistribution, so it can't be used as a web font. (And you agreed to this license before downloading the font.)

So what's a coder to do?

If you know that your content will only appear in an Apple browser or web view, the markup is pretty simple:
    
    
    body {
      font-family: -apple-system, "Helvetica Neue", "Lucida Grande";
    }
    

You'll get the system font on the most current browsers and a fallback to Helvetica Neue or Lucida Grande on older systems.

If Chrome or another browser is a part of the picture, I'd suggest the following:
    
    
    body {
      font-family: system, -apple-system,
          ".SFNSDisplay-Regular", "Helvetica Neue", "Lucida Grande";
    }
    

The ".SFNSDisplay-Regular" is the private font name for the regular face of San Francisco in the current beta release (remember, it can change at any time!)

The "system" generic family name doesn't currently exist, but I'd encourage browser manufacturers to adopt this technique. It would be helpful for coders on all platforms. On Android, Roboto or Noto could be selected as needed. On operating systems like Windows, where the user can choose their system font, the automatic selection would make content fit in more easily.

Before closing, I'd like to point out [the HTML and CSS I used for doing this research](http://furbo.org/stuff/systemfonts.html). If you're not running El Capitan yet, this is is how that markup looks in Safari:

![Test Page shown in Safari running on El Capitan](http://furbo.org/wp-content/uploads/2015/07/Safari-ElCap.png)

> _And the same page rendered in Chrome:_

![Test Page shown in Chrome running on El Capitan](http://furbo.org/wp-content/uploads/2015/07/Chrome-ElCap.png)

> _[Test Page shown in Chrome running on El Capitan](http://furbo.org/wp-content/uploads/2015/07/Chrome-ElCap.png)_

The purple line of sample text displays correctly on both browsers using the "hybrid" hack I've shown above. That text will also display in Helvetica Neue on Yosemite (10.10) and Lucida Grande on Mavericks (10.9).

As Apple starts to roll out the new software releases that feature San Francisco, I hope the information presented here will be of help. [Enjoy!](https://www.youtube.com/watch?v=r6DUwMnDxEs)

"[-apple-system"](https://bugs.webkit.org/show_bug.cgi?id=146860), not "-apple-system-font"; I've updated the post accordingly. Also, as I suspected, this change is very much a work in progress and the team is aware that there needs to be [more documentation](https://twitter.com/xeenon/status/619616436596551680). They also reminded me that Chrome is now based on the Blink fork of WebKit, so I've clarified that as well.

**Updated July 14th, 2015:** Some folks have suggested using "sans-serif" to get the system font on El Capitan. My testing shows that all browsers on all versions of OS X render this generic font name in Helvetica (**not** Helvetica Neue.) Also many browsers give users ways to override this default font. I also updated the sample code so that it works better with Firefox.

**Updated July 27th, 2015:** Apple's Surfin' Safari blog has [more information on the new "-apple-system" CSS value](https://www.webkit.org/blog/3709/using-the-system-font-in-web-content/) for `font-family`. It also looks like they're working with the W3C to [standardize a "system" generic font family](https://lists.w3.org/Archives/Public/www-style/2015Jul/0169.html).
