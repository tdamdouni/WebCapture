# What Is JavaScript Obfuscation and When Is it Used?

_Captured: 2018-02-02 at 16:55 from [dzone.com](https://dzone.com/articles/obfuscation-what-is-obfuscation-in-javascript-why?edition=359105&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202018-02-01)_

In this post, we will discuss more obfuscation, where it is used, and its advantages.

![Image title](http://nodesimplified.com/wp-content/uploads/2018/01/obfuscation.png)

## What Is Obfuscation?

Obfuscation is the deliberate act of creating obfuscated code, i.e. **source or machine code** that is difficult for humans to understand. It is something similar to encryption, but a machine can understand the code and is able to execute: it.

The URLs we will use to obfuscate JavaScript code:

Obfuscation using [danstools.](http://www.danstools.com/javascript-obfuscate/)

Original code:

After obfuscation:

The output of both programs will be the same:

![Image title](http://nodesimplified.com/wp-content/uploads/2018/01/Screen-Shot-2018-01-07-at-12.23.37-PM.png)

Obfuscation can be used to hide business logic from the outside world, and it will drastically reduce the size of the file, so data transfers between server and client will be fast.

Minification is also a type of obfuscation where empty spaces are removed and variables will be renamed.

**Examples:**

## **Why Are Open Source Projects Obfuscated?**

  * Code size will be reduced
  * In JavaScript, download time will reduce

Most open source JavaScript projects are minified to reduce download time and code size. During minification, a minified file and a map file will get generated. Using a map file, actual code can be retrieved. The map file for the above Angular file will is here: <https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.6.5/angular.js.map>

## Why Obfuscation?

  * Code size will be reduced
  * Hide the business logic and your code from others
  * Reverse engineering is highly difficult
  * In JavaScript, download time will be reduced

Example:

![Obfuscation Example](http://nodesimplified.com/wp-content/uploads/2018/01/obfuscation-1-1024x344.png)

> _Obfuscation Example_

## Obfuscation == Encryption?

No, obfuscation != encryption.

  * In JavaScript, the browser can't execute encrypted code, whereas the browser will execute obfuscated code.
  * Encrypted code always needs decryption to be executed.
  * The obfuscated code doesn't require deobfuscation to execute.

Bottom line, it is good to obfuscate JavaScript code.

If you are developing enterprise application, Then I believe you can use a product like [Jscrambler](https://jscrambler.com/) for obfuscating your code. Reverse engineering of obfuscated code is really difficult hence we can hide the business logic and core logic from outside world.

Next article: [Start Using Map and Set In Your Javascript Application](http://nodesimplified.com/start-using-map-set-javascript-application/).
