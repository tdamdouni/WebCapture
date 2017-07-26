# 3 reasons why you should let Google host jQuery for you

_Captured: 2015-12-11 at 16:16 from [encosia.com](http://encosia.com/3-reasons-why-you-should-let-google-host-jquery-for-you/)_

All too often, I find code similar to this when inspecting the source for public websites that use jQuery:

If you're doing this on a _public facing_ website, **you are doing it wrong**.

Instead, I urge you to use the [Google Hosted Libraries](https://developers.google.com/speed/libraries/devguide#jquery) content delivery network to serve jQuery to your users directly from Google's network of datacenters. Doing so has several advantages over hosting jQuery on your server(s): **decreased latency**, **increased parallelism**, and **better caching**.

In this post, I will expand upon those three benefits of Google's CDN and show you a couple examples of how you can make use of the service.

### Just here for the links?

If you've already read this post and are just here for the links, you're in the right place!

If you care about older browsers, primarily versions of IE prior to IE9, this is the most widely compatible jQuery version:

If you don't care about oldIE, this one is smaller and faster:

**Either way, you should use a [fallback to local](http://weblogs.asp.net/jongalloway/using-cdn-hosted-jquery-with-a-local-fall-back-copy)** just in case the Google CDN fails (unlikely) or is blocked in a location that your users access your site from (slightly more likely), like Iran or sometimes China. This is an example of using a local fallback with jQuery 2.x:

Now, on to the reasons why you should use these links.

### Decreased Latency

A CDN -- short for [Content Delivery Network](http://en.wikipedia.org/wiki/Content_Delivery_Network) -- distributes your static content across servers in various, diverse physical locations. When a user's browser resolves the URL for these files, their download will automatically target the closest available server in the network.

In the case of Google's AJAX Libraries CDN, what this means is that any users not physically near your server will be able to **download jQuery faster** than if you force them to download it from your arbitrarily located server.

There are a handful of CDN services comparable to Google's, but it's hard to beat the price of **free**! This benefit alone could decide the issue, but there's even more.

### Increased parallelism

To avoid needlessly overloading servers, browsers limit the number of connections that can be made simultaneously. Depending on which browser, this limit may be **as low as two connections** per hostname.

Using the Google AJAX Libraries CDN eliminates one request to your site, allowing more of your local content to downloaded in parallel. It doesn't make a gigantic difference for users with a six concurrent connection browser, but for those still running a browser that only allows two, [the difference is noticeable](http://yuiblog.com/blog/2007/04/11/performance-research-part-4/).

### Better caching

Potentially the greatest benefit of using the Google AJAX Libraries CDN is that **your users may not need to download jQuery at all.**

No matter how well optimized your site is, if you're hosting jQuery locally then your users must download it at least once. Each of your users probably already has dozens of identical copies of jQuery in their browser's cache, but those copies of jQuery are ignored when they visit your site.

However, when a browser sees references to CDN-hosted copies of jQuery, it understands that all of those references do refer to the exact same file. With all of these CDN references point to exactly the same URLs, the browser can trust that those files truly are identical and won't waste time re-requesting the file if it's already cached. Thus, the browser is able to use a single copy that's cached on-disk, regardless of which site the CDN references appear on.

This creates a potent "cross-site caching" effect which all sites using the CDN benefit from. Since Google's CDN serves the file with headers that attempt to **cache the file for up to one year**, this effect truly has amazing potential. With many [thousands of the most trafficked sites on the Internet already using the Google CDN to serve jQuery](http://encosia.com/6953-reasons-why-i-still-let-google-host-jquery-for-me/), it's quite possible that many of your users will never make a single HTTP request for jQuery when they visit sites using the CDN.

Even if someone visits hundreds of sites using the same Google hosted version of jQuery, **they will only need download it once**!

### Implementation

_Note: At the time I originally wrote this, Google used to recommend this loader approach, but no longer does. I'm leaving this section of the post intact, but you can skip to the next section unless you're planning on time traveling to 2008 someday._

By now, you're probably convinced that the Google AJAX Libraries CDN is the way to go for your public facing sites that use jQuery. So, let me show you how you can put it to use.

Of the two methods available, this option is the one that Google recommends:

> The google.load() approach offers the most functionality and performance.

For example:

While there's nothing wrong with this, and it is definitely an improvement over hosting jQuery locally, I don't agree that it offers the best performance.

![Firebug image of the longer loading time caused by jsapi](http://encosia.com/blog/wp-content/uploads/2008/12/jsapi-long-load.jpg)

> _Firebug image of the longer loading time caused by jsapi_

As you can see, loading, parsing, and executing jsapi delays the actual jQuery request. Not usually by a very large amount, but it's an unnecessary delay. Tenths of a second may not seem significant, but **they add up very quickly**.

Worse, you cannot reliably use a $(document).ready() handler in conjunction with this load method. The setOnLoadCallback() handler is a requirement.

### Back to basics

In the face of those drawbacks to the google.load() method, I'd suggest using a good 'ol fashioned <script> declaration. Google does support [this method](http://code.google.com/apis/ajaxlibs/documentation/#jquery) as well.

For example:

Not only does this method avoid the jsapi delay, but it also eliminates three unnecessary HTTP requests. I prefer and recommend this method.

Note that the script reference above uses the HTTPS protocol. For years, the examples on this page used a protocol-relative reference, beginning with just `//` instead of `http://` or `https://`, and this section of the post described how that was not a typo and was actually a valid URL.

I no longer recommend that approach.

You should always use the HTTPS jQuery CDN reference, even if you're including jQuery on a page that is itself being served via unencrypted HTTP. This greatly reduces the chances of someone tampering with the contents of the jQuery script between Google's CDN servers and your users' browsers. The overhead is minimal and all of the three benefits that I described earlier are still applicable when using the encrypted transport.

### Other implementations

**WordPress** - If you're using WordPress and want to take advantage of the Google CDN throughout your WordPress site without manually editing themes, plugins, etc, check out [Jason Penney](http://jasonpenney.net/)'s [Use Google Libraries](http://wordpress.org/extend/plugins/use-google-libraries/) plugin.

**HTML5 Boilerplate** - [H5BP](http://html5boilerplate.com/) is a web site skeleton that provides a great starting point for building a modern site. As part of that, it uses a reference to jQuery on the Google CDN (and an automatic fallback to a local copy for users that aren't able to load jQuery from the CDN for some reason).

### Conclusion

According to a recent study, Google will consume **16.5%** of all consumer Internet capacity in the United States during 2008. I think it's fair to say that they know how to efficiently serve up some content.

The opportunity to let the pros handle part of your site's JavaScript footprint free of charge is too good to pass up. As [often as even returning users experience the "empty cache"](http://yuiblog.com/blog/2007/01/04/performance-research-part-2/) load time of your site, it's important to take advantage of an easy optimization like this one.

What do you think? Are you using the Google AJAX Libraries CDN on your sites? Can you think of a scenario where the google.load() method would perform better than simple <script> declaration?
