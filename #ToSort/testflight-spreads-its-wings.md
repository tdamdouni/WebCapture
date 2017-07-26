# TestFlight Spreads Its Wings

_Captured: 2017-05-06 at 17:59 from [dzone.com](https://dzone.com/articles/testflight-spreads-its-wings-under-the-bridge?oid=twitter&utm_content=buffer14ca4&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190139&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190139&u=https%3A%2F%2Fwww.wakanda.io%2F).

You catch the [latest TestFlight news](https://developer.apple.com/testflight/) just now? This looks pretty [interesting](https://developer.apple.com/news/?id=04112017a):

![Image title](https://dzone.com/storage/temp/5119876-screen-shot-2017-04-28-at-12920-pm.png)

Well doesn't that just sort a whole lot of issues we routinely run into, am I right? Sure we can play games with app IDs and icon tagging and whatever, not even going to bother linking to our various posts on tips and tricks for that kind of thing, but this looks waaay easier_._

Mind you, we haven't actually distributed an app using Apple's incarnation of TestFlight yet- next one'll be the first. When [they first acquired it](http://www.alexcurylo.com/2014/02/21/testflight-r-i-p/) the "no iOS 7" thing was a flat out dealbreaker, and by the time that wasn't well we'd settled into a Crashlytics-centered flow nicely so eh, whatever dudes.

The first time it crossed our mind that, "hmmm...maybe we could rethink that," was this post last fall: [How Not to Crash #1](http://blog.supertop.co/post/152615019837/how-not-to-crash-1).

Interestingly, these crashes did not appear in our usual crash reporting service, HockeyApp, so it actually took us a while to realize that we had a problem. To be aware of all crashes, developers need to check for crash reports through iTunes Connect, or Xcode too…

Well, if we have to check them there, why bother checking other places too? Always like to streamline our process, being awesome DevOps dudes and all. But that wasn't enough to seriously consider going all in, until [a few weeks ago](http://www.alexcurylo.com/2017/01/19/fabric-r-i-p/) Google gobbled as Google gobbles and we were a tad miffed, you might recall.

Clearly this is great if you've already bought into [the Firebase platform](http://www.alexcurylo.com/2016/05/20/fire-up-the-base/), but if you haven't, there's a bit of thinking to do now, especially for those of us in businesses that Google actively competes with, so we have a smidgen of trepidation about handing over our collective user profiles and activity. Paranoid, yes yes, but hey- paranoids have enemies too.

So that was enough to prod us into actively researching alternatives. In our considered opinion [Bugsee](https://www.bugsee.com) is the best out there right now by a spectacular margin, oooh network logs would rock! But oh, come on dudes, we're an indie place here (OK, actually these days we're DevOps at [Agoda.com](https://www.agoda.com/) because Bangkok!) You actually think we can pay? Heh, that's cute. And yes yes, Dear Reader, your favorite is very nice too, but nothing else really struck us as worth the effort to switch to.

But this. This here, this actively solves recurring problems! And far as we're aware -- please correct us if we're wrong -- the only actual downside from a dev perspective remaining with TestFlight is that users can opt out of reporting, and then no doubt those that choose to are the exact ones that would get that one weird crash we'd get grumpies 1-starring us with no way to figure out WTF they're going on about, which would be … suboptimal. But, oh wait, [that problem's sorted now too](https://developer.apple.com/news/?id=03272017c), so … what's left as a practical objection to going all in on TestFlight for your iOS platform needs? Why, nothing we can see!

If there's anything we've still overlooked, please comment, but at first glance, our verdict is "yep, next project, no Google libs, all in Apple." We'll update here if any flaws arise in that cunning plan!

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190140&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190140&u=https%3A%2F%2Fwww.wakanda.io%2F).
