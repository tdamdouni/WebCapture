# How — and why — you should use Python Generators

_Captured: 2017-12-08 at 09:51 from [medium.freecodecamp.org](https://medium.freecodecamp.org/how-and-why-you-should-use-python-generators-f6fb56650888)_

![](https://cdn-images-1.medium.com/freeze/max/60/1*UifvzyheweFeO0u6nS7Q0g.jpeg?q=20)![](https://cdn-images-1.medium.com/max/2000/1*UifvzyheweFeO0u6nS7Q0g.jpeg)

> _Image Credit: [Beat Health Recruitment](https://beathealth.com.au/wp-content/uploads/2015/11/bigstock-Robotic-arm-concept-75270622.jpg)_

**Generators** have been an important part of Python ever since they were introduced with [PEP 255](https://www.python.org/dev/peps/pep-0255/).

Generator functions allow you to declare a function that behaves like an iterator.

They allow programmers to make an iterator in a fast, easy, and clean way.

What's an iterator, you may ask?

An **[iterator**](https://en.wikipedia.org/wiki/Iterator) is an object that can be iterated (looped) upon. It is used to abstract a container of data to make it behave like an iterable object. You probably already use a few iterable objects every day: strings, lists, and dictionaries to name a few.

An iterator is defined by a class that implements the **[Iterator Protocol**](https://docs.python.org/3/c-api/iter.html). This protocol looks for two methods within the class: `__iter__` and `__next__`.

Whoa, step back. Why would you even want to make iterators?

#### Saving memory space

Iterators don't compute the value of each item when instantiated. They only compute it when you ask for it. This is known as [lazy evaluation](https://en.wikipedia.org/wiki/Lazy_evaluation).

Lazy evaluation is useful when you have a very large data set to compute. It allows you to start using the data immediately, while the whole data set is being computed.

Let's say we want to get all the prime numbers that are smaller than a maximum number.

We first define the function that checks if a number is prime:
    
    
    def check_prime(number):  
        for divisor in range(2, int(number ** 0.5) + 1):  
            if number % divisor == 0:  
                return False  
        return True

Then, we define the iterator class that will include the `__iter__` and `__next__` methods:
    
    
    class Primes:  
        def __init__(self, max):  
            self.max = max  
            self.number = 1
    
    
        def __iter__(self):  
            return self
    
    
        def __next__(self):  
            self.number += 1  
            if self.number >= self.max:  
                raise StopIteration  
            elif check_prime(self.number):  
                return self.number  
            else:  
                return self.__next__()

`Primes` is instantiated with a maximum value. If the next prime is greater than the `max`, the iterator will raise a `StopIteration` exception, which ends the iterator.

When we request the next element in the iterator, it will increment `number` by 1 and check if it's a prime number. If it's not, it will call `__next__` again until `number` is prime. Once it is, the iterator returns the number.

By using an iterator, we're not creating a list of prime numbers in our memory. Instead, we're generating the next prime number every time we request for it.

Let's try it out:
    
    
    primes = Primes(100000000000)
    
    
    print(primes)
    
    
    for x in primes:  
        print(x)
    
    
    ---------
    
    
    <__main__.Primes object at 0x1021834a8>  
    2  
    3  
    5  
    7  
    11  
    ...

Every iteration of the `Primes` object calls `__next__` to generate the next prime number.

**Iterators can only be iterated over once.** If you try to iterate over `primes` again, no value will be returned. It will behave like an empty list.

Now that we know what iterators are and how to make one, we'll move on to generators.

### Generators

Recall that generator functions allow us to create iterators in a more simple fashion.

Generators introduce the `yield` statement to Python. It works a bit like `return` because it returns a value.

The difference is that **it saves the state** of the function. The next time the function is called, execution continues from **where it left off**, with the **same variable values** it had before yielding.

If we transform our `Primes` iterator into a generator, it'll look like this:
    
    
    def Primes(max):  
        number = 1  
        while number < max:  
            number += 1  
            if check_prime(number):  
                yield number
    
    
    primes = Primes(100000000000)
    
    
    print(primes)
    
    
    for x in primes:  
        print(x)
    
    
    ---------
    
    
    <generator object Primes at 0x10214de08>  
    2  
    3  
    5  
    7  
    11  
    ...

Now that's pretty pythonic! Can we do better?

Yes! We can use **Generator Expressions**, introduced with [PEP 289](https://www.python.org/dev/peps/pep-0289/).

This is the list comprehension equivalent of generators. It works exactly in the same way as a list comprehension, but the expression is surrounded with `()` as opposed to `[]`.

The following expression can replace our generator function above:
    
    
    primes = (i for i in range(2, 100000000000) if check_prime(i))
    
    
    print(primes)
    
    
    for x in primes:  
        print(x)
    
    
    ---------
    
    
    <generator object <genexpr> at 0x101868e08>  
    2  
    3  
    5  
    7  
    11  
    ...

This is the beauty of generators in Python.

### In summary…

  * Generators allow you to create iterators in a very pythonic manner.
  * Iterators allow lazy evaluation, only generating the next element of an iterable object when requested. This is useful for very large data sets.
  * Iterators and generators can only be iterated over once.
  * Generator Functions are better than Iterators.
  * Generator Expressions are better than Iterators (for simple cases only).

You can also check out my [explanation](https://medium.freecodecamp.org/how-i-used-python-to-find-interesting-people-on-medium-be9261b924b0) of how I used Python to find interesting people to follow on Medium.
