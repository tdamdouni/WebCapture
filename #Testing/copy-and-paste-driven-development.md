# Copy-and-Paste-Driven Development

_Captured: 2017-02-17 at 15:28 from [dzone.com](https://dzone.com/articles/copy-and-paste-driven-development?oid=twitter&utm_content=bufferf225b&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Software development is rife with copy and paste. We all resort to copy-and-paste coding sometimes. We know we probably shouldn't, but we do it anyway. It's the industry's dirty little secret: we mainly just copy and paste code from the internet or from somewhere else in the code base then bash it till it works.

![copy-paste-nailedit](https://activelylazy.files.wordpress.com/2017/02/copy-paste-nailedit.jpg)

But maybe, just maybe, the fact that we all rely on this from time to time should be telling us something.

## The Good

Sometimes, copy-and-paste coding can be a good thing. A while ago, I was pairing with someone where we did what I would call search-and-replace coding. I love to code golf. In tools like Eclipse, Intellij or Resharper, there is always an optimal way to make each change, letting the tools do as much of the typing as possible. So, it was with fascination recently that a colleague showed me an interesting code golf using search and replace.

The change was around extending an existing class with a load of new fields. We had a basic class with a couple of sample fields and a test that verified something simple about the class -- say, that it could be serialized to JSON successfully. We needed to add a boatload of new fields to the class (don't ask). This involved five separate tasks which, at a macro level, had a lot in common:

  1. Adding each field.
  2. Initializing each field in the constructor.
  3. Modifying the test to setup sample values for each field.
  4. Modifying the test to pass the sample value for each field to the constructor.
  5. Writing an assert that each field had successfully serialized and deserialized.

My colleague demonstrated that we could write the list of fields once, then copy, paste, search, and replace. We'd have a list of parameters for the constructor. By carefully crafting the search term and a suitable replacement term, you can do some limited meta-programming, taking the list of fields and transforming it into the actual lines of code you need in each instance. The list of fields replaced one way gives you a list of parameters to the constructor. With a different replacement, you get the field declarations in the test. With another replacement, you get assert statements.

I found this a very interesting way to write software. It definitely optimized the number of key presses required to type the code in. The long, boring list of field names only had to be typed in once; after that, we merely (carefully) crafted a search-and-replace regex to do the lifting for us. However, it demonstrates an underlying truth. We had five separate changes to make, which accepted a parameter. If we could have actually meta-programmed this, we would have passed in the list of fields to some meta-programming code which would output the desired lines of code.

While it's very clever that we could use search-and-replace meta-programming for this, it feels like the tools are lacking somehow.

## The Bad

Everyone copies code from StackOverflow from time to time. Hopefully, you do it sensibly, using it as a starting point for your own production code -- working through what you've just pasted in to understand it, experimenting with it, modifying it, making it fit for your purpose rather than just blindly copy-and-pasting random code from the internet. I mean, who'd just [randomly run code from the internet](https://gkoberger.github.io/stacksort/)?

StackOverflow is great. It's an amazing resource for programmers. While learning WPF, I got the sense that as a technology, it couldn't have taken off without something like StackOverflow. The technology is so opaque, so hard to learn. It took me many, many months of copy-and-pasting XAML from StackOverflow until I started to really understand how it worked. This is a technology that is not trivial to understand. Without being able to just copy and paste code from the internet, the technology would take a lot longer to learn.

But often, we're lazy. We try it. It works. Woohoo! Next problem. I've written before about [voodoo programming](https://blog.activelylazy.co.uk/2012/10/09/knowledge-vs-superstition/), but the problem is that it's easy to think you've understood what code is doing. If you didn't actually have to invent those lines, to reason through to them...maybe you don't understand. Maybe you only think you know what the code's doing. Maybe there's some horrific bug you're not aware of yet.

## The Ugly

Almost every time I've seen TDD done at any scale, when it comes to writing a new test, the first question to ask is, "Which existing test is this most like?" Yup, in other words, "Where can I go copy and paste?" I'm so lazy, I don't want to have to invent a whole test setup on my own. I'll just borrow somebody else's homework. We've all done it. It seems to be an unwritten rule of TDD. By the time you're on to the third or fourth test in a given file, I guarantee the temptation to just copy and paste to make the fifth test is incredibly strong.

The trouble with this is that all sorts of weird test artifacts get copied forwards. You start off with a simple test with some simple setup -- say, an empty bank account. Then, to test non-zero balance, you need an account with a transaction. Then, to test balance summing, you need an account with two transactions.

Each test so far is building on the last, so you've just copy-and-pasted the previous one as a starting point.

Test 4 is inserting a new transaction, so you just copy the third test (with two existing transactions that are unnecessary for this test). Test 5 is that a withdrawal can't go below zero, so you copy and paste the previous test and set the amount to be a large negative value. Test 6 is an overdraft test, so you copy and paste the previous test but change the account setup to include an overdraft so the balance can go negative.

By the time you copy and paste Test 7, your starting point is an account with an overdraft, with two transactions where a third transaction is added. Test 7 is about adding a standing order. None of this noise is necessary.

This might seem a ridiculous example, but I see this time and again in real code. Sometimes, it's not even me that's done it. This noise accumulates as you read down a test file. The tests at the bottom have all sorts of weird artifacts that were only relevant to one test half way up the file. It means fixing tests and changing behaviors becomes a real problem. If I change, say, how overdrafts are defined in my example above - I might have half a dozen tests to change, only one of which even mentions overdrafts. However, they've inherited that setup because the tests were just copy-and-pasted around. Not only does this make tests hard to read and understand -- it makes them hard to maintain.

We all do it. It seems a pretty accepted part of how TDD happens in the wild -- and yet, it clearly isn't right. With discipline, we can keep our tests clean. Yes, when we're all being conscientious developers we start writing our tests from scratch each time. But most of the time we're busy or lazy or whatever.

## Conclusion

What do these three things have in common besides copy-and-paste? In each example, we're using copy-and-paste to save time, to find the most efficient path through the work we're doing. Nobody is doing it out of malice or stupidity. Laziness? Almost certainly -- but the good kind. The kind of laziness that encourages elegant solutions.

However, copy-and-paste isn't an elegant solution. It's a crappy solution to a more fundamental problem: the fact that our tools are deficient. Really, what we're working around is the fact that our tools don't let us express what we really want.

What if we could write our tests in a higher level language? "A test with a bank account with two transactions." Sure, there are internal and external DSLs you can use to do this, but typically, the cost in setting up the DSL isn't worth the hassle for unit tests. It would completely ruin the flow of TDD. Does that just mean we haven't found a good way of doing it yet? Is there a way we could more fluidly express the intent of the test, filling in the gaps as we go?

Instead of copy-and-pasting code from the internet, could our tools get smarter? Could we take some of the amazing machine learning stuff that's going on and apply it to software development? I tried playing with an [IntelliJ plugin](https://plugins.jetbrains.com/idea/plugin/9203-ai-predictive-coding) recently that promises just that. Unfortunately, it's pretty buggy at the moment and doesn't really work, but the idea is incredibly attractive. I like the idea of being able to express intent instead of mindlessly typing in the nuts and bolts.

Finally, instead of doing search-and-replace coding, wouldn't it be great if we could actually meta-program? Wouldn't it be great if we could actually write code that would write code for us -- not just code generators, but something that can generate small sections of code? I had a very limited go at this some time ago with [rescripter](https://github.com/activelylazy/Rescripter), but it turns out it's very hard to write a decent meta-programming tool that anyone except the author can understand. However, I think the idea still has merit. Too often, I find cases where I can describe the intent of my change very succinctly, but implementing it will involve far more typing than I'd like.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).

### Like This Article? Read More From DZone
