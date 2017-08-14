# Code Smells: Null

_Captured: 2017-08-14 at 10:08 from [dzone.com](https://dzone.com/articles/code-smells-null?edition=315392&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-10)_

During my research on refactoring, I've seen a number of patterns (smells) crop up again and again. None of these are particularly new, and there are [plenty](https://martinfowler.com/books/refactoring.html) of [books,](https://martinfowler.com/books/r2p.html) [blogs](https://refactoring.com/), and [videos](https://youtu.be/y4_SJzNJnXU) that cover smells and how to deal with them. But I wanted to demonstrate some specific, non-trivial examples and, of course, how IntelliJ IDEA may (or may not) be able to help you.

The first problem I've been trying to counter is the use of nulls, particularly when it leads to null-checks scattered around the code.

I thought Java 8's `[Optional`](https://docs.oracle.com/javase/8/docs/api/java/util/Optional.html) should solve a lot of these problems. I assumed that a type that specifically states that it may be null, that is designed to let you say what to do on these occasions, is exactly the right solution.

However, things are never as simple as they seem, and I suspect that's why there's no magic "Optionalize my project" intention in IntelliJ IDEA. Rather disappointingly, this is an area that needs me, the developer, to think hard about what should be done.

We have to come to terms with the fact that null means many things. It can mean:

  1. Value was never initialized (whether accidentally or on purpose)
  2. Value is not valid
  3. Value is not needed
  4. No such value exists
  5. Something went terribly wrong and something that should be there is not
  6. …probably dozens of other things

You can assume some of these don't apply to your code base if you're a disciplined team with clear design goals - for example, having final fields that are always initialized in the constructor, using builders or factories to validate correct combinations before instantiation, not using nulls in the core of your application (i.e. pushing all checks to the edges) and so on.

`Optional` really solves only one of these cases, case 4. For example, you ask the database for a Customer with a given ID. Previously, you might have used `null` to represent this, but that could be ambiguous - does it mean the customer wasn't found? Or that there's a customer with that ID, but has no values? Or was `null` returned because the connection to the database failed? By returning an empty `Optional`, you've removed the ambiguity - there's no customer with that ID.

In a normal, mature, code base that's been worked on by numerous people, is it possible to tell what all our nulls mean, and what to do about them? We should be able to make some progress by taking very tiny bites.

## **The Case Study**

I'm using the [Morphia project](https://github.com/mongodb/morphia/) as an example in this blog post, as I have in previous talks and articles about refactoring. This is a great example project because it's a) open source, b) small enough to easily download and explore, and c) mature enough to contain the sort of real life example code you probably have in your own applications.

## **The Smell: Return Null**

I did a [Find in Path](https://www.jetbrains.com/help/idea/find-and-replace-in-path.html) for all the places where null is explicitly returned. I have a theory that maybe we can change these methods into something that returns an `Optional`.

_![Find places that return null](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/01-FindInPath.png)_

> _Results of "Find in Path" for "return null"_

## **Example 1: Converter.decode()**

Given that lots of these *Converter classes seem to return a null value in the `decode` method, it seems reasonable that we might want to change the Converter superclass (an abstract class called `[TypeConverter`](https://github.com/mongodb/morphia/blob/master/morphia/src/main/java/org/mongodb/morphia/converters/TypeConverter.java)) to return `Optional` here. But a closer look at the code shows what's actually happening: we see exactly the same pattern happening again and again - the method checks if a value passed in was null, and if so returns null:

The first question is, can `fromDBObject` actually be null? The code is sufficiently complicated that it's difficult to tell, but theoretically it seems plausible, since this is a value from the database.

A quick search shows that all instances of this method are actually only called from one central place, so instead of making this check in 21 different places, we can just do it in a single place and from there on assume `fromDBObject` can no longer be null.

### **Solution: `@NotNull` Parameter**

My original assumption that we can use `Optional` here turned out to be wrong. Instead, I'm going to change the method signature of `decode` to declare that `fromDBObject` cannot be null - I've opted to use the [JetBrains annotations](https://www.jetbrains.com/help/idea/nullable-and-notnull-annotations.html) to do this.

Then I move the null check (and subsequent null return) in the place where `fromDBObject` could actually be null, the single place that calls `decode`.

![Add null check to call site](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/02-MoveNullCheck.png)

> _Moving the null check to the single call site where fromDBObject can be null_

It makes the call site a bit more untidy, but constrains this logic to a single place instead of scattered through all implementations. Now, we can either document the fact that `fromDBObject` will not be null or rely on the annotation to do this for us, so we never have to perform this null check in the Converter implementations.

Next, we can tidy up and remove all the duplicated code. Here, IntelliJ IDEA can help us. If we go back to the abstract method in `TypeConverter` that we annotated with the `@NotNull` parameter, we are given a warning:

_![Overridden parameters are not annotated](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/03-OverriddenNotAnnotated.png)_

> _Warning that implementations don't annotate this parameter_

The quick fix suggested when we use Alt+Enter on this warning lets us apply this annotation to all the implementations of this method in one easy step, so let's do that.

![Quick fix to apply the annotation to all implementations](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/04-QuickFixImplementations.png)

> _Use the quick fix to apply to all implementations_

Our VCS log shows that all the Converter implementations have been updated

![All Converters updated](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/05-ConvertersUpdated.png)

This has added the `@NotNull` annotation to the `decode` method's parameter, but we still haven't tracked down and removed all the duplicate null-check code. The good news is that now we've said `fromDBObject` cannot be null, we can use the inspections to find all of our redundant null checks and remove them.

One way to do this is to navigate into an implementation that we know has the check (in this case I chose [StringConverter](https://github.com/mongodb/morphia/blob/master/morphia/src/main/java/org/mongodb/morphia/converters/StringConverter.java)) to see what warning IntelliJ IDEA gives me.

_![Null check not needed as value is never null](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/06-NullCheckNotNeeded.png)_

> _Null check not needed as value is never null_

This turns out to be triggered by the "[Constant conditions & exceptions](https://blog.jetbrains.com/idea/2009/04/avoiding-assert-statements-with-constant-conditions/)" inspection. We can run just this inspection over the code base to find other examples easily, using [Ctrl+Shift+Alt+I and typing the inspection name](https://www.jetbrains.com/help/idea/running-inspection-by-name.html).

![Run inspection by name](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/07-RunInspectionByName.png)

> _Using Ctrl+Shift+Alt+I to run an inspection by name_

This returns more results than just my Converters, but by grouping the results by directory I can see all the Converter implementations easily

![Inspection results](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/08InspectionResults.png)

I can use the preview window on the right to check which code has been flagged, and see what IntelliJ IDEA suggests doing with each problem. After scanning through and making sure this is the null check I'm looking for, I select the converters directory and press the "Simplify boolean expression" button.

To sanity check the changes, I go into the [VCS Local Changes](https://www.jetbrains.com/help/idea/local-changes-tab.html) window and use Show Diff (Ctrl+D) to check the changes that were applied to the 36 files there.

_![Using the diff view to sanity check changes](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/09Diff.png)_

> _Using the diff view to sanity check changes_

I can even use the diff view to make small edits if I want - in this case I use Ctrl+Y to remove the unnecessary empty lines 26 and 27 of my file (the file on the right). By using Alt+Right to check all the files that have been changed, I find an example where the null check wasn't removed (this was a test converter and therefore was not in the converters directory), but I can easily use quick fixes even in the diff view to remove it.

This sanity check gave me peace of mind about the automatic changes IntelliJ IDEA made, and let me make some additional tweaks too. The last thing to do is run all the tests, and when they pass (hurrah!) now seems like a really good time to commit all these changes.

If you're uncomfortable adding a new library to document that a parameter can't be null and make the IDE warn you if you pass in null values, you can always remove the `@NotNull` just before committing - after all, it's done its job now. In this case, you should at least update the Javadoc to state that the parameter is assumed to be not null.

## **Example 2: Converter.encode()**

Earlier we saw that the `decode` method was only one of several that explicitly returned null values. Now we've dealt with that, we can take a look at another example.

The `encode` method on the same `TypeConverter` class can also return null. But unlike `decode`, there are valid times when the converter implementations explicitly return null:

### **Solution: `Optional`**

This is a good place for `Optional` -- we're explicitly stating that there are some cases where the encode method does not return a value. `Optional.empty()` seems like a good representation of this fact. So I change the `TypeConverter.encode()` method to return an `Optional` instead. It makes all the implementations a little more untidy, as things need to be wrapped in an `Optional`, but it is more explicit about the fact that this method sometimes does not return a value. I'd love to show you IntelliJ IDEA magic that does this for you (in some cases, [Type Migration](https://www.jetbrains.com/help/idea/type-migration.html) will work, but not in my example) but I made this change the hard way - I changed the return type of the super class to `Optional` and fixed all the places that broke. The good news is that once I'd changed the method signature to return an `Optional`, IntelliJ IDEA did offer a quick fix to wrap my return values in an `Optional`.

![Wrap value in Optional](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/10-WrapReturnWithOptional.png)

> _Wrap value in Optional_

Similarly, null values can also be replaced

![Return Optional.empty\(\) instead of null](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/11-ReplaceNullWithOptionalEmpty.png)

> _Return Optional.empty() instead of null_

Now we're returning an `Optional`, we have to work with this new type at the call site. In my case, I actually got no compiler warnings as my return type was originally an `Object`, and obviously an `Optional` is also an `Object` (note: this is why we shouldn't use raw Object types, because it basically removes the benefits of having a strongly typed language. This code would have been better with [Generics](https://docs.oracle.com/javase/tutorial/java/generics/)). I just have to change the one place that calls the `encode` method to unwrap the `Optional`. I'm going to do something that's pretty nasty and use `orElse(null)`, but since this is the same behaviour the original methods were doing anyway, and it's restricted to one place in the code, I'm happy with this - I can flag it as tech debt and we can gradually deal with the issue rather than chasing it all around the code.

![Dealing with the optional return](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/12-DealWithOptionalReturn.png)

In tests that call the `encode` method I simply updated them to call `encode(o).get()` - usually this is unsafe, but a) the tests should not return an empty `Optional` and b) if they do, they'll fail and that's correct. In fact in my case this highlights that there are no tests for the case where no value is returned, so I should add new tests for empty `Optional` returns.

Changing your API to use `Optional` is often a non-trivial task, but in cases like this one it can really help clarify the intent - instead of returning nulls when there's no valid value, it will return you an empty `Optional` and you can declare what to do - return an alternate value, throw an Exception, or perform some other operation. Beware though, this can get hairy.

Note: This example was OK, but there are other methods in this code that are perfect for returning `Optional`, but the upstream effect of applying this change was huge - the methods are called in multiple places and the return types used in all sorts of very complex methods, making it nearly impossible to track down the right place to test the Optional and unwrap it vs letting it propagate around the code. The lesson I have learned is to apply this if you can limit the impact to one or two call sites and deal with the `Optional` return type immediately.

## **Example 3: Mapper.getId()**

Here's another example of null returns:

This is a great example of where null means two different things. The first null means we were given a null input, therefore we give you a null output. Seems fairly valid, if a little unhelpful. The second null means "an error happened and I couldn't give you a value, so here, have null". Presumably, a null ID is a valid response, given the first case, but it would probably be more helpful to the caller to know what the error was and deal with it accordingly. Even if the Exception is such that the caller cannot deal with it, it's pretty unfriendly to catch the Exception and return null, especially when the Exception isn't even logged. This is a really good way to hide genuine problems. Exceptions should be handled where they're found, or passed on in some useful way, they should not be swallowed unless you really _really_ know it's not an error.

So this `null` means "something unexpected happened and I don't know what to do about it, so I'm going to give you null and hope that's OK", which is not at all clear to the caller. These cases should definitely be avoided, and `Optional` is not going to be your solution. The solution is to implement much clearer error handing.

## **In Summary**

Null is a particularly difficult problem. The main problem with null is we don't know what it means. It's an absence of a value, but this could be for any number of reasons. Using null is not a useful way to flag what any of these reasons are, since by its very definition, it has no value, no meaning.

Symptoms:

  * Null checks extensively used throughout the application code, without it being clear to you, the developer, what null really signifies or if the value can really be null at all.
  * Explicit `return null`

Possible Solutions:

  * `Optional`. Not a solution to everywhere you find a null. But if a method is deliberately returning a null value to mean "not found" or "I don't have one of those", this is a good candidate for returning an `Optional`.
  * `@NotNull/@Nullable`. One of the problems with complex code bases is understanding what are actually valid values. If you're checking for null parameters, try putting `@NotNull` on the signature and seeing if null values are ever passed. If nulls are never passed, you can remove the null check. If you're uncomfortable adding a dependency just to use the `@NotNull` annotation, you can apply the annotation temporarily, get IntelliJ IDEA to tell you if there are any problems, fix up if necessary and run all your tests to make sure everything works. If it's all good, you can remove the annotation, add a Javadoc comment (not as safe as the annotation, but still enormously useful for developers who call or maintain the method) and commit the updated code.
  * Exception handling. Returning null for an Exceptional case is very unfriendly, and unexpected from the caller's point of view. It can lead to `NullPointerException` further down the line, or at least more of the pervasive null checks (without a clear idea of _why_ the value is null). Throwing a descriptive Exception is much more valuable for those downstream.
  * Sometimes, it's fine. Field-level nulls (where it should be well understood what can be null and why) are examples where null may be perfectly acceptable.
