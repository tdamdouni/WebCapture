# Multidimensional Arrays vs. Method References

_Captured: 2018-01-12 at 20:11 from [dzone.com](https://dzone.com/articles/multidimensional-arrays-vs-method-references?edition=352102&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-11)_

Playing with multidimensional arrays and method references can be tricky sometimes.

## **Referencing an Array's Constructor**

Let's say we want to create a function that takes an integer value and returns an array with a size initialized to that value.

We can do that fairly easily using a lambda expression literal:

But what if we wanted to grant it its own name?

There are a number of ways to do that. The two most natural ways would be to represent it either as a _Function<Integer, String[]>_ or an _IntFunction<String[]>:_
    
    
    IntFunction<String[]> foo1 = size -> new String[size];
    
    
    Function<Integer, String[]> foo2 = size -> new String[size];

Since our logic is trivial and we're just passing a raw parameter straight to the constructor, we might as well directly reference the array's constructor to avoid boilerplate:

## **Referencing a Multidimensional Array's Constructor**

Why not do the same with a 2D array?
    
    
    (rows, cols) -> new String[rows][cols];
    
    
    BiFunction<Integer, Integer, String[][]> foo2D2 = 

Unfortunately, the method reference approach leaves us with a compilation error. Do you already have an idea why?

Since multidimensional arrays in Java aren't really multidimensional (they're just arrays of arrays), when writing _String[][]::new, _we're still referencing exactly same one-parameter constructor as in the first example:

It's just the type that array stores isn't _String_ anymore but _String[]:_

Essentially, both cases could be represented as a generic _IntFunction<T[]>_.

Hopefully, everything becomes clear if we look at the standard lambda expression equivalent of the second example:

This short write-up was brought to you by this [StackOverflow question](https://stackoverflow.com/questions/40561843/method-references-to-multidimensional-arrays-in-java-8/40561911#40561911).
