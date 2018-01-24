# Calling Into Javascript From a WebAssembly Module

_Captured: 2017-12-21 at 23:06 from [dzone.com](https://dzone.com/articles/webassembly-calling-into-javascript-from-bare-bone?edition=347111&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-21)_

In [my previous article](https://dzone.com/articles/webassembly-emscripten-side-module), we explored the idea of creating a bare-bones WebAssembly module with no Emscripten plumbing. In that article, we were able to call into the module from JavaScript but we didn't get into the reverse:

How does one call into JavaScript from a module?

In this article, we're going to try and get a WebAssembly module to call a method that's defined in our JavaScript.

In order to compile C code, when the method being used isn't in the source code, you need to define the method signature using the extern keyword as shown in the following example:

You can run the following command line to build the wasm file:

`emcc test.c -s WASM=1 -s SIDE_MODULE=1 -O1 -o test.wasm`

To define the method in our JavaScript, we just need to add it to the env object that is part of the main object that we pass as the 2nd parameter to the `WebAssembly.instantiate` method:

Just like how we needed to add an underscore character before the method name when calling into the module from JavaScript, we also need to include an underscore before the method name here.

The following is the full HTML/JavaScript for our example module:
