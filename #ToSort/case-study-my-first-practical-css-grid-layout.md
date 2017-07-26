# Case Study: My First Practical CSS Grid Layout

_Captured: 2017-03-29 at 00:53 from [cloudfour.com](https://cloudfour.com/thinks/first-css-grid-layout/)_

![](https://cdn.cloudfour.com/wp-content/uploads/2017/03/grid-responsive.gif)

Like a lot of my peers, I've been watching the [astonishingly rapid adoption of CSS Grid Layout](http://caniuse.com/#feat=css-grid) with great anticipation thanks to the amazing work of people like [Rachel Andrew](http://gridbyexample.com/), [Jen Simmons](http://jensimmons.com/post/feb-27-2017/learn-css-grid) and [Chris House](http://chris.house/blog/a-complete-guide-css-grid-layout/) to demonstrate, document and evangelize this game-changing set of new design tools.

Unfortunately, my brain tends to jettison technical knowledge I've yet to find a practical application for. As much as I wanted to commit all the `grid-*` rules to memory after watching a talk or walking myself through a demo step-by-step, doing so proved difficult as long as those styles relied on Firefox Developer Edition or an experimental Chrome flag.

But as of Firefox 52 and Chrome 57, that's no longer the case. And almost immediately, a challenge cropped up in one of our projects that served as a simple, self-contained example of how grid layout can make things easier. While it may not be as impressive or inspiring as [Jen Simmons' layout experiments](http://labs.jensimmons.com/), I've found that little victories like this often pave the way for more inventiveness later on.

![](https://cdn.cloudfour.com/wp-content/uploads/2017/03/goal-tweaked.png)

I was provided page content with this priority:

  1. Introductory text
  2. Actionable links organized into two sections
  3. Deeper explanatory text

As space allows, I want the link sections to display side by side, with equal heights for balance. At wider viewports, I'd like those sections to occupy a sidebar, with all the prose content flowing together in the remaining space.

The markup is structured like so:
    
    
    <div class="container">
      <div class="prose"></div>
      <div class="sidebar">
        <div class="box"></div>
        <div class="box"></div>
      </div>
      <div class="prose"></div>
    </div>
    

For this design, we want every element to be `1.5em` apart from its neighbors on every side. I start by applying [Samantha Zhang's technique](https://alistapart.com/article/learning-from-lego-a-step-forward-in-modular-web-design) of half-padding on the container and its children:
    
    
    .container,
    .prose,
    .sidebar {
      padding: 0.75em;
    }
    

But this doesn't take into account the sidebar boxes, which _also_ need gaps. I can't use `padding` on those without distorting their appearance. I could add containing elements, but instead I choose `margin` and `display: flex;` to prevent whitespace collapse (we'll need Flexbox on these elements pretty soon anyway). I also need to _negate_ some of the sidebar's `margin` to account for this second level of whitespace:
    
    
    .sidebar {
      display: flex;
      flex-direction: column;
      margin: -0.75em;
      position: relative;
    }
    
    .box {
      margin: 0.75em;
    }
    

Now time to make it responsive! At modest viewport widths, we can piggy-back on that `display: flex` rule we just wrote to arrange sidebar content evenly across a row:
    
    
    @media (min-width: 34em) and (max-width: 49.9375em) {
      .sidebar {
        flex-direction: row;
      }
    
      .box {
        flex: 50%;
      }
    }
    

Once the viewport is large enough, I want the prose content on the left and the sidebar on the right. I decide to float both types of elements, which means I'll also need a [clearfix](https://css-tricks.com/snippets/css/clear-fix/) on the container:
    
    
    .container::after {
      clear: both;
      content: " ";
      display: table;
    }
    
    @media (min-width: 50em) {
      .prose {
        float: left;
        width: 66.666%;
      }
    
      .sidebar {
        float: right;
        width: 33.333%;
      }
    }
    

And here's [the end result](http://codepen.io/tylersticka/pen/vxdprZ/left?editors=0100) with layout elements outlined:

![Responsive demo without grid layout](https://cdn.cloudfour.com/wp-content/uploads/2017/03/demo-before-12fps.gif)

While the CSS in that demo isn't the gnarliest I've written, it's easy to take for granted some of its more baffling techniques:

  * To get equal whitespace around responsive patterns, we have to define half of it on a containing element, half on the children.
  * Flexbox allows us to communicate our design intent using terms like `row` and `column`, but only one or the other, which made us regress to the less intuitive `float` property when we needed to modify both axes at the same time.
  * Because we had to float _every_ child element, we were forced to use pseudo elements to artificially `clear` the container to avoid disrupting any page elements that may follow.

You might suggest I could have used a different technique, but few are without compromise. Absolute-position the sidebar, and now its content can never exceed that of the prose. Move the sidebar to the end of the markup and change it with `order` at small sizes, and you may have to adjust your tab indexes for assistive devices.

CSS Grid Layout is different. It's been designed from the ground up as a two-dimensional layout system for the web.

Let's see how it applies to this layout.

I tell the browser that the container will use grid, and the gap between items should be `1.5em`… no division required:
    
    
    .container {
      display: grid;
      grid-gap: 1.5em;
      padding: 1.5em;
    }
    

We also want the sidebar to use the same layout style and whitespace. Eventually we'll be able to use `[display: subgrid`](http://chris.house/blog/a-complete-guide-css-grid-layout/#prop-display) for that, but for now it isn't too hard:
    
    
    .sidebar {
      display: inherit;
      grid-gap: inherit;
    }
    

That's all we need for the mobile-first layout. At medium widths, I tell the sidebar to arrange its children into two equal-width columns, each taking up half of the available space:
    
    
    @media (min-width: 34em) and (max-width: 49.9375em) {
      .sidebar {
        grid-template-columns: 1fr 1fr;
      }
    }
    

([The `fr` unit](https://alligator.io/css/css-grid-layout-fr-unit/) is new and I love it. It stands for "fractional," and it basically means "one part of the available space." We could have also used `50% 50%`, but then we'd have to do some extra math to account for the `grid-gap`.)

At large sizes, we apply the same technique to the container, except we make the first column `2fr` so it will take up two-thirds of the available space:
    
    
    @media (min-width: 50em) {
      .container {
        grid-template-columns: 2fr 1fr;
      }
    }
    

By default, the sidebar will be one row tall, and each of its children will stretch to fill the available space. The final step is [spanning the sidebar across both of our content rows](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Line-based_Placement_with_CSS_Grid#Using_the_span_keyword), and sizing its children based on [the minimum size necessary to display their content](https://www.w3.org/TR/css3-grid-layout/#valdef-grid-template-columns-min-content):
    
    
    @media (min-width: 50em) {
      .sidebar {
        grid-auto-rows: min-content;
        grid-row: span 2;
      }
    }
    

That's it! Here's [the freshly grid'dled version](http://codepen.io/tylersticka/pen/wJyprm/left?editors=0100) of our earlier demo as it appears in the latest Firefox and Chrome:

![Responsive demo recreated using CSS grid layout](https://cdn.cloudfour.com/wp-content/uploads/2017/03/demo-after-12fps.gif)

Barely more than half the required CSS, no negative margins and almost no math! Hooray!

Confession time: I struggled making the above grid demo. I had to get a lot of help from my Cloud Four cohort [Erik Jung](https://cloudfour.com/is/erik/) to get it working as intended. In hindsight, I think my greatest enemy was my own 15 (!) years of experience writing stylesheets. I'm so used to having to _abstract_ my design intent, to speak the language of CSS and work around its quirks, that I made the task harder for myself than it needed to be. I wasted time trying to hack around problems, when all I had to do was say "hey, make that `div` span two rows."

My takeaway from this exercise is that CSS Grid Layout is awesome, and I've _barely_ scratched the surface of its capabilities. It's also heartening to know every browser that supports Grid also supports [feature queries](https://hacks.mozilla.org/2016/08/using-feature-queries-in-css/), so we can probably start using it sooner than expected. The next time I'm wrangling a layout, I'm going to approach the problem as a student, resisting the mental calluses that have formed from years of workarounds.

I'm looking forward to it!
