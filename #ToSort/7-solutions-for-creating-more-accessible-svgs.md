# 7 solutions for creating more accessible SVGs

_Captured: 2017-03-19 at 21:48 from [simplyaccessible.com](http://simplyaccessible.com/article/7-solutions-svgs/)_

We've been working with SVGs a lot recently, which has led our developers down a rabbithole of discovery! Here are some things to consider when it comes to SVGs and accessibility.

When it comes to displaying images online nowadays, designers and developers have plenty of great formats from which to choose. There's the ubiquitous GIF (Graphics Interchange Format), the universal JPEG (Joint Photographic Experts Group), and the animated SVG (Scalable Vector Graphics), to name just a few. How do you know which one to use in your designs? Are any of these more amenable to creating an accessible site?

While we don't like to pick favourites, our clients are choosing SVGs more and more, which means we're working with SVGs more and more. As a result, we've learned the ins and outs of this image format, and how to make them accessible. And now, we want to share all that goodness with you!

Scalable Vector Graphics, otherwise known as SVGs, are a useful way to display images: they can scale smoothly, and they lack issues that exist with icon fonts, which can cause challenges for users with reading disabilities and parsing errors with some screen readers, depending on how they're implemented. SVGs also give designers and developers a lot of flexibility in creating complex graphics natively and dynamically.

Many of our clients use SVGs to display their images, which is great. However, the way in which SVGs are implemented can affect users with disabilities in a big way. To that end, we've put together a roundup of the most common challenges we're seeing with SVGs right now and how to address them, along with some examples for you to try out yourself.

## 1\. <img> tags and SVGs

When SVGs are implemented as <img> tags with an .svg as the source, we've encountered a few issues for VoiceOver and TalkBack users. These issues occur when those <img> tags don't also have an ARIA role="img" attribute.

  * VoiceOver/Safari on desktop will read an alt value but does not identify the image as such without the role, and it doesn't show up in the image list in the rotor.
  * VoiceOver/Safari on mobile skips the image entirely, even if there is an alt value, without the role.

If the image is part of a link, both have the same result:

  * VoiceOver/Safari on desktop reads the alt value as the link content, but does not identify the image, without the role.
  * VoiceOver/Safari on mobile reads the alt value as the link content, but does not identify it as part of an image, without the role.

TalkBack with Chrome and Firefox will identify the SVG as an image either way, unless it's part of a link. Then, the alt value is identified as the link text, but no image is mentioned. This might not be a problem if the fact that the link content is an image doesn't matter, but it might potentially cause problems. It's usually safest to just include the role!

## 2\. <title> tags and SVGs

We often see examples of making SVGs accessible by simply adding a <title> element within the inline <svg>. While this does help in some situations, like a lone SVG icon within a link, adding a <title> element doesn't make SVGs accessible in all browsing environments.

For example, when using Firefox and NVDA, a link containing an SVG would be recognized as a link, but the text within the <title> element would not be announced. NVDA announces the path within the href attribute only.

Adding an aria-labelledby attribute to the SVG can help expose the text within the <title> element to the browser's accessibility API. However, even with this in place, NVDA does not announce the <title> text as we might expect.

Our most recommended approach when it comes to browser support and consistency across screen readers is to add a visually-hidden element as a sibling element to the <svg>. With this implementation, we've found that all browser and screen reader combinations tested were able to announce the link with the expected text announcement.

We also recommend adding aria-hidden="true" to the <svg> element itself. This is to help prevent having any other text that may be embedded within the SVG be announced by screen readers. Then, the only text that should be announced would be the content within that visually-hidden element.

## 3\. IE focus bug with focusable elements

The <svg> elements inside focusable elements (like links or buttons) in Internet Explorer default to focusable="true" due to a bug. This causes both the parent element and the <svg> to receive focus. The focus indicator disappears when the image file receives focus, which is a problem for sighted keyboard-only users. Additionally, some screen readers read the content twice since parts of it get focus twice.

The way to fix this is to add focusable="false" to the <svg> to set the attribute to what it should be by default.

Here's an example with the [focus broken](http://simplyaccessible.com/wordpress/wp-content/uploads/2017/03/ie-svg-focus-broken.gif), and here's one with the [focus fixed](http://simplyaccessible.com/wordpress/wp-content/uploads/2017/03/ie-svg-focus-fixed.gif).

## 4\. Safari 10 focus bug with <use>

When accessed in Safari 10, <svg> that have <use> elements without whitespace between the parent <svg> and child <use> tags prevent focus from moving past the <svg>. This is an issue for all desktop Safari keyboard users. This is fixed in WebKit Nightly, so it may not affect more tech-savvy users, but users who keep Safari up to date in the normal channels will run into problems.

The solution, thankfully, is to just add whitespace around the <use> tags like so:
    
    
    <svg> <use>...</use> </svg>

Check out some more [discussion on VoiceOver and <use> over at allyjs.io](https://allyjs.io/tutorials/focusing-in-svg.html#the-use-element).

## 5\. Aria-label inconsistency

Another VoiceOver issue! An aria-label value reads consistently on <svg> elements that are children of a focusable control, like a link or button, but it's skipped by VoiceOver/Safari on iOS and OS X/macOS when the aria-label is used on a non-focusable element.

To prevent conflicts, we recommend using aria-hidden on the <svg> and using CSS to visually hide a text equivalent instead of relying on aria-label or similar techniques, just like we recommend for the <title> scenario discussed earlier.

## 6\. IE8 and below render <desc>

Internet Explorer 8 and below will visually render the content found in the <desc>…</desc> tags. A conditional can be used to hide this from old Internet Explorer versions.

## 7\. Colour contrast

While not a bug per se, we also see a lot of cases where designers and developers don't plan for colour contrast issues for SVGs. Since SVGs function just like transparent GIFs in how they are displayed, different page background colors and effects can cause unanticipated issues for low vision users.

For example, a black SVG icon that's perfectly visible with a white page background is going to be invisible in a Windows High Contrast theme that uses a black background. This is a common use case for users who use High Contrast settings due to light sensitivity or related issues. When you provide a solid background or contrasting border for SVGs, you can help avoid those kinds of problems.

Every image format has its pros and cons, and SVGs are no different. In spite of these potential snags, SVGs have a lot going for them. What accessibility issues have you noticed with SVGs? How did you solve the problems? How are SVGs as a format better for you than traditional images in your designs? We'd love to hear about it in the comments below.

![](http://simplyaccessible.com/wordpress/wp-content/themes/sa-wp-2014/images/articles-category-development-icon.svg)

![](http://simplyaccessible.com/wordpress/wp-content/themes/sa-wp-2014/images/articles-category-design-icon.svg)
