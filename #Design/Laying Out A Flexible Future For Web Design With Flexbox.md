# Laying Out A Flexible Future For Web Design With Flexbox 

_Captured: 2015-08-17 at 17:28 from [www.smashingmagazine.com](http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/?utm_medium=App.net+Broadcast&utm_source=PourOver)_

CSS floats and clears define web layout today. Based on principles derived from centuries of print design, they've worked well enough -- even if, strictly speaking, floats weren't meant for that purpose. Neither were tables, but that didn't stop us in the 1990s.

Nevertheless, the **future of web layout is bright**, thanks to [flexbox](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Flexible_boxes/). The CSS layout mechanism lets us arrange elements in a truly web-like way. Some elements can be fixed, while others scroll. The order in which they appear can be independent of the source order. And everything can fit a range of screen sizes, from widescreen TVs to smartphones -- and even devices as yet unimagined. [Browser support is fantastic](http://caniuse.com/#search=flexbox) (except _you-know-who_). Yep, it's a great time to jump into flexbox if you haven't done so yet.

But changing our ways isn't easy. **Flexbox has a dizzying array of features**, few of which are familiar. It's a lot to take in. Luckily, for layout purposes, you need to know only a few basics. Let's take a look at how we could create a basic Gmail-like, flexbox-based interface. If you haven't explored or fully understood flexbox yet, this piece will revisit and explain a few things that might be confusing at first.

Flexbox requires a new way of thinking. Instead of arranging items in left-to-right, top-to-bottom rows and columns, we arrange blocks on a line -- two lines, in fact, a main axis and a cross axis, the first of which we'll use today. Think of the **main axis as a rope** along which boxes (divs or other HTML elements) are strung. The metaphorical rope runs from one end of its container to the other, a taut and invisible axis. This leads to four interesting concepts.

First, we can slide the "boxes" to one side of the "rope" or the other, center them or distribute them evenly. That means objects can stick to one side of a layout or the other -- say, to the left or right edge of the screen, no matter the screen's width. Even distribution means they will adapt well to any size screen, which is ideal in our [multi-screen world](http://www.smashingmagazine.com/2011/01/12/guidelines-for-responsive-web-design/).

![Illustration of boxes pushed to the left.](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2015/06/01-push-left-opt.png)  


> _Flexbox allows designers to push HTML elements to either end of the "rope."_

We can also **reverse** the string, so that boxes run in the opposite direction, without editing the HTML. This is similar to the [sort-order technique](http://foundation.zurb.com/docs/components/grid.html#source-ordering) that lets us flip columns around -- except the third trait takes that a step further.

![Illustration of boxes pushed to the right.](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2015/06/02-flip-horizontal-opt.png)  


> _Both the order and position of elements may be flipped._

Thirdly, we can turn the rope by 90 degrees to dangle from the top of its container, instead of running from side to side. Media queries and flexbox's ability make it possible to run items -- say, a header, article and footer -- down a smartphone's screen but left to right on a desktop computer. What used to be called rows can now run top to bottom or bottom to top with a dash of CSS.

![Illustration of boxes hanging from the top of a box.](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2015/06/03-vertical-hang-opt.png)  


> _The entire arrangement can turn 90 degrees, "hanging" from the top of the container._

Finally, we can control which boxes come first, second, third and so forth on the rope **without editing the HTML**. This is huge. It means we can structure an HTML document for, say, [SEO](http://www.smashingmagazine.com/2013/11/15/seo-for-responsive-websites/), [accessibility](http://zurb.com/university/lessons/five-minutes-towards-an-accessible-page) or plain ol' [semantics](http://html5doctor.com/lets-talk-about-semantics/) -- independent of layout. Want to center elements vertically? No problem. Want navigation at the end of your HTML but at the beginning of your layout? Sure. Want to experiment with different layouts? It's all in the CSS. And just like that, we're already thinking in terms of content and devices, not rigid grids.

![Illustration of boxes in random order.](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2015/06/04-reordered-horizontal-opt.png)  


> _The exact order of elements can change with CSS -- and without changing the HTML._

There's more, but this covers the basics for now. To recap:

  1. Blocks are strung along an invisible line.
  2. We can push them to and fro along that line.
  3. We can reverse the line, thus reversing the boxes' order.
  4. The line can turn 90 degrees.
  5. We can shuffle things along the line in any order we please, regardless of the HTML.

Order is an important concept in flexbox. Let's take a basic HTML document: A typical blog post would include certain bits of information.

  * **header**  
website title, description, search form (These frame the content and inform people where they are.)
  * **meta data**  
author/publisher, date, topic(s) (These help people decide whether the content is relevant to their needs.)
  * **main content**  
what the page is all about (the reason the page exists)
  * **supplemental content**  
related information (teasers, links, "See also")
  * **navigation**  
links to elsewhere on the website (high-level topics)
  * **footer**  
copyright, RSS, social media, newsletter registration

These elements are listed in order of what search engines or screen readers might scan. Now, let's dangle a "rope" from the top of a mobile device and reorder them to put content first.

  1. main content
  2. meta data
  3. supplemental content
  4. header
  5. navigation
  6. footer

Meanwhile, desktop computers would have a different view.

  1. header
  2. meta data
  3. main content
  4. supplemental content
  5. navigation
  6. footer

Wait, that's not quite right. We want navigation at the top, and flexbox makes that a snap.

It follows that you can also put "ropes" inside of boxes, and all of the rules apply anew. But first, let's talk about order. Here's where things get tricky.

Each flexbox layout -- each box -- can contain another set of boxes strung along their own rope. That rope can run from left to right or vice versa, from top to bottom or vice versa, and push objects to either end, center them or distribute them. And while that flexibility opens up many possibilities, it also means we need to plan our layouts carefully.

![Illustration of boxes within a box.](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2015/06/05-nested-horizontal-opt.png)  


> _Elements along a flexbox rope may, in turn, contain other flexbox ropes._

Let's start with some content to understand why things get complicated; this isn't necessarily in order of layout (i.e. the order in which people see it). Imagine giving a presentation to an audience. You tell them what you're going to say, then you say it, and you wrap up with a summary of what you've said. Our hypothetical page follows a familiar structure:

  * header
  * the current message
  * message list
  * links to inbox(es), archive, etc.
  * footer

To keep things simple, we'll work with a familiar layout.

![Illustration of an email app layout](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2015/06/06-gmail-diagram-opt.png)  


> _A typical arrangement for an email app._

There are two flexbox layouts here. The first has three boxes from top to bottom. The second layout resides inside the middle box, from right to left.

The header and footer span the width of the viewport. The navigation fits in a small column to the left, and the content area lets the user scroll when it contains more information than can be displayed. We could achieve this with a few floats and fixed positions, but flexbox gives us more options with less markup. Let's take a look.

The outer container has only three sections, wrapped in a `.flex-container` element:
    
    
    <body>
      <div class="flex-container">
        <header>…</header>
        <main class="flex-container">…</main>
        <footer>…</footer>
      </div>
    </body>
    

We call it `flex-container` to describe its purpose in a somewhat semantic way. At least our CSS will make sense.

Inside the `main` element, we need three blocks:
    
    
    <main class="flex-container content">
      <article class="message">…</article>
      <div class="message-list">…</div>
      <nav class="mailbox-list">…</nav>
    </main>
    

This example uses `article` as an independent entity, [not in the magazine sense](http://html5doctor.com/lets-talk-about-semantics/#what-about-adding-more-elements).

We need to tell browsers that these elements will be, um, flexible.
    
    
    .flex-container,
    .flex-container header,
    .flex-container footer {
      display: -webkit-box;
      display: -moz-box;
      display: -ms-flexbox;
      display: -webkit-flex;
      display: flex;
    }
    

Note that this applies flexbox to the major containers, not the content.

Based on the design sketch, we know that certain elements will have widths and heights. The `body`'s header and footer, for example, will be long, thin strips compared to the `main`'s tall, relatively narrow left-hand navigation bars. The `article`'s content area fills the rest of the space. In the interest of staying flexible regardless of screen size (and clarity in this tutorial), these areas won't have fixed widths.
    
    
    .message {
      flex-basis: 70%;
    }
    .message-list {
      flex-basis: 15%;
    }
    .mailbox-list {
      flex-basis: 15%;
    }
    .flex-container header,
    .flex-container footer {
      width: 100%;
      height: 5rem;
    }

Here, `flex-basis` is like width -- as long as the main axis is horizontal. If we dangle the rope from the top, then `flex-basis` becomes height automatically. Handy!

This one's easy. Just add `overflow: scroll` to the `main` element to keep it from overriding the header and footer. **Handy tip:** Try `overflow: auto` to hide scroll bars (when they're unnecessary) [in most browsers](http://caniuse.com/#search=overflow).
    
    
    .message {
      flex-basis: 70%;
      overflow: scroll;
    }

At this point, the header's form should float with a little margin, even when the browser is resized. The content should flow well in browser windows of any size. And if a browser doesn't support flexbox, then the page will turn into a content-first layout.

That's important because [you-know-who doesn't support flexbox](http://caniuse.com/#search=flexbox) yet. Every modern version does, however, so it's a matter of when users update their software. So, where is flexbox supported?

  * Safari for iOS 7.1 and later
  * Android browser 4.4 and later
  * Chrome for Android 42 and later
  * Opera 27 and later

Clicky has a graph of the [marketshare of assorted mobile browsers.](https://clicky.com/marketshare/global/web-browsers/mobile/)

What about older browsers? Solutions vary wildly depending on the layout you're trying to achieve, although we can derive a few tips.

The safest way to support flexbox-incapable browsers is to write CSS in the order in which you want it to appear. Start by [thinking semantically](http://www.smashingmagazine.com/2013/08/20/semantic-css-with-intelligent-selectors/). Old versions of Internet Explorer will ignore flexbox properties -- thankfully, good ol' [conditional comments](http://www.quirksmode.org/css/condcom.html) enable us to apply floats and clears to semantic layouts. Old versions of other browsers tend to give you mobile-friendly layouts that stack content in a logical order. So flexbox can co-exist with floats, `display: table-cell` and positioning, so that smart browsers will apply flexbox properties while legacy browsers will ignore them. Finally, if you're feeling experimental, then try [Flexie](http://flexiejs.com), which amends old browsers with a JavaScript-based polyfill.

Give flexbox a go. While it offers many options, most -- such as alignment -- come into play after you've settled on how elements are arranged. The central techniques, which we've covered here, are alignment, direction, orientation, order and nesting. We've found these to be critical in Foundation's new layout framework: If you can wrap your head around alignment, direction, orientation and order, then you're well on your way to a flexible future. [Check out my demo](http://codepen.io/benthinkin/pen/wadabR) to see it in action (keep in mind that it's not responsive just yet).

To learn more about flexbox, check out the following:

_(da, ml, al)_

**SmashingConf** isn't the eighth wonder of the world, but we are pretty close. Join us at the [SmashingConf Barcelona](http://auslieferung.commindo-media-ressourcen.de/www/delivery/ck.php?oaparams=2__bannerid=11335__zoneid=94__OXLCA=1__cb=88a1172225__oadest=http%3A%2F%2Fauslieferung.commindo-media-ressourcen.de%2Fwww%2Fdelivery%2Fck.php%3Foaparams%3D2__bannerid%3D6259__zoneid%3D68__OXLCA%3D1__cb%3D4bbeba9171__oadest%3Dhttp%3A%2F%2Fwww.smashingmagazine.com%2F2015%2F06%2Fsmashingconf-barcelona-2015-release%2F) on **October 20-21, 2015** -- with fantastic talks, practical workshops and lots of good ol' networking. You won't be disappointed. We can help you [convince your boss](http://auslieferung.commindo-media-ressourcen.de/www/delivery/ck.php?oaparams=2__bannerid=11335__zoneid=94__OXLCA=1__cb=88a1172225__oadest=http%3A%2F%2Fauslieferung.commindo-media-ressourcen.de%2Fwww%2Fdelivery%2Fck.php%3Foaparams%3D2__bannerid%3D6259__zoneid%3D68__OXLCA%3D1__cb%3D4bbeba9171__oadest%3Dhttp%3A%2F%2Fsmashingconf.com%2Fpdf%2F8-reasons-for-Smashing-Conference-Barcelona-2015.pdf) (PDF), too.
