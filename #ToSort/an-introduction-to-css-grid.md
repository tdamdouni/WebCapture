# An Introduction to CSS Grid

_Captured: 2017-05-08 at 17:21 from [speckyboy.com](https://speckyboy.com/css-grid/)_

CSS Grid has become one of the more talked about developments in web design in recent times. The reason for all of the excitement is simple: CSS Grid looks like it just may change the way we create grid layouts. That's a pretty big deal.

If you're looking to learn more about what CSS Grid is and what it does, you've come to the right place. We'll provide a rundown of what you need to know, along with some helpful resources to get you started.

## First Thing's First

One thing we need to note is that, as of this writing, CSS Grid is still a [work in progress](https://drafts.csswg.org/css-grid/) according to the W3C. That means that the final version of this specification hasn't been fully released just yet. Overall, [browser support](https://css-tricks.com/snippets/css/complete-guide-grid/#grid-browser-support) is a bit spotty. But that will certainly change as the final spec rolls out.

That being said, it's never a bad idea to get ahead of the curve when it comes to learning new techniques. Just keep in mind that some things may change between now and the official release. With that fair warning out of the way, let's dig in and learn more about this important development in web design.

![Layout in 2-D](https://speckycdn-sdm.netdna-ssl.com/wp-content/uploads/2017/05/css-grid-07.png)

## Layout in 2-D

CSS Grid is a system that allows for building 2-D grid layouts. While the term "2-D" doesn't sound so groundbreaking, it absolutely is in this particular case. You see, CSS Grid will allow you to manage layout according to both _columns_ and _rows_.

[Flexbox](https://speckyboy.com/getting-started-css-flexbox/), by comparison, is really just meant for columns (1-D, if you will). Using CSS Grid, designers will be able to achieve layouts that were downright difficult before. In fact, some of these things were on our wish lists since the days of table-based layouts.

With tables, it was easy enough to have a column take up multiple rows using the `rowspan` attribute. CSS didn't really have a direct equivalent. That led to using multiple nested containers, floats, clearfixes, etc. to achieve the desired effect. This is exactly what CSS Grid aims to fix.

The good thing is that if you are at all familiar with Flexbox, then you'll be off to a great start with CSS Grid. With both Flexbox and CSS Grid, things are set up via a parent container and subsequent items (children). And, like Flexbox, content order can be set via CSS. This is particularly nice when adjusting content for mobile devices. What shows up first on a desktop grid may be pushed down lower in the display order on smaller screens.

## A Simple CSS Grid Example

Let's look at a very basic CSS Grid layout. There are five columns and two rows. The fifth column is unique in that it spans both rows and will display on the right side of the layout.

It actually takes very little code to make this happen. Take a look:

![A Simple CSS Grid Example](https://speckycdn-sdm.netdna-ssl.com/wp-content/uploads/2017/05/css-grid-01.png)

**CSS**:
    
    
    .container {
    display: grid;
    grid-template-columns: [col1] 33% [col2] 33% [col3] 33%;
    grid-gap: 10px;
    grid-template-rows: [row1] 47% [row2] 47%;
    text-align: center;
    color: #FFF;}.grid-cell-1 {
    background-color: #658db5;
    padding: 25px;
    border-radius: 6px;}.grid-cell-2 {
    background-color: #658db5;
    padding: 25px;
    border-radius: 6px;}.grid-cell-3 {
    background-color: #658db5;
    padding: 25px;
    border-radius: 6px;}.grid-cell-4 {
    background-color: #658db5;
    padding: 25px;
    border-radius: 6px;}.grid-cell-5 {
    background-color: #898989;
    grid-column: 3 ;
    grid-row: 1 / 3;
    padding: 25px;
    border-radius: 6px;}

A few notes on the CSS:

  * In `.container`, notice that we have the ability to define the width of columns and height of rows. We can also individually name columns and rows with the use of brackets: `[name]`
  * `.grid-cell-5` has a couple of interesting attributes. `grid-column: 3;` tells the browser to start this item as the third column. Meanwhile, `grid-row: 1/3;` says that the cell will span from the first row until the start of the (non-existent) third row.

**HTML:**
    
    
    <div class="container"><div class="grid-cell-1">1</div><div class="grid-cell-2">2</div><div class="grid-cell-3">3</div><div class="grid-cell-4">4</div><div class="grid-cell-5">5</div></div>

Doing this type of layout without CSS Grid would be significantly more challenging. There are, of course, a number of more complicated layouts that can be achieved. But hopefully this will illustrate the ease in which something basic can be setup.

**[See it on CodePen.](https://codepen.io/karks88/pen/eWWaPg)**

## CSS Grid Resources

There are a number of outstanding guides and tutorials out there to help you make the most out of CSS Grid. Here are just a few to get you started:

## You might also like...
