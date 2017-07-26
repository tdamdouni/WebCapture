# Libraries Used in the Top 100 iOS Apps

_Captured: 2015-10-10 at 10:10 from [medium.com](https://medium.com/ios-os-x-development/libraries-used-in-the-top-100-ios-apps-5b845ad927b7)_

I am eternally curious. A big motivation for writing the [FLEX](https://github.com/Flipboard/FLEX) debugging tool was to explore other apps and discover how they tackle common problems. On Monday, armed with a jailbroken iPhone and an extended version of FLEX, I ran some analysis on the top 100 free apps in the US App Store.

I started by building up a database of the objective-c classes in each app. The median number of classes per app came in at 1,175. In total, the database contained over 181,000 classes. The app with the most classes had over 15 times the median. I bet you can guess which one that was ;). Each of the top 7 apps by number of classes was made by either Facebook or Google.

![](https://cdn-images-1.medium.com/freeze/max/30/1*xRhRZYw-FjUC2P8vPbLTxg.png?q=20)![](https://cdn-images-1.medium.com/max/800/1*xRhRZYw-FjUC2P8vPbLTxg.png)

Next, I looked for common class names and tried to match them to open source projects and 3rd party libraries. I bucketed nearly 5,000 of the most common classes into over 100 projects.

The most used project by far was the [Facebook iOS SDK](https://github.com/facebook/facebook-ios-sdk) which appeared in 67 of the 100 apps. Other category leaders included [AFNetworking](https://github.com/AFNetworking/AFNetworking) for networking (39) and [Crashlytics](https://cocoapods.org/pods/Crashlytics) for crash reporting (38). Several Apple sample code projects show up across many apps, with the most popular being [Reachability](https://developer.apple.com/library/ios/samplecode/Reachability/Introduction/Intro.html) (38). Finally, evidence of the dependency manager [CocoaPods](https://cocoapods.org/) only appeared in 30 apps, indicating that many developers are still adding these projects the old fashioned way. The gist below gives the full list of projects and the number of apps each one appears in.

Exploring other apps is a great way to expand your iOS knowledge. If you've ever been curious about what's in an app, I highly encourage you to dig in and find out for yourself!

```
# https://gist.github.com/ryanolsonk/e33bf9e89677da9fe8ce#file-top100appprojects-txt

67	facebook-ios-sdk
48	Bolts-iOS
39	AFNetworking
38	Google-Mobile-Ads-SDK
38	Reachability (Apple)
37	Crashlytics
31	Flurry-iOS-SDK
30	CocoaPods
29	GoogleConversionTracking
26	SDWebImage
25	Fabric
25	mopub-ios-sdk
23	Unity
22	AdColony
20	GoogleAnalytics
19	GTMLogger
18	comScore-iOS-SDK
18	google-plus-ios
17	OpenUDID
17	CocoaLumberjack
16	Adjust
16	ChartboostSDK
16	MBProgressHUD
15	OpenInChrome
15	TTTAttributedLabel
14	HockeySDK
14	google-breakpad
13	CocoaAsyncSocket
13	AppLovin
13	SBJson
12	FMDB
12	GLImageProcessing (Apple Sample)
12	pop
12	SSZipArchive
12	Appirater
11	BPXLUUIDHandler
11	VungleSDK-iOS
11	Protobuf
11	UnityAds
10	SSKeychain
10	KeychainItemWrapper
10	PLCrashReporter
10	secureudid
10	libPhoneNumber-iOS
10	oauthconsumer
9	InMobiSDK
9	MobileAppTracker
9	TapjoySDK
9	TrustDefender Mobile
9	iRate
8	OnePasswordExtension
8	SFHFKeychainUtils
8	Tweaks
8	cocos2d
8	GPUImage
8	KVOController
8	Nimbus
8	google-cast-sdk
7	HPGrowingTextView
7	Localytics
7	thrift
7	FormatterKit
7	Kochava
7	Mantle
7	Mixpanel
7	AppNexusSDK
7	JSONKit
7	NJKWebViewProgress
7	cocos2d-x
7	TouchJSON
6	SupersonicAds
6	TPKeyboardAvoiding
6	SponsorPaySDK
6	PhotoScroller (Apple)
6	TwitterKit
6	SpeechKit
6	ReactiveCocoa
6	UICKeyChainStore
6	WeChatSDK
6	XMLDictionary
5	SVProgressHUD
5	SocketRocket
5	libextobjc
5	Shimmer
5	TransitionKit
5	AsyncDisplayKit
5	SnowplowTracker
5	aws-sdk-ios
5	SVPullToRefresh
5	MMWormhole
5	Masonry
5	UIAlertView+Blocks
5	FLAnimatedImage
5	AppsFlyer-SDK
5	CardIO
5	TMCache
5	youtube-ios-player-helper
4	Weibo
4	Parse
4	MagicalRecord
4	GoogleMaps
4	GoogleAds-IMA-iOS-SDK
4	Braintree
4	PSPDFTextView
4	FXBlurView
4	ASIHTTPRequest
```
