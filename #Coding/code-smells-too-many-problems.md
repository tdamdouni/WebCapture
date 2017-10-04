# Code Smells: Too Many Problems

_Captured: 2017-09-21 at 11:05 from [dzone.com](https://dzone.com/articles/code-smells-too-many-problems?edition=326502&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-09-20)_

Or: argh! Where do I start?!

_This is part of a series investigating code that looks suspicious ("code smells") and exploring possible alternatives._

  * **Code Smells: Too Many Problems**

For the middle articles of this series, we've been focusing on a single method and demonstrating how to improve this method, one smell at a time. While it has been… useful… that a single method has demonstrated so many smells, if you came across that method in real life it wouldn't be obvious what to do with it.

As a reminder, let's look at the original method. This is actually before we added the [Optional return from getMappedField](https://blog.jetbrains.com/idea/2017/08/code-smells-mutation/).
    
    
    static MappedField validateQuery(final Class clazz, final Mapper mapper, final StringBuilder origProp, final FilterOperator op,
    
    
                                         final Object val, final boolean validateNames, final boolean validateTypes) {
    
    
            if (!origProp.substring(0, 1).equals("$")) {
    
    
                final String[] parts = prop.split("\\.");
    
    
                for (int i = 0; ; ) {
    
    
                    final String part = parts[i];
    
    
                    mf = mc.getMappedField(part);
    
    
                    if (mf == null && !fieldIsArrayOperator) {
    
    
                        if (validateNames && mf == null) {
    
    
                                                                 mc.getClazz().getName(), prop
    
    
                            parts[i] = mf.getNameToStore();
    
    
                    if (mf != null && mf.isMap()) {
    
    
                    if (i >= parts.length) {
    
    
                        if (validateNames && !canQueryPast(mf)) {
    
    
                                                                 + " validating - %s", part, mc.getClazz().getName(), prop));
    
    
                        if (mf == null && mc.isInterface()) {
    
    
                        } else if (mf == null) {
    
    
                            throw new ValidationException(format("The field '%s' could not be found in '%s'", prop, mc.getClazz().getName()));
    
    
                        mc = mapper.getMappedClass((mf.isSingleValue()) ? mf.getType() : mf.getSubClass());
    
    
                    for (int i = 1; i < parts.length; i++) {
    
    
                if (validateTypes && mf != null) {
    
    
                    List<ValidationFailure> typeValidationFailures = new ArrayList<ValidationFailure>();
    
    
                    boolean compatibleForType = isCompatibleForOperator(mc, mf, mf.getType(), op, val, typeValidationFailures);
    
    
                    List<ValidationFailure> subclassValidationFailures = new ArrayList<ValidationFailure>();
    
    
                    boolean compatibleForSubclass = isCompatibleForOperator(mc, mf, mf.getSubClass(), op, val, subclassValidationFailures);
    
    
                    if ((mf.isSingleValue() && !compatibleForType)
    
    
                        || mf.isMultipleValues() && !(compatibleForSubclass || compatibleForType)) {
    
    
                                               + "for the field '%s.%s' which is declared as '%s'", val.getClass().getName(),
    
    
                                               mf.getDeclaringClass().getName(), mf.getJavaFieldName(), mf.getType().getName()

I know there are developers out there who can either parse this code and understand it, or who have the ability to only focus on the areas of the code that concern the thing they are working on right now and can easily ignore less important problems. But I get easily distracted by complexity, and every time I've stumbled over this method I've wanted to do something about it. Actually, I've tried to do something about it more than once.

The problem is that the method is so long, and so complex, that it's overwhelming. It's difficult to see what is the best/right/simplest step to take first. While I was working on this series of posts I spent a lot of time going in circles and trying to weigh up the pros and cons of various approaches. So for this article, instead of highlighting a specific smell and what to do about it, I want to take a step back and talk about how to get started.

## **The Smell: So Many Problems**

![](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/09/the-problems-annotated.png)

> _Code has issues_

I've covered three of the problems in individual articles so far ([mutation](https://dzone.com/articles/code-smells-mutation), [multi-responsibility methods](https://dzone.com/articles/code-smells-multi-responsibility-methods), and [if statements](https://dzone.com/articles/code-smells-if-statements)), and we still have more. There's also poor naming; a poor domain model; (possibly) premature optimization; and procedural programming, amongst others. In fact, there's only a couple of smells in the series that _aren't_ in this method. Where to start?

### **Approach 1: Break the Method Into Smaller Pieces**

My first instinct was to break it up into smaller, nicely named methods. Then even in a procedural piece of code like this, at least the steps are "documented" in methods. Although we can do this for [some of the code](https://blog.jetbrains.com/idea/2017/09/code-smells-multi-responsibility-methods/), we saw that some of the smells make this [impossible for other pieces](https://blog.jetbrains.com/idea/2017/08/code-smells-mutation/).

This approach doesn't work as well as I hoped for this particular method, but if you're facing a similar problem you may find simply [extracting methods](https://refactoring.com/catalog/extractMethod.html) for logical chunks of functionality increases readability and lets you refactor each smaller section as and when it makes sense to do so. You may even be able to [move some of these methods](https://refactoring.com/catalog/moveMethod.html) into different classes to improve the domain model.

### **Approach 2: Work on One Smell at a Time**

This is the approach we ended up taking for the articles.

Firstly, we "fixed" the [null problem](https://dzone.com/articles/code-smells-null) by using `Optional` to document that the `MappedField mf` may not have a value.

Secondly, we [identified the issues caused by mutability](https://blog.jetbrains.com/idea/2017/08/code-smells-mutation/) and addressed many of those.

Thirdly, we managed to split out parts of this method into their own methods, the first was enabled by reducing the amount of mutable state and the second by [identifying the two different functions the method was performing](https://blog.jetbrains.com/idea/2017/09/code-smells-multi-responsibility-methods/) and [replacing a parameter with explicit methods.](https://refactoring.com/catalog/replaceParameterWithExplicitMethods.html)

Finally, we could take a look at the meat of the method, which was the long series of if statements. We worked out that some of them were being used for flow control, which we replaced with a traditional for loop (incidentally removing the "smell" of having to turn off checkstyle) and [simplified the if statements](https://blog.jetbrains.com/idea/2017/09/code-smells-if-statements/) to something easier to reason about.

At the end of all of this, we had simplified this method to something that fits on a single screen, and it is easier to reason about. This version is even shorter than that in the last article, thanks to several readers who pointed out further simplifications.

This code still demonstrates several smells and can benefit from further refactoring, but it's a definite improvement on the original.

What we haven't really done is address some of the larger problems, particularly around the domain model being difficult to work with. It may be the case that it's hard to make further improvements to the method without addressing underlying design issues. We did introduce a new class, `ValidatedQuery`, which may help us to evolve our model in the right direction, but ultimately we didn't address some of the root problems that caused this in the first place. For example, the need to iterate over a String to identify a particular `MappedField` (instead of having a model that allows us to navigate directly to a field from a path); and the fact that it's very hard to get a `MappedClass` for a `MappedField`, even though in theory every field lives in some class. Our process of working on smaller, lines-of-code-level smells may have helped us get closer to identifying these design smells, but they haven't given us much of an opportunity to do anything about them.

### **Approach 3: Step Back and Try to Model the Problem**

I'm not going to cover this in any real detail, but if you're interested my first serious attempt to refactor this method can be found in [this branch here](https://github.com/trishagee/morphia/blob/blog-mutability-4/morphia/src/main/java/org/mongodb/morphia/query/QueryValidator.java). With this approach, instead of looking at individual smells (e.g. mutation) or individual lines of code (e.g. how can I simplify this if statement), I looked at what the code was doing and tried to model it more accurately. For example, I introduced an enumeration to represent the for loop and moved any code that was responsible for iteration logic into that class. I introduced a `FieldPathElement` to encapsulate all the information about each thing we were iterating over.

I was happy with this for a while, particularly as I could imagine some of the new types (which I introduced as inner classes but intended to set free as "real" classes) could be valuable for refactoring other areas of the code. But as I went further and further, I effectively moved all the complexity that was in `validateQuery` into my new classes - more or less the same complexity existed, just in different places.

This approach can be a good way of encouraging a bit of redesign and may lead to new classes that can help you to refactor other areas of your code. But if you're not careful you may find you have all the same problems as before, just in different places.

## **In Summary**

The hardest thing about tackling complex code (other than working out what the code is actually supposed to do) is figuring out where to start. It can be really overwhelming to see blocks of code with multiple problems, and it's hard to know what's the best thing to do.

I have listed three different approaches here, and there are, no doubt, many more (please feel free to suggest them in the comments). Each approach has its pros and cons, and some developers will be more comfortable with one than another. Despite my preference for approach 3, as I think it is a) fun to model problems "correctly" and b) good to attempt to tackle design-level issues, I actually found approach 2 much easier and it gave me simpler code. It was also less risky and easier to reason about the impact of each step.

There's nothing to stop you combining approaches either. As a result of tackling specific code smells, I was then able to apply step 1 to break the problem into smaller pieces. Now the core of the method is simpler and easier to reason about, I may have more success at applying approach 3 (which we already made a start on with the introduction of ValidatedQuery) to help improve the domain model.

Symptoms

  * Very long and/or complicated methods or classes.
  * Seeing more than one smell when you first glance at the code.
  * That feeling of "Argh! What's this???"

Possible Solutions

  * Break the code into smaller sections.
  * Attempt to fix just one smell at a time.
  * Introduce new domain objects to model what's happening in the code.
  * Rename variables/fields, and extract very small well-named methods, to "document" what the code's doing as you work with it. Even writing comments can help.
  * As you discover what features the code is providing, and, even more importantly, as you identify edge cases it may be trying to cater for, write tests to document these.
  * Combining approaches may lead to the best version of the code.
