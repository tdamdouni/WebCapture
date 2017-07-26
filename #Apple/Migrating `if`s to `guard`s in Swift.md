# Migrating `if`s to `guard`s in Swift

_Captured: 2015-12-30 at 12:58 from [ericasadun.com](http://ericasadun.com/2015/12/29/migrating-ifs-to-guards-in-swift/)_

Scattered throughout my code are uncountable variations on the following statement:
    
    
    if some condition {continue}

Recently, I have been converting a vast swath of these from `if` statements to `guards`. This post describes my reasons for voluntarily performing this migration: a step that seemingly has no impact on the efficiency or correctness of my code.

## The Guard Statement

Guard statements are best known for adding conditional bindings to an enclosing scope:
    
    
    guard let value = possibleNil else {leave scope}

But guards can also differentiate positive and negative execution paths:
    
    
    guard some condition else {continue}

In this latter form, guard statements act as non-fatal assertions. They prevent forward progress should that precondition fail. It checks a condition and then, if false, leaves scope via continue, break, return, etc. For example, in loops, they limit whether each iteration is fully run. In functions, they prevent bad data from causing errors.

A properly-constructed `guard` statement takes on the metaphoric characteristics of a human traffic flagman. It allows your code to proceed only when it conforms to certain rules.

## Establishing Execution Requirements

A general guard statement establishes requirements for execution. It also provides a safe path for transferring control if and when those requirements fail. Contrast that behavior with `assert()` and `precondition()`. Like these other runtime checks, guards add tests for desired state. However, its outcome is not noisy fatal errors that terminate execution.

Guards with requirements are _not_ substitutes for normal if clauses. Avoid `guard` when a Boolean false value introduces side effects or runs a true execution branch. Instead, `guard` creates instantly identifiable predicates that establish the required conditions for code to execute properly and offer early exit on failure.

## Refactoring

The `guard` keyword jumps out from code in a way that unambiguously distinguishes these statements from `if`. Even though my code would continue to operate without my by-hand-migration, upgrading to `guard` from `if` improves readability and enhances the clarity of my intent.

Placing guards at the start of scopes, as I do with assertions, forms a new kind of requirements block. Dave Abrahams wrote about the roles of assert and precondition on the Swift Evolution list:

> The two functions have distinct roles:  
- `assert`: checking your own code for internal errors.  
- `precondition`: for checking that your clients have given you valid arguments.

To this, I add `guard`: establishing a set of requirements that must be met before the code that follows can be safely executed. Consider refactoring any statement that say, in essence, "unless this statement is true, do not progress any further".

Are you migrating to guard in your own code? And if so, what are the rules you use to decide whether to stay with "if" or switch to "guard"? Let me know in the comments or throw me a tweet or email.

[ Tweet this Post ](https://twitter.com/share?text=Migrating%20%60if%60s%20to%20%60guard%60s%20in%20Swift&url=http://ericasadun.com/2015/12/29/migrating-ifs-to-guards-in-swift/&counturl=http://ericasadun.com/2015/12/29/migrating-ifs-to-guards-in-swift/)
