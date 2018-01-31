# The Basics of TDD

_Captured: 2017-01-31 at 23:55 from [dzone.com](https://dzone.com/articles/the-basics-of-tdd?edition=266901&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-31)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

The objectives of test-driven development and unit testing are generally misunderstood. The problem is the word "test." It is much less about testing and much more about the specification of requirements and showing your working -- as in math and the impact it has on design. TDD is much more important than only testing. Robert C. Martin has a good analogy. He likens TDD to double-entry bookkeeping:

> Software is a remarkably sensitive discipline. If you reach into a base of code and you change one bit, you can crash the software. Go into the memory and twiddle one bit at random, and very likely, you will elicit some form of crash. Very, very few systems are that sensitive. You could go out to one of these bridges over here, start taking bolts out, and they probably wouldn't fall. I could pull out a gun and start shooting randomly and I probably wouldn't kill too many people. I might wound a few but -- you know -- you get a bullet in the leg or a lung and you'd probably survive. People are resilient -- they can survive the loss of a leg and so forth. Bridges are resilient -- they survive the loss of components. But software isn't resilient at all. One bit changes and -- BANG! -- it crashes. Very few disciplines are that sensitive.   
  
But there is one other [discipline] that is, and that's accounting. The right mistake at exactly the right time on the right spreadsheet -- that one-digit error can crash the company and send the offenders off to jail. How do accountants deal with that sensitivity? Well, they have disciplines. One of the primary disciplines is dual-entry bookkeeping. Everything is said twice. Every transaction is entered two times -- once on the credit side and once on the debit side. Those two transactions follow separate mathematical pathways until they end up at this wonderful subtraction on the balance sheet that has to yield to zero.   
  
This is what test-driven development is: dual-entry bookkeeping. Everything is said twice -- once on the test side and once on the production code side and everything runs in an execution that yields either a green bar or a red bar just like the zero on the balance sheet. It seems like that's a good practice for us: to [acknowledge and] manage these sensitivities of our discipline. -- [Robert C. Martin](https://archive.is/o/LLhot/unhandled-exceptions.com/blog/index.php/2009/02/15/uncle-bob-tdd-as-double-entry-bookkeeping/comment-page-3/)

The sensitivity of software is a good point to reflect upon. There is little in human experience that is so complex and yet so fragile. Without a strong focus on showing your working, no matter how good you are as a developer, if you omit the tests, your software will be worse than it could have been.

The double-entry bookkeeping analogy only holds up though if you do test first development. If you write your test after the code it is generally not sufficiently independent to provide a valid "separate path" check.

Testing first is the idea that you write the test before you write the code that is being tested. This seems like a bizarre idea to many people at first, but actually, it makes perfect sense.

If you write the test first and run it, you get to see it fail, so you are testing the test.

If you write the test first then you are expressing what you want of your software from the outside in. It leads you to design for behavior and so you have less of a tendency to get lost in irrelevant technicalities.

This is a much more effective design approach than testing after you have written the code, and as a by-product, it leads inevitably to software that is easy to test. You have to be pretty dumb to write a test before you have written the code for an idea that can't be tested!

Finally, there is a virtuous circle here. Software is easy to test when it is modular. It is easy to test when dependencies are externalized and it is easy to test when there is a clear separation of concerns.

Now the software industry is famous for change. However, if there is any idea that has remained constant for literally decades, it is that quality software is modular and has well-defined dependencies and the clear separation of concerns. Sound familiar? This has been how computer science has defined quality since before I started, and that was a very long time ago!

Using TDD as a practice makes you produce higher quality software, not because it is well-tested (though that is a nice by-product) but because it improves the quality of your designs.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
