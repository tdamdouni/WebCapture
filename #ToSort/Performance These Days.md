# Performance These Days

_Captured: 2016-04-21 at 22:36 from [inessential.com](http://inessential.com/2016/04/21/performance_these_days)_

[Mike Ash reports](https://mikeash.com/pyblog/friday-qa-2016-04-15-performance-comparisons-of-common-operations-2016-edition.html) that objc_msgSend takes 2.6 nanoseconds on his Mac and 2.7 nanoseconds on his iPhone. This shouldn't come as much surprise -- we've known since [Mike's first report in 2007](https://www.mikeash.com/pyblog/performance-comparisons-of-common-operations.html) that objc_msgSend is fast. (Though this function isn't the only measure of Objective-C's speed relative to other languages, it's indicative.)

So Objective-C is fast -- but it hardly matters, because almost all of your code might as well be written in Ruby. (Or in any relatively slow scripting language.)

Pushing a view controller onto a navigation controller takes the time it takes. Your text fields won't draw their strings any faster just because you're using Swift instead of Python. Hitting the disk is still hitting the disk.

There may be some things your app does that need to be super-fast. Parsing email messages or RSS feeds, for instance. Processing audio. You wouldn't want to use a scripting language for those -- you'd want something like Objective-C or Swift, or even C or C++ -- to make those parts fast. (And you probably want to move those things off the main thread.)

But that's the minority of your app, by far. Imagine a typical RSS reader -- what percentage of the code makes up the feed and OPML parsers? Well under 1%, I'd bet. The rest might as well be in Lua or JavaScript, and users would never feel the difference, because there would hardly _be_ a difference.

Maybe Swift is faster than Objective-C, or will be. But that _also_ hardly matters.

#### Performance does matter

That's not to say performance doesn't matter. It totally matters. If an RSS reader blocks the main thread while parsing feeds -- and is slow at parsing feeds -- it's going to suck.

But making things fast has to do with choosing fast data structures and algorithms, moving things off the main thread when needed, and figuring out which of the other things Mike Ash lists as slow (such as object creation and disk access) you can avoid. Switching to Swift -- or whatever -- isn't going to make a slow algorithm appreciably faster.

#### Another kind of performance

Instead of language performance the focus should be on developer productivity. _Developer_ performance. That's the thing that counts these days.

Swift makes a bunch of leaps forward here and some leaps back. Awesome things: type inference (I could stop right there and be done); not having separate header files; easier syntax for blocks; `let` for immutable variables; `map` and `filter` (though easily done in Objective-C); protocol extensions; etc.

And yet it's _stuffier_ than Objective-C, and in some respects feels like a lower-level language. We've given up dynamic dispatch (largely) and gained optionals and a stricter type system. We've also given up simplicity (assuming you know C, and you should, the "Objective" part is pretty small) for a much more complex language.

Objective-C has way too much housekeeping, yes. Totally. And yet, in Swift, I sometimes feel like I'm filling out a form in triplicate before I can use a variable, or faxing various department heads before I can call a method.

#### Where Swift is awesome and not-awesome

As a [system programming language](https://en.wikipedia.org/wiki/System_programming_language), Swift is, I strongly suspect, utterly brilliant. I _want_ that kind of programming to be buttoned-down. Absolutely.

Swift seems like the answer to the question: "What would a language for system programming look like that's both safer and better for productivity than C and C++?"

The problem is, the answer to that particular question is not necessarily the same as the answer to the question, "What would a language for app programming look like that's both safer and better for productivity than Objective-C?"

The _safer_ part is easy: remove the C. _Huge_ win right there.

But I think Swift otherwise gives and takes away -- we get type inference and all the lovely things I mentioned before, but we end up fighting the type system, standing on our heads to deal with optionals, and working with a language that's much larger (demonstrably) than is needed for writing great apps. It solves a whole bunch of problems that didn't need solving (for app-writing).

I'd rather we focused harder on making writing high-quality apps easier. A scripting language, or something spiritually close, that took the best parts of Swift, but was much smaller and simpler, more supple, that ran on the Objective-C runtime -- dynamic dispatch and all -- would have been ideal. I could _fly_ in that language.

Yes, I realize that would have meant pushing some errors from compile time to run time, in exactly the same way Objective-C does right now.

But I don't care -- I'd take that trade-off every single day of the week.

[Archive](http://inessential.com/archive)
