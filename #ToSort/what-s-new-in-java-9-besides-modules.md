# What's New in Java 9? (Besides Modules)

_Captured: 2017-05-10 at 16:31 from [dzone.com](https://dzone.com/articles/java-9-besides-modules?edition=298023&utm_source=weekly%20digest&utm_medium=email&utm_campaign=wd%202017-05-10)_

The most important feature of Java 9 is the [Java Platform Module System (JPMS)](http://openjdk.java.net/projects/jigsaw/spec/). There are other interesting features like improvements to the Process API and new tools likeJSshell. Over the past couple of years, I wasn't paying much attention to the other "smaller" changes until I attended [this interesting speech at Devoxx France](https://www.youtube.com/watch?v=tQ02pShPLHk). Now that [JDK 9 has been announced as Feature Complete](http://mail.openjdk.java.net/pipermail/jdk9-dev/2017-January/005505.html) earlier this year, this post compiles all those features that are interesting enough for a wide range of developers, and provides detail on each of them. Of course, not everything is mentioned below (you can look at the complete feature set [here](http://openjdk.java.net/projects/jdk9/), which is currently frozen). If you think there is some feature that I missed and are worth describing on this list, please leave a comment.

## Process API Updates (JEP 102)

Among the API changes is the introduction of the `[ProcessHandle](http://download.java.net/java/jdk9/docs/api/java/lang/ProcessHandle.html)` interface, which makes common operations on native processes much easier.

### Retrieve PID of Current Process

Before Java 9, there was no standard solution to get the native ID of the current process. One could use `java.lang.management.ManagementFactory` as follows:
    
    
    java.lang.management.RuntimeMXBean runtime = java.lang.management.ManagementFactory.getRuntimeMXBean();
    
    
    java.lang.reflect.Field jvm = runtime.getClass().getDeclaredField("jvm");
    
    
    sun.management.VMManagement mgmt = (sun.management.VMManagement) jvm.get(runtime);
    
    
    java.lang.reflect.Method pid_method = mgmt.getClass().getDeclaredMethod("getProcessId");
    
    
    int pid = (Integer) pid_method.invoke(mgmt);

Or rely on parsing a command result:

Starting in Java 9, we can use the `[pid()](http://download.java.net/java/jdk9/docs/api/java/lang/ProcessHandle.html#pid--)` method of the current `ProcessHandle`:

###   
Checking If a Process Is Currently Running

Prior to the introduction of `ProcessHandle`, checking if a process was alive could be done by running a command such as `ps -ef` and parsing its output to see if the process is listed. Another workaround relies on the `[exitValue()](http://download.java.net/java/jdk9/docs/api/java/lang/Process.html#exitValue--)` method of the `Process` class, which throws an `IllegalThreadStateException` if the process has not yet terminated.

Starting Java 9, we can use the `[isAlive()](http://download.java.net/java/jdk9/docs/api/java/lang/ProcessHandle.html#isAlive--)` method:

###   
Retrieving Process Information

Similarly, if we wanted to retrieve basic information about a certain process, there is no built-in solution. One could parse a command result or rely on a third-party library to do it. In Java 9, we can retrieve a `[ProcessHandle.Info](http://download.java.net/java/jdk9/docs/api/java/lang/ProcessHandle.Info.html)` instance, which contains this information:

### Running Post-Termination Code

Another convenient feature in the new process API is the ability to run code upon process termination. This can be done using the `onExit` method in either a `Process` or a `ProcessHandle`, which returns a `CompletableFuture`.

### Getting Children and Parent Processes

A few other methods further make it easier to navigate process trees:

Method name Description

`[children()](http://download.java.net/java/jdk9/docs/api/java/lang/ProcessHandle.html#children--)`
Returns a `Stream<ProcessHandle>` that captures the current direct children.

`[descendants()](http://download.java.net/java/jdk9/docs/api/java/lang/ProcessHandle.html#descendants--)`
Returns a `Stream<ProcessHandle>` that captures the descendant processes.

`[allProcesses()](http://download.java.net/java/jdk9/docs/api/java/lang/ProcessHandle.html#allProcesses--)`

A static method that returns a `Stream<ProcessHandle>` of all processes currently visible.

**Note: **It is important to keep in mind that the operating system can restrict some of these APIs, and for the above three methods,_ those processes are created and terminate asynchronously. There is no guarantee that a process in the stream is alive or that no other processes may have been created since the inception of the snapshot._

## Milling Project Coin (JEP 213)

Five items in this JEP introduce small changes to the language.

### `@SafeVarargs` Annotation Can Be Applied to Private Methods

This [annotation](https://docs.oracle.com/javase/7/docs/api/java/lang/SafeVarargs.html) was introduced in Java 7 to allow a programmer to signal to the compiler that a variable arity method performs safe operations on its varargs parameter. A bit of context about the annotation: Due to the type-unsafe nature of mixing generic types with array creation, and because varargs are translated into arrays behind the scenes, the compiler generates a warning for varargs methods that use such generic types, as well as warning in all method invocations where there is a generic array creation.

As an example, the following method causes a compiler warning:

To make the compiler ignore this (although it would be the **wrong thing to do in this case**), we can annotate the method with `@SafeVarargs`.

**So what changed in Java 9?** Before Java 9, `@SafeVarargs` could be applied to either static or final methods. In Java 9, the annotation can also be used on private methods.

### Allow Effectively Final Variables to Be Used in a Try-With-Resources Statement

Try-with-resources statements require a local variable declaration for the resource:

Now it is possible to use the statement on a resource without declaring a local variable for it, as long as the variable referencing the resource is final or [effectively final](https://docs.oracle.com/javase/tutorial/java/javaOO/localclasses.html#accessing-members-of-an-enclosing-class).

###   
Allow the <> Operator in Anonymous Classes

For reasons related to the compiler's type inference implementation, diamond operators were not allowed when instantiating anonymous classes in Java 7. With this change, as long as the compiler can infer the type argument of the anonymous class, we can use the operator:

###   
Forbid the Underscore as an Identifier

In Java 8, Java compilers started to issue a warning on using an underscore as an identifier and an error when used in lambdas. With Java 9, an error is thrown in all cases underscores are used:

### Private Methods in Interfaces

When default methods were being added to interfaces in Java 8, private methods were being considered as well. But it was later postponed. Now with Java 9, interfaces can have private methods (static and instance) to allow non-abstract methods to share code:

## New Doclet API (JEP 221)

The [Doclet API](http://docs.oracle.com/javase/7/docs/technotes/guides/javadoc/doclet/overview.html), which allowed client applications to customize the output of Javadocs, underwent a re-design as defined in [JEP 221](http://openjdk.java.net/jeps/221). The goal was to make use of the [Language Model API](http://docs.oracle.com/javase/8/docs/api/javax/lang/model/element/package-summary.html) introduced in Java 6 as a standard of representing program elements, as well as the [DocTree API](http://docs.oracle.com/javase/8/docs/jdk/api/javac/tree/com/sun/source/doctree/package-summary.html) to represent documentation elements in the source code and get rid of using the old language model that was part of the old Doclet API. The outcome is a migration of the old API from the [com.sun.javadoc](http://docs.oracle.com/javase/8/docs/jdk/api/javadoc/doclet/index.html) package to a new [jdk.javadoc.doclet](http://download.java.net/java/jdk9/docs/jdk/api/javadoc/doclet/jdk/javadoc/doclet/package-summary.html) package.

Also, the [standard doclet](http://docs.oracle.com/javase/7/docs/technotes/guides/javadoc/standard-doclet.html) that the Javadoc tool uses by default to generate HTML documentation has been adapted to use the new API.

## JShell: The Java Shell (JEP 222)

JShell is a REPL (Read-Eval-Print-Loop) tool that allows snippets of code to be run without having to place them in classes. It is similar to what exists in other JVM-based languages such as Groovy or Scala. One of the motivations behind JShell was that _"the number one reason schools cite for moving away from Java as a teaching language is that other languages have a REPL and have far lower bars to an initial `Hello, world!` program"_. Meh... a bit debatable maybe. But a more convincing rationale would be to facilitate quick prototyping of new code without having to compile and run and without having to open an IDE.

In addition to the command line tool, JShell comes with an [API](http://download.java.net/java/jdk9/docs/api/jdk.jshell-summary.html) to allow other tools to integrate JShell's functionality.

Some rules such as ending statements with semi-colons and checked exceptions are relaxed. You can even declare variables of some type that you define _after_ declaring the variable. The class path and module path can also be changed during the session, or when starting JShell the first time (using `\--class-path` and `\--module-path`).

## New Versioning Scheme (JEP 223)

Throughout the past 20+ years, the versioning of Java releases was inconsistent and sometimes confusing. The first two major releases were JDK 1.0 and JDK 1.1. From 1.2 till 1.5, the platform was referred to as J2SE (for the Standard Edition). Starting in 1.5, the versioning changed to become Java 5, then Java 6, and so on. However, when you run `java -version` with an installed Java 8, the output still shows 1.8 instead of 8. The [current versioning scheme](http://www.oracle.com/technetwork/java/javase/overview/jdk-version-number-scheme-1918258.html) for releases, introduced after Oracle acquired Sun, goes as follows:

  * For Limited Update Releases (no critical security fixes), release numbers will multiples of 20.
  * For Critical Patch Updates (fixes security vulnerabilities), the release number will be calculated by adding multiples of five to the prior Limited Update and when needed adding one to keep the resulting number odd.

### Version Numbers

Starting Java 9, the versioning will be consistent with [semantic versioning](http://semver.org/), and version numbers have the format `$MAJOR.$MINOR.$SECURITY(.$otherpart)?` where:

  * `$MAJOR` is the major version number and is incremented when a major version is released that typically changes the platform specification. For JDK 9, this value will be 9.
  * `$MINOR` is the minor version number, and is incremented for releases that contain bug fixes and enhancements to standard APIs.
  * `$SECURITY` is the security level, and is incremented for releases that contain critical security fixes. This version is **not** reset to zero when the minor version number is incremented.
  * `$otherpart` consists of one or more versions that can be used by JVM providers to indicate a patch with a small number of non-security fixes.

### Version Strings

The version string will be the version number with some other information such as early-access release identifier or the build number:

`$VNUM(-$PRE)?\\+$BUILD(-$OPT)?`

`$VNUM-$PRE(-$OPT)?`

`$VNUM(+-$OPT)?`

where:

  * `$PRE` is a pre-release identifier.
  * `$BUILD` is the build number
  * `$OPT` is optional information such as the timestamp.

For comparison, the versioning for JDK 9 using both the existing and upcoming schemes is shown in the below table:

The new versioning scheme is fully documented in the `[Runtime.Version](http://download.java.net/java/jdk9/docs/api/java/lang/Runtime.Version.html)` class and version information can be accessed from it:

## Javadoc Search and HTML5 (JEPs 224-225)

Have you noticed anything new in the content of Javadoc pages for Java 9 API so far? Look at the top right of the main frame. That's right, there is now a search box that you can use to search for classes, methods, etc. It's hard to believe it took them so long to implement it. The pages are also in HTML5 by default instead of HTML 4.

The searching is done locally, and the things that can be searched are:

  * Modules, packages, types, and members.
  * Text that is marked with the tag `@index`.

## New HotSpot Diagnostic Commands (JEP 228)

The following JVM diagnosis commands were added:

  * **`print_class_summary`**: print all loaded classes and their hierarchy
  * `**print_codegenlist**`: show the queue of methods to be compiled in C1 and C2 compilers
  * `**print_utf8pool**`: print string table
  * `**datadump_request**`: signal the JVM to do a data dump request for JVMTI
  * `**dump_codelist**`: print all compiled methods in code cache that are alive
  * `**print_codeblocks**`: print code cache layout and bounds
  * `**set_vmflag**`: set VM flag option using the provided value

Here is a sample test that sends a command to print the string table using the `jcmd` utility:

## Create PKCS12 Keystores by Default (JEP 229)

Starting Java 9, keystores are created using the PKCS12 format instead of JKS because it offers stronger cryptographic algorithms. This change is backward compatible, so applications accessing existing keystores continue to work.

## Multi-Release JAR Files (JEP 238)

One of the most interesting features introduced in Java 9 is the multi-release Jar (MRJAR), which allows bundling code targeting multiple Java releases within the same Jar file. By setting `[Multi-Release: true](http://download.java.net/java/jdk9/docs/api/java/util/jar/Attributes.Name.html#MULTI_RELEASE)` in the MANIFEST.MF file, the file becomes a multi-release JAR and the Java runtime will pick the appropriate versions of classes depending on the current major version running. The structure of such a file is illustrated as follows:

  * On JDKs < 9, only the classes in the root entry are visible to the Java runtime.
  * On a JDK 9, the classes A and B will be loaded from the directory `root/META-INF/versions/9`, while C and D will be loaded from the base entry.
  * On a JDK 10, class A would be loaded from the directory `root/META-INF/versions/10`.

A multi-release JAR file allows projects to maintain different versions of their code targeting different Java platforms, while being able to distribute the code as one JAR, with a single version (e.g. Maven artifact version). This relaxes the common restriction of writing backward compatible code, and allows developers to benefit from a new language and API changes incrementally as they add new code.

This feature naturally requires modifications to some APIs used to process JAR files, such as `[JarFile](http://download.java.net/java/jdk9/docs/api/java/util/jar/JarFile.html)` and `[URLClassLoader](http://download.java.net/java/jdk9/docs/api/java/net/URLClassLoader.html)`. Also, many JDK tools have been adapted to be aware of the new format, such as `java`, `javac`, and `jar`.

As an example, the `jar` command can be used to create a multi-release JAR containing two versions of the same class compiled for both Java 8 and Java 9, albeit with a warning telling that the classes are identical:

This creates an MRJAR named MR.jar with the following contents:

Let us now create a class called Main that prints the URL of the SampleClass, and add it for the Java 9 version:

If we compile this class and re-run the JAR command, we get an error:

It turns out that the `jar` tool prevents adding public classes to versioned entries if they are not added to the base entries as well. This is done so that the MRJAR exposes the same public API for the different Java versions. Note that at runtime, this rule is not required. It may be only applied by tools like `jar`. In this particular case, the purpose of `Main` is to run sample code, so we can simply add a copy in the base entry. If the class were part of a newer implementation that we only need for Java 9, it could be made non-public.

To add Main to the root entry, we first need to compile it to target a pre-Java 9 release. This can be done using the new `\--release` option of `javac` (see JEP 247 - Compile for Older Platform Versions):

Running the Main class shows that the SampleClass gets loaded from the versioned directory:

## Remove the JVM TI hprof Agent (JEP 240)

The hprof JVM native agent was removed. Before Java 9, it could be used to dump the heap or profile the CPU. The reason it was removed is the existence of better alternatives. For example, jmap can do the heap dump, while JVisualVM can be used to profile running applications.

To demonstrate the impact of removing this agent, we can run a Java program with the hprof agent enabled (i.e. using the option `-agentlib:hprof`) on Java 8 and then on Java 9 (which is added on my system path):

In all cases, this agent was not an official part of the JDK and it was rarely used by existing applications.

## Remove the jhat Tool (JEP 241)

The `jhat` tool, which could be used to browse a heap dump in a web browser was removed, since better alternatives exist. The tool was marked experimental and subject to removal in previous releases.

## Compile for Older Platform Versions (JEP 247)

Before Java 9, we used to apply `-source` to tell it to use the selected language specification and `-target` to generate a certain version of bytecode. However, this can still lead to runtime issues as the compiler will link compiled classes to platform APIs of the current version of the JDK (unless you override the boot classpath). In Java 9, these options are replaced with one simple option `\--release` to be able to compile for an older version.

`\--release` is equivalent to `-source N -target N -bootclasspath <bootclasspath-from-N>`

JDK 9 makes this possible by maintaining some signature data about APIs from old releases, specifically under `$JDK_HOME/lib/ct.sym`.

## G1 as Default Garbage Collector (JEP 248)

Prior to Java 9, the default garbage collector was typically the Parallel GC on server VMs and the Serial GC on client ones. On Java 9, server VMs will use G1 as the default, which was introduced in Java 7. G1 is a parallel and low-pause garbage collector that works especially well for multi-core machines with big heap sizes. For an overview of the G1 collector, see <http://www.oracle.com/technetwork/tutorials/tutorials-1876574.html>. In addition to this feature, the Concurrent Mark Sweep (CMS) collector was deprecated.

## Multi-Resolution Images (JEP 251)

A new interface `[MultiResolutionImage](http://download.java.net/java/jdk9/docs/api/java/awt/image/MultiResolutionImage.html)` is added with a base implementation `[BaseMultiResolutionImage](http://download.java.net/java/jdk9/docs/api/java/awt/image/BaseMultiResolutionImage.html)` that can encapsulate several image variants with different sizes. This interface can be used to select the best image variant given certain width and height values.

## Compact Strings (JEP 254)

An internal optimization is applied to the `String` class to reduce memory consumption. The idea is that most String objects contain characters that do not need 2 bytes to represent. The change consists of replacing the internal character array with a byte array, plus an extra byte that denotes the encoding of the byte array: either Latin-1 which takes up 1 byte, or UTF-16, which takes up 2 bytes. The `String` class will determine which encoding based on the content to be stored.

This is expected to reduce the size of heap memory in existing applications that rely heavily on strings, and should also reduce time spent on garbage collection. This change is internal and does not affect the external API of `String` and its related classes such as `StringBuilder` or `StringBuffer`.

To disable compacting strings, the option `-XX:-CompactStrings` can be passed to VM.

## Stack-Walking API (JEP 259)

Prior to Java 9, access to the thread stack frames was limited to an internal class `sun.reflect.Reflection`. Specifically the method `sun.reflect.Reflection::getCallerClass`. Some libraries rely on this method, which is deprecated. An alternative standard API is now provided in JDK 9 via the `[StackWalker`](http://download.java.net/java/jdk9/docs/api/java/lang/StackWalker.html) class, and is designed to be efficient by allowing lazy access to the stack frames. Some applications may use this API to traverse the execution stack and filter on classes. Two methods are of interest in this class:

  * `public <T> T walk(Function<Stream<StackFrame>, T> function);` which allow traversing a stream of stack frames for the current thread, starting from the top frame, and applying the given Function on the stream.
  * `public Class<?> getCallerClass();` which returns the class that invoked the method that calls this method.

This class is thread-safe, so multiple threads can use the same instance to walk their stacks.

For example, the following prints all stack frames of the current thread:

**Output:**

`test.BarHelper 26 bar`

`test.FooHelper 19 foo`

`test.StackWalkerExample 13 main`

The following prints the current caller class. Note that in this case, **the `StackWalker` needs to be created with the option `RETAIN_CLASS_REFERENCE`, so that `Class` instances are retained in the `StackFrame` objects**. Otherwise, an exception would occur.

**Output:**

`class test.FooHelper`

A couple of other options allow stack traces to include implementation and/or reflection frames. This may be useful for debugging purposes. For instance, the first example includes some reflection to invoke `FooHelper`, but the reflection methods were not shown in the output. We can add the `SHOW_REFLECT_FRAMES` option to the `StackWalker` instance upon creation so that the frames for the reflective methods are printed as well:

**Output:**

`test.BarHelper 27 bar`

`test.FooHelper 20 foo`

`jdk.internal.reflect.NativeMethodAccessorImpl -2 invoke0`

`jdk.internal.reflect.NativeMethodAccessorImpl 62 invoke`

`jdk.internal.reflect.DelegatingMethodAccessorImpl 43 invoke`

`java.lang.reflect.Method 563 invoke`

`test.StackWalkerExample 14 main`

Note that line numbers for some reflection methods may not be available so `StackFrame.getLineNumber()` may return negative values.

## Encapsulate Internal APIS (JEP 260)

Types whose packages start with `sun.` (and some starting with com.sun.) are internal to the Java platform. The Java development team has long discouraged their use since they are not supported and vary from implementation to another. Now, most of these classes have been encapsulated in modules that don't export them for code outside the JDK. This means that existing code that relies on them will break; however this decision was based on the analysis that these APIs are very rarely, or either they have official replacements that exist prior to JDK 9. Exceptionally, the following internal APIs remained exported and placed in a separate module, and for those have supported replacements in JDK 9 they have been deprecated and may be encapsulated or removed in JDK 10:

  * `sun.misc.{Signal,SignalHandler}`
  * `sun.misc.Unsafe`
  * `sun.reflect.Reflection::getCallerClass`
  * `sun.reflect.ReflectionFactory.newConstructorForSerialization`

These APIs have been exported to public use because they are heavily used by some libraries, notably `Unsafe`. They are used to perform intrinsic JVM operations that are otherwise impossible to achieve.

## Reactive Stream Flow API (JEP 266)

A standard set of interfaces corresponding to the [reactive-streams](http://www.reactive-streams.org/) specification have been introduced nested under the `[Flow`](http://download.java.net/java/jdk9/docs/api/java/util/concurrent/Flow.html) class. These interfaces define a publish-subscribe mechanism that allows asynchronous flow-controlled communication between producers and consumers of data streams.

  1. `[Flow.Publisher`](http://download.java.net/java/jdk9/docs/api/java/util/concurrent/Flow.Publisher.html): specifies a producer of data items and has one method `subscribe(Flow.Subscriber subscriber)` that adds a subscriber to be sent items.
  2. `[Flow.Subscriber](http://download.java.net/java/jdk9/docs/api/java/util/concurrent/Flow.Subscriber.html)`: specifies a consumer of data items, and defines four methods: 
    1. `[onSubscribe(Flow.Subscription subscription)`](http://download.java.net/java/jdk9/docs/api/java/util/concurrent/Flow.Subscriber.html#onSubscribe-java.util.concurrent.Flow.Subscription-): invoked upon subscription of the subscriber by the publisher, and passes an instance of a `[Flow.Subscription`](http://download.java.net/java/jdk9/docs/api/java/util/concurrent/Flow.Subscription.html) to allow the subscriber to control the flow.
    2. `[onComplete()`](http://download.java.net/java/jdk9/docs/api/java/util/concurrent/Flow.Subscriber.html#onComplete--): invoked when all items have been sent by the publisher and no further items are to be received.
    3. `[onError(Throwable throwable)](http://download.java.net/java/jdk9/docs/api/java/util/concurrent/Flow.Subscriber.html#onError-java.lang.Throwable-)`: invoked when an error occurs on this subscription. No subsequent items are received.
  3. `[Flow.Subscription`](http://download.java.net/java/jdk9/docs/api/java/util/concurrent/Flow.Subscription.html): represents a subscription and can be used by the subscriber to control the flow of data, and defines two methods: 
    1. `[request(long n)`](http://download.java.net/java/jdk9/docs/api/java/util/concurrent/Flow.Subscription.html#request-long-): can be invoked by the consumer to demand up to `n` items to be sent from the publisher. The number may be < `n` if the publisher finished sending all items.
  4. `[Flow.Processor`](http://download.java.net/java/jdk9/docs/api/java/util/concurrent/Flow.Processor.html): implements both a Publisher and a Subscriber and is used to transform data items. It can be used as a medium between a publisher and a subscriber.

Using this model of communication, the subscriber is more in control of the flow of data so that the rate of messages can be handled more efficiently. There is one additional utility class `[SubmissionPublisher`](http://download.java.net/java/jdk9/docs/api/java/util/concurrent/SubmissionPublisher.html) that can be used by item generators that want to publish their data. This class implements the `Flow.Publisher` and `AutoCloseable` interfaces and can be closed to complete sending its items.

## Convenience Factory Methods for Collections (JEP 269)

The interfaces `List`, `Set` and `Map` have been enriched for factory methods for immutable collections:

  1. 12 Overloaded `of(...)` factory methods for `Set` and `List`. One with a varargs parameter.
  2. 11 Overloaded `of(...)` factory methods for Map that take key and value arguments. Plus one that takes a varargs of `Entry` objects `ofEntries(Entry<? extends K, ? extends V>... entries)`.

The returned collections are instances of nested types defined under `java.util.ImmutableCollections`. This class is package-private so it cannot used to check if the collection is immutable. This is left as an implementation detail of your application.

### Enhancements to Streams

Apart from collections, new methods were added to `java.util.stream.Stream<T>`. The first two are normally intended to be used when the stream is [ordered](https://docs.oracle.com/javase/8/docs/api/java/util/stream/package-summary.html#Ordering):

#### `Stream<T> takeWhile(Predicate<? super T> predicate)`

This method returns, for an ordered stream, a stream that consists of the longest _prefix_ of elements that match the give predicate. The returned stream consists of the prefix of elements matching the predicate in that order. If the original stream is unordered, the order of elements is nondeterministic; the implementation is free to return any subset of elements that matches the predicate. However, if it happens that all elements match the predicate then the returned stream will consist of the same sequence of elements of the original (in the same order). If no element matches the predicate, an empty stream is returned.

An example that returns the first 5 integers of an ordered infinite stream:

**Output:**

`0`

`1`

`2`

`3`

`4`

Example with an unordered stream:

**Output:**

`3`

`2`

`1`

`0`

Note that if we run this last example, it may return any other result that excludes 5.

#### `Stream<T> dropWhile(Predicate<? super T> predicate)`

This method does the opposite. It returns, for an ordered stream, a stream consisting of the elements remaining after dropping the longest prefix of elements matching the predicate. If the original stream is unordered, the behavior is indeterministic; the implementation is free to drop any subset of elements matching the predicate and return the remaining elements in the stream.

Example using an ordered stream:

**Output:**

`5`

`6`

`7`

`8`

`9`

Example using an ordered stream:

**Output:**

`5`

`4`

Note that if we run this last example, it may return some other stream that contains 5.

#### `Stream<T> iterate(T seed, Predicate<? super T> hasNext, UnaryOperator<T> next)`

This method returns an ordered stream that applies iteratively the predicate starting on an initial value, until the predicate returns a false with the subsequent increment specified by the `UnaryOperator`. It is conceptually similar to the traditional for loop:

#### `Stream<T> ofNullable(T t)`

This method returns the given element if not null; otherwise an empty stream.

### Enhancements to Optional

Three new methods were added to Optional:

#### `void ifPresentOrElse(Consumer<? super T> action, Runnable emptyAction)`

If a value is present, it performs the given action with the value. Otherwise, it performs the given empty-based action.

#### `Optional<T> or(Supplier<? extends Optional<? extends T>> supplier)`

If a value is present, it returns an `Optional` describing the value. Otherwise, it returns an `Optional` produced by the supplying function.

#### `Stream<T> stream()`

If a value is present, it returns a sequential `Stream` containing only that value. Otherwise, it returns an empty `Stream`.

## Enhanced Deprecation (JEP 277)

The following elements have been added to the @Deprecated annotation to provide more information about the deprecation status:

1\. `forRemoval()` If true, the deprecated API is intended to be removed in a future JDK release.

2\. `since()` which indicated since which release this API has been deprecated.

As part of this JEP, some existing API elements have been planned for deprecation, such as legacy collections (e.g. `Vector` and `Hashtable`); some deprecated elements have been marked as for removal such as `Thread.stop()` and `Thread.destroy()`.

Furthermore, a new utility `[jdeprscan`](https://docs.oracle.com/javase/9/tools/jdeprscan.htm) has been added in the JDK tools to scan a JAR file or a set of classes for usage of deprecated code. Note that it only scans for deprecated code from the standard libraries.

## Spin-Wait Hints (JEP 285)

This feature introduces a new method in `java.lang.Thread` called `[onSpinWait()](http://download.java.net/java/jdk9/docs/api/java/lang/Thread.html#onSpinWait--)`, which allows application code to provide a hint to the JVM that it running in a spin-loop, meaning it is busy waiting for some event to occur. The JVM can benefit from this hint to execute some intrinsic code that leverages hardware platform specific instructions. For example, x86 processors can execute a PAUSE instruction to indicate spin-wait, which can improve performance.

Note that the method `onSpinWait` does nothing. It is simply marked as an intrinsic candidate (using the `jdk.internal.HotSpotIntrinsicCandidate` annotation) to indicate to the JVM that it can replace it with native code optimized for the target platform. The method is just a hint, so the JVM is free to simply do nothing. A typical scenario where this method may be used is illustrated in the docs:

## Applet API Deprecated (JEP 289)

Due to the decreasing support of Java plug-ins by web browsers, the Applet API is deprecated. However, there is no intention to remove it in the next major release, so there is no `forRemoval = true` in the `@Deprecated`.

## Conclusion

And those are the interesting bits! Of course, most people are looking forward to Project Jigsaw, but Java 9 will expand far beyond modules. Again, if I missed anything that you are excited about, please let me know in the comments.
