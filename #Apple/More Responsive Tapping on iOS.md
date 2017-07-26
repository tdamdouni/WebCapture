# More Responsive Tapping on iOS

_Captured: 2015-12-16 at 00:33 from [webkit.org](https://webkit.org/blog/5610/more-responsive-tapping-on-ios/)_

WebKit on iOS has a 350 millisecond delay before single taps activate links or buttons. WebKit has this delay because we also allow users to double tap to zoom, which is a great way to zoom in on content that is well-sized for large desktop displays, but appears too small on mobile devices. However, when a user has tapped once, WebKit cannot tell if the user intends on tapping again to trigger a double tap gesture. Since double tapping is defined as two taps within a short time interval (350ms), WebKit must wait for this time interval to pass before we're sure that the user intended to tap only once.

We know that responsive tapping is really important to web developers -- so much so that many are willing to employ JavaScript frameworks to avoid the delay using touch handlers. Instead of waiting for WebKit to fire a click after a delay, these libraries prevent the default behavior of the touchend event and call `click()` immediately so that the element is clicked the moment the user stops touching the element. While this may make a link feel fast, it can also reduce responsiveness in other ways, including page load time and scrolling. To address this, we baked fast tapping optimizations into WebKit so well-scaled mobile web pages will be able to achieve responsive tapping out of the box without the drawbacks of third-party frameworks.

On web pages optimized for mobile viewports, elements such as links and form controls are scaled to fit well on smaller screens. As such, double tapping on these elements increases the page scale by only a small amount. Since double tapping provides little value on these web pages, we've implemented a mechanism for removing the delay for single taps by disabling double tap gestures.

The following examples show the amount of time required to tap a button 10 times in a page with `<meta name="viewport" content="initial-scale=1.0, width=device-width">`, with and without the fast-tap optimization. The left video shows the old behavior, while the right video shows the new behavior.

  


### When Fast-Tap Optimizations Apply

When content is scaled to fit well on a mobile device, WebKit disables double tapping in favor of fast single tapping. Using the viewport meta tag, there are a few ways WebKit determines whether content is well-proportioned.

Since users cannot zoom in unscalable viewports (using meta tags with `user-scalable=no` or a `minimum-scale` equal to the `maximum-scale`) WebKit assumes that if a page has an unscalable viewport, all content is already well-proportioned relative to the screen. On these pages, WebKit removes the ability to double-tap on elements altogether and dispatches all taps immediately as clicks. We implemented this behavior in [Bug #149968](https://bugs.webkit.org/show_bug.cgi?id=149968).

However, we believe web pages should be scalable when possible. For this reason, viewports that have `width=device-width` will have fast single tapping when the user is at initial scale. We added this optimization in [Bug #150604](https://bugs.webkit.org/show_bug.cgi?id=150604).

### Styling Fast-Tap Behavior

Even if a web page cannot use one of the viewport configurations above, it can still opt in to the fast-tap optimization. We've implemented the `manipulation` value of the new `touch-action` CSS property in [Bug #149854](https://bugs.webkit.org/show_bug.cgi?id=149854). By default, elements have `touch-action: auto`, which indicates that WebKit may enable any touch behaviors such as panning, pinching and double-tapping. Putting `touch-action: manipulation;` on a clickable element makes WebKit consider touches that begin on the element only for the purposes of panning and pinching to zoom. This means WebKit does not consider double-tap gestures on the element, so single taps are dispatched immediately. Single taps on an element become fast when any of the element's ancestors have the `touch-action: manipulation`. Note that putting `touch-action: manipulation` on any node opts all children of the node into the fast-tap optimization.

Additionally, single taps on an element with `touch-action: manipulation` are fast for all zoom scales, whereas our optimizations on device-width viewports only trigger when the viewport is at initial scale.

If you have questions, comments or other feedback regarding fast-tapping in mobile Safari, feel free to reach out to Jon Davis [@jonathandavis](http://twitter.com/jonathandavis) or WebKit [@webkit](http://twitter.com/webkit) on Twitter, or email me directly at [wenson_hsieh@apple.com](https://webkit.org/blog/5610/more-responsive-tapping-on-ios/wenson_hsieh@apple.com).
