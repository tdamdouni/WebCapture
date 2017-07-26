# Shoot the Heap

_Captured: 2015-11-06 at 09:41 from [www.russbishop.net](http://www.russbishop.net/shoot-the-heap)_

### _Leaks is a filthy liar_

## Fall Cleaning

This is a blog post I started many months ago and never got around to finishing; please forgive any outdated screenshots or references. The core ideas are still relevant so I'm gonna go ahead and post it. The bug in UIKit that confused Leaks into missing the cycle was supposedly fixed but a good Software Engineer should always be prepared to roll up their sleeves and figure things out the hard way if the tools won't cooperate.

## Intro

Ah, the joys of non-garbage-collected languages. I spent some time debugging a retain cycle today and thought I'd share the process I used to locate and fix the cycle. Along the way, we'll see how the Leaks instrument is a dirty _filthy_ liar, watch as Xcode inexplicably mixes old and new code into the same binary yielding _impossible_ behavior, and finally figure out how to use heap shots (or as the new Allocations instrument calls them _Generations_) to find the retain cycle even in the midst of a retain/release history thousands of entries long.

## The Setup

The bug report started off innocently enough: When projects were removed from the local device cache they would occasionally pop back into the local list of their own accord. Words like **"occasionally"** and **"sometimes"** usually cause the little hairs on the back of my neck to stand up, but in this case a list of repro steps was located rather quickly and I set about tracking down the problem.

It was immediately obvious that the project's model object was staying alive and being retrieved via a weak reference, despite all `UIViewController` instances (and everything else that might be holding onto the model) submitting to `dealloc` like good little objects. A weak reference that stubbornly refuses to nil out is a sure sign that someone somewhere is keeping the object alive. Time to fire up Instruments and see what we can find.

## Liar Liar, Leaks on Fire

![Leaks being hateful](https://silvrback.s3.amazonaws.com/uploads/c288b40d-19b1-4774-ae6a-3a58a004584d/Screen%20Shot%202015-03-06%20at%203.05.30%20PM_medium.png)

> _Leaks being hateful_

Life as a Software Engineer is beset by constant roadblocks. The first was the failure of Leaks to function on-device with iOS 8. After the first snapshot, leaks simply gets stuck on _Analyzing Process_. _Update: I never did get this to work on device_.

Very well, simulator it is then. I'm greeted with a few framework leaks in `NSDateComponents` but otherwise nothing of interest which is _very_ disappointing since I know for a fact that something is keeping the project model alive. I can follow the repro steps from login back to logout and I continue to see the `# Persistent` column for the model increasing each time I do.

## Allocations: Initially Useless

I know the model is staying alive; the question is why? My first thought is to look at the retain/release history in Allocations. Often you can spot the problem just by looking at where the object is retained. Unfortunately the project model is used _everywhere_, so its retain history is extensive.

![Pairing retain-release in Allocations](https://www.dropbox.com/s/79swa0bt0pj6kp9/allocations_pair_unpair.gif?dl=1)

> _Pairing retain-release in Allocations_

Switching to Unpaired mode can help, but in this case the history is still too complicated for Allocations to figure out. I tried manually pairing the retain/release calls but that still wasn't helping. I spent a half hour checking call sites, pairing different ways, and getting absolutely nowhere.

## Roots & Cycles: ... And the Horse You Rode In On

At this point I went back to the Leaks instrument and took a look at the Roots & Cycles view.

![Leaks cycles sb-float](https://silvrback.s3.amazonaws.com/uploads/10570733-fe70-43af-9132-583c4a1ea352/Screen%20Shot%202015-03-06%20at%203.48.27%20PM_large.png)

> _Leaks cycles sb-float_

Unfortunately there was nothing useful, just some FMDB Sqlite blocks and other framework bits. Perhaps there are some real leaks in there, but none of it has anything to do with my problem. It was at this point I desperately wanted a way to tell Leaks that it should be looking at a _specific_ class I know is involved in a retain cycle. It seems like it ought to be smart enough to trace the history of that class and find why it is still alive.

## Allocations: The Hard Way

Let's try using the Generations feature of Allocations. By marking generations, Allocations can show you objects that were created but never destroyed during a specific period of time. I marked a generation after startup, walked through the repro steps, returned to the login view, then marked another generation. In theory everything should have been deallocated and released at that point.

Working on a hunch that a view controller might be involved, I looked for living instances of our `UIViewController` subclasses. Bam, there it was! A long-dismissed View Controller still hanging around in memory. Unfortunately a quick scan of the code revealed all delegates were weak and there were no obvious block cycles (all blocks stored by the View Controller only captured `weak` references to `self`). Just to confirm it I ran through several more repro cycles and each and every time another zombie instance of the same View Controller was left in memory.

Yet again I ran into the problem that the View Controller has thousands of `retain/release` entries. There was simply no way to filter out all the framework noise of every animation, transition coordinator, presentation coordinator, etc. I resigned myself to looking at each entry one by one, starting with the block retains contained only in my module on the assumption that it wasn't a bug in UIKit. Eventually I found the cycle! (A helper class stored a block which captured `self`; the helper class was itself stored strongly on the View Controller. A classic retain cycle that Leaks was baffled to locate).

You would think finding the cycle was a joyous moment and the end of all my woes.

You would be wrong.

## Wherein Xcode Attempts to Drive Me Insane

Proud of my achievement, I dutifully stop instruments, make the fix, then run just to make sure Xcode updates the simulator. I went back to Instruments and ran again. No dice... The same View Controller is still leaking.

Fine, I quit Instruments, Xcode, and the Simulator. Another clean and build cycle, then select "Profile" in Xcode. Nope... still leaking! Assuming there must be another similar leak elsewhere, I spent at least a half hour searching but came up empty.

Then I remembered: This is _Xcode_ we're talking about.

I dropped into the terminal and ran `fuxcode` (my script that nukes all DerivedData).

One more rebuild cycle later and Instruments confirms it: there are no more leaks.

## Conclusion

If I had just one wish, it would be for all the money in the world.

But if I had a second wish, it would be for Leaks to actually show me retain cycles; maybe it would be too noisy and useless most of the time. That's fine, just let me put in a class name that I know for a fact is involved in a retain cycle, then show it to me!
