# O(n^2) vs O(n) Techniques for Finding the Max Count of a Digit in the Given Numerical String

_Captured: 2018-06-22 at 14:58 from [dzone.com](https://dzone.com/articles/on2-vs-on-techniques-for-finding-the-max-count-of?edition=383245&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-06-22)_

[Learn how error monitoring with Sentry](https://dzone.com/go?i=286425&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzoneperformancezone%26utm_campaign%3Dsponsorship) closes the gap between the product team and your customers. With Sentry, you can focus on what you do best: building and scaling software that makes your users' lives better.

Hello, Buddies. I came across this question related to Java String handling, so I thought of sharing it .

**Question:** Given a string made up of n number of digits, find the digit having the maximum number of occurrence.   
For example: "12333123654"  
Here, 3 is the digit repeated the maximum number of times.

For a complete solution, refer to the **Answer:**

The first approach is to scan the string as a character array, maintain a map that can update the occurrence count. In the end, find the max value and then the corresponding key.

**Question: **What is the complexity of this solution?

**Answer:** O(n^2) since we are iterating and using contains check.

**Question: **Any better approach? A solution with O(n) complexity, i.e. having a lookup array.

**Answer:** We have digits 0 to 9, which can be related to each index of an array. For the values, update the occurrence count in the values.

Happy coding! Check out the repo at [this link](https://github.com/namitsharma99/numArrayFindMaxOccurrence/blob/master/NumericalString.java).

[What's the best way to boost the efficiency of your product team](https://dzone.com/go?i=286426&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzoneperformancezone%26utm_campaign%3Dsponsorship) and ship with confidence? Check out this [ebook](https://dzone.com/go?i=286426&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzoneperformancezone%26utm_campaign%3Dsponsorship) to learn how Sentry's real-time error monitoring helps developers stay in their workflow to fix bugs before the user even knows there's a problem.
