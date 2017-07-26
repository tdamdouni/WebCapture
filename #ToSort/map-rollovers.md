# Map Rollovers

_Captured: 2017-01-26 at 21:31 from [mediatemple.net](http://mediatemple.net/blog/tips/map-rollovers/)_

Let's say you have a map of the world and you want to be able to highlight the country (or state, or county, etc.) as the cursor hovers over it or it is tapped.

Doable!

First, the map should probably be vector. SVG is almost certainly the right image format choice here. It will give us a crisp looking map at likely a reasonable size, and most importantly, give us the interactivity and easy styling we need.

Let's use a state map of the United States as an example. [Wikipedia has a perfect one](https://commons.wikimedia.org/wiki/File:Blank_US_Map_\(states_only\).svg) for us to use.

![Blank_US_Map_\(states_only\).svg.png](https://draftin.com/images/49560?token=MDHkPDEApgJWNqnG3NY6M6wipSUmsCCS2plc_0rmUxlsqLXLICsTMhxt3IuidnPhTzWzftWYym0ZyZPPo1U_XE0)

Let's download that SVG and take a peek at the code:

![Screen Shot 2017-01-15 at 10.38.03 AM.png](https://draftin.com/images/49561?token=jH6hF54RC7v57vPUR_ubelZhcpVpOgEovC6uIEoLdAnd2TdKFWo7EHAyOBv8eEFZUq5j2CzshCU9khYb0l7S710)

There's some pretty well-formatted SVG here, with each state represented by a `<path>` with a unique ID.

The [simplest possible](http://codepen.io/chriscoyier/pen/849c4409d27f660c67f2d86cf2f94592) map hovers would involve just dumping this SVG into the HTML, and adding a `:hover` to the CSS like:
    
    
    path:hover {
      fill: red;
    }
    

![Screen Shot 2017-01-15 at 10.40.04 AM.png](https://draftin.com/images/49562?token=6rA--dHb7FQLmkuOEjGSvuAEdKzd_XZPd0L59IQ2FafVegBKoGgzDiteijYYIcolb8IgFKwV283PKQjLdLWsAG8)

But let's take this to the next level.

## Two-way hovers

By which I mean: you can hover over the _state_, or, you can hover over the _name of the state_ in a list and you'll see it highlighted.

Say we have a list of states like this:
    
    
    <ul class="list-of-states">
      <li>Alabama</li>
      <li>Alaska</li>
      <li>Arizona</li>
      <li>Arkansas</li>
      ...
    

In the SVG we got from Wikipedia, the paths were like:
    
    
    <path id="AK" fill="#D3D3D3" d="..." />
    

Unfortunately, there isn't a simple, currently existing way to connect those elements programmatically. I created that connection by hand, using a `data-*` attribute for each state in the list:
    
    
    <ul class="list-of-states">
      <li data-state="AL">Alabama</li>
      <li data-state="AK">Alaska</li>
      <li data-state="AZ">Arizona</li>
      <li data-state="AR">Arkansas</li>
    

Now we have what we need.

Let's attach an event handler both from when the list items are _hovered onto_ and _hovered off_. When those things happen, through the data attribute we'll figure out which SVG state is relevant, then add classes to both.
    
    
    var wordStates = document.querySelectorAll(".list-of-states li");
    
    wordStates.forEach(function(el) {
    
      el.addEventListener("mouseenter", function() {
        var stateCode = el.getAttribute("data-state");
        var svgState = document.querySelector("#" + stateCode);
        el.classList.add("on");
        svgState.classList.add("on");
      });
    
      el.addEventListener("mouseleave", function() {
        var stateCode = el.getAttribute("data-state");
        var svgState = document.querySelector("#" + stateCode);
        el.classList.remove("on");
        svgState.classList.remove("on");
      });
    
    });
    

Now we can use that class name to style each and every thing to our very wish.
    
    
    .list-of-states li.on {
      background: red;
      color: white;
      font-weight: bold;
    }
    path.on {
      fill: red;
    }
    

![state-rollovers.gif](https://draftin.com/images/49613?token=WQzdsoFyxlf3bdYoeDOe_YDDGSRxrbXwc5afbqnzlFND8c_Zj1MHwf40PMeboKIw5SXr-85BZ_J-J1msitGLYo0)

We can do the exact reverse thing for the state paths too, so that the state in the list highlights when we hover over the map:
    
    
    var svgStates = document.querySelectorAll("#states > *");
    
    svgStates.forEach(function(el) {
    
      el.addEventListener("mouseenter", function() {
        var stateId = el.getAttribute("id");
        var wordState = document.querySelector("[data-state='" + stateId + "']");
        el.classList.add("on");
        wordState.classList.add("on");
      });
    
      el.addEventListener("mouseleave", function() {
        var stateId = el.getAttribute("id");
        var wordState = document.querySelector("[data-state='" + stateId + "']");
        el.classList.remove("on");
        wordState.classList.remove("on");
      });
    
    });
    

## DRYing up

Unfortunately, that's a lot of repetitive code. So let's clean it up. We can abstract the functionality into:

  * Adding the "on" state (from hovering the map)
  * Adding the "on" state (from hovering the list)
  * Removing all "on" states

We can make those into functions which we can call as needed:
    
    
    var wordStates = document.querySelectorAll(".list-of-states li");
    var svgStates = document.querySelectorAll("#states > *");
    
    function removeAllOn() {
      wordStates.forEach(function(el) {
        el.classList.remove("on");
      });
      svgStates.forEach(function(el) {
        el.classList.remove("on");
      });
    }
    
    function addOnFromState(el) {
      var stateCode = el.getAttribute("data-state");
      var svgState = document.querySelector("#" + stateCode);
      el.classList.add("on");
      svgState.classList.add("on");
    }
    
    function addOnFromList(el) {
      var stateId = el.getAttribute("id");
      var wordState = document.querySelector("[data-state='" + stateId + "']");
      el.classList.add("on");
      wordState.classList.add("on");
    }
    
    wordStates.forEach(function(el) {
      el.addEventListener("mouseenter", function() {
        addOnFromState(el);
      });
      el.addEventListener("mouseleave", function() {
         removeAllOn();
      });
    });
    
    svgStates.forEach(function(el) {
      el.addEventListener("mouseenter", function() {
        addOnFromList(el);
      });
      el.addEventListener("mouseleave", function() {
         removeAllOn();
      });
    });
    

![all-hover.gif](https://draftin.com/images/49614?token=9morkB-LilekwLGvjVu5NCCaK4ov4mUNx2cgazYBkR9YZ9MTX5EoQ3mUPHor-sDeGSdGErnKP8bFdIFXdDVMMvk)

## Mobile support

Have you heard? There isn't a single cursor on (most) touch screens.

We can easily make it work with taps though, which was part of the reason for DRYing out. In addition to binding to `mouseenter` and `mouseleave`, we also do `touchstart` (`click` would work too).
    
    
    wordStates.forEach(function(el) {
      // other vents
    
      el.addEventListener("touchstart", function() {
        removeAllOn();
        addOnFromList(el);
      });
    });
    
    svgStates.forEach(function(el) {
      // other events
    
      el.addEventListener("touchstart", function() {
        removeAllOn();
        addOnFromState(el);
      });
    });
    

## Demo

See the Pen [Hoving States](http://codepen.io/chriscoyier/pen/WRwxYO/) by Chris Coyier ([@chriscoyier](http://codepen.io/chriscoyier)) on [CodePen](http://codepen.io).

![](http://s2.mt-cdn.net/blog/wp-content/uploads/2016/01/me3-380x380.jpg)
