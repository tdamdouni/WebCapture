# iOS 9 and Safari View Controller: The Future of Web Views

_Captured: 2015-06-24 at 22:04 from [www.macstories.net](http://www.macstories.net/stories/ios-9-and-safari-view-controller-the-future-of-web-views/)_

![](https://cd336977afb0dc8522f0-3b1073ac6adc6b2fffddbe35a528b598.ssl.cf1.rackcdn.com/Photo-2015-06-24-14-44-9p8BeYnfFs4mFDZzU4rx1BWK2jwfpkSIlT.jpg)

For a long time, iOS apps have been able to open links as web views. When you tap a link in a Twitter client, an RSS reader, or a bookmark utility, it usually opens in a mini browser that doesn't leave the app, providing you with the convenience of not having to switch between Safari and the app. For years, in spite of some security concerns, this worked well and became the de-facto standard among third-party iOS apps.

With iOS 9, Apple wants this to change - and they're bringing the power of Safari to any app that wants to take advantage of it.

## Web Views

The history of iOS has seen a complicated history between apps and the web. Since the inception of the App Store in 2008 and the first third-party apps - back when iOS was called [iPhone OS](https://en.m.wikipedia.org/wiki/History_of_iOS) - Apple has allowed developers to display web content in their apps. Web views were, in most cases, webpages displayed in the context of an app and they were handled by a simple API, [UIWebView](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIWebView_Class/). By not having to open links in Safari, developers were able to augment their apps with rich web functionality; in return, users could view webpages in the app they were into, often enjoying custom features added by developers such as sharing buttons, navigation between pages, and even special readability modes to declutter websites and make them more pleasant on mobile.

With the release of [iOS 4.3 in early 2011](http://www.macstories.net/news/apple-releases-ios-4-3-direct-links/), Apple introduced Nitro, a faster, just-in-time ([JIT](https://en.m.wikipedia.org/wiki/Just-in-time_compilation)) JavaScript engine for Safari that considerably sped up the browser's performance in loading complex webpages. Nitro was exclusive to Safari: third-party developers couldn't benefit from the faster performance in their web views based on UIWebView, and this led many to believe that it was a calculated move to encourage usage of Safari over web views and web apps saved to the iPhone's Home Screen.

In a widely circulated article, [The Register wrote](http://www.theregister.co.uk/2011/03/15/apple_ios_throttles_web_apps_on_home_screen/) that Apple was "handcuffing" open web apps with Safari-only Nitro. As [Daring Fireball's John Gruber noted](http://daringfireball.net/2011/03/nitro_ios_43), however, Apple's decision to restrict Nitro was likely motivated by its nature: Nitro's JIT engine was designed to mark pages stored in RAM as executable, something that third-party apps couldn't enable due to security reasons. As is often the case with new features on iOS, Apple was willing to trade off _some_ security for higher performance, but only in the browser under their direct control.

From 2011 until 2014, the exclusivity of Nitro to Safari created a disparity between Apple's browser and web views accessed from apps. Simply put: web apps and web views performed just as well as before, but Safari was _faster_ thanks to Nitro. For users, this resulted in slower loading times when viewing webpages in third-party apps, such as links opened from Twitter and Facebook.

![Web views in Twitterrific, NewsBlur, and Instapaper.](http://48ce6c28e7bf5f42a1b7-2712e00ea34e3076747650c92426bbb5.r89.cf1.rackcdn.com/2015-06-24-142252.jpeg)

> _Web views in Twitterrific, NewsBlur, and Instapaper._

At WWDC 2014, Apple announced [WKWebView](https://developer.apple.com/library/ios/documentation/WebKit/Reference/WKWebView_Ref/), a new API that could allow developers to display web content in custom web views with the same performance benefits of Safari. Designed with security in mind, WKWebView featured the same Nitro engine of Safari, responsive 60fps scrolling, and built-in gestures - all while still giving developers the opportunity to customize a web view with their own UI and features.

[NSHipster called WKWebView](http://nshipster.com/wkwebkit/) "the centerpiece of the modern WebKit API introduced in iOS 8 & OS X Yosemite"; [developers at Telerik noted](http://developer.telerik.com/featured/why-ios-8s-wkwebview-is-a-big-deal-for-hybrid-development/) that it would be "a big deal" for hybrid development of native apps and web views.

WKWebView was indeed a big change: after three years, web views in iOS apps could be just as fast as webpages opened in Safari, and thousands of developers quickly updated their apps to take advantage of it. To this day, iOS 8's WKWebView is used in a vast amount of apps that display webpages, with a better user experience for users who have come to expect the speed of Safari anywhere on iOS.

Still, in spite of the legacy UIWebView and last year's WKWebView, web views on iOS still aren't on par with the years of polish and evolution that Apple put into Safari. Among [security concerns for web authentication](http://furbo.org/2014/09/24/in-app-browsers-considered-harmful/) and limitations such as the inability to access the system autofill and iCloud Keychain, traditional web views don't offer the same flexibility of Safari, requiring users to manually switch to the full browser for functionalities that apps can't embed on their own.

[Alex Price](https://mobile.twitter.com/alexjprice), indie developer at [Homegrown Software](http://homegrownsw.com/), noted that there are advantages to redirecting users to Safari, but a lot of apps prefer the in-app web view approach, and since "most in-app browsers don't have as nice an interface as Safari and most don't clearly display the URL of the page being visited", this could be an issue for phishing attempts as well as consistency in the user interface.

[FutureTap](http://www.futuretap.com/apps/whereto/)'s [Ortwin Gentz](https://mobile.twitter.com/ortwingentz?p=s), creator of navigation app [Where To?](https://itunes.apple.com/us/app/where-to-find-best-places/id903955898?mt=8&uo=4&at=10l6nh&ct=ms_inline), also added that custom mini browsers and web views in apps most likely lack "some features such as a nice progress bar or the lock icon to indicate a secure connection" - other downsides that contribute to a confusing experience when compared to the consistency and feature set of Safari.

As [Bryan Irace](https://mobile.twitter.com/irace), iOS developer at Tumblr, pointed out in our conversation earlier this week, "in-app web views have always been a compromise". While users get to stay in the current app, he said, they "don't have access to any of their cookies, and put themselves at risk by entering sensitive information into a web view controlled by a third-party who users may not necessarily trust".

With iOS 9, Apple wants to provide an easy solution to all these potential issues and pitfalls. And if my initial discussions with developers for the past two weeks are of any indication, it looks like we're going to see this feature being widely adopted later this year.

## Safari View Controller

Apple is introducing a Safari View Controller on iOS 9. Created with the goal to let developers stop writing miniature web browsers, Safari View Controller enables apps to delegate the responsibility of showing web content to Safari itself, avoiding the need to write custom code for built-in browsers.

![Safari View Controller in action.](http://48ce6c28e7bf5f42a1b7-2712e00ea34e3076747650c92426bbb5.r89.cf1.rackcdn.com/2015-06-24-135453.jpeg)

> _Safari View Controller in action._

In a technical session at WWDC, Apple detailed how Safari View Controller has been closely modeled after Safari with consistency and quick interactions in mind. Safari View Controller looks a lot like Safari: when users tap a web link in an app that uses Safari View Controller, they'll be presented with a Safari page that displays the address bar at the top and other controls at the bottom or next to it - just like the regular Safari on the iPhone and iPad. There are two minor visual differences with Safari: when opened in Safari View Controller, the URL in the address bar will be grayed out to indicate it's in read-only mode; and, a Safari button is available in the toolbar, so that users will be able to quickly jump to Safari if they want to continue navigation in the full browser.

The problem that Safari View Controller tries to solve is twofold. Apple wants to give developers a way to focus on other parts of their apps' code, leaving the job to display web content to the browser that is already installed on millions of devices and that has been refined and improved over the years with features for millions of people. Gentz told me that Safari View Controller is "way easier to implement than to build a custom mini browser using UIWebView or its successor WKWebView"; [2T App Development](https://twot.lynx.uberspace.de/wordpress/)'s [Tobias Tiemerding](https://github.com/honkmaster) also lauded the possibility of not having to write a browser of his own, resulting in fewer bugs and "the same convenient look in many apps".

![Autofill is supported in Safari View Controller.](http://48ce6c28e7bf5f42a1b7-2712e00ea34e3076747650c92426bbb5.r89.cf1.rackcdn.com/2015-06-24-135541.jpeg)

> _Autofill is supported in Safari View Controller._

At the same time, Apple is making sure that user privacy and security are highly valued in how Safari View Controller operates. Safari View Controller runs in a separate process from the host app, which doesn't "see" the URL or navigation happening inside it. Therefore, Apple claims that Safari View Controller is entirely "safe", as private user data stays in Safari and is never exposed to a third-party app that wants to open a link in it.

Because of this, Apple has been able to port many of the features that users know from Safari to any app that uses Safari View Controller in iOS 9. Safari View Controller shares cookies and website data with Safari, which means that if a user is already logged into a specific website in Safari and a link to that website is opened in Safari View Controller, the user will already be logged in. This alone could make for a drastically superior experience when tapping, for instance, links to services like Amazon, Pinterest, or Facebook from third-party apps. If those services use Safari View Controller and the user is already logged in from Safari, she'll get a continuous and consistent experience.

![Safari Reader mode in Safari View Controller.](https://cd336977afb0dc8522f0-3b1073ac6adc6b2fffddbe35a528b598.ssl.cf1.rackcdn.com/Photo-2015-06-24-14-43-WwsaOE86h30NcWKk5yI5bFXGoGUCw0yKOS.jpg)

> _Safari Reader mode in Safari View Controller._

But there's more. Because Safari View Controller is Safari made available to an app, Apple can offer more than shared cookies and a familiar interface. Safari View Controller has access to iCloud Keychain's password autofill, plus contact card and credit card autofill, Safari Reader, and the system share sheet for action and share extensions. Safari View Controller supports detection of phishing attempts, has a nice built-in progress bar, and it also provides custom views for errors and other issues in webpages. Apple even added support for the new Content Blocking extensions in iOS 9 to Safari View Controller: described as a way to add something to the experience of a webpage "by taking something away", content blockers can be turned on once in the iOS Settings and they'll be automatically enabled in Safari and Safari View Controller.

While [Apple's new deep linking framework](http://www.macstories.net/stories/inside-ios-9-search-apples-plan-for-more-connected-apps/) will give developers a faster way to open Safari and return to their apps, it's clear that they're not taking a half-baked approach with Safari View Controller, which they're positioning as the best way to open web views in apps.

This isn't surprising: in every area of iOS, Apple has been on a long path to prioritize privacy, security, performance, and consistency with a meticulous consideration of trade-offs. Safari View Controller embodies these principles, and judging from the reactions of developers I spoke with, this will be a welcome change in iOS 9.

## Developer Reactions Are Positive

"I expect that Safari View Controller will quickly become the de facto solution for in-app browsing, and that apps that continue to use hand-rolled web views will be rightfully viewed with skepticism", Irace told me.

Last year, Irace wrote [a popular blog post](http://bryan.io/post/104845880796/we-need-a-safari-view-controller) asking for a Safari View Controller on iOS, and while he won't comment on Tumblr's plans after only two betas of iOS 9, he believes that adopting Safari View Controller "will become a checklist item for being a good platform citizen". Prior to iOS 9, Apple's guidelines mandated authentication with web services via in-app web views, which, as Craig Hockenberry noted, could lead to serious security concerns. "Since I can't see a reason for most developers not to adopt Safari View Controller", Irace added, "I look forward towards looking back at custom in-app browsers as seeming crazy in hindsight".

"I've already replaced Instapaper's in-app browser with Safari View Controller", [Brian Donohue](https://mobile.twitter.com/bthdonohue), lead developer of [Instapaper](https://itunes.apple.com/us/app/instapaper/id288545208?mt=8&uo=4&at=10l6nh&ct=ms_inline) for iOS, told me this week. Instapaper allows users to view the original web version of articles saved in the app's read-later list, but, until today, Donohue had to maintain a custom browser that didn't have all the features and credentials of Safari, a problem for websites that present content behind a paywall. With Safari View Controller, Instapaper can offer native Safari functionality for every article that needs to be viewed on the web, and Donohue is optimistic about this feature.

"When logging into BitBucket and GitHub there is an authentication flow that currently sends the user to Safari and back to my application and I hope to keep this inside my app", said [Anders Borum](https://mobile.twitter.com/palmin), the developer of [Working Copy](https://itunes.apple.com/us/app/working-copy/id896694807?mt=8&uo=4&at=10l6nh&ct=ms_inline), a Git client for iOS. Like many other apps, Working Copy requires users to log into an existing account, which is likely already present in Safari's autofill preferences. For this reason, he said that having built-in access to the iCloud Keychain will be the "primary advantage" of adopting Safari View Controller in his app. [Geoff Hackworth](https://mobile.twitter.com/geoffhackworth), the developer of various iOS apps such as Pommie and Easy Shopping List, shared a similar sentiment, describing Safari View Controller as a superior option even for the "simple needs" of his apps because "it will work better, look more familiar to the user, has standard share sheet options, auto-hides the navigation and toolbar nicely, and provides an escape hatch to open in the "real" Safari if necessary".

[Oisin Prendiville](https://mobile.twitter.com/prendio2?lang=en) is one half of [Supertop](http://supertop.co/), the indie duo behind well-known podcast client [Castro](https://itunes.apple.com/us/app/castro-podcast-app/id723142770?mt=8&uo=4&at=10l6nh&ct=ms_inline) and RSS reader [Unread](https://itunes.apple.com/us/app/unread-rss-news-reader/id911364254?mt=8&uo=4&at=10l6nh&ct=ms_inline). In our chat, Prendiville said that most developers will "strongly consider" transitioning to Safari View Controller, a welcome addition that, like extensions in iOS 8, should help bridge the gap between apps and the rest of the OS.

Supertop is currently working on a major 2.0 update to Castro, and they believe they'll "almost definitely" use Safari View Controller in the new app. "We steered away from having an in-app browser at all in the first version", he said, citing the deadline of Castro 1.0 and the infrequency of user requests as the reasons why the app didn't offer a browser to open links from podcast episodes. "The ease of adopting it in Castro 2, and the fact we no longer need to think about a custom browser UI, means it's pretty much a no-brainer to use it", Prendiville concluded.

"It's a big step forward". Singapore-based [Hwee-Boon Yar](https://mobile.twitter.com/hboon) is the creator of Regex, Everyday Journal, and other apps for iOS, and like others he's often wished for a way to let users browse web content with the convenience and security of Safari without taking them out of the app. Over the years, he has relied on custom web views to display webpages in his apps - a crucial feature for popular categories of apps like News and Social Networking. With iOS 9, he'll be able to stop worrying about writing tons of code to build an in-app browser. "A homegrown solution is not only hard to get right", he said, "it's also impossible in cases like access to keychain login data".

## Some Caveats, Some Doubts

The overwhelmingly positive reactions from developers I spoke with, however, came with a few concerns and doubts that can't be answered today after the second beta of iOS 9.

"Whether to transition to Safari View Controller in Unread is more difficult to decide", Prendiville told me. Supertop's excellent RSS app, which I [covered](http://www.macstories.net/reviews/unread-review/) several times in the past here at MacStories, features a highly customized browser that relies on gestures for navigation and sharing. Were Supertop to adopt Safari View Controller in Unread, much of the browser's customization and uniqueness would go away. "The question we need to answer is whether it's worth sacrificing the seamlessness of the current implementation with the flexibility of using the system-provided option".

Supertop isn't alone in considering the trade-off of custom branding and behavior for consistency and system features. [Andrew Milham](http://zeode.com/), developer of [GiftPlanner](http://zeode.com/giftplanner/), is worried that Safari View Controller will "never look completely integrated" because of the lack of deep interface and action customizations that could make the web view feel out of place with the rest of an app. In his GiftPlanner, for example, users can tap & hold an image in a webpage to choose it as the gift's preview image, but this won't be possible with the standard menus and actions offered by Safari View Controller. And yet, Milham notes that these are "very few downsides" compared to "significant upsides", adding that Safari View Controller will save development time and that he's still planning to support it in his apps when iOS 9 launches.

![Apps like Editorial and 1Password have more advanced browsers that feature controls and options not available in Safari View Controller.](http://48ce6c28e7bf5f42a1b7-2712e00ea34e3076747650c92426bbb5.r89.cf1.rackcdn.com/2015-06-24-142550.jpeg)

> _Apps like Editorial and 1Password have more advanced browsers that feature controls and options not available in Safari View Controller._

Apple is still advising developers who need to customize web views to use the traditional web view approach[1](http://www.macstories.net/stories/ios-9-and-safari-view-controller-the-future-of-web-views/); when iOS 9 launches later this year, expect to see high profile apps and advanced productivity suites _not_ using Safari View Controller and sticking with their own custom browsers instead. "However, the majority of in-app browsers are using the exact same paradigm of forward button, back button, share button, and URL field that Safari View Controller offers out of the box", Donohue noted.

As with other system features built by Apple to enhance communication between apps, it's fair to wonder how much [big companies with their ecosystems of iOS apps](http://www.macstories.net/stories/no-ecosystem-is-an-island-google-microsoft-facebook-adobes-ios-apps/) actually want users to be able to easily exchange data with different apps. Twitter and Facebook are two notable examples: their apps - two of the most downloaded free apps on the App Store - don't use iOS 8 share sheets, likely because it's in their own interest to make it difficult for users to, say, save links and pictures discovered in their feeds somewhere else.

![Custom web views in Twitter and Facebook Paper.](http://48ce6c28e7bf5f42a1b7-2712e00ea34e3076747650c92426bbb5.r89.cf1.rackcdn.com/2015-06-24-143351.jpeg)

> _Custom web views in Twitter and Facebook Paper._

This poses a few interesting questions for Safari View Controller as well. Safari View Controller brings the sharing and Reader capabilities of Safari to any app, while at the same time hiding information about the URLs being viewed from the app that displayed the web view. It's easy to imagine why companies like Google, Facebook, or Twitter may not want to rely on Safari View Controller, therefore slowing its uptake in public perception.

With Safari View Controller, Twitter for iOS may end up having a consistent way to save web links to any service; Facebook may not be able to see webpages users open and navigate to; if it were adopted in Gmail, Google would lose the ability to analyze user data for web browsing that originated from email. These are just examples that I imagined for this article, but history tends to repeat itself, and I'd doubt that companies that depend on tightly controlled experiences and data collection will like the privacy-first design of Safari View Controller.

In discussing Safari View Controller with developers, another potential issue also came up - whether users will recognize it as part of the Safari they already know. "One slight concern is how exactly a user will know for sure that they're in a secure environment", Irace told me. Safari View Controller is similar to Safari, but it doesn't live inside Safari, and its ability to autofill logins and request access to the iCloud Keychain may raise questions in users who are not familiar with the feature, at least initially.

"It's not obvious to the user that this is Safari View Controller and not a homegrown component based on UIWebView/WKWebView", said Hwee-Boon Yar. He compared the native features of Safari View Controller to alert dialogs used by Apple across the system. "There's also no way to be absolutely sure even for a more technical user. This is a similar situation to the prompts Apple uses, asking for iCloud password. How does the user know this is the real thing?", he asked.

Lastly, for apps that offer users the ability to download files from webpages with an integrated download manager, using Safari View Controller won't likely be an option this year.

The topic was brought up by indie developer [Riley Testut](https://mobile.twitter.com/rileytestut?lang=en), and it'd apply to hundreds of "downloader" apps that could consider Safari View Controller on iOS 9. Like its app counterpart, Safari View Controller doesn't have a proper download management feature - a showstopper for any developer looking to give users the ability to download files with a browser UI. "My app falls in the narrow category of apps who need a simple in-app web browser, but needs just a _tiny_ bit more control", Testut said, adding that, however, "unless the app has a very good reason for not using it", he expects to see Safari View Controller in most iOS apps "very soon".

## New Web Views

"The majority of us are not in the business of creating browsers". "I think every iOS developer is happy about this addition".

Brian Donohue's conclusion has been a recurring theme in my conversation with iOS developers about Safari View Controller for the past two weeks. Like other iOS APIs before, there are some initial doubts and limitations: most of them will be fixed with time, either by getting accustomed to new features or waiting for improvements in software updates.

Every feature has a development cost both before and after an app is released, and eliminating code required for a common task such as viewing webpages will help developers spend time improving their apps and fixing other bugs.

With Safari View Controller, Apple is freeing many developers from the burden of writing browser components for their apps. "This is something developers have been asking for for years", Milham told me, and it's not hard to understand why. If an app's primary functionality isn't to display web content but still needs to occasionally present webpages, having to code a browser from scratch is a waste of precious time in most cases. Safari View Controller fixes this by bringing years of Safari evolution to every app. This is good for developers, who won't need to spend hours writing a decent browser from the ground up, and it's good for users, who will be able to rely on the power of Safari almost anywhere on iOS.

"Safari View Controller is the rare opportunity for developers to easily give their users a better _and_ more secure experience", Irace said. Apple's willingness to protect user privacy is a fundamental trait of Safari View Controller: for security concerns and other technical limitations, web views have never been on par with Safari. Safari View Controller combines the best aspects of Safari in a web view that's consistent, fast, inherently private, and full-featured.

"A safer, faster, and better in-app browser is great for everyone", Price concluded. For both developers and users, it's easy to see how Safari View Controller is on track to be widely adopted later this year.
