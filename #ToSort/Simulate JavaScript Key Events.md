# Simulate JavaScript Key Events

_Captured: 2016-03-08 at 10:29 from [stackoverflow.com](http://stackoverflow.com/questions/596481/simulate-javascript-key-events)_

What you can do is programmatically trigger _keyevent listeners_ by firing _keyevents_. It makes sense to allow this from a sandboxed security-perspective. Using this ability, you can then apply a typical [observer-pattern](http://en.wikipedia.org/wiki/Observer_pattern). You could call this method "simulating".

Below is an example of how to accomplish this in the W3C DOM standard along with jQuery:
    
    
    function triggerClick(){varevent=newMouseEvent('click',{'view': window,'bubbles':true,'cancelable':true});var cb = document.querySelector('input[type=submit][name=btnK]');var canceled =!cb.dispatchEvent(event);if(canceled){// preventDefault was called and the event cancelled}else{// insert your event-logic here...}}

This example is adapted from: <https://developer.mozilla.org/en-US/docs/Web/Guide/Events/Creating_and_triggering_events>

In jQuery:
    
    
    jQuery('input[type=submit][name=btnK]').trigger({
        type:'keypress',
        which: character.charCodeAt(0/*the key to trigger*/)});

**But as of recently, there is no [DOM] way to actually trigger keyevents leaving the browser-sandbox.** And all major browser vendors will adhere to that security concept.

As for plugins such as Adobe Flash - which are based on the NPAPI-, and permit bypassing the sandbox: these are [phasing-out](http://blog.chromium.org/2013/09/saying-goodbye-to-our-old-friend-npapi.html) ; [Firefox](http://blog.mozilla.org/futurereleases/2013/09/24/plugin-activation-in-firefox/).

**Detailed Explanation:**

You cannot and you must not for security reasons (as Pekka already pointed out). You will always require a user interaction in between. Additionally imagine the chance of the browser vendors getting sued by users, as various programmatic keyboard events will have led to spoofing attacks.

See this [post](http://goo.gl/ghyhA0) for alternatives and more details. There is always the flash based copy-and-paste. Here is an elegant [example](http://www.colorzilla.com/gradient-editor/). At the same time it is a testimony why the web is moving away from plugin vendors.

There is a similar security mindset applied in case of the [opt-in CORS policy](http://goo.gl/JiYNEE) to access remote content programmatically.

The answer is:  
**There is no way to programmatically trigger input keys in the sandboxed browser environment under normal circumstances**.

**Bottomline:** I am not saying it will not be possible in the future, under special browser-modes and/or privileges towards the end-goal of gaming, or similar user-experiences. However prior to entering such modes, the user will be asked for permissions and risks, similar to the [Fullscreen API model](https://www.google.at/search?client=opera&q=w3c%20fullscreen%20api%20permission).

**Useful:** In the context of KeyCodes, [this](http://www.lsauer.com/2011/08/javascript-keymap-keycodes-in-json.html) tool and keycode mapping will come in handy.

_Disclosure:_ The answer is based on the answer [here](http://stackoverflow.com/questions/8668192/programmatically-triggering-ctrls/19882728#19882728).
