# A Fast, Flexible JSON Library for Java

_Captured: 2017-04-19 at 08:43 from [dzone.com](https://dzone.com/articles/dealing-with-json-in-a-new-way?oid=twitter&utm_content=buffer10e67&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Don't we already have objectMapper.readValue? Why another JSON library? I found myself stuck in a couple of situations, and [jsoniter ](http://jsoniter.com/)(json-iterator) really worked for me:

  * **Working with PHP**: You want to int, so they might give you 100 or "100". You want an object, so they might give you [] as an empty object.

  * **Parsing large JSON streams**: Parsing a large stream of JSON, then extracting only what you need from the jungle.

  * **Cannot bind**: The JSON is organized in a key/value form, and it cannot bind directly to my object model.

Also, [jsoniter](http://jsoniter.com) is much much faster than existing libraries (jackson, gson, you name it). Third party benchmarking is welcome. Here are the [shameless self-benchmarking](http://jsoniter.com/benchmark.html) results for data binding 1kb of JSON:

![Image title](https://dzone.com/storage/temp/3871852-java1.png)

> _The advantages of jsoniter come from these innovations:_

  * **[Any type](https://github.com/json-iterator/java/blob/master/src/main/java/com/jsoniter/any/ObjectLazyAny.java)**: Capture raw bytes as the Any type. Parsing is done lazily. Any can be used like a PHP array or JavaScript Object and be weakly typed.

  * **[Iterator abstraction](https://github.com/json-iterator/java/blob/master/src/main/java/com/jsoniter/JsonIterator.java)**: Take the JSON input stream as an iterator like object. You can walk through the graph in a streaming way, just like iterating collections. It's similar to the gson API, but greatly simplified.

  * **[Trie-tree](https://github.com/json-iterator/java/blob/master/src/main/java/com/jsoniter/CodegenImplObject.java)**: The biggest drawback (and maybe its biggest benefit) of JSON is the string typed field name. It is time-consuming to bind object fields by comparing strings. [Jsoniter](http://jsoniter.com) uses tri-tree to boost the performance.

  * **[Code generation](http://jsoniter.com/java-features.html#performance-is-optional)**: All decoder/encoder logic can be code generated. You have plenty of options available, such as reflection/dynamic codegen/static codgen. 

  * **[Only pay for the feature you want](https://github.com/json-iterator/java/blob/master/src/main/java/com/jsoniter/DynamicCodegen.java)**: Taking InputStream as an input is slower than byte[]. Traditional parsers use a virtual method or feature flags to generalize, which is a performance killer. Jsoniter uses dynamic class shadowing to switch implementations.

  * **[Required field validation](http://jsoniter.com/java-features.html#validation)**: When you parse an object of int field. You can not tell the field is zero because no input from JSON or the field is indeeded specified as zero. Jsoniter implemented required field tracking using bit mask, now you can know.

A lot of work has been done to make sure jsoniter is the fastest out there. Benchmarking aside, what most people truly want is to get their job done fast. Here is an example to show you how flexible the API is:
    
    
    [1024, {"product_id": 100, "start": "beijing"}]
    
    
    ["1025", {"product_id": 101, "start": "shanghai"}]

Each line is an object. The first element is the order ID, and the second element is the order details. Notice:

  * There are many lines, and reading them all in once will lead to memory issues.

  * Some order IDs are ints and some are strings. This is very common when working with PHP.

  * The order details have many fields and need object binding.

In 6 lines, we have solved all the problems.

  * JsonIterator.parse takes InputStream as the input and parses everything in a stream.

  * ReadAny returns an instance of Any. The parsing is lazily done when actually getting the field, which makes it simple and performant.

  * BindTo(orderDetails): Data binding can reuse existing objects

This example is just a demo of the flexibility. It might seems overly complex, it will be handy when you need it though. For everyday use, just remember two lines:

I hope you are interested. This library is new, so bug reports or pull requests should be submitted to <https://github.com/json-iterator/java>. The Golang version will be available soon.
