# Quick Take on iOS 9 URL Scheme Changes

_Captured: 2015-06-10 at 21:08 from [awkwardhare.com](http://awkwardhare.com/post/121196006730/quick-take-on-ios-9-url-scheme-changes)_

[**UPDATE #2: I have independent confirmation from several sources that these limitations are meant to only apply to "canOpenURL" and it is a bug that they are also effecting "openURL". There are still implications, and many apps will need some updates, but that's not so dramatic a change.**]

[**UPDATE:** _The more I think about this and get feedback from people on Twitter, the more I think these limitations on "openURL" have to be a bug. It would break too many things (like login workflows for Facebook/Dropbox). There are still significant side effects from the change to canOpenURL alone, but surmountable ones._]

During Session 703, "Privacy and Your App", at WWDC 2015 ([video](https://developer.apple.com/videos/wwdc/2015/?id=703)), Apple discussed changes impacting URL schemes on iOS 9. URLs are used extensively by some of [my apps](http://agiletortoise.com), so this piqued my interest. This post is a quick summary of how I understand the changes and their impact. Some of this could turn out to be wrong or change before iOS 9's final release, but I thought I'd get the discussion going.

#### What are URL schemes?

I will not attempt to [define URL](https://en.wikipedia.org/wiki/Uniform_resource_locator), but suffice to say URLs are the part and parcel of navigation on the Internet. You are likely quite familiar with web URLs like "http://apple.com". The first part of a URL, the part before the colon, is the URL scheme. The scheme is used to identify the type of service required to understand the URL, and most operating systems have a mechanism for applications to register that they are capable of opening URLs with certain URL schemes. The common example being the web browsers registering to open "http" and "https" URL schemes so that web links will open in the browser.

iOS has a system for registering URLs schemes as well. Some URL schemes, like "http" and "mailto" are reserved by Apple to point to their own Safari and Mail apps, but apps installed from the App Store can register to handle other arbitrary URL schemes.

Custom URL schemes like these are used by many apps for a variety of purposes. A common use is to deep link to a particular piece of content within an app - seen as an "Open in app" link from a web page.

Because of the limited available channels for apps to communicate with each other on iOS, URLs have been employed to expose functionality between apps as well. The iOS automation community has built a tremendous amount of functionality on top of URL schemes to allow apps to provide services, forward data to other apps, or simply launch other apps. If you use [Drafts](http://agiletortoise.com/drafts), [Launch Center Pro](http://contrast.co/launch-center-pro/), [Workflow](https://workflow.is) or many, many other apps, you are using and benefiting from URL schemes on iOS.

#### What is Apple Changing?

The key bits regarding changes to URL schemes in iOS 9 is the [Privacy and Your Apps](https://developer.apple.com/videos/wwdc/2015/?id=703) session, starting at around the 9 minute mark under the heading "App Detection".

There are two URL-related methods available to apps on iOS that are effected: [canOpenURL](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIApplication_Class/index.html#//apple_ref/occ/instm/UIApplication/canOpenURL:) and [openURL](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIApplication_Class/index.html#//apple_ref/occ/instm/UIApplication/openURL:). These are not new methods and the methods themselves are not changing. As you might expect from the names, "canOpenURL" returns a yes or no answer after checking if there is any apps installed on the device that know how to handle a given URL. "openURL" is used to actually launch the URL, which will typically leave the app and open the URL in another app.

Up until iOS 9, apps have been able to call these methods on any arbitrary URLs. Starting on iOS 9, apps will have to declare what URL schemes they would like to be able to check for and open in the configuration files of the app as it is submitted to Apple. This is essentially a whitelist that can only be changed or added to by submitting an update to Apple. It appears that certain common URLs handled by system apps, like "http", "https", do not need to be explicitly whitelisted.

I have tested these limits in Xcode 7 with the initial iOS 9 beta pre-release with the following results:

  * If you call the "canOpenURL" method on a URL that is not in your whitelist, it will return "NO", even if there is an app installed that has registered to handle this scheme. A "This app is not allowed to query for scheme xxx" syslog entry will appear.
  * If you call the "openURL" method on a URL that is not in your whitelist, it will fail silently. A "This app is not allowed to query for scheme xxx" syslog entry will appear.

It was not clear from the session if these limits apply to the "openURL" call, but in actual testing it appears that they do. It is possible (I hope) this is a bug.

Per the discussion in the session, these limits will be retroactively enforced on apps built and submitted to the store prior to iOS 9 by the system, which will build it's own whitelist of up to 50 URL schemes allowed for an app based on the actual calls made by the app. The session does not explicitly state a limit to the number of URL schemes that can be in the app's own whitelist, but I have to assume 50, or some other reasonable limit will be enforced - likely by a validator when submitting apps to Apple.

In practice, this means URLs are now something that can only be used to check for and open a small number of known outside apps. For example, the way Google uses [x-callback-url](http://x-callback-url.com) based URL callbacks to create "Back" buttons to return to other apps from their iOS versions of Chrome and Maps could still continue to work between their own family of apps which they would likely whitelist, but would not be able to continue to be used by other arbitrary apps wishing to make that "Back" button appear in Chrome.

This will also practically kill any sort of launcher app, and prevent apps like Drafts and Workflow from accessing services in other apps, chaining URL callbacks and other complicated automation tasks.

#### Why is Apple Making this Change?

Apple is making this change for privacy reasons.

Although any app can register any arbitrary URL schemes and there is no guarantee that because the system returns "YES" from a canOpenURL call that a particular app is actually installed, registering unique URL schemes has become a de facto way to check if a certain app is installed on the system - and by scanning lists of "known" URL schemes with canOpenURL, certain apps (like Twitter's) have been abusing this loophole to scan your system for installed apps and used this information for whatever nefarious reasons - likely involving advertising.

Apple has been adding more secure and reliable ways to do many (but not all) of the things possible with URLs (Extensions, App Links, etc.). Long term these are important changes because it is true that there are implications to the uncontrolled use of URLs that may be exploited.

#### Possible Alternatives

I agree with Apple's concerns regarding the abuse of "canOpenURL", but if the current implementation is their intended solution, I believe it is too severe and will cause too much breakage and bad user experience for many users.

My hope is (as mentioned above) that these changes were only meant to apply to the "canOpenURL" method, and that it is a bug that they have also limited the functionality of the "openURL" call. I have filed a radar reporting this as a bug, if you are a developer and agree with my assessment please consider duplicating it (rdar://21320635 | [openradar](http://openradar.appspot.com/radar?id=6159379246088192)).

Even if that is the case, loss of the ability to call "canOpenURL" on arbitrary URLs will limit the user experience on many automation applications of URLs because an app has no way of testing if the URL can be opened successfully and will have to rely on the system to report errors. It might also be possible to allow it to continue to function for apps in a throttled fashion that would only allow a certain number of "canOpenURL" calls in a certain time period - thus hindering it's usefulness for scanning.

I have not fully thought out the ramifications of this change, and it was made public yesterday - but I wanted to get some thoughts out quickly to start a discussion and hope Apple is listening and willing to make good compromises that protect users and allow iOS to continue to be as powerful and flexible as possible.
