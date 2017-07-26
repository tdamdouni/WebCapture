# Declarative vs. Imperative Programming for the Web

_Captured: 2015-11-19 at 14:59 from [codenugget.co](http://codenugget.co/2015/03/05/declarative-vs-imperative-programming-web.html)_

Unless you have been living under a rock, you might have noticed a programming paradigm shift in the last couple of years. These days, the cool kids are all doing [Functional Programming](http://en.wikipedia.org/wiki/Functional_programming) (FP) while embracing [immutable data structures](http://en.wikipedia.org/wiki/Immutable_object), [higher-order functions](http://en.wikipedia.org/wiki/Higher-order_function), and [tail recursions](http://en.wikipedia.org/wiki/Tail_call).

The overall concept isn't new at all, but it gained a lot of traction with the rise of the more modern FP languages like [Haskell](https://www.haskell.org/) or [Clojure](http://clojure.org/), and even "traditional" programming languages like [Java](https://www.java.com) adding more and more [FP-orientated features](http://www.drdobbs.com/jvm/lambda-expressions-in-java-8/240166764) in their recent versions. Another example: [Swift](https://developer.apple.com/swift/), Apple's new programming language and designated successor of [Objective-C](http://en.wikipedia.org/wiki/Objective-C), took [quite a few hints](http://www.reddit.com/r/haskell/comments/27nez1/apple_invents_maybe/) from Haskell in the overall language design[1](http://codenugget.co/2015/03/05/declarative-vs-imperative-programming-web.html). You can't deny, that FP does have some really huge advantages over [Object-orientated Programming](http://en.wikipedia.org/wiki/Object-oriented_programming) (OOP). Avoiding state, mutability and side-effects is a big step towards more robust and less fragile applications, especially in today's world, where even our mobile phones are equipped with multi-core CPUs for parallelizing computations.

So is our good ol' pal OOP slowly fading into oblivion? Of course, it's not! It's still the most comprehensible and approachable paradigm, and the way most of us found into programming. Whenever there is a discussion about FP vs. OOP, you'll likely also hear something about _Declarative vs. Imperative Programming_. Let's talk about both concepts and their implications in your everyday life as a web developer.

## Declarative vs. Imperative

When you look on the internet for a definition, you might find something like [this](http://foldoc.org/declarative+language) (emphasis mine):

> Any relational language or functional language. These kinds of programming language describe **relationships between variables in terms of functions or inference rules**, and the language executor (interpreter or compiler) **applies some fixed algorithm to these relations to produce a result**.
> 
> Declarative languages contrast with imperative languages which **specify explicit manipulation of the computer's internal state**; or procedural languages which specify an explicit sequence of steps to follow.

Wow, quite a handful. But it really captures the essence. If this is all highbrow computer science speak to you, there's an even more compact version on which most of the internet agrees upon: _Imperative programming_ is about telling your machine **how** to do something, while _Declarative programming_ really is about telling your machine **what** you would like to happen in order to do something.

Sounds esoteric, right? Let's dive into an example.

### Example: Crunching the numbers

Say, we want to calculate the sum of the squares of some consecutive natural numbers.

Yeah I know... MATH! But bear with me, this is a simple one. We'll come to the more interesting stuff later on ;) Let's see how to tackle this in the traditional, imperative way with JavaScript.
    
    
    function sumOfSquares(nums) {
      var i, sum = 0, squares = [];
      for (i = 0; i < nums.length; i++) {
        squares.push(nums[i]*nums[i]);
      }
    
      for (i = 0; i < squares.length; i++) {
        sum += squares[i];
      }
    
      return sum;
    }
    
    console.log(sumOfSquares([1, 2, 3, 4, 5]));
    

This looks familiar! We `for`-loop over the elements, calculate the squares and push them into a new array. Then, we `for`-loop over that array to calculate the sum and return it. Although almost all of us can relate to it, this approach acutally has some problems. It's not that easy to read and new members of your development team might need some time to figure out what this code does. And don't get me started on `for`-loops themselves, because we all ran into [out of bounds errors](https://www.google.com/search?q=out%20of%20bounds%20error&rct=j) at least once in our lives as developers.

Let's see a declarative / functional approach done in Clojure:
    
    
    (defn square-of [n]
      (* n n))
    
    (defn sum-of-squares [nums]
      (reduce + (map #(square-of %) nums)))
    
    
    (sum-of-squares '(1 2 3 4 5))
    

_"Are you drunk? This isn't readable at all!"_. Okay, if you're new to Clojure and its weird bracket syntax, I'll give you that. `sum-of-squares` is the function which we'll feed our list of numbers. A Clojure function consists of one or more, mostly nested [expressions or forms](http://clojure.org/evaluation). In order to understand a nested form, you have to read it _"inside-out"_. Take a look at line 5. Even if you might not fully understand it, you see three nested forms: It starts at `square-of`, goes then into `[map`](http://clojuredocs.org/clojure.core/map) and finally into `[reduce`](http://clojuredocs.org/clojure.core/reduce).

Luckily, we can rewrite this whole thing in JavaScript.
    
    
    function sumOfSquares2(nums) {
      return nums
        .map(function(num) { return num * num; })
        .reduce(function(start, num) { return start + num; }, 0)
      ;
    }
    
    console.log(sumOfSquares([1, 2, 3, 4, 5]));
    

Aaah, we're back in our comfort zone ;) Here's what we do: We start with our array of numbers, chain both `[Array.prototype.map`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/map) and `[Array.prototype.reduce`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce) methods on it, and return the result. Not only is it more readable as the imperative approach, it is also much more concise. And most important: We're **describing what** we want to happen instead of providing details on **how** to do it.

This really is the whole idea. Instead of thinking about `for`-loops and indices, we just care about two things:

  1. Take every number and calculate its square (_"apply a **mapping** function, which happens to calculate the square of a number, to each element of the array"_)
  2. Calculate the sum of all those squares (_"**reduce** the array through a function, which happens to calculate the sum of two numbers, into a single number"_)

If you still can't wrap your head around it, don't be frustrated. It takes time to fully grasp it. A more practical example will follow shortly.

## Back to the web

Let's glance one last time at our previous example. With the declarative approach we were basically **processing sequences or streams of input values** (our array of numbers) via method-chains (or nested functions in Clojure), where we used **the output one method / function as input** of the following method / function, and so on. This is, by the way, one of the most important concepts of Functional Programming. How can we take this to the web?

Take, for example, our old friend [jQuery](http://jquery.com/).
    
    
    jQuery(function($) {
    
      var username = '';
      var password = '';
    
      // Disable the button at start
      $('#signup-button').attr('disabled', true);
    
      // Email field
      $('#email-field').on('blur', function() {
        username = $(this).val();
        if (username == '') {
          $('#email-error').html('Please enter email address');
          $('#signup-button').attr('disabled', true);
        } else {
          checkValues();
        }
      });
    
      // Password field
      $('#password-field').on('blur', function() {
        password = $(this).val();
        if (password == '') {
          $('#password-error').html('Please enter password');
          $('#signup-button').attr('disabled', true);
        } else {
          checkValues();
        }
      });
    
      // Both fields
      function checkValues() {
        if (username != '' && password != '') {
          $('#email-error').html('');
          $('#password-error').html('');
          $('#signup-button').attr('disabled', false);
        }
      }
    
    });
    

Yep, we've all seen this and probably even wrote jQuery spaghetti-code [like this](https://github.com/b00giZm/fm-tags/blob/74aebf90cdd55d46f31c7f7fea041e2f676ca805/src/jquery.fmtag.js). We're enabling or disabling the sign up button depending on the values of both `#email` and `#password` input fields and showing some error messages in case that input is missing.

As you might have guessed, it's imperative (we're concerned with the **how** instead of the **what**), not very functional (we're changing the global state) and plain ugly. We can do better!

## Enter Functional Reactive Programming

_"What the what?"_ \- Fear not. Although [Functional Reactive Programming](http://en.wikipedia.org/wiki/Functional_reactive_programming) (FRP) is a whole topic on its own[2](http://codenugget.co/2015/03/05/declarative-vs-imperative-programming-web.html), just think of it as a fancy way of transforming asynchronous events such as `click` or `blur` into streams of values, which you can then process in a functional manner like our simple numbers array.

There are many libraries for all different kinds of programming languages out there for implementing FRP, but the one I use most and I'm most familiar with is [Bacon.js](https://github.com/baconjs/bacon.js/), so I'll use it in the following examples.

Let's get declarative, should we? We'll start with just the email field.
    
    
    $('#email-field')
      .asEventStream('blur')
      .map(function(e) { return !e.target.value; })
      .assign($('#signup-button'), 'attr', 'disabled')
    ;
    

What is happening here? Bacon.js provides a jQuery plugin, which lets you call `[asEventStream`](http://codenugget.co/2015/03/05/\(https://github.com/baconjs/bacon.js/) on wrapped elements in order to create a stream for a given event (in this case `blur`). DOM elements typically emit [event](https://developer.mozilla.org/docs/Web/API/Event) objects into their stream, which can then be transformed by a `[map`](https://github.com/baconjs/bacon.js/#observable-map) method, just like in our previous math example. Last not least, there's `[assign`](https://github.com/baconjs/bacon.js/#property-assign), which takes calls the method of a given object with its input as argument(s). In this case, it'll either enable or diable the button element through jQuery's `[attr`](http://api.jquery.com/attr/) method.

You can even get a bit more declarative by using named mapping functions instead of an anonymous one.
    
    
    function checkIfEmpty(e) { return !e.target.value; }
    
    $('#email-field')
      .asEventStream('blur')
      .map(checkIfEmpty)
      .assign($('#signup-button'), 'attr', 'disbled')
    ;
    

Isn't this much nicer? Even if you're not familiar with the Bacon.js API, you can somewhat guess what's going on by just looking at it.

But we won't stop here. Now that we have one or more event stream, it's almost trivial to combine them into a new stream with a custom combinator. That's exactly what we need in our case.
    
    
    function checkIfBothEmpty(noEmail, noPass) { return noEmail || noPass; }
    
    var email = $('#email-field').asEventStream('blur').map(checkIfEmpty);
    var password = $('#password-field').asEventStream('blur').map(checkIfEmpty);
    
    Bacon
      .combineWith(checkIfBothEmpty, email, password);
      .assign($('#signup-button'), 'attr', 'disabled')
    ;
    

Combining streams is a powerful feature which enables you to model fairly complex scenarios with very little code.

Now, the only thing that's missing is our error handling.
    
    
    function getEmailMessage(noEmail) {
      return noEmail ? 'Please enter email address.' : '';
    }
    
    function getPasswordMessage(noPassword) {
      return noPassword ? 'Please enter password.' : '';
    }
    
    email.map(getEmailMessage).assign($('#email-error'), 'html');
    password.map(getPasswordMessage).assign($('#password-error'), 'html');
    

That's it! Let's take a look at the whole thing.
    
    
    jQuery(function($) {
    
      function checkIfEmpty(e) { return !e.target.value; }
      function checkIfBothEmpty(noEmail, noPass) { return noEmail || noPass; }
    
      function getEmailMessage(noEmail) {
        return noEmail ? 'Please enter email address.' : '';
      }
    
      function getPasswordMessage(noPassword) {
        return noPassword ? 'Please enter password.' : '';
      }
    
      // Email field
      var email = $('#email-field').asEventStream('blur').map(checkIfEmpty);
      email.map(getEmailMessage).assign($('#email-error'), 'html');
    
      // Password field
      var password = $('#password-field').asEventStream('blur').map(checkIfEmpty);
      password.map(getPasswordMessage).assign($('#password-error'), 'html');
    
      // Both fields
      Bacon
        .combineWith(checkIfBothEmpty, email, password)
        .assign($('#signup-button'), 'attr', 'disabled')
      ;
    
    });
    

I prepared a [jsfiddle](https://jsfiddle.net/b00gizm/f011j2qo/1/) so you can see it in action.

Much cleaner, more readable and, above all, functional. You might argue that it's roughly the same amount than our imperative example. But think about this: What if we need to add one or more fields? Maybe a check box, or dialog box. Our imperative code would get more and more complex and confusing. But for our declarative case, we just had to create the additional event streams and combine them at the end. A real maintenance and extensibility win for us.

## Conclusion

Declarative Programming and/or adapting a functional style is not an easy topic, and some of its abstract concepts can be pretty baffling, even for experienced developers. But once you wrap your head around it and understand all its benefits, it can really help you to write code that's more both more expressive and more concise, even in OOP environments.

  1. If you want to learn more, I can only recommend the [Functional Programming in Swift](http://www.objc.io/books/) book written by the [objc.io](http://www.objc.io/) guys. Great, great stuff and one of the best books I read last year. [↩](http://codenugget.co/2015/03/05/declarative-vs-imperative-programming-web.html)

  2. There's a geat posting called [The introduction to Reactive Programming you've been missing](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754) for all of you, who want a more pragmatic introduction to that topic. [↩](http://codenugget.co/2015/03/05/declarative-vs-imperative-programming-web.html)
