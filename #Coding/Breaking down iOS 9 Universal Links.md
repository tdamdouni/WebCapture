# Breaking down iOS 9 Universal Links

_Captured: 2015-09-24 at 00:42 from [blog.hokolinks.com](http://blog.hokolinks.com/how-to-implement-apple-universal-links-on-ios-9/)_

On the last WWDC, held a couple of weeks ago, Apple announced a deep linking feature called **Universal Links** for iOS 9 on the "[Seamless Linking to Your App" session](https://developer.apple.com/videos/wwdc/2015/?id=509.). Although it isn't a hard feature to implement, there are some caveats.

There is some confusion and misinformation on the Internet, and the Apple session itself doesn't get into much detail. Fortunately for you, at HOKO we just added this new feature on our Smart Links, so we can redirect users to the app in a seamless way.

### What are Universal Links?

It is clear that on iOS 9 Apple is pushing app developers more into deep linking for a better experience. All the news around indexation and search rely on deep linking technology. At the same time, Apple introduced Universal Links -- a way to launch apps easily with traditional HTTP links, using the same URLs to open the website and the app.

With a unique web address, you can then link a specific view inside your app, without the need of a special scheme. Imagine that Twitter starts using Universal Links, then every time you tap a link for an accommodation from twitter.com, your iOS device would automatically open that accommodation page inside the Twitter app, if it's installed, instead of redirecting you to the normal web page. The experience will be smoother and most importantly the user doesn't lose context (no more empty tabs on Safari after redirecting to the app).

### Getting your app ready for Universal Links

Implementing Universal Links is not hard, but you must comply with some pre-requisites first. Here's a list of what you need:

  * Have a registered domain (doh!)
  * SSL access to your domain
  * Ability to upload a JSON file to your domain
  * At least iOS 9 beta 2 ([download](https://developer.apple.com/ios/download/)) -- this is important, because in the previous beta you had to do extra steps.
  * At least Xcode 7 beta 2 ([download](https://developer.apple.com/xcode/downloads/))

If you have everything above just follow the 3 steps bellow to have Universal Links working on your iOS 9 app.

#### 1\. Add the domain to Capabilities

First, you have to add your app domain to your app capabilities on Xcode. You have to prefix it with `applinks:` and also add any subdomains and variants that you might have (www.domain.com, news.domain.com, etc.).

![Add all the domains prefixed with applinks: and don't forget to include every subdomain you might need](https://s3-eu-west-1.amazonaws.com/hoko-blog/apple_capabilities.png)

> _Add all the domains prefixed with applinks: and don't forget to include every subdomain you might need_

Add all the domains prefixed with applinks: and don't forget to include every subdomain you might need

This will enable your app to request a special JSON file `apple-app-site-association` from your domain. **When you first run your app** it will download this file from `https://domain.com/apple-app-site-association`. Jump to the next step to learn how to build this file.

#### 2\. Upload apple-app-site-association file

This file must be present and accessible through a GET request with SSL for security reasons. You can open a text editor and write a simple JSON with this format:
    
    
    {
      "applinks": {
        "apps": [],
        "details": {
          "TBEJCS6FFP.com.domain.App": {
            "paths":[ "*" ]
          }
        }
      }
    }
    

Under the `paths` key you can have a list of allowed paths (the paths that you want your app to react to) or just asterisk if you want to open the app, no matter what the path is.

You may be wondering where `TBEJCS6FFP.com.domain.App` came from. Basically, it is your team id joined with your bundle identifier. You can get your team id from your [Apple's Developer account page](https://developer.apple.com/membercenter/index.action#accountSummary):

![This is the page that has your TEAM_ID, that you have to copy/paste into apple-app-site-association file](https://s3-eu-west-1.amazonaws.com/hoko-blog/apple_team_id.png)

> _This is the page that has your TEAM_ID, that you have to copy/paste into apple-app-site-association file_

This is the page that has your TEAM_ID, that you have to copy/paste into apple-app-site-association file

And the bundle identifier can be found under 'General' on project target:

![Check the General tab and copy/paste into apple-app-site-association file](https://s3-eu-west-1.amazonaws.com/hoko-blog/apple_bundle.png)

> _Check the General tab and copy/paste into apple-app-site-association file_

Check the General tab and copy/paste into apple-app-site-association file

Finally, you upload this file to the root of your domain. If you can see your file when requesting `https://domain.com/apple-app-site-association` then you're ready for the next step.

#### 3\. Handle Universal Links in your app

In order to support Universal Links in your app, you need to implement the [application(_:continueUserActivity:restorationHandler:)](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIApplicationDelegate_Protocol/index.html#//apple_ref/occ/intfm/UIApplicationDelegate/application:continueUserActivity:restorationHandler:) on your AppDelegate. Even though this method may serve many different purposes (e.g. [Handoff](https://developer.apple.com/handoff/) and [Search APIs](https://developer.apple.com/videos/wwdc/2015/?id=709)), we will focus on how to handle incoming Universal Links.

```
import UIKit

extension AppDelegate {

func application(application: UIApplication, continueUserActivity userActivity: NSUserActivity, restorationHandler: ([AnyObject]?) -> Void) -> Bool {

if userActivity.activityType == NSUserActivityTypeBrowsingWeb {

let webpageURL = userActivity.webpageURL! // Always exists

if !handleUniversalLink(URL: webpageURL) {

UIApplication.sharedApplication().openURL(webpageURL)

}

}

return true

}

private func handleUniversalLink(URL url: NSURL) -> Bool {

if let components = NSURLComponents(URL: url, resolvingAgainstBaseURL: true), let host = components.host, let pathComponents = components.path?.pathComponents {

switch host {

case "domain.com":

if pathComponents.count >= 4 {

switch (pathComponents[0], pathComponents[1], pathComponents[2], pathComponents[3]) {

case ("/", "path", "to", let something):

if validateSomething(something) {

presentSomethingViewController(something)

return true

}

default:

return false

}

}

default:

return false

}

}

return false

}

}
```

If the provided `userActivity` is of type `NSUserActivityTypeBrowsingWeb`, it means it has been delegated through the Universal Links APIs. Should that be the case, it is guaranteed that it will have a non-nil `webpageURL` property which is the URL the user opened. Following the previous example, this would be the `NSURL` representation of `http://domain.com/path/to/thezoo`.

To make sure your app can translate the URL into actual content you have to do a few steps:

  * Easily parse the `webpageURL` with the [NSURLComponents](https://developer.apple.com/library/prerelease/ios/documentation/Foundation/Reference/NSURLComponents_class/index.html) into the host (e.g. `domain.com`) and the path components (e.g. `["/", "path", "to", "thezoo"]`).
  * Make sure you recognise the `host`.
  * Try to match the `pathComponents` into a known content inside your app.
  * Validate that the content can actually be presented.
  * Present the content to the user.

In case any of the above fails, Apple advises that your app should fail gracefully by opening the `webpageURL` on Safari instead.

Here's everything summarized in one image:

![This image gives you a quick resume of the whole process of having Universal Links working](https://s3-eu-west-1.amazonaws.com/hoko-blog/universal_links.png)

> _This image gives you a quick resume of the whole process of having Universal Links working_

This image gives you a quick resume of the whole process of having Universal Links working

### Drawbacks of Universal Links

Universal Links are a great deal for developers, but there are a few drawbacks that might lead to an adoption resistance:

Universal Links only work on iOS 9 +

Configuration an app to support Universal Links means that only the users running iOS 9 will take advantage of this technology. Users with prior iOS versions will not be able to open the apps just from tapping on the web links. Instead, they will all fall back to the browser and web page just like before with normal web links.

However, HOKO provides mobile deep linking for devices with **iOS 5 or higher**. Hence, your mobile deep links will work on almost every iOS device worldwide, even if they have iOS 9 or not.

Universal Links will always fall back to the web page previously created.

What if you want to fall back to the homepage or to a complete different website that is not associated with the app? Achieving this would require some additional work, to configure a web page that could redirect your users to the destination page. Furthermore, if you don't have a website at all this turns into an impossible solution.

You can easily solve both use cases using HOKO smart links and their adaptive fallback. For each smart link created, you can choose on each platform what will happen if the app is not installed. Independently you can set the fall back to your website, iTunes store page or any other external website.

With Universal Links, the developer must host a website that will be associated with an app.

This could be bad news for small developers that can't claim, afford or maintain a website for their apps, but still want incoming traffic to their apps through web links.

HOKO is the solution for this problem because it acts as the developer website, with each app being hosted in different subdomains. Thus, the developer just needs create the smart links and publish its URLs and each will open the appropriate app seamlessly.

The association between your app and your website is powered by a configuration file that needs to be created and hosted in the developer's website.

With HOKO, you can skip this tedious configuration because we provide it out-of-the-box. Furthermore, our servers run on the industry top standards for security and performance, providing this configuration to each device in a secure and fast manner.

If you want learn more about HOKO, drop us [an email](mailto:support@hokolinks.com) or [register.](https://hokolinks.com)

![](http://blog.hokolinks.com/content/images/2015/07/HOKO-banner-blog-2.png)

_(Or check out our detailed guide about [Google's App Links](http://blog.hokolinks.com/android-m-app-links-implementation-drawbacks/))_
