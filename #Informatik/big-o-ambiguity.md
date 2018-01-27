# Big-O Ambiguity

_Captured: 2018-01-19 at 13:24 from [dzone.com](https://dzone.com/articles/big-o-inaccuracy?edition=355098&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-01-19)_

[Learn how _real _real-time monitoring is critical for DevOps](https://dzone.com/go?i=272435&u=https%3A%2F%2Fsignalfx.com%2Fsolutions%2Fenabling-devops%2F). Because you can't build what you can't see.

## Back to University

Most people talk about Big-O notation when it comes to runtime and space complexity. But when you recall your first year at university, most probably you had an Algorithm and Data Structure course when you have learned not only Big-O notation, but also **Big-Ω** (Omega) and **Big-Θ** (Theta). Here is a very brief definition:

  * if _f(n)_ is _O(g(n))_, it means that _f(n)_ grows asymptotically **no faster** than _g(n)_
  * if _f(n)_ is _Ω(g(n))_, itmeans that _f(n)_ grows asymptotically **no slower** than _g(n)_
  * if _f(n)_ is _Θ(g(n))_, it means that _f(n) _grows asymptotically at the **same rate** as _g(n)_

In other words, _O(g(n))_ is an upper bound which means that from certain point (_n0_ on the graph below), _c*g(n)_ is never below the function _f(n) _which we are analyzing (don't worry about _c_ -- it is just a constant).

![Image title](https://dzone.com/storage/temp/7838462-big-o-1.png)

_Ω(g(n))_ is a lower bound which means that from the certain point (_n0_), _c*g(n)_ is never above our function_ f(n)_.

![Image title](https://dzone.com/storage/temp/7838463-big-omega-1.png)

_Θ(g(n))_ means that function _g(n)_ grows exactly in the same asymptotic way as our function _f(n)_. Obviously, everything that is _Θ(g(n))_ is also _O(g(n))_ and _Ω(g(n))_, but not the other way around. On the graph below, we have our function _f(n)_ which is tightly bounded by function _g(n)_ from both sides (multiplied by constants _c_1_ and _c2_).

![Image title](https://dzone.com/storage/temp/7838477-big-theta-fixed-1.png)

## Bound Is Just a Bound

What's the runtime complexity expressed in Big-O notation of this simple snippet below?

It is obviously _O(n2)_. We have two nested loops and both of them iterate over the input array. What's less obvious is that answers such as _O(n3)_, _O(2n)_ and even _O(n!)_ are also correct. Take a look back at the definition of Big-O. These are all upper bounds of function _n2_. There is nothing wrong with saying that we are not more than 33 years old, when we are actually 25. It's a true statement, however not very informative. We prefer having **tight bounds** rather than loose bounds**.** That's why people are used to using as tight bounds as possible in Big-O notation. Nevertheless, if somebody asks you during an interview, what the time complexity of the algorithm, expressed in Big-O notation is, saying that it's something very high such as _O(n!)_ gives you quite good chance of being correct. However, I don't really recommend it ;)

If Big-O notation can be so ambiguous, why do we use it? Why don't we use Big-Θ instead of Big-O notation for all the algorithms we analyze? Wouldn't it give us way more precise information? It seems that there are a couple of reasons for that. First of all, it's very hard or even impossible to find a function which grows at exactly the same rate as the function we want to analyze. Have a look at this figure below (the function is defined for the integers _n ≥ 1_) and try to come up with an idea of what Big-Θ would it be?

![Image title](https://dzone.com/storage/temp/7838479-example-1-1.png)

It is not an easy task, is it? But let's try to bound it from both sides instead.

![Image title](https://dzone.com/storage/temp/7838480-example-2-1.png)

We can easily find two simple linear and constant functions which bound our function _f(n)_. Additionally, those are very tight bounds. Interested in what kind of algorithm would have this complexity? It can be actually something as simple as that:

Another reason why Big-O notation is used more often is that people usually worry about what's the worst that can happen. In such cases, Big-O is sufficient, because it guarantees that it can't get much worse than what we estimated (it can still get a bit worse because we drop some less dominant factors).

But the first example with two nested loops is trivial -- we can certainly say that it's _Θ(n2)_. It grows exactly at the same rate as the quadratic function. Similarly, the upper bound of the basic implementation of bubble sort is _O(n2)_. In the **worst case scenario**, you can't be better than that which means that it's also _Ω(n2)_. If we can find upper and lower bounds which are exactly the same, then we have our Big-Θ. So the runtime complexity of bubble sort is _Ω(n2)_, however, in most sources, it is expressed as _O(n2)_. Why is that? It seems that most people are more familiar with Big-O notation rather than Big-Θ. That's why Big-O is a little bit abused in computer science.

## Difference Between Bound and Case

In the previous paragraph I mentioned that in the worst case scenario, bubble sort is _Ω(n2)_. Why worst case scenario? Wouldn't it grow slower if we consider the best case scenario? Yes, it would. But when we use asymptotic notation, unless stated otherwise, we are talking about **worst-case **running time.

I've noticed that a lot of people confuse lower (Big-Ω) bound with the best case scenario, upper bound (Big-O) with the worst case and Big-Θ with an average case. But these terms are not the same. If they were, then we wouldn't have the best-case performance for quicksort expressed as _O(n log n)_, but _Ω(n log n)_. It's important to remember that we can calculate any of Big-Ω, Big-O, or Big-Θ for best, average and the worst-case scenarios separately.

## Summary

It seems somehow obvious that algorithm which has asymptotically constant time is better than a linear or polynomial algorithm. But is it always like that? Just because an algorithm is _Θ(1)_ doesn't mean it's necessarily going to run faster than _Θ(n2)_ algorithm for all sizes of _n_. Imagine _Θ(1)_ algorithm with an enormous constant number of long-running operations like 1 billion. Then _n_ parameter of _Θ(n2)_ algorithm would have to grow extremely large before it's slower than our _Θ(1)_ algorithm. It's important to keep in mind that asymptotic notation has its limitation and dropping some factors can potentially have a tremendous impact on algorithm performance in practice.

[Get real-time alerts and visualizations](https://dzone.com/go?i=272432&u=https%3A%2F%2Fsignalfx.com%2F%3Fsignup%3Dtrue) across your cloud infrastructure for real real-time cloud monitoring. [Try it FREE now](https://dzone.com/go?i=272432&u=https%3A%2F%2Fsignalfx.com%2F%3Fsignup%3Dtrue)!
