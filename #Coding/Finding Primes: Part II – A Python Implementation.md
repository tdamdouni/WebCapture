# Finding Primes: Part II – A Python Implementation

_Captured: 2016-11-18 at 12:37 from [davidcorne.com](https://davidcorne.com/2012/07/16/finding-primes-part-ii-a-python-implementation/)_

As it is easy to get started I first wrote a prime finding algorithm in Python. I used a very basic algorithm for this. I store a list of prime numbers, and I check the numbers less than the square root of the possible prime, if any are a factor of the number I'm checking then it's a composite otherwise I append it to the list of prime numbers.

The code for this is on my Box account [here](https://www.box.com/s/9d9c31e55203a9f79133).

This way I only check for prime factors and I check the least possible numbers as if there are any factors then some will be less than the square root.

Here is the code for the `_test` function that contains this algorithm:

1112131415161718192021
`def` `_test(``self``, possible_prime):``"""Test if any elements of primes divides possible_prime."""``prime ``=` `True``for` `i ``in` `self``.primes:``if` `(i > math.sqrt(possible_prime)):``break``if` `(possible_prime ``%` `i) ``=``=` `0``:``prime ``=` `False``break``if` `(prime):``self``.primes.append(possible_prime)`

There are two other methods in my `Prime` class; `primes_below(self, limit)` and `primes_number_of(self, limit)`. These are methods to get either all primes below a number or a specific number of primes. Here is the code for both of these:

2324252627282930313233
`def` `primes_below(``self``, limit):``"""Return a list of primes below the input argument."""``i ``=` `self``.primes[``len``(``self``.primes) ``-` `1``]``if` `(i ``=``=` `2``):``i ``+``=` `1``else``:``i ``+``=``2``while` `i <``=` `limit:``self``._test(i)``i ``+``=` `2` `return` `self``.primes`

In this I get the last member of the list of primes and increment either to two or to the next odd number. This is because `self.primes` is initialised to `[2]`. Then I check only odd numbers to cut down on time and use the `_test` function I have described earlier.

The other function runs in much the same way except the loop runs until the length of `self.primes` is equal to `limit`.

If this file is run then it asks what mode you want (looping till you give it a satisfactory answer) then runs the method you wanted and gives you the output. Here is that code:

484950515253545556575859606162636465666768697071727374757677787980818283
`if` `__name__ ``=``=` `"__main__"``:``type` `=` `-``1``while` `(``type` `!``=` `0` `and` `type` `!``=` `1``):``question ``=` `"Do you want number of primes [0]"``question ``+``=` `", primes below a number[1]?\n"``type` `=` `input``(question)``limit ``=` `1``print``("")``if` `(``type` `=``=` `0``):``limit ``=` `input``(``"How many primes do you want?\n"``)``else``:``limit ``=` `input``(``"Primes (inclusivly) below what number?\n"``)``t_start ``=` `time.time()``calculator ``=` `Prime()``if` `(``type` `=``=` `0``):``primes ``=` `calculator.primes_number_of(limit)``end_calc ``=` `time.time()``msg ``=` `"\n"``if` `(limit < ``1000``):``msg ``+``=` `"The first "` `+` `str``(limit) ``+` `" primes are:\n"` `+` `str``(primes) ``+` `"\n"``msg ``+``=` `"The "` `+` `str``(limit) ``+` `"th primes is: "` `+` `str``(primes[``-``1``])``print``(msg)``else``:``if` `(``type` `=``=` `1``):``primes ``=` `calculator.primes_below(limit)``else``:``assert``(``False``)``end_calc ``=` `time.time()``msg ``=` `"\n"``if` `(limit < ``1000``):``msg ``+``=` `"The primes below "` `+` `str``(limit) ``+` `" are:\n"` `+` `str``(primes) ``+` `"\n"``msg ``+``=` `"There are "` `+` `str``(``len``(primes)) ``+` `" primes below "` `+` `str``(limit)``msg ``+``=` `"\nThe largest of which is: "` `+` `str``(primes[``-``1``])``print``(msg)``print``(``"\nCalculation time:"``),``print``(``str``(end_calc``-``t_start))`

You'll notice that when this is run it will return the calculation time. This is because I was interested in a comparison between Python and C++ for this task. The difference in speed (which I will publish in a later post) was such that for large computational tasks I will only use Python for an indication of the result or if it's something I can just run overnight. The next part: C++ and the Sieve of Eratosthenes.

The full code for this is on my Box account [here](https://www.box.com/s/9d9c31e55203a9f79133).
