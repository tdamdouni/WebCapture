# SOLID principles by example: Dependency inversion

_Captured: 2017-09-22 at 13:55 from [ilclubdellesei.wordpress.com](https://ilclubdellesei.wordpress.com/2017/09/05/solid-principles-by-example-dependency-inversion/)_

This is the last blog post about the [SOLID](https://ilclubdellesei.wordpress.com/2017/07/03/solid-principles-by-examples-introduction/) principles in object-oriented programming and we talk about the Dependency Inversion Principle (DIP).

![Screenshot_1](https://ilclubdellesei.files.wordpress.com/2017/09/screenshot_12.png)

The principle states:

> A. High-level modules should not depend on low-level modules. Both should depend on abstractions.  
B. Abstractions should not depend on details. Details should depend on abstractions.

This definition was written by Robert C. Martin in his Agile Software Development, Principles, Patterns, and Practices book.

But what does this really mean? How do we need to organize our code? Let's continue with some examples.

## Bad example

In a traditional application architecture top-level components rely on specific implementation of low-level components, for example:

1234567891011
`class` `Logger {``private` `NtfsFileSystem _fileSystem = ``new` `NtfsFileSystem ();``public` `void` `Log (``string` `text) {``var` `fileStream = _fileSystem.OpenFile (``"log.txt"``);``fileStream.Write (text);``fileStream.Dispose ();``}``}`

Everything looks good, right? We have our **Logger** class that's able to log a text message into a specific file of the file system. But we have some issues here. Our Logger class _depends_ on the specific implementation of the **NtfsFileSystem** class. What if that class needs to change because of a new Ntfs version or because of a bug that has been fixed? It's likely that our class will need to change, too! What if we need to log into another completely different type of file system? Or into a database? We realize that our code is **tightly copuled** and manteinance is difficult.

Let's apply the DIP to our architecture.

## Good example

We declare an **abstraction** (interface) like this:

1234
`public` `interface` `ILoggable``{``void` `Log(``string` `textToLog);``}`

This interface states that ILoggable classes con "Log" a text message.

Our NtfsFileSystem class becomes:

12345
`class` `NtfsFileSystem : ILoggable {``public` `void` `Log (``string` `textToLog) {``//file handling, writing and disposing.``}``}`

And our logger:

12345678910111213
`class` `Logger2 {``private` `ILoggable _logService;``public` `Logger (ILoggable logService) {``if` `(logService == ``null``) ``throw` `new` `ArgumentNullException ();``_logService = logService;``}``public` `void` `Log (``string` `text) {``_logService.Log (text);``}``}`

What we've done here is to **inject** into the constructor the log sub-system we want to use. Our **Logger2** class can work with every class that implements ILoggable. This is also very useful for unit testing purpose when we would like to remove externale dependencies and test our code in isolation (but that's outside the scope of this post).  
Our code is now **loosely-coupled** because the Logger2 class doesn't depend on a specific implementation but only on an interface.

Now we can write a program like this, for example:

123456789101112
`class` `Program () {``void` `Main () {``var` `ntfsLogger = ``new` `Logger2 (``new` `NtfsFileSystem ());``var` `noSqlLogger = ``new` `Logger2 (``new` `DbNoSql ());``ntfsLogger.Log(``"some text"``);``noSqlLogger.Log(``"other text"``);``}``}`

## TL;DR

In this blog post we explored the Dependency Inversion Principle with some examples turning some higly-coupled code into a better architecture without hard dependencies on a specific implementation. Our Logger class is more reusable and even testable!

The word Inversion comes from the fact that both the high-level and the low-level depend on abstraction and this is the opposite of the classical approach where the high-level classes depend on the low-level classes.

### SOLID posts
