# You Have No Excuse for Your Dead Code

_Captured: 2017-10-27 at 17:10 from [dzone.com](https://dzone.com/articles/you-have-no-excuse-for-your-dead-code?edition=334741&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202017-10-27)_

In darker times, software management would [measure productivity as a function of lines of code](https://blog.ndepend.com/alternatives-lines-of-code-loc/). More code means more done, right? Facepalm. When I work with IT management in my capacity as a consultant, I encourage them to view code differently. I encourage them to view code as a liability, like inventory. And when useful code is a liability, think of what a boat anchor dead code is.

I once wrote [a fun post](https://blog.ndepend.com/paying-for-dead-code/) about the fate of dead code in your codebase. And while I enjoyed writing that, it had a serious underlying message. Dead code costs you time, money, and maintenance headaches. And it has absolutely no upside.

## A Working Definition for Dead Code

Okay. If I'm going to make a blog post out of disparaging dead code, I should probably offer a definition. Let's do that here.

Some people will draw a distinction between code that can't be executed (unreachable) and executed code whose effects don't matter (dead). I acknowledge this definition but won't use it here. For the sake of simplicity and clarity of message, let's create a single category of dead code: any code in your codebase that has no bearing on your application's behavior is, for our purposes here, dead.

## The Problems With Dead Code

Having defined it, what's the problem? If it has no bearing on your application's behavior, what's the harm? How does it cost time and money, as I claimed a moment ago?

Well, simply put, your code does not live in a shrink-wrapped vacuum. As your application evolves, developers have to change the code. When you have only code that matters in your codebase, they can do this with the most efficiency. If, on the other hand, you have thousands of lines of useless code, these developers will spend hundreds of hours maintaining that useless code.

Think of having dead code as being reminiscent of running your heat in the winter while keeping all of your windows open. It's self-defeating and wasteful.

But even worse, it's a totally solvable problem. Let's take a look at different types of dead code that you encounter and what you can do about it.

### Commented-Out Code

Let's start with an easy one. I'm talking about commented-out code. This happens when you take a chunk of code and comment all of it out, like this:

I think this comes about for a couple of reasons. First, some folks carry this kind of thing forward from before the days of ubiquitous source control. They leave it in as a historical reference. Secondly, people comment out an implementation to experiment with another and then forget to remove the commented code.

Whatever the reason, your course of action is simple. Just delete it on sight, no questions asked. If someone needs this, source control will have it. And if you don't have source control, you have bigger problems than dead code.

### Unreachable Code

This is where my definition may run counter to other folks' ways of thinking. But I'm going to lump unreachable code in as a subset of what I'm calling dead code. Unreachable code looks like this:

That second line method is, thankfully, unreachable. Never in all the world will you reach that line of code that returns 2 + 2.

Getting rid of this code is also pretty easy, and you should do it with no questions asked. While you won't always pick this up immediately on visual inspection, your compiler will warn you about it. That's because it understands you'll never use this code. So make sure you pay attention to compiler warnings -- or better still, enable a setting where you [treat them as errors](http://dailydotnettips.com/2016/03/04/avoid-code-warnings-being-missed-or-ignored-treating-warnings-as-errors-in-visual-studio/).

### Unused Parameters, Variables, Fields, Return Values

Now we start to get into somewhat more subtle territory. I'll give an example here of an unused parameter, but the same sort of reasoning applies to variables, fields, and return values as well.

Notice that the parameter _z_ has no impact on the method. In fact, it's never referenced at all. This unused parameter represents a form of dead code. It serves no purpose and will only confuse maintenance programmers. Why is this here? Should I be doing something with _z_? Did someone used to do something with it?

Spare them the mental waste by getting rid of unused constructs like this. Many times, your IDE will flag them for you. If not, productivity add-ins will flag and sometimes [even fix them](https://documentation.devexpress.com/CodeRushForRoslyn/115567/Refactoring-Assistance/Remove-Unused-Parameter). For fields, specifically, [NDepend will call them out for you](https://www.ndepend.com/Default-Rules/Q_Potentially_dead_Fields.html).

The same principle applies here -- if you determine these things to be useless, delete them. Even if they serve as some kind of historical reference point, let them serve that way in your source control history and not in your code.

### Uncalled Non-Publicly-Visible Methods

There's one final case of relatively easy dead code that I'll mention: the uncalled non-public method. Here you have a method with a visibility indicating that only your code could call it. But none of your code _does_ call it.

This can easily happen when you factor away from using some kind of auxiliary method or when you create a new version of a method but forget to delete the old version. This sort of thing happens relatively frequently, and it leaves you with a method you don't need anymore.

This is easy enough to detect. Again, some IDEs will detect this automatically, as will some plugins. If you use NDepend, you can use its "[potentially dead methods" functionality](https://www.ndepend.com/Default-Rules/webframe.html?Q_Potentially_dead_Methods.html). If you take a deep dive into the CQLinq for that functionality, you'll see that this computation is surprisingly complex. You have to ignore things you might not immediately consider, such as compiler-generated methods, finalizers, etc.

Again, once you've identified these methods using your tools, delete them. If deleting them produces no compiler errors or unit test failures, you should feel reasonably confident that you'll experience no adverse side effects (though you may want to run more tests).

### Visible Methods and Types

This brings us to the final and most difficult type of dead code to eliminate. It's hard simply because so many things can go wrong.

You may find methods or types in your codebase that have no references to them. You might then delete them with no errors at all. But that might actually prove catastrophic.

When these things have public visibility, they might be part of an API that you offer. Or they might only get invoked through something like an IoC container. It gets _really_ hard to identify this type of dead code with certainty.

But that doesn't mean you have no options. You could, for instance, use NDepend to actively flag any types and methods intended for use in IoCs or publicly. This kind of opt-in white-listing would give you confidence when deleting errand methods. Another option you have is to make sure you have very robust automated testing. And finally, you can [write your own CQLinq queries](https://www.ndepend.com/features/cqlinq) to help prevent and eliminate this type of code, knowing your own tools and dependencies.

While this presents the most difficult sort of dead code to root out, it doesn't render the task impossible by a long shot. Avoid writing speculative code, stay organized, and routinely audit your code for dead code candidates.

### Take Advantage of Tooling

I absolutely stand by the claim that there's _no excuse_ for dead code. That doesn't mean that you'll never have it or that you're a bad programmer if you do. We'll all have an instance here or there, just as we all occasionally overindulge a sweet tooth. Realize that you've indulged, remedy the situation, and don't make excuses.

The tooling in this day and age is so good that it can automatically find just about any potential candidate for dead code that you can think of. You just have to make sure you avail yourself of that tooling and then pay attention to what it says. And finally, have the discipline to act on its results, deleting dead code and updating the tool's configuration so that it doesn't keep flagging false positives.

Being a programmer is hard, and maintaining code is hard. There's no reason to make it harder and more confusing by maintaining useless code.
