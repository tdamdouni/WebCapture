# Why the iPad Pro needs Xcode

_Captured: 2015-11-13 at 09:36 from [medium.com](https://medium.com/@stevestreza/why-the-ipad-pro-needs-xcode-8335ee787a09)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*kRcx7nWCcsmxT3DKYLUkVw.png?q=20)![](https://cdn-images-1.medium.com/max/800/1*kRcx7nWCcsmxT3DKYLUkVw.png)

> _"It kind of looks like a blown-up smartphone app. That's because that's exactly what it is." -- Tim Cook_

On March 7, 2012, Tim Cook [announced](http://events.apple.com.edgesuite.net/123pibhargjknawdconwecown/event/index.html) their 3rd-generation "New iPad", leading into it with a (fair and justified) dig at the state of Android tablet apps. Apps like Twitter and Yelp were shown as they ran at the time, with a smartphone-based UI stretched out to fit the wider display. Cook made jokes about apps being hard to see, with small text and lots of whitespace.

The prospect of building iPad apps has not been as popular for developers as building for iPhone. At the same time, iOS as a platform went from having a couple fixed screen sizes to requiring developers design their apps to be flexible. In an effort to bring more iPhone apps to iPad, Apple developed the concept of [Adaptive UI](https://developer.apple.com/design/adaptivity/), pushing developers away from targeting screen sizes to targeting flexible rectangles with certain size properties.

What Apple wanted to happen was that developers would build a compact UI, and a full-size UI, and the library of iPad apps would naturally expand to have a lot of what was on iPhone. But that didn't really happen. What happened instead was that many developers design and target for iPhone, then fudge and fiddle with that UI until it looks okay on iPad, leading to (in the worst case) things like what Twitter's iPad app has now become.

App developers don't feel this pain as much, because they're not living on iPad. For 8+ hours a day, they're stuck using Xcode on a Mac. They aren't living and breathing the idioms and design patterns of great iPad apps. Instead they're stuck on Macs, usually sitting on desks with mice or trackpads, using a very underpowered and unwieldy iPad simulator, to build apps you touch with your hands on the couch.

Xcode running directly on the iPad Pro could fix many of those problems. You now have a tablet powerful enough to run an IDE, with a very nice keyboard cover, and a screen big enough to encompass all the functionality of Xcode, capable of testing almost every feature of every iOS device ever made. You can code with your keyboard and test with multitouch. You could work on a desk and take your whole development environment with you on the couch, bed, or plane.

And let's not forget about the benefit to students that have long been argued. Many kids today are tablet-native, never having grown up with a PC. Today, there's no way for them to learn to code. And who better to build the next generation of incredible iPad apps than those who grew up with them? Young coders need to own both a Mac and an iPad to build software for it, learning Xcode and navigating provisioning notwithstanding.

In many ways, Xcode on iPad Pro would be the ultimate mobile developer platform. It would lead to better iPad apps, built by engineers who can now live and breathe iPad, and young people who already do. It won't happen overnight. But you'll slowly see more apps build toward universality, rather than being chained to a portrait iPhone.
