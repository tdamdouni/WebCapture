# Node.js Crash Course

_Captured: 2017-12-01 at 02:30 from [dzone.com](https://dzone.com/articles/nodejs-crash-course?edition=339014&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-30)_

## Introduction

I've been doing Node full-time at work and noticed a lot of other people lacking a centralized resource to get up and running quickly. There are a lot of wonderful resources out there for Node that are only a Google search away, but, hopefully, this document should get you coding quickly and help you to communicate effectively with other Node developers.

I've tried to write this list in order of the most important things you need to know. Feel free to skip around.

## Node Version Manager (NVM)

Node changes often. To quickly change which version you're using, install [NVM](https://github.com/creationix/nvm). I've put `nvm use stable` in my `.bash_profile` so whenever I open a terminal, it uses the latest version. If this is confusing or doesn't work, simply download the latest installable from [nodejs.org](https://nodejs.org/en/).

## Running and Testing Node

Open a command line and type `node`. To get out, on your keyboard press Control + C. While in the Node terminal, you can write JavaScript, and import modules to test them.

To run a JavaScript file, simply `cd` to the directory of the code, and in your command line, type `node yourfile.js`.

## Modules

To share code, you use modules. There are 2 types of modules: CommonJS and ES6 (ignore AMD for now). CommonJS is what Node started with, and then browsers adopted ES6. Node 9 will officially adopt ES6 modules, but, for now, ignore that and focus on CommonJS modules since they work with Node, both old and new.

The easiest way is to define functions/variables, then at the very bottom, put them in a list.

### Simple
    
    
    console.log("cow:", cow());

### Big One

When you have a higher module that imports a bunch of child ones, you can enforce the user to require subfolders like this:

This is fine. But, another way to suggest what the user should use is to only expose that in a higher module:

### What Are These Weird, Empty Functions at the Top of My File?

If you see things like:

Where the majority of the code is in the `. . .` part, that's called an Immediately Invoked Function Expression. It's an old pattern used in the client-side/browser and is not needed or used in Node. Simple remove the top/bottom parts and manually expose the functions/variables you wish to use.

### Modify Dependency Injection

If you see this version:

That's the browser's way of performing dependency injection, specifically to help remove global variables. While things like `window` and `document` are globals, global variables make things hard to test, so this allows you to pass those values in during testing and runtime. Refactor the functions that use those globals as function parameters.

## Functions vs. Arrow Functions

There are a variety of ways to define functions in JavaScript. The 2 most common ways in Node are old sch00l function declarations and arrow functions.

### Old Functions

The old way of defining functions is:

The powers that these named function declarations have are:

  1. You can forward reference them, meaning you can call them from higher up in the code before they're actually defined in the file if you write imperative code.
  2. They have a built-in `arguments` property that is an array of the arguments passed into the function.
  3. They have a `this` keyword which allows various forms of Object Orientated Programming.
  4. Older browsers provide more informative stack traces because the function name is included in the stack trace vs. an anonymous function (Node doesn't have this problem).

### Arrow Functions

None of those things are needed anymore, especially in Node where stateful OOP doesn't really exist in stateless server applications. That said, many developers still use classes.

Arrow functions have the following differences:

  1. No `this`, instead they adopt whatever scope they are in. If you never use `this` or scope, then you have none of those problems.
  2. No `arguments` property. If you wish to use something like that, you can define a function by using rest parameters, like `addNumbers(...numbers)`. This makes the `numbers` property an Array of arguments; otherwise, you'll have an empty Array.
  3. They are treated like anonymous JavaScript functions, which means they are normal variables and you cannot forward reference them. That problem only occurs if you write imperative code. Calling an one arrow function from another arrow function works fine.
  4. They automatically return values unless you add {} to the function block. This removal of the need to manually write `return` combined with the removal of the need to write the word `function` leads to much smaller functions.

You should use Arrow Functions unless you know why you should be using older functions.

### Arrow Functions With One Parameter

Typically, you write an Arrow function with a parameter like this:

However, if you just have one argument, the () are optional:

### Arrow Function Line Length

While smaller, two new problems are created using lots of arrow functions. The first is, the line length can still get pretty long as you try to put everything on one line. Some [ESLint](https://eslint.org/) rules written by jerks yell about this. The second is you'll start having functions return functions, especially with Promises, and it gets unwieldy to read.

You cannot break them into multiple lines after the equal:

But you can line break after the fat arrow:

This helps with nested functions since we don't have pipe operators like [Elm](http://elm-lang.org/examples/pipes/code) or [Elixir](https://elixir-lang.org/getting-started/enumerables-and-streams.html#the-pipe-operator).

### Common Pitfall

Debugging one-line arrow functions that are composed together can be a bit challenging. You have three options here.

The first is to break it out into a multi-line, imperative style function:

The challenge is to remember to use the `return` keyword to return the result once you go back to multiple line arrow functions.

The second option is to use an `||` (or) statement to log your information first. Since `console` is a noop ( a function that returns no value), it'll return undefined, and trigger the code to the right of the `||` operator.

The third option is to use a modern IDE like [Visual Studio Code](https://code.visualstudio.com/) that supports adding breakpoints on columns.

## Truthy/Falsey

### if (thing)

JavaScript has lax operators for Boolean evaluation. In short, they suck, hence we call them "truthy" and "falsey." [They aren't very exact](https://j11y.io/javascript/truthy-falsey/).

You have a few options:

  1. Learn them and look smart, yet have to continually remind your coworkers.
  2. Ignore them and don't go down that path and use Lodash.

For example, this prints out "it's true, homey":

So does this:

The same holds true for nothing using equality vs strict equality in JavaScript:

Ignore it and all the weird edge cases. Create predicate functions using [Lodash](https://lodash.com/docs/4.17.4), and your problems go away, and your code works in all browsers and in Node versions.

## Nots

You'll occasionally see people do `if(!thing) {`. It basically means `!==true`.

## Equality

Comparison operators in JavaScript are broken. You can [learn the differences](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators) if you care to, but they are too hard to remember and don't really help you write better code. Don't use two equals, use three:

## Asynchronous Programming

JavaScript, unlike other programming languages, is asynchronous by default. [Learn more](http://jessewarden.com/2017/11/asynchronous-programming.html) to understand how to avoid creating race conditions as well as helpful tips if you come from C#. If you're from Scala, JavaScript's Promises are like Scala's Futures.

In short, JavaScript does not stop or "block" on a line of code while an asynchronous operation such as an HTTP request, file read, or database call is run. Instead, you can give it a function to call later when it's done, and your code keeps running in the current call stack. I've written an article that hopefully gives you [clear examples of asynchronous programming](http://jessewarden.com/2017/11/asynchronous-programming.html).

## Callbacks vs. Promises

The old way to code in Node is using callbacks. The new way is Promises. Since it is an opinion, Node continues to support callback APIs and create new APIs using callbacks. While callbacks can result in [callback hell](http://callbackhell.com/), so can [Promises](http://solutionoptimist.com/2013/12/27/javascript-promise-chains-2/).

Either way, callbacks sadly are noops, meaning they don't return a value. We don't do that in functional programming, and neither should you. While newer versions of node support [promisify](http://2ality.com/2017/05/util-promisify.html), you should be using Promises because:

  1. They always return a value.
  2. They have built-in `try/catch`
  3. They are a native, finite state machine.
  4. They use Left/Right functional programming error handling fall through.

This leads to easier unit testing, more composable functions, and easier to debug code.

Best article to learn Promises is to learn [how Promises are used wrong](https://pouchdb.com/2015/05/18/we-have-a-problem-with-promises.html).

That said, if callbacks are easier for you, and you're stuck with Promise based code, Node 9 has a way to [convert them back to callbacks](https://nodejs.org/api/util.html#util_util_callbackify_original).

## Command Line

To build command line Node apps, check out [Commander](https://github.com/tj/commander.js/).

## Object-Oriented Programming

The basics of classes with inheritance work in the latest browser and Node without the need of a transpiler/compiler using ES6. However, transpilers offer a lot of nice features that, if you're from an OOP background, it's worth your time to check out.

For the basics, check out the [Babel compiler](https://babeljs.io/). For a language, compiler, and simpler parallelism functionality, with runtime exceptions for non-prod code, check out [Google's Dart](https://www.dartlang.org/). For another great typed language with a helpful compiler, check out [Microsoft's TypeScript](https://www.typescriptlang.org/). [Facebook has Flow](https://github.com/facebook/flow) in much the same vein.

Be aware, a lot of the marketing of the above tools target browser developers, but many work fine for Node. The beauty of Node is you "can just write code and run it" without waiting for a recompile, but for many, this isn't a problem.

## Functional Programming

You have two options: use libraries or a transpiler.

For libraries, [Folktale v2](http://folktale.origamitower.com/api/v2.0.0/en/folktale.html) follows the [Fantasy Land spec](https://github.com/fantasyland/fantasy-land). [Lodash](https://lodash.com/) has both functional methods as well as array comprehensions, and low-level JavaScript predicates.

If the mutable state and impurity of JavaScript is too much, you can use Facebooks' OCAML influenced [Reason](https://reasonml.github.io/), or Haskell influenced [PureScript](http://www.purescript.org/).

## Unit and Integration Testing

To unit test, the four main test runners are [Tape](https://github.com/substack/tape), [Jasmine](https://jasmine.github.io/), [Mocha](https://mochajs.org/), and [Jest](https://facebook.github.io/jest/). I like Mocha. Mocha has an assertion library, [Chai](http://chaijs.com/). For code coverage, use [Istanbul](https://istanbul.js.org/). To prevent unit tests from accidentally becoming integration tests that make HTTP calls and other HTTP exceptions, use [Nock](https://github.com/node-nock/nock). For mocking and spies (you poor thing) use [Sinon](http://sinonjs.org/). For integration testing, check out [Supertest](https://github.com/visionmedia/supertest).
