# How many third parties allow site owners to measure their performance?

_Captured: 2017-08-08 at 19:56 from [www.lognormal.com](http://www.lognormal.com/blog/2017/07/25/a-study-of-timing-allow-origin/)_

![A Page Waterfall using Resource Timing data from mPulse](http://www.lognormal.com/blog/assets/timing-allow-origin/resource-waterfall.png)

Web site owners need to monitor the performance of their site, and measuring how long things take to load is a significant part of that. While measuring the performance of assets you own is straightforward, measuring the performance of third-party assets is not.

This brought me to an important question: How many third parties allow site owners to measure their performance?

## Jump Forward

If you're already familiar with RUM and Resource Timing, you can skip the definitions and [jump straight to the investigation and results](http://www.lognormal.com/blog/2017/07/25/a-study-of-timing-allow-origin/).

## Definitions

### Where's the Party?

For the purpose of this post, the term first-party refers to any domain and assets on that domain that will pass the browser's [Same-Origin Policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy). Any domains that do not pass the Same-Origin Policy are considered non-first-party. Some of these non-first-party domains may be under your control.

For example, if you visited `https://www.akamai.com/`, you'd find many assets that were loaded from `https://www.akamai.com/`, but you'd also find assets loaded from `https://ds-aksb-a.akamaihd.net/`, `https://www.google-analytics.com/`, and others. The assets loaded from `https://www.akamai.com/` are considered first party, while all others are considered non-first-party. So even though `ds-aksb-a.akamaihd.net` is owned by Akamai, it is not a first party domain as it differs from the domain of the origin page.

The term third-party refers to any non-first-party that is not within your control (`www.google-analytics.com` in the example above), and we won't bother too much about this.

With those definitions out of the way, let's move on to measuring performance.

### Real User Measurement

When studying the performance of your web site, it is important to measure the actual user's experience with all of its uncontrolled factors rather than a controlled synthetic experience.

The process of measuring the experience of a Real User of the site, while they browse your site, is called Real User Measurement, often abbreviated as RUM. RUM libraries, like [boomerang](https://github.com/soasta/boomerang) (used by Akamai's [mPulse RUM](https://www.soasta.com/performance-monitoring/) tool), use various methods to collect user perceived performance in the browser. Among these methods are browser APIs like [Navigation Timing](https://www.w3.org/TR/navigation-timing/) and [Resource Timing](https://www.w3.org/TR/resource-timing-2/).

### The Resource Timing API

The Resource Timing API gives you timing information about all of the assets (images, scripts, css, [custom fonts](https://developer.akamai.com/blog/2017/07/25/performance-usage-implications-custom-fonts/), etc.) on the page.

This works well for first-party assets, and gives you access to detailed timing information like how long the request was blocked, how long the browser took to do a DNS lookup, a TCP connect, an SSL handshake, get the first byte of the response and complete loading. We also have access to size information like the number of bytes over the wire (`transferSize`), and the number of bytes of the asset, both compressed (`encodedSize`) and uncompressed (`decodedSize`).

### Non-first-parties & privacy aspects of the Resource Timing API

For non-first-party assets, unless the Timing-Allow-Origin response header is explicitly set, we only get the time the browser intended to download the asset (`startTime`) and the time it completed downloading (`responseEnd`). Additional timing and byte size information is omitted.

This is to prevent scenarios such as an evil site using the data to fingerprint users by surreptitiously loading an asset (for example, the facebook.com css) in the background, and using timing or size analysis to detect if the asset is cached or not. More sophisticated timing or size attacks can even be used to detect the user's facebook [username](https://littlemaninmyhead.wordpress.com/2015/07/26/account-enumeration-via-timing-attacks/) or [zip code](https://www.reddit.com/r/netsec/comments/52kpzv/profiling_site_visitors_by_timing_attacks_on/).

### The Timing-Allow-Origin header

Non-first-parties can opt-in to detailed timing information using the Timing-Allow-Origin header, giving sites that include their assets permission to collect performance data of these assets from the browser. This is especially useful in the case of critical third-party assets such as JavaScript CDNs, so that site owners can understand how well the content is being delivered to their customers.

The owner of a non-first-party domain, for example, `google-analytics.com`, could add a `Timing-Allow-Origin: *` header to its responses to indicate to the browser that reporting detailed timing and size information is acceptable for all page domains that include the asset. They could also be a little more strict and specify a domain, for example, `Timing-Allow-Origin: https://www.akamai.com` indicating that only pages on `https://www.akamai.com/` could access detailed timing and size information.

![Donut chart showing relative population of responses with TAO on v/s off](http://www.lognormal.com/blog/assets/timing-allow-origin/tao-on-off.png)

## Do non-first party domains enable Timing-Allow-Origin?

I looked at resource timing data across multiple customers to determine if non-first-party domains included a suitable Timing-Allow-Origin (TAO) header or not. For the purpose of this study, any domain that was not the same as the main page is considered a non-first party domain, so some of these domains may have been the CDN used by the first party.

All results are from mPulse Real User Monitoring (RUM) data over 15 days.

To determine if the `Timing-Allow-Origin` header is set, I ran two checks.

  1. If the hit contains Resource Timing Level 2 data like `transferSize` or `decodedSize`, then TAO is set.
  2. If neither of the above fields are present, we look to see whether the hit had a non-zero `responseEnd` AND a non-zero `responseStart`. If both are non-zero, then TAO is set, if both are zero, then the result is indeterminate. If `responseEnd` is non-zero but `responseStart` is zero, then TAO is not set.
![Donut chart showing relative population of cached responses v/s uncached](http://www.lognormal.com/blog/assets/timing-allow-origin/cache-on-off.png)

We also look at the size and timing fields to determine if the resource was served from cache or over the network. Identifying if a resource is cached or not helps us better determine the effects of the TAO header on assets fetched over the network.

Overall I found that only 18% of all non-first-party requests (across domains) have a response with a suitable `Timing-Allow-Origin` header set. While one third of all assets were served from a local browser cache.

This combination of factors makes it hard for site owners to determine the total byte size of assets on their pages as experienced by real visitors to their site, and to set download policies for low bandwidth or metered connections based on asset size. For many site owners, this data is useful in setting an SLA for their third party service providers.

### How are domains using Timing-Allow-Origin (TAO)?

As expected, we found that more than half of all domains do not include a suitable `Timing-Allow-Origin` response header. But what was surprising was that very few of the domains we looked at included the header on all their responses.

![Donut chart showing breakdown of domains by how prevalent the TAO header is on their responses.](http://www.lognormal.com/blog/assets/timing-allow-origin/ab-testing-tao.png)

What is more common are domains that include the header only on some, but not all responses. We have a few guesses for why this might be.

  1. They may set it only for some assets and not all to protect the user's privacy for user specific assets (eg: `Cache-control: private` type resources)
  2. There could be a browser bug at play.
  3. The domain might be A/B testing the feature.
  4. They might have accidentally only configured some hosts behind a load balancer.

In investigating the data further, we found that a few of these anomalous cases were in fact caused by a browser bug where a particular browser leaked `responseStart` values for domains that did not have the `Timing-Allow-Origin` header set. We've reported the bug to the vendor in question.

I found that among domains that did include the TAO header, the majority were using it at a sampling rate of less than 10%.

Only 6.4% of domains had the TAO header on for more than 40% of responses, but still hadn't committed to it completely.

### Domain breakdown

Looking at a sample of the most popular non-first party domains sorted alphabetically, we notice that Google tag services, DoubleClick (from Google), AkamaiHD & Facebook.net include the `Timing-Allow-Origin` header in their responses most of the time.

![Bar chart showing prevalence of the TAO header by domain sorted alphabetically](http://www.lognormal.com/blog/assets/timing-allow-origin/tao-domains.png)

Other Google services such as `google-analytics.com`, `google.com`, `googleadservices.com`, `googleapis.com`, `googlesyndication.com`, and `gstatic.com` are far lower. Similarly, `facebook.com` at 5% is significantly lower than `facebook.net` at 84%.

Presumably these service providers have fine-grained control over who can read timing information from each of their service endpoints, and even different results for different asset types.

### Does asset type have an effect?

![Donut chart showing a relative population breakdown of assets by type.](http://www.lognormal.com/blog/assets/timing-allow-origin/asset-types.png)

The next question that came up was whether services were setting the `Timing-Allow-Origin` header only for certain types of content. It is not easy to determine the actual content type of an asset from JavaScript, but we can make assumptions based on the initiator type field and the filename of the asset.

Looking at a breakdown of the number of requests by asset type, we see that Scripts and Images make up the bulk of all assets by hit count, however when we take byte size into account, JavaScript accounts for 58% of the bytes sent over the network.

We looked at the usage of `Timing-Allow-Origin` across asset types, and it wasn't great. Font files and Beacons, which were the least populous assets, had 100% TAO coverage. Scripts were the next most likely asset type to have the TAO header set, at 33% coverage. Images, including background images loaded from CSS, and CSS files were the next most likely at 8%.

Looking at our earlier numbers but limiting them to only script assets, we find that some of the domains with low TAO usage suddenly shoot up. In particular, `google-analytics.com`'s usage of TAO is at 96% when we only look at JavaScript. This agrees with our earlier hypothesis that large sites might control usage of TAO based on the asset type served and the privacy policies they've set around each of those assets.

### Correlation with performance

When I showed my preliminary results to a few people, the guess was that the only people who turn on the TAO header are those whose performance was already good. There are various problems with this logic that we won't go into here.

Just for fun though, I checked if there was a correlation between whether the TAO header was turned on or not, and the download latency of an asset. I separated domains and asset types to run this correlation, and excluded anything with an unknown asset type as there could be multiple asset types within that group that would confound the results.

The x-axis of this chart is the percentage of hits for a domain + asset type combination that had the TAO header set, while the y-axis is the percentage change in asset load time over the non-TAO scenario. Positive is an improvement while negative is a degradation.

![Scatter plot showing correlation of TAO usage with performance improvements broken down by cached v/s uncached assets](http://www.lognormal.com/blog/assets/timing-allow-origin/tao-corr-speed.png)

> _To avoid data skew caused by cached assets, I split the data by whether assets were served out of browser cache or not._

It is very important to note while reading this chart, that because of the way the x-axis is set up, the extrema have a huge data imbalance between the on and off groups, so only the (largely sparse) middle of the chart can be truly considered reliable. This chart is, **_only for fun_**.

The interesting thing here is that the results were completely different for cached and uncached assets. Cached assets, which make up 33% of all requests, showed performance get worse as use of `Timing-Allow-Origin` increased, while assets requiring network requests showed an improvement.

It is tempting to conclude that only domains that have fast assets are willing to use the `Timing-Allow-Origin` header to expose these timings. What is more likely is that sites that do include the TAO header are more performance aware, and having the header turned on allows them to identify performance problems faster.

As an example, when mPulse beacons back performance data for a page, it also includes resource timing information for all our own assets. This helps us identify and fix performance problems before they become a major issue.

## In Conclusion

  * The Timing-Allow-Origin header is not very prevalent across non-first party domains (18% usage).
  * For domains that do use it, its use fluctuates greatly by asset type. Fonts and Beacons, which are the least used assets are the most likely to have the _TAO_ header set. JavaScript, the second most popular asset type is the next most likely to have the _TAO_ header set.
  * Domains that use _TAO_ a lot have better performing assets with _TAO_ turned on than with it turned off.
  * For every browser feature that you try to use, there will be browser bugs that make your implementation harder.

## Acknowledgements

I'd like to thank [Iris Lieuw](https://twitter.com/irislieuw) for her help with data visualization and [Yoav Weiss](https://twitter.com/yoavweiss), [Charlie Vazac](https://twitter.com/vazac) and [Simon Hearne](https://twitter.com/simonhearne) for suggestions and help editing this blog post.
