# How to use LLVM API with Swift

_Captured: 2015-12-03 at 19:35 from [lowlevelbits.org](http://lowlevelbits.org/how-to-use-llvm-api-with-swift/)_

This article shows how to use LLVM C API with Swift. It doesn't aim to show how to write proper idiomatic Swift. Besides that I omit some good practices for sake of simplicity.

Our plan for today:

  * grab latest version of LLVM
  * build it using CMake and llvm-config
  * create simple Swift program (~50 LoC), build and link it against LLVM
  * create simple `sum` function in memory and execute it using LLVM interpreter

So, let's go to town!

### Preparing LLVM

Let's grab fresh version of LLVM. It can be done using central SVN repository, or via official git mirror. I prefer latter option, since it's, imho, a bit faster.

For this particular example I will put everything into a directory inside of the home directory:
    
    
    1
    2
    3
    
    
    
    ~ $ mkdir swift_llvm
    ~ $ cd swift_llvm
    ~/swift_llvm $ git clone http://llvm.org/git/llvm.git
    

LLVM uses CMake as a build system. To make a build let's create a separate directory near LLVM directory and generate build rules:
    
    
    1
    2
    3
    
    
    
    ~/swift_llvm $ mkdir build
    ~/swift_llvm $ cd build
    ~/swift_llvm/build $ cmake  ../llvm
    

CMake could generate various output: makefiles, Xcode projects, VisualStudio solutions and more. If build system is not specified (like in the script above), then CMake takes default one, which is GNU/Make.

Modularity is one of the significant advantages of LLVM. It has dozens of 'small' libraries. We will need to link our program against some of them. If you're like me and not an LLVM expert, then you probably don't know which ones you need.

The naive way of solving this problem is to build the program and resolve linker errors manually until they disappear. It will work, indeed, but it's became boring after resolving 5-6 errors.

Thank god, LLVM developers are thoughtful and provide a great tool `llvm-config`. Let's build it and see what it does.
    
    
    1
    
    
    
    ~/swift_llvm/build $ make llvm-config -j4
    

_Note: `-j4` says 'I have multi core/processor environment, run 4 jobs simultaneously'_

`llvm-config` provides different options/shortcuts, e.g.: where to look for built libraries, where to look for headers, which linker flags to pass to link in JIT module or interpreter, and so on.

_Note: Run `llvm-config` without options to learn more._

We're particularly interested in interpreter. Let's look what we need to build:
    
    
    1
    2
    
    
    
    ~/swift_llvm/build $ ./bin/llvm-config --libs interpreter
    -lLLVMInterpreter -lLLVMExecutionEngine -lLLVMRuntimeDyld -lLLVMObject -lLLVMMCParser -lLLVMCodeGen -lLLVMTarget -lLLVMScalarOpts -lLLVMInstCombine -lLLVMInstrumentation -lLLVMTransformUtils -lLLVMMC -lLLVMBitWriter -lLLVMBitReader -lLLVMAnalysis -lLLVMCore -lLLVMSupport
    

To make our little program working we need to build all these libraries. Again, there is naive way of doing this, but we will go with shell magic:
    
    
    1
    
    
    
    ~/swift_llvm/build $ ./bin/llvm-config --libs interpreter | sed "s/-l//g" | xargs make -j4
    

### Hello LLVM

Since we have done and have everything in place it's time to create our little Swift program:
    
    
    1
    2
    3
    
    
    
    ~/swift_llvm/build $ cd ..
    ~/swift_llvm $ touch hello_llvm.swift
    ~/swift_llvm $ open hello_llvm.swift
    

To check that everything is working as we expect we will first create an empty module and dump it:
    
    
    1
    2
    3
    4
    5
    6
    7
    
    
    
    import LLVM_C
    let module = LLVMModuleCreateWithName("Hello")
    LLVMDumpModule(module)
    LLVMDisposeModule(module)
    

Building this small program requires passing numerous flags to compiler. We need to specify SDK, to set which module to link with, specify linker flags, set correct header search paths and probably provide some additional arguments:
    
    
    1
    
    
    
    ~/swift_llvm $ xcrun -sdk macosx swiftc hello_llvm.swift -module-link-name LLVM_C -L??? -lLLVM??? -I??? ???
    

So many questions, so much magic.

In fact specifying correct linker flags and libraries path is easy, thanks `llvm-config`:
    
    
    1
    
    
    
    ~/swift_llvm $ xcrun -sdk macosx swiftc hello_llvm.swift -module-link-name LLVM_C `./build/bin/llvm-config --libs interpreter` -L ./build/lib -I??? ???
    

Situation with headers and additional parameters is a bit more trickier. Normally, if we use clang, we could just rely on `llvm-config --cflags`, though it does not work with swift compiler. Let's examine the `\--cflags` and see what we can do here:
    
    
    1
    2
    
    
    
    ~/swift_llvm $ ./build/bin/llvm-config --cflags
    -I/Users/alexdenisov/swift_llvm/llvm/include -I/Users/alexdenisov/swift_llvm/build/include  -fPIC -Wall -W -Wno-unused-parameter -Wwrite-strings -Wmissing-field-initializers -pedantic -Wno-long-long -Wcovered-switch-default -D__STDC_CONSTANT_MACROS -D__STDC_FORMAT_MACROS -D__STDC_LIMIT_MACROS
    

The output contains a few parameters, we can easily omit all arguments except of headers search paths (`-I ...`) and macro definitions (`-D__...`). The problem is that swift compiler does not handle macro definitions the way as clang does, though we could bypass them directly to clang driver using `-Xcc` option:
    
    
    1
    
    
    
    ~/swift_llvm $ xcrun -sdk macosx swiftc hello_llvm.swift -module-link-name LLVM_C `./build/bin/llvm-config --libs interpreter` -L ./build/lib -I ./llvm/include -I ./build/include -Xcc -D__STDC_CONSTANT_MACROS -Xcc -D__STDC_LIMIT_MACROS -Xcc -D__STDC_FORMAT_MACROS
    

If you were eager enough and run the recent command, then you might see some errors: linker complains because it can't find symbols from ncurses and STD C++ libraries. No worries, here is the correct command:
    
    
    1
    
    
    
    ~/swift_llvm $ xcrun -sdk macosx swiftc hello_llvm.swift -module-link-name LLVM_C `./build/bin/llvm-config --libs interpreter` -L ./build/lib -lc++ -lcurses -I ./llvm/include -I ./build/include -Xcc -D__STDC_CONSTANT_MACROS -Xcc -D__STDC_LIMIT_MACROS -Xcc -D__STDC_FORMAT_MACROS
    

Now we can run the program and see the beautiful LLVM IR:
    
    
    1
    2
    
    
    
    ~/swift_llvm $ ./hello_llvm
    ; ModuleID = 'Hello'
    

Ok, it's empty and doesn't look cool. But there are good news: we are able to use LLVM C API from Swift. Isn't this impressive?

Let's go further and create simple `sum` function that accepts two integers, sums them and returns result. Here is a C equivalent:
    
    
    1
    2
    3
    
    
    
    int sum(int a, int b) {
      return a + b;
    }
    

To create a function we need to specify all types involved: return type and types of arguments.

Types of arguments must be passed as an array. Since we interop with C API it's a bit tricky, but still pretty straightforward:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    21
    
    
    
    import LLVM_C
    let module = LLVMModuleCreateWithName("Hello")
    let int32 = LLVMInt32Type()
    let paramTypes = [int32, int32]
    // need to convert paramTypes into UnsafeMutablePointer because of API requirements
    var paramTypesRef = UnsafeMutablePointer<LLVMTypeRef>.alloc(paramTypes.count)
    paramTypesRef.initializeFrom(paramTypes)
    let returnType = int32
    let functionType = LLVMFunctionType(returnType, paramTypesRef, UInt32(paramTypes.count), 0)
    let sumFunction = LLVMAddFunction(module, “sum”, functionType)
    LLVMDumpModule(module)
    paramTypesRef.dealloc(paramTypes.count)
    LLVMDisposeModule(module)
    

Build it:
    
    
    1
    
    
    
    ~/swift_llvm $ xcrun -sdk macosx swiftc hello_llvm.swift -module-link-name LLVM_C `./build/bin/llvm-config --libs interpreter` -L ./build/lib -lc++ -lcurses -I ./llvm/include -I ./build/include -Xcc -D__STDC_CONSTANT_MACROS -Xcc -D__STDC_LIMIT_MACROS -Xcc -D__STDC_FORMAT_MACROS
    

And run:
    
    
    1
    2
    3
    
    
    
    ; ModuleID = 'Hello'
    declare i32 @sum(i32, i32)
    

Here you go, function prototype is ready - next step is function body.

Atomic particle of code is a `basic block`. Function or loop body, conditional branch (`if/else`, `switch/case`, etc.) these are basic blocks. Our simple function has one as well:
    
    
    1
    
    
    
    let entryBlock = LLVMAppendBasicBlock(sumFunction, "entry")
    

This block could be filled in using builder. First we emit instructions to access function arguments. Next one - addition of the arguments with the `temp` variable holding the result. And the last instruction - return statement.
    
    
    1
    2
    3
    4
    5
    6
    7
    
    
    
    let builder = LLVMCreateBuilder()
    LLVMPositionBuilderAtEnd(builder, entryBlock)
    let a = LLVMGetParam(sumFunction, 0)
    let b = LLVMGetParam(sumFunction, 1)
    let temp = LLVMBuildAdd(builder, a, b, "temp")
    LLVMBuildRet(builder, temp)
    

_Put this code after `sumFunction` declaration, but before `LLVMDumpModule`. Or just keep reading, you will see the full code listing at the end of the article._

Build and run, you will see the function body:
    
    
    1
    2
    3
    4
    5
    6
    7
    
    
    
    ; ModuleID = 'Hello'
    define i32 @sum(i32, i32) {
    entry:
      %temp = add i32 %0, %1
      ret i32 %temp
    }
    

Last and the most interesting part - how to run this code?

LLVM C API provides couple of execution engines: `MCJIT` and `Interpreter`, we will go with the latter one.

_Note: To be honest I don't really know exact difference between them, the only reason I use interpreter here - I got a few different errors when I tried to use MCJIT._

Let's create an execution engine:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    
    
    
    let engine = UnsafeMutablePointer<LLVMExecutionEngineRef>.alloc(alignof(LLVMExecutionEngineRef))
    var error =  UnsafeMutablePointer<UnsafeMutablePointer<Int8>>.alloc(alignof(UnsafeMutablePointer<Int8>))
    LLVMLinkInInterpreter()
    if LLVMCreateInterpreterForModule(engine, module, error) != 0 {
      print("can't initialize engine: \(String.fromCString(error.memory)!)")
      // TODO: cleanup all allocated memory ;)
      exit(1)
    }
    

You can build and run it, just to ensure that everything is still working.

Finally, let's run our function and actually compute the sum. Here we do the same trick as with function type - API requires `UnsafeMutablePointer`. Keep in mind that you should deallocate this memory manually.
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    
    
    
    let x: UInt64 = 10
    let y: UInt64 = 25
    let args = [LLVMCreateGenericValueOfInt(int32, x, 0),
                LLVMCreateGenericValueOfInt(int32, y, 1)]
    var argsRef = UnsafeMutablePointer<LLVMTypeRef>.alloc(args.count)
    argsRef.initializeFrom(args)
    let result = LLVMRunFunction(engine.memory, sumFunction, UInt32(args.count), argsRef)
    print("\(x) + \(y) = \(LLVMGenericValueToInt(result, 0))")
    argsRef.dealloc(args.count)
    

If you build and run the program - you will see the result:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    
    
    
    ; ModuleID = 'Hello'
    define i32 @sum(i32, i32) {
    entry:
      %temp = add i32 %0, %1
      ret i32 %temp
    }
    10 + 25 = 35
    

Here is the full code listing:
    
    
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    21
    22
    23
    24
    25
    26
    27
    28
    29
    30
    31
    32
    33
    34
    35
    36
    37
    38
    39
    40
    41
    42
    43
    44
    45
    46
    47
    48
    49
    50
    51
    52
    53
    54
    55
    56
    57
    
    
    
    import LLVM_C
    let module = LLVMModuleCreateWithName("Hello")
    let int32 = LLVMInt32Type()
    let paramTypes = [int32, int32]
    // need to convert paramTypes into UnsafeMutablePointer because of API requirements
    var paramTypesRef = UnsafeMutablePointer<LLVMTypeRef>.alloc(paramTypes.count)
    paramTypesRef.initializeFrom(paramTypes)
    let returnType = int32
    let functionType = LLVMFunctionType(returnType, paramTypesRef, UInt32(paramTypes.count), 0)
    let sumFunction = LLVMAddFunction(module, "sum", functionType)
    let entryBlock = LLVMAppendBasicBlock(sumFunction, "entry")
    let builder = LLVMCreateBuilder()
    LLVMPositionBuilderAtEnd(builder, entryBlock)
    let a = LLVMGetParam(sumFunction, 0)
    let b = LLVMGetParam(sumFunction, 1)
    let temp = LLVMBuildAdd(builder, a, b, "temp")
    LLVMBuildRet(builder, temp)
    LLVMDumpModule(module)
    let engine = UnsafeMutablePointer<LLVMExecutionEngineRef>.alloc(alignof(LLVMExecutionEngineRef))
    var error =  UnsafeMutablePointer<UnsafeMutablePointer<Int8>>.alloc(alignof(UnsafeMutablePointer<Int8>))
    LLVMLinkInInterpreter()
    if LLVMCreateInterpreterForModule(engine, module, error) != 0 {
      print("can't initialize engine: \(String.fromCString(error.memory)!)")
      // TODO: cleanup all allocated memory ;)
      exit(1)
    }
    let x: UInt64 = 10
    let y: UInt64 = 25
    let args = [LLVMCreateGenericValueOfInt(int32, x, 0),
                LLVMCreateGenericValueOfInt(int32, y, 1)]
    var argsRef = UnsafeMutablePointer<LLVMTypeRef>.alloc(args.count)
    argsRef.initializeFrom(args)
    let result = LLVMRunFunction(engine.memory, sumFunction, UInt32(args.count), argsRef)
    print("\(x) + \(y) = \(LLVMGenericValueToInt(result, 0))")
    argsRef.dealloc(args.count)
    paramTypesRef.dealloc(paramTypes.count)
    LLVMDisposeModule(module)
    

### Summary

As you may see using LLVM from Swift is a bit tricky, but it's still doable. It actually gives us great opportunity - you can write a language (probably domain specific) in Swift using all the power of LLVM. C API may look limited, but it's full enough to start with.

If you curious and want to learn more about the topic, please consider looking at these resources:

[How to get started with the LLVM C API](https://pauladamsmith.com/blog/2015/01/how-to-get-started-with-llvm-c-api.html) \- great how-to on LLVM C API. This article basically based on it.

[Kaleidoscope Tutorials](http://llvm.org/docs/tutorial/index.html) \- tutorial on implementing simple but powerful language. Currently, there are two versions - for C++ and OCaml.

[Kaleidoscope Implementation](https://github.com/bencochran/Kaleidoscope) \- same language as above implemented using Swift. Trove of treasures there.

[Auspicion](https://github.com/robrix/Auspicion) \- LLVM C API bindings for Swift.

[LLVM.swift](https://github.com/bencochran/LLVM.swift) \- another Swift wrapper for LLVM C API.

[Source code](https://github.com/AlexDenisov/swift_llvm) \- source code for this article.

Thank you for your attention.

Happy hacking!
