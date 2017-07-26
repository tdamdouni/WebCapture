# Faster Page Load Using Lightweight CSS and SVG Animation (Without JavaScript)

_Captured: 2017-06-16 at 02:11 from [dzone.com](https://dzone.com/articles/faster-page-load-using-lightweight-css-and-svg-ani?edition=305097&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-15)_

[Start coding today](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt) to experience the powerful engine that drives data application's development, brought to you in partnership with [Qlik](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt).

Including animations on a web page is an exciting process. However exciting, it can be also an expensive process for your users. Common web animation tools, while effective, can create a lot of frontend bloat with large JavaScript animation libraries and multiple file requests for source images.

The end result (while pretty) can leave your user spending precious time waiting for the page to load.

If you need to create an attractive new animation for your homepage, for example, you will need to keep the page [load time well under two seconds.](https://raygun.com/blog/speed-up-your-website/?utm_source=dzone&utm_medium=article&utm_content=lightweight_svg) But you also want your page to look incredible and stand out from your competitors.

So, how can we create a lightweight solution that won't affect your website performance and user's experience? The solution is to build a high performing CSS and SVG animation without the JavaScript.

## **Creating a High Performing CSS and SVG Animation **

### Raw CSS Animation on Inline SVG

**Pros:**

  * The image is inline HTML, which means zero file requests.
  * All animation uses CSS, no JavaScript animation libraries.
  * Super small code footprint.

**Cons:**

  * Plan your CSS and SVG animation in detail. You cannot just export the image and expect usable SVG code. Also plan ahead and know which shapes need to be grouped. 
  * It's very hands on. If you manually add classes to SVG paths, and you decide to change your source image, you must reapply the classes.
  * Internet Explorer/Edge do not like animating SVGs. Fallbacks with static images work fine.

So, while a little hands on for some, I think it's awesome that we can create a fully animated piece of art with a pretty much non-existent footprint using **only** CSS animations.

**Next: I'll jump into my process for creating something like what I've created here: **Pen [Pow! CSS only SVG animation](https://codepen.io/kyleHenwood/pen/pPXNXE/) by Kyle Henwood ([@kyleHenwood](https://codepen.io/kyleHenwood)) on [CodePen](https://codepen.io/).

(Below is a screenshot from the animation)

![Image title](https://dzone.com/storage/temp/5570782-codepen.png)

Most of the complexity when creating an animation from SVG elements is exporting the artwork in a way that allows you to create the animation you want. For the above image, I drew inspiration [from a clip](https://dribbble.com/shots/1702884-POW) Fraser Davidson from Cub Studio made for [Raygun.com](https://raygun.com/?utm_source=dzone&utm_medium=article&utm_content=lightweight_svg) a few years ago.

### Creating the Artwork for Animation

Easily the hardest part of creating one of these animations is the creation of your file. You have to make it easy to animate post export.

You'll need to know what you can animate to get the desired result and the grouping of layers.

Knowing what the desired outcome is for the animation at this step is very important. Better planning allows you to group layers in such a way that can reduce complexity, and therefore reduce the amount of impact it has on your website performance.

Let me break down how I'm tackling this animation:

  * All the artwork moves as one, both into and out of the canvas, and scale. With this knowledge, I create a new group in Adobe Illustrator that contains all the artwork. The reason for doing this is so that when I export the file as an SVG, I can target that group item and add a class to it that performs the animation I want.
  * The Raygun rotates and moves independently of the beam and the sparks that come from the gun when firing, so while contained in the artwork group, I create another group that contains all the pieces of the Raygun.
  * The shine/sheen moves across the body of the Raygun, above the shadows but beneath the surface detail. I order the layers as such and create a mask of the Raygun. Within the mask, I add a polygon that I can move from left to right to create the sleek shine effect. This whole layer needs to move with the Raygun, so I also placed it inside the Raygun group.
  * There are a few ways I could have tackled the particles and beam. I opted to leverage the ability to animate a strokes border and border-offset using the CSS properties 'stroke-dasharray' and 'stroke-offset.' When I drew the completed paths I wanted two dashes to follow and worried about how they would look after the fact. Both these groups are contained in the artwork group.

## ![The artwork group for creating high performing css and svg animations ](https://raygun.com/blog/wp-content/uploads/2017/06/Screen-Shot-2017-06-01-at-2.37.22-PM.png)

> _Screenshot showing high performing svg animation_

### **Exporting SVG**

Once the artwork is sorted and grouped, the next step is exporting the SVG from Adobe Illustrator. When exporting, make sure you select inline CSS. While this may seem counter-intuitive as we want to manipulate classes, the last thing we want to do is fight generated classes for specificity.

## ![css and svg animation : the SVG option s in Adobe Inllustrator](https://raygun.com/blog/wp-content/uploads/2017/06/Screen-Shot-2017-06-01-at-2.38.16-PM.png)

> _Screenshot showing the Inline SVG options_

Once exported, you can open the SVG file in an editor, and copy the complete SVG code into an HTML page. Then, begin to add the classes and CSS animations.

### **Adding Classes and Creating the Animations**

With each of the groups we created in Adobe Illustrator, note the order of the SVG code. You'll notice it is in reverse order of what we would expect to find. The reason is that in HTML code, shapes are rendered top down, and thus they appear further down the page.

There are two methods you can use for writing complex CSS animations:

  1. **Staggered animations using short durations and animation offsets.**
  2. **Single duration variable + easing and percentage keyframes.**

There are pros and cons to each, but I prefer to use a single animation duration for the simple reason that I can slow down and control my entire timeline with a single variable. The cons to this approach are the limitations with animation easing.

For example, if you are only animating between keyframes 30% -> 40%, but have an easing function set to ease in, the easing is applied to the 0% -> 100% range, not just the 10% you have animated. I opt to apply the same easing function and timing to all the animations so that each keyframe occurs at the same point regardless of animation, making events easier to line up.

### Final Notes on Creating a High Performing CSS and SVG Animation

Remember, your page load time should never be over three seconds. Now, all that's left to do is tinker with your keyframes and classes, and create your animation!

[Create data driven applications](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij) in Qlik's free and easy to use coding environment, brought to you in partnership with [Qlik](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij).
