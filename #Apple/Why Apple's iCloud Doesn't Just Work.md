# Why Apple's iCloud Doesn't Just Work

_Captured: 2015-09-26 at 17:11 from [readwrite.com](http://readwrite.com/2012/08/23/why-apples-icloud-doesnt-just-work)_

![](http://a3.files.readwrite.com/image/upload/c_fit,cs_srgb,dpr_1.0,q_80,w_620/MTIyNDM2NjU4NzQ1MzQ0NjE0.jpg)

"It just works," the Apple marketing slogan goes. But for the syncing features in iCloud, that promise has proven too good to be true. On Thursday, the first iOS app launched that eschews iCloud in favor of a new third-party service called Simperium. If you use an iPhone or iPad, you'll want to know why.

iCloud is not a discrete thing. It's actually an ad hoc bundle of different syncing technologies, and they're just buggy enough to be unsettling to users. We take Apple at its word that "it just works," but every so often, an app that syncs with iCloud takes five or ten painful seconds to open. This only has to happen once in a hundred times to shake our faith in the system.

Our instinct is to blame the app when it's actually iCloud's fault. Greg Pierce, the developer at [Agile Tortoise](http://agiletortoise.com/) released [Drafts 2.0 and Drafts for iPad](http://agiletortoise.com/drafts) Thursday, and he decided to avoid this problem.

Drafts ([which I love](http://www.readwriteweb.com/archives/drafts_for_iphone_write_first_then_act.php)) is the quickest way to jot anything down on the iPhone, and now it syncs to the iPad version. But rather than take the heat for iCloud's problems, Pierce decided to make Drafts the first app to sync via third-party provider [Simperium](https://simperium.com/).

## **Building Drafts 2.0**

"Drafts is designed around speed and simplicity," Pierce says, "so I knew the right sync solution would have to be fast and simple."

[Dropbox](http://dropbox.com) is a proven option for syncing whole documents, but that's not how Drafts works. Drafts saves all your notes in one database, which makes the app faster, but Dropbox sync would be much slower than a solution that can just sync little changes to the one big database.

So Pierce initially considered iCloud's Core Data syncing, which is designed for exactly this. "Many of the initial setup steps were deceptively easy," Pierce says, "but as I dug deeper into providing a complete implementation, it became clear to me that I was going to find many rabbit to chase."

The first problem was speed, which is pretty much the selling point for Drafts. iCloud sometimes slows an app's launch to a crawl, a deal-breaker for Drafts.

The other problem Pierce found with iCloud was more philosophical. iCloud syncing is restricted to apps sold within Apple's App Stores. As of now, there's no way for Web-based apps to sync with iCloud, nor for Mac apps sold outside the App Store or on other platforms. While Pierce has no specific plans for Drafts to sync more widely, he wanted to give himself the flexibility to build it later.

So when you first launch Drafts 2.0 on your phone or Drafts on your iPad, you'll be prompted to sign up for Simperium if you want syncing features. All you need is an email address and a password, and you're likely to see Simperium in more apps in the near future.

## **What The Heck Is A Simperium?**

[Simperium](https://simperium.com/) is actually the in-house syncing service for the beloved note-taking app [Simplenote](http://simplenoteapp.com/), but the company has decided to abstract it and make it available for other developers to implement.

"You can think of Simperium as a post-PC circulatory system for data," co-founder Mike Johnston says. It's built to speak to all kinds of devices and services and be easy to implement. "The result is that developers can use Simperium like a Lego brick," snapping together different applications and devices with data that fits, allowing "pretty much any feature where data needs to move quickly and reliably from one place to another."

## **Why Is Sync So Hard?**

The short answer for why syncing doesn't "just work" is that conflicts in the data always pop up. "Conflicts happen a lot more often than many developers realize, especially at scale," Johnston says. "The symptoms are duplications, corruption, or in the worst case, outright data loss, all of which are unacceptable."

iCloud handles the headache of resolving conflicts, but it does so at great cost, such as preventing the app from loading while it sorts things out. "It pains us to see apps, some of them very prominent, with bad syncing, or no offline support, or interfaces that block the user while waiting for network data," says Johnston. "These are inexcusable user experience blunders."

Sync was one of Pierce's most requested features for Drafts after it launched on the iPhone. It sure is convenient for our data to sync everywhere. But the implementation of that magic is much more delicate than meets the eye. Pierce found a solution that works, and if you [check out the new Drafts](http://agiletortoise.com/drafts), it surely won't be the last time an app asks you to log into Simperium.
