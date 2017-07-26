# Beware the UIKit Visitors!

_Captured: 2016-05-13 at 00:57 from [blog.benjamin-encz.de](http://blog.benjamin-encz.de/post/disassembling-uikit-tintcolor-visitor/)_

#### Investigating the Cause of Quadratic Time Complexity When Adding Subviews in UIKit

Yesterday Two weeks ago we identified a performance regression in the PlanGrid app, when entering a view that dynamically adds a large amount of subviews.

I started this blog post back then, but was recently motivated to finish it quickly by seeing other developers running into this issue as well:

> My discovery for the day is iOS has an O(n^2) cost to add a subview so never have too many subviews on a view or performance goes to shit
> 
> -- Rupert H (@rpy) [May 9, 2016](https://twitter.com/rpy/status/729550705137090560)

For this blog post I wanted to isolate this issue from our code base. I was able to reproduce the issue with this minimal example inside of a blank `UIViewController`:
    
    
    override func viewDidAppear(animated: Bool) {
            super.viewDidAppear(animated)
    
            self.view.tintColor = .blueColor()
    
            for i in 1..<10000 {
                let view = UIView()
                self.view.addSubview(view)
            }
    }
    

The above example is obviously extreme, but it reveals an interesting performance issue: when setting a `tintColor` on a parent view, and not setting an explicit color on child views the performance of `addSubview` reduces itself drastically with a large amount of added subviews.

Here's what I could identify within Instrument's time profiler:

![](https://dl.dropboxusercontent.com/u/13528538/Blog/UITintColorVisitor/tint-color-visitor-highlight.png)

A majority of the time is adding subviews is spent within `[_UITintColorVisitor _visitView:]`. In this example it's 64% of the time; and the proportion only increases with the amount of subviews we're adding.

We like our custom tint color; but not enough to justify such an impact on performance. **By deactivating the custom tint color we bring the overall run time of `viewDidAppear` from our example project from over 700ms down to ~10ms.**

The same affect can be accomplished by specifying the `tintColor` on each view we're adding, which stops the expensive `_UITintColorVisitor` from stopping by too often.

## Digging into UIKit

Finding a workaround for this issue is only half of the fun. Let's try to find out what is causing these poor performance characteristics in the first place. We can start by taking a closer look at the time profiler output:

![](https://dl.dropboxusercontent.com/u/13528538/Blog/UITintColorVisitor/focus-tint-color-visitor.png)

We can see that the app doesn't spend too much time in `[_UITintColor _visitView]` itself. The majority of the time is consumed by `objc_msgSend` which indicates that this method is causing many, many method invocations or the method itself is being called extremely frequently. Further, we're spending a lot of time in `[NSArray containsObject:]` which either means that the array is being searched through too often in the first place, or that a data structure that is more efficient for lookups should be used instead of an array (e.g. a dictionary or a set).

### Breakpoints in Framework Functions

We can start by setting a breakpoint within the `[_UITintColor _visitView]` method; that will give us an idea of how often that method is called.

We can do that by setting a breakpoint early in our program to bring up the lldb console (alternatively we could use lldb from the terminal). Then we can enter the following command to set a breakpoint:
    
    
    (lldb) b -[_UITintColorVisitor _visitView:]
    

Now we can continue execution; soon we should trap into our breakpoint:

![](https://dl.dropboxusercontent.com/u/13528538/Blog/UITintColorVisitor/visit-view-breakpoint.png)

Checking how often this method is called, I quickly identified that the amount of calls grows with the amount of subviews we have added. As a next step I wanted to see which views exactly are being visited. For that we need to dive into a little bit of assembly code.

### Inspecting the Assembly Code

When stepping into the breakpoint in `-[_UITintColorVisitor _visitView:]` you are greeted with a cryptic wall of assembly code. I started out with very barebones knowledge of understanding/investigating complex assembly code, but this bug forced me to learn some tricks that hopefully are useful to you as well!

#### Running the Example App on 32-Bit Mode

As a first step, let's ensure that our app runs in **32-Bit** mode in the simulator. This architecture is known as **i386**. We choose to run the app in 32-Bit mode since i386 has a simpler way of passing function arguments (which will come in handy shortly). In Xcode 7 the easiest way to run on the i386 architecture is to select the _iPad 2_ simulator.

With this setup in place, we can now inspect which views are visited from within our breakpoint in `-[_UITintColorVisitor _visitView:]`. Looking at the method signature we can see that this method takes on argument: the view that is being visited. That's the information that we would like to inspect further. In addition to that explicit argument every method call in Objective-C receives `self` as the first and the `selector` as the second implicit argument.

#### Printing Function Arguments in Assembly

By using [this handy reference](https://www.clarkcox.com/blog/2009/02/04/inspecting-obj-c-parameters-in-gdb/) we can look up where these arguments are stored when a method is called (the reference is old and refers `gdb` instead of `lldb`, but the info is still up to date.). The order of these arguments is part of what we call a "calling convention". It states that on a i386 architecture function arguments are passed as follows:

  * Before prologue: 
    * *($esp+4n) ➡ arg(n)  

  * After prologue: 
    * *($ebp+8+4n) ➡ arg(n)

The _n_ here refers to the index of the argument.

Without getting into too much detail at this point: the "prologue" is a sequence at the beginning of a function call that configures the stack pointer and different stack variables. The variable locations for our function arguments are different before and after the prologue ([this blog post](http://arigrant.com/blog/2014/2/18/chisels-print-invocation-command) by Ari Grant has a good description for what the function prologue and epilogue do). All arguments are offset from the base address that is stored in the `esp` register.

For now we'll use the addresses before the prologue, since we'll access the arguments as soon as we trap into our breakpoint at the beginning of the `-[_UITintColorVisitor _visitView:]` method.

When we reach that breakpoint we can print all 3 arguments to our function call as following:
    
    
    (lldb) po *(id *)($esp+4)
    <_UITintColorVisitor: 0xc502540>
    
    (lldb) po *(SEL *)($esp+8)
    "_visitView:"
    
    (lldb) po *(id *)($esp+12)
    <UIView: 0xc131830; frame = (0 0; 768 1024); autoresize = W+H; tintColor = UIDeviceRGBColorSpace 0 0 1 1; layer = <CALayer: 0xc1176d0>>
    

Now we can use this new ability to print the visited view every time we step into our breakpoint, by calling: `po *(id *)($esp+12)` (alternatively you can also use a [breakpoint command](http://objectivistc.tumblr.com/post/40854305239/stack-trace-dumping-regular-expression-based)).

Using this technique I identified that after a new subview is added, the parent view and all of its children are passed to calls of `-[_UITintColorVisitor _visitView:]`. For each added view UIKit will iterate all of its siblings.

Why exactly is that happening? I have not yet been able to track it down definitely, but I have a bunch more clues that I'd like to share.

#### Let the Guesswork begin

Since we want to know why the `_UITintColorVisitor` is called so frequently, it makes sense to start by investigating the backtrace. We can do this with the `bt` lldb command that we can invoke while halted in a breakpoint:
    
    
    (lldb) bt
    * thread #1: tid = 0x156ea9, 0x00e4b61c UIKit`-[_UITintColorVisitor _visitView:], queue = 'com.apple.main-thread', stop reason = breakpoint 9.1
      * frame #0: 0x00e4b61c UIKit`-[_UITintColorVisitor _visitView:]
        frame #1: 0x00e4bfbb UIKit`_UIViewVisitorEntertainVisitors + 107
        frame #2: 0x00e4af30 UIKit`_UIViewVisitorRecursivelyEntertainDescendingVisitors + 162
        frame #3: 0x00e4a8ca UIKit`_UIViewVisitorEntertainDescendingTrackingVisitors + 705
        frame #4: 0x00e4a2be UIKit`_UIViewVisitorEntertainHierarchyTrackingVisitors + 58
        frame #5: 0x00a9ce3f UIKit`__45-[UIView(Hierarchy) _postMovedFromSuperview:]_block_invoke + 268
        frame #6: 0x005b1440 Foundation`-[NSISEngine withBehaviors:performModifications:] + 150
        frame #7: 0x005b491c Foundation`-[NSISEngine withAutomaticOptimizationDisabled:] + 48
        frame #8: 0x00a9cce4 UIKit`-[UIView(Hierarchy) _postMovedFromSuperview:] + 521
        frame #9: 0x00aac7f1 UIKit`-[UIView(Internal) _addSubview:positioned:relativeTo:] + 2367
        frame #10: 0x00a9acc8 UIKit`-[UIView(Hierarchy) addSubview:] + 56
        frame #11: 0x00002be9 ExampleApp`ViewController.viewDidAppear(animated=false, self=0x0c72cce0) -> () + 825 at ViewController.swift:40
        frame #12: 0x00002cbf ExampleApp`@objc ViewController.viewDidAppear(Bool) -> () + 63 at ViewController.swift:0
        [...]
    

Up until `frame #11` we're only seeing code that is necessary to set up the example project. `frame #10` is the actual starting point for our investigation. It is called whenever a new subview is added and it eventually results in a call to the `_UITintColorVisitor`.

What is interesting is that `addSubview` is only ever called on our root view, but the `_UITintColorVisitor` is called for all of the subviews of that root view. The cause of this problem must lie somewhere between `frame #11` and `frame #0`.

At this point it was not obvious to me why all views were being caused to be visited; at the very end of the next section I might have a likely answer to that question…

#### Digging Deeper

Since I hit a dead end in identifying why all subviews in the view hierarchy were constantly being revisited, I decided to investigate another interesting aspect about this problem that profiler had revealed.

Earlier we identified that about 25% of the total time is taken up in calls to `[NSArray containsObject:]` which is called as part of the implementation of `[_UITintColorVisitor visitView:]`. I have used [Hopper Disassembler](http://www.hopperapp.com/) to try to understand why that's the case. A disassembler can translate a binary (in machine code) back into assembly instructions which enables us to explore some of the inner workings of closed source software. This is useful, e.g. to explore issues in Apple's UIKit framework.

If you have never used Hopper before, but would like to follow along, I would recommend reading this [brief introduction](http://www.bartcone.com/new-blog/2014/11/26/hopper-lldb-for-ios-developers-a-gentle-introduction).

Hopper has a handy feature that can generate pseudo code from the disassembled binary, which makes it somewhat easier to try and grasp the control flow of a program (if, like me, you're mostly unfamiliar with assembly code).

By browsing throught the pseudo code generated by Hopper I could identify the section of `[_UITintColorVisitor _visitView:]` that calls `containsObject`:

I also stepped through the assembly code that corresponds to this pseudo code in the debugger. As part of that effort I identified a few things that are relevant to this snippet:

  * One `_UITintColorVisitor` instance is used to visit all views (at least in this simple example with only one view hierarchy)
  * The `_UITintColorVisitor` has a few properties that are persisted between the different invocations of `visitView:`. Here's an overview of all properties found in Hopper: ![](https://dl.dropboxusercontent.com/u/13528538/Blog/UITintColorVisitor/tint-color-visitor-properties.png)

From stepping through the assembly code and investigating different registries I could identify that in the above pseudo code `eax` refers to the `_originalVisitedView` and `edi` refers to the view that is currently being visited.

This means, that as soon as a `_UITintColorVisitor` has an original visited view (which is true after it visited its first view), the outlined code checks if the `subviews` array of the `originalVisitedView` contains the currently visited view. This check scans the full array of subviews; in cases where the `originalVisitedView` is our root view, the cost of this operation grows linearly with the amount of added subviews.

I investigated this further by creating another breakpoint in UIKit at the point where this check takes place. When disassembling the 32-Bit slice of UIKit and running the app in 32-Bit mode, the address offsets align nicely. By stepping into the breakpoint in `-[_UITintColorVisitor visitView:]` I could compare the assembly addresses in the debugger and in Hopper and identify that the addresses match up when replacing the `495` in the hopper address with `0xe4b`. The relative addresses within UIKit are constant, only the base address at which the framework is loaded is dynamic:

![](https://dl.dropboxusercontent.com/u/13528538/Blog/UITintColorVisitor/address-align.png)

Once we know the memory address offset we can create breakpoints in lldb based on addresses in Hopper.

Knowing this, I created a new breakpoint based on the `loc_4956fd` in Hopper like this:
    
    
    b 0xe4b6fd
    

Within the breakpoint I printed both the `eax` register and the `_originalVisitedView` of `self` (which is stored in the `ebx` register):
    
    
    (lldb) po $eax
    <UIView: 0xc131830; frame = (0 0; 768 1024); autoresize = W+H; tintColor = UIDeviceRGBColorSpace 0 0 1 1; layer = <CALayer: 0xc1176d0>>
    
    (lldb) po [$ebx valueForKey:@"_originalVisitedView"]
    <UIView: 0xc131830; frame = (0 0; 768 1024); autoresize = W+H; tintColor = UIDeviceRGBColorSpace 0 0 1 1; layer = <CALayer: 0xc1176d0>>
    

With this approach I identified that with the current sample code, `eax` **always refers to the root view**. This means we are iterating over all subviews of the root view, N times for each subview that is added.

I'm no expert in complexity analysis but it appears that the total cost of `[_UITintColor visitView:]` sums up to `n^2`:

(**n** invocations of `[_UITintColor visitView:]`) * (**n** cost of iterating all subviews) where **n** = amount of added subviews

**But why do we have these two code paths outlined above in the first place**? Why do we need to check if the currently visited view is a subview of the original visited view?

In both cases, whether it is a subview or not, we end up calling: `___34-[_UITintColorVisitor _visitView:]_block_invoke`. In the case of the currently visited view being a subview of the original visited view, we pass two arguments to the block, in the other case we pass only one.

Before moving on, here's an annotated version of the method we just investigated:

![](https://dl.dropboxusercontent.com/u/13528538/Blog/UITintColorVisitor/visit-view-pseudo-code-annotated.png)

Now let's take a look at the block that is being invoked from here. By double-clicking onto the call to the block in Hopper, we can jump into the called block. It looks as following:

![](https://dl.dropboxusercontent.com/u/13528538/Blog/UITintColorVisitor/called-block.png)

We can see that this block receives two arguments. Using the address translation technique from earlier I decided to create the following breakpoint to jump into this block using lldb:
    
    
    (lldb) b 0xe4b7ee
    

By investigating the registers I found out that `ebx` refers to the `UIView` instance that is being visited and `*(esi + 0x14)` refers to the tint color visitor. The code seems to switch over the `_reasons` property of the `[_UITintColorVisitor]` and over some properties of the visited view.

After stepping through the function prologue we can investigate the relevant values:
    
    
    po [*(id *)($esi+0x14) valueForKey:@"_reasons"]
    1
    

The `_reasons` property seems to store a bitmask value. Our bitmask is set to `1`. The first `if` statment in the pseudo code checks if the `1` bit of the bitmask is set. A further condition is that the view's `_interactionTintColor` needs to be `nil` (this check likely explains why setting an explicit `tintColor` on a view fixes our performance issue). Since both conditions are met, we execute the body of the first `if` block.

Inside of the `if` block we finally find a key that might help solve this puzzle:
    
    
    [ebx _setAncestorDefinesTintColor:eax];
    

Here UIKit is marking this view, noting that its parent is defining a tint color. I'm assuming that this flag is what registers this view in some way to be visited by the `_UITintColorVisitor`, since we are passing it as an argument to the `_setAncestorDefinesTintColor` method.

The big question remains why this is flag is set every single time the view is visited and not only in cases where the subview has moved in the view hierarchy or when the parent view changes its tint color. Another interesting question is why the `superview` property of the visited view is not used instead of iterating over the array of subviews of the parent view. Both of these mysteries will most likely remain unsolved.

However, our new findings help explain the two code paths in the piece of code that calls into this block (which we examined earlier):

![](https://dl.dropboxusercontent.com/u/13528538/Blog/UITintColorVisitor/visit-view-pseudo-code.png)

If the currently visited view is not a child view of the original visited view, we don't pass a second argument to this block; which is equivalent to passing `nil`. This means that `ebx` will be `nil`, which in turn means we will never call `[ebx _setAncestorDefinesTintColor:eax];`.

# Conclusion

When I started out diving into this issue I was almost entirely clueless about how to interpret complex disassembled code - now I'm still mostly clueless. However, I learned a few very handy tricks along the way:

  * I learned how to set breakpoints in private methods & and at any address within the assembly code.
  * I learned about the i386 and Objective-C calling conventions, e.g. which arguments are stored in which registers.
  * I learned that the addresses in Hopper match the addresses in the actual framework code (besides a base pointers offset depending on where UIKit is loaded into memory). In hindsight this sounds obvious but it definitely was not the case when starting out. [This article](http://www.bartcone.com/new-blog/2014/11/26/hopper-lldb-for-ios-developers-a-gentle-introduction) was very helpful in getting more comfortable with working with lldb in UIKit alongside of Hopper.

These three tools allowed me to explore the code paths & relevant variables a lot faster which in turn made it a lot easier (yet still hard) to get a grasp of what was going on.

In the end I didn't find a definite answer on how this issue could be fixed, but I found a lot of clues about how the current visitor pattern is implemented and I think I got fairly close to the underlying issue.

Most importantly I learned how to be more efficient at exploring the inner workings of closed source frameworks which will surely come in handy in future! Attempting to reverse engineer code can be very intimidating and the learning curve is really steep. I hope some day when I have a better grasp myself I can share a beginner friendly guide on all of this!

Thanks a lot to Russ Bishop who tracked down the original issue together with me. He has also filed a radar: 25934331 (fingers crossed)!

I also recommend the following helpful articles for getting started with reverse engineering closed source Cocoa code:

  * This article was a great introduction to the very basics of using Hopper and lldb side by side: [Hopper + lldb for iOS Developers: A Gentle Introduction](http://www.bartcone.com/new-blog/2014/11/26/hopper-lldb-for-ios-developers-a-gentle-introduction)
  * Very good discussion of function prologue and epilogue as well as calling conventions: [Printing Objective-C Invocations in LLDB](http://arigrant.com/blog/2014/2/18/chisels-print-invocation-command)
  * Another post on calling conventions in Objective-C by Jeff Hui, recommended by[@rpy](https://twitter.com/rpy): [Reverse Engineering Objective-C](https://www.jeffhui.net/2014/03-reverse-engineering-objective-c.html)
