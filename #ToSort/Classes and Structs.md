# Classes and Structs

_Captured: 2015-12-03 at 19:30 from [swift.ayaka.me](http://swift.ayaka.me/posts/2015/11/30/classes-and-structs)_

Both classes and structs are the main building blocks of most applications. They help us organize our code into pieces that we can reason about more intuitively and with greater ease. Today, we'll go over how classes and structs behave differently from each other, and finish off by starting to think about when to use a class vs. when to use a struct.

I highly recommend [downloading the Playground](http://swift.ayaka.me/s/Structsplayground.zip) or cloning [the repo](https://github.com/ayanonagon/learn-swift) to follow along.

Let's get started. ⚡️

### Classes

Classes allow us to model many real world examples and help us organize and reason about our code. For example, we might want to make a shopping app. In our app, you can choose items, put them in a cart, and find out the total to pay.

We might model an "item" as below:

We can model a "cart" as below. It has a function `total` that calculates the total price of the items in the cart. (Don't worry if you don't know what `reduce` is, but feel free to look it up if you're curious! 👀)

class Cart {

let items: [Item]

var total: UInt {

return items.reduce(0) { sum, item in

sum + item.price

}

}

init(items: [Item]) {

self.items = items

}

}

And now we go shopping! 💳

First, we need to buy a chicken hat. (Well, I need one. Why not?) I found a hand-knit wool chicken hat for $50 and a crispy green apple for $1. (I hope you like apples.) Let's put those in the cart and calculate the total.

![](http://static1.squarespace.com/static/56129a82e4b0147725b391f5/t/5651494be4b02ba778fef128/1448167756931/?format=1500w)

The total we expect to pay is $51. That seems like a pretty good deal, especially for such a high quality chicken hat. Let's go and pay before we find the urge to buy more stuff.

While we're strolling toward the checkout counter with the soon-to-be-ours chicken hat and apple, the shop decides to increase the price of the chicken hat to $1000. When they ring up our items at checkout, the total is $1001. We were expecting to pay $51. Not 🆒.

![](http://static1.squarespace.com/static/56129a82e4b0147725b391f5/t/56514994e4b02ba778fef26b/1448167830224/?format=1000w)

What happened here?

Classes are **passed by reference** meaning that there can be more than one reference to a given instance of a class. So in our case, we had a reference to 🐔 in our `Cart` instance, but we also had a reference outside the cart which allowed the shop to change its price on us unexpectedly.

So what's the alternative to passing by reference? That's where structs come into play.

### Structs

In Swift, there are structs (short for "structures"). Like classes, they allow us to model many real world examples and help us organize and reason about our code. Unlike like classes, which are passed by reference, structs are **passed by value**.

Let's see what happens if we make `Item` a struct instead of a class. All we have to do is change it from `class` to `struct` in our declaration.

Now let's try shopping again. I still need my chicken hat and you're still hungry for a green apple. We put those items in our cart, and the total is $51 as before.

![Screen Shot 2015-11-29 at 14.19.22.png](http://static1.squarespace.com/static/56129a82e4b0147725b391f5/t/565b7a65e4b0702d3803357d/1448835686499/Screen+Shot+2015-11-29+at+14.19.22.png?format=1500w)

The shop, again, decides to increase the price of the chicken hat to $1000 (maybe we should stop shopping here?). What's the total in the cart?

![](http://static1.squarespace.com/static/56129a82e4b0147725b391f5/t/565b7a75e4b0702d38033620/1448835702744/?format=1000w)

It's still $51. 🎉

What was different in the struct example compared to the class example? When something is "passed by value" (which is the case for structs, but not classes), the value is copied on assignment instead of sharing a reference. So when we created the `items` array like `var items = [chickenHat, apple]` that `chickenHat` was already different from the `chickenHat` from `var chickenHat = Item(name: "🐔", price: 5000)`. If you're curious, you can update `chickenHat`'s price right after we create `items` and see what the playground thinks is the value of `items`.

![Screen Shot 2015-11-29 at 14.43.34.png](http://static1.squarespace.com/static/56129a82e4b0147725b391f5/t/565b8008e4b0702d38036776/1448837129509/Screen+Shot+2015-11-29+at+14.43.34.png?format=1500w)

As you can see above, `items` has not changed.

However, if you do the same when `Item` is a class, you get the following result.

![](http://static1.squarespace.com/static/56129a82e4b0147725b391f5/t/565b8044e4b09e25855e5450/1448837189615/?format=1500w)

The chicken hat in `items` is $1000!

This is cool and all, but you might be wondering how structs and "value types" are even useful. Because in reality, you wouldn't write such silly code that accidentally increases the price of the chicken hat, right? Imagine an app that's been around for a while with a codebase of ten of thousands or more lines of code. On top of that, we're in a multi-threaded environment because that's the nature of our apps. Even if we are careful about not doing stupid things, accidents happen. When used effectively, value types can make code easier to reason about and follow, especially as our codebase gets bigger and more complex. 🌟

### Value-types, everywhere

It's also worth mentioning that value-types are nothing new. Take a look at this for example.

![](http://static1.squarespace.com/static/56129a82e4b0147725b391f5/t/565b92b9e4b0fad364f6cfcf/1448841914203/?format=300w)

If `Int`'s were passed by reference, `y` would also be `2` at the end, but it's not because it's passed by value. In Swift standard library offers many value-types, including but not limited to `Int`, `String`, and `Array`. Structs are just another addition to this family, and we can start using them immediately.

At this point, I hope you have a lot of questions. Which brings us to the final part…

I learned about reference-types vs. value-types back when I was first learning C programming, and I still remember how confusing it was and how much it didn't make sense at first. Looking back and thinking about how I learned and am still learning, I think learning about values and references comes in two parts:

  1. Learning how structs and classes behave similarly and differently.
  2. Learning when to use structs and when to use classes.

I leave you all with some resources that I recommend for both parts.

For this, I recommend experimenting in a Playground (maybe you can extend the example that we worked on today!) and reading explanations from many different sources. Hopefully, this post was also a good introduction to this. If you want to keep exploring, we only made `Item` a struct in our example, but what happens if we also make `Cart` a struct? What changes?

#### 2\. Learning when to use structs and when to use classes.

This is a much more nuanced and difficult topic, and for me, I've been learning mostly by trying things out and making mistakes. Luckily, some people have been writing and talking about what they've learned, so you can make fewer mistakes to start with.

  * Drew Crawford's blog post [Should I use a Swift struct or a class?](http://faq.sealedabstract.com/structs_or_classes/) The TL;DR: at the end of the post is a must-read too.
  * [Andy Matuschak on objc.io](https://www.objc.io/issues/16-swift/swift-classes-vs-structs/) in which he discusses the "value of values" and the "object of objects" and more.
  * [Boundaries](https://www.destroyallsoftware.com/talks/boundaries) by Gary Bernhardt goes over value-types and how to use them effectively with reference-types. This isn't Swift-specific, but it's a nice reminder that these concepts are relevant across different languages and problems.

One of these days I hope to have enough organized thoughts and opinions about when to use a class or struct based on experience and write about it. If you have any thoughts around specific cases of when it was better to a struct or class (or know anyone who's written about their experience), let me know in the comments below! 😃

That's it for now. If you have any questions, feel free to leave them in the comments below, or tweet at me [@ayanonagon](https://twitter.com/ayanonagon). The biggest reason I'm writing these posts is to get better at explaining concepts and how amazing they are, so any feedback about what was clear vs. not would be much appreciated as well. Also let me know what other topics you want to hear about. Hope you had fun learning, and thanks for reading! ☕️
