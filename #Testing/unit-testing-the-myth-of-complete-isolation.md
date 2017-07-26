# Unit Testing: The Myth of Complete Isolation

_Captured: 2017-06-07 at 00:41 from [dzone.com](https://dzone.com/articles/unit-testing-the-myth-of-complete-isolation?edition=304133&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-06)_

### The notion that unit tests should be performed in complete isolation is a myth. We should use isolation to our advantage, wherever it makes our tests more manageable.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Time and time again, when people talk about unit testing, they mention the fragility of unit tests as some inherent disadvantage of the technique. I disagree. I believe this is just bad unit testing and that the people who hold and spread such opinions are simply victims of what I call _The Myth of Complete Isolation_.

## Fragile Unit Tests

Whether these people believe in it or they are just copy-pasting through their programming career, most of those who experience the pains of fragile unit tests practice excessive isolation of their units under test. They do that by mocking out any single thing their object might be cooperating with.

Let's consider an imaginary `Order` class:
    
    
                    .map(item -> item.getPrice().multiply(item.getQuantity()))

If we were to test this class in the mock-everything style, it would look somewhat like this:
    
    
            Order order = new Order(asList(item1, item2));
    
    
            assertEquals(BigDecimal.valueOf(26), order.getTotalPrice());
    
    
            when(item.getQuantity()).thenReturn(BigDecimal.valueOf(quantity));

Of course, I made the example as small as possible while still making the point, so I don't waste your valuable time. In reality, these mocking tests usually look much worse than that and contain ridiculous practices like verifying a number of interactions with every single method (sic!).

Now, with code like the one above, if the communication between `Order` and `OrderItem` changed for whatever reason, I would have to change every single test related to them. Just consider this simple, obvious refactoring that should be screaming right at your face from the very first code example:

If I did this change and my test looked like the one above, then BOOM!, my test has failed with a `NullPointerException` in the `BigDecimal` class. Pretty fragile, isn't it?

I see at least two arguments why it's a very, very bad thing. One is that correcting the tests every single time we change a method's signature is annoying. The other one is that the test suite is supposed to check if I'm not breaking anything, while, instead, it stops working every single change I make!

## The Myth of Complete Isolation

I believe that this style of writing mock-everything unit tests is a result of a giant misunderstanding. Unit tests, as the name suggests, are supposed to test individual software units, which can be individual classes, whole [aggregates](http://tidyjava.com/aggregate-pattern/), or whatever else fits. Since we're only interested in the proper behavior of our unit, we should isolate external dependencies such as databases, remote systems, etc. Hence, we say that unit tests are performed in isolation.

Unfortunately, when most people first brain-parse the phrase "unit tests are performed in isolation," they understand it as "complete isolation," i.e. we should isolate the unit from EVERYTHING. Also unfortunately, modern mocking tools are powerful enough to mock anything, including static methods and final classes. Make a combo of these two facts and you have a recipe for fragile unit tests.

This is not to say that isolation itself is bad. On the contrary, I think that the general idea of testing smaller pieces exhaustively to reduce the complexity of testing bigger ones is worthwhile. The actual problem here is coupling between the test code and the production code. The more your tests know about the inner details of your production code, the more these two are coupled together, and so the bigger the chance that changing the latter will break the former.

This brings me to the final point of this section. **The notion that unit tests should be performed in complete isolation is a myth. We should use isolation to our advantage, wherever it makes our tests more manageable. At the same time, we should take coupling into account and limit the isolation in places where the pains are bigger than the gains.** It's a trade-off, as almost any programming decision.

## Robust Unit Testing

Coming back to our example, we could make our `Order` class's test better by giving up a little isolation and using real instances of the `OrderItem` class. It's just a simple change in the way order items are created, while the rest of the test stays the same:
    
    
            Order order = new Order(asList(item1, item2));
    
    
            assertEquals(BigDecimal.valueOf(26), order.getTotalPrice());
    
    
            return new OrderItem(BigDecimal.valueOf(price), BigDecimal.valueOf(quantity));

Obviously, this example is pretty naive and the code is far from what you should really write in a real project. If you start to use more real objects instead of test doubles, your tests are going to become more robust, but you will experience some new problems e.g. how to instantiate the objects for test purposes. You're not going to copy and paste methods like `orderItem` all around the project, are you?

Of course, it ain't rocket science. There are simple solutions such as static factory methods and patterns like [ObjectMother](https://martinfowler.com/bliki/ObjectMother.html) or [Test Data Builder](http://natpryce.com/articles/000714.html) to help us deal with this problem and many others that can appear. In the end, it won't be as easy to write as bashing mocks everywhere, but it will be worthwhile.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
