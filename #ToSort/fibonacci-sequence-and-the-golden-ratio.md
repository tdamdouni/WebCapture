# Fibonacci Sequence and the Golden Ratio

_Captured: 2017-02-18 at 18:45 from [pi3.sites.sheffield.ac.uk](http://pi3.sites.sheffield.ac.uk/tutorials/week-1-fibonacci)_

### Using Python files

Last time, we wrote our Python commands directly into the shell, by typing at the prompt (`>>>`). This is OK for simple commands, but quickly becomes cumbersome. Especially if, like me, you make mistakes when entering the code. Also, when you quit Python, your precious lines of code may be forgotten! From now on, we will keep our programs in Python files.

In the menu of IDLE, go to File -> New Window. In the new window, type `print "Hello everyone!"`, and now save the file, by going to File -> Save. I save all my files in a directory Code/Pi3/, under my home directory. You may wish to create a new directory. Choose a suitable filename, for example, `hello.py`. Note that all Python files end with the extension `.py` .

You can run your program (i.e. execute the commands in the python file, in the order in which they appear) by pressing F5 in IDLE, or selecting the menu option Run -> Run Module. You should now see your greeting appear in the Python Shell.

You can also run your program directly from the command line, by typing `python hello.py`

From now on, I suggest that you save (Ctrl-S) your Python commands in files, and run them with F5 in IDLE. At the end of this page, I have attached some example Python files which you may wish to investigate.

## The Fibonacci Sequence

You can see that the next value in the list is found by adding together the preceding two values. For example, 13 = 8 + 5, 21 = 13 + 8, 34 = 21 + 13, etc. Mathematically, we can define the sequence with a _recurrence relation_:

and two initial 'seed values', **F(0) = 0** and **F(1) = 1**.

Leonardo of Pisa, known as Fibonacci, introduced this sequence to European mathematics in his 1202 book [Liber Abaci](http://en.wikipedia.org/wiki/Liber_Abaci). It is thought to have arisen even earlier in Indian mathematics.

Let's look at a simple code -- from the [official Python tutorial](http://docs.python.org/2/tutorial/introduction.html#first-steps-towards-programming) \-- that generates the Fibonacci sequence.

`# Fibonacci series:`  
`# the sum of two elements defines the next`  
`a, b = 0, 1`  
`while b < 10:`  
`print b`  
`a, b = b, a+b`

I've put these commands in `fib.py`, attached to this page. Try running `fib.py` in IDLE. Do you get the output that you expected?

This example introduces some new Python commands, which are [explained here](http://docs.python.org/2/tutorial/introduction.html#first-steps-towards-programming). Let's take a look at each line in turn:

  * The `#` symbol allows us to write a "comment". A comment is just human-readable text, that the computer will ignore. Adding comments to your code is a very good idea, especially if -- like me -- you have a short memory. 
  * `a, b = 0, 1` This line is equivalent to two lines, a = 0 and b = 1, executed simultaneously. The comma allows two lines to be written in one (but see below for a subtlety)
  * `while b < 10:` This is another type of loop statement, similar to the `for i in range(10):` syntax we saw in [tutorial 0](http://pi3.sites.sheffield.ac.uk/tutorials/week-0). When the program reaches this line, Python will check whether the value of `b` is less than 10. If so, it will run the indented statements once, and will then return again to the while statement. If `b` is still less than 10, then it will run the indented statements again ... and so on. It will only stop this process when b is found not to be less than 10.   

  * `print b` This prints the value of b to the output
  * `a, b = b, a+b` It's tempting to interpret this as two statements, executed one after the other, i.e. first assign the value of b to a, and then assign the value of a+b to variable b. But this is not correct. In fact, this is a _multiple assignment_. The correct interpretation is, make a pair of values, from b and a+b. Then, assign them to a and b simultaneously. In this way, the value of a is not replaced until the final step. The same result could be achieved with three lines of code:  


`a_old = a`  
`a = b`  
`b = a_old + b`

### An iterative method

There are many other ways to compute the Fibonacci sequence. One possibility is the following code:

`# Fibonacci series`  
`# Iterative method, ``with values saved in a list`  
`fiblist = [0,1]`  
`for i in range(10):`  
`    fiblist.append(fiblist[i] + fiblist[i+1])`  
`print fiblist`

This is an **iterative** method, like the previous example -- it uses a loop. The main difference is that I keep the values in a list, and "appending" new values to the end of the list.

Do you see how we can retrieve the individual elements of the list? Here, `fiblist[0]` refers to the first element of the list (the "head"), `fiblist[1]` to the second, etc. In many computing languages it is conventional to number from zero, rather than from 1.

### A recursive method

Fibonacci numbers are defined mathematically (above) with (i) a recurrence relation F(n+1) = F(n) + F(n-1) and (ii) base cases F(1) = 1, F(0) = 0. Rather than using an iterative method, featuring a loop, we may instead define a "recursive" function which is closer in spirit to this mathematical definition.

`def fibRec(n):`  
`    if n < 2:`  
`        return n`  
`    else:`  
`        return fibRec(n-1) + fibRec(n-2)`

See how the function calls itself repeatedly? This is an example of a **recursive** method. By repeatedly calling itself, the recurrence proceeds downwards until the base case is reached.

## The Golden Ratio

Now let's think about the ratio of successive elements of the sequence, i.e. F(n+1) / F(n). It turns out that this ratio tends towards a fixed value, as the Fibonacci numbers get larger. Moreover, this particular value is very well-known to mathematicians through the ages. It is known as the **[golden ratio**](http://en.wikipedia.org/wiki/Golden_ratio), and is given by  
  

![](http://pi3.sites.sheffield.ac.uk/_/rsrc/1472766562965/tutorials/week-1-fibonacci/fibeq2.png?height=32&width=200)

  
Try computing the ratio of successive terms in the list of Fibonacci numbers, with a statement like:  
  
`gratio=``[fiblist[i] / float(fiblist[i-1]) for i in range(2,len(fiblist))]`  
`print gratio`

What do you see? How close can you get to the precise value of the Golden Ratio? (This code may be found in `gratio.py` at the end of the page).  

### Graphical Representation

The Fibonacci numbers can be represented graphically as the lengths of arms in a spiral, or as squares tiling a rectangle, as shown below. In future weeks, I will show how to draw such patterns using the `pygame` module.  

![Fibonacci squares in a rectangle](http://pi3.sites.sheffield.ac.uk/_/rsrc/1472766538327/tutorials/week-1-fibonacci/FibonacciBlocks.png?height=201&width=320)

The Golden Ratio is found in a special type of rectangle. When a rectangle is placed next to a square, as shown, they make a second rectangle. The Golden Ratio occurs when the two rectangles are **[similar**](http://en.wikipedia.org/wiki/Similarity_\(geometry\)), which means that the ratio of their side lengths is that same,` a/b = (a+b)/a`. This ratio is the Golden Ratio.  

![](http://pi3.sites.sheffield.ac.uk/_/rsrc/1472766539687/tutorials/week-1-fibonacci/SimilarGoldenRectangles.png?height=183&width=200)

### Binet's Formula  

  

There is actually a simple mathematical formula for computing the _n_th Fibonacci number, which does not require the calculation of the preceding numbers. It features the Golden Ratio:  
  

![](http://pi3.sites.sheffield.ac.uk/_/rsrc/1472766570405/tutorials/week-1-fibonacci/fibeq1.png?height=38&width=200)

  
This is called **Binet's formula**. We can implement Binet's formula in Python using a function:  
  

`def fibBinet(n):`  
`    phi = (1 + 5**0.5)/2.0`  
`    return int(round((phi**n - (1-phi)**n) / 5**0.5))`  

  
Note that `**` means "_raise to the power of_", and raising to the power of one-half (0.5) is mathematically equivalent to taking a square root. (Another way to take the square root would be using the math module, which we first needs to be loaded into Python: `import math` allows us to use `math.sqrt(5)`).  

  

This code might look a bit dodgy. For instance, how can we be sure that the square root will be taken _before_ the division? Here, we are relying on the fact that Python (like most languages) executes statements in a certain fixed order of precedence.  Raising-to-the-power takes precedence over division, which (like multiplication) takes precedence over addition and subtraction. See here for the [order of precedence](http://docs.python.org/2/reference/expressions.html#operator-precedence) of common operations. Where a different order is required, we should use brackets (as in the example above).   

  

Python code for all of these methods can be found in `fibonacci.py`, attached at the bottom of this page. Examples of other methods for calculating Fibonacci numbers can be found at [RosettaCode](http://rosettacode.org/wiki/Fibonacci_sequence) and at [LiteratePrograms](http://en.literateprograms.org/Fibonacci_numbers_\(Python\))  
  

### Challenges

  

**1\. **In the picture above, six squares are fitted inside a rectangle, leaving no space. In other words, the rectangle is tiled with squares. Can you add another square to make a new rectangle? How big is it? Now add another square ... how big? How does the size of the squares relate to the Fibonacci sequence?  
  
**2.** In the picture above, there are two squares of the same size. But if you could only use squares of different sizes (whole numbers), can you tile a rectangle?  If so, can you work out how?  [This is quite hard, if you need a hint, pi3challenge@sheffield.ac.uk]  
