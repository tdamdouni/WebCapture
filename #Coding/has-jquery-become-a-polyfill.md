# Has jQuery Become a Polyfill?

_Captured: 2018-02-09 at 22:20 from [dzone.com](https://dzone.com/articles/has-jquery-become-a-polyfill?edition=360096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-22)_

[Get the senior executive's handbook](https://dzone.com/go?i=266423&u=https%3A%2F%2Fwww.appian.com%2Fresources%2Fresource%2Fguide-digital-transformation%2F%3Futm_source%3Ddzone%26utm_medium%3Dcontextual-ads%26utm_campaign%3Ddigital-transformation%26utm_content%3Dtransformers-almanac) of important trends, tips, and strategies to compete and win in the digital economy.

![](https://www.danylkoweb.com/content/images/pinkcadillac-polyfills.jpg)

Last week in the [newsletter](https://www.danylkoweb.com/subscribe), I mentioned a [new release of jQuery 3.3.0](https://blog.jquery.com/2018/01/19/jquery-3-3-0-a-fragrant-bouquet-of-deprecations-and-is-that-a-new-feature/).

In this release, a new feature was added: adding/removing/toggling classes from a DOM element using an array.

With this new release, it got me thinking.

Over the years, jQuery has become the Adobe Flash of the Internet. I would even go as far as to say it even surpasses Flash installs.

But as we've progressed through the years, I'm starting to rely less on jQuery and focusing more on the new features of JavaScript.

Or as the kids call it...ES6.

Even though [jQuery was introduced 11 years ago](https://en.wikipedia.org/wiki/JQuery), it's now starting to feel like a polyfill library.

## Is jQuery Really Necessary Anymore?

As a refresher, a polyfill library is a script meant to backfill current technology on older machines.

For example, if your browser doesn't support the new HTML5 input types (date, email, etc.), you download a polyfill library to "simulate" the input types.

Wikipedia.org defines a [polyfill](https://en.wikipedia.org/wiki/Polyfill_\(programming\)) with the following:

> In web development, a polyfill is code that implements a feature on web browsers that do not support the feature. Most often, it refers to a JavaScript library that implements an HTML5 web standard, either an established standard (supported by some browsers) on older browsers, or a proposed standard (not supported by any browsers) on existing browsers. Formally, "a polyfill is a shim for a browser API."

Based on this definition, does this make jQuery a polyfill?

When a browser evolves, the polyfill isn't required anymore because it's built into the browser. We don't need to "simulate" the feature anymore. It's already there.

I learned about polyfills when I was [building apps with Aurelia](https://www.danylkoweb.com/Blog/why-im-going-to-use-aurelia-CO) a while back.

## Did the jQuery Team Just Confirm This?

If you read the latest release notes on the blog, you'll notice this statement:

> Generally, jQuery is not looking to add anything new. We tend to focus more on what we can remove rather than what we can add. 

Interesting.

This is almost what a polyfill's lifecycle consists of: as browsers mature/evolve, some polyfill features aren't necessary in the library. They become, in a sense, deprecated.

As mentioned, polyfill libraries are built to provide older browsers with newer functionality. With the latest JavaScript/ES6, some of these features in jQuery aren't required anymore.

Hence, the removal of said features from the library.

## Should I Remove jQuery?

Now we come to the post where you ask yourself: should I remove jQuery?

As always, it depends.

I would ask these questions:

  * **How comfortable are you writing JavaScript and/or ES6?** \- If you are, then you may not need jQuery.
  * **Do you have legacy browsers?** \- Are you supporting older browsers where they don't have the latest and greatest available? If so, you may still need jQuery for those sites.
  * **How jQuery-heavy is your website?** \- If you have a ton of jQuery on your site, rewriting it may take a while and you (or the company) may not have the budget for a rewrite. Gradual refactoring is advised and considered more of an option.
  * **Would you want a faster website?** \- With [Google's requirement for faster websites](https://searchengineland.com/google-now-counts-site-speed-as-ranking-factor-39708), jQuery still packs on a 30K load. While it is a "small" library, it's still 30K you could do without.

With over 11 years of jQuery habits like typing `$(function() {})` every time I see a blank file.js, you can understand how hard it would be to adapt to something different.

But that's our business in IT and we need to adapt and roll with the changes.

## Replacing the Essentials

With the latest ES6 and most browsers (notice I said _most_) supporting it, what would be required to transition over to ES6 or pure JavaScript?

  * **DOM Navigation** \- Maneuvering through the DOM to find classes and Ids has always been there using `document.getElementsByClassName()` and `document.getElementById()`.
  * **Events (onChange, onLoad, onClick, etc.)** \- Attaching an event to a DOM element now is just as easy as performing the old `$(".button").click()`.
  * **Module Loading** \- I know a lot of devs were looking for this. With the latest in ES6, we now have an `import` keyword to include common JavaScript libraries in our modules.
  * **AJAX/Web API Calls** \- Ahh, AJAX. Instead of using the ole `$.getJson()` or `$.ajax()` calls, we now have the `fetch` function.

JavaScript frameworks like Angular are becoming more and more like jQuery to compensate for these essential features.

Looking at these functions in a general jQuery application, I would say this list covers 99% of my JavaScript development.

The other 1% is using the animation library to make monkeys dance across my screen.

## Conclusion

jQuery has been in my toolkit for those 11 years and, yes, it's definitely a hard habit to break.

Watching as JavaScript progressed over the years, I feel jQuery (along with Node.js) has truly influenced the direction and passion of JavaScript in the browser and the community making it the true "language of the web."

We may get to one point in the future where the jQuery library is not necessary anymore.

Because it's all in the browser.

_**What other features do you use in jQuery? Have you already stopped using jQuery? Why or Why not? **_

[Read this guide](https://dzone.com/go?i=266422&u=https%3A%2F%2Fwww.appian.com%2Fresources%2Fresource%2Fguide-robotic-process-automation-rpa%2F%3Futm_source%3Ddzone%26utm_medium%3Dcontextual-ads%26utm_campaign%3Drpa%26utm_content%3Dlookbook-guide-rpa) to learn everything you need to know about RPA, and how it can help you manage and automate your processes.
