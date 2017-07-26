# Responsive Typography With Sass Maps

_Captured: 2015-06-17 at 08:20 from [www.smashingmagazine.com](http://www.smashingmagazine.com/2015/06/17/responsive-typography-with-sass-maps/?utm_medium=App.net+Broadcast&utm_source=PourOver)_

Managing consistent, typographic rhythm isn't easy, but when the type is responsive, things get even more difficult. Fortunately, Sass maps make responsive typography much more manageable.

Writing the code is one thing, but keeping track of font-size values for each breakpoint is another -- and the above is for paragraphs alone. Throw in `h1` to `h6`s, each with variable font sizes for each breakpoint, and it gets cumbersome, especially when the type doesn't scale linearly.

If you've tried to tackle responsive type, this may look familiar:
    
    
    p { font-size: 15px; }
    
    @media screen and (min-width: 480px){
      p { font-size: 16px; }
    }
    @media screen and (min-width: 640px){
      p { font-size: 17px; }
    }
    @media screen and (min-width: 1024px){
      p { font-size: 19px; }
    }
    

Sass variables are great for making values reusable throughout a project, but managing them for responsive font sizes easily becomes a mess.
    
    
    $p-font-size-mobile : 15px;
    $p-font-size-small  : 16px;
    $p-font-size-medium : 17px;
    $p-font-size-large  : 19px;
    
    $h1-font-size-mobile: 28px;
    $h1-font-size-small : 31px;
    $h1-font-size-medium: 33px;
    $h1-font-size-large : 36px;
    
    // I think you get the point…
    

This is where [Sass maps](https://jonsuh.com/blog/sass-maps/) and loops are powerful: They've helped me manage [z-index values](https://jonsuh.com/blog/organizing-z-index-with-sass/), [colors](https://jonsuh.com/blog/sass-maps/#loops-and-maps) and, as you'll see in a moment, font sizes.

### Organizing Font Sizes With Sass Maps

Let's start by creating a Sass map with key-value pairs -- breakpoints as keys and font sizes as corresponding values.
    
    
    $p-font-sizes: (
      null  : 15px,
      480px : 16px,
      640px : 17px,
      1024px: 19px
    );
    

With mobile-first in mind, we see that the key `null` represents the default font size (not in a media query), and breakpoints are in ascending order.

Next, the mixin, which iterates through a Sass map and generates the appropriate media queries.
    
    
    @mixin font-size($fs-map){
      @each $fs-breakpoint, $fs-font-size in $fs-map {
        @if $fs-breakpoint == null {
          font-size: $fs-font-size;
        }
        @else{
          @media screen and (min-width: $fs-breakpoint){
            font-size: $fs-font-size;
          }
        }
      }
    }
    

Note: It's worth mentioning that this mixin, along with the ones to follow, feature some basic programming logic. Sass, with the help of [SassScript](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#sassscript) (a set of extensions that comes baked in), makes basic programming constructs possible, like `if`/`else` statements, `each` loops and a ton more. I encourage you to take some time to read through the [documentation](http://sass-lang.com/documentation/file.SASS_REFERENCE.html). Sass' "power features" will introduce you to a new dimension of things you can do with Sass.

We'll then use the mixin for paragraphs:
    
    
    p {
      @include font-size($p-font-sizes);
    }
    

… which results in the following CSS:
    
    
    p { font-size: 15px; }
    
    @media screen and (min-width: 480px){
      p { font-size: 16px; }
    }
    @media screen and (min-width: 640px){
      p { font-size: 17px; }
    }
    @media screen and (min-width: 1024px){
      p { font-size: 19px; }
    }
    

Managing and keeping track of font sizes for elements becomes a whole lot easier! With every new element, create a map and call the mixin in the appropriate selector.
    
    
    $h1-font-sizes: (
      null  : 28px
      480px : 31px,
      640px : 33px,
      1024px: 36px
    );
    
    h1 {
      @include font-size($h1-font-sizes);
    }
    

Keep font sizes consistent for various elements:
    
    
    p, ul, ol {
      @include font-size($p-font-sizes);
    }
    

### Solving Breakpoint Fragmentation

But wait! What if we decide that we want the font size of `p`s to be 17 pixels and of `h1`s to be 33 pixels at a breakpoint of 700 pixels, instead of 640 pixels? With the solution above, that would require manually changing every instance of `640px`. By trying to solve one problem, we've inadvertently created another: breakpoint fragmentation.

If we can manage font sizes in Sass maps, surely we can do the same with breakpoints, right? Exactly!

Let's create a map for common breakpoints and assign each value an appropriate name. We'll also change the font-sizes map a bit by using the breakpoint names we assigned in `$breakpoints` to establish a relationship between the breakpoints and font-sizes maps.
    
    
    $breakpoints: (
      small : 480px,
      medium: 700px, // Previously 640px
      large : 1024px
    );
    
    $p-font-sizes: (
      null  : 15px,
      small : 16px,
      medium: 17px,
      large : 19px
    );
    
    $h1-font-sizes: (
      null  : 28px
      small : 31px,
      medium: 33px,
      large : 36px
    );
    

The last step is to tweak the mixin a bit so that when it iterates through the font-sizes map, it'll use the breakpoint name to get the appropriate value from `$breakpoints` before generating the media query.
    
    
    @mixin font-size($fs-map, $fs-breakpoints: $breakpoints){
      @each $fs-breakpoint, $fs-font-size in $fs-map {
        @if $fs-breakpoint == null {
          font-size: $fs-font-size;
        }
        @else{
          // If $fs-font-size is a key that exists in
          // $fs-breakpoints, use the value
          @if map-has-key($fs-breakpoints, $fs-breakpoint){
            $fs-breakpoint: map-get($fs-breakpoints, $fs-breakpoint);
          }
          @media screen and (min-width: $fs-breakpoint){
            font-size: $fs-font-size;
          }
        }
      }
    }
    

Note: The mixin's default breakpoints map is `$breakpoints`; if your breakpoints variable's name is different, be sure to change it in the second argument of line 1.

Voila! Now, what if we want an element to have a font size for a custom breakpoint that doesn't exist in `$breakpoints`? In the font-sizes map, simply drop in the breakpoint value instead of a name as the key, and the mixin will do the work for you:
    
    
    $p-font-sizes: (
      null  : 15px,
      small : 16px,
      medium: 17px,
      900px : 18px,
      large : 19px,
      1440px: 20px,
    );
    
    p {
      @include font-size($p-font-sizes);
    }
    

The magic happens in the mixin thanks to Sass' `[map-has-key` function](http://sass-lang.com/documentation/Sass/Script/Functions.html#map_has_key-instance_method). It checks to see whether the key name exists in `$breakpoints`: If it exists, it'll use the value of the key; if not, it'll assume the key is a custom value and use that instead when generating the media query.
    
    
    p { font-size: 15px; }
    
    @media screen and (min-width: 480px){
      p { font-size: 16px; }
    }
    @media screen and (min-width: 700px){
      p { font-size: 17px; }
    }
    @media screen and (min-width: 900px){
      p { font-size: 18px; }
    }
    @media screen and (min-width: 1024px){
      p { font-size: 19px; }
    }
    @media screen and (min-width: 1440px){
      p { font-size: 20px; }
    }
    

### Improving Vertical Rhythm With Line Height

Line height is also an important part of achieving consistent vertical rhythm. So, without going overboard, let's include line height in the solution.

Extend the font-sizes map by including both font size and line height in a list as the value of the desired key:
    
    
    $breakpoints: (
      small : 480px,
      medium: 700px,
      large : 1024px
    );
    
    $p-font-sizes: (
      null  : (15px, 1.3),
      small : 16px,
      medium: (17px, 1.4),
      900px : 18px,
      large : (19px, 1.45),
      1440px: 20px,
    );
    

Note: Although line-height values can be defined using any valid CSS unit (percentages, pixels, ems, etc.), "unitless" values are [recommended](https://css-tricks.com/almanac/properties/l/line-height/) and [preferred](https://developer.mozilla.org/en-US/docs/Web/CSS/line-height#Prefer_unitless_numbers_for_line-height_values) in order to avoid unexpected results due to inheritance.

We then need to modify the mixin to include line height when generating the CSS.
    
    
    @mixin font-size($fs-map, $fs-breakpoints: $breakpoints){
      @each $fs-breakpoint, $fs-font-size in $fs-map {
        @if $fs-breakpoint == null {
          @include make-font-size($fs-font-size);
        }
        @else{
          // If $fs-font-size is a key that exists in
          // $fs-breakpoints, use the value
          @if map-has-key($fs-breakpoints, $fs-breakpoint){
            $fs-breakpoint: map-get($fs-breakpoints, $fs-breakpoint);
          }
          @media screen and (min-width: $fs-breakpoint){
            @include make-font-size($fs-font-size);
          }
        }
      }
    }
    
    // Utility function for mixin font-size
    @mixin make-font-size($fs-font-size){
      // If $fs-font-size is a list, include
      // both font-size and line-height
      @if type-of($fs-font-size) == "list" {
        font-size: nth($fs-font-size, 1);
        @if (length($fs-font-size) > 1){
          line-height: nth($fs-font-size, 2);
        }
      }
      @else{
        font-size: $fs-font-size;
      }
    }
    

The mixin checks to see whether the value of the key in the font-sizes map is a list as opposed to a font-size value. If it's a list, then it gets the correct value from the list by index value, with the help of the `[nth` function](http://sass-lang.com/documentation/Sass/Script/Functions.html#nth-instance_method). It assumes that the first value is the font size and the second is the line height. Let's see it in action:
    
    
    p {
      @include font-size($p-font-sizes);
    }
    

And here's the resulting CSS:
    
    
    p { font-size: 15px; line-height: 1.3; }
    
    @media screen and (min-width: 480px){
      p { font-size: 16px; }
    }
    @media screen and (min-width: 700px){
      p { font-size: 17px; line-height: 1.4; }
    }
    @media screen and (min-width: 900px){
      p { font-size: 18px; }
    }
    @media screen and (min-width: 1024px){
      p { font-size: 19px; line-height: 1.45; }
    }
    @media screen and (min-width: 1440px){
      p { font-size: 20px; }
    }
    

This final solution is easily extensible to accommodate a host of other attributes, such as font weights, margins, etc. The key is to modify the `make-font-size` utility mixin and use the `nth` function to get the appropriate value from the list.

### Conclusion

There are various ways to approach responsive typography and consistent vertical rhythm, and they are not limited to my suggestion. However, I find that this works for me more times than not.

Using this mixin will likely generate duplicate media queries in your compiled CSS. There's been a lot of discussion about duplicate media queries versus grouped media queries, [using @extend instead of mixins](https://tech.bellycard.com/blog/sass-mixins-vs-extends-the-data/), and performance and file size; however, tests have concluded that "[the difference, while ugly, is minimal at worst, essentially non-existent at best](http://sasscast.tumblr.com/post/38673939456/sass-and-media-queries)."

I also realize that my solution is not robust (it's not designed to handle media-query ranges, `max-width` or viewport orientation). Such features can be implemented in the mixin (my personal version also converts pixel values to ems), but for complex media queries, I prefer to write by hand. Don't forget that you can use the `[map-get` function](http://sass-lang.com/documentation/Sass/Script/Functions.html#map_get-instance_method) to retrieve values from existing maps.

#### Alternatives

[Viewport units](https://css-tricks.com/viewport-sized-typography/) (`vh`, `vw`, `vmin` and `vmax`) can also be used to create responsive typography:

  


> _An example of viewport units in action. One viewport unit = 1% of the viewport's width or height. (For a 1000-pixel-wide viewport, `1vw` = `100px`; for a 500-pixel-high viewport, `1vh` = `5px`.)_

For example, viewport-width units can be used to build [fluid hero text](http://demosthenes.info/blog/739/Creating-Responsive-Hero-Text-With-vw-Units). However, because the text will be scaled to the width or height of the viewport (as opposed to the size of the content area of the page) and because CSS currently lacks `min` and `max` values for the `font-size` property, viewport units aren't suitable for body text: No matter what value you choose, body text sized in viewport units will always end up being too large or too small at extreme browser sizes, necessitating intervention by media query.

[FitText.js](http://fittextjs.com/) does a similar job, with a focus on sizing text so that it always rests on a single line or measure. SVG techniques can also be used to achieve a similar effect.

Finally, [Erik van Blokland](https://twitter.com/letterror) has been working on some very [exciting possibilities for responsive typography](http://letterror.com/dev/mathshapes/page_20_Excellence.html), such as letterforms that actually alter with viewport size to preserve space, rather than simply get smaller.

#### Further Resources

[Modular Scale](http://www.modularscale.com/) is a great tool to achieve responsive typography, and Sara Soueidan has a great article on [responsive typography techniques](http://tympanus.net/codrops/2013/11/19/techniques-for-responsive-typography/).

_(ds, ml, al)_
