# 10 Useful jQuery iPad Code Snippets and Plugins 

_Captured: 2015-06-09 at 21:21 from [www.sitepoint.com](http://www.sitepoint.com/10-jquery-ipad-code-snippets-plugins/)_

**We have put together some of the easy to use tricks, code snippets and plugins all for the iPad device**. Be sure to let us know in the comments which snippets and plugins you found useful and of any others that you know of that can be useful.

## 1\. Detecting iPad Orientation in Safari using JavaScript

Style your website or re-order your content to match exactly your iPad's orientation. Here's an example on how to detect the current orientation of the iPad device either by pressing a button or when the orientation changes, using an event called onOrientationChange…

123456789
`<button onclick=``"detectIPadOrientation();"``>What's my Orientation?</button>``<script type=``"text/javascript"``>``window.onorientationchange = detectIPadOrientation;``function` `detectIPadOrientation () {``if` `( orientation == 0 ) {``alert (``'Portrait Mode, Home Button bottom'``);``}``else` `if` `( orientation == 90 ) {``alert (``'Landscape Mode, Home Button right'``);``}``else` `if` `( orientation == -90 ) {``alert (``'Landscape Mode, Home Button left'``);``}``else` `if` `( orientation == 180 ) {``alert (``'Portrait Mode, Home Button top'``);``}``}``</script>`

Using the media definition, you can also use CSS Stylesheets:

12
`<link rel=``"stylesheet"` `media=``"all and (orientation:portrait)"` `href=``"portrait.css"``/>``<link rel=``"stylesheet"` `media=``"all and (orientation:landscape)"` `href=``"landscape.css"``/>`

## 2\. jQuery Add Drag/Touch Support for iPad

jQuery code snippet to apply Drag/Touch Support for the iPad and devices with touch support.

23456
`//iPAD Support``$.fn.addTouch = ``function``(){``this.each(``function``(i,el){``$(el).bind(``'touchstart touchmove touchend touchcancel'``,``function``(){``//we pass the original event object because the jQuery event``//object is normalized to w3c specs and does not provide the TouchList``handleTouch(event);``});``});``var` `handleTouch = ``function``(event)``{``var` `touches = event.changedTouches,``first = touches[0],``type = ``''``;``switch``(event.type)``{``case` `'touchstart'``:``type = ``'mousedown'``;``break``;``case` `'touchmove'``:``type = ``'mousemove'``;``event.preventDefault();``break``;``case` `'touchend'``:``type = ``'mouseup'``;``break``;``default``:``return``;``}``var` `simulatedEvent = document.createEvent(``'MouseEvent'``);``simulatedEvent.initMouseEvent(type, true, true, window, 1, first.screenX, first.screenY, first.clientX, first.clientY, false, false, false, false, 0``/*left*/``, null);``first.target.dispatchEvent(simulatedEvent);``};``};`

## 3\. TouchSwipe jQuery plugin for iPad, iPhone and Android

A jquery plugin to be used with jQuery on touch input devices such as iPad, iPhone etc.

![TouchSwipe](http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/jquery4u/2012/09/TouchSwipe.jpg)

[Source](http://labs.skinkers.com/touchSwipe/)[Demo](http://labs.skinkers.com/touchSwipe/demo/1_Basic_swipe.php)

## 4\. jQuery iPad one finger scroll

Touch devices (iPad, iPhone, Android etc) have quite weird behavour for scrolling overflow:auto elements. iPad requires two finger scrolling and dosen't add any scrollbars to make it obvious. This plugin allows you to scroll an overflow:auto element with one finger.

![jQuery iPad one finger scroll](http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/jquery4u/2012/09/iPad-on-One-Finger-Scroll.jpg)

> _[jQuery iPad one finger scroll](http://forrst.com/posts/jQuery_iPad_one_finger_scroll-B30)_

[Source](http://forrst.com/posts/jQuery_iPad_one_finger_scroll-B30)[Demo](http://jsfiddle.net/mfXMn/)

## 5\. jQuery Detect Mobile Devices - iPhone iPod iPad

jQuery code snippet to detect if a user is viewing the website using a mobile device, specifically an iPhone iPod or iPad.

`jQuery(document).ready(``function``($){``var` `deviceAgent = navigator.userAgent.toLowerCase();``var` `agentID = deviceAgent.match(/(iphone|ipod|ipad)/);``if` `(agentID) {``// mobile code here``}``});`

## 6\. Multiselect picklist jquery plugin for iPad and Desktop browsers

A multi-row/multiselect picklist that looks similar in both desktop and iPad browser.

We could have easily used the usual Visualforce tag i.e. for the purpose, like this:

`<apex:selectlist id=``"contactPickList"` `value=``"{!selectedContactIds}"` `multiselect=``"true"` `size=``"4"``>``<apex:selectoptions value=``"{!contactOptions}"``></apex:selectoptions>``</apex:selectlist>`

## 7\. JQUERY CLICK EVENTS ON THE IPAD

A solution to fix it. This was the advice given in the developer docs at apple.com. This basically searches for iPad in the userAgent string (case insensitive). If the user is on an iPad we use touchstart and if not we default back to a standard click.

The code you need is:

`var` `ua = navigator.userAgent, ``event = (ua.match(/iPad/i)) ? ``"touchstart"` `: ``"click"``;``$(``"#theElement"``).bind(event, ``function``() {``// jquery code``}`

## 8\. Easy iPad Gestures in your website with jQuery

jQuery makes this so easy to integrate and use that I couldn't help but fool around with it.

First off all make sure you have the latest jQuery library included in your site. Include it directly from the site like this:

Second step, download the TouchWipe library from the author website OR you can just bind the Touchwipe to the .  
Include the touchwipe library before the tag. ex:

1
`<script type=``"text/javascript"` `src=``"jquery.touchwipe.1.1.1.js"``></script>`

Then initialise TouchWipe on to the body tag, and give the gestures the chosen action to perform, for this example I just used alerts:

`$(document).ready(``function``(){``$(``'body'``).touchwipe({``wipeLeft: ``function``(){ alert(``'You swiped left!'``) },``wipeRight: ``function``(){ alert(``'You swiped right!'``) },``wipeUp: ``function``(){ alert(``'You swiped up!'``) },``wipeDown: ``function``(){ alert(``'You swiped down!'``) }``})``})`

Touchwipe can be added to a specific div as well rather than the body tag. And there ya go. You could add that to any html page to add swipe Gestures.  
[Source](http://www.janes.co.za/easy-ipad-gestures-in-your-website-with-jquery/#.UEKoPcHiY0V)

## 9\. IPHONE/IPAD DOUBLETAP EVENT HANDLER

Enable the use of "doubletap" events on iPhone and iPad devices. The functionality is still available when the plugin is used on Desktop Browser. This means that you don't have to worry about the environment where the plugin is used.

![IPHONE/IPAD DOUBLETAP EVENT HANDLER](http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/jquery4u/2012/09/iPhone-iPad-DoubleTap.jpg)

> _[IPHONE/IPAD DOUBLETAP EVENT HANDLER](http://appcropolis.com/implementing-doubletap-on-iphones-and-ipads/)_

[Source](http://appcropolis.com/implementing-doubletap-on-iphones-and-ipads/)[Demo](http://sanraul.com/lab/jquery.doubletap/)

## 10\. jQuery.UI.iPad plugin

Provides an interface layer to map touch events to jQuery UI interface elements.

`$(``function``() {``//``// Extend jQuery feature detection``//``$.extend($.support, {``touch: typeof Touch == ``"object"``});``//``// Hook up touch events``//``if` `($.support.touch) {``document.addEventListener(``"touchstart"``, iPadTouchHandler, false);``document.addEventListener(``"touchmove"``, iPadTouchHandler, false);``document.addEventListener(``"touchend"``, iPadTouchHandler, false);``document.addEventListener(``"touchcancel"``, iPadTouchHandler, false);``}``});``var` `lastTap = null;      ``// Holds last tapped element (so we can compare for double tap)``var` `tapValid = false;      ``// Are we still in the .6 second window where a double tap can occur``var` `tapTimeout = null;      ``// The timeout reference``function` `cancelTap() {``tapValid = false;``}``var` `rightClickPending = false;  ``// Is a right click still feasible``var` `rightClickEvent = null;    ``// the original event``var` `holdTimeout = null;      ``// timeout reference``var` `cancelMouseUp = false;    ``// prevents a click from occuring as we want the context menu``function` `cancelHold() {``if` `(rightClickPending) {``window.clearTimeout(holdTimeout);``rightClickPending = false;``rightClickEvent = null;``}``}``function` `startHold(event) {``if` `(rightClickPending)``return``;``rightClickPending = true; ``// We could be performing a right click``rightClickEvent = (event.changedTouches)[0];``holdTimeout = window.setTimeout(``"doRightClick();"``, 800);``}``function` `doRightClick() {``rightClickPending = false;``//``// We need to mouse up (as we were down)``//``var` `first = rightClickEvent,``simulatedEvent = document.createEvent(``"MouseEvent"``);``simulatedEvent.initMouseEvent(``"mouseup"``, true, true, window, 1, first.screenX, first.screenY, first.clientX, first.clientY,``false, false, false, false, 0, null);``first.target.dispatchEvent(simulatedEvent);``//``// emulate a right click``//``simulatedEvent = document.createEvent(``"MouseEvent"``);``simulatedEvent.initMouseEvent(``"mousedown"``, true, true, window, 1, first.screenX, first.screenY, first.clientX, first.clientY,``false, false, false, false, 2, null);``first.target.dispatchEvent(simulatedEvent);``//``// Show a context menu``//``simulatedEvent = document.createEvent(``"MouseEvent"``);``simulatedEvent.initMouseEvent(``"contextmenu"``, true, true, window, 1, first.screenX + 50, first.screenY + 5, first.clientX + 50, first.clientY + 5,``false, false, false, false, 2, null);``first.target.dispatchEvent(simulatedEvent);``//``// Note:: I don't mouse up the right click here however feel free to add if required``//``cancelMouseUp = true;``rightClickEvent = null; ``// Release memory``}``//``// mouse over event then mouse down``//``function` `iPadTouchStart(event) {``var` `touches = event.changedTouches,``first = touches[0],``type = ``"mouseover"``,``simulatedEvent = document.createEvent(``"MouseEvent"``);``//``// Mouse over first - I have live events attached on mouse over``//``simulatedEvent.initMouseEvent(type, true, true, window, 1, first.screenX, first.screenY, first.clientX, first.clientY,``false, false, false, false, 0, null);``first.target.dispatchEvent(simulatedEvent);``type = ``"mousedown"``;``simulatedEvent = document.createEvent(``"MouseEvent"``);``simulatedEvent.initMouseEvent(type, true, true, window, 1, first.screenX, first.screenY, first.clientX, first.clientY,``false, false, false, false, 0, null);``first.target.dispatchEvent(simulatedEvent);``if` `(!tapValid) {``lastTap = first.target;``tapValid = true;``tapTimeout = window.setTimeout(``"cancelTap();"``, 600);``startHold(event);``}``else` `{``window.clearTimeout(tapTimeout);``//``// If a double tap is still a possibility and the elements are the same``//  Then perform a double click``//``if` `(first.target == lastTap) {``lastTap = null;``tapValid = false;``type = ``"click"``;``simulatedEvent = document.createEvent(``"MouseEvent"``);``simulatedEvent.initMouseEvent(type, true, true, window, 1, first.screenX, first.screenY, first.clientX, first.clientY,``false, false, false, false, 0``/*left*/``, null);``first.target.dispatchEvent(simulatedEvent);``type = ``"dblclick"``;``simulatedEvent = document.createEvent(``"MouseEvent"``);``simulatedEvent.initMouseEvent(type, true, true, window, 1, first.screenX, first.screenY, first.clientX, first.clientY,``false, false, false, false, 0``/*left*/``, null);``first.target.dispatchEvent(simulatedEvent);``}``else` `{``lastTap = first.target;``tapValid = true;``tapTimeout = window.setTimeout(``"cancelTap();"``, 600);``startHold(event);``}``}``}``function` `iPadTouchHandler(event) {``var` `type = ``""``,``button = 0; ``/*left*/``if` `(event.touches.length > 1)``return``;``switch` `(event.type) {``case` `"touchstart"``:``if` `($(event.changedTouches[0].target).is(``"select"``)) {``return``;``}``iPadTouchStart(event); ``/*We need to trigger two events here to support one touch drag and drop*/``event.preventDefault();``return` `false;``break``;``case` `"touchmove"``:``cancelHold();``type = ``"mousemove"``;``event.preventDefault();``break``;``case` `"touchend"``:``if` `(cancelMouseUp) {``cancelMouseUp = false;``event.preventDefault();``return` `false;``}``cancelHold();``type = ``"mouseup"``;``break``;``default``:``return``;``}``var` `touches = event.changedTouches,``first = touches[0],``simulatedEvent = document.createEvent(``"MouseEvent"``);``simulatedEvent.initMouseEvent(type, true, true, window, 1, first.screenX, first.screenY, first.clientX, first.clientY,``false, false, false, false, button, null);``first.target.dispatchEvent(simulatedEvent);``if` `(type == ``"mouseup"` `&amp;&amp; tapValid &amp;&amp; first.target == lastTap) {  ``// This actually emulates the ipads default behaviour (which we prevented)``simulatedEvent = document.createEvent(``"MouseEvent"``);    ``// This check avoids click being emulated on a double tap``simulatedEvent.initMouseEvent(``"click"``, true, true, window, 1, first.screenX, first.screenY, first.clientX, first.clientY,``false, false, false, false, button, null);``first.target.dispatchEvent(simulatedEvent);``}``}`
