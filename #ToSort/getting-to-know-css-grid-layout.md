# Getting to know CSS Grid Layout

_Captured: 2017-03-24 at 10:41 from [cm.engineering](https://cm.engineering/getting-to-know-css-grid-layout-818e43ca71a5#.d8af4bvjd)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*M1-XZtjX5vTYJtnk23Mjaw.png?q=20)![](https://cdn-images-1.medium.com/max/2000/1*M1-XZtjX5vTYJtnk23Mjaw.png)

> _Photos from [Unsplash](https://unsplash.com/)_

CSS Grid is the most critical layout feature to come to browsers since Flexbox. It allows us to escape some of the magic numbers, hacks, and workarounds that we've grown accustomed to using for the last 15 years. It brings simplicity to declaring layouts that will tear a chunk out of most of the major CSS frameworks, and reduce bloat in our own hand crafted styles.

If you're not familiar with what CSS Grid is, and you've made it this far, it's a layout tool that applies to a containing element which then manages how the child elements are spaced, sized, and aligned.

CSS Grid gives us powerful new abilities -- most notably for layout to be aware of both horizontal and vertical space at the same time, for changes to layout not to impact markup, and the ability adapt to available space without the need for media queries.

### Learning the minimum required

At first it might seem like Grid has a lot of new syntax to learn, but you only need a fraction to get started. This article will use examples to introduce you to the various concepts important to getting started to build with CSS Grid.

### Browser compatibility

CSS Grid is currently being rolled out to browsers and will appear in Safari 10.1, Firefox 52, Opera 44, Chrome 57.

There is an older legacy implementation available to Microsoft browsers which have a number of limitations, we'll only briefly cover legacy implementation to explain some of the differences between newer and older implementations and how you can get around them.

For most layouts, we will use the following feature query to allow older browsers to still serve layout they understand:
    
    
    **@supports** (display: grid) {  
        .grid {  
            display: grid;  
        }  
    }

Browsers that don't support _@supports_, or don't support grid, won't be served the feature.

To follow along properly with the examples in this article, you'll need to use a [Grid enabled browser](https://igalia.github.io/css-grid-layout/enable.html).

### Creating a two-column grid with gutters

To demonstrate how CSS Grid defines columns, we'll start with this layout:

> _Two column layout with gutters using grid-template-columns and grid-gap_

To create this grid we need to use `grid-template-columns` and `grid-gap`.

_Grid-template-columns_ declare how the columns of a grid will be laid out, it take a series of values separated by spaces, that declare the size of each column; the number of values specified give us the number of columns.

For example, a four column grid of 250px wide columns can be expressed like this:
    
    
    grid-template-columns: 250px 250px 250px 250px;

That same layout can also be expressed with a handy _repeat_ keyword.
    
    
    grid-template-columns: repeat(4, 250px);

#### Defining gutters

_Grid-gap_ specifies the size of gutters in grid layout, it can accept one or two values, if you specify two values you are defining both the row and the column's gutter size.

In our split two-column layout example we might declare our grid like this:
    
    
    .grid {  
      display: grid;  
      grid-template-columns: 50vw 50vw;  
      grid-gap: 1rem;  
    }

Unfortunately, the gap will be added to the overall width of the containing element making the calculation _100vw_ \+ _1rem_, and the layout will end up with a horizontal scroll-bar.

> _Horizontal scrollbar from using grid gap with viewport units_

In order to fix this space overflow, we need a slightly different solution. Enter the **fraction** unit or **FR**.

#### The fraction unit

A fraction unit takes up a share of available space; if 900px was the available space, and one element had one fraction, and another had two fractions -- the first would get 1/3 and the second would get 2/3 of that 900px.

Revising our new code with fractions replacing the view-port units:
    
    
    .grid {  
      display: grid;  
      grid-template-columns: 1fr 1fr;  
      grid-gap: 1rem;  
    }

#### Aligning the content

To align the content in our example, we declare grid on the child elements and use the alignment properties to position them on their track; a track is just a generic name for something that is a grid column or row. Grid, like Flexbox, has a series of alignment properties -- four values -- _start, center, end_, and _stretch_ which relate to where the children are on their appropriate track. Stretch, unlike the others, will pull the element from the start to the end of that track.

> _align-items and justify-content_

In our example, to get the content to center both vertically and horizontally we can apply these properties on the container:
    
    
    .center-content {  
        display: grid;  
        align-items: center;  
        justify-content: center;  
    }

#### Recreating the two column layout with legacy grid

To recreate the layout with legacy grid, we have to consider many of the limitations in the implementation. Not only does _grid-gap_ not exist in legacy grid, you must declare on each grid item where that grid item starts, otherwise it defaults to 1, meaning all of the grid children will stack on the first column.

The legacy version of this layout has to handle the lack of the gap feature by adding the gap as its own grid track, and also include where each item starts:
    
    
    .grid-legacy {  
       display: -ms-grid;  
       -ms-grid-columns: 1fr **1rem** 1fr; // gap replacement  
    }
    
    
    .grid-legacy:first-child {  
       -ms-grid-column: 1;  
    }
    
    
    .grid-legacy:last-child {  
        -ms-grid-column: 3;  
    }

#### Approaching alignment, and full height in legacy grid

Legacy grid has a similar problem to Flexbox in IE11, [setting min-height on the container won't necessarily be honored](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items). This problem is much easier to work around with Grid.

To do this we can use _the minmax_ function on the parent container's row, _minmax _specifies a range of the largest and smallest values a row or column could be.
    
    
    -ms-grid-rows: minmax(100vh, 1fr);

On the child items we can declare grid and set a single column and row of _1fr_.
    
    
    .ms-cell {  
       -ms-grid-columns: 1fr;  
       -ms-grid-rows: 1fr;  
    }

Lastly, because we can't align from the parent like Flexbox, or modern Grid, we have to use the elements themselves to align.
    
    
    .ms-align-center {  
        -ms-grid-column: 1;  
        -ms-grid-column-align: center; // like align-self in modern grid  
        -ms-grid-row-align: center; // like justify-self in modern grid  
    }

If you want to encourage Microsoft to update Grid in MS Edge, visit their [platform status page for CSS Grid update](https://developer.microsoft.com/en-us/microsoft-edge/platform/status/gridupdate/?q=grid) and up-vote it out of their backlog.

So far we've covered how to create columns, gutters, align content, and how we could support legacy grid. Let's experiment with how to create negative space with grid.

### Creating negative space with CSS Grid

One ability Grid allows you to do is declare where a column begins on the grid item with a property called `grid-column-start`, this opens up possibilities for creating negative space within the grid.

> _Negative space using grid-template-columns and grid-column-start_

One way to create negative space is to set a column a number above its actual position, leaving the grid item's original space open while it pushes that item across to a new column.

> _Pushing the first item along with grid-column-start_

In the negative space example above, the markup is a div wrapping another div.
    
    
    <div class="grid">  
        <div class="child"><!-- content --></div>  
    </div>

The grid is expressed like this:
    
    
    .grid {  
        display: grid;  
        grid-template-columns: 1fr 1fr;  
    }

To get the child to start in the right hand column, we make the child start at column 2.
    
    
    .child {  
        grid-column-start: 2;  
    }

**Note:** An inconsistency in Firefox 52 causes some vertical alignment problems where a [row-based FR unit doesn't stretch to the full viewport](https://bugzilla.mozilla.org/show_bug.cgi?id=1346699), to address this we make the children grid items, and add a single row of our desired height.
    
    
    .l-grid--full-height {  
        grid-template-rows: minmax(100vh, 1fr);  
    }

### Creating content dead-zones

In a four column layout, declaring `grid-column-start:2;` on a grid item that starts naturally in the third column will try to find the next available second column to fill the space.

> _Content deadzone created using grid-template-columns and grid-column-start_

The grid track will skip columns until it finds the next free second column. This provides us with a method to create dead-zones within the grid where no content grid tracks will be assigned.

### Creating rows

What if we wanted to split the layout into four? Everything we've covered so far about columns also applies to rows.
    
    
    .grid {  
        display: grid;  
        grid-template-columns: 1fr 1fr;  
        grid-template-rows: 250px 250px;  
    }

> _Creating grid layouts using both grid-template-columns and grid-template-rows together_

The problem with this example is it is an ideal scenario. Every grid item's content is small enough to never breach the specified row size. When dealing with rows, content changes everything. Take this example of what happens when your content overflows a specified row size:

> _Content overflows declared row sizes_

We've created two rows of 250px, if the content inside of a row overflows the row, it'll break out of its row and start to overlap the row's content below it. Not really a desired outcome.

### Setting a minimum with flexibility

What we need in this scenario is the ability to set a minimum size, but allow for it to be flexible for content, we can achieve this using the **minmax** keyword we used back in the legacy example.
    
    
    .grid {  
        grid-template-rows: minmax(250px, auto) minmax(250px, auto);  
    }

Now that we have covered the basics we need to create rows with content, we can start to build up more complex grids that are both horizontal and vertical.

> _Using grid-column-start and the span keyword to create complex grids. Photos from [Unsplash](https://unsplash.com/)_

### Creating more complex grids

We can start to create more complex grids by making grid items occupy multiple tracks within the grid. In a column, we can achieve this with grid-column-start and grid-column-end, or express it in shorthand like this:
    
    
    grid-column: 1 / 3;

The drawback of this approach is it's not very modular, and it can lead to writing a lot of code for positioning pieces of content.

The **span** keyword is more modular because we can place it anywhere and let the grid handle it. It allows us to define from its start position, a grid item will take multiple tracks:
    
    
    .span-column-3 {  
        grid-column-start: span 3;  
    }

Anywhere we put this class within a grid, it will cause that item to span three tracks from its current position.

### Planning out a layout using span

We can plan out multi-track layouts by breaking apart the layout to the smallest unit in the grid layout. In this example our smallest unit is highlighted:

> _The smallest grid item is used for grid columns so we can build up the larger items with span_

By building around the smallest unit, we can flexibly apply span classes to create interesting layouts, and since span is additive -- you can combine row and column tracks to create hierarchy in the grid.

### Flexible grids without media queries

While some of the previous examples could handle changes in available space, none of them were designed specifically for these changes. Grid has two extremely powerful features for dealing with changes in available space. These features are called _'auto-fit'_ and _'auto-fill' _and are used within a repeat function typically with a **minmax** function such as:
    
    
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));

These replace the number in repeat, and calculate how many columns or rows they can fit into a line. The main differences between the two is how they deal with the overflow of space on a line.

**Auto-fill** attempts to put the largest number of repeated items into a column that it can manage without overflowing. When there isn't enough space to add another item, the next element will be placed on the next line, and the space it couldn't fill is left open.

> _Example: Auto-fill. Auto-fill can leave spaces behind whereas auto-fit will collapse empty spaces to 0px_

**Auto-fit **behaves in a similar fashion to _auto-fill_ except any empty space will collapse and stretch the items on that line -- giving a flexbox-like experience that collapses columns as the available space gets smaller.

> _Example of grid-auto-fit_

Layout that relies on media queries is tied to the view-port, this isn't modular -- components within a system need to be able to adapt to the space they have available. So how might this look in practice?

> _Practical example of grid auto-fit_

### This is just a fraction of the basics

We've had nearly fifteen years of CSS floats dominating layout, we've learnt just about everything you could do with floats -- CSS Grid is the new kid on the block and there's still so much to experiment with and learn.

At the moment the most important step is just to start building with it to get comfortable enough to create more advanced layouts. Grid is mostly uncharted territory, once we understand its capabilities better and start to combine it with other features, we'll be able to make more interesting, flexible layouts with less overhead, and reduce the need for framework abstractions.

If you're interested in going further with CSS Grid than this article, try [Rachel Andrew's GridByExample](http://gridbyexample.com/), which explores every single feature of CSS Grid in demo with explanation.
