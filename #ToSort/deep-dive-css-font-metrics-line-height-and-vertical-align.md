# Deep dive CSS: font metrics, line-height and vertical-align

_Captured: 2017-02-17 at 18:08 from [iamvdo.me](http://iamvdo.me/en/blog/css-font-metrics-line-height-and-vertical-align)_

`Line-height` and `vertical-align` are simple CSS properties. So simple that most of us are convinced to fully understand how they work and how to use them. But it's not. They really are complex, maybe the hardest ones, as **they have a major role in the creation of one of the less-known feature of CSS: inline formatting context**.

For example, `line-height` can be set as a length or a unitless value [1](http://iamvdo.me/en/blog/css-font-metrics-line-height-and-vertical-align), but the default is `normal`. OK, but what normal is? We often read that it is (or should be) 1, or maybe 1.2, even the [CSS spec is unclear on that point](https://www.w3.org/TR/CSS2/visudet.html#propdef-line-height). We know that unitless `line-height` is `font-size` relative, but the problem is that `font-size: 100px` behaves differently across font-families, so is `line-height` always the same or different? Is it really between 1 and 1.2? And `vertical-align`, what are its implications regarding `line-height`?

Deep dive into a not-so-simple CSS mechanism…

Look at this simple HTML code, a `<p>` tag containing 3 `<span>`, each with a different `font-family`:
    
    
    <p>
        <span class="a">Ba</span>
        <span class="b">Ba</span>
        <span class="c">Ba</span>
    </p>
    
    
    p  { font-size: 100px }
    .a { font-family: Helvetica }
    .b { font-family: Gruppo    }
    .c { font-family: Catamaran }

Using the same `font-size` with different font-families produce elements with various heights:

![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/font-size.png)

> _Different font-families, same font-size, give various heights_

Even if we're aware of that behavior, why `font-size: 100px` does not create elements with 100px height? I've measured and found these values: Helvetica: 115px, Gruppo: 97px and Catamaran: 164px

![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/font-size-line-height.png)

> _Elements with font-size: 100px have height that varies from 97px to 164px_

Although it seems a bit weird at first, it's totally expected. **The reason lays down inside the font itself**. Here is how it works:

  * a font defines its [em-square](http://designwithfontforge.com/en-US/The_EM_Square.html) (or UPM, units per em), a kind of container where each character will be drawn. This square uses relative units and is generally set at 1000 units. But it can also be 1024, 2048 or anything else.
  * based on its relative units, metrics of the fonts are set (ascender, descender, capital height, x-height, etc.). Note that some values can bleed outside of the em-square.
  * in the browser, relative units are scaled to fit the desired font-size.

Let's take the Catamaran font and open it in [FontForge](https://fontforge.github.io/en-US/) to get metrics:

  * the em-square is 1000
  * the ascender is 1100 and the descender is 540. After running some tests, it seems that browsers use the HHead Ascent/Descent values (on a Mac) and Win Ascent/Descent values on Windows (these values may differ!). We also note that Capital height is 640 and X height is 485.
![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/font-forge-metrics.png)

> _Font metrics values using FontForge_

That means the Catamaran font uses 1100 + 540 units in a 1000 units em-square, which gives a height of 164px when setting `font-size: 100px`. **This computed height defines the _content-area_ of an element** and I will refer to this terminology for the rest of the article. You can think of the _content-area_ as the area where the `background` property applies [2](http://iamvdo.me/en/blog/css-font-metrics-line-height-and-vertical-align).

We can also predict that capital letters are 68px high (680 units) and lower case letters (x-height) are 49px high (485 units). As a result, `1ex` = 49px and `1em` = 100px, not 164px (thankfully, `em` is based on `font-size`, not computed height)

![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/upm-px-equivalent.png)

> _Catamaran font: UPM --Units Per Em-- and pixels equivalent using font-size: 100px_

Before going deeper, a short note on what this it involves. When a `<p>` element is rendered on screen, it can be composed of many lines, according to its width. Each line is made up of one or many inline elements (HTML tags or anonymous inline elements for text content) and is called a _line-box_. **The height of a _line-box_ is based on its children's height**. The browser therefore computes the height for each inline elements, and thus the height of the _line-box_ (from its child's highest point to its child's lowest point). As a result, a _line-box_ is always tall enough to contain all its children (by default).

> Each HTML element is actually a stack of _line-boxes_. If you know the height of each _line-box_, you know the height of an element.

If we update the previous HTML code like this:
    
    
    <p>
        Good design will be better.
        <span class="a">Ba</span>
        <span class="b">Ba</span>
        <span class="c">Ba</span>
        We get to make a consequence.
    </p>

It will generate 3 _line-boxes_:

![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/line-boxes.png)

> _A <p> (black border) is made of line-boxes (white borders) that contain inline elements (solid borders) and anonymous inline elements (dashed borders)_

We clearly see that the second _line-box_ is taller than the others, due to the computed _content-area_ of its children, and more specifically, the one using the Catamaran font.

**The difficult part in the _line-box_ creation is that we can't really see, nor control it with CSS**. Even applying a background to `::first-line` does not give us any visual clue on the first _line-box_'s height.

Until now, I introduced two notions: _content-area_ and _line-box_. If you've read it well, I told that a _line-box_'s height is computed according to its children's height, I didn't say its children _content-area_'s height. And that makes a big difference.

Even though it may sound strange, **an inline element has two different height: the _content-area_ height and the _virtual-area_ height** (I invented the term _virtual-area_ as the height is invisible to us, but you won't find any occurrence in the spec).

  * the _content-area_ height is defined by the font metrics (as seen before)
  * **the _virtual-area_ height is the `line-height`**, and it is the height **used to compute the _line-box_'s height**
![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/line-height.png)

> _Inline elements have two different height_

That being said, it breaks down the popular belief that `line-height` is the distance between baselines. In CSS, it is not.

![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/line-height-yes-no.png)

> _In CSS, the line-height is not the distance between baselines_

The computed difference of height between the _virtual-area_ and the _content-area_ is called the leading. Half this leading is added on top of the _content-area_, the other half is added on the bottom of the _content-area_. **The _content-area_ is therefore always on the middle of the _virtual-area_**.

Based on its computed value, the `line-height` (_virtual-area_) can be equal, taller or smaller than the _content-area_. In case of a smaller _virtual-area_, leading is negative and a _line-box_ is smaller than its children.

There are also other kind of inline elements:

For these specific inline elements, height is computed based on their `height`, `margin` and `border` properties. If `height` is `auto`, then `line-height` is used and the _content-area_ is strictly equal to the `line-height`.

![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/line-height-inline-block.png)

> _Inline replaced elements, inline-block and blocksified inline elements have a content-area equal to their height, or line-height_

Anyway, the problem we're still facing is how much the `line-height`'s `normal` value is? And the answer, as for the computation of the _content-area_'s height, is to be found inside the font metrics.

So let's go back to FontForge. The Catamaran's em-square is 1000, but we're seeing many ascender/descender values:

  * generals _Ascent/Descent_: ascender is 770 and descender is 230. Used for character drawings. (table _"OS/2"_)
  * metrics _Ascent/Descent_: ascender is 1100 and descender is 540. Used for _content-area_'s height. (table _"hhea"_ and table _"OS/2"_)
  * metric _Line Gap_. Used for `line-height: normal`, by adding this value to _Ascent/Descent_ metrics. (table _"hhea"_)

In our case, the Catamaran font defines a 0 unit line gap, so **`line-height: normal` will be equal to the _content-area_, which is 1640 units, or 1.64**.

As a comparison, the Arial font describes an em-square of 2048 units, an ascender of 1854, a descender of 434 and a line gap of 67. It means that `font-size: 100px` gives a _content-area_ of 112px (1117 units) and a `line-height: normal` of 115px (1150 units or 1.15). All these metrics are font-specific, and set by the font designer.

**It becomes obvious that setting `line-height: 1` is a bad practice**. I remind you that unitless values are `font-size` relative, not _content-area_ relative, and dealing with a _virtual-area_ smaller than the _content-area_ is the origin of many of our problems.

![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/line-height-1.png)

> _Using line-height: 1 can create a line-box smaller than the content-area_

But not only `line-height: 1`. For what it's worth, on the 1117 fonts installed on my computer (yes, [I installed all fonts from Google Web Fonts](https://github.com/qrpike/Web-Font-Load)), 1059 fonts, around 95%, have a computed `line-height` greater than 1. Their computed `line-height` goes from 0.618 to 3.378. You've read it well, 3.378!

Small details on _line-box_ computation:

  * for inline elements, `padding` and `border` increases the background area, but not the _content-area_'s height (nor the _line-box_'s height). The _content-area_ is therefore not always what you see on screen. `margin-top` and `margin-bottom` have no effect.
  * for replaced inline elements, `inline-block` and _blocksified_ inline elements: `padding`, `margin` and `border` increases the `height`, so the _content-area_ and _line-box_'s height

I didn't mention the `vertical-align` property yet, even though it is an essential factor to compute a _line-box_'s height. We can even say that **`vertical-align` may have the leading role in inline formatting context**.

The default value is `baseline`. Do you remind font metrics ascender and descender? These values determine where the baseline stands, and so the ratio. As the ratio between ascenders and descenders is rarely 50/50, it may produce unexpected results, for example with siblings elements.

Start with that code:
    
    
    <p>
        <span>Ba</span>
        <span>Ba</span>
    </p>
    
    
    p {
        font-family: Catamaran;
        font-size: 100px;
        line-height: 200px;
    }

A `<p>` tag with 2 siblings `<span>` inheriting `font-family`, `font-size` and fixed `line-height`. Baselines will match and the _line-box_'s height is equal to their `line-height`.

![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/vertical-align-baseline.png)

> _Same font values, same baselines, everything seems OK_

What if the second element has a smaller `font-size`?
    
    
    span:last-child {
        font-size: 50px;
    }

As strange as it sounds, **default baseline alignment may result in a higher (!) _line-box_**, as seen in the image below. I remind you that a _line-box_'s height is computed from its child's highest point to its child's lowest point.

![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/vertical-align-baseline-nok.png)

> _A smaller child element may result in a higher line-box's height_

That could be [an argument in favor of using `line-height` unitless values](http://allthingssmitty.com/2017/01/30/nope-nope-nope-line-height-is-unitless/), but sometimes you need fixed ones to [create a perfect vertical rhythm](https://scotch.io/tutorials/aesthetic-sass-3-typography-and-vertical-rhythm#baseline-grids-and-vertical-rhythm). **To be honest, no matter what you choose, you'll always have trouble with inline alignments**.

Look at this another example. A `<p>` tag with `line-height: 200px`, containing a single `<span>` inheriting `line-height`
    
    
    <p>
        <span>Ba</span>
    </p>
    
    
    p {
        line-height: 200px;
    }
    span {
        font-family: Catamaran;
        font-size: 100px;
    }

How high is the _line-box_? We should expect 200px, but it's not what we get. The problem here is that the `<p>` has its own, different `font-family` (default to `serif`). Baselines between the `<p>` tag and the `<span>` are likely to be different, the height of the _line-box_ is therefore higher than expected. **This happens because browsers do their computation as if each _line-box_ starts with a zero-width character**, that the spec called a strut.

> An invisible character, but a visible impact.

To resume, we're facing the same previous problem as for siblings elements.

![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/vertical-align-strut.png)

> _Each child is aligned as if its line-box starts with an invisible zero-width character_

Baseline alignment is screwed, but what about `vertical-align: middle` to the rescue? As you can read in the spec, `middle` "aligns the vertical midpoint of the box with the baseline of the parent box plus half the x-height of the parent". **Baselines ratio are different, as well as x-height ratio, so `middle` alignment isn't reliable either**. Worst, in most scenarios, `middle` is never really "at the middle". Too many factors are involved and cannot be set via CSS (x-height, ascender/descender ratio, etc.)

As a side note, there are 4 other values, that may be useful in some cases:

  * `vertical-align: top` / `bottom` align to the top or the bottom of the _line-box_
  * `vertical-align: text-top` / `text-bottom` align to the top or the bottom of the _content-area_
![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/vertical-align-top-bottom-text.png)

> _Vertical-align: top, bottom, text-top and text-bottom_

Be careful though, in all cases, it aligns the _virtual-area_, so the invisible height. Look at this simple example using `vertical-align: top`. **Invisible `line-height` may produce odd, but unsurprising, results**.

> _vertical-align may produce odd result at first, but expected when visualizing line-height_

We've talked about how `line-height` and `vertical-align` work together, but now the question is: are font metrics controllable with CSS? Short answer: no. Even if I really hope so. Anyway, I think we have to play a bit. Font metrics are constant [3](http://iamvdo.me/en/blog/css-font-metrics-line-height-and-vertical-align), so we should be able to do something.

What if, for example, we want a text using the Catamaran font, where the capital height is exactly 100px high? Seems doable: let's do some maths.

First we set all font metrics as CSS custom properties [4](http://iamvdo.me/en/blog/css-font-metrics-line-height-and-vertical-align), then compute `font-size` to get a capital height of 100.
    
    
    p {
        /* font metrics */
        --font: Catamaran;
        --capitalHeight: 0.68;
        --descender: 0.54;
        --ascender: 1.1;
        --linegap: 0;
    
        /* desired font-size for capital height */
        --fontSize: 100;
    
        /* apply font-family */
        font-family: var(--font);
    
        /* compute font-size to get capital height equal desired font-size */
        --computedFontSize: (var(--fontSize) / var(--capitalHeight));
        font-size: calc(var(--computedFontSize) * 1px);
    }

![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/css-metrics-capital-height.png)

> _The capital height is now 100px high_

Pretty straightforward, isn't it? But what if we want the text to be visually at the middle, so that the remaining space is equally distributed on top and bottom of the "B" letter? To achieve that, we have to compute `vertical-align` based on ascender/descender ratio.
    
    
    p {
        …
        --lineheightNormal: (var(--ascender) + var(--descender) + var(--linegap));
        --contentArea: (var(--lineheightNormal) * var(--computedFontSize));
    }

Then, we need:

  * the distance from the bottom of the capital letter to the bottom edge
  * the distance from the top of the capital letter to the top edge

Like so:
    
    
    p {
        …
        --distanceBottom: (var(--descender));
        --distanceTop: (var(--ascender) - var(--capitalHeight));
    }

We can now compute `vertical-align`, which is the difference between the distances multiplied by the computed `font-size`. (we must apply this value to an inline child element)
    
    
    p {
        …
        --valign: ((var(--distanceBottom) - var(--distanceTop)) * var(--computedFontSize));
    }
    span {
        vertical-align: calc(var(--valign) * -1px);
    }

At the end, we set the desired `line-height` and compute it while maintaining a vertical alignment:
    
    
    p {
        …
        /* desired line-height */
        --lineheight: 3;
        line-height: calc(((var(--lineheight) * var(--fontSize)) - var(--valign)) * 1px);
    }

> _Results with different line-height. The text is always on the middle_

Adding an icon whose height is matching the letter "B" is now easy:
    
    
    span::before {
        content: '';
        display: inline-block;
        width: calc(1px * var(--fontSize));
        height: calc(1px * var(--fontSize));
        margin-right: 10px;
        background: url('https://cdn.pbrd.co/images/yBAKn5bbv.png');
        background-size: cover;
    }

![](http://iamvdo.me/content/01-blog/30-css-avance-metriques-des-fontes-line-height-et-vertical-align/css-metrics-results-icon.png)

> _Icon and B letter are the same height_

What we learned:

  * inline formatting context is really hard to understand
  * all inline elements have 2 height: 
    * the _content-area_ (based on font metrics)
    * the _virtual-area_ (`line-height`)
    * none of these 2 heights can be visualize with no doubt. (if you're a devtools developer and want to work on this, it could be awesome)
  * `line-height: normal` is based on font metrics
  * `line-height: n` may create a _virtual-area_ smaller than _content-area_
  * `vertical-align` is not very reliable
  * a _line-box_'s height is computed based on its children's `line-height` and `vertical-align` properties
  * we cannot easily get/set font metrics with CSS
  * there is a related future spec to help with vertical alignment: the [Line Grid module](https://drafts.csswg.org/css-line-grid/)

But I still love CSS :)
