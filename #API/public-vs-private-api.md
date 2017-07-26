# Public vs. Private API

_Captured: 2017-03-07 at 02:11 from [dzone.com](https://dzone.com/articles/public-vs-private-api?edition=273885&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-06)_

_[This article is featured in the new DZone Guide to the Cloud: Native Development and Deployment. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/the-cloud-native-development-and-deployment?oid=cloudarticles)_

For those developers who are old enough to remember, it's with mixed parts nostalgia, disgust, and/or amusement that we recall the troubles Microsoft had with "undocumented APIs" back in the early 1990s. The subject of numerous conspiracy theories (and not a few books, including such icons as Undocumented Windows and Windows Internals , not to mention their nominal kin Undocumented DOS and others like them), the notion of an "undocumented" API call and its reasons for existence has seen much debate, discussion, and--so we thought--retirement. But if it's one thing age teaches us, it's that what's old is eventually new again.

Recently, debates began to rage around "APIs" and their legal status (looking at you, Google and Oracle!). With the proliferation of Web APIs (looking at you, uh... Internet!), the whole subject of "APIs" and their openness is starting to creep back upon us. More commonly, however, it seems that as more and more companies are moving to a REST-centric or -influenced style of architecture (particularly for mobile applications), companies are developing these Web APIs initially as something entirely for internal use, and only belatedly considering making them open to the rest of the world, usually after some kind of external or internal pressure to do so.

## Private Web APIs?

For many API developers, it's not clear what a "private Web API" would be or look like; to ensure that we're all on the same page, very simply, a private Web API would be an HTTP endpoint that isn't advertised to those who consume APIs (meaning developers, for the most part).

To be fair, for many developers, it doesn't start this way. The internal monologue usually begins with the realization that building a web application could/will end up having a mobile app (or two) as close kin, and that therefore some kind of centralized logic is necessary and desirable. "HTTP is ubiquitous," they nod sagely, "So let's use that." Before long, however, doubt creeps in: "Will this be something that others will want to consume? Will they consume it the same way as the web and mobile apps will? Perhaps the 'outside world' needs a simpler version of the API, but my internal needs are more complicated. Maybe the best path to take is to keep it obscured, at least to start."

Sometimes, the API implementors will take some step to make the API less discoverable, such as making it accessible only from machines inside a VPN, or restricting the IP range of acceptable incoming clients. In some cases, it's as simple as "If we don't tell them, they won't know." If the parameters to the API calls aren't described somewhere, nobody "unauthorized" to use them can, right?

Thus, on the surface, it would seem this discussion is entirely moot: so long as an API is accessible to callers, it would seem to be, by definition, accessible and therefore public. However, in an interesting twist, the same is true of the Windows environment thirty years ago: armed with only a few command-line tools (DUMPBIN.exe, shipping with every version of Visual C++/Visual Studio since 1992) and a basic knowledge of how the Portable Executable format is written (such as this article from 1994: ([bit.ly/2l9tIme](https://msdn.microsoft.com/en-us/library/ms809762.aspx)), any developer could discover method-entry points that weren't in the formal documentation set. Despite the ease with which an API could be discovered by anybody with basic knowledge of the system, Microsoft (and others) still left certain APIs to be undocumented and, presumably, untouched by their developer-consumers.

In the 2017 era, those tools are already bundled in every web browser and/or accessible via the command-line on most operating systems. HTTP, after all, is a far simpler standard than the Common Object File Format. Why, then, might a company consider creating Web APIs, only to leave them unpublished?

_Read the rest of this article and a lot more in:_

![Cloud Guide](https://dz2cdn1.dzone.com/storage/rc-covers/4448764-dzone-2017cloudcover.png)

**[DZone's Guide to the Cloud:** Native Development and Deployment](https://dzone.com/guides/the-cloud-native-development-and-deployment?oid=cloudarticles)

Including:

  * Industry Research Data
  * Articles Written by Industry Experts
  * Cloud Architecture Infographic
  * Directory of the Best Tools & Solutions
