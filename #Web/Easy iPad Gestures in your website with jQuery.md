# Easy iPad Gestures in your website with jQuery

_Captured: 2015-06-09 at 21:37 from [www.janes.co.za](http://www.janes.co.za/easy-ipad-gestures-in-your-website-with-jquery/#.UEKoPcHiY0V)_

![](http://www.janes.co.za/wp-content/uploads/2011/06/ipad-241x300.jpg)

Recently in my surf across the web I came across this and this is actually quite awesome. Seeing iPads are becoming such a common device to use I thought it would be great to be able to include the swipe gestures functionality into your site or maybe into the ipad version of your site.

jQuery makes this so easy to integrate and use that I couldn't help but fool around with it.

Here is a quick tutorial on using it.

First off all make sure you have the latest jQuery library included in your site. You can download this from here or include it directly from the site like this:

Second step, download the TouchWipe library from the author website : [TouchWipe](http://www.netcu.de/jquery-touchwipe-iphone-ipad-library)

For this example I am just going to bind the Touchwipe to the <body>.

Include the touchwipe library before the tag. ex:

1
`<script type=``"text/javascript"` `src=``"jquery.touchwipe.1.1.1.js"``></script>`

Next initialise TouchWipe on to the body tag, and give the gestures the chosen action to perform, for this example I just used alerts

12345678
`$(document).ready(``function``(){``$(``'body'``).touchwipe({``wipeLeft: ``function``(){ alert(``'You swiped left!'``) },``wipeRight: ``function``(){ alert(``'You swiped right!'``) },``wipeUp: ``function``(){ alert(``'You swiped up!'``) },``wipeDown: ``function``(){ alert(``'You swiped down!'``) }``})``})`

Touchwipe can be added to a specific div aswell rather than the body tag.

And that is it. You could add that to any html page to add swipe Gestures. I didn't put much meat into this post as there is so much you could do with it.

[Check out the demo on your ipad here](http://play.janes.co.za/i/index.html)

If anyone wants examples, feel free to leave a reply.

## **Update : **

Refer from adding this directly to your body tag, as this will affect your whole site then. Also if you are only going to use left and right swipes and want it to use normal scrolling on up and down swipes. A parameter can be added in your javascript.

You can add "preventDefaultEvents: false" after you swipe functions to prevent the plugin from overwriting your normal events.
