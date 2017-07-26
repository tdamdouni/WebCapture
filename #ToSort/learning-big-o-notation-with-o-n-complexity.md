# Learning Big O Notation With O(n) Complexity

_Captured: 2017-04-26 at 20:19 from [dzone.com](https://dzone.com/articles/learning-big-o-notation-with-on-complexity?edition=292930&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-26)_

Discover 50 of the latest mobile performance statistics with the [Ultimate Guide to Digital Experience Monitoring](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE).

Big O Notation is one of those things that I was taught at university, but I never really grasped the concept. I knew enough to answer very basic questions on it, but that was about it. Nothing has changed since then as I have not used or heard any of my colleagues mention it since I started working. So, I thought I'd spend some time going back over it and write this post summarizing the basics of Big O Notation along with some code examples to help explain it.

So, what is Big O Notation? In simple terms:

  * It is the relative representation of the complexity of an algorithm.
  * It describes how an algorithm performs and scales.
  * It describes the upper bound of the growth rate of a function and could be thought of the _worst case scenario_.

Now for a quick look at the syntax: _O(n2)_.

_n_ is the number of elements that the function receiving as inputs. So, this example is saying that for _n_ inputs, its complexity is equal to _n2_.

## Comparison of the Common Complexities

![Image title](https://dzone.com/storage/temp/5068673-screen-shot-2017-04-24-at-21022-pm.png)

As you can see from this table, as the complexity of a function increases, the number of computations or time it takes to complete a function can rise quite significantly. Therefore, we want to keep this growth as low as possible, as performance problems might arise if the function does not scale well as inputs are increased.

![bigo](https://lankydanblog.files.wordpress.com/2017/04/bigo.png?w=616)

> _Graph showing how the number of operations increases with complexity._

Some code examples should help clear things up a bit regarding how complexity affects performance. The code below is written in Java but obviously, it could be written in other languages.

## O(1)

_O(1)_ represents a function that always takes the same take regardless of input size.

## O(n)

_O(n)_ represents the complexity of a function that increases linearly and in direct proportion to the number of inputs. This is a good example of how Big O Notation describes the _worst case scenario_ as the function could return the _true_ after reading the first element or _false_ after reading all _n_ elements.

## O(n2)
    
    
      for (int outer = 0; outer < input.size(); outer++) {
    
    
        for (int inner = 0; inner < input.size(); inner++) {
    
    
          if (outer != inner && input.get(outer).equals(input.get(inner))) {

_O(n2)_ represents a function whose complexity is directly proportional to the square of the input size. Adding more nested iterations through the input will increase the complexity which could then represent _O(n3)_ with 3 total iterations and _O(n4)_ with 4 total iterations.

## O(2n)
    
    
        return fibonacci(number - 1) + fibonacci(number - 2);

_O(2n)_ represents a function whose performance doubles for every element in the input. This example is the recursive calculation of Fibonacci numbers. The function falls under _O(2n)_ as the function recursively calls itself twice for each input number until the number is less than or equal to one.

## O(log n)
    
    
    public boolean containsNumber(List<Integer> numbers, int comparisonNumber) {
    
    
      int high = numbers.size() - 1;
    
    
        int middle = low + (high - low) / 2;
    
    
        if (comparisonNumber < numbers.get(middle)) {
    
    
        } else if (comparisonNumber > numbers.get(middle)) {

_O(log n)_ represents a function whose complexity increases logarithmically as the input size increases. This makes _O(log n)_ functions scale very well so that the handling of larger inputs is much less likely to cause performance problems. The example above uses a binary search to check if the input list contains a certain number. In simple terms, it splits the list in two on each iteration until the number is found or the last element is read. This method has the same functionality as the _O(n)_ example -- although the implementation is completely different and more difficult to understand. But this is rewarded with a much better performance with larger inputs (as seen in the table).

There is much more to cover about Big O Notation but hopefully you now have a basic idea of what Big O Notation means and how that can translate into the code that you write.

[Is your APM strategy broken?](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) This [ebook](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) explores the latest in Gartner research to help you learn how to [close the end-user experience gap in APM](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE).
