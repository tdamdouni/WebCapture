# JavaScript: The Keyword ‘This’ for Beginners

_Captured: 2017-04-28 at 09:13 from [hackernoon.com](https://hackernoon.com/javascript-the-keyword-this-for-beginners-fb5238d99f85)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*UoOa49EaOxjNNG0J_3-e0A.jpeg?q=20)![](https://cdn-images-1.medium.com/max/800/1*UoOa49EaOxjNNG0J_3-e0A.jpeg)

Understanding the keyword `this` in JavaScript, and what it is referring to, can be a little complicated at times. Fortunately, there are five general rules that you can use to determine what `this` is bound to. There are some cases that these rules don't cover, but this should help you through the vast majority of cases… So, lets get started!

  1. The value of `this` is usually determined by a functions **execution context**. Execution context simply means _how_ a function is called.
  2. It's important to know that `this` may be different (refer to something different) each time the function is called.
  3. It's okay if #1 and #2 don't make sense yet. They will by the end of this article.

### #1 Global Object

Alright, we got the definition out of the way, now lets back up for a minute. Open up your Chrome Developer Console (Windows: Ctrl + Shift + J)(Mac: Cmd + Option + J) and type the following:
    
    
    console.log(this);

What do you get?
    
    
    // Window {...}

The `window` object! That's because in the global scope, `this` refers to the global object. In a browser, the global object is the `window` object.

To help you better understand why `this` refers to the `window` object, let's look at it more in depth. In your console, create a new variable and assign it to your name:
    
    
    var myName = 'Brandon';

We can access this new variable again by calling it:
    
    
    myName  
    // returns -> 'Brandon'

But did you know that every variable you declare in the global scope is attached to the `window` object? Lets test this:
    
    
    window.myName  
    // returns -> 'Brandon'
    
    
    window.myName === myName  
    // returns -> true

Cool. So earlier when we ran `console.log(this)` in global context, we know that `this` was being called on the global object. Since the global object in the browser is the `window` object, it makes sense that:
    
    
    console.log(this)  
    // returns -> window{...}

Now lets put `this` inside of a function. Recall our earlier definition: The value of `this` is usually determined by _how_ a function is called. With that in mind, what do you expect this function to return? In your browser console, copy the code below and hit enter.
    
    
    function test() {  
      return this;  
    }  
    test()

Once again, the keyword `this` returns to global (window) object. This happens because the keyword `this` is not inside of a declared object, so it defaults to the global (window) object. This concept may be a little tough to understand right now, but it should make more sense as you read on. One thing to note, if you are using strict mode, in the above example `this` will be `undefined`

### #2 Declared Object

When the keyword `this` is used inside of a declared object, the value of `this` is set to the _closest parent object_ the method is called on. Take a look at the code below where I declare the object `person` and use this inside the method `full`
    
    
    var person = {  
      first: 'John',  
      last: 'Smith',    
      full: function() {  
        console.log(this.first + ' ' + this.last);  
      }  
    };
    
    
    person.full();  
    // logs => 'John Smith'

To better illustrate that `this` is in fact referencing the person object, copy the below code into your browser console. It's mostly the same code as above, we're just going to `console.log(this)` instead, so we can see what it returns.
    
    
    var person = {  
      first: 'John',  
      last: 'Smith',    
      full: function() {  
        **console.log(this);**  
      }  
    };
    
    
    person.full();  
    // logs => Object {first: "John", last: "Smith", full: function}

As you'll see, the console returns the `person` object, proving `this` has taken the value of `person`

One last thing before we move on. Remember when we said the value of `this` is set to the _closest parent object_ the method is called on? What would you expect to happen in a scenario where we have nested objects? Take a look at the code sample below. We've got a `person` objected that contains the same `first`, `last`, and `full` keys as before. This time, we've also nested in the `personTwo` object. Person two contains the same three keys.
    
    
    var person = {  
      first: 'John',  
      last: 'Smith',  
      full: function() {  
        console.log(this.first + ' ' + this.last);  
      },  
      personTwo: {  
        first: 'Allison',  
        last: 'Jones',  
        full: function() {  
          console.log(this.first + ' ' + this.last);  
        }  
      }  
    };

What's going to happen when we call our two `full` methods? Let's find out.
    
    
    person.full();  
    // logs => 'John Smith'
    
    
    person.personTwo.full();  
    // logs => 'Allison Jones'

Again, the value of `this` is set to the _closest parent object_ the method is called on. When `person.full()` is invoked, inside the function `this` is bound to the `person` object. Meanwhile, when `person.personTwo.full()` is invoked, inside the `full` function, `this` is bound to the `personTwo` object!

### #3 The `New` Keyword

When the `new` keyword is used(a constructor), `this` is bound to the new object being created.

Lets look at an example:
    
    
    function Car(make, model) {  
      this.make = make;  
      this.model = model;  
    };

Above, you might guess that `this` is bound to the global object -- and you'd be correct…until we add in the keyword `new` . When we use `new` the value of `this` is set to an empty object, in this case, `myCar`.
    
    
    var myCar = **new **Car('Ford', 'Escape');
    
    
    console.log(myCar);  
    // logs => Car {make: "Ford", model: "Escape"}

For this to make sense, you need to understand what exactly the `new` keyword does. That's an entirely new topic in itself though. So for now, if you're unsure and you see the keyword `new`, just know that `this` is referring to a brand new, blank object.

### #4 Call, Bind, Apply

Last, but certainly not least, we can actually set the value of `this` explicitly with `call()`, `bind()`, and `apply()` . The three are very similar, but it's important to understand the minor differences.

Call and Apply are each invoked immediately. Call takes any number of parameters: this, followed by the additional arguments. Apply takes only two parameters: this, followed by an array of the additional arguments.

You following me still? An example should make this clearer. Look at the code below. We're trying to add numbers. Copy this into your browser console and call the function.
    
    
    function add(c, d) {  
      console.log(this.a + this.b + c + d);  
    }
    
    
    add(3,4);  
    // logs => NaN

The `add` function logs `NaN` (not a number). That's because `this.a` and `this.b` are undefined. They don't exist. And you can't add a number to something that is undefined.

Lets introduce an object to the equation. We can use `call()` and `apply()` to call the function with our object:
    
    
    function add(c, d) {  
      console.log(this.a + this.b + c + d);  
    }
    
    
    var ten = {a: 1, b: 2};
    
    
    add.call(ten, 3, 4);  
    // logs => 10
    
    
    add.apply(ten, [3,4]);  
    // logs => 10

When we use `add.call()` the first parameter is what `this` should be bound to. The subsequent parameters are passed into the function we are calling. Thus, in `add()` , `this.a` refers to `ten.a` and `this.b` refers to `ten.b` and we get `1+2+3+4` returned, or 10.

`add.apply()` is similar. The first parameter is what `this` should be bound to. The subsequent parameter is an array of arguments to be used in the function.

What about Bind? The parameters in `bind()` are identical to `call()` but `bind()` is not invoked immediately. Instead, `bind()` returns a function with the context of `this` bound already. Because of this, `bind()` is useful when we don't know all of our arguments up front. Again, an example should help with your understanding:
    
    
    var small = {  
      a: 1,  
      go: function(b,c,d){  
        console.log(this.a+b+c+d);  
      }  
    }
    
    
    var large = {  
      a: 100  
    }

Copy the above into your console. Then call
    
    
    small.go(2,3,4);  
    // logs 1+2+3+4 => 10

Cool. Nothing new here. But, what if we want to use the value of `large.a` instead? We can use call/apply:
    
    
    small.go.call(large,2,3,4);  
    // logs 100+2+3+4 => 109

Now, what if we don't know all 3 arguments yet? We can use bind:
    
    
    var bindTest = small.go.bind(large,2);

If we console.log our variable above, `bindTest` , we can see what we're working with
    
    
    console.log(bindTest);  
    // logs => function (b,c,d){console.log(this.a+b+c+d);}

Remember, with `bind` a function is returned that already has `this` bound! So our `this` has been successfully bound to our `large` object. We've also already passed in our second argument as the number 2. Later, when know the rest of the arguments we can pass them in:
    
    
    bindTest(3,4);  
    // logs 100+2+3+4 => 109

For clarity, here is all of the code together in one block. Look it over, and copy it into your console to really understand what is happening!
    
    
    var small = {  
      a: 1,  
      go: function(b,c,d){  
        console.log(this.a+b+c+d);  
      }  
    }
    
    
    var large = {  
      a: 100  
    }
    
    
    small.go(2,3,4);  
    // logs 1+2+3+4 => 10
    
    
    var bindTest = small.go.bind(large,2);
    
    
    console.log(bindTest);  
    // logs => function (b,c,d){console.log(this.a+b+c+d);}
    
    
    bindTest(3,4);  
    // logs 100+2+3+4 => 109

### #5 Arrow Functions

This is such a big topic in itself that I wrote an entire article on it. I'll be releasing it on 4/28 and updating this link at that time.

### Conclusion

You made it! Under most circumstances you should now be able to deduce what exactly `this` is referring to! Remember a few things:

  1. The value of `this` is usually determined by a functions **execution context**.
  2. In the global scope, `this` refers to the global object (the window object).
  3. When the `new` keyword is used(a constructor), `this` is bound to the new object being created.
  4. We can set the value of `this` explicitly with `call()`, `bind()`, and `apply()`
  5. Arrow Functions don't bind `this` -- instead `this` is bound lexically (i.e. based on the original context)

#### **❤ If this post was helpful, please hit the little heart! And don't forget to check out my other recent articles:**
