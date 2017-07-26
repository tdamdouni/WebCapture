# Test well, sleep well

_Captured: 2016-11-19 at 09:48 from [medium.com](https://medium.com/@piotr.slesarew/test-well-sleep-well-f4ba89b0a8cc?source=userActivityShare-c79006fee040-1479545310)_

> Systems that aren't testable aren't verifiable. Arguably, a system that cannot be verified should never be deployed. -- **Robert C. Martin**

Sleep is one of the most important and healthiest things you can do for your body. It is said that good sleepers have better concentration and productivity, isn't that what we are all aiming for? I have been producing code for almost ten years now and I have seen and written tons of smelly, spaghetti code. Testing allows me to sleep well at night and that is why I want to share my thoughts and practices about it.

#### Start writing tests

Writing tests should be an integral part of our daily duties as you consider yourself professional software engineer. If this sounds new to you, please **start testing your code** **from today**. Trust me. I was in your boots and I know how hard is to kick off but in fact, it is easier than you think. In the beginning, you will feel a little bit disappointed because it will perturb your productivity but I can assure you that "test investment" pays off sooner than later. In addition, over time you will become more confident and a faster engineer in test.

#### Treat tests like your codebase

Almost all software engineers I have met know who is Robert C. Martin. He is a clean code evangelist and the author of amazing books and articles that changed our way of thinking about software development. Nowadays there is a lot of buzz about code refactoring, code readability, and code conciseness so why are you not applying this knowledge to your tests? People tend to draw a strong line between code and tests but for me, there is no difference and I see them as siblings. That is why **I treat my tests like I treat my codebase **caring about readability, conciseness, and usefulness. DRY and SOLID testing!

#### Document code through tests

Documentation is always a big pain because of hardness in maintaining it, and additionally, it is often outdated. In my opinion, the code has to be self-documented by being clear, simple, and having a full suite of tests. I always try to make my **tests** as **readable** as it is possible **to provide the best documentation** **for my code**. It is a hidden benefit of testing that every software engineer should be aware of.

#### Make them fail

If there are no failing tests every now and again, it is a sign that you are not doing them right. It is a very good practice to write tests first but this is not what I mean. **Fail them to check** if **your** setup works as incorrect mocking can make your **assertions** **and verifications** weak.

#### Happy path is not enough

The **worst thing** is the code covered with **"happy path"** tests as they give an illusory safety. Designing robust and reliable test cases is the hardest and the most satisfying part of my daily duties. To make it more interesting take your craft to extreme and use test driven development and pair program with your colleagues.

#### Do not change code to write tests

This point is crucial in conjunction with architecture and security so it should be as important as your date of birth. Think twice while breaking an encapsulation to test your code because **the leaking architecture will slow down your work in the future**. Actually, this kind of situations is always pointing on bad design. I made this mistake and in most cases, I ended up rewriting components from the scratch.

#### Be careful with test doubles

Simply do not misuse test doubles as they can lead to non-obvious **implementation leak**. When implementation details in your production code change, you will have to refactor your tests to reflect these changes. Moreover, tests will become **less readable and maintainable** because of huge setups.

#### Review test **cases**

Code review is the best tool to examine pre-production code and find bugs in it. Lately, I was interviewing a couple of engineers and I noticed that their code reviewing skills were terribly neglected. Most of them do not even try to open a test class to check what is inside, scary right?

Personally, I love to **review test cases** and I always investigate them first. I use built-in code coverage tool in IntelliJ to check "Hits". Too many or too little of them can tell you if the code is over or under covered.

#### Test picked up use cases

Reading and understanding someone else's code is our daily routine. Do you know that feeling when you have to change the non-tested code? During it you research repository, talk to other programmers, make notes and then you apply changes. There is one step missing in that chain. Before changing the code you should **write the test to every single use case that you picked up**. Also, you can use "characterization testing" against an existing code to understand the logic behind it.

#### Try different frameworks

It is not just that software engineers fear new tools, though they undoubtedly do. It is also that they truly believe that when you have been doing something a particular way for some time, it must be the best way to do it. I notice a strong tendency in Java world to use JUnit as a main tool to write unit tests despite the fact that it has a lot of pitfalls. I use Spock in exchange for JUnit to apply robust Groovy syntax to my tests and it works like a charm. There are many **other**, great **frameworks** like TestNG and the latest Spek that **can** **help you to achieve conciseness and readability**.

#### Be pragmatic

With growing skills hunger accelerates rapidly, and to feed it you try to test everything. Remember that the more tests you write, the more code you have to maintain. **Being pragmatic will stop you** **from testing boilerplate** code such as getters, setters, constructors etc.

Summing up, I hope that you have found some helpful bits of advice or at least I inspired you enough to start working on your own best testing practices.

#### Article Notes

_If this was interesting to you, please do hit the heart button ❤ or __[let me know on Twitter_](https://twitter.com/SliskiCode)_._
