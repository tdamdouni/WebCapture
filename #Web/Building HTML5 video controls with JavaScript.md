# Building HTML5 video controls with JavaScript

_Captured: 2016-02-16 at 01:35 from [www.broken-links.com](https://www.broken-links.com/2009/10/06/building-html5-video-controls-with-javascript/)_

**Warning** This article was written over six months ago, and may contain outdated information.

The [HTML5 video element](http://www.whatwg.org/specs/web-apps/current-work/multipage/video.html#video) is now included in Firefox, Safari & Chrome, and on its way in Opera. By using JavaScript to access the [media elements API](http://www.whatwg.org/specs/web-apps/current-work/multipage/media-elements.html#media-elements) it's easy to build your own custom controls for it; in this article I'm going to show how I built a (very) basic control interface.

A quick disclaimer: my JavaScript is a little rusty, so may not use best practice throughout; if you can see a way my code could be better, don't hesitate to let me know.

Anyway, [here's the finished demo](https://www.broken-links.com/tests/video/).

## Getting started

First you must include the `video` element. There are a number of attributes available, but for our purposes we need define only the `src`, which is the URI of our video file **Update**: changed the markup to use the more correct `source` elements inside `video`.
    
    
    <video>
      <source src="filename.mp4">
      <source src="filename.webm">
      <source src="filename.ogg">
    </video>

The video has been encoded twice, once in Theora and once in H264, to cater for different browsers; [Kroc Camen's Video for Everybody](http://camendesign.com/code/video_for_everybody) explains the reasons behind this (and how to make a bulletproof player). **Update:** added [WebM](http://www.webmproject.org/) support.

Having marked up a few controls with HTML (I've used `id` attributes on all of them to make this demo easier), the next step is to write the JavaScript to access the API ([which is well explained in this article at the Mozilla Developer Center](https://developer.mozilla.org/En/NsIDOMHTMLMediaElement)) for the controls.

The first and most important control is the play/pause button; for this I've written a function which checks so see if the `paused` attribute is true or false, and triggers the `play()` or `pause()` methods accordingly:
    
    
    play.addEventListener('click',playControl,false);
    function playControl() {
        if (video.paused == false) {
            video.pause();
            this.firstChild.nodeValue = 'Play';
            pauseCount();
        } else {
            video.play();
            this.firstChild.nodeValue = 'Pause';
            startCount();
        }
    }

You'll notice that it also updates the control text to indicate the action that the control will perform. There are also two function calls - `pauseCount()` and `startCount()` - which control the timer shown next to the play button.

The timer uses the `currentTime` and `duration` attributes (although the latter doesn't seem to be currently supported by Chrome). To get the current time I've used `setInterval` to create a loop:
    
    
    function startCount() {
        t = window.setInterval(function() {
            if (video.ended != true) {
                timer.firstChild.nodeValue = Math.round(video.currentTime + 1);
            } else {
                play.firstChild.nodeValue = 'Play';
                window.clearInterval(t);
            }
        },1000);		
    }

First it uses an `if...else` statement on the `ended` attribute to check that the video has not finished playing; if it hasn't, it updates the timer with `currentTime` (plus a little maths). If the video HAS finished, it uses `clearInterval` to stop the loop; this is also used in a function to pause the timer if the pause control is used:
    
    
    function pauseCount() {
        window.clearInterval(t);
    }

To complete the controls we have functions to increase and decrease the volume. Both are very similar:
    
    
    vUp.addEventListener('click',volUp,false);
    function volUp() {
        if (video.volume  1) {
            video.volume = Math.round((video.volume + 0.1)*10)/10;
            volume.firstChild.nodeValue = Math.round(video.volume*10);
        }
    }

First they check that the minimum/maximum limits have not been reached, and increase/decrease the `volume` attribute if not. Volume is on a scale of 0 to 1, and this function changes that value in increments of 0.1. The on-screen volume counter is also changed accordingly.

There are a number of small details elsewhere in the script, so feel free to have a dig through to see what else I've done; [here's another link to the finished demo](https://www.broken-links.com/tests/video/).

## Further steps

I've obviously used a little CSS to tidy the controls up, but a lot more could be done; using images instead of text, for example, or perhaps using something like [jQuery's user interface library](http://jqueryui.com/) to make more dynamic controls.

This article was intended only to show how easy it is to get started; what will be exciting is to see how these techniques can be expanded upon.

**Update:** If you found this article useful, you may be interested to know that I returned to this subject in a later post, [Building a better HTML5 video player with Glow](https://www.broken-links.com/2010/04/14/building-a-better-html5-video-player-with-glow/).
