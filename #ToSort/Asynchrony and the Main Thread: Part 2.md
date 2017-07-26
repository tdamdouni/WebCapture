# Asynchrony and the Main Thread: Part 2

_Captured: 2015-11-27 at 11:21 from [www.figure.ink](http://www.figure.ink/blog/2015/11/22/asynchrony-and-the-main-thread-part-2)_

[Last week](http://www.figure.ink/blog/2015/11/15/asynchronicity-and-the-main-thread-part-1) we talked about how we could run bursty asynchronous tasks on the main thread without blocking it. This is super-easy if we have a single task that exists in isolation -- let's say, some JSON we need to download. For example:[1](http://www.figure.ink/blog/2015/11/22/)
    
    
    if let url = NSURL(string: "http://example.com"){
      let req = NSURLRequest(URL:url)
      let main = NSOperationQueue.mainQueue()
      NSURLConnection
        .sendAsynchronousRequest(req, queue: main){
        //Profit!
      }
    }

That's pretty straight forward. The problem is, in applications, nothing happens in isolation. Raw JSON bytes don't do us any good. We need to parse them. And we probably want to update our interface to reflect the downloaded data. This would be simple enough if everything were synchronous:
    
    
    //Timing is easy in the synchronous world
    //(but blocks the main thread) 
    let data = downloadJSON()
    let json = parseJSON(data)
    myController.updateUI(json)

To prevent blocking the main thread, though, we have to make these operations asynchronous. But now ordering is difficult. In an asynchronous world, the data isn't downloaded by the time `downloadJSON()` returns. The JSON isn't parsed by the time `parseJSON()` gets back to us. We have to rely on completion blocks (or the [delegate pattern](https://en.wikipedia.org/wiki/Delegation_pattern)) to let us know when our work is completed:
    
    
    NSURLConnection
    .sendAsynchronousRequest(req, queue: main){
    (res, data, error) in
      parseJSON(data){ json in
        myController.updateUI(json)
      }
    }

Chaining one operation on the completion of another like this not only leads to a lot of confusing indentation, but now our controller code is all mixed up with our parsing code which is all up in our networking code. It's a [complected](https://en.wiktionary.org/wiki/complect#Verb) mess that only gets worse the more dependencies we add.

What we need is an [abstraction](https://dl.dropboxusercontent.com/u/364098/Abstraction.png) around the life-cycle of our tasks. One that lets them run asynchronously, but also manages their completions such that we can queue them to run in a specific order.

Thankfully, `NSOperation` (and the associated `NSOperationQueue` machinery) lets us do just that.

## NSOperation, Queues, and Dependencies

An `NSOperation` encapsulates the execution of isolated chunks of work. We can subclass[2](http://www.figure.ink/blog/2015/11/22/) `NSOperation` to do pretty much any kind of work we want, then add instances of our subclass to an `NSOperationQueue` to start them processing.

Of course, encapsulating work and processing it isn't exactly rocket science. We've been doing it forever with simple functions. The magic of `NSOperation/Queue` is that it tracks the status of our operations, only starting them when they're ready, and taking note of when they finish.

That lets us set up chains of dependencies with `[addDependency` ](https://developer.apple.com/library/ios/documentation/Cocoa/Reference/NSOperation_class/index.html#//apple_ref/occ/instm/NSOperation/addDependency:) like so:
    
    
    let myDownloadOp = DownloadOperation()
    let myParseOp = ParseOperation()
    let myUpdateOp = UpdateOperation()
    let queue = NSOperationQueue.mainQueue()
    myUpdateOp.addDependency(myParseOp)
    myParseOp.addDependency(myDownloadOp)
    queue.addOperations(
      [myDownloadOp, myParseOp, myUpdateOp],
      waitUntilFinished:false)

Because of our dependencies, `mainQueue` will only execute our parse operation after the download operation has completed. Likewise, it will only start the update operation after the parse operation has completed. Note that everything is self-contained in its own operation and nothing is nested.

More important in the context of our current conversation, this is true _even if_ all these operations are _asynchronous_. And, as long as we use `[mainQueue()`](https://developer.apple.com/library/ios/documentation/Cocoa/Reference/NSOperationQueue_class/index.html#//apple_ref/occ/clm/NSOperationQueue/mainQueue) to process all these operations, everything will happen on the main thread.

In other words, `NSOperation/Queue` lets us run asynchronous operations on the main thread while maintaining complete control over their timing and order of execution.[3](http://www.figure.ink/blog/2015/11/22/)

Which means we should be ready to go. And we would be… if the documentation around `NSOperation` weren't a confusing and self-contradictory hodgepodge.

## Making Sense of Asynchronous Operations

Here I'm going to try to synthesize, as best I can, what I've learned about implementing asynchronous `NSOperation` subclasses from the maze of documentation. If you're more interested in the "what" than the "how", feel free to skip to the next section.

By default, `NSOperation` assumes that when an operation hits the end of its `start()` method,[4](http://www.figure.ink/blog/2015/11/22/) it is complete.[5](http://www.figure.ink/blog/2015/11/22/) Making its `concurrent` property return `true` is supposed to indicate an operation's task lives beyond the scope of `start()` -- in other words, it's _asynchronous_ -- and thus shouldn't be considered complete just because `start()` has returned.

Because such an operation would be responsible for _manually_ marking itself as completed, operation queues used to assume concurrent operations managed their own internal thread. It would be redundant for a queue to create its own thread to run a concurrent operation like this, so "concurrent" used to also mean "Tell the queue not to create a new thread for this operation."

Then operation queues got rewritten to use Grand Central Dispatch under the covers. As a result, [the documentation says](https://developer.apple.com/library/ios/documentation/Cocoa/Reference/NSOperationQueue_class/index.html#//apple_ref/occ/cl/NSOperationQueue), "Operations are always executed on a separate thread, regardless of whether they are designated as asynchronous or synchronous operations."[6](http://www.figure.ink/blog/2015/11/22/)

Because the `concurrent` property was being ignored when it came to threading, it's only remaining job was to indicate whether an operation was asynchronous or not. "Concurrent" and "asynchronous" technically mean different things, though. So in iOS 7, the more semantically precise `asynchronous` got added to the API, to be used in place of `concurrent`.[7](http://www.figure.ink/blog/2015/11/22/)

The only problem being, neither the `asynchronous` nor `concurrent` properties seem to _do_ anything.[8](http://www.figure.ink/blog/2015/11/22/) Operations with either of these set still report themselves as completed whenever `start()` returns (whether added to a queue or launched manually, [contrary to the docs](https://developer.apple.com/library/ios/documentation/Cocoa/Reference/NSOperation_class/index.html#//apple_ref/doc/uid/TP40004591-RH2-SW15)). The only way to make sure an operation doesn't finish when `start()` completes is to override `start()` itself (being careful not to call `super`).

## Making a New Start

And so, the most important thing we have to do when implementing an asynchronous subclass of `NSOperation` is to override its `start()` method. But `start()` is actually responsible for a few things.

  1. Calling the main implementation in `main()`
  2. Updating the operation's state to `executing` when it starts.
  3. Changing the operation's state to `finished` when it's done.
  4. Sending KVO notifications for each of the above.

Calling `main()` is easy. Our initial `start()` method could look like this:
    
    
    override func start() {
      main()
    }

To model state, we're going to create an enumeration, a property to hold it, and override the derived properties `executing` and `finished`:
    
    
    enum State{
      case Waiting, Executing, Finished
    }
    
    var state = State.Waiting
    
    override var executing:Bool{
      return state == .Executing
    }
    
    override var finished:Bool{
      return state == .Finished
    }

And update our `start()` to shift us in to "executing" mode before calling main:
    
    
    override func start() {
      state = .Executing
      main()
    }

That's great for setting up "executing". But how do we mark our operation as "finished"? Remember, this is going to be asynchronous, so we don't technically know when the operation is going to end. The best we can do is create a method that subclasses will have to call when their task is complete:
    
    
    func finish(){
      state = .Finished
    }

This mostly works. But `NSOperationQueue` (and anything else using our operation) expects to be notified about changes to our state through KVO. And KVO doesn't get automatically triggered when the value of a derived property changes. So we have to send those notifications ourself:
    
    
    var state = State.Waiting{
      willSet{
        switch(state, newValue){
        case (.Waiting, .Executing):
          willChangeValueForKey("isExecuting")
        case (.Waiting, .Finished):
          willChangeValueForKey("isFinished")
        case (.Executing, .Finished):
          willChangeValueForKey("isExecuting")
          willChangeValueForKey("isFinished")
        default:
          fatalError( ... )
        }
      }
      didSet{
        switch(oldValue, state){
        case (.Waiting, .Executing):
          didChangeValueForKey("isExecuting")
        case (.Waiting, .Finished):
          didChangeValueForKey("isFinished")
        case (.Executing, .Finished):
          didChangeValueForKey("isExecuting")
          didChangeValueForKey("isFinished")
        default:
          fatalError( ... )
        }
      }
    }

This simply [sets up two observers](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Properties.html#//apple_ref/doc/uid/TP40014097-CH14-ID262) on our `state` property, one for before it gets changed, the other for after. Depending on which state transitions to what, we call [the appropriate KVO notifications](https://developer.apple.com/library/mac/documentation/Cocoa/Reference/Foundation/Protocols/NSKeyValueObserving_Protocol/#//apple_ref/doc/uid/20002299-SW8) (or bail with an error).

There are a few things we're playing fast and loose with here that wouldn't fly in a multi-threaded environment. There's no locking around our `state` property for one thing. And we've given no consideration to what happens if we're initialized by one thread, while `start()` is called by another.

That's alright because the whole point of this operation is to be run on the main queue. But we should encode that assumption into our class. Also, as a best practice, we should check that our operation hasn't been cancelled before we begin:
    
    
    override func start() {
      guard NSThread.isMainThread() else{
        fatalError( ... )
      }
    
      guard !cancelled else{
        return
      }
    
      state = .Executing
      main()
    }

And that's more or less it! From here, subclasses can override `main()` to spin up whatever asynchronous task they want, and as long as it calls `finish()` when it completes, everything will just work.

Exactly what these subclasses will look like is a topic for another week. But for now, [here's a gist of the AsyncOperation we created together](https://gist.github.com/jemmons/b1c84130a7dcf0fc1f11).

1: We should all be using `NSURLSession`-based networking in the real world. I'm using `NSURLConnection` in my snippets because it happens to have a more example-friendly interface, but don't take that as an endorsement of best practice. [↩︎](http://www.figure.ink/blog/2015/11/22/)

2: `NSBlockOperation` is a great way to quickly experiment with `NSOperation` and `NSOperationQueue` without all the hassle of subclassing. But a block operation marks itself as `finished` as soon as its block returns, so it's not well suited for asynchronous tasks. [↩︎](http://www.figure.ink/blog/2015/11/22/)

4: Including `main()` which is, by default, called by `start()` [↩︎](http://www.figure.ink/blog/2015/11/22/)

5: "Complete" being defined as a state where `isFinished` is `true` and KVO notifications have been dispatched to that effect. [↩︎](http://www.figure.ink/blog/2015/11/22/)

6: Note the main queue is an exception. Operations executed on the main queue always run on the main thread. Which, incidentally, is what allows us to ignore most of this nonsense. [↩︎](http://www.figure.ink/blog/2015/11/22/)

7: Technically, the two are synonyms as far as `NSOperation` is concerned. Overriding `concurrent` to return `true` does the same for `asynchronous` and vice-versa. [↩︎](http://www.figure.ink/blog/2015/11/22/)

8: As a matter of style, we still override `asynchronous` to return `true` in our example. But it's just as a nod toward semantic correctness. There's no functional benefit to doing so that I can find. [↩︎](http://www.figure.ink/blog/2015/11/22/)
