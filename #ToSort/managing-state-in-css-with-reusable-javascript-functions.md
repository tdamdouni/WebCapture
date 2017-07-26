# Managing State in CSS with Reusable JavaScript Functions

_Captured: 2017-05-09 at 20:37 from [css-tricks.com](https://css-tricks.com/managing-state-css-reusable-javascript-functions/)_

Determining the most efficient way of managing state can be a challenging issue in CSS, but thankfully there are many OOCSS-based methodologies out there which provide some good solutions. My preferred comes from [SMACSS (Scalable and modular architecture for CSS)](https://smacss.com/) and involves stateful classes. To quote SMACSS's [own documentation](https://smacss.com/book/type-state), stateful classes are:

> A state is something that augments and overrides all other styles. For example, an accordion section may be in a collapsed or expanded state. A message may be in a success or error state.
> 
> States are generally applied to the same element as a layout rule or applied to the same element as a base module class.

One of my most-used stateful classes is `is-active`. Taking the accordion example from the prior quote, `is-active` in this instance would apply all the required CSS styles to represent an expanded state. As seen in the example below:

See the Pen [#1) Accordion Component w Stateful Class](https://codepen.io/lukedidit/pen/mmJRQP/) by Luke Harrison ([@lukedidit](http://codepen.io/lukedidit)) on [CodePen](http://codepen.io).

You will notice there's some JavaScript which toggles the `is-active` class on the component when a click event is detected:
    
    
    var accordion = document.querySelectorAll(".c-accordion");
    
    for(var i = 0; i < accordion.length; i++) {
        var accordionHeader = accordion[i].querySelector(".c-accordion__header"),
        accordionCurrent = accordion[i];
    
        accordionHeader.addEventListener("click", function(){
            accordionCurrent.classList.toggle("is-active");
        });
    }

Whilst valid JavaScript, this would have to be repeated again and again for any other components which leverage the `is-active` stateful class via a click event, leading to many duplicates of what is essentially the same code snippet.

Not very efficient and certainly not very DRY.

A better approach would be instead to write a single function which performs the same task and can be reused over and over again with different components. Let's do that.

### Creating a simple reusable function

Let's start off by building a simple function which accepts an element as a parameter and toggles `is-active`:
    
    
    var makeActive = function(elem){
        elem.classList.toggle("is-active");
    }

This works fine, but if we slot it into our accordion JavaScript there's a problem:
    
    
    var accordion = document.querySelectorAll(".c-accordion"),
    makeActive = function(elem){
        elem.classList.toggle("is-active");
    }
    
    for(var i = 0; i < accordion.length; i++) {
        var accordionHeader = accordion[i].querySelector(".c-accordion__header"),
        accordionCurrent = accordion[i];
    
        accordionHeader.addEventListener("click", function(){
            makeActive(accordionCurrent);
        });
    }

Although the `makeActive` function is reusable, we still need to first write code to grab our component and any of its inner elements, so there's certainly lots of room for improvement.

To make these improvements, we can leverage [HTML5 custom data attributes](http://html5doctor.com/html5-custom-data-attributes/):
    
    
    <div class="c-accordion js-accordion">
        <div class="c-accordion__header" data-active="js-accordion">My Accordion Component</div>
        <div class="c-accordion__content-wrapper">
            <div class="c-accordion__content">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce laoreet ultricies risus, sit amet congue nulla mollis et. Suspendisse bibendum eros sed sem facilisis ornare. Donec sit amet erat vel dui semper pretium facilisis eget nisi. Fusce consectetur vehicula libero vitae faucibus. Nullam sed orci leo. Fusce dapibus est velit, at maximus turpis iaculis in. Pellentesque ultricies ultrices nisl, eu consequat est molestie sit amet. Phasellus laoreet magna felis, ut vulputate justo tempor eu. Nam commodo aliquam vulputate.
            </div>
        </div>
    </div>

A `data-active` attribute has been added to the element which previously triggered the `is-active` toggle when clicked. This attribute's value represents the element where the `is-active` toggle should take place, which as before is the top-level `c-accordion` element. Note the addition of a new `js-accordion` class rather than hooking into the existing `c-accordion` class. This is to decouple functional aspects of the component from it's styling.

Let's take a look at the JavaScript:
    
    
    // Grab all elements with data-active attribute
    var elems = document.querySelectorAll("[data-active]");
    
    // Loop through if any are found
    for(var i = 0; i < elems.length; i++){
        // Add event listeners to each one
        elems[i].addEventListener("click", function(e){
    
            // Prevent default action of element
            e.preventDefault();
    
            // Grab linked elements
            var linkedElement = document.querySelectorAll("." + this.getAttribute("data-active"));
    
            // Toggle linked element if present
            for(var i = 0; i < linkedElement.length; i++) {
                linkedElement[i].classList.toggle("is-active");
            }
    
        });    
    }

This has certainly improved things as we no longer have to write code to grab any elements, just attach a data-active attribute to our trigger element and specify a target element. As it stands, this function can be used for any other component where a click-based `is-active` class is required without any additional coding. Full example below:

See the Pen [#2) Accordion Component w reusable is-active function](https://codepen.io/lukedidit/pen/zwGdqV/) by Luke Harrison ([@lukedidit](http://codepen.io/lukedidit)) on [CodePen](http://codepen.io).

### Improving our reusable function

This reusable function works, but when scaled, we have to take care to make sure trigger and target element classes don't conflict with one another. In the example below, clicking one accordion would trigger `is-active` on all of them.
    
    
    <div class="c-accordion js-accordion">
        <div class="c-accordion__header" data-active="js-accordion">First Accordion</div>
        [...]
    </div>
    
    <div class="c-accordion js-accordion">
        <div class="c-accordion__header" data-active="js-accordion">Second Accordion</div>
        [...]
    </div>
    
    <div class="c-accordion js-accordion">
        <div class="c-accordion__header" data-active="js-accordion">Third Accordion</div>
        [...]
    </div>

Adding number suffixes to each `js-accordion` reference does solve the problem, but it's a hassle which we can do without. A good solution would be to instead implement scoping to our reusable function which would enable us to encapsulate our toggles so they only effect the elements we want.

To implement scoping, we'll need to create a separate custom attribute called `data-active-scope`. Its value should represent the parent element which the toggle should be encapsulated within, which in this instance is the parent `js-accordion` element.
    
    
    <div class="c-accordion js-accordion">
        <div class="c-accordion__header" data-active="js-accordion" data-active-scope="js-accordion">First Accordion</div>
        [...]
    </div>
    
    <div class="c-accordion js-accordion">
        <div class="c-accordion__header" data-active="js-accordion">Second Accordion</div>
        [...]
    </div>

Using the above HTML, the following behaviour should happen:

  1. When you click the first accordion, because it has a scope set to `js-accordion`, only `data-active` elements which match or are children of this `js-accordion` instance will have `is-active` toggled.
  2. When you click the second accordion, which doesn't have a scope, `is-active` would be toggled on all instances of `js-accordion`.

Provided `data-active-scope` is correctly set, any class toggles within each `js-accordion` element should be encapsulated regardless of any conflicting classnames.

Here's the modified Javascript and a working example showing accordions with and without a `data-active-scope` attribute:
    
    
    // Grab all elements with data-active attribute
    var elems = document.querySelectorAll("[data-active]"),
    // closestParent helper function
    closestParent = function(child, match) {
        if (!child || child == document) {
            return null;
        }
        if (child.classList.contains(match) || child.nodeName.toLowerCase() == match) {
            return child;
        }
        else {
            return closestParent(child.parentNode, match);
        }
    }
    
    // Loop through if any are found
    for(var i = 0; i < elems.length; i++){
        // Add event listeners to each one
        elems[i].addEventListener("click", function(e){
    
            // Prevent default action of element
            e.preventDefault();
    
            // Grab scope if defined
            if(this.getAttribute("data-active-scope")) {
                var scopeElement = closestParent(this, this.getAttribute("data-active-scope"));
            }
    
            if(scopeElement) {
                // Grab scoped linked element
                var linkedElement = scopeElement.querySelectorAll("." + this.getAttribute("data-active"));
                // Convert to array
                linkedElement = Array.prototype.slice.call(linkedElement);
                // Check if our scope matches our target element and add to array if true.
                // This is to make sure everything works when data-active matches data-active-scope.
                if(scopeElement.classList.contains(this.getAttribute("data-active"))) {
                    linkedElement.unshift(scopeElement);
                }
            }
            else {
                // Grab linked element
                var linkedElement = document.querySelectorAll("." + this.getAttribute("data-active"));
            }
    
            // Toggle linked element if present
            for(var i = 0; i < linkedElement.length; i++) {
                linkedElement[i].classList.toggle("is-active");
            }
    
        });    
    }

See the Pen [#3) Accordion Component w Improved reusable is-active function](http://codepen.io/lukedidit/pen/YVXEMy/) by Luke Harrison ([@lukedidit](http://codepen.io/lukedidit)) on [CodePen](http://codepen.io).

### Moving beyond is-active

Our reusable function is now working nicely and is an efficient way of setting up `is-active` toggles on all kinds of components. However what if we need to set up a similar toggle for another stateful class? As it stands we would have to duplicate the function and change all references of `is-active` to the new stateful class. Not very efficient.

We should improve our reusable function to accept any class by refactoring our data-attributes. Instead of attaching the `data-active` attribute to our trigger element, let's replace it with the following:

  * `data-class` \- The class we wish to add.
  * `data-class-element` \- The element we wish to add the class to.
  * `data-class-scope` \- The scope attribute performs the same function, but has been renamed for consistency.

This requires a few minor tweaks to our JavaScript:
    
    
    // Grab all elements with data-active attribute
    var elems = document.querySelectorAll("[data-class][data-class-element]");
    
    // closestParent helper function
    closestParent = function(child, match) {
        if (!child || child == document) {
            return null;
        }
        if (child.classList.contains(match) || child.nodeName.toLowerCase() == match) {
            return child;
        }
        else {
            return closestParent(child.parentNode, match);
        }
    }
    
    // Loop through if any are found
    for(var i = 0; i < elems.length; i++){
        // Add event listeners to each one
        elems[i].addEventListener("click", function(e){
    
            // Prevent default action of element
            e.preventDefault();
    
            // Grab scope if defined
            if(this.getAttribute("data-class-scope")) {
                var scopeElement = closestParent(this, this.getAttribute("data-class-scope"));
            }
    
            if(scopeElement) {
                // Grab scoped linked element
                var linkedElement = scopeElement.querySelectorAll("." + this.getAttribute("data-class-element"));
                // Convert to array
                linkedElement = Array.prototype.slice.call(linkedElement);
                // Check if our scope matches our target element and add to array if true.
                // This is to make sure everything works when data-active matches data-active-scope.
                if(scopeElement.classList.contains(this.getAttribute("data-class-element"))) {
                    linkedElement.unshift(scopeElement);
                }
            }
            else {
                // Grab linked element
                var linkedElement = document.querySelectorAll("." + this.getAttribute("data-class-element"));
            }
    
            // Toggle linked element if present
            for(var i = 0; i < linkedElement.length; i++) {
                linkedElement[i].classList.toggle(this.getAttribute("data-class"));
            }           
    
        });    
    }

It would be set up in the HTML like so:
    
    
    <button class="c-button" data-class="is-loading" data-class-element="js-form-area">Submit</button>

In the example below, clicking the `c-button` component toggles the `is-loading` class on the `js-form-area` component:

See the Pen [#4) Form Component w Improved reusable any class function](http://codepen.io/lukedidit/pen/oWXowO/) by Luke Harrison ([@lukedidit](http://codepen.io/lukedidit)) on [CodePen](http://codepen.io).

### Handling multiple toggles

So we have a reusable function which toggles any class on any element. These click events can be set up without having to write any additional JavaScript through the use of custom data attributes. However, there's still ways to make this reusable function even more useful.

Coming back to our previous example of the login form component, what if when the `c-button` element is clicked, in addition to it toggling `is-loading` on `js-form-area`, we also want to toggle `is-disabled` on all instances of `c-input`? At the moment this isn't possible as our custom attributes only accept a single value each.

Let's modify our function, so instead of each custom data attribute only accepting a single value, it accepts a comma separated list of values - with each item value in `data-class` linking with the value of a matching index in `data-class-element` and `data-class-scope`.

Like so:
    
    
    <button class="c-button" data-class="is-loading, is-disabled" data-class-element="js-form-area, js-input" data-class-scope="false, js-form-area">Submit</button>

Assuming the above is used, the following would happen once `c-button` is clicked:

  1. `is-loading` would be toggled on `js-form-area`.
  2. `is-disabled` would be toggled on `js-input` and be scoped within the parent `js-form-area` element.

This requires more changes to our JavaScript:
    
    
    // Grab all elements with data-active attribute
    var elems = document.querySelectorAll("[data-class][data-class-element]");
    
    // closestParent helper function
    closestParent = function(child, match) {
        if (!child || child == document) {
            return null;
        }
        if (child.classList.contains(match) || child.nodeName.toLowerCase() == match) {
            return child;
        }
        else {
            return closestParent(child.parentNode, match);
        }
    }
    
    // Loop through if any are found
    for(var i = 0; i < elems.length; i++){
        // Add event listeners to each one
        elems[i].addEventListener("click", function(e){
    
            // Prevent default action of element
            e.preventDefault();
    
            // Grab classes list and convert to array
            var dataClass = this.getAttribute('data-class');
            dataClass = dataClass.split(", ");
    
            // Grab linked elements list and convert to array
            var dataClassElement = this.getAttribute('data-class-element');
            dataClassElement = dataClassElement.split(", ");
    
            // Grab data-scope list if present and convert to array
            if(this.getAttribute("data-class-scope")) {
                var dataClassScope = this.getAttribute("data-class-scope");
                dataClassScope = dataClassScope.split(", ");
            }
    
            // Loop through all our dataClassElement items
            for(var b = 0; b < dataClassElement.length; b++) {
                // Grab elem references, apply scope if found
                if(dataClassScope && dataClassScope[b] !== "false") {
                    // Grab parent
                    var elemParent = closestParent(this, dataClassScope[b]),
    
                    // Grab all matching child elements of parent
                    elemRef = elemParent.querySelectorAll("." + dataClassElement[b]);
    
                    // Convert to array
                    elemRef = Array.prototype.slice.call(elemRef);
    
                    // Add parent if it matches the data-class-element and fits within scope
                    if(dataClassScope[b] === dataClassElement[b] && elemParent.classList.contains(dataClassElement[b])) {
                        elemRef.unshift(elemParent);
                    }
                }
                else {
                    var elemRef = document.querySelectorAll("." + dataClassElement[b]);
                }
                // Grab class we will add
                var elemClass = dataClass[b];
                // Do
                for(var c = 0; c < elemRef.length; c++) {
                    elemRef[c].classList.toggle(elemClass);
                }
            }
    
        });    
    }

And here's another working example:

See the Pen [#5) Form Component w Improved reusable + multiple any class function](https://codepen.io/lukedidit/pen/oWjZej/) by Luke Harrison ([@lukedidit](http://codepen.io/lukedidit)) on [CodePen](http://codepen.io).

### Moving beyond toggle

Our reusable function is quite useful now, but it makes a presumption that toggling classes is the desired behavior. What if when clicked we want the trigger to remove a class if it's present and do nothing otherwise? Currently, that's not possible.

To round the function off let's integrate a bit of extra logic to allow for this behaviour. We'll introduce an optional data-attribute called `data-class-behaviour` which accepts the following options:

  * `toggle` \- Toggles `data-class` on `data-class-element`. This should also be the default behaviour which happens if `data-class-behaviour` isn't defined.
  * `add` \- Adds `data-class` on `data-class-element` if it isn't already present. If it is, nothing happens.
  * `remove` \- Removes `data-class` on `data-class-element` if it's already present. If it isn't, nothing happens.

As with previous data attributes, this new optional attribute will be a comma-separated list to allow for different behaviours for each action. Like so:
    
    
    <button class="c-button" data-class="is-loading, is-disabled" data-class-element="js-form-area, js-input" data-class-behaviour="toggle, remove">Submit</button>

Assuming the above HTML is used, the following would happen once `c-button` is clicked:

  1. `is-loading` would be toggled on `js-form-area`
  2. `is-disabled` would be removed from `js-input` if present.

Let's make the necessary JavaScript changes:
    
    
    // Grab all elements with data-active attribute
    var elems = document.querySelectorAll("[data-class][data-class-element]");
    
    // closestParent helper function
    closestParent = function(child, match) {
        if (!child || child == document) {
            return null;
        }
        if (child.classList.contains(match) || child.nodeName.toLowerCase() == match) {
            return child;
        }
        else {
            return closestParent(child.parentNode, match);
        }
    }
    
    // Loop through if any are found
    for(var i = 0; i < elems.length; i++){
        // Add event listeners to each one
        elems[i].addEventListener("click", function(e){
    
            // Prevent default action of element
            e.preventDefault();
    
            // Grab classes list and convert to array
            var dataClass = this.getAttribute('data-class');
            dataClass = dataClass.split(", ");
    
            // Grab linked elements list and convert to array
            var dataClassElement = this.getAttribute('data-class-element');
            dataClassElement = dataClassElement.split(", ");
    
            // Grab data-class-behaviour list if present and convert to array
            if(this.getAttribute("data-class-behaviour")) {
                var dataClassBehaviour = this.getAttribute("data-class-behaviour");
                dataClassBehaviour = dataClassBehaviour.split(", ");
            }
    
            // Grab data-scope list if present and convert to array
            if(this.getAttribute("data-class-scope")) {
                var dataClassScope = this.getAttribute("data-class-scope");
                dataClassScope = dataClassScope.split(", ");
            }
    
            // Loop through all our dataClassElement items
            for(var b = 0; b < dataClassElement.length; b++) {
                // Grab elem references, apply scope if found
                if(dataClassScope && dataClassScope[b] !== "false") {
                    // Grab parent
                    var elemParent = closestParent(this, dataClassScope[b]),
    
                    // Grab all matching child elements of parent
                    elemRef = elemParent.querySelectorAll("." + dataClassElement[b]);
    
                    // Convert to array
                    elemRef = Array.prototype.slice.call(elemRef);
    
                    // Add parent if it matches the data-class-element and fits within scope
                    if(dataClassScope[b] === dataClassElement[b] && elemParent.classList.contains(dataClassElement[b])) {
                        elemRef.unshift(elemParent);
                    }
                }
                else {
                    var elemRef = document.querySelectorAll("." + dataClassElement[b]);
                }
                // Grab class we will add
                var elemClass = dataClass[b];
                // Grab behaviour if any exists
                if(dataClassBehaviour) {
                    var elemBehaviour = dataClassBehaviour[b];
                }
                // Do
                for(var c = 0; c < elemRef.length; c++) {
                    if(elemBehaviour === "add") {
                        if(!elemRef[c].classList.contains(elemClass)) {
                            elemRef[c].classList.add(elemClass);
                        }
                    }
                    else if(elemBehaviour === "remove") {
                        if(elemRef[c].classList.contains(elemClass)) {
                            elemRef[c].classList.remove(elemClass);
                        }
                    }
                    else {
                        elemRef[c].classList.toggle(elemClass);
                    }
                }
            }
    
        });    
    }

And finally, a working example:

See the Pen [#6) Form Component w Improved reusable + multiple any class + behaviours function](https://codepen.io/lukedidit/pen/zwvdeY/) by Luke Harrison ([@lukedidit](http://codepen.io/lukedidit)) on [CodePen](http://codepen.io).

### Closing

What we've created is a powerful function which can be reused over and over again without writing any extra code. It allows us to quickly assign add, remove or toggle logic for multiple stateful classes on click and lets us scope these changes to the desired area.

There's still many ways in which this reusable function can be improved even further:

  * Support for using different events other than click.
  * Swipe support for touch devices.
  * Some form of simple validation which allows you to declare JavaScript variables which must be truthy before a class change goes ahead.

In the meantime, if you have any ideas for your own improvements or even a completely different method of managing stateful classes altogether, then be sure to let me know in the comments below.
