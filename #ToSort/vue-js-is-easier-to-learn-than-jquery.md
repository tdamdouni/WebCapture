# Vue.js Is Easier to Learn Than jQuery

_Captured: 2017-05-31 at 08:49 from [dzone.com](https://dzone.com/articles/vuejs-is-easier-to-learn-than-jquery?edition=304091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-30)_

[Start coding today](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt) to experience the powerful engine that drives data application's development, brought to you in partnership with [Qlik](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt).

jQuery is commonly suggested as a good starting point for beginner web developers. Many learn jQuery even before they've begun to learn vanilla JavaScript.

Why? It's partly because of jQuery's popularity, but mostly because of a misguided belief that more experienced developers have: since jQuery is simple for them, that it's also simple for beginners.

## jQuery Offers Brevity, Not Simplification

jQuery definitely takes away a lot of grief with older browser issues. But otherwise, it doesn't do that much to encapsulate the complexity of the DOM API or JavaScript.

Oh, I know it's much _briefer_ to type `$('#id').click(function(event) {..});` than to do it with vanilla JS. But you still need to _understand_ the same stuff to write that code: DOM node selection, event handling, callbacks, and so on.

jQuery is simpler to write if you _already_ understand the DOM API and JavaScript well, but it's not any easier for beginners.

## Vue.js

Vue.js is the hot new framework of the week. But it's not without merit. Of its many strengths, I'd say the simplicity of learning is probably number one. Simplicity is built into its design.

I assert that a beginner could build a trivial web app with Vue and understand much more of _how their code works_ than they would by building the same thing with jQuery.

So, let's implement a really simple app with both jQuery and Vue.js and see what that brings to light. This app will count the number of times a button is clicked, and display that number on the screen.

## Implementing With jQuery

Here's a typical implementation with jQuery:
    
    
    <div id="output"></div>
    
    
    <button id="increment">Increment</button>

It looks simple, but consider that's only because you're viewing it with your experienced developer eyes. Understanding what that code is doing is actually pretty tricky. Consider:

  1. The first thing you will usually type in a jQuery script is `$(document).ready(function() { .. });`. In those 30-something characters, you're assaulted by these four tough concepts: DOM node selection, event handling, the loading process of a document, and callbacks. If you don't get all those things, then you _don't_ understand the code you just wrote.
  2. Getting to the business of selecting a DOM element to work with, you'll need the jQuery constructor `$('...')`. Unfortunately you can't specify exactly what nodes you'll get, instead, you need to create an appropriate filter using a CSS3-like selector and what you actually get will be determined when it runs. To do this well, you'll need to create a mental copy of your DOM and simulate what would happen when you run your filter against it. And as every method you write updates the DOM, you have to similarly update your mental DOM and consider if your filters are still going to work as intended.
  3. For some positive news, there's only really one pattern in jQuery: select something, then do stuff to that selection with a method from the API. The problem with this pattern is that we now have a flat, one-dimensional API with well over 100 methods that do everything from AJAX to array iteration. It's impossible to make that many method names descriptive enough to distinguish both what they do _and_ what they return. Good luck to a beginner comprehending what chained methods are really doing.

## Implementing With Vue.js

Here's a typical implementation with Vue.js:
    
    
      <button v-on:click="increment">Increment</button>

Vue has taken care of many of the pain points raised above about jQuery:

  1. No need to worry about DOM ready callback hijinks, that complexity has been encapsulated. Vue's lifecycle hooks will allow more refined control if and when it's needed.
  2. An obvious link is made between the data property `counter` and the DOM node where it's rendering. There is no mental DOM required, you can see it on the page and have the assurance that updating the counter is not going to mess with your DOM in unexpected ways due to wonky node selection.
  3. We don't have ambiguous API methods to look up or remember. Different functionality is nicely organized and stratified in the Vue constructor object or is applied directly to DOM nodes in the template via directives giving them more context by which to be understood.

## Wrapping Up

jQuery is only easier if you already understand JavaScript and the DOM API. That's not the case for beginners. jQuery is not simpler, just abbreviated.

Vue, on the other hand, has simplicity built into its design. Many difficult parts of the DOM API have been well encapsulated. Beginners will be able to write code that they actually understand, and when they need to do more complex stuff, it'll be available to them.

So next time someone asks you what they should learn as a beginner web developer, maybe jQuery is not the thing.

[Create data driven applications](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij) in Qlik's free and easy to use coding environment, brought to you in partnership with [Qlik](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij).
