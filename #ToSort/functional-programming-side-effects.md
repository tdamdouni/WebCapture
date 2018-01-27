# Functional Programming: Side Effects

_Captured: 2017-11-14 at 21:09 from [dzone.com](https://dzone.com/articles/side-effects-1?edition=334873&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-14)_

"[Automated Testing: The Glue That Holds DevOps Together"](https://dzone.com/go?i=236222&u=http%3A%2F%2Finfo.saucelabs.com%2FAutomated_Testing_Glue_LP-DZone.html%3Futm_medium%3Dpre-roll_textlink%26utm_content%3Darticle) to learn about the key role automated testing plays in a DevOps workflow, brought to you in partnership with Sauce Labs.

Functional programming is based on the simple premise that **your functions should not have side effects**; they are considered evil in this paradigm. **If a function has side effects we call it a procedure**, so functions do not have side effects. We consider that a function has a side effect if it modifies a mutable data structure or variable, uses IO, throws an exception or halts an error; all of these things are considered side effects. The reason why side effects are bad is because, if you had them, a function can be unpredictable depending on the state of the system; when a function has no side effects we can execute it anytime, it will always return the same result, given the same input.

Don't get me wrong, this paradigm doesn't try to get rid of side effects, just limit them when they are required. Side effects are needed because without them our programs will do only calculations. We often have to write to databases, integrate with external systems or write files.

## Referential Transparency

A function that returns always the same result for the same input is called a pure function. A pure function, therefore, is a function with no observable side effects, if there are any side effects on a function the evaluation could return different results even if we invoke it with the same arguments. We can substitute a pure function with its calculated value, for example:

for the input

`f(2, 2)`

can be replaced by

`4`

It is like a big [lookup table](https://en.wikipedia.org/wiki/Lookup_table). We can do so because it does not have any side effects. The ability to replace an expression with its calculated value is called [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).

Referential transparency is important because it allows us to substitute expressions with values. This property enables us to think and reason about the program evaluation using the substitution model. Hence, we can say that expressions that can be replaced by values are deterministic, as they always return the same value for a given input.

## Local Side Effects

We defined a function with side effects as a function that does some visible mutation, uses IO, etc… But what about functions that always return the same value even though they do some side effect internally? For example:
    
    
      0 to i foreach((i) => result = result + i)

That function has a side effect; it mutates the result variable in every iteration of the loop. But even if it does, that side effect the function can be replaced by a value, because the side effects are not visible from the outside. In other words, the function is deterministic, `sumsIntsUntil(5) = 10` and `sumsIntsUntil(10) = 45` etc… We say that the function has a local side effect, but the user of that function does not care as it does not break our substitution model. Therefore, this function is pure, even if it has a local side effect.

Consider a similar example, but with a slight difference:
    
    
        0 to i foreach((i) => result = result + i)

With this particular variation, when we call the function for the first time: `sumsIntsUntil(5)` will give us 10, but if we call it again with the same input, it will give us 20. This is the reason why variable mutation is considered a side effect, even though in the previous example, the side effect is local to the function, making it deterministic.

The use of local side effects is a common practice to optimize functions. We can find some examples in Scala's List class. For instance, this is the implementation of the drop function:
    
    
      while (!these.isEmpty && count > 0) {

As you can see, there are a lot of names and terms in this little post; there are a lot of them in this paradigm, and they are very important because it gives us a vocabulary to express more complex concepts in terms of other concepts. I will continue explaining more concepts in the next post.

## References

_This article was first published on the [Codurance blog](https://codurance.com/publications/)._

[Learn about the importance of automated testing](https://dzone.com/go?i=236223&u=http%3A%2F%2Finfo.saucelabs.com%2FAutomated_Testing_Glue_LP-DZone.html%3Futm_medium%3Dpost-roll_textlink%26utm_content%3Darticle) as part of a healthy DevOps practice, brought to you in partnership with Sauce Labs.
