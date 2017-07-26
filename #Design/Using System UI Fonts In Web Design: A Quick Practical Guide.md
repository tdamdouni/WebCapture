# Using System UI Fonts In Web Design: A Quick Practical Guide

_Captured: 2015-12-09 at 12:32 from [www.smashingmagazine.com](http://www.smashingmagazine.com/2015/11/using-system-ui-fonts-practical-guide/)_

For perhaps the first time since the original Macintosh, we can get excited about using system UI fonts. They're an interesting, **fresh alternative to web typography** -- and one that doesn't require a web-font delivery service or font files stored on your server. How do we use system UI fonts on a website, and what are the caveats?

System UI fonts being amazing kind of snuck up on us. Google has been toiling away at [Roboto](http://www.google.com/design/spec/style/typography.html) with great success (including [regular updates](http://www.fastcodesign.com/3033126/roboto-rebooted-why-google-plans-to-update-its-font-like-the-rest-of-its-products)), Apple made a splash with [San Francisco](https://developer.apple.com/fonts/), and Mozilla asked renowned type designer Erik Spiekermann to create [Fira Sans](http://mozilla.github.io/Fira/). Last but not least, let us not forget about Microsoft. It was Microsoft that restarted conversations about system UI fonts with its original Windows Phone design language (nee Metro), which relied heavily on typography in general, and on a font named [Segoe](https://en.wikipedia.org/wiki/Segoe) in particular.

![The latest generation of system UI fonts and their allegiances](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/11/01-modern-system-fonts-preview.png)[6](http://www.smashingmagazine.com/2015/11/using-system-ui-fonts-practical-guide/)  


> _The latest generation of system UI fonts and their allegiances. (_

No wonder that the idea of using those fonts is spreading through the web world as well. Whether you want your website to feel more like an app, to draw clearer lines between the content and user interface, or to **use modern, beautiful fonts with zero latency**, you might be interested in using system UI fonts on your website.

But it's not as easy as it could be. That's because the CSS support is **curiously schizophrenic**.

(Nomenclature note: I am using "system UI font" here to refer to the font that the user interface of the operating system is rendered in -- distinct from a "system font," a traditional name for any local or platform font that is already present on the user's system and that doesn't need to be included in the website's payload.)

Currently, there are two approaches to making your website use the system UI font for its typography.

Approach A is to use the "magical" shorthand CSS property:
    
    
    font: menu;
    

A [few of these shorthand properties](https://developer.mozilla.org/en-US/docs/Web/CSS/font) have existed for the longest time (`caption`, `icon`, `menu`, `message-box`, `small-caption`, `status-bar`), yet I have never seen them being commonly used.

Approach A has its drawbacks:

  * It **doesn't return a correct font on iOS**, nor in many Android browsers.
  * It's a shorthand, which means it **overrides the font size** (although that can be reset), and it cannot be combined with and does not fall back to anything else.
  * Until December 2015 in Firefox on Mac OS X, it **doesn't use the "smart" properties of San Francisco** (which switches from San Francisco Text to San Francisco Display automatically for text over 20 pixels and adjusts letter spacing).
![Mac OS X system UI fonts over the ages: from Chicago in 1984, through Charcoal and Lucida Grande, to San Francisco on a high-resolution display in 2015](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/11/02-history-mac-preview.png)[9](http://www.smashingmagazine.com/2015/11/using-system-ui-fonts-practical-guide/)  


> _Mac OS X system UI fonts over the ages: from Chicago in 1984, through Charcoal and Lucida Grande, to San Francisco on a high-resolution display in 2015. (_

Approach B is to list fonts by name:
    
    
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue", sans-serif;
    

This, too, has its drawbacks:

  * You'll have to **maintain the list** (and its order). Perhaps system UI fonts won't change as often as they did in the last few years -- but in any case, this is not future-proof.
  * The list targets the most popular browsers and operating systems, but it **doesn't target all of them**.
  * It doesn't yet work in Firefox on Mac OS X El Capitan, resulting in Neue Helvetica being shown, rather than San Francisco. (This is slated to be fixed in December 2015.)
  * This solution is prone to naming conflicts, which led to a very interesting [bug with the system font on Medium](https://medium.com/@mwichary/system-shock-6b1dc6d6596f). Also, for example, Oxygen ([KDE's UI font](https://www.google.com/fonts/specimen/Oxygen)) is the name of [another font](http://www.identifont.com/show?HYN) that people can install, which can lead to [surprises](https://twitter.com/zipboing/status/659744396431261696). Also, if you are a developer and happen to have installed Roboto or Fira Sans on your machine, then this font declaration might use one of those instead of the system's actual UI font.
  * Mac OS 10.0 to 10.9 uses Lucida Grande as the system UI font. Mac OS 10.10 uses Neue Helvetica. However, all versions of Mac OS X have both of these fonts installed. Because the `font-family` declaration works by sequentially going through the list of fonts to find the first one installed, choosing Lucida Grande on some platforms and Neue Helvetica on others is impossible. The first available one listed in the declaration will always be chosen.

You might be inclined to combine approach A with approach B to get the best of both worlds. Unfortunately, this is not easy because the `font` and `font-family` properties are **mutually exclusive** -- one will just override the other. Perhaps media queries can come to the rescue, but that's hacky.

You might also imagine sending different CSS values from the server, depending on the user agent (for example, sending only `font-family: "Fira Sans", sans-serif;` if we know the browser is running on Firefox OS), or doing it via JavaScript. But this seems cumbersome and hard to maintain, and it still doesn't solve all of our problems.

![You can use the system UI font just for the user interface \(on the left, medium.com\) or for the entire website \(on the right, colepeters.com\). Note, however, that many system UI fonts are not optimized for longer content.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/11/03-two-sites-preview.png)[15](http://www.smashingmagazine.com/2015/11/using-system-ui-fonts-practical-guide/)  


> _[You can use the system UI font just for the user interface (on the left, medium.com) or for the entire website (on the right, colepeters.com). Note, however, that many system UI fonts are not optimized for longer content.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/11/03-two-sites.png)_

I work at Medium, and currently we use approach B:
    
    
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue", sans-serif;
    

We chose this approach because it seems to have fewer major problems. (Approach A fails in mobile browsers in ways that are unacceptable. Approach B fails, too, but less often and with fewer consequences. Your mileage may vary.)

You and I can make this even better together. The box below uses the declaration above and should render in your system's UI font. If it doesn't or if you have any thoughts, please leave a comment!

> This should be rendered in your system's UI font.  
The quick brown fox jumps over the lazy dog.

Here are the currently known problems with this approach:

  * At least until December 2015, this solution doesn't render San Francisco in Firefox on Mac OS X, but rather falls back to Neue Helvetica.
  * It doesn't render Lucida Grande on pre-Yosemite versions of Mac OS X, falling back to Neue Helvetica. And it might not match the correct font on less popular operating systems or more complicated configurations.

If you are interested in the details, let's work through how this list got to look the way it does:
    
    
    font-family:
      -apple-system, BlinkMacSystemFont,
      "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans",
      "Helvetica Neue", sans-serif;
    

The first grouping is CSS properties that map to the system's UI font. That covers a lot of ground, and there is no chance that these fonts will be mistaken for something else:

  * `-apple-system` targets San Francisco in Safari on Mac OS X and iOS, and it targets Neue Helvetica and Lucida Grande on older versions of Mac OS X. It properly selects between San Francisco Text and San Francisco Display depending on the text's size.
  * `BlinkMacSystemFont` is the equivalent for Chrome on Mac OS X.

The second grouping is for known system UI fonts:

  * `Segoe UI` targets Windows and Windows Phone.
  * `Roboto` targets Android and newer Chrome OS'. It is deliberately listed after Segoe UI so that if you're an Android developer on Windows and have Roboto installed, Segoe UI will be used instead.
  * `Oxygen` targets KDE, `Ubuntu` targets… well, you can guess, and `Cantarell` targets GNOME. This is beginning to feel futile because some Linux distributions have many of these fonts.
  * `Fira Sans` targets Firefox OS.
  * `Droid Sans` targets older versions of Android.
  * Note that we don't specify San Francisco by name. On both iOS and Mac OS X, San Francisco isn't obviously accessible, but rather exists as a "hidden" font.
  * We also don't specify San Francisco using `.SFNSText-Regular`, the internal PostScript name for San Francisco on Mac OS X. It only works in Chrome and is less versatile than `BlinkMacSystemFont`.

The third grouping is our fallback fonts:

  * `Helvetica Neue` targets pre-El Capitan versions of Mac OS X. It is listed close to the end because it's a popular font on other non-El Capitan computers.
  * `sans-serif` is the default sans-serif fallback font.
![The evolution of Windows’ system UI font is even more drastic than Mac OS X’s — from monospaced bitmapped fonts in Windows 1.0 in 1985 to the high-resolution Segoe UI in Windows 10.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/11/04-history-win-preview.png)[19](http://www.smashingmagazine.com/2015/11/using-system-ui-fonts-practical-guide/)  


> _The evolution of Windows' system UI font is even more drastic than Mac OS X's -- from monospaced bitmapped fonts in Windows 1.0 in 1985 to the high-resolution Segoe UI in Windows 10. (_

There's still work to do. Everything we've covered works only for Western typography. Also, if you want to adjust the padding or line height according to the UI font that your website is using, then you'll have to use the hybrid approach above or else [detect the font after rendering](https://www.bramstein.com/writing/detecting-system-fonts-without-flash.html).

Still, the early results are already good enough. Hopefully, in the future, all of this will become less complicated. If any of this is important to you, please [tell browser vendors!](http://www.smashingmagazine.com/2011/09/help-the-community-report-browser-bugs/)

![The last three versions of Mac OS X use three different system UI fonts: Lucida Grande on Mac OS 10.9 \(Mavericks\); a special version of Neue Helvetica on Mac OS 10.10 \(Yosemite\); and a special version of San Francisco on Mac OS 10.11 \(El Capitan\). It’s safe to assume that future versions will continue using San Francisco.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/11/05-recent-mac-os-preview.png)[23](http://www.smashingmagazine.com/2015/11/using-system-ui-fonts-practical-guide/)  


> _The last three versions of Mac OS X use three different system UI fonts: Lucida Grande on Mac OS 10.9 (Mavericks); a special version of Neue Helvetica on Mac OS 10.10 (Yosemite); and a special version of San Francisco on Mac OS 10.11 (El Capitan). It's safe to assume that future versions will continue using San Francisco. (_

_Thanks to John Daggett, Michael Duggan, Kenneth Ormandy and Emil Eklund for their help with this article._

_(vf, al)_
