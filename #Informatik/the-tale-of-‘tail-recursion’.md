# The Tale of ‘Tail Recursion’

_Captured: 2017-05-01 at 20:41 from [dzone.com](https://dzone.com/articles/the-tale-of-tail-recursion?edition=292955&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-30)_

The single app analytics solutions to take your web and mobile apps to the next level. [Try today!](https://dzone.com/go?i=208121&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143155%3Bdc_trk_aid%3D321036346%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D)

**Recursion** in [computer science](https://en.wikipedia.org/wiki/Computer_science) is a method where the solution to a problem depends on solutions to smaller instances of the same problem (as opposed to [iteration](https://en.wikipedia.org/wiki/Iteration#Computing)).

Recursions are really cool and highly expressive. For example, consider this factorial function:

![imageedit_2_7440821029](https://maheshkndpl.files.wordpress.com/2017/04/imageedit_2_74408210291.png?w=640)

But if I increase the size of input, the code will blow up.

![imageedit_4_3062358181](https://maheshkndpl.files.wordpress.com/2017/04/imageedit_4_30623581811.png?w=640)

**Recursions** don't scale very well for large input sizes. And in practical way, I want to use recursions when the problem size is complex and big. So, it kind of defeats the purpose. You can't use it when you need it the most.

This is where a fairly interesting set of techniques come in.

Distinction between a procedure and process.

> Procedure: The code we write.
> 
> Process: The code that runs.

So essentially, the idea is to write a piece of code that gets transformed into an optimized one when we run it.

We can write such code in the following ways:

  * We can write code in an iterative procedure and run it as an iterative process. But it is not expressive.

  * And we can write code in a recursive procedure and run it as a recursive process. Unfortunately, it does not scale. When our input size gets big, it fails.

  * Another technique is to use some compiler magic if we can to write code as a recursive procedure and transform it into an iterative process under the covers. An implementation with this property is called **tail-recursive**.

![imageedit_16_7482961416](https://maheshkndpl.files.wordpress.com/2017/04/imageedit_16_7482961416.png?w=640)

So, now it is working and the stack didn't blow up this time. In order to see how it works, let's analyze the stack trace of both functions:

![imageedit_10_4364322468](https://maheshkndpl.files.wordpress.com/2017/04/imageedit_10_4364322468.png?w=640)

In a normal recursive function, we are **five levels deep**. Now let's see the stack trace of tail-recursive code.

![imageedit_12_5615457333](https://maheshkndpl.files.wordpress.com/2017/04/imageedit_12_5615457333.png?w=640)

Notice the difference in output. The point here is that there is** only one level of stack**. Structurally, we didn't reduce number of recursive calls. We are still going through five recursions. The reason we have only one level of stack is that the compiler was able to optimize it. Very quietly under the covers, the compiler modified this recursion into a simple iteration.

I hope this has been helpful!

CA App Experience Analytics, a whole new level of visibility. [Learn more.](https://dzone.com/go?i=208122&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143157%3Bdc_trk_aid%3D321036346%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D)
