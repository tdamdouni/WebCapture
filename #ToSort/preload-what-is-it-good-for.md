# Preload: What Is It Good For?

_Captured: 2017-04-25 at 14:25 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2016/02/preload-what-is-it-good-for/)_

  * [44 Comments](https://www.smashingmagazine.com/2016/02/preload-what-is-it-good-for/)

Meet the new [Sketch Handbook](https://shop.smashingmagazine.com/products/sketch-handbook?utm_source=magazine&utm_campaign=sketch-handbook&utm_medium=html-ad-content-1), our brand **new Smashing book** that will help you master all the tricky, advanced facets of Sketch. Filled with **practical examples and tutorials in 12 chapters**, the book will help you become more proficient in your work. [Get the book now ->](https://shop.smashingmagazine.com/products/sketch-handbook?utm_source=magazine&utm_campaign=sketch-handbook&utm_medium=html-ad-content-1)

**Preload** ([spec](https://w3c.github.io/preload/)) is a new web standard aimed at improving performance and providing more granular loading control to web developers. It gives developers the ability to **define custom loading** logic without suffering the performance penalty that script-based resource loaders incur.

A few weeks ago, I [shipped](https://groups.google.com/a/chromium.org/d/msg/blink-dev/_nu6HlbNQfo/XzaLNb1bBgAJ) preload support in Chrome Canary, and barring unexpected bugs it will hit Chrome stable in mid-April. But what is that preload thing? What does it do? And how can it help you?

Well, `<link rel="preload">` is a declarative fetch directive.

In human terms, it's a way to tell a browser to start fetching a certain resource, because we as authors (or as server administrators, or as smart-server developers) know that the browser is going to need that particular resource pretty soon.

Kinda, but not really. `<link rel="prefetch">` has been supported on the web for a long while, and has [decent browser support](http://caniuse.com/#feat=link-rel-prefetch). On top of that we've also supported `<[link rel="subresource">`](https://web.archive.org/web/20150907034803/https://www.chromium.org/spdy/link-headers-and-server-hint/link-rel-subresource) in Chrome for some time. So what's new about preload? How is it different from these other directives? They all tell the browser to fetch things, right?

Well, they do, but there are significant differences between them. Differences that warrant a shiny new directive that tackles many use cases that the old ones never did.

`<link rel="prefetch">` is a directive that tells a browser to **fetch a resource that will probably be needed** for the next navigation. That mostly means that the resource will be fetched with extremely low priority (since everything the browser _knows_ is needed in the current page is more important than a resource that we _guess_ might be needed in the next one). That means that prefetch's main use case is speeding up the next navigation rather than the current one.

`<link rel="subresource">` was originally planned to tackle the current navigation, but it failed to do that in some spectacular ways. Since the web developer had no way to define what the priority of the resource should be, the browser (just Chrome and Chromium-based browsers, really) downloaded it with fairly low priority, which meant that in most cases, the resource request came out at about the same time that it would if subresource wasn't there at all.

Preload is destined for current navigation, just like subresource, but it includes one small yet significant difference. It has an `as` attribute, which enables the browser to do a number of things that subresource and prefetch did not enable:

  * The **browser can set the right resource priority**, so that it would be loaded accordingly, and will not delay more important resources, nor tag along behind less important resources.
  * The browser can make sure that the request is subject to the right [Content-Security-Policy](http://www.html5rocks.com/en/tutorials/security/content-security-policy/) directives, and doesn't go out to the server if it shouldn't.
  * The browser can send the appropriate `Accept` headers based on the resource type. (e.g. advertise support for "image/webp" when fetching images)
  * The browser knows the resource type so it can later determine if the resource could be reused for future requests that need the same resource.

Preload is also different since it has a functional `onload` event (which, at least in Chrome, wasn't working for the other two `rel` values).

On top of that, preload **does not block the window's `onload` event**, unless the resource is also requested by a resource that blocks that event.

Combining all these characteristics together enables a bunch of new capabilities that were not possible until now.

Let's go over them, shall we?

The basic way you could use preload is to **load late-discovered resources early**. While most markup-based resources are discovered fairly early by the browser's [preloader](http://calendar.perfplanet.com/2013/big-bad-preloader/), not all resources are markup-based. Some of the resources are hidden in CSS and in JavaScript, and the browser cannot know that it is going to need them until it is already fairly late. So in many cases, these resources end up delaying the first render, the rendering of text, or loading of critical parts of the page.

Now you have the means to tell the browser, "Hey, browser! Here's a resource you're going to need later on, so start loading it now."

Doing so would look something like:
    
    
    <link rel="preload" href="late_discovered_thing.js" as="script">

The `as` attribute tells the browser what it will be downloading. Possible `as` values include:

  * `"script"`,
  * `"style"`,
  * `"image"`,
  * `"media"`,
  * and `"document"`.

(See the [fetch spec](https://fetch.spec.whatwg.org/#concept-request-destination) for the full list.)

Omitting the `as` attribute, or having an invalid value is equivalent to an XHR request, where the browser doesn't know what it is fetching, and fetches it with a fairly low priority.

One popular incarnation of the "late-discovered critical resources" pattern is web fonts. On the one hand, in most cases they are critical for rendering text on the page (unless you're using the shiny [font-display CSS values](https://tabatkins.github.io/specs/css-font-display/)). On the other hand, they are buried deep in CSS, and even if the browser's preloader parsed CSS, it cannot be sure they'd be needed until it also knows that the selectors that require them actually apply to some of the DOM's nodes. While in theory, browsers could figure that out, none of them do, and if they would it could result in spurious downloads if the font rules get overridden further down the line, once more CSS rules come in.

In short, it's complicated.

But, you could get away from all that complexity by **including preload directives for fonts** you know are going to be needed. Something like:
    
    
    <link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin>

One point worth going over: You [have to add a `crossorigin` attribute](https://github.com/w3c/preload/issues/32) when fetching fonts, as they are [fetched using anonymous mode CORS](https://drafts.csswg.org/css-fonts/#font-fetching-requirements). Yes, even if your fonts are on the same origin as the page. Sorry.

Also, the `type` attribute is there to make sure that this resource will only get preloaded on browsers that support that file type. Right now, only Chrome supports preload, and it does support WOFF2 as well, but more browsers may support preload in the future, and we cannot assume they'd also support WOFF2. The same is true for any resource type you're preloading and which browser support isn't ubiquitous.

Another interesting scenario that suddenly becomes possible is one where you want to **download a resource because you know you'd need it**, but you don't yet want to execute it. For example, think of a scenario where you want to execute a script at a particular point in the page's life, without having control over the script (so without the ability to add a `runNow()` function to it).

Today, you are very limited in the ways you can do that. If you only inject the script at the point you want it to run, the browser will have to then download the script before it can be executed, which can take a while. You could download the script using XHR beforehand, but the browser will refuse to reuse it, since the resource wasn't downloaded with the same type as the one that is now trying to use the resource.

So what can you do?

Before preload, not much. (In some cases you can `eval()` the contents of the script, but that's not always feasible nor without side effects.) But with preload you can!
    
    
    var preload = document.createElement("link");
    link.href = "myscript.js";
    link.rel = "preload";
    link.as = "script";
    document.head.appendChild(link);
    

You can run that earlier on in the page load process, way before the point you want the script to execute (but once you're fairly confident that the script loading will not interfere with other, more critical resources that need loading). Then when you want it to run, you simply inject a `script` tag and you're good.
    
    
    var script = document.createElement("script");
    script.src = "myscript.js";
    document.body.appendChild(script);
    

Another cool hack is to use the `onload` handler in order to create some sort of a markup-based async loader. [Scott Jehl](https://twitter.com/scottjehl) was the first to [experiment](https://github.com/filamentgroup/loadCSS/issues/59) with that, as part of his loadCSS library. In short, you can do something like:
    
    
    <link rel="preload" as="style" href="async_style.css" onload="this.rel='stylesheet'">

and get async loaded styles in markup! Scott also has a nice [demo](http://filamentgroup.github.io/loadCSS/test/preload.html) page for that feature.

The same can also work for async scripts.

We already have `<script async>` you say? Well, `<script async>` is great, but it blocks the window's onload event. In some cases, that's exactly what you want it to do, but in other cases less so.

Let's say you want to download an analytics script. You want it to download fairly quickly (to avoid losing visitors that the analytics script didn't catch), but you don't want it to delay any metrics that impact the user experience, and specifically, you don't want it to delay onload. (You can [claim that onload](http://www.stevesouders.com/blog/2013/05/13/moving-beyond-window-onload/) is not the only metric that impacts users, and you would be right, but it's still nice to stop the spinning loading icon a bit sooner).

With preload, achieving that is easy:
    
    
    <link rel="preload" as="script" href="async_script.js"
    onload="var script = document.createElement('script');
            script.src = this.href;
            document.body.appendChild(script);">
    

(It's probably not a great idea to include long JS functions as `onload` attributes, so you may want to define that part as an inline function.)

Since **preload is a link**, according to the spec it has a `media` attribute. (It's currently not supported in Chrome, but will be soon.) That attribute can enable conditional loading of resources.

What is that good for? Let's say your site's initial viewport has a large interactive map for the desktop/wide-viewport version of the site, but only displays a static map for the mobile/narrow-viewport version.

If you're being smart about it, you want to **load only one of those resources rather than both**. And the only way to do that would be by loading them dynamically, using JS. But by doing that, you're making those resources invisible to the preloader, and they may be loaded later than necessary, which can impact your users' visual experience, and **negatively impact** your [SpeedIndex](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/metrics/speed-index) score.

What can we do to make sure the browser is aware of those resources as early as possible?

You guessed it! Preload.

We can **use preload to load them ahead of time**, and we can use its `media` attribute so that _only_ the required script will be preloaded:
    
    
    <link rel="preload" as="image" href="map.png" media="(max-width: 600px)">
    
    <link rel="preload" as="script" href="map.js" media="(min-width: 601px)">

One more feature that comes along free with link tags is that they can be [represented as HTTP headers](https://tools.ietf.org/html/rfc5988). That means that for most markup examples I showed above, you can have an HTTP response header that does exactly the same thing. (The only exception is the `onload`-related example. You cannot define an onload handler as part of an HTTP header.)

Examples for such HTTP response headers may look like:
    
    
    Link: <thing_to_load.js>;rel="preload";as="script"
    
    Link: <thing_to_load.woff2>;rel="preload";as="font";crossorigin

HTTP headers can come in handy when the person doing the optimization is not the same person who's responsible for editing the markup. The prominent example is an **external optimization engine** that scans the content and optimizes it (full disclosure: [I work on one](https://www.akamai.com/us/en/resources/front-end-optimization-feo.jsp)).

Other examples can include a separate performance team that wants to add such optimizations, or an optimization build process where avoiding HTML fiddling significantly reduces complexity.

One last point: In some of our examples above, we're relying on the fact that preload is supported for basic functionality such as script or style loading. What happens in browsers where this is not true?

Everything breaks!

We don't want that. So as part of the preload effort, we also changed the DOM spec so that feature detection of supported `rel` keywords would be possible.

An **example feature detection** function could look something like:

var DOMTokenListSupports = function(tokenList, token) {

if (!tokenList || !tokenList.supports) {

return;

}

try {

return tokenList.supports(token);

} catch (e) {

if (e instanceof TypeError) {

console.log("The DOMTokenList doesn't have a supported tokens list");

} else {

console.error("That shouldn't have happened");

}

}

};

var linkSupportsPreload = DOMTokenListSupports(document.createElement("link").relList, "preload");

if (!linkSupportsPreload) {

// Dynamically load the things that relied on preload.

}

That enables you to **provide fallback loading mechanisms** in cases where the lack of preload support would break your site. Handy!

Not really. While there is some overlap between the features, for the most part, they complement each other.

HTTP/2 Push has the advantage of being able to **push resources** that the browser hasn't sent the request for yet. That means that Push can send down resources before the HTML even started to be sent to the browser. It can also be used to send resources down on an open HTTP/2 connection without requiring a response on which HTTP Link headers can be attached.

On the other hand, **preload can be used to resolve use cases that HTTP/2 cannot**. As we've seen, with preload the application is aware of the resource loading taking place, and can be notified once the resource was fully loaded. That's not something HTTP/2 Push was designed to do. Furthermore, HTTP/2 Push cannot be used for third-party resources, while preload can be used for them just as efficiently as it would be used on first-party resources.

Also, HTTP/2 Push **cannot take the browser's cache and non-global cookie state into account**. While the cache state might be resolved with the new [cache digest specification](https://tools.ietf.org/html/draft-kazuho-h2-cache-digest-00), for non-global cookies there's nothing that can be done, so Push cannot be used for resources that rely on such cookies. For such resources, preload is your friend.

Another point in preload's favor is that it can perform content negotiation, while HTTP/2 Push cannot. That means that if you want to use [Client-Hints](https://www.smashingmagazine.com/2016/01/leaner-responsive-images-client-hints/) to figure out the right image to send to the browser, or `Accept:` headers in order to figure out the best format, HTTP/2 Push cannot help you.

I hope you're now convinced that preload opens up a new set of loading capabilities that weren't feasible before, and you're excited about using it.

What I ask of you is to go pick up Chrome Canary, play around with preload, break it into pieces and come whining back to [me](https://twitter.com/yoavweiss). It's a new feature, and like any new feature, it **may contain bugs**. Please help me find them and fix them as early as possible.

_(og)_
