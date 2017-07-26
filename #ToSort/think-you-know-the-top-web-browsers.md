# Think you know the top web browsers?

_Captured: 2017-04-16 at 11:14 from [medium.com](https://medium.com/samsung-internet-dev/think-you-know-the-top-web-browsers-458a0a070175)_

## Our traditional idea of the top five browsers may be over-simplified, outdated and skewed.

If you attend web developer events in much of Europe and North America, inevitably you will see the same browser logos keep cropping up in the speakers' slides:

![](https://cdn-images-1.medium.com/max/1600/1*b9Q1ffCZBKb4_fVlQfEtZQ.png)

> _You've probably seen lots of slides that look like this._

Chrome, Firefox, Safari, IE/Edge, Opera… It is a common idea that these are the five "major browsers". Our familiarity with them is comforting, but it might be a skewed and outdated view. Partly from our Western bubble and partly a hangover from the days of desktop dominance.

Let's take a look at some numbers so we can better represent the reality.

#### All platforms

First, let's go as broad as we can: all platforms (desktop, tablet, mobile), worldwide. Here's the top five, in order, according to [StatCounter](http://gs.statcounter.com/browser-market-share):

![](https://cdn-images-1.medium.com/max/1600/1*sXGVai4dCOrvTuu0QtPPEg.png)

> _Source: StatCounter, Feb 2017. Percentages rounded to nearest whole number. *Note: I've used the Edge logo, but these stats do not break out Edge and Internet Explorer._

Hey there's a weird orange logo in the middle! That's [UC Browser](https://en.wikipedia.org/wiki/UC_Browser) -- originated in China and owned by Alibaba Group -- which has a notable market share, particularly in Asia.

This is an important point. The browser market share can vary a lot depending on location.

For example, in Russia (population: [143 million](http://www.worldometers.info/world-population/russia-population/)), [StatCounter suggests](http://gs.statcounter.com/browser-market-share/all/russian-federation/#monthly-201603-201703) Chrome is on top as we would expect, but guess which comes second? It's one we don't tend to see mentioned much here: [Yandex](https://en.wikipedia.org/wiki/Yandex_Browser).

![](https://cdn-images-1.medium.com/max/1600/1*aqNz6qk1LxZufQYJKFzg7A.png)

> _[Yandex](https://en.wikipedia.org/wiki/Yandex_Browser) logo_

#### Mobile

We know that mobile is "[eating the world"](http://a16z.com/2016/12/09/mobile-is-eating-the-world-outlook-2017/). In fact, StatCounter recently announced that, according to their data, [Android has now surpassed Windows as the world's number one Internet platform](http://gs.statcounter.com/press/android-overtakes-windows-for-first-time). However, out of habit, we still tend to think about desktop by default!

So let's take a look at mobile browsers. StatCounter suggests a different set again:

![](https://cdn-images-1.medium.com/max/1600/1*9HmuRgFVqoSjgSm3V2dMxA.png)

> _Source: StatCounter, Feb 2016 to 2017. Percentages rounded to nearest whole number. *Note: I've used the Opera Mini logo, but these stats do not break out Opera Mini, Opera Mobile and Opera Coast._

Hey now there's a strange purple logo - our [Samsung Internet](https://medium.com/samsung-internet-dev/introducing-samsung-internet-for-developers-6c3a3be42f72)! StatCounter suggests it's a [top 3 mobile browser in Europe](http://gs.statcounter.com/browser-market-share/mobile/europe/#monthly-201602-201702), with over 15% market share in some countries:

![](https://cdn-images-1.medium.com/max/1600/1*oyJuuhaXxwL96KEks0NaVQ.png)

> _Mobile browser market share in Germany. Source: StatCounter, Jan 2017 to Feb 2017_

As for Opera on the right -- [in 2016 Opera shared](https://www.opera.com/blogs/news/wp-content/uploads/sites/2/2016/11/SMWAfrica-Opera-report-2016-01-WEB-1.pdf) that Opera Mini was Africa's favourite browser, with an impressive 58% market share.

#### Challenging our assumptions

Business coaches often teach us to recognise and challenge our own assumptions. Our assumptions about browser market share should be no different. The data may tell a different story.

I've referenced StatCounter above, but I would also suggest seeking multiple sources. Although StatCounter's data are aggregated from [over 3 million websites](http://gs.statcounter.com/about), it should still only be considered an approximate picture of reality. You may get some anomalies, especially when you narrow down on specific geographies and platforms.

#### Is the best data your own data?

In general it's probably best to pay most attention to your own analytics. However, this could be misleading too. Some analytics providers appear to be confused by the user agent strings and do not break out browsers like Samsung Internet (which is based on Chromium) correctly. For example, if you rely only on Google Analytics, you may not be seeing the whole story:

Also, if you simply focus on the browsers of your existing users, you might fail to spot the trends for your _potential_ users. Bruce Lawson covers this brilliantly in "[World Wide Web, Not Wealthy Western Web"](https://www.smashingmagazine.com/2017/03/world-wide-web-not-wealthy-western-web-part-1/):

> When I speak at conferences in rich Western countries, I often ask people, "Where will your next customers come from?" You don't know. In our truly worldwide web, you _can't_ know.  
-- [Bruce Lawson](https://www.smashingmagazine.com/2017/03/world-wide-web-not-wealthy-western-web-part-1/)

#### Browsers everywhere

So do you really know which are the top browsers, both amongst your existing customers and your potential audience? Perhaps it's worth taking a closer look; it might just be time to check your site in some of the lesser-known, yet popular browsers like UC, Yandex and Samsung Internet.

And next time you're making a slide to share about browser support, or see someone else present one, please take a moment to consider: is this based on assumptions, or on data? Why not update it to include the top browsers globally, or -- like [Ada](https://medium.com/@Lady_Ada_King) [did recently in Bulgaria](https://twitter.com/Lady_Ada_King/status/849997167452446720) -- for the location of your audience? You may find Cătălin Mariș's [browser-logos repository](https://github.com/alrra/browser-logos) helpful!

![](https://cdn-images-1.medium.com/max/1600/1*Dg8dR-vyRRqQIQC_UEc1-Q.png)

> _Many browsers… Mobile browser logos from alraa/browser-logos. NB. The purple one is our new Samsung Internet logo, currently in beta and coming soon to stable!_

There may be more browsers out there than we care to think, but as my colleague [Diego](https://medium.com/@diekus) shared, thankfully they are all based on our open web standards: _[Many browsers, one Web_](https://medium.com/samsung-internet-dev/many-browsers-one-web-21730352afbc)_!_

**_Update:_**_ Peter Gasston __[made a great point_](https://twitter.com/stopsatgreen/status/852530928383557632)_ that a very major "browser" (well, a WebView) I have not mentioned here is __[Facebook_](https://twitter.com/stopsatgreen/status/836174049873125377)_. Another example of the frequent omissions in the "browsers" we think and talk about!_
