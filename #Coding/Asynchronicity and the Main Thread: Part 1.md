# Asynchronicity and the Main Thread: Part 1

_Captured: 2015-11-19 at 19:51 from [www.figure.ink](http://www.figure.ink/blog/2015/11/15/asynchronicity-and-the-main-thread-part-1)_

Here's bit of advice we should all follow if we want to reduce bugs and increase the stability of our apps:

> "Do everything on the main thread, always."

This might raise a few eyebrows, as it seems to run contrary to another common bit of advice often given to iOS developers:

> "Never block the main thread, ever."

Enlightenment comes when we realize the two are not mutually exclusive. We're free to do all the work we please on the main thread -- just as long as we don't block it.

Fair enough. But how can we run tasks on main _and_ keep it responsive? Asynchronicity is the answer.

Let's say we want to write an app that downloads [this recreation of the Final Fantasy IV map](http://elemental79.deviantart.com/art/Final-Fantasy-IV-Overworld-568682564) because it's awesome. If we download it _synchronously_, the thread we run it on has to wait until the download completes before it can move on. Essentially, we _block_ the thread from the moment the download starts until the last byte is transferred.

But that map contains a full 30mb worth of pixels! If we download it on the main thread, we can expect it to freeze our interface for a few seconds at least… and that's over wifi. On a dodgy cell connection, it'd probably block main long enough to crash the app.

That certainly sounds like a deal breaker. Guess it's time to spin up something on a background thread, right?

Not necessarily. The trick is, our download is sitting idle for most of the 3-5 seconds it's blocking the thread. Network connections are high-latency and therefore inherently bursty. For every millisecond of requests sent there's around 200-600ms of just waiting around for a response to come back.

We can reclaim those idle milliseconds by making our download asynchronous. Unlike its synchronous counterpart, an _asynchronous_ download returns control to the thread as soon as it's called. Then, as time goes on, it only asks for the thread's attention when something needs to happen, like a request needs to be sent or some chunk of the download needs to be written to disk. The rest of the time, the thread is free to do other work, keeping it responsive.

In other words, as long as a task spends a lot of its time doing nothing, we can call it asynchronously on the main thread without blocking it. Thankfully, it turns out "nothing" is exactly what most tasks do for the majority of their time!

Think of displaying a dialog, for example. There's a few milliseconds of work at the beginning to show it on the screen. And it'll take a few milliseconds at the end to process a user's tap. But for the many seconds in between? It's just waiting, doing nothing.

Or animations. Even if we're animating a scene at a smooth 60 frames per second _and_ taking a full 10ms to prepare each frame, our animation is still spending 1/3 of its time twiddling its thumbs, waiting.

With so many every-day tasks benefitting from asynchronicity, it is perhaps no surprise that the Cocoa frameworks are chock-full of wonderfully asynchronous APIs. Networking with `NSURLConnection/Session`; displaying stuff with `UITableView`, `UIAlertView/Controller`, etc.; processing input via `UITextField/View`… if it has a delegate or takes a completion handler, chances are it's operating asynchronously.

In fact, most of the Cocoa code we write is either already asynchronous or can be made so by looking up its documentation and [following the "important" instructions in the discussion section](https://developer.apple.com/library/ios/documentation/Cocoa/Reference/Foundation/Classes/NSData_Class/index.html#//apple_ref/occ/clm/NSData/dataWithContentsOfURL:). So if step 1 towards making our apps safer and less crashy is to prefer asynchronous APIs over their synchronous counterparts, we're already 90% of the way there.

Once everything is asynchronous, step 2 is pretty easy, too. We _could_ try to stop thinking in terms of the total synchronous time it takes a task to complete, and instead reason about the aggregate of work it actually performs, interleaved between other work on a thread -- but I usually just throw everything on the main thread and see how it performs. I've yet to be disappointed.

Step 3 is more complicated. Now that we have a bunch of asynchronous tasks on a single thread, it turns out to be surprisingly hard to answer questions like "What order will this happen in?" or "When would it be safe to load this?"

Managing that complexity will be the topic of next week's post.
