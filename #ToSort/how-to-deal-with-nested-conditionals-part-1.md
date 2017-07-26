# How to Deal With Nested Conditionals (Part 1)

_Captured: 2017-02-15 at 19:45 from [dzone.com](https://dzone.com/articles/how-to-deal-with-nested-conditionals?edition=269881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-15)_

In my current project, there are thousands of lines of code (LOC), some of which date back to 10 years ago. An important part of my day-to-day job is trying to understand and debug functions just like the following example (Listing 1). I omitted the boolean expressions and the code in branches, but there is still something wrong with it!

You might think, "What's the problem? If it's working, it's fine!" Indeed, it is working but:

  * Is it easy for you to read it?

  * Can you understand the execution flow?

  * What if you add new functionality to that function? Are you sure that you won't break existing requirements?

  * How testable is that function?

I think somebody knows the answers: _"**Any fool can write code that a computer can understand. Good programmers write code that humans can understand,**_"_ Martin Fowler, 2008._

The original code, 412 LOC in total, is much more complex in terms of readability and maintainability. There are multiple boolean expressions in almost every if statement; such as the code in Listing 2:

## **Decompose Conditional**

We can start refactoring with complicated conditionals. Extract methods for each boolean expression as follows. The result is still nested, but there is another technique -- consolidating conditional expressions -- that will help.

## **Consolidate Conditional Expression**

Another attempt to eliminate nested if-else statements could be combining multiple conditionals into a single conditional expression and extracting it; such as the code in Listing 3_:_

### **Step 1**: Consolidate Conditionals Into One Statement

### **Step 2**: Decompose Conditionals Into Relevant Functions
