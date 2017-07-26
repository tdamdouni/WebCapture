# Sideloading f.lux on iOS with Xcode 7

_Captured: 2015-11-11 at 12:26 from [justgetflux.com](https://justgetflux.com/sideload/)_

In Xcode 7, you can install apps directly to your iOS device with a free account from Apple. So we decided to make a beta version of f.lux for people to try.

It's a few more steps than installing the app store, but there are plenty of harder things even on Pinterest. So, here's how to get f.lux installed on your iOS device.

Download f.lux for iOS  
for use with Xcode 7 

**Ingredients**

  * Mac, OSX 10.10 or greater
  * 1 installed version of [Xcode 7](https://developer.apple.com/xcode/download/)
  * 1 Developer account (use your AppleID)
  * 1 Download, [f.lux for iOS](https://justgetflux.com/sideload/f.lux-xcode-master.zip), unzipped

**Instructions**

First, mix the build ingredients together. Batter may be slightly lumpy.

  1. Open the "iflux.xcodeproj" project in Xcode
  2. Open Xcode > Preferences > Accounts and enter your iCloud or developer credentials
  3. Under Targets > iflux > General > Identity, add a word to the end of the Bundle Identifier to make it a unique name
  4. In the same place, under Identity > Team, select your iCloud account or Developer profile

While the batter chills, connect your iPhone or iPad and load the iflux build:

  1. From the Xcode Product menu, choose Destination and select your iOS device (f.lux doesn't work in a Simulator)
  2. Push Cmd-R when you're ready to have f.lux
  3. When you first run, you'll be prompted to open Settings > General > Profile on your device, and trust your developer account
  4. Run again, and allow location and notifications (things don't work so well without both of these)

By loading an app this way, there are no automatic updates or bug fixes, so this version does a daily update check. If one is available, a message will appear at the bottom of the app, so you can stay up to date when we make fixes.

![](https://justgetflux.com/news/images/sideload.png)

We welcome your feedback - this is a beta release so please let us know if you find any issues or have feature requests. [Visit our forum to discuss](https://justgetflux.com/forum/category/6/ios).

### FAQ

Q: Why is my screen waking up?

A: f.lux has to wake up your screen to make changes:

  * The best way we know to do this is to send notifications (which is why you'll see a lot of them).
  * If you disallow notifications (or have "do not disturb" turned on), it will instead do this by asking for a device unlock, which wakes up the screen for quite a while. This is not a security risk or anything to be worried about.
  * If you allow notifications and make "do not disturb" hours reflect your bedtime, it will be quite a bit less annoying.

Q: Why is my screen locked at 1900K? I don't want it this dark.

A: Because we added the [bedtime mode](https://justgetflux.com/news/pages/mac/) without really finishing the UI to customize it! So if you don't like that, or if you prefer the classic/Windows sunrise/sunset, just change the wake time setting to "Dawn" until we make a better UI. "Bedtime mode" overall is supposed to look like a candle while you're sleeping so you can use your device in the middle of the night, if you have to.

Enjoy!

_--Michael and Lorna_

[twitter](http://twitter.com/justgetflux) [facebook](http://facebook.com/justgetflux) [email](mailto:support@justgetflux.com)
