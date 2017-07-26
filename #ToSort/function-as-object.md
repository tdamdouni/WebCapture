# Function-as-Object

_Captured: 2017-02-17 at 19:03 from [dzone.com](https://dzone.com/articles/functionasobject?edition=271881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-17)_

Make the transition to Node.js if you are a Java, PHP, Rails or .NET developer with [these resources to help jumpstart your Node.js knowledge](https://dzone.com/go?i=182121&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20127833%26PluID%3D0%26ord%3D%5Btimestamp%5D) plus pick up some development tips. Brought to you in partnership with [IBM](https://dzone.com/go?i=182121&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20127833%26PluID%3D0%26ord%3D%5Btimestamp%5D).

In programming, the fundamental notion of an object is the bundling of data and behavior. This provides a common data context when writing a set of related functions. It also provides an interface for manipulating the data that allows the object to control access to that data, making it easy to support derived data and prevent invalid modifications of data. Many languages provide explicit syntax to define classes, which act as definitions for objects. But if you have a language with first-class functions and closures, you can use these constructs to create objects using the 'function-as-object' pattern (originally described by Eugene Wallingford).

Here is an example of a simplistic person object, done using the function-as-object style in JavaScript.

The outer form of a function-as-object is a function, which is called as a constructor function. The result of the call is, in essence, a hashmap of functions which acts as a method selector. This map captures the state of any variables in the function in a closure, allowing the data to persist beyond a single function invocation. This result hashmap can be treated like a classical object.

Looking at the function-as-object from a classical OO point of view:

  * The fields of the object are represented by the parameters to the constructor function `(name)`together with the local variables `(birthday)`.
  * The methods of the object are the functions nested within the constructor function. Like object methods, they can freely call each other and manipulate the data in these locally scoped variables (fields).
  * Nothing outside the constructor function can access the variables, preserving data encapsulation.
  * The public methods of the object are those functions that are present in the result hashmap.
  * Any functions nested inside the constructor function, but not present in the result hashmap, are private methods.
  * The names of the public methods are the keys of the result hashmap, not the names of the functions within the constructor function. I prefer to keep the keys and function names the same to avoid confusion (although it can be handy to alias functions if needed).

A common alternative implementation of this pattern is to return a function as the method selector rather than the hashmap which is the natural method selector in JavaScript. To use a function as the method selector, I'd return a function whose first argument is the name of the method to invoke. The function body then switches on that value (see [Wallingford](http://www.cs.uni.edu/~wallingf/patterns/envoy.pdf) for more on this).

The function-as-object approach has been around for a long time. I've seen it described in lisp many times, and it's been widely used in JavaScript (until ES6, JavaScript had a very limited notion of classes). It's often used as an argument that a specific syntax for classes isn't necessary, which is the equivalent of object-aficionados arguing that you don't need first class functions when you can write a class with a single "call" method. As a consequence, many people in the JavaScript world argue against using the ES6 class syntax. Personally, I like having both first class functions and first-class classes and prefer ES6's class syntax.

Learn why developers are gravitating towards Node and its ability to [retain and leverage the skills of JavaScript developers](https://dzone.com/go?i=182122&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20127834%26PluID%3D0%26ord%3D%5Btimestamp%5D) and the ability to deliver projects faster than other languages can. Brought to you in partnership with [IBM](https://dzone.com/go?i=182122&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20127834%26PluID%3D0%26ord%3D%5Btimestamp%5D).
