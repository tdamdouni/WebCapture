# Mathematicians Discover Prime Conspiracy

_Captured: 2016-03-20 at 12:48 from [www.quantamagazine.org](https://www.quantamagazine.org/20160313-mathematicians-discover-prime-conspiracy/)_

![](https://www.quantamagazine.org/wp-content/plugins/magic-fields-2/thirdparty/phpthumb/phpThumb.php?src=/wp-content/uploads/2016/03/Primes_1K.jpg&w=996&h=581&zc=C)

> _Zim + Teemo for Quanta Magazine_

Two mathematicians have uncovered a simple, previously unnoticed property of prime numbers -- those numbers that are divisible only by 1 and themselves. Prime numbers, it seems, have decided preferences about the final digits of the primes that immediately follow them.

Among the first billion prime numbers, for instance, a prime ending in 9 is almost 65 percent more likely to be followed by a prime ending in 1 than another prime ending in 9. In a [paper posted online today](http://arxiv.org/abs/1603.03720), [Kannan Soundararajan](http://math.stanford.edu/~ksound/) and [Robert Lemke Oliver](http://web.stanford.edu/~rjlo/) of Stanford University present both numerical and theoretical evidence that prime numbers repel other would-be primes that end in the same digit, and have varied predilections for being followed by primes ending in the other possible final digits.

"We've been studying primes for a long time, and no one spotted this before," said [Andrew Granville](http://www.dms.umontreal.ca/~andrew/), a number theorist at the University of Montreal and University College London. "It's crazy."

The discovery is the exact opposite of what most mathematicians would have predicted, said [Ken Ono](http://www.mathcs.emory.edu/~ono/), a number theorist at Emory University in Atlanta. When he first heard the news, he said, "I was floored. I thought, 'For sure, your program's not working.'"

This conspiracy among prime numbers seems, at first glance, to violate a longstanding assumption in number theory: that prime numbers behave much like random numbers. Most mathematicians would have assumed, Granville and Ono agreed, that a prime should have an equal chance of being followed by a prime ending in 1, 3, 7 or 9 (the four possible endings for all prime numbers except 2 and 5).

"I can't believe anyone in the world would have guessed this," Granville said. Even after having seen Lemke Oliver and Soundararajan's analysis of their phenomenon, he said, "it still seems like a strange thing."

Yet the pair's work doesn't upend the notion that primes behave randomly so much as point to how subtle their particular mix of randomness and order is. "Can we redefine what 'random' means in this context so that once again, [this phenomenon] looks like it might be random?" Soundararajan said. "That's what we think we've done."

**Prime Preferences **

Soundararajan was drawn to study consecutive primes after hearing a lecture at Stanford by the mathematician [Tadashi Tokieda](https://www.dpmms.cam.ac.uk/~tokieda/), of the University of Cambridge, in which he mentioned a counterintuitive property of coin-tossing: If Alice tosses a coin until she sees a head followed by a tail, and Bob tosses a coin until he sees two heads in a row, then on average, Alice will require four tosses while Bob will require six tosses (try this at home!), even though head-tail and head-head have an equal chance of appearing after two coin tosses.

![Waheeda Khalfan](https://www.quantamagazine.org/wp-content/uploads/2016/03/PrimesResearchers.jpg)

> _Kannan Soundararajan, left, and Robert Lemke Oliver of Stanford University in February._

Soundararajan wondered if similarly strange phenomena appear in other contexts. Since he has studied the primes for decades, he turned to them -- and found something even stranger than he had bargained for. Looking at prime numbers written in base 3 -- in which roughly half the primes end in 1 and half end in 2 -- he found that among primes smaller than 1,000, a prime ending in 1 is more than twice as likely to be followed by a prime ending in 2 than by another prime ending in 1. Likewise, a prime ending in 2 prefers to be followed a prime ending in 1.

Soundararajan showed his findings to postdoctoral researcher Lemke Oliver, who was shocked. He immediately wrote a program that searched much farther out along the number line -- through the first 400 billion primes. Lemke Oliver again found that primes seem to avoid being followed by another prime with the same final digit. The primes "really hate to repeat themselves," Lemke Oliver said.

Lemke Oliver and Soundararajan discovered that this sort of bias in the final digits of consecutive primes holds not just in base 3, but also in base 10 and several other bases; they conjecture that it's true in every base. The biases that they found appear to even out, little by little, as you go farther along the number line -- but they do so at a snail's pace. "It's the rate at which they even out which is surprising to me," said [James Maynard](http://www.magd.ox.ac.uk/member-of-staff/james-maynard/), a number theorist at the University of Oxford. When Soundararajan first told Maynard what the pair had discovered, "I only half believed him," Maynard said. "As soon as I went back to my office, I ran a numerical experiment to check this myself."

Lemke Oliver and Soundararajan's first guess for why this bias occurs was a simple one: Maybe a prime ending in 3, say, is more likely to be followed by a prime ending in 7, 9 or 1 merely because it encounters numbers with those endings before it reaches another number ending in 3. For example, 43 is followed by 47, 49 and 51 before it hits 53, and one of those numbers, 47, is prime.

But the pair of mathematicians soon realized that this potential explanation couldn't account for the magnitude of the biases they found. Nor could it explain why, as the pair found, primes ending in 3 seem to like being followed by primes ending in 9 more than 1 or 7. To explain these and other preferences, Lemke Oliver and Soundararajan had to delve into the deepest model mathematicians have for random behavior in the primes.

**Random Primes**

Prime numbers, of course, are not really random at all -- they are completely determined. Yet in many respects, they seem to behave like a list of random numbers, governed by just one overarching rule: The approximate density of primes near any number is inversely proportional to how many digits the number has.

In 1936, Swedish mathematician Harald Cramer [explored this idea](http://matwbn.icm.edu.pl/ksiazki/aa/aa2/aa212.pdf) using an elementary model for generating random prime-like numbers: At every whole number, flip a weighted coin -- weighted by the prime density near that number -- to decide whether to include that number in your list of random "primes." Cramer showed that this coin-tossing model does an excellent job of predicting certain features of the real primes, such as how many to expect between two consecutive perfect squares.

Despite its predictive power, Cramer's model is a vast oversimplification. For instance, even numbers have as good a chance of being chosen as odd numbers, whereas real primes are never even, apart from the number 2. Over the years, mathematicians have developed refinements of Cramer's model that, for instance, bar even numbers and numbers divisible by 3, 5, and other small primes.

These simple coin-tossing models tend to be very useful rules of thumb about how prime numbers behave. They accurately predict, among other things, that prime numbers shouldn't care what their final digit is -- and indeed, primes ending in 1, 3, 7 and 9 occur with roughly equal frequency.

Yet similar logic seems to suggest that primes shouldn't care what digit the prime after them ends in. It was probably mathematicians' overreliance on the simple coin-tossing heuristics that made them miss the biases in consecutive primes for so long, Granville said. "It's easy to take too much for granted -- to assume that your first guess is true."

The primes' preferences about the final digits of the primes that follow them can be explained, Soundararajan and Lemke Oliver found, using a much more refined model of randomness in primes, something called the prime k-tuples conjecture. [Originally stated](http://link.springer.com/article/10.1007%2FBF02403921#page-1) by mathematicians G. H. Hardy and J. E. Littlewood in 1923, the conjecture provides precise estimates of how often every possible constellation of primes with a given spacing pattern will appear. A wealth of numerical evidence supports the conjecture, but so far a proof has eluded mathematicians.

The prime k-tuples conjecture subsumes many of the most central open problems in prime numbers, such as the [twin primes conjecture](https://www.quantamagazine.org/tag/twin-primes-conjecture/), which posits that there are infinitely many pairs of primes -- such as 17 and 19 -- that are only two apart. Most mathematicians believe the twin primes conjecture not so much because they keep finding more twin primes, Maynard said, but because the number of twin primes they've found fits so neatly with what the prime k-tuples conjecture predicts.

In a similar way, Soundararajan and Lemke Oliver have found that the biases they uncovered in consecutive primes come very close to what the prime k-tuples conjecture predicts. In other words, the most sophisticated conjecture mathematicians have about randomness in primes forces the primes to display strong biases. "I have to rethink how I teach my class in analytic number theory now," Ono said.

At this early stage, mathematicians say, it's hard to know whether these biases are isolated peculiarities, or whether they have deep connections to other mathematical structures in the primes or elsewhere. Ono predicts, however, that mathematicians will immediately start looking for similar biases in related contexts, such as prime polynomials -- fundamental objects in number theory that can't be factored into simpler polynomials.

And the finding will make mathematicians look at the primes themselves with fresh eyes, Granville said. "You could wonder, what else have we missed about the primes?"

![twinprimes_maynard_thumb](https://www.quantamagazine.org/wp-content/uploads/2013/11/twinprimes_maynard_thumb.jpg)

> _[Together and Alone, Closing the Prime Gap](https://www.quantamagazine.org/20131119-together-and-alone-closing-the-prime-gap/)_

![Prime Gaps](https://www.quantamagazine.org/wp-content/uploads/2014/12/PrimeFeatured.jpg)

> _[Prime Gap Grows After Decades-Long Lull](https://www.quantamagazine.org/20141210-prime-gap-grows-after-decades-long-lull/)_

![ZhangFt](https://www.quantamagazine.org/wp-content/uploads/2015/04/ZhangFt.jpg)

> _[After Prime Proof, an Unlikely Star Rises](https://www.quantamagazine.org/20150402-prime-proof-zhang-interview/)_
