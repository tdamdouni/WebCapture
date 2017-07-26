# Java Math.random Examples

_Captured: 2017-03-10 at 19:27 from [dzone.com](https://dzone.com/articles/java-mathrandom-examples?edition=278882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-10)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

Let's learn how to generate some random numbers in Java. Random numbers are needed for various purposes; maybe you want to generate a password or a session identifier. Whatever the purpose may be, there are a number of issues to be aware of when generating a random number.

## Using Math.random()

The most common way of generating a random double number in Java is to use _[Math.random()](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#random--)_. Each invocation of this method returns a random number. The following code generates 10 random numbers and prints them.

This is about as simple as it gets for generating random numbers. Issues with this method include:

  1. There is no way to specify a seed for the generator. It is picked automatically for you.
  2. _Math.random()_ creates an instance of _[Random_ ](https://docs.oracle.com/javase/8/docs/api/java/util/Random.html)for the actual generation. The instance of _Random_ created by this method is synchronized for use with multiple threads. So while this method can safely be used by multiple threads, you might want to employ other methods to reduce contention.

## Employ the Random Class

You could also directly create and use an instance of _[Random](https://docs.oracle.com/javase/8/docs/api/java/util/Random.html)_. That way, you have more control over the seed, and also generate far more than just random double numbers.

The following code initializes an instance of _Random_ and uses it to generate 10 integers.
    
    
    for (int i = 0 ; i < 10 ; i++) {

## Specifying the Seed

To specify a particular seed, use the appropriate constructor as follows:

Of course, since this is a Pseudo Random Number Generator (PRNG), specifying the same seed results in the same sequence of random numbers being generated. You can verify the fact by specifying a known seed and running the code again.
    
    
    for (int i = 0 ; i < 10 ; i++) {

And that determinism is why when these random numbers are used in secure applications (say generating a password), it is important to "hide" the seed. If someone else were to obtain the same seed, the same sequence can be generated again.

## Multi-Threaded Applications

While the same instance of _Random_ can be used by different threads (since it is thread-safe), it might be better to use another class more appropriate for the purpose. The _[ThreadLocalRandom](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/ThreadLocalRandom.html)_ is a direct subclass of _Random_ and does not have the contention problems of a plain _Random_ instance.

Use the instance of _ThreadLocalRandom_ in each thread as follows:

The instance of _ThreadLocalRandom_ is initialized with a random seed the first time in each thread. To initialize with a cryptographically secure random seed, set the system property `java.util.secureRandomSeed`" to `true`.

## Cryptographic Security

Some applications require cryptographic level of security in the random number generation. What this means is that the generator must pass tests outlined in section 4.9.1 of [this document](http://csrc.nist.gov/publications/fips/fips140-2/fips1402.pdf). You can generate cryptographically secure random numbers using the class _[SecureRandom](https://docs.oracle.com/javase/8/docs/api/java/security/SecureRandom.html)_.

Implementations of the _SecureRandom_ class might generate pseudo random numbers; this implementation uses a deterministic algorithm (or formula) to produce pseudo random numbers. Some implementations may produce true random numbers while others might use a combination of the two.

Running the following code two times on my machine produced the output shown. Even when the generator is being initialized with a known seed, it produces different sequences. Does that mean the sequence is truly random? The answer lies in how the RNG is initialized. _SecureRandom_ combines the user-specified seed with some random bits from the system. This results in a different sequence even when the seed is set to a known value. _Random_, on the other hand, just replaces the seed with the user specified value.

## Random Integers in a Specific Range

Generating random integers in a specific range is a frequent requirement. Here's the easiest way to do it:

The above is good for multi-threaded access. However, it is not suitable when you need to be able to seed the generator. For that case:
    
    
    int value = random.nextInt(max - min) + min;

Using _Math.random()_:

What if you want to generate a random string, say for a password or a session identifier? You can use _[BigInteger_ ](https://docs.oracle.com/javase/8/docs/api/java/math/BigInteger.html)as shown below. Use _Random_ when you don't need cryptographic level security; this will generate a known sequence with a known seed.
    
    
    BigInteger bi = new BigInteger(100, random);

When you need cryptographic security, use _SecureRandom_.

When you run the above code a second time with the same values of seed (and radix), here is what you get. The string is different with _SecureRandom_.

Let's review.

We learned how to generate random numbers in Java. Simple methods include using Math.random(). More control is offered by java.util.Random, whereas cryptographically secure random numbers can be generated using SecureRandom. For multi-threaded PRNG, we have ThreadLocalRandom class. Finally, we learned how to generate random strings using BigInteger.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).
