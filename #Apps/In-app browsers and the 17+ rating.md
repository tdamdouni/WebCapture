# In-app browsers and the 17+ rating

_Captured: 2015-06-24 at 21:55 from [agiletortoise.com](http://agiletortoise.com/blog/2012/03/02/in-app-browsers-and-the-17-rating/)_

Apple has a nagging App store review problem to solve. One that dates back as long as the App store has been around, and one which will continue to be a problem until a technical solution is put in place. The crux of the problem is the "unfiltered Internet content" rule. As a policy, the App review team is suppose to ensure that apps which provide unfiltered access to the Internet are given a rating of 17 . This is a rather harsh rating, because it triggers additional warnings and limits when purchasing the app.

The iOS SDK provides a [UIWebView](https://developer.apple.com/library/ios/#documentation/UIKit/Reference/UIWebView_Class/Reference/Reference.html) control. It is used to embed web content in an app - it is essentially the Safari renderer, outside of Safari. There are any number of useful applications of this control, but one of most common is the "in-app browser". When you click on a link in your Twitter client, it shows that web page in the app - rather than opening it in Safari. This is great. It is convenient for the user, avoids the context switching between apps and allows the app developer to provide other features related to the web view that are not available in Safari.

The parental controls in iOS are implemented by the Safari app, however. Therefore any current or future steps taken by Apple to safeguard and filter Internet usage through parental controls are only available in the Safari app, and not when using the UIWebView embedded in another app. In theory, to be fair and equal with it's review process every app with an in-app browser should be rated 17+.

To date, apps whose primary function is web surfing - essentially Safari replacements - have been consistently rated 17+ (see: [Mercury Web Browser](http://itunes.apple.com/us/app/mercury-web-browser-pro-most/id348701575?mt=8), [Opera Mini](http://itunes.apple.com/us/app/opera-mini-web-browser/id363729560?mt=8)).

For the most part, apps with in-app browsers have not been subjected to this same requirement. There are too many to list, but more-or-less every Twitter client, RSS reader, Social networking app (Facebook, Yelp!, etc.) have some form of in-app browser. Somewhat randomly, however, the App Review team catches an app with an in-app browser and rejects it on this basis. Marco Arment has written about his [issues with this rule with Instapaper](http://www.marco.org/2009/07/15/theres-a-pretty-significant-problem-in-the-new) as far back as 2009.

In my own case, it happened to a well establish app on a minor update that had no relation to changes in this area and resulted in a month long ordeal to get that rejection overturned. I have heard similar stories from other developers - some of whom have been successful in getting the rejection appealed, other not.

The App Review team is in a tough spot here. The rule is not a completely unreasonable one, but it would generate some odd results if applied consistently. If the App Review team did apply the 17+ rating to every app that displayed Internet content this way, it would undermine the end-user's trust in the rating system - because they would constantly find themselves warned about mature content for apps that did not appear to have any in their own personal judgement.

To me, there is a clear solution to this problem. There needs to be a way to utilize a UIWebView that is subject to the same parental controls and filters available to Safari. It would be an opt-in feature of the UIWebView and when applied, the App Review team could be sure that the app utilizing the control does not require a special rating. I think the vast majority of the developers using in-app browsers would happily turn this feature on - because we are not interested exposing minors to inappropriate materials.

I have no idea what is involved in implementing something like this from the technical side, but I know this problem is only going to get worse and more confusing for the App Review team, developers and the owners of iOS devices.

I have [filed a radar with Apple](http://openradar.appspot.com/10971985) regarding this issue. I hope those of you with developer accounts will consider duping this radar to try to draw attention to the problem and get a long term solution.
