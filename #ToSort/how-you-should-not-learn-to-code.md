# How You Should (Not) Learn to Code

_Captured: 2017-03-29 at 20:13 from [dzone.com](https://dzone.com/articles/how-you-should-not-learn-to-code?edition=286946&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-29)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

In order to achieve productivity and robustness of our applications, we are constantly introducing new coding practices, new tools, new frameworks. Consequently, with every new introduction of additional complexity, we are permanently raising a bar for newcomers in programming business.

Through time, the process of learning is getting longer, the required amount of effort increases, and we are failing to provide beginners with the tools and/or methods for getting from the point of not knowing anything to knowing something.

In that learning process, they are often left alone to choose any method to go through that path by themselves. Very often, they choose wrong.

When I was starting with development (around 16 years ago) there were no such complex tools and technologies, there were no frameworks - or at least, it was not as widespread as it is now. You could get and do this job, very successfully, without knowledge of, for example, any programming framework. In general, if you could write down a meaningful "if-then-else" statement, you were good to go. Especially if you were a PHP developer if you knew the meaning of PHP acronym, you were just fine, the rest could be handled along the way.

Nowadays, you ought to know at least one backend framework, some knowledge of JavaScript is required as well as some popular JS libraries like jQuery, some CSS/LESS/SCSS is a plus, HTML of course, and there is no reason to even mention SQL. But it does not stop there, you have to know how to work in at least one testing framework, store your code in some VCS system (preferably git), manage your tasks in some software dedicated for that task (like JIRA), and you should be familiar with deployment tools as well as with managing runtime environments (like Docker).

Besides tools, you should be familiar with good coding standards and practices, static code analysis, design patterns, etc.

And those are for entry level positions! And that list just getting bigger every day.

## Learning by "Writing the Written" Method - The Wrong Way

Lately, I have been involved in arguments with a few developers who tried to increase their level of understanding of a few of the most complex concepts in OOP - MVC pattern and MVC frameworks and ORM and Active record patterns. Their approach was to write their own small frameworks/libraries, hoping that by doing so they would understand the basic concepts and ideas behind them.

I have fought tooth-and-nail trying to discourage somebody in doing so, claiming that that is erroneously directed effort. My arguments were based on several paradigms and theories:

#### **The Very Idea Violates DRY (Don't Repeat Yourself) Paradigm.**

The [DRY paradigm](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)) is well known and already explained, so I will not go into further explanation, except, I would like to quote one rather important sentence from a referred article:

> Violations of DRY are typically referred to as WET solutions, which is commonly taken to stand for either "write everything twice", "we enjoy typing" or "waste everyone's time."

#### **Libraries Should Be Written (or at Least Designed) by Experts in the Domain.**

When someone writes a library, that means that he is fully familiar with a problem's domain, its requirements, theoretical and academic basis and achievements in the field, similar and related domains, common pitfalls, other approaches, good and bad practices in solving similar problems - in general, everything about a problem that a library ought to solve. Learners do not possess that knowledge - not even remotely, and therefore, most of the time they will do things the wrong way with extremely low (or no) gains in knowledge.

#### **In Development Lingo - That Learning Method Is an Anti-Pattern**.

In order for something to be declared as an [anti-pattern](https://en.wikipedia.org/wiki/Anti-pattern), at least two criteria have to be satisfied:

  1. The process (and/or structure) can appear as effective and appropriate response to a problem. This typically has more bad consequences than good ones
  2. Another solution exists that is documented, repeatable, and proven to be effective.

Learning by "doing it again" seems, at first glance, like a method that will help you to understand how things work and the motivations and benefits for doing them. If you want to learn how to build a house - take bricks and put them together, right? However, the very fact that it is being redone by someone who lacks expert knowledge about the domain pretty much guarantees that a majority of your effort will go wasted. Surely, from those failed attempts something will be learned along the way, but how efficient is that process of learning?

Take, for example, the Rosetta Stone application for learning foreign languages - it mimics the learning process of a baby/infant which learns words by connecting them with context and objects. It is true that you will learn, at least, the basics of the language with Rosetta Stone. However, its methodology is a major subject of criticism. Simply put - a baby/infant has more time to learn a language (measured in years) and has a slower pace and capacity of memorizing words and language rules in comparison to an adult.

Same goes for learning how to use MVC frameworks or ORMs. You can learn about them by trying to write your own - but there are far more superior methods to achieve that result.

## Learning Through Mentorship

What is the preferable and most productive way? There is no discussion there. You need an expert teacher with all the required knowledge and who will guide you trough everything, helping you with every obstacle. The fact that commercial companies are spending tons of money for various lectures, training sessions, and mentorships for their employees is the very proof of how effective this method is.

There is, however, a major drawback for individual learners - it is not easily affordable and experts are usually not available. They are usually rather busy people, not to mention the difficulties that go along with teaching (especially if it's not your primary job). I mentored previously on a voluntary basis and I do not believe that I would do that again in my life for any amount of money.

## Conventional Learning - Reading/Watching Talks

It is free. There is a lot of things that you can find that are worth reading/watching, and a lot of things can be recommended to you for free to be read/watched. The method by itself is not sufficient, it has to be accompanied with some practical appliance and/or mentorship and/or guidance.

**But let me hit you with some hard facts. **Without a theoretical knowledge/background, any practical appliance, any mentorship, any type and method of learning, is just a waste of time, for both you and others willing to spend time with you in order to improve your skills. I have noticed a desire in every beginner/intermediate to skip that part and go straight to the practical appliance and practical knowledge, hoping that there is some shortcut that will help them graduate to "pro level" in the shortest time possible with the least amount of effort invested.

There are no shortcuts. Everything that you miss will come back to bite you, sooner or later. It is very easy to spot when someone didn't do his homework - didn't read the documentation carefully, or didn't familiarize themselves with a topic/domain.

As a matter of fact, you should exploit this method as much as possible. Read everything that you can get your hands on, watch every video possible (of course, make sure to check the credibility of the author). And don't focus too much on one technology, one programming language - almost everything is portable, transferable and applicable to various technologies and programming language. For example, in order to learn about implementation details for Symfony's ACL security component (PHP framework) which was poorly written when it was published, I had to read Spring's ACL security component documentation (Java framework). In conclusion, read literally every credible source.

## Join an Open Source Community and Get Actively Involved

Lately, I have been promoting this idea a lot. Maybe because I personally believe that the OS community has shaped me a lot. If anyone ever thought of me as a good/fine developer/architect it is because of certain people from the OS world from which I have learned a lot (like Thibault Duplessis, a.k.a [ornicar](https://github.com/ornicar), or Stephane Erard, a.k.a [stephaneerard](https://github.com/stephaneerard)).

It is almost impossible to get the best developer as an in-person mentor, fortunately, because of the open source world and GitHub (or other free source versioning systems), you can get the second best thing: you can learn from the best developers for free.

So, how you can do that?

Well, first thing - you can **read their code** and probe their minds, how do they think, how do they see problems, how they organize their code, files, classes and functions, what are their coding practices and habits, and so on. Personally, I have learned more by reading code rather than writing it.

**Read issues**, open ones as well as closed ones. You will find a lot of arguing there, but a lot of constructive arguing, and you can learn a lot from that. There is always a discussion about usability, coding practices, real problems, technologies, etc. You can observe a clash of opinions and see a lot of stated "pros" and "cons" and learn from them.

**Read the documentation and improve documentation.** Open source libraries often do have poorly written documentation. Even the best ones do miss some chapters or some better explanations of a certain feature. Improve it, submit PR, help others by helping yourself.

**Fix a bug, propose a feature. **There is no better way to get practical knowledge than actually coding, so code something which benefits all of us. There are a lot of bugs, much more than the community can handle, so every effort is appreciated.

**Write a test, improve the test. **Open source libraries suffer from low code coverage. And there is always the possibility of improving tests to cover edge cases. You can easily spot if some line of code lacks a test, and tests are much easier to write then fixing a bug.

### Why Should You Invest Your Time in Open Source Projects?

You will get an opportunity to work with the best developers from around the world, and you will be able to learn from them.

In order to submit a PR, you have to go trough a library, documentation, code, everything you can find that is related - in order to understand it and be able to modify it in a way that creates some benefit.

You should be prepared to argue and to be rejected as well. In the beginning, that will happen, a lot! But that is a good thing, you shouldn't be discouraged, on the contrary - you should be more motivated.

And here is the well-hidden fact: when you submit a PR, you get a free mentorship. Some hot-shot, well-paid developer has to review your code, decline it, and write you a reason for the rejection. And that is pure gold - whether you believe it or not: in my career, I have learned more from my rejected PRs then from accepted ones.

It is a "_quid pro quo_" relationship between you and a reviewer - if you are not a good developer now, you will be better in 6 or 12 months from now, and every code reviewer in open source is aware of that. Not that they don't want to be rude to you now, but they can not, they will need you - you are their free labor in the future and open source libraries are fuelled with free labor.

Eventually, your efforts will pay off, you will return your debt to the open source community, your patches, fixes, and features will get merged, and you will feel like a part of something more important and bigger than yourself (if you don't believe that that is important, I recommend you watch this [video](https://www.youtube.com/watch?v=rrkrvAUbU9Y)).

With those contributions recorded and displayed on your GitHub profile you will get swamped with job offers and exciting opportunities.

It is a "_quid pro quo_" relationship - give in order to receive.

## Work Pro Bono

I often hear a lot of complaints from beginners that they don't have an opportunity to get practical knowledge and to get real-life problems to solve.

Nowadays, everything runs on information and I just refuse to accept that - there are a lot of real life problems to be solved, and a lot more problems than developers.

So, you need a real-life problem to solve in order to get practical experience? Work pro bono! Find an NGO, find poorly funded government institutions and/or organizations, offer them your services. Ask your neighbor who has a small grocery store if he can provide you with sales data so you can write him a reporting tool, or business intelligence tool, or whatever creative application you can find.

If your motivation really is to get practical experience it is really hard to believe that you can not find a problem to solve.

So, I beg you, if you are eager to learn and you have spare time please, don't spend it writing something already written. There are far more superior methods which you can apply to acquire knowledge.

There are no shortcuts, don't look for them. We already did, we are telling you that from our experience, learn from our mistakes.

Your time and effort is precious and can benefit us all, even if you are at the very beginning of your career. We value it, why don't you?

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
