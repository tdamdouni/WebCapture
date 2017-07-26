# iOS 9, thoroughly reviewed

_Captured: 2015-09-16 at 21:32 from [arstechnica.com](http://arstechnica.com/apple/2015/09/ios-9-thoroughly-reviewed/8/)_

## Performance and battery life

When it comes to iOS 9's performance, the news is mostly good. Using it on every supported iPhone, iPod, and iPad feels about the same as using iOS 8--it doesn't fix that operating system's biggest performance sins, particularly for Apple A5 devices, but it doesn't make anything much worse (we'll be examining iPhone 4S and iPad 2 performance in a separate article). In some cases, it even makes things better.

First, mobile Safari sports some JavaScript performance improvements across the board. Kraken test scores improved on everything from the iPhone 4S to the iPad Air 2, while Google Octane scores rose for nearly every device. There are some regressions in the Sunspider test, but that one's old and light enough that we won't keep it around much longer.

[ ![](http://cdn.arstechnica.net/wp-content/uploads/2015/09/iOS-9-charts.004-980x720.png) ](http://cdn.arstechnica.net/wp-content/uploads/2015/09/iOS-9-charts.004.png)

On newer iDevices that support Metal, you may also see better graphics performance in iOS 9. We noticed improvements in A7, A8, and A8X-based devices running the GFXBench Metal Offscreen tests--Apple is apparently still fine-tuning its proprietary graphics API as it goes.

![](http://cdn.arstechnica.net/wp-content/uploads/2015/09/iOS-9-charts.007-980x720.png)

Finally, we get to battery life. For this test, we wiped each device, ran the battery test twice in each OS version, and averaged the results. Most of the iOS 9 results are just a few minutes up or down from the iOS 8 results, within what we'd consider to be the margin for error. A few see noticeable improvements, particularly the iPhone 6 Plus, but no device sees debilitating drops.

[ ![](http://cdn.arstechnica.net/wp-content/uploads/2015/09/iOS-9-charts.001-980x720.png) ](http://cdn.arstechnica.net/wp-content/uploads/2015/09/iOS-9-charts.001.png)

### Low Power Mode

[ ![](http://cdn.arstechnica.net/wp-content/uploads/2015/09/IMG_00151.png) ](http://cdn.arstechnica.net/wp-content/uploads/2015/09/IMG_00151.png)

Low Power Mode is only supported on iPhones, and it uses a few tricks to squeeze a bit more life out of your phone:

  * Slightly lowers screen brightness.
  * Locks screen after 30 seconds, which can't be changed.
  * Mail fetch, background app refresh, and background downloads are limited or turned off altogether.
  * Tones down some visual effects.
  * Limits the peak speed of the SoC.

Low Power Mode can be enabled manually at any time through the Settings app, and it's offered as an option in the 20 percent and 10 percent battery dialogue boxes. Once enabled, it can be turned off manually in the Settings, or your phone will turn it off automatically once it's got a sufficient charge.

It's difficult to develop a consistent, repeatable test for Low Power Mode, partly because most battery tests require the phone to be active constantly, and most of the power-saving features are intended to increase the amount of time the phone spends idle. Our standard tests won't run because the screen won't stay on longer than 30 seconds. In Geekbench's battery test, which can force the display to stay on, we saw only a marginal difference in battery life between Low Power Mode and standard mode, so it's probably not the best way to measure.

Anecdotally, Low Power Mode makes it easier to squeeze extra time out of your battery by automating things that many people do to preserve battery life anyway--dimming the screen and disabling things like Background App Refresh are already common recommendations for people whose phones are nearing death. The Battery page of the Settings app also makes other power-saving recommendations based on your settings. If you turn off auto-brightness, for example, it will recommend that you turn it back on.

The battery usage stats in iOS 9 are also more granular than in iOS 8--you can see for exactly how long something was "on screen" or in the background, giving you a bit more insight into what apps are using the most power and when they're using it.

## Grab bag

[ ![](http://cdn.arstechnica.net/wp-content/uploads/2015/09/IMG_4616.jpg) ](http://cdn.arstechnica.net/wp-content/uploads/2015/09/IMG_4616.jpg)

The things we've covered so far are the largest and most immediately noticeable changes, but there are a few smaller niceties that are worth taking a quick look at.

### Searchable Settings

We've been asking this for a while now--iOS' labyrinthine Settings app finally has a search box, giving you quicker access to those settings you need to change just seldom enough that you always forget where they're hidden.

Otherwise iOS 9 does a bit of the typical settings-shuffling. The biggest change is a new "Battery" subheading. Low Power Mode lives here, but the Battery Percentage status bar setting and the battery usage stats live here too. It used to be buried all the way under General > Usage > Battery Usage, so it's good to see it climb out of that hole.

### Smaller updates (and more)

A major complaint about iOS 8 was the amount of free space it needed to download and install updates over the air, a particular frustration for people with 8GB and 16GB iDevices. App Thinning will help give those devices more free space in the first place, but Apple has made other adjustments to make updates easier to install.

For one, updates just require less free space than they did. The main iOS 9 update will require 1.3GB to install instead of iOS 8.0's 4.6GB, at least according to Apple (though as we saw toward the beginning of the review, the amount of space it takes up on a device once installed is more or less the same). And if you're trying to install an app on an iDevice without sufficient space, iOS 9 will offer to uninstall and redownload apps for you to make room (the company tells us that data saved in the apps is preserved during this process).

With some luck, this will improve adoption rates. If you still find yourself without the free space you need to install the OTA update, connecting your device to iTunes and updating the old fashioned way should work regardless of the amount of free space you have.

### 6-digit passcodes and two-factor authentication

If you've got a device with a TouchID fingerprint sensor (the iPhone 5S, 6, 6 Plus, 6S, and 6S Plus as well as the iPad Air 2, Mini 3, and Mini 4), you'll now need to create a backup passcode with a minimum of six digits. This is true even if you opt not to use TouchID. Non-TouchID phones and tablets still prompt for a four-digit passcode by default.

This shouldn't be disruptive for anyone who's generally happy with TouchID's accuracy--you only need your passcode when unlocking your device or changing your security settings, both of which happen relatively rarely. I switched to using an eight-digit passcode in September of 2013 when the iPhone 5S came out, and it hasn't been a particular hardship.

Apple is also pushing two-factor authentication (2FA) harder in both iOS 9 and OS X El Capitan, and it has [published a support page](https://developer.apple.com/support/two-factor-authentication/) outlining roughly how the new system works. Even if you install these betas today, you may not be offered the chance to enroll in the new 2FA system until Apple deems your account "eligible."

If you're already using the old two-factor system, the new one doesn't look all that different on paper. You still have to use phone numbers or trusted devices to log in on new devices, the new system just requires six-digit verification codes rather than the current four digits. The fact that Apple is pushing 2FA a bit harder might result in more people using it, though, which is a good thing.

### Battery widget

There's a handy new Today widget that can show you the battery levels of your device and any battery-powered accessories connected to your device. This works for accessories like the Apple Watch and Bluetooth speakers, but not for our Apple wireless keyboard. If previous versions of iOS showed you a little battery icon next to the Bluetooth symbol at the top of the screen, the battery level should be visible in this widget now.

### New default photo albums

Apple has added two new special photo albums to the Photos app, one for selfies and one for screenshots. If you prefer everything in one place, you can always fall back on the Camera Roll, which displays every picture, selfie, and screenshot in a chronological list as always.

### Find iPhone and Find Friends

These two utility apps were previously available in the iTunes Store, but as of iOS 9 they've joined the gaggle of pre-installed Apple apps. Aside from some visual tweaks, the apps work the same way they did before, though Find Friends appears to support location sharing via AirDrop where it didn't before.

### New wallpapers and missing wallpapers

iOS 9 includes a handful of new wallpapers, mostly dark and trippy where iOS 7's and 8's were a combination of bright colors and nature themes. I liked the old ones better and I don't like that iOS 9 includes fewer wallpapers in total, but given the number of people who use their own photos as wallpapers it's hard to justify the storage space used up by high-resolution pictures.

## Conclusions

Last year we said that iOS 8 felt like the second half of the iOS 7 update, the one that completed the transition between iOS' skeuomorphic era and our current reality, where the lines between "mobile device" and "computer" blur a little more every day. iOS 9 takes that foundation and builds on top of it without radically altering things, much in the same way that iOS 6 built on top of the advancements in iOS 4 and iOS 5.

It was a smaller release, and as a result, testing the final build of iOS 9 was frankly kind of a relief.

iOS 7 and 8 made big changes, and those changes could make the early releases of those operating systems frustrating to use. iOS 7 didn't settle down until version 7.1, and iOS 8 didn't feel quite right until 8.3. iOS 9 doesn't feel like it needs a major bugfix release before we can recommend it without hesitation for every device that supports it (and we should know, we tested it on most of them).

The worst thing we can say about the new release is that its biggest, best new contributions--the things that make the iPad feel more like its own device and less like a big iPhone--are only available to a sliver of existing devices. Slide Over and Picture-in-Picture need an iPad from 2013 or later, and the truly transformative Split View mode needs a cutting-edge model. The rest of the operating system is about spit-and-polish, taking existing features (Siri, Spotlight, Maps) and extending them in logical ways.

And then you get to iOS 9's real killer feature--you can fire up your iDevice and download it today, regardless of which one you're using or which carrier you subscribe to. It feels vaguely absurd to say that in 2015, but that's the state of mobile devices today; in any given Android phone you're usually two companies removed from Google's OS updates, and neither your OEM nor your carrier are particularly interested in giving you reliable, extended software support. You can read volumes about new software updates and then go months without seeing them on the one device you actually carry around daily.

But if you're running iOS 8, update. There's no reason not to, and there's nothing keeping you from doing it.

### The good

  * Visual tweaks continue to refine the aesthetic introduced in iOS 7. The software keyboard in particular is a big improvement.
  * The iPad was in need of some attention, and this update's multitasking features and hardware keyboard support give it that attention.
  * Supports all hardware that ran iOS 8 and shouldn't really slow anything down or consume much more space.
  * Improved battery life on some devices, and Low Power Mode should help you squeeze a bit more out of your phone in a pinch.
  * Updates require less space to install, and the OS includes several other space-saving tricks.
  * Proactive Siri and third-party search APIs are welcome additions to the platform.
  * Additions to existing apps like Safari and Notes are generally useful.
  * Searchable Settings. SEARCHABLE SETTINGS.
  * Available to everyone today.

### The bad

  * Maps public transit supports a discouragingly small number of cities after three years of waiting.
  * Proactive Siri still isn't as capable or as useful as Google Now.
  * iPhone 4S' cramped screen is still a problem, given that many buttons and boxes expand in iOS 9.
  * No Low Power Mode on iPads or iPods.

### The ugly

  * Few iPads are actually powerful enough to use the best of the new features.
