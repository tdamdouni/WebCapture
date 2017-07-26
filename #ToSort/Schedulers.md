# Schedulers

_Captured: 2015-12-03 at 19:34 from [codeplease.io](http://codeplease.io/2015/11/30/schedulers/)_

When you think about ReactiveCocoa, one immediately thinks about Signals, streams of events and transformations. Although that's all there, RAC is more than meets the eye.

Lately I had to do the following:

  * Track if a user spends more than 2 seconds in a screen. 

I went with `viewDidAppear:` and `viewDidDisappear:` as the window to be tracked. The only piece missing is the actual logic that allows me to enqueue an action ( `Void -> Void`) and, if less than 2 seconds have passed, cancel it, otherwise execute it.

RAC in this scenario does most of the work via [Schedulers](https://github.com/ReactiveCocoa/ReactiveCocoa/blob/master/ReactiveCocoa/Swift/Scheduler.swift):

> A scheduler, represented by the [SchedulerType](https://github.com/ReactiveCocoa/ReactiveCocoa/blob/master/ReactiveCocoa/Swift/Scheduler.swift#L12) protocol, is a serial execution queue to perform work or deliver results upon.
> 
> [Signals](https://github.com/ReactiveCocoa/ReactiveCocoa/blob/master/Documentation/FrameworkOverview.md#signals) and [signal producers](https://github.com/ReactiveCocoa/ReactiveCocoa/blob/master/Documentation/FrameworkOverview.md#signal-producers) can be ordered to deliver events on a specific scheduler. Signal producers can additionally be ordered to start their work on a specific scheduler.
> 
> Schedulers are similar to Grand Central Dispatch queues, but schedulers support cancellation (via disposables), and always execute serially. With the exception of the `[ImmediateScheduler`](https://github.com/ReactiveCocoa/ReactiveCocoa/blob/master/ReactiveCocoa/Swift/Scheduler.swift), schedulers do not offer synchronous execution. This helps avoid deadlocks, and encourages the use of [signal and signal producer primitives](https://github.com/ReactiveCocoa/ReactiveCocoa/blob/master/Documentation/BasicOperators.md) instead of blocking work.
> 
> Schedulers are also somewhat similar to NSOperationQueue, but schedulers do not allow tasks to be reordered or depend on one another.

The implementation is less than 30 lines of code:

import Foundation

import ReactiveCocoa

final class ActionScheduler {

private var schedulerDisposable: Disposable?

private let scheduler: QueueScheduler

private let delay: NSTimeInterval

init(delay: NSTimeInterval, queue: dispatch_queue_t = dispatch_get_main_queue()) {

self.delay = delay

self.scheduler = QueueScheduler(queue: queue)

}

func start(action: Void -> Void) {

self.stop()

let date = NSDate().dateByAddingTimeInterval(delay)

schedulerDisposable = scheduler.scheduleAfter(date, action: action)

}

func stop() {

schedulerDisposable?.dispose()

}

}

Finally:
