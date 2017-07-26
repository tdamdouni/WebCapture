# Keep Your Code Consistent

_Captured: 2017-02-04 at 19:15 from [dzone.com](https://dzone.com/articles/keep-your-code-consistent?edition=267883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-04)_

Navigate the Maze of the End-User Experience and pick up this [APM Essential guide](https://dzone.com/go?i=147026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fapm-essentials-navigating-the-maze-of-end-user-experience-solutions.register.html%3Fmrm%3D519574), brought to you in partnership with [CA Technologies](https://dzone.com/go?i=147026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fapm-essentials-navigating-the-maze-of-end-user-experience-solutions.register.html%3Fmrm%3D519574).

There's a bunch of things in programming that have seemingly little to no meaning. Some of those things, despite their "seemingly" little meaning cause a lot of pointless discussions e.g. _tabs vs. spaces_ (as long as you use 4 spaces) or _braces vs. no braces_ (as long as you use braces). I'd say that it doesn't matter which one you choose, but there is one important thing to remember. Once you've made a decision, **you have to be consistent!**

## Why Does it Matter?

When I first thought about writing this article, I thought I'd put up an argument like: _Look. You spend much more time reading code than writing it. So when talking about consistency, we're mostly concerned with reading. Imagine you're reading a book that has different fonts on each page, uses different spacing and punctuation or even the writing style changes every other paragraph. Would it read nicely? _Now, such an argument would be lame, as the analogy doesn't necessarily have to hold, but it looks I made it anyway ;).

Having weakened you with a shot from my lame cannon, I can now try to convince you to keep consistent using some other arguments:

  * **Merging changes is easier**: Anyone who has tried resolving an SCM conflict with a guy who uses a different formatter is smiling right about now. Some consistency issues make you waste even more time in the pleasant process of merging changes.
  * **Code is more predictable**: If you see a construct in the code, there's a higher chance that you know what it is, why it is there, where to look for more, and so on because there might be similar ones in the codebase already.
  * **Some errors might be easier to spot or avoid**: The simplest example being either always using braces or always making the body of conditionals and loops one-liners.
  * **Weird people like me are happier**: Some of us just need things to be in perfect symmetry, well-ordered, etc. Otherwise, our brain raises an alert and we get less effective.

## What to Keep Consistent?

### Whitespaces

Whitespaces help you organize your code nicely. They let you keep things close that should stay close and separate things that deserve to be separated. Conventions regarding whitespaces can save you a ton of time when merging, so it's good to start with this one.

When it comes to examples, as already mentioned, one of the choices would be _tabs vs. spaces_. If spaces, then _how many spaces? How many tabs/spaces when breaking a line?_ _Where do you put new lines and how many? _Should you put them between fields? Annotated fields? Methods? Before and after loops? Parts of your tests? I could go on and on, but you most likely get the point already.

### Member Ordering

Ordering is another very important point when merging as SCMs get lost when you shuffle things in a source file. It also affects predictability -- because you want to know whether you should look up or down the source file for the thing you want to find.

For this point, there are two particularly important choices:

  1. _What order do different language constructs go in a class?_ Most likely, you will choose something like: constants, fields, constructors, methods, inner classes.
  2. _What order should methods go in a class?_ Here I'd expect something like the step-down rule.

### Braces

Braces are not a hot topic in Java when it comes to their placement in a line, but they surely are when it comes to one-line conditionals and loops. Some argue that always using braces makes you safer because you will never forget to add them to an existing statement when extending it. Others argue that those statements should contain one line of code anyway and thus braces are not necessary. In other languages, the placement of braces in a line is also discussed, because some claim that one>

Having said all of the above, decide with your team: _Should you use braces with conditionals and loops? _And, if necessary: _Where do you put braces in a line?_

### Naming

Naming is very important in software development. I guess nobody questions that. While, in general, we strive for "good names," there are some things that cannot be evaluated as better or worse. We just have to agree on them.

The first and very important example that comes to my mind is: _How should you name your tests? _Depending on language and framework used, there might be a lot of different options. In general, you want to specify the functionality being tested, the assumed system or object state, and the expected behavior. Another thing to decide on would be _when to capitalize a letter in a name? _It's common to see a project where some abbreviations are moved into names as is, while others have only the first letter capitalized. And maybe one more inconsistency that I recently came across: _Where to put prefixes like "Test" in a name?_

### Package Structure

Different modules/components of your application might have similar building blocks at the lower level, e.g. entities, context configurations, repositories, etc. Keeping their internal package structure consistent across the application might make the project more browsable and thus more comprehensible, at the cost of having some packages with just one or two classes inside.

### Solutions to Similar Problems

This point is less about conventions and more about coding sense. In general, we want to use similar solutions to similar problems, especially inside a single source file. For example, if somebody is using a `Stream` for filtering a collection, you don't write a `for` loop with an `if` statement inside a few lines below unless you have a good reason to do so. If the whole project uses a library class for constructing URLs, you don't do `String` escapes and concatenation just because you know how. If the project uses JUnit's assertions for unit tests, you don't add AssertJ to the projects just because you prefer it. These are just a few examples that annoyed me in the past, but you get the point.

## Your Turn!

The list above is surely incomplete -- these are just the things that came across my mind at the time of writing this article. If you have any ideas for other things to keep consistent, please put them in the comments so that we can all benefit!

Thrive in the application economy with [an APM model that is strategic](https://dzone.com/go?i=147025&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fepic-apm-toward-a-better-apm-model-for-the-application-economy.register.html%3Fmrm%3D519574). Be E.P.I.C. with CA APM. Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=147025&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fepic-apm-toward-a-better-apm-model-for-the-application-economy.register.html%3Fmrm%3D519574).
