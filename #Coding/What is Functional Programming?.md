# What is Functional Programming?

_Captured: 2016-11-12 at 08:07 from [www.chriskrycho.com](http://www.chriskrycho.com/2016/what-is-functional-programming.html)_

## Clearing the Table: Functional Programming's Reputation

Functional programming has something of a reputation: on the one hand, as incredible difficult, dense, full of mathematical jargon, applicable only to certain fields like machine learning or massive data analysis; on the other hand, as a kind of panacea that solves all of your problems. The reality, I think, is a little bit of both.

The world of functional programming _does_ include a lot of jargon from the math world, and there are good reasons for that, but there is also a lot we could do to make it more approachable to people who don't have a background in, say category. Category theory is useful, of course, and I think there are times when we might want to be able to draw on it. But gladly, functional programming doesn't require you to know what an _applicative functor_ is to be able to use it. (And, gladly, there's a lot of increasingly-solid teaching material out there about functional programming which _doesn't_ lean on math concepts.)

On the other side, functional programming does give us some real and serious benefits, and that's what I'm going to spend the first third or so of this talk looking at. But of course, it's still just a tool, and even though it is a very helpful and very powerful tool, it can't keep us from writing bugs. Still, every tool we can add to our belt for writing correct software is a win.

One more prefatory note before we get into the meat of this talk: unfamiliar terminology is not specific to functional programming. So, yes, when you see this list, it might seem a little out there:

  * Functor
  * Applicative
  * Monoid
  * Monad

And in truth, a number of those could have better names. _But_ we have plenty of terminology we throw around in the world of imperative, object-oriented programming. To pick just one, obvious and easy example -- what are the SOLID principles?

  * Single reponsibility
  * Open/closed
  * Liskov substitution
  * Interface segregation
  * Dependency inversion

You may not remember what it felt like the first time you encountered SOLID, but suffice it to say: "Liskov substitution principle" isn't any more intuitive or obvious than "Monad". You're just familiar with one of them. The same is true of "applicative" and "Visitor pattern". And so on. Granted, again: it would be nice for some of these things to have easier names, a _big_ part of the pain here is just unfamiliarity.

So, with that out of the way, what _is_ functional programming?

## What is functional programming?

Functional programming is a style of programming that uses _pure functions_ and _immutable data_ for as many things as possible, and builds programs primarily out of _functions_ rather than other abstractions. I'll define all of those terms in a moment, but first…

### Why do we care?

We care, frankly, because _we're not that smart_. Let's think about some of the kinds of things we're doing with, say, restaurant software: clients, with locations, building baskets, composed of products with options and modifiers, which have a set of rules for what combinations are allowed both of products and of their elements as making up a basket, which turn into orders, which have associated payment schemes (sometimes a lot of them), which generate data to send to a point-of-sale as well as summaries for the customer who ordered it, and so on. There are a _lot_ of moving pieces there. I'm sure a missed some non-trivial pieces, too. And if all of that is _stateful_, that's a lot of state to hold in your head.

Let me be a bit provocative for a moment. Imagine you were reading a JavaScript module and it looked like this:
    
    
    var foo = 12;
    var bar = 'blah';
    var quux = { waffles: 'always' };
    
    export function doSomething() {
      foo = 42;
    }
    
    export function getSomething() {
      bar = quux;
      quux.waffles = 'never';
      return bar;
    }

Everyone watching would presumably say, "No that's bad, don't do that!" Why? Because there is _global state_ being changed by those functions, and there's nothing about the functions which tells you what's going on. Global variables are bad. Bad bad bad. We all know this. Why is it bad? Because you have no idea when you call `doSomething()` or `getSomething()` what kinds of side effects it might have. And if `doSomething()` and `getSomething()` affect the same data, then the order you call them in matters.

In a previous job, I spent literally months chasing a bunch of bugs in a C codebase where all of the state was global. _We don't do this anymore._

But really, what's different about this?
    
    
    class AThing {
      constructor() {
        this.foo = 12;
        this.bar = 'blah';
        this.quux = { waffles: 'always' };
      }
    
      doSomething() {
        this.foo = 42;
      }
    
      getSomething() {
        this.bar = this.quux;
        this.quux.waffles = 'never';
        return this.bar;
      }
    }

We have some "internal" data, just like we had in the module up above. And we have some public methods which change that state. In terms of these internals, it's the same. There are differences in terms of having _instances_ and things like that, but in terms of understanding the behavior of the system -- understanding the state involved -- it's the same. It's global, mutable state. Now it's not global like attaching something to the `window` object in JavaScript, and that's good, but still: at the module or class level, it's just global mutable state, with no guarantees about how anything works. And this is normal -- endemic, even -- in object-oriented code. We encapsulate our state, but we have _tons_ of state, it's all mutable, and as far as any given class method call is concerned, it's all global to that class.

You have no idea, when you call a given object method, what it might do. The fact that you call it with an `Int` and get out a `String` tells you almost nothing. For all you know, it's triggering a JSON-RPC call using the int as the ID for the endpoint, which in turn triggers an operation, responds with another ID, which you then use to query a database, and load a string from there, which you then set on some other member of the object instance, and then return. Should you write a method that does that? Probably not. But you can; nothing stops you.

When you call a method, you have no idea what it will do. JavaScript, TypeScript, C♯, it doesn't matter. You have literally no idea. And that makes things _hard_.

  * It often makes fixing bugs hard, because it means you have to figure out which particular _state_ caused the issue, and find a way to reproduce that state. Which usually means calling methods in a particular order.
  * It makes testing hard. Again, it often entails calling methods in a particular order. It also means you often need mocks for all those outside-world things you're trying to do.

Functional programming is an out. An escape hatch. An acknowledgement, a recognition, that holding all of this in our heads is too much for us. No one is that smart. And our software, even at its best, is hard to hold in our heads, hard to make sure that our changes don't break something seemingly unrelated, hard to see how the pieces fit together -- hard, in a phrase you'll often hear from functional programming fans, hard to reason about.

So, how do we solve these problems? With functional programming!

### What _is_ functional programming?

Functional programming is basically combining four bigs ideas:

  1. First class functions
  2. Higher-order functions
  3. Pure functions
  4. Immutable data

The combination of these things leads us to a _very_ different style of programming than traditional OOP. Let's define them.

We'll start by looking at the things that are probably most familiar to you if you're a JavaScript developer (even if you haven't necessarily heard the names): first-class functions and higher-order functions.

When we talk about _first class functions,_ we mean that functions are just data -- they're first-class items in the language just like any other type. As such, a function is just another thing you can hand around as an argument to other functions. There's no distinction between a function and a number or a string or some complex data structure. This is essential because, when you combine it with higher-order functions, it allows for incredible _simplicity_ and incredible _reusability_.

Higher-order functions, in turn, are functions which take other functions as parameters or return them as their values. We'll see this in detail in a worked example in a few, but for right now, let's just use a really simple example that will be familiar to anyone who's done much JavaScript: using `map`.

If we have a collection like an array and we want to transform every piece of data in it, we could of course do it with a for loop, and with iterable types we could use `[for ... of`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of). But with `map`, we can just leave the implementation details of _how_ the items in the array are iterated through, and instead worry about what we want to change. We can do that because `map` takes functions as arguments.
    
    
    const initialValues = [1, 2, 3];
    const doubledValues = initialValues.map(value => value * 2);

We did it there with a function explicitly, but we could just as easily extract the function like this:
    
    
    const double = value => value * 2;
    const initialValues = [1, 2, 3];
    const doubledValues = initialValues.map(double);

This is possible because _functions are just data_--they're first-class members of the language -- and therefore _functions can be arguments or return values_--the language supports higher-order functions.

What about _pure functions_? Pure functions are functions with _no effects_. The input directly translates to the output, every time. The examples we looked at just a moment ago with `map` are all pure functions (and it's a really weird antipattern to use effectful functions with `map`! Don't do that! Use `forEach` if you must have an effect). Here are a few more super simple examples:
    
    
    const add = (a, b) => a + b;
    const toString = (number) => `The value is ${number}`;
    const toLength = (list) => list.length;

Here are some examples of straightforward functions which are _not_ pure:
    
    
    const logDataFromEndpoint = (endpoint) => {
      fetch(endpoint).then(response => {
        console.log(response);
      });
    };
    
    let foo = 42;
    const setFoo = (newValue) => {
      foo = newValue;
    };
    
    const getFoo = () => foo;

So a pure function is one whose output is _solely_ determined by its input That means no talking to a database, no making API calls, no reading from or writing to disk.

And of course, you can't do anything meaningful with _just_ pure functions. We need user input, and we need to put the results of our computation somewhere. So the goal isn't to write _only_ pure functions. It's to write _mostly_ pure functions and to _isolate_ all impure functions.

What this gets us is two things:

  1. A much smaller list of things to worry about when we're looking at a given function.
  2. The ability to _compose_ functions together more easily.

We have fewer things to keep in our heads when we look at any given pure function, because we don't have to worry at all about whether something it touches has been changed by another function or not. We have inputs. We transform them into outputs. That's it. Compare these two things in practice.

Here's a traditional OOP approach:
    
    
    class Order {
      constructor() {
        this.subTotal = 0.0;
        this.taxRate = 0.01;
      }
    
      getTotal() {
        return this.subTotal * (1 + this.taxRate);
      }
    }
    
    const order = new Order();
    order.subTotal = 42.00;
    
    const total = order.getTotal();

Note that the total is always dependent on what has happened in the object. If we write `order.subTotal = 43`, `order.total` will change. So if we want to test how `total` behaves, or if there's a bug in it, we need to make sure we've made all the appropriate transformations to the object ahead of time. That's no big deal here; the `total` getter is incredibly simple (and in fact, we'd normally just write it with a property getter). But still, we have to construct an order and make sure all the relevant properties are set to get the right value out of `getTotal()`. Things outside the method call itself affect what we get back. We have no way to test `getTotal()` by itself, and no way to debug it if there's a bug without first doing some object setup.

Now, here's a functional approach.
    
    
    const order = {
      subTotal: 42.0,
      taxRate: 0.01
    }
    
    const getTotal = (subTotal, taxRate) => subTotal * (1 + taxRate);
    const total = orderTotal(order.subTotal, order.taxes);

Note that the object is _just data_. It's a _record_. And the function just takes a couple of arguments. If there needed to be a more complicated transformation internally, we could do that just as easily. Note that it also decouples the structure of the data from the actual computation (though we could pass in a record as well if we had a good reason to).

This makes it easily testable, for free. Want to make sure different tax rates get the correct output? Just… pass in a different tax rate. You don't have to do any complicated work setting up an object instance first (which is especially important for more complex data types). It also makes it easier to chase down any bugs: the only thing you have to care about is that simple function body. There's no other state to think about, because there's no state at all here from the perspective of the function: just inputs and outputs.

This has one other _really_ important consequence, which goes by the name **referential transparency**. All that means is that anywhere you see a pure function, you can always substitute the value it produces, or vice versa. So unlike the `Order::getTotal()` method, where (a) it's attached to an object instance and (b) it's dependent on other things about that object, so you can't just substitute it in, or freely move it around, when you're doing a refactor. _Maybe_ you can, but you'd better hope that all the other state is shuffled around with it correctly. Whereas, with the standalone `getTotal()` function, all you need is its arguments, and you'll always get the same thing back.

This is just like math: if you say, _x_ = 5 when solving an algebraic equation, you can put 5 _anywhere you see _x__; or, if it's useful for factoring the equation or something, you can just as easily put _x_ anywhere you see 5. And in math, that's true for _f_(_x_) as well. When we use pure functions, it's true for programming, too! That makes refactoring much easier.

As we'll see in the example I walk through in a minute, it also lets us _compose_ functions together far more easily. If all we have are inputs and outputs, then I can take the output from one function and use it as the input to the next.

Complementing the use of mostly pure functions is to use _immutable data_. Instead of having objects which we mutate, we create copies of the data as we transform it.

You're probably wondering how in the world this can work (and also how you avoid it being incredibly computationally expensive). For the most part, we can rely on two things: smart compilers and runtimes, and the fact that we often don't need to reuse the _exact_ same data because we're transforming it. However, as we'll see below, in languages which don't have native support for immutability, it can impose a performance penalty. Gladly, there are ways to work around this!

## A Worked Example

Let's get down to a real example of these ideas. This is a 'code kata' I do every so often. In this particular kata, you get a list of burger orders which looks like this:
    
    
    [
      { condiments: ['ketchup', 'mustard', 'pickles'] },
      { condiments: ['tomatoes'] },
      { condiments: ['mustard', 'ketchup'] },
      // etc...
    ]

You're supposed to take this list (of 10,000-some-odd burger variations!) and determine what the top ten most common orders (not just condiments, but orders) are. (The truth is, the list actually mostly looks like `condiments: ['ketchup']` over and over again.) So as a preliminary, you can assume that the data is being loaded like this:
    
    
    const getBurgers = () =>
      fetch('http://files.example.com/burgers.json')
        .then(request => request.json());

And we'll print our results (which will always end up in the same format) like this:
    
    
    const descAndCountToOutput = descAndCount => `${descAndCount[0]}: ${descAndCount[1]}`;

This is actually a perfect case to demonstrate how functional programming ideas can help us solve a problem.

First, let's look at what I think is a _relatively_ reasonable imperative approach. Our basic strategy will be:

  1. Convert condiments to descriptions. 
    1. Convert the objects to just their lists of condiments.
    2. Sort those strings.
    3. Turn them into descriptions by joining them with a comma.
  2. Build up a mapping from description to count.
  3. Sort that by count.
  4. Get the top 10.
  5. Print out the results.
    
    
    getBurgers().then(burgers => {
      let totals = {};
    
      // 2. Build up a mapping from description to count.
      for (let burger of burgers) {
        // 1. Convert condiments to descriptions.
        // 1.1. Convert the objects to just their lists of condiments.
        const condiments = burger.condiments;
        // 1.2. Sort those strings.
        condiments.sort();
        // 1.3. Turn them into descriptions by joining them with a comma.
        const description = condiments.join(', ');
    
        // 2. Build up a mapping from description to count.
        const previousCount = totals[description];
        totals[description] = previousCount ? previousCount + 1 : 1;
      }
    
      // 3. Sort that by count.
      const sortableCondiments = Object.entries(totals);
      sortableCondiments.sort((a, b) => b[1] - a[1]);
      // 4. Get the top 10.
      const topTen = sortableCondiments.slice(0, 10);
      // 5. Print out the results.
      for (let descAndCount of topTen) {
        console.log(descAndCountToOutput(descAndCount));
      }
    });

That's pretty well-factored. But it's pretty wrapped up on the specific details of this problem, and there's basically nothing here I could reuse. It's also relatively hard to test. There aren't really a lot of pieces there we could break up into smaller functions if we wanted to figure out why something was broken. The way you'd end up fixing a bug here is probably by dropping `debugger` or `console.log()` statements in there to see what the values are at any given spot.

And this is where functional programming really does give us a better way.

Instead of thinking about the specific details of _how_ to get from A to B, let's think about what we start with and what we finish with, and see if we can build up a pipeline of transformations that will get us there.

We start with a _list_ of _objects_ containing _arrays_ of _strings_. We want to end up with a _list_ of the _distinct combinations_ and their _frequency_. How can we do this? Well, the basic idea is the same as what we did above:

  1. Convert condiments to descriptions. 
    1. Convert the objects to just their lists of condiments.
    2. Sort those strings.
    3. Turn them into descriptions by joining them with a comma.
  2. Build up a mapping from description to count.
  3. Sort that by count.
  4. Get the top 10.
  5. Print out the results.

To someone acquainted with functional programming, that looks like a bunch of `map`s, a `reduce`, and some `sort`s. And each of those using just simple, pure functions. Let's see what that might look like. First, what are our transformations?

The step 1 transformations are all quite straightforward:
    
    
    // 1. Convert condiments to descriptions.
    // 1.1. Convert the objects to just their lists of condiments.
    const toCondiments = burger => burger.condiments ? burger.condiments : [];
    // 1.2. Sort those strings.
    const toSortedCondiments = condiments => condiments.concat().sort();
    // 1.3. Turn them into descriptions by joining them with a comma.
    const toDescriptions = condiments => condiments.join(', ');

Step 2 is a little more involved: it involves building up a new data structure (`totals`) from an old one. This function is a _reducer_: it will build up `totals` by updating `totals` with each `description` from an array of them.
    
    
    // 2. Build up a mapping from description to count.
    const toTotals = (totals, description) => {
      const previousCount = totals[description];
      const count = previousCount ? previousCount + 1 : 1;
      totals[description] = count;
      return totals;
    };
    
    // 3. Sort that by count.
    const byCount = (a, b) => b[1] - a[1];

We'll see how to get just 10 in a moment; for now, let's also wrap up the output:
    
    
    // 5. Print it out
    const output = value => { console.log(value); };

These are our base building blocks, and we'll re-use them in each of the approaches I cover below. Note that we've now taken those same basic steps from our imperative approach and turned them into standalone, testable functions. They're small and single-purpose, which always helps. But more importantly, (with two exceptions we'll talk about in a minute) all of those transformations are _pure functions_, we know that we'll get the same results every time we use them. If I want to make sure that burger condiments are converted correctly, I can test _just that function_.
    
    
    describe('toCondiments', () => {
      it('returns an empty list when there is no `condiments`', () => {
        toCondiments({}).should.deepEqual([]);
      });
    
      it('returns the list of condiments when it is passed', () => {
        const condiments = ['ketchup', 'mustard'];
        toCondiments({ condiments }).should.deepEqual(condiments);
      });
    })

This is a trivial example, of course, but it gets the point across: all we have to do to test this is pass in an object. It doesn't depend on anything else. It doesn't have _any knowledge_ of how we're going to use it. It doesn't know that it's going to be used with data coming from an array. All it knows is that if you give it an object with a `condiments` property, it'll hand you back the array attached to that property.

The result is that, with all of these functions, we don't have to deal with mocks or stubs or anything like that to be testable. Input produces output. Pure functions are great for this. Now, some of you may be thinking, "That's great, but what about IO, or databases, or any other time we actually interact with the world? What about talking to a point-of-sale?" I actually have some tentative thoughts about a future tech talk to look at how to do that in some detail, but for today, just remember that the goal is to write as many pure functions as possible, and to isolate the rest of your code from knowing about that. And of course, that's best practice anyway! We're just codifying it. We'll see what that looks like in practice in jus ta minute.

Now, while we're on the topic of pure functions, some of you with quick eyes may have noticed that two of these little functions we laid out are actually _not_ pure: JavaScript's `Array.sort` method operates in-place, for performance reasons, and so does our `toTotals` function. So a truly pure version of the sorting function looks like this:
    
    
    const toSortedCondiments = condiments => condiments.concat().sort();

Similarly, we _could_ define the `toTotals` to return a new object every time, like this:
    
    
    const toTotals = (totals, description) => {
      const previousCount = totals[description];
      const count = previousCount ? previousCount + 1 : 1;
      const update = { [description]: count };
      return Object.assign({}, totals, update);
    };

Unfortunately, given the amount of data we're dealing with, that's prohibitively expensive. We end up spending a _lot_ of time allocating objects and garbage-collecting them. As a result, it's tens of thousands of times slower. Running it on my 4GHz iMac, the in-place version takes less than 40ms. Doing it the strictly pure way -- returning copies every time -- takes ~53s. And if you profile it, almost all of that time is spent in `assign` (52.95s).

This takes us to an important point, though: it's actually not a particularly big deal to have this particular data changed in place, because we're not going to do anything _else_ with it. And in fact, under the hood, this is exactly what pure functional languages do with these kinds of transformations -- precisely because it's perfectly safe to do so, because we're the only ones who have access to this data. We're generating a _new_ data structure from the data that we were originally handed, and the next function will make its own new data structure (whether a copy or something else).

In other words, when we're talking about a _pure function_, we don't really care about internal mutability (though of course, that can bite us if we're not careful). We're really concerned about _external_ mutability. As long as the same inputs get the same outputs every time, the rest of the world doesn't have to care how we got that result.

Now let's see how we use these functions.

First, here's a pure-JavaScript approach, but a more functional one instead of an imperative one:
    
    
    getBurgers().then(burgers => {
      const descriptionToCount = burgers
        .map(toCondiments)
        .map(toSortedCondiments)
        .map(toDescriptions)
        .reduce(toTotals, {})
    
      const entries = Object.entries(descriptionToCount);
    
      [...entries]
        .sort(byCount)
        .slice(0, 10)  // 4. Get the top 10.
        .map(descAndCountToOutput)
        .forEach(output);
    });

First, the good: our transformation is no longer all jumbled together. In fact, our code reads a lot like our original description did. Also, notice that we just have a bunch of functions operating on data: none of the functions used here have any knowledge about where the data comes from that they operate on.

But then we also have a couple things that are a _little_ bit clunky. The main thing that sticks out is that sudden stop in the chain in the middle.

When we're dealing with the `Array` type, everything is fine, but when we convert our data into a `Map`, we no longer have that option, so we have to jump through some hoops to do the transformation back into the data type we need. We're stuck if the object type doesn't have the method we need. We're kind of trying to mash together the imperative and functional styles, and it's leaving us in a little bit of a weird spot.

There's another issue here, though, and it's the way that using the method-style calling convention obscures something important. When we call _most_ of those methods, we're doing something quite different from what most _methods_ do. A method normally is an operation on an object. These methods -- most of them -- are operations that return _new_ objects. So it's nice from a syntax perspective, but if we're not _already_ familiar with the behavior of a given method, it won't be clear at all that we're actually generating a bunch of totally new data by calling those methods.

And… two of these methods (`sort` and `forEach`) _are_ not doing that, but are modifying an array in place instead.

The first step away from this problem is to use a tool like [Lodash](https://lodash.com).
    
    
    // More functional, with _:
    // We tweak how a few of these work slightly to play nicely.
    const _toDescriptions = condiments => _.join(condiments, ', ');
    const _byCount = _.property(1);
    
    getBurgers().then(burgers => {
      const condiments = _.map(burgers, toCondiments);
      const sortedCondiments = _.map(condiments, toSortedCondiments);
      const descriptions = _.map(sortedCondiments, _toDescriptions);
      const totals = _.reduce(descriptions, toTotals, {});
      const totalPairs = _.toPairs(totals);
      const sortedPairs = _.sortBy(totalPairs, _byCount);
      const sortedPairsDescending = _.reverse(sortedPairs);
      const topTen = _.take(sortedPairsDescending, 10);
      const forOutput = _.map(topTen, descAndCountToOutput)
      _.forEach(forOutput, output);
    });

But it seems like we lost something when we moved away from the object-oriented approach. Being able to chain things, so that each item worked with the previous item, was actually pretty nice. And needing all these intermediate variables is _not_ so nice.

One way around this is to use Lodash's `_.chain` method. That would have let us write it like this:
    
    
    getBurgers().then(burgers => {
      const foo = _.chain(burgers)
        .map(toCondiments)
        .map(toSortedCondiments)
        .map(_toDescriptions)
        .reduce(toTotals, {})
        .toPairs()
        .sortBy(_byCount)
        .reverse()
        .take(10)
        .map(descAndCountToOutput)
        .value()
        .forEach(output);
    });

And that _is_ a win. But it only works because JavaScript is _incredibly_ dynamic and lets us change the behavior of the underlying `Array` type. (You'd have a much harder time doing that in Java or C♯!)

Perhaps just as importantly, it requires us to make sure that we do that `_.chain()` call on on anything we want to tackle this way. So, can we get the benefits of this some _other_ way? Well, obviously the answer is _yes_ because I wouldn't be asking otherwise.

But we can actually go a bit further, and end up in a spot where we don't need to modify the object prototype at all. We can just do this with a series of standalone functions which don't depend on being attached to _any_ object. If we use the [Ramda](http://ramdajs.com) library,[1](http://www.chriskrycho.com/2016/what-is-functional-programming.html) we can tackle this with nothing but functions.
    
    
    const getTop10Burgers = R.pipe(
      R.map(R.prop('condiments')),
      R.map(R.sortBy(R.toString)),
      R.map(R.join(', ')),
      R.reduce(toTotals, {}),
      R.toPairs,
      R.sortBy(R.prop(1)),  // will give us least to greatest
      R.reverse,
      R.take(10),
      R.map(descAndCountToOutput)
    );
    
    return getBurgers()
      .then(getTop10Burgers)
      .then(R.forEach(output));

Notice the difference between here and even where we started with Lodash: we're no longer dependent on a specific piece of data being present. Instead, we've created a standalone function which can operate on that data, simply by "piping" together -- that is, _composing_--a bunch of other, smaller functions. The output from each one is used as the input for the next.

One of the many small niceties that falls out of this is that we can refactor this just by pulling it apart into smaller acts of compositions.

Here's an example of how we might use that. We defined those simple transformations for the condiments as a set of three functions, which converted them from objects with `condiments` elements, sorted them, and joined them into a string. Now, let's build those into meaningful functions for each step:
    
    
    // 1. Convert condiments to descriptions.
    const burgerRecordsToDescriptions = R.pipe(
      R.map(R.prop('condiments')),
      R.map(R.sortBy(R.toString)),
      R.map(R.join(', ')),
    );
    
    // 2. Build up a mapping from description to count.
    const descriptionsToUniqueCounts = R.pipe(
      R.reduce(toTotals, {}),
      R.toPairs,
    );
    
    // 3. Sort that by count.
    const uniqueCountsToSortedPairs = R.pipe(
      R.sortBy(R.prop(1)),
      R.reverse,
    );
    
    // For (4), to get the top 10, we'll just use `R.take(10)`.
    // We could also alias that, but it doesn't gain us much.
    
    // 5. Print it out
    const sortedPairsToConsole = R.pipe(
      R.map(descAndCountToOutput),
      R.forEach(output)
    );

Then we can put those together into another, top-level function to do _exactly_ our steps.
    
    
    const getTop10Burgers = R.pipe(
      burgerRecordsToDescriptions,  // (1)
      descriptionsToUniqueCounts,   // (2)
      uniqueCountsToSortedPairs,    // (3)
      R.take(10)                    // (4)
    );
    
    getBurgers()
      .then(getTop10Burgers)
      .then(sortedPairsToConsole);  // (5)

Notice that, because each step is just composing together functions, "refactoring" is easy. And, to be sure, you have to be mindful about what comes in and out of each function. But that's true in the imperative approach, too: you always have to keep track of the state of the object you're building up, but there you're doing it in the middle of a loop, so you're keeping track of a lot _more_ state at any given time. Functions with simple inputs and outputs give us a more explicit way of specifying the structure and state of the data at any given time. That's true even in JavaScript, but it goes double if we're in a typed language like F♯, Elm, etc., where we can specify those types for the function as a way of designing the flow of the program. (That's such a helpful way of solving problems, in fact, that I may also do a talk on type-driven design in the future!)

Note, as well, that we've now completely isolated our input and output from everything else. The middle there is a chain of pure functions, built out of other pure functions, which neither know nor care that the data came in from an API call, or that we're going to print it to the console when we finish.

So this takes us back around to that first question: why do we care? At the end of the day, is this really a win over the imperative style? Is the final version, using Ramda, really better than the pure-JavaScript mostly-functional version we used at first?

Obviously, I think the answers there are yes. The Ramda version there at the end is _way_ better than the imperative version, and substantially better than even the first "functional" JavaScript versions we wrote.

For me, at least, the big takeaway here is this: we just built a small but reasonable transformation of data out of a bunch of really small pieces. That has two big consequences -- consequences we've talked about all along the way, but which you've now seen in practice:

  1. Those pieces are easy to test. If something isn't working, I can easily take those pieces apart and test them individually, or test the result of any combination of them. As a result, I can test any part of that pipe chain, and I can _fix_ pieces independent of each other. No part depends on being in the middle of a looper where transformations are done to other parts.

  2. Because they're small and do one simple things, I can recombine those pieces any way I like. And you see that in the Ramda examples in particular: most of what we're doing in those examples is not even something we wrote ourselves. They're also _really_ basic building blocks, available in basically every standard library.

One last thing: if you're curious about performance… you should know that it does matter for data at scale. In my tests (which are admittedly extremely unscientific; unfortunately, I couldn't get JSPerf running nicely with this particular set of variations), I found that the time it took to run these varied depending on the approach _and_ the library. With a ~10k-record data set:

  * The imperative version, unsurprisingly, was the fastest, taking ~16 - 17ms.
  * After that, the chained lodash version and the pure-JS version were comparable, at ~32 - 36ms, or around twice as long to finish as the imperative version.
  * The plain lodash version was consistently a _little_ slower yet, at ~38 - 43ms.
  * Ramda is _slow_: both variations consistently took over 90ms to finish.

Those differences added up on larger data sets: dealing with ~10,000,000 records, the times ranged from ~12s for the imperative version, to ~15s for the lodash and pure-JS variants, to ~50s for the Ramda version.

They were all pretty darn quick. Compilers, including JavaScript JITs, are incredibly smart. Mostly you can just trust them; come back and profile before you even _think_ about optimizing things. But you _should_ know the performance characteristics of different libraries and consider the implications of what the language does well and what it doesn't. Ramda is likely slower because of the way it curries every function -- something that works well in languages with native support for it, e.g. F♯ or Elm or Haskell, but imposes a penalty in languages which don't… like JavaScript. That said, if you're not in the habit of processing tens of thousands of records, you're probably okay using any of them.
