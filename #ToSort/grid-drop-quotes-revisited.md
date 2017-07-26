# Grid Drop Quotes, Revisited

_Captured: 2017-04-22 at 10:33 from [meyerweb.com](http://meyerweb.com/eric/thoughts/2017/04/10/grid-drop-quotes-revisited/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)_

In last week's [Grid-Powered Drop Quotes](http://meyerweb.com/eric/thoughts/2017/04/07/grid-powered-drop-quotes/), I overlooked a potential problem with the styles I created. Fortunately, [Philippe Wittenbergh](https://l-c-n.com/) caught it and pointed it out, and we both hit on the same solution.

The problem-in-waiting is that the big drop quote will force a gap between the first child element of the blockquote and the second, if the first child is short. You can see this in the demo below ([external version also available](http://meyerweb.com/eric/css/examples/grid/drop-quote-2.html)), where I made the first paragraph only a few words long. If you select the "Borders" option, you can see the problem more clearly.

Borders Row span Short quote Line height

> Besides, Grid was coming.
> 
> In the run-up to Grid support being released to the public, I was focused on learning and teaching Grid, creating test cases, and using it to build figures for publication. And then, March 7th, 2017, it shipped to the public in Firefox 52. I tweeted and posted [an article](http://meyerweb.com/eric/thoughts/2017/03/07/welcome-to-the-grid/) and [demo](http://meyerweb.com/eric/css/examples/grid/masks.html) I'd put together the night before, and sat back in wonderment that the day had finally come to pass. After 20+ years of CSS, finally, a real layout system, a set of properties and values designed from the outset for that purpose.
> 
> And then I decided, more or less in that moment, to convert my personal site to use Grid for its main-level layout. It took me less than five minutes…

The solution is to have the drop quote span multiple rows. The original CSS went something like this, simplified for the sake of clarity:
    
    
    blockquote::before {
        grid-column: 1;
        content: "“";
        font-size: 5em;
    }

That suffices to drop the drop quote into column 1 (explicitly) and row one (implicitly). The row is as tall as the tallest of the grid items it contains, so in this case, the quote controls the row height.

The fix:
    
    
    blockquote::before {
        grid-row: 1 / span 10;
        grid-column: 1;
        content: "“";
        font-size: 5em;
    }

You can see that effect by enabling the "Row span" option. I recommend trying it first with borders turned on, just to see how the element boxes change.

But wait! Why `span 10`? There aren't that many rows in the blockquote, because there aren't that many child elements! That's okay: the extra rows will be auto-created, but because they contain no content, the rows are of no height. This means that in cases where there's a blockquote with a lot of short child elements--think a passage of snappy dialogue--the pseudo-element will have more than enough spannability. I could've gone with `span 5` or similar, to echo the font sizing of the drop quote, but no sense risking having too little spannability. (Which is a word I made up, then discovered it seems to have a meaning in mathematics, so I hope I'm not implying some sort of topological set unity of something.)

Auto-row generation may seem like dark magic, but you're already soaking in it: remember how none of the blockquote's child elements are explicitly given a row number, nor did I define rows with the `grid-template-rows` property? That means they're _all_ auto-created rows. This means if you do something like specify `grid-auto-rows: 1em`, then all the rows will be one em tall, with the contents spilling out and overlapping with each other. For extra fun, try setting your auto row height to `0px` instead! (Warning: do not attempt where prohibited by law.)

The other thing Philippe pointed out was that in cases where the blockquote has only a single child element that's one or two lines tall, the drop quote will not only set the height of the row, but the entire grid. You can create this situation by selecting the "Short quote" option; again, I recommend leaving "Borders" enabled so you can see what's happening.

Philippe's proposal was to bring the `line-height` of the drop quote to nothing or almost nothing, and add some top margin to make up the difference. For example:
    
    
    blockquote::before {
        grid-column: 1;
        content: "“";
        font-size: 5em;
        line-height: 1px;
        margin-top: 0.33em;
    }

This certainly works, as you can see by selecting the "Line height" option. My concern is that having a great big drop quote next to a single-line blockquote is…not optimal. I'd be more inclined to add a class for short blockquotes, and then restrict the drop quote effect to blockquotes without that class. For example:
    
    
    blockquote:not(.short)::before {
        grid-column: 1;
        content: "“";
        font-size: 5em;
    }

That removes the need to fiddle with line heights and top margins, in exchange for remembering to class appropriately. That's a fair trade as far as I'm concerned. Your preference may vary, of course.

Many thanks to Philippe for pointing out the error and proposing solutions!
