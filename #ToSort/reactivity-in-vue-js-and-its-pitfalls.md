# Reactivity in Vue.js and Its Pitfalls

_Captured: 2017-05-12 at 17:33 from [dzone.com](https://dzone.com/articles/reactivity-in-vuejs-and-its-pitfalls?oid=twitter&utm_content=buffer9d5fb&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

One thing we love about Vue is the reactivity of the system. If we change a data value it triggers an update of the page to reflect that change.

For example:

Data properties, like `message` in this example, are _reactive_, meaning they will trigger a re-render if changed.

## Pitfalls of Automatic Reactivity Configuration

Vue configures reactivity _automatically_ whenever you create a data property, computed property, bind a prop, etc. This automatic setup is great when coding an app because it can:

  * Save us time.
  * Make our code terse.
  * Help minimize our cognitive load.

It just makes things simpler. **But this simplicity can come back to bite us!** The pitfall is that, like an automatic car, automatic reactivity makes us _lazy_ and when it doesn't work we have no idea why!

### When Good Reactivity Goes Bad

A student in the Ultimate Vue.js Developers course I teach brought an interesting problem to me the other day. He was working on [Vue.js Poster Shop](http://vuejs-poster-shop.vuejsdevelopers.com/), the first project of the course, which requires you to make a shopping cart using Vue.

A product being displayed in the shop is initially represented like this:

But when you add a product to the shopping cart you also need to a quantity, which he dealt with in a method like this:

The logic of the method is as follows:

  * Find the item in the shopping cart.
  * If it's there, increase the quantity.
  * If it's not there, give it a quantity of 1 and add it to the cart.

#### A Problem Appears

The shopping cart template simply displays a list of cart items:

The problem was that no matter the value of `qty`, the template always showed its value as "1."

My initial thought was that the logic of the `addToCart` function must be wrong. But after some debugging, I discovered that the `qty` property was indeed being increased each time the method was called, so that wasn't the issue.

## How Reactivity Works Under the Hood

While causing a mild form of joy in most circumstances, Vue's reactivity system can cause confusion and frustration when it doesn't work like you expect.

This can largely be avoided if you understand _how_ it works.

### Getters and Setters

The default behavior for a JavaScript object, when accessed, is to retrieve or modify the property in question directly. For example:

But when `get` and `set` pseudo properties have been defined, these functions override that default behavior. Read more about [getters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get) and [setters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/set) if you don't know what I'm talking about.

When a Vue instance is created, each data property, component prop, etc., is traversed and getters and setters are added for each. These getters and setters allow Vue to observe changes to the data and trigger updates.

### reactiveSetter()

So, coming back to our product object which looked like this when we defined it:

After Vue instantiates, we can view this object in the console and see the getters and setters that Vue has defined on it:

![Image title](https://dzone.com/storage/temp/5179354-reactivity-1.png)

These getter and setter functions have a number of jobs (check the [source code](https://github.com/vuejs/vue)), but one of the jobs of `rectiveSetter` is to trigger a change notification which results in a page re-render!

### Caveats

This is a brilliant system, albeit a fallible one. If you add (or delete) a property _after_ Vue has instantiated (for example in a method or lifecycle hook) _Vue does not know about it_.

Look and see that although `qty` is defined on the object there are no getters/setters for it:

![Image title](https://dzone.com/storage/temp/5179357-reactivity-2.png)

## Updating Reactive Objects

In the shopping cart example, the way we solved the problem is to create a fresh object when adding to the cart rather than adding a property. That ensures that Vue has the opportunity to define reactive getters and setters:

### Vue.set

But if you don't want to create a new object you can use [Vue.set](https://vuejs.org/v2/api/#Vue-set) to set a new object property. This method ensures the property is created as a reactive property and triggers view updates:

## Arrays

Like objects, arrays are reactive and are observed for changes. Also like objects, arrays have caveats for manipulation. Vue wraps array methods like `push`, `splice`, etc., so they will also trigger view updates.

This is not possible when directly setting an item with the index, for example:

Again, `Vue.set` comes to the rescue:

> Get the latest Vue.js articles, tutorials and cool projects in your inbox with the [Vue.js Developers Newsletter](http://vuejsdevelopers.com/newsletter/?jsdojo_id=dz_riv). 
