# WebAssembly: Web Workers

_Captured: 2018-01-04 at 15:02 from [dzone.com](https://dzone.com/articles/webassembly-web-workers?edition=347159&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202018-01-04)_

This is a continuation of a series of articles exploring how we can build and work with WebAssembly modules using Emscripten. The previous articles are not required reading to understand what we're going to cover today but, if you're curious, you can find them here:

Today we're going to continue using a bare-bones WebAssembly module_ (no Emscripten built-in helper methods)_ just to keep things as clear as possible as we examine HTML5 Web Workers.

Web Workers allow JavaScript code to run in a separate thread from the browser window's UI thread. This allows long-running scripts to do their processing without interfering with the responsiveness of the browser's UI.

Because Web Workers are running in a separate thread from the UI, the worker threads have no access to the DOM or other UI functionality. In addition, Web Workers are not intended to be used in large numbers and are expected to be long-lived since they have a high start-up performance cost and high memory cost per worker instance.

WebAssembly modules can be loaded in either the UI thread or in a Web Worker. You would then take the compiled module and pass that to another thread, or even another window, by using the **postMessage **method.

Since you will only be passing the compiled module to the other thread, you can call **WebAssembly.compile** rather than WebAssembly.instantiate to get just the module.

The following is some code that will request the wasm file from the server, compile it into a module, and then pass the compiled module to a Web Worker:
    
    
    fetch("test.wasm").then(response => 

The code above will also work in a Web Worker if you wanted to do this in reverse _(load and compile the module in a Web Worker and then pass the module to the UI thread)_. The only difference would be that you would use **self**.postMessage as opposed to g_WebWorker.postMessge in the example above.

The following is some example code that creates a Web Worker in the UI thread, loads the wasm file, and then passes the compiled module to the Web Worker:
    
    
        <input type="button" value="Test" onclick="OnClickTest();" />
    
    
          g_WebWorker.onerror = function (evt) { console.log(`Error from Web Worker: ${evt.message}`); }
    
    
          g_WebWorker.onmessage = function (evt) { alert(`Message from the Web Worker:\n\n ${evt.data}`); }
    
    
          fetch("test.wasm").then(response =>
    
    
            g_WebWorker.postMessage({ "MessagePurpose": "AddValues", "Val1": 1, "Val2": 2 });

The following is the content of our **WebWorker.js** file:
    
    
         'table': new WebAssembly.Table({ initial: 0, element: 'anyfunc' })
    
    
    self.onmessage = function (evt) {
    
    
        var iResult = g_objInstance.exports._add(objData.Val1, objData.Val2);
    
    
        self.postMessage(`This is the Web Worker...The result of ${objData.Val1.toString()} + ${objData.Val2.toString()} is ${iResult.toString()}.`);
    
    
        WebAssembly.instantiate(objData.WasmModule, g_importObject).then(instance => 

The following is the C code as well as the command line needed to turn the code into a WebAssembly module for today's article:

`emcc test.c -s WASM=1 -s SIDE_MODULE=1 -O1 -o test.wasm `

### **Inline Web Workers**

While reading about using Web Workers with WebAssembly modules, I ran across one comment about how this adds yet another network request _(one for the wasm file and now another for the Web Worker's JavaScript file)_.

The following may not work for every situation, especially if the Web Worker's code is large or complex, but there is a way to create an inline Web Worker by using a **Blob **object.

You can pass a Blob object a string of JavaScript but I found that using a literal string was difficult to work with and that having a section in the HTML felt more natural which is why we're using a custom Script tag in the sample code below.

The following is an example of how you can create an inline Web Worker:

### **Summary**

One nice thing about Web Workers is that they also have access to IndexedDB which means the worker thread can handle caching too if you wish to work with WebAssembly modules entirely from the worker thread.

We didn't dig into caching a WebAssembly module in this article but, if you're interested, you can check out our previous article: [WebAssembly - Caching to HTML5 IndexedDB](https://dzone.com/articles/webassembly-caching-to-html5-indexeddb)

The focus of today's article with Web Workers was just around what was needed when working with WebAssembly modules. If you'd like to know more about Web Workers, I have several articles that may be of interest:

  * [A DZone Refcard on HTML5 Web Workers](https://dzone.com/refcardz/html5-web-workers) _(covers what's in the two articles above but also introduces additional topics like Inline Web Workers)_
