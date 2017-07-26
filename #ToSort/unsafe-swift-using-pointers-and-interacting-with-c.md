# Unsafe Swift: Using Pointers And Interacting With C

_Captured: 2017-01-08 at 22:13 from [www.raywenderlich.com](https://www.raywenderlich.com/148569/unsafe-swift)_

If you're new here, you may want to subscribe to my [RSS feed](http://www.raywenderlich.com/feed/) or follow me on [Twitter](http://twitter.com/rwenderlich). Thanks for visiting!

![UnsafeSwift-feature](https://koenig-media.raywenderlich.com/uploads/2017/01/UnsafeSwift-feature-250x250.png)

By default, Swift is memory safe, which means that it prevents direct access to memory and makes sure everything is initialized before you use it. The key phrase is "by default." Unsafe Swift lets you get directly at memory through pointers if you need to.

This tutorial will take you on a whirlwind tour of the so-called "unsafe" features of Swift. The term "unsafe" sometimes causes confusion. It doesn't mean that you are writing dangerously bad code that might not work. Rather, it means you are writing code that you need to be extra careful about because the compiler is limited in how it can help you.

You may find yourself needing to use these features if you interoperate with an unsafe language such as C, need to gain additional runtime performance, or simply want to explore internals. While this is an advanced topic, you should be able to follow along if you have reasonable Swift competency. C experience will help, but is not required.

## Getting Started

This tutorial consists of three playgrounds. In the first playground, you'll create several short snippets that explore memory layout and use unsafe pointers. In the second playground, you will wrap a low-level C API that performs streaming data compression with a Swifty interface. In the final playground, you will create a platform independent alternative to `arc4random` that, while using unsafe Swift, hides that detail from users.

Start by creating a new playground, calling it _UnsafeSwift_. You can select any platform, since all the code in this tutorial is platform-agnostic. Make sure to import the Foundation framework.

## Memory Layout

![Sample memory](https://koenig-media.raywenderlich.com/uploads/2017/01/memory-480x214.png)

Unsafe Swift works directly with the memory system. Memory can be visualized as series of boxes (billions of boxes, actually), each with a number inside it. Each box has a unique _memory address_ associated with it. The smallest addressable unit of storage is a _byte_, which usually consists of eight _bits_. Eight bit bytes can store values from 0-255. Processors can also efficiently access _words_ of memory which are typically more than one byte. On a 64-bit system, for example, a word is 8 bytes or 64 bits long.

Swift has a `MemoryLayout` facility that tells you about the size and alignment of things in your program.

Add the following to your playground:
    
    
    MemoryLayout<Int>.size          // returns 8 (on 64-bit)
    MemoryLayout<Int>.alignment     // returns 8 (on 64-bit)
    MemoryLayout<Int>.stride        // returns 8 (on 64-bit)
     
    MemoryLayout<Int16>.size        // returns 2
    MemoryLayout<Int16>.alignment   // returns 2
    MemoryLayout<Int16>.stride      // returns 2
     
    MemoryLayout<Bool>.size         // returns 1
    MemoryLayout<Bool>.alignment    // returns 1
    MemoryLayout<Bool>.stride       // returns 1
     
    MemoryLayout<Float>.size        // returns 4
    MemoryLayout<Float>.alignment   // returns 4
    MemoryLayout<Float>.stride      // returns 4
     
    MemoryLayout<Double>.size       // returns 8
    MemoryLayout<Double>.alignment  // returns 8
    MemoryLayout<Double>.stride     // returns 8

`MemoryLayout<Type>` is a generic type evaluated at compile time that determines the `size`, `alignment` and `stride` of each specified `Type`. The number returned is in bytes. For example, an `Int16` is two bytes in `size` and has an `alignment` of two as well. That means it has to start on even addresses (evenly divisible by two).

So, for example, it is legal to allocate an `Int16` at address 100, but not 101 because it violates the required alignment. When you pack a bunch of `Int16`s together, they pack together at an interval of `stride`. For these basic types the `size` is the same as the `stride`.

Next, look at the layout of some user defined `struct`s and by adding the following to the playground:
    
    
    struct EmptyStruct {}
     
    MemoryLayout<EmptyStruct>.size      // returns 0
    MemoryLayout<EmptyStruct>.alignment // returns 1
    MemoryLayout<EmptyStruct>.stride    // returns 1
     
    struct SampleStruct {
      let number: UInt32
      let flag: Bool
    }
     
    MemoryLayout<SampleStruct>.size       // returns 5
    MemoryLayout<SampleStruct>.alignment  // returns 4
    MemoryLayout<SampleStruct>.stride     // returns 8

The empty structure has a size of zero. It can be located at any address since `alignment` is one. (i.e. All numbers are evenly divisible by one.) The `stride`, curiously, is one. This is because each `EmptyStruct` that you create has to have a unique memory address despite being of zero size.

For `SampleStruct`, the `size` is five but the `stride` is eight. This is driven by its alignment requirements to be on 4-byte boundaries. Given that, the best Swift can do is pack at an interval of eight bytes.

Next add:
    
    
    class EmptyClass {}
     
    MemoryLayout<EmptyClass>.size      // returns 8 (on 64-bit)
    MemoryLayout<EmptyClass>.stride    // returns 8 (on 64-bit)
    MemoryLayout<EmptyClass>.alignment // returns 8 (on 64-bit)
     
    class SampleClass {
      let number: Int64 = 0
      let flag: Bool = false
    }
     
    MemoryLayout<SampleClass>.size      // returns 8 (on 64-bit)
    MemoryLayout<SampleClass>.stride    // returns 8 (on 64-bit)
    MemoryLayout<SampleClass>.alignment // returns 8 (on 64-bit)

Classes are reference types so `MemoryLayout` reports the size of a reference: eight bytes.

If you want to explore memory layout in greater detail, see [this excellent talk by Mike Ash](https://realm.io/news/goto-mike-ash-exploring-swift-memory-layout/).

## Pointers

A pointer encapsulates a memory address. Types that involve direct memory access get an "unsafe" prefix so the pointer type is called `UnsafePointer`. While the extra typing may seem annoying, it lets you and your reader know that you are dipping into non-compiler checked access of memory that when not done correctly could lead to [undefined behavior](http://blog.llvm.org/2011/05/what-every-c-programmer-should-know.html) (and not just a predictable crash).

The designers of Swift could have just created a single `UnsafePointer` type and made it the C equivalent of `char *`, which can access memory in an unstructured way. They didn't. Instead, Swift contains almost a dozen pointer types, each with different capabilities and purposes. Using the most appropriate pointer type communicates intent better, is less error prone, and helps keep you away from undefined behavior.

Unsafe Swift pointers use a very predictable naming scheme so that you know what the traits of the pointer are. Mutable or immutable, raw or typed, buffer style or not. In total there is a combination of eight of these.

![unsafe swift pointers](https://koenig-media.raywenderlich.com/uploads/2016/12/pointers-650x444.png)

In the following sections, you'll learn more about these pointer types.

## Using Raw Pointers

Add the following code to your playground:
    
    
    // 1
    let count = 2
    let stride = MemoryLayout<Int>.stride
    let alignment = MemoryLayout<Int>.alignment
    let byteCount = stride * count
     
    // 2
    do {
      print("Raw pointers")
     
      // 3
      let pointer = UnsafeMutableRawPointer.allocate(bytes: byteCount, alignedTo: alignment)
      // 4
      defer {
        pointer.deallocate(bytes: byteCount, alignedTo: alignment)
      }
     
      // 5
      pointer.storeBytes(of: 42, as: Int.self)
      pointer.advanced(by: stride).storeBytes(of: 6, as: Int.self)
      pointer.load(as: Int.self)
      pointer.advanced(by: stride).load(as: Int.self)
     
      // 6
      let bufferPointer = UnsafeRawBufferPointer(start: pointer, count: byteCount)
      for (index, byte) in bufferPointer.enumerated() {
        print("byte \(index): \(byte)")
      }
    }

In this example you use Unsafe Swift pointers to store and load two integers. Here's what's going on:

  1. These constants hold often used values: 
    * _count_ holds the number of integers to store
    * _stride_ holds the stride of type `Int`
    * _alignment_ holds the alignment of type `Int`
    * _byteCount_ holds the total number of bytes needed
  2. A `do` block is added, to add a scope level, so you can reuse the variable names in upcoming examples.
  3. The method `UnsafeMutableRawPointer.allocate` is used to allocate the required bytes. This method returns an `UnsafeMutableRawPointer`. The name of that type tells you the pointer can be used to load and store (mutate) raw bytes.
  4. A `defer` block is added to make sure the pointer is deallocated properly. ARC isn't going to help you here - you need to handle memory management yourself! You can read more about `defer` [here](https://www.raywenderlich.com/130197/magical-error-handling-swift).
  5. The `storeBytes` and `load` methods are used to store and load bytes. The memory address of the second integer is calculated by advancing the pointer `stride` bytes.

Since pointers are `Strideable` you can also use pointer arithmetic as in `(pointer+stride).storeBytes(of: 6, as: Int.self)`.

  6. An `UnsafeRawBufferPointer` lets you access memory as if it was a collection of bytes. This means you can iterate over the bytes, access them using subscripting and even use cool methods like `filter`, `map` and `reduce`. The buffer pointer is initialized using the raw pointer.

## Using Typed Pointers

The previous example can be simplified by using typed pointers. Add the following code to your playground:
    
    
    do {
      print("Typed pointers")
     
      let pointer = UnsafeMutablePointer<Int>.allocate(capacity: count)
      pointer.initialize(to: 0, count: count)
      defer {
        pointer.deinitialize(count: count)
        pointer.deallocate(capacity: count)
      }
     
      pointer.pointee = 42
      pointer.advanced(by: 1).pointee = 6
      pointer.pointee
      pointer.advanced(by: 1).pointee
     
      let bufferPointer = UnsafeBufferPointer(start: pointer, count: count)
      for (index, value) in bufferPointer.enumerated() {
        print("value \(index): \(value)")
      }
    }

Notice the following differences:

  * Memory is allocated using the method `UnsafeMutablePointer.allocate`. The generic parameter lets Swift know the pointer will be used to load and store values of type `Int`.
  * Typed memory must be initialized before use and deinitialized after use. This is done using `initialize` and `deinitialize` methods respectively. _Update:_ as noted by user atrick in the comments below, deinitialization is only required for _non-trivial types_. That said, including deinitialization is a good way to future proof your code in case you change to something non-trivial. Also, it usually doesn't cost anything since the compiler will optimize it out.
  * Typed pointers have a `pointee` property that provides a type-safe way to load and store values.
  * When advancing a typed pointer, you can simply state the number of values you want to advance. The pointer can calculate the correct stride based on the type of values it points to. Again, pointer arithmetic also works. You can also say `(pointer+1).pointee = 6`
  * The same holds true for typed buffer pointers: they iterate over values, instead of bytes.

## Converting Raw Pointers to Typed Pointers

Typed pointers need not always be initialized directly. They can be derived from raw pointers as well.

Add the following code to your playground:
    
    
    do {
      print("Converting raw pointers to typed pointers")
     
      let rawPointer = UnsafeMutableRawPointer.allocate(bytes: byteCount, alignedTo: alignment)
      defer {
        rawPointer.deallocate(bytes: byteCount, alignedTo: alignment)
      }
     
      let typedPointer = rawPointer.bindMemory(to: Int.self, capacity: count)
      typedPointer.initialize(to: 0, count: count)
      defer {
        typedPointer.deinitialize(count: count)
      }
     
      typedPointer.pointee = 42
      typedPointer.advanced(by: 1).pointee = 6
      typedPointer.pointee
      typedPointer.advanced(by: 1).pointee
     
      let bufferPointer = UnsafeBufferPointer(start: typedPointer, count: count)
      for (index, value) in bufferPointer.enumerated() {
        print("value \(index): \(value)")
      }
    }

This example is similar to the previous one, except that it first creates a raw pointer. The typed pointer is created by _binding_ the memory to the required type `Int`. By binding memory, it can be accessed in a type-safe way. Memory binding is done behind the scenes when you create a typed pointer.

The rest of this example is the same as the previous one. Once you're in typed pointer land, you can make use of `pointee` for example.

## Getting The Bytes of an Instance

Often you have an existing instance of a type that you want to inspect the bytes that form it. This can be achieved using a method called `withUnsafeBytes(of:)`.

Add the following code to your playground:
    
    
    do {
      print("Getting the bytes of an instance")
     
      var sampleStruct = SampleStruct(number: 25, flag: true)
     
      withUnsafeBytes(of: &sampleStruct) { bytes in
        for byte in bytes {
          print(byte)
        }
      }
    }

This prints out the raw bytes of the `SampleStruct` instance. The `withUnsafeBytes(of:)` method gives you access to an `UnsafeRawBufferPointer` that you can use inside the closure.

`withUnsafeBytes` is also available as an instance method on `Array` and `Data`.

## Computing a Checksum

Using `withUnsafeBytes(of:)` you can return a result. An example use of this is to compute a 32-bit checksum of the bytes in a structure.

Add the following code to your playground:
    
    
    do {
      print("Checksum the bytes of a struct")
     
      var sampleStruct = SampleStruct(number: 25, flag: true)
     
      let checksum = withUnsafeBytes(of: &sampleStruct) { (bytes) -> UInt32 in
        return ~bytes.reduce(UInt32(0)) { $0 + numericCast($1) }
      }
     
      print("checksum", checksum) // prints checksum 4294967269
    }

The `reduce` call adds up all of the bytes and `~` then flips the bits. Not a particularly robust error detection, but it shows the concept.

## Three Rules of Unsafe Club

You need to be careful when writing unsafe code so that you avoid undefined behavior. Here are a few examples of bad code.

### Don't return the pointer from withUnsafeBytes!

You should never let the pointer escape the `withUnsafeBytes(of:)` closure. Things may work today but…

### Only bind to one type at a time!
    
    
    // Rule #2
    do {
      print("2. Only bind to one type at a time!")
     
      let count = 3
      let stride = MemoryLayout<Int16>.stride
      let alignment = MemoryLayout<Int16>.alignment
      let byteCount =  count * stride
     
      let pointer = UnsafeMutableRawPointer.allocate(bytes: byteCount, alignedTo: alignment)
     
      let typedPointer1 = pointer.bindMemory(to: UInt16.self, capacity: count)
     
      // Breakin' the Law... Breakin' the Law  (Undefined behavior)
      let typedPointer2 = pointer.bindMemory(to: Bool.self, capacity: count * 2)
     
      // If you must, do it this way:
      typedPointer1.withMemoryRebound(to: Bool.self, capacity: count * 2) {
        (boolPointer: UnsafeMutablePointer<Bool>) in
        print(boolPointer.pointee)  // See Rule #1, don't return the pointer
      }
    }

![badpun](https://koenig-media.raywenderlich.com/uploads/2016/12/badpun-480x175.png)

Never bind memory to two unrelated types at once. This is called _Type Punning_ and Swift does not like puns. Instead, you can temporarily rebind memory with a method like `withMemoryRebound(to:capacity:)`. Also, the rules say it is illegal to rebind from a [trivial type](https://github.com/apple/swift-evolution/blob/master/proposals/0107-unsaferawpointer.md#trivial-types) (such as an `Int`) to a non-trivial type (such as a `class`). Don't do it.

### Don't walk off the end… whoops!
    
    
    // Rule #3... wait
    do {
      print("3. Don't walk off the end... whoops!")
     
      let count = 3
      let stride = MemoryLayout<Int16>.stride
      let alignment = MemoryLayout<Int16>.alignment
      let byteCount =  count * stride
     
      let pointer = UnsafeMutableRawPointer.allocate(bytes: byteCount, alignedTo: alignment)
      let bufferPointer = UnsafeRawBufferPointer(start: pointer, count: byteCount + 1) // OMG +1????
     
      for byte in bufferPointer {
        print(byte)  // pawing through memory like an animal
      }
    }

The ever present problem of off-by-one errors are especially worse with unsafe code. Be careful, review and test!

## Unsafe Swift Example 1: Compression

Time to take all of your knowledge and wrap a C API. Cocoa includes a C module that implements some common data compression algorithms. These include _LZ4_ for when speed is critical, _LZ4A_ for when you need the highest compression ratio and don't care about speed, _ZLIB_ which balances space and speed and the new (and open source) _LZFSE_ which does an even better job balancing space and speed.

Create a new playground, calling it _Compression_. Begin by defining a pure Swift API that uses `Data`.

Then, replace the contents of your playground with the following code:
    
    
    import Foundation
    import Compression
     
    enum CompressionAlgorithm {
      case lz4   // speed is critical
      case lz4a  // space is critical
      case zlib  // reasonable speed and space
      case lzfse // better speed and space
    }
     
    enum CompressionOperation {
      case compression, decompression
    }
     
    // return compressed or uncompressed data depending on the operation
    func perform(_ operation: CompressionOperation,
                 on input: Data,
                 using algorithm: CompressionAlgorithm,
                 workingBufferSize: Int = 2000) -> Data?  {
      return nil
    }

The function that does the compression and decompression is `perform` which is currently stubbed out to return `nil`. You will add some unsafe code to it shortly.

Next add the following code to the end of the playground:
    
    
    // Compressed keeps the compressed data and the algorithm
    // together as one unit, so you never forget how the data was
    // compressed.
     
    struct Compressed {
     
      let data: Data
      let algorithm: CompressionAlgorithm
     
      init(data: Data, algorithm: CompressionAlgorithm) {
        self.data = data
        self.algorithm = algorithm
      }
     
      // Compress the input with the specified algorithm. Returns nil if it fails.
      static func compress(input: Data,
                           with algorithm: CompressionAlgorithm) -> Compressed? {
        guard let data = perform(.compression, on: input, using: algorithm) else {
          return nil
        }
        return Compressed(data: data, algorithm: algorithm)
      }
     
      // Uncompressed data. Returns nil if the data cannot be decompressed.
     func decompressed() -> Data? {
        return perform(.decompression, on: data, using: algorithm)
      }
     
    }

The `Compressed` structure stores both the compressed data and the algorithm that was used to create it. That makes it less error prone when deciding what decompression algorithm to use.

Next add the following code to the end of the playground:
    
    
    // For discoverability, add a compressed method to Data
    extension Data {
     
      // Returns compressed data or nil if compression fails.
      func compressed(with algorithm: CompressionAlgorithm) -> Compressed? {
        return Compressed.compress(input: self, with: algorithm)
      }
     
    }
     
    // Example usage:
     
    let input = Data(bytes: Array(repeating: UInt8(123), count: 10000))
     
    let compressed = input.compressed(with: .lzfse)
    compressed?.data.count // in most cases much less than orginal input count
     
    let restoredInput = compressed?.decompressed()
    input == restoredInput // true

The main entry point is an extension on the `Data` type. You've added a method called `compressed(with:)` which returns an optional `Compressed` struct. This method simply calls the static method `compress(input:with:)` on `Compressed`.

There is an example usage at the end but it is currently not working. Time to start fixing that!

Scroll back up to the first block of code you entered, and begin the implementation of the `perform(_:on:using:workingBufferSize:)` function as follows:
    
    
    func perform(_ operation: CompressionOperation,
                 on input: Data,
                 using algorithm: CompressionAlgorithm,
                 workingBufferSize: Int = 2000) -> Data?  {
     
      // set the algorithm
      let streamAlgorithm: compression_algorithm
      switch algorithm {
      case .lz4:   streamAlgorithm = COMPRESSION_LZ4
      case .lz4a:  streamAlgorithm = COMPRESSION_LZMA
      case .zlib:  streamAlgorithm = COMPRESSION_ZLIB
      case .lzfse: streamAlgorithm = COMPRESSION_LZFSE
      }
     
      // set the stream operation and flags
      let streamOperation: compression_stream_operation
      let flags: Int32
      switch operation {
      case .compression:
        streamOperation = COMPRESSION_STREAM_ENCODE
        flags = Int32(COMPRESSION_STREAM_FINALIZE.rawValue)
      case .decompression:
        streamOperation = COMPRESSION_STREAM_DECODE
        flags = 0
      }
     
      return nil /// To be continued
    }

This converts from your Swift types to the C types required by the compression library, for the compression algorithm and operation to perform.

Next, replace `return nil` with:
    
    
    // 1: create a stream
    var streamPointer = UnsafeMutablePointer<compression_stream>.allocate(capacity: 1)
    defer {
      streamPointer.deallocate(capacity: 1)
    }
     
    // 2: initialize the stream
    var stream = streamPointer.pointee
    var status = compression_stream_init(&stream, streamOperation, streamAlgorithm)
    guard status != COMPRESSION_STATUS_ERROR else {
      return nil
    }
    defer {
      compression_stream_destroy(&stream)
    }
     
    // 3: set up a destination buffer
    let dstSize = workingBufferSize
    let dstPointer = UnsafeMutablePointer<UInt8>.allocate(capacity: dstSize)
    defer {
      dstPointer.deallocate(capacity: dstSize)
    }
     
    return nil /// To be continued

This is what is happening here:

  1. Allocate a `compression_stream` and schedule it for deallocation with the `defer` block.
  2. Then, using the `pointee` property you get the stream and pass it to the `compression_stream_init` function. The compiler is doing something special here. By using the inout `&` marker it is taking your `compression_stream` and turning it into a `UnsafeMutablePointer<compression_stream>` automatically. (You could have also just passed `streamPointer` and not needed this special conversion.)
  3. Finally, you create a destination buffer that will act as your working buffer.

Finish the `perform` function by replacing `return nil` with:
    
    
    // process the input
    return input.withUnsafeBytes { (srcPointer: UnsafePointer<UInt8>) in
      // 1
      var output = Data()
     
      // 2
      stream.src_ptr = srcPointer
      stream.src_size = input.count
      stream.dst_ptr = dstPointer
      stream.dst_size = dstSize
     
      // 3
      while status == COMPRESSION_STATUS_OK {
        // process the stream
        status = compression_stream_process(&stream, flags)
     
        // collect bytes from the stream and reset
        switch status {
     
        case COMPRESSION_STATUS_OK:
          // 4
          output.append(dstPointer, count: dstSize)
          stream.dst_ptr = dstPointer
          stream.dst_size = dstSize
     
        case COMPRESSION_STATUS_ERROR:
          return nil
     
        case COMPRESSION_STATUS_END:
          // 5
          output.append(dstPointer, count: stream.dst_ptr - dstPointer)
     
        default:
          fatalError()
        }
      }
      return output
    }

This is where the work really happens. And here's what it's doing:

  1. Create a `Data` object which is going to contain the output - either the compressed or decompressed data, depending on what operation this is.
  2. Set up the source and destination buffers with the pointers you allocated and their sizes.
  3. Then you keep calling `compression_stream_process` as long as it continues to return `COMPRESSION_STATUS_OK`.
  4. The destination buffer is then copied into `output` that is eventually returned from this function.
  5. When the last packet comes in, marked with `COMPRESSION_STATUS_END` only part of the destination buffer potentially needs to be copied.

In the example usage you can see that the 10,000-element array is compressed down to 153 bytes. Not too shabby.

## Unsafe Swift Example 2: Random Generator

Random numbers are important for many applications from games to machine learning. macOS provides `arc4random` (A Replacement Call 4 random) that produces great (cryptographically sound) random numbers. Unfortunately this call is not available on Linux. Moreover, `arc4random` only provides randoms as `UInt32`. However, the file _/dev/urandom_ provides an unlimited source of good random numbers.

In this section, you will use your new knowledge to read this file and create completely type safe random numbers.

![hexdump](https://koenig-media.raywenderlich.com/uploads/2016/12/hexdump-480x202.png)

Start by creating a new playground, calling it _RandomNumbers_. Make sure to select the _macOS_ platform this time.

Once you've created it, replace the default contents with:
    
    
    import Foundation
     
    enum RandomSource {
     
      static let file = fopen("/dev/urandom", "r")!
      static let queue = DispatchQueue(label: "random")
     
      static func get(count: Int) -> [Int8] {
        let capacity = count + 1 // fgets adds null termination
        var data = UnsafeMutablePointer<Int8>.allocate(capacity: capacity)
        defer {
          data.deallocate(capacity: capacity)
        }
        queue.sync {
          fgets(data, Int32(capacity), file)
        }
        return Array(UnsafeMutableBufferPointer(start: data, count: count))
      }
    }

The `file` variable is declared `static` so only one will exist in the system. You will rely on the system closing it when the process exits. Since it is possible that multiple threads will want random numbers, you need to protect access to it with a serial GCD queue.

The `get` function is where the work happens. First you create some unallocated storage that is one beyond what you need because `fgets` is always 0 terminated. Next, you get the data from the file, making sure to do so while operating on the GCD queue. Finally, you copy the data to a standard array by first wrapping it in a `UnsafeMutableBufferPointer` that can act as a `Sequence`.

So far this will only (safely) give you an array of `Int8` values. Now you're going to extend that.

Add the following to the end of your playground:
    
    
    extension Integer {
     
      static var randomized: Self {
        let numbers = RandomSource.get(count: MemoryLayout<Self>.size)
        return numbers.withUnsafeBufferPointer { bufferPointer in
          return bufferPointer.baseAddress!.withMemoryRebound(to: Self.self, capacity: 1) {
            return $0.pointee
          }
        }
      }
     
    }
     
    Int8.randomized
    UInt8.randomized
    Int16.randomized
    UInt16.randomized
    Int16.randomized
    UInt32.randomized
    Int64.randomized
    UInt64.randomized

This adds a static `randomized` property to all subtypes of the `Integer` protocol (see [protocol oriented programming](https://www.raywenderlich.com/148448/introducing-protocol-oriented-programming) for more on this!). You first get the random numbers, and with the bytes of the array that is returned, you rebind (as in C++'s `reinterpret_cast`) the `Int8` values as the type being requested and return a copy. Simples! :]

And that's it! Random numbers in a safe way, using unsafe Swift under the hood.

## Where to Go From Here?

Here are [the completed playgrounds](https://koenig-media.raywenderlich.com/uploads/2017/01/Unsafe.zip). There many additional resources you can explore to learn more:

  * [Swift Evolution 0107: UnsafeRawPointer API](https://github.com/apple/swift-evolution/blob/master/proposals/0107-unsaferawpointer.md) gives a detailed overview of the Swift memory model and makes reading the API documents more understandable.
  * [Swift Evolution 0138: UnsafeRawBufferPointer API](https://github.com/apple/swift-evolution/blob/master/proposals/0138-unsaferawbufferpointer.md) talks extensively about working with untyped memory and has links to open source projects that benefit from using them.
  * If you are converting unsafe code to Swift 3 check out [The Migration Guide](https://swift.org/migration-guide/se-0107-migrate.html). Even if you aren't migrating, it contains a number of interesting examples.
  * [Interacting with C APIs](https://developer.apple.com/library/content/documentation/Swift/Conceptual/BuildingCocoaApps/InteractingWithCAPIs.html) will give you insights in how Swift interacts with C.
  * Mike Ash has an excellent presentation on [Exploring Swift Memory Layout](https://realm.io/news/goto-mike-ash-exploring-swift-memory-layout/). 

I hope you have enjoyed this tutorial. If you have questions or experiences you would like to share, I am looking forward to hearing about them in the forums!
