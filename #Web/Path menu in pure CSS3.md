# Path menu in pure CSS3

_Captured: 2015-09-26 at 17:20 from [lab.victorcoulon.fr](http://lab.victorcoulon.fr/css/path-menu/)_

I'm fall in love with the new UI of [Path](http://path.com). I really love the user interaction design like the "add menu". So, as I'm a front-end developer, I tried to recreate the same thing on my browser.

Firstly, I posted a video of the effect on [dribbble](http://dribbble.com/shots/339001-Path-menu-recreated-in-css3) and now, I share my code.

## An experiment in CSS

I made the choice to do this with only html/css3 and no images whatsoever.  
There is **0 line of javascript**.  
I'm aware that you can do the same with a bit of javascript to be compliant with others browsers. But, It was not my goal :)

## How was this made?

To calculate the coordinates of items and generate the animation, I used Sass+Compass.  
I used a math formula in order to add the items's position on the arc of circle. So, you can add or remove items without rewrite the code.  
Finally, I generate a keyframe animation for each item. To be honnest, I had a lot of problems to use keyframes and Sass. It's for this reason, that it's only compliant with Webkit.

You can fork **[the source](http://github.com/victa/path-menu)** on github !

Follow [me](http://twitter.com/_victa) on Twitter! And ask any questions you want or send comments.
