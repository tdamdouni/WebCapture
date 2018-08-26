# The Deadly Sins of Unit Testing — Part 2

_Captured: 2018-07-06 at 19:30 from [dzone.com](https://dzone.com/articles/the-deadly-sins-of-unit-testing-part-2?edition=385206&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-07-06)_

Container Monitoring and Management eBook: [Read about the new realities of containerization.](https://dzone.com/go?i=291440&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fcontainer-monitoring-and-management.html%3Fcid%3DNA-DSP-APM-AEJ-000195-00001663-000000492%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_eb1-container-monitoring-mgmt-articlepreroll%26mrm%3D)

![](https://www.typemock.com/wp-content/uploads/2018/06/part2.jpg)

## Unit Testing Sloth

Have you watched the movie Zootopia? If so, then you definitely remember the sloths who work at the DMV. And what are their defining characteristics? Well, this is easy to answer: they're slow. Like, reaaaaally slow. Amazingly...incredibly...sssssslooooow.

So it makes a lot of sense to talk about unit testing speed under this particular deadly sin. This shouldn't come as a surprise to anyone-your tests should be fast. In fact, they should be amazingly-incredibly-spectacularly-super-duper-ultra-breathtakingly fast.

What causes unit testing sloth? More often than not, it's a reliance on external dependencies that are slow by nature, such as the database. In this case, the solution is probably to [mock those dependencies out](https://www.typemock.com/mocking-frameworks-is-it-worth-paying-for-them/).

Other times, the slowness might be caused by a legitimate performance problem, which will need to be properly benchmarked and fixed.

## Unit Testing Envy

We finally get to another term that's been used as a metaphor in the software world before. But while "greedy algorithms" didn't carry any moral judgments, we can't say the same about [feature envy](https://refactoring.guru/smells/feature-envy). That's because feature envy is a [code smell](https://en.wikipedia.org/wiki/Code_smell): a property of a piece of code that's a sign that something might be wrong with the code itself.

If you browse around for a definition of feature envy, you might end up on [this post by Jeff Atwood, in which he talks about several code smells](https://blog.codinghorror.com/code-smells/). Here's his definition of feature envy:

> Methods that make extensive use of another class may belong in another class. Consider moving this method to the class it is so envious of.

A class envies another a class when it _wants to be that class_. It's generally considered a case of not enough encapsulation.

Similarly, we can say a unit test envies another when it contains assertions that should belong in the other test case. A somewhat easy way to test this is to compare the assertions in the test with its name. Do they fit? Do they look like they belong together? If the answer is no, maybe you're facing a case of unit testing envy.

## Unit Testing Lust

I'll admit that this one gave me a little bit of trouble, as far as finding a good match to the actual capital sin. I thought about some things that, although plausible, might be a little too much of a stretch. Fortunately, the accumulated software wisdom came to my aid again. As was the case with envy, there's actually a code smell that I believe we can faithfully repurpose into a unit testing capital sin.

I'm talking about the **inappropriate intimacy** code smell. Let's see [Jeff Atwood's definition](https://blog.codinghorror.com/code-smells/):

> Watch out for classes that spend too much time together, or classes that interface in inappropriate ways. Classes should know as little as possible about each other.

I think you'll agree with me that the advice of "Classes should know as little as possible about each other" is very sensible. It's similar to feature envy in that it suggests a lack of proper encapsulation. What would a lustful unit test look like, though? And how does it relate to the inappropriate intimacy code smell?

Unit testing lust manifests itself when a test invades the intimacy of the SUT. In other words, the test shouldn't care about the internal, private details of the method it's testing. These details belong to the SUT and should be kept private. Tests that not only care about but also rely upon the internal details of the class it's testing are bound to cause problems.

Read [Part 1 ](https://dzone.com/articles/the-deadly-sins-of-unit-testing-part-1)here.

Take the Chaos Out of Container Monitoring. [View the webcast on-demand!](https://dzone.com/go?i=291441&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcompany%2Fevents%2Fwebcasts%2Fapplication-performance-monitoring-and-management.html%3Fcommid%3D286663%26cid%3DNA-DSP-APM-AEJ-000195-00001663-000000493%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_webcast1-apm-taming-chaos-articlepostroll%26mrm%3D)
