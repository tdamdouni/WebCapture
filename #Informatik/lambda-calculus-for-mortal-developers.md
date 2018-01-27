# Lambda Calculus for Mortal Developers

_Captured: 2017-11-14 at 21:15 from [dzone.com](https://dzone.com/articles/lambda-calculus-for-mortal-developers?edition=334873&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-14)_

Get the Edge with a Professional Java IDE. [30-day free trial](https://dzone.com/go?i=255333&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-preroll%26utm_campaign%3Didea).

Lambda Calculus sounds like an arcane term that only functional programming wizards can understand. Nothing could be further from the truth. We use Lambda Calculus every day when we program. It is the most reducible form of all Functional Programming languages; the primitive building block of Functional Programming.

## The Atoms of Lambda Calculus

Lambda Calculus is based on three basic building blocks: **expressions**, **variables**, and **functions**, which are combined to form other expressions.

**Variables** are not the ones we use to temporarily store values in imperative languages; variables in Lambda Calculus are the parameters of functions.

**Functions** consist of a head and a body. The head is a lambda plus a variable, and the body is an expression. As we will see later, functions have only one parameter. A function looks like this:

`λx.x`

λx is the head, the second x is the body, and the dot symbol (.) separates both. This example is the _identity function_.

Functions are also known as **abstractions**. The reason is that they allow us to generalize a computation and reuse it for the different values of the variable (or parameter).

**Expressions** are evaluated until an irreducible term is obtained as a result. An example of a simple expression could look like the following:

`(λx.x) 3`

(λx.x) is a function, as we have seen in the previous example. 3 is the parameter the function is applied to. This expression will be evaluated and reduced until an irreducible term is obtained (we will explain this process later).

## Types of Variables

We have seen so far functions with one variable in the head. When applying the function to an expression, the occurrences of the variable in the body are substituted with the applied expression. These kinds of variables are called **bound variables**.

Example:

`(λx.x) 3`

When the lambda is applied to the 3 parameter, the x variable is substituted with this value in the body. We will see this process in more detail later.

Nothing strange so far; we use functions and variables substitution every day when coding.

Another type of variable are **free variables**. They appear in the body, but not in the head. In other words, they cannot be bound. Their values are defined outside of the function they are referenced in. Their scope is not local to the function. This has some implications during the evaluation of the function.

Example:

`λx.xz`

The variable z does not appear in the head, therefore it cannot be bound and substituted in the scope of the function.

## Alpha and Beta to Reduce Them All

We've talked about expressions, which are used to create more complex abstractions (or functions). Later on, we will want to _reduce_ these expressions in order to get the value they produce. In this process, also called _evaluation_, two new concepts are involved:

### Alpha Equivalence

Two expressions are _alpha-equivalent_ if they can be obtained from each other; in other words, if replacing the bound variables with other variables gives us back an equivalent expression. In simple terms, this means that we can use different variable names for the same function as long as we preserve their meaning in the body of the function.

Examples:

These alpha-equivalent functions could be used instead of the other ones, and the result, when evaluating the expression, would still be the same. This is important when there are name clashes during beta reduction.

What about free variables?

Free variables cannot be substituted if we want to preserve alpha equivalence. This makes sense because different free variables can mean different things and they are irreducible, so they aren't equivalent in the context of a function.

Is alpha equivalence something really new for developers? I don't think so. Every time we rename a parameter in one of our functions, we are applying this concept.

### Beta Reduction

The process of evaluating (reducing) a lambda expression is known as beta reduction. It's called _reduction_ because the head is consumed (reduced) by substituting its parameter in the body with the value the function was applied to.

Example: apply the identity function to 3.

This is also called _application_. [x:=3] means that we substitute x with 3. There are other kinds of notation for variable substitutions, but I find this one quite clear and more familiar for developers, as it reminds of variable assignations.

The process of reducing more complex applications is quite simple, based on a few rules: Applications are left associative. Using parenthesis helps to clarify the associativity when there are more than a few terms. The leftmost outermost term is applied to the leftmost lambda. Free variables name clashes are solved by applying alpha equivalence. Free variables cannot be reduced.

Example:
    
    
    Apply (λx.xz), the leftmost outermost term.
    
    
    ((λx.xz)y)(λy.y)

zy is not reducible anymore, it's a fully evaluated expression. At this stage, we say that zy is in **beta normal form**. In Programming words, this means that the function was _evaluated_ and returned the result term, which cannot be reduced any further.

## Multiple Parameters

So far, we've seen how to work with functions with only one parameter. How do we reduce functions with two or more parameters? As lambdas can only bind one parameter, the way to rearrange several parameters is to split the head into nested heads, each one containing a single parameter. For example:

`λxy.yx`

This function contains one head with two parameters. We could split the head in two:

`λx.λy.yx` or `λx.(λy.yx)`

Now we have a function with one parameter, and its body contains another function with one parameter (the second parameter, y, in the original head). When reducing this expression, y will be bound and substituted as usual, and x will be bound and substituted before reducing the nested function.

This simple idea is called **currying**.

Finally, we could have a look at an example of beta reduction with a name clash, to see the how alpha equivalence works in practice:

`(λxyz.xyz)(λx.xz)(λx.x)`

The head of the leftmost lambda has three parameters. They can be split into three different heads.

`(λx.λy.λz.xyz)(λx.xz)(λx.x)`

The next step would be to bind [x:=(λx.xz)]. The problem is that there is already az free variable in one of the heads of the leftmost lambda. This is a name clash, as they are different variables but have the same name. To solve this, we can rename one of them before we apply the binding.

`(λx.λy.λz'.xyz')(λx.xz)(λx.x)`

Now, we can bind [x:=(λx.xz)] safely.

This function has no arguments to be applied, so we are done.

We have seen how to beta reduce an expression containing functions with multiple parameters. The process is the same as per functions with one parameter. But, are all expressions reducible to beta normal form?

## Divergence

When an expression is beta reduced and produces a result, we say that the expression converged. But not all expressions converge. Let's see a classical example:

As x appears twice in the body, the new expression is the same as the original one.

The next application returns again the same expression.

This expression does not converge and will never be reduced to beta normal form. When this happens, we say that the expression _diverges_.

Some expressions will even grow when evaluating them:
    
    
    (λx.xxx)(λx.xxx)(λx.xxx)(λx.xxx)
    
    
    (λx.xxx)(λx.xxx)(λx.xxx)(λx.xxx)(λx.xxx)

Does divergence remind you of something? It is an infinite recursion. Any Java developer has seen this more than once. The Java API calls it `StackOverflowError`.

## Was It That Bad After All?

As we've seen, the ideas behind Lambda Calculus are more familiar to developers than we thought in the first place. Names such as alpha equivalence or beta reduction can sound scary, but we, as developers, already use these concepts in our daily work. The importance of Lambda Calculus not only applies to Functional Programming, but also to the basic building blocks of Programming itself.

## References

This article was first published on the [Codurance blog](https://codurance.com/publications/).

[Get the Java IDE](https://dzone.com/go?i=255334&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-postroll%26utm_campaign%3Didea) that understands code & makes developing enjoyable. Level up your code with IntelliJ IDEA. [Download the free trial](https://dzone.com/go?i=255334&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-postroll%26utm_campaign%3Didea).
