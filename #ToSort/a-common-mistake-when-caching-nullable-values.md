# A Common Mistake When Caching Nullable Values

_Captured: 2017-12-19 at 04:48 from [dzone.com](https://dzone.com/articles/a-common-mistake-when-caching-nullable-values?edition=345100&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-18)_

Caching is hard in various ways. Whenever you're caching things, you have to at least think of:

  * Memory consumption
  * Invalidation

In this article, I want to show a flaw that often sneaks into custom cache implementations, making them inefficient for some execution paths. I've encountered this flaw in Eclipse, recently.

## What Did Eclipse Do Wrong?

I periodically profile Eclipse using [Java Mission Control (JMC)](http://www.oracle.com/technetwork/java/javaseproducts/mission-control/java-mission-control-1998576.html) when I discover a performance issue in the compiler (and I've discovered a few).

Just recently, I've found a new regression that must have been introduced with the new Java 9 module support in Eclipse 4.7.1a.

Luckily, the issue has already been fixed for 4.7.2 (<https://bugs.eclipse.org/bugs/show_bug.cgi?id=526209>).

What happened?

In that profiling session, I've found an awful lot of accesses to `java.util.zip.ZipFile` whenever I used the "content assist" feature (auto completion). This was the top stack trace in the profiler:
    
    
    int java.util.zip.ZipFile$Source.hashN(byte[], int, int)
    
    
    ZipFile org.eclipse.jdt.internal.core.JavaModelManager.getZipFile(IPath, boolean)
    
    
    ZipFile org.eclipse.jdt.internal.core.JavaModelManager.getZipFile(IPath)
    
    
    ZipFile org.eclipse.jdt.internal.core.JarPackageFragmentRoot.getJar()
    
    
    byte[] org.eclipse.jdt.internal.core.AbstractClassFile.getClassFileContent(JarPackageFragmentRoot, String)
    
    
    boolean org.eclipse.jdt.internal.core.ModularClassFile.buildStructure(...)
    
    
    void org.eclipse.jdt.internal.core.Openable.generateInfos(Object, HashMap, IProgressMonitor)
    
    
    Object org.eclipse.jdt.internal.core.JavaElement.openWhenClosed(Object, boolean, IProgressMonitor)
    
    
    Object org.eclipse.jdt.internal.core.JavaElement.getElementInfo()
    
    
    boolean org.eclipse.jdt.internal.core.JavaElement.exists()
    
    
    boolean org.eclipse.jdt.internal.core.Openable.exists()
    
    
    IModuleDescription org.eclipse.jdt.internal.core.NameLookup.getModuleDescription(IPackageFragmentRoot, Map, Function)

In fact, the profiling session doesn't show the exact number of accesses, but rather the number of stack trace samples that contained the specific method(s), which corresponds to the time spent inside of a method, not the number of calls (which is less relevant). Clearly, accessing ZIP files shouldn't be the thing that Eclipse should be doing most of the time when auto completing my code. So, why did it do it anyway?

It turns out that the problem was in the method getModuleDescription(), which can be summarized as follows:

The ZipFile access is hidden inside the `getModuleDescription()` call. A debugger revealed that the JDK's rt.jar file was opened quite a few times to look for a `module-info.class` file. Can you spot the mistake in the code?

The method gets an external cache that may already contain the method's result. But the method may also return null in case there is no module description. Which there isn't. jOOQ has not yet been modularized, and most libraries upon which jOOQ depends haven't been modularised either, nor has the JDK been modularized using what jOOQ is currently built with (JDK 8). So, this method always returns `null` for non-modular stuff.

But if it returns null, it won't put anything in the cache:

… which means the next time it is called, there's a cache miss:

… and the expensive logic involving the ZipFile call is invoked again. In other words, it is invoked all the time (for us).

## Caching Optional Values

This is an important thing to always remember, and it is not easy to remember. Why? Because the developer who implemented this cache implemented it for the "happy path" (from the perspective of someone working with modules). They probably tried their code with a modular project, in which case it worked perfectly. But they didn't check if the code still works for everyone else. And in fact, it does work. The logic isn't _wrong_. It's just not _optimal_.

The solution to these things is simple. If the value `null` encodes a cache miss, we need another `PSEUDO_NULL` to encode the actual `null` value. So, the method can be rewritten as:

… where this `PSEUDO_NULL` can be a simple `java.lang.Object` if you don't care about generics, or a dummy `IModuleDescription` in our case:

Since it will be a singleton instance, we can use identity comparisons in our method.

## Conclusion

When caching method results, always check if `null` is a valid result for the method. If it is, and if your cache is a simple `Map`, then you have to encode the `null` value with some sort of `PSEUDO_NULL` value for the cache to work properly. Otherwise, you won't be able to distinguish `Map.get(key) == null` for the cases:

  * Cache miss and Map returns `null`
  * Cache hit and the value is `null`
