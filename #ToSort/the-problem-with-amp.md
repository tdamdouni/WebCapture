# The Problem With AMP

_Captured: 2017-01-18 at 01:55 from [80x24.net](https://80x24.net/post/the-problem-with-amp/)_

Google's Accelerated Mobile Pages or [AMP](https://www.ampproject.org/) is a markup language similar to HTML that allows publishers to write mobile optimized content that loads "instantly". AMP is Google's response to both the Apple News Format and Facebook's Instant Articles. The goal of the AMP project is to make websites faster by essentially disabling external JavaScript and caching all pages on Google's CDN. While the intentions of the project seem good, there are a number of issues with AMP that both promote lock-in and provide a poor user experience.

## Poor User Experience

Many of the AMP links to pages are either broken or do not load properly despite their HTML equivalents working flawlessly. As of the time of this writing, I am having trouble loading Reddit pages with an AMP link. The exact same link to the HTML version loads correctly. For pages from sites that do manage to load, many are missing important content elements that have been accidentally excluded during the AMP HTML generation process. I have run into issues with tabular data on wordpress.com sites that fail to load without any indication that something has gone wrong. These bugs are simply unacceptable for a standard that has been in use and promoted by Google for over a year, and there have been [numerous](https://productforums.google.com/forum/#!topic/webmasters/8ogdv04Cm-k/discussion) [complaints](https://shkspr.mobi/blog/2016/11/removing-your-site-from-amp/) from users about AMP.

The largest complaint by far is that the URLs for AMP links differ from the canonical URLs for the same content, making sharing difficult. The current URLs are a mess. They all begin with some form of `https://wwww.google.com/amp/` before showing a URL to the AMP version of the site. There is currently no way to find the canonical link to the page without guessing what the original URL is. This usually involves removing either a `.amp` or `?amp=1` from the URL to get to the actual page.

## Lock In

Make no mistake. AMP is about lock-in for Google. AMP is meant to keep publishers tied to Google. Clicking on an AMP link _feels_ like you never even leave the search page, and links to AMP content are displayed prominently in Google's news carousel. This is their response to similar formats from both Facebook and Apple, both of which are designed to keep users within their respective ecosystems. However, Google's implementation of AMP is more broad and far reaching than the Apple and Facebook equivalents. Google's implementation of AMP is on the open web and isn't limited to just an app like Facebook or Apple.

If you want to avoid AMP, it is a lot easier to stop using the Facebook app or Apple News app than it is to avoid Google search. Google is the gateway to the web at large and is the doorway to information access in a way that Facebook will never be. Facebook might be the gatekeeper of social, but Google is the gatekeeper to a far larger and more meaningful set of information stored on the web - anything from cat pictures to scientific research. It's disappointing to see Google promoting a closed standard under the guise of an open one.

Google insists that AMP is not a factor in a site's search ranking. However, AMP compatibility **does** determine whether or not publishers are featured in the much coveted news carousel. This, in effect, forces publishers to start using AMP regardless of how fast their site loaded previously.

Google has the ability to further change the AMP HTML specification to keep publishers in their ecosystem. Google already makes deleting AMP pages [difficult](https://developers.google.com/amp/cache/update-ping). Despite touting AMP HTML as an open standard, every one of the AMP Project's core developers appears to be a Google employee. Google's own [governance policy](https://www.ampproject.org/it/contribute/governance/) for AMP HTML states the following.

> There is a single Tech Lead, who will have the final say on all decisions regarding technical direction. The Tech Lead directs the Core Committers, whose members include the Tech Lead and those who have been appointed by the Tech Lead as Core Committers. In the event the Tech Lead is unable to perform his or her duties, or abdicates, the Core Committers can select a new Tech Lead from amongst themselves. In the event there are no Core Committers, Google Inc. will appoint one.

This keeps the AMP HTML specification squarely in the hands of Google, who will be able to take it in any direction that they see fit without input from the community at large. This guise of openness is perhaps even worse than the Apple News Format, which at the very least does not pretend to be an open standard.

## Privacy And Security Issues

The AMP HTML Specification states that all AMP HTML pages must load a JavaScript file from `https://cdn.ampproject.org/`. If you already run Google Analytics on your pages you probably don't care that you're loading yet another black-box JS file from Google. But sites that load absolutely nothing from external sources (such as this one) should understand the privacy and security implications that come along with running JavaScript that you don't control.

If only for the (albeit somewhat small risk) of a compromised CDN server sending your users malicious JavaScript, appropriate care should be taken when resources are loaded from an external source. Techniques such as [subresource integrity](https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity) should be used where appropriate.

For something that is supposedly considered an open standard, requiring JavaScript and then forcing users to load that JavaScript from an external source should give any privacy conscious site pause. I hope that Google amends the specification to allow its users to load the required scripts from a location of their choosing.

## Conclusion and What You Can Do

Google's goals with the AMP Project are laudable, but there are major security and UX concerns that need to be addressed. In its current form, AMP is bad for the open web and should be changed or eliminated.

In the mean time, if switching away from Google is not an option for you and you dislike AMP, switch to searching from <https://encrypted.google.com/> on your device. AMP does not appear to be enabled here and I have successfully avoided the pages for the past few weeks.
