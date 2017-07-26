# A Tiny Yet Powerful Alternative to jQuery

_Captured: 2017-03-31 at 20:13 from [dzone.com](https://dzone.com/articles/a-tiny-yet-powerful-alternative-to-jquery?edition=286955&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-31)_

jQuery has been by far the most popular JavaScript library for the last 5 years. It's powerful, easy to use, and widespread. However, the latest jQuery release is 250kb. Since [website speed](http://www.catswhocode.com/blog/make-wordpress-faster) is extremely important, what about giving Umbrella JS, which is only 4kb, a try? Let's have a look at this new and promising JavaScript library.

## Why Umbrella JS?

jQuery is an amazing piece of code! Since its first release in 2006, jQuery has played a key role in shaping the web as we know it nowadays. Still, every now and then a new JavaScript library is released. One that caught my attention lately is [Umbrella JS](http://umbrellajs.com), a library heavily influenced by jQuery, but way more compact (3kb!) and limited to DOM manipulation, events, and Ajax.

So what are the top advantages in using Umbrella JS?

  * **It's super lightweight:** Umbrella JS is only 3kb minified, which ensures super fast loading speeds, even on mobile devices. Website loading speed is now an extremely important factor in search engine rankings and ease of use for mobile users, so this is indeed a great thing.
  * **It's easy to use:** Umbrella JS is heavily influenced by jQuery. If you know jQuery's syntax, adapting to Umbrella JS will be very easy.
  * **It's complete:** Despite being small in size, Umbrella JS contains everything you need for DOM manipulation, events, and Ajax.
  * **It's free:** Released under the terms of the [MIT license](https://github.com/franciscop/umbrella/blob/master/LICENSE), Umbrella JS can be used freely in all your projects.

## Installation and Usage

Installing Umbrella JS is easy. You can use [JSdelivr](http://www.jsdelivr.com/projects/umbrella) CDN, or [download the .js file](https://raw.githubusercontent.com/franciscop/umbrella/master/umbrella.min.js) and add it to your HTML document:

If you want to test and experiment with Umbrella JS, you can do so in [JS Fiddle](https://jsfiddle.net/franciscop/mwpcqddj/).

## A Few Snippets

Now let's see what we can do with Umbrella JS. If you're familiar with jQuery, you will get the syntax very easily. If you want more snippets and examples, check out the [documentation](https://umbrellajs.com/documentation).

### Simple event

Handling a simple event: When the user clicks on a button, an alert is displayed.

### Automatic target="_blank" on Links

A good example of the `each()` function, which is used to loop through all of the nodes and to execute a callback for each.

### Ajax

Performing Ajax requests is even easier than with jQuery.

### Scroll to an Element

As seen on many websites, clicking on a link with the class `team` will scroll to the first `<section>` element with the class `team`:

### Auto-Save a Form Every 10 Seconds

Using the `ajax()` and `trigger()` functions, it only takes a few lines to create an auto-save function for any kind of form.

Do you have any [Umbrella JS](https://umbrellajs.com) experiences to share? Leave a comment below.
