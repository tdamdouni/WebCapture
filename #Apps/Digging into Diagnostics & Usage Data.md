# Digging into Diagnostics & Usage Data

_Captured: 2015-10-06 at 21:46 from [joecaiati.info](http://joecaiati.info/post/130542880175/digging-into-diagnostics-usage-data)_

Diagnostics & Usage isn't just the name of [my podcast](http://5by5.tv/dau) with [Cody Coats](https://twitter.com/cpcoats). Its name comes from Apple's Diagnostics & Usage Data section in iOS. Pre-iOS 8, you could have found this is section under Settings -> General -> About -> Diagnostics & Usage, but now it lives in Settings -> Privacy -> Diagnostics & Usage.

### What Is It?

I would liken the Diagnostics & Usage Data section to the Console on the Mac. There is a lot of noise in there, but sometimes you can find important information about issues related to your device. At its most basic definition, the Diagnostics & Usage Data section is a log of system events that happen on your iOS device. This log isn't tracking your every move, but it is creating entries whenever events like an app crash happens.

Like the Console, unless you are an engineer at Apple, you probably won't know what every string of text means, but I'd like to think I know enough to help you figure out what's important. If you are interested in what's going on in your iOS device, navigate to the section and let's dig in.

### Common Entries

Now that you are in your Diagnostics & Usage Data section[1](http://joecaiati.info/post/130542880175/digging-into-diagnostics-usage-data), if it's your first time, you may be overwhelmed by the amount of entries and gibberish you are seeing. The good news is that some of these entries are very common across devices and generally can be ignored.

#### Apple Wireless Diagnostics Data

Entries starting with "awdd-[yyyy-mm-dd]" are the most common. Depending on whether you read the setup screen when configuring iOS, you may remember coming across a screen like this:

![diag](http://s.mlkshk.com/r/161IF)

If you enabled diagnostics data, Apple will periodically create logs and send them anonymously to their servers for examination. Each time Apple does this, it creates an "awdd" log in that list. If you didn't realize you have enabled this feature, just back out one screen in the Diagnostics & Usage section and toggle it off. Though I'd recommend you keep it on, including the "Share With App Developers" section because it helps resolve bugs a lot faster.

#### Memory

I would be shocked if there wasn't "JetsamEvent-[yyyy-mm-dd]" entries on your devices. These were previously called "LowMemory" and are logs of when apps and data have been booted from your device's RAM.

Even on the 2 GB-equipped iPhone 6s, I am seeing one or two entries per day which is pretty good, but if you are seeing ten or more per day, you probably haven't turned off your iOS device in a very long time or your device is getting old and new apps are consuming all available RAM. I've found that completely powering off your iOS device, waiting ten seconds, then powering it back on should be done once every few weeks and can help with RAM management.

I wouldn't worry too much about seeing this listed, but there have been situations where I've seen this log hundreds of times on people's phones which could signify a problem and warrant a trip to the Genius Bar.

#### Stacks

The "stacks-[yyyy-mm-dd]" entry, short for stackshot, doesn't represent a crash. A stackshot collects kernel and OS data that are generally meant for Apple engineers. Some of these entries can be accidentally triggered by users if they press the home button and one of the volume buttons at the same time. These shouldn't be a concern.

#### Other Entries

  * Certain entries that you will see daily are "log-sessions", "log-[daemon]" and "CoreTime". There isn't much value into reading these, but you will see them. 
  * Entries like "Carousel", "BTServer", "searchd" and other daemons can be peppered in, but you shouldn't see them every day. 

If you've noticed some common entries and know why they are in your diagnostics data, feel free to [reach out](mailto:joe@joecaiati.info). I'd love to keep this a running list.

### Problematic Entries

#### Springboard

Think of Springboard like the Finder in Mac OS X. Sometimes Finder locks up, crashes or needs to be relaunched. On a healthy Mac, this should happen close-to-never, but it isn't uncommon to run into it a few times. The same rules apply with Springboard on iOS.

Springboard is what runs your iPhone's home screen. If you've ever experienced a Springboard crash, it's when your device cuts to the Apple logo for about 5-7 seconds then goes back to the lock screen. This is shorter than a complete device reboot.

If Springboard crashes are something you are commonly seeing - even a few days per week - I would back up your device, erase your iPhone and restore from your backup. Keep in mind, if your device continues to crash the Springboard, your backup may be corrupt and you will have to erase and set up as a new device.

#### App Crash

Sometimes when an app is problematic, it is obvious. You see it freezing, hanging or crashing to the home screen. But there are times when an app could be malfunctioning in the background and one way to see that is if the app name shows up in your Diagnostics & Usage data. Like with Springboard, a few entries aren't a problem, but seeing 15-20 happening repetitively each day usually points to a faulty application. These entries may start with the words "LatestCrash" preceding the app's name.

The good news is that most of the time this can be resolved by deleting the application and reinstalling it from the App Store. In certain cases, the app may be poorly developed and I'd recommend looking at alternatives.

If it's a first party app in the logs, then an OS re-install would be in order.

#### Panic

![panic](http://s.mlkshk.com/r/161M8)

I've saved the worst for last. Entries ending in "panic" or "panic.plist" have historically meant that your iOS device needs to be replaced due to faulty hardware. In Mac OS X, kernel panics aren't as clear-cut. They could be caused by software or hardware issues and although technically panics work the same way when it comes to iOS, I've never personally seen an iOS device with a "panic.plist" not have to be replaced.

The symptoms that I've seen which would cause a "panic.plist" entry are random device reboots and random device shut-offs where the device gets very hot and can only be turned back on with a hard reset connected to power.

If you are seeing these entries and symptoms, I'd recommend booking a Genius Bar appointment as soon as possible.

### Unknowns

With iOS and watchOS evolving on a yearly basis, new entries are bound to appear in the Diagnostics & Usage Data section. I'm sure we aren't meant to know what they all mean, but I hope this has alleviated some curiosity or anxiety about the data that lives there now.
