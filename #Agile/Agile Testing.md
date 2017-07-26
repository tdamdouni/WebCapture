# Agile Testing

_Captured: 2016-07-10 at 22:55 from [www.skankworks.net](https://www.skankworks.net/agile/agile-testing/)_

[March 31, 2015](https://www.skankworks.net/agile/agile-testing/)[IT](https://www.skankworks.net/agile/category/it/), [Project Failure](https://www.skankworks.net/agile/category/project-failure/), [Scrum Master](https://www.skankworks.net/agile/category/roles/scrum/), [SPL](https://www.skankworks.net/agile/category/roles/spl/)[Testing](https://www.skankworks.net/agile/tag/testing/)[alt-f4](https://www.skankworks.net/agile/author/alt-f4/)

As professional software testers, we at the skankworks.net have found ourselves increasingly drawn into what are described as "Agile tester" roles. 

Now, in a tough market a contractor has to take what he or she can get. It's also a part of being a professional to sometimes do a job the way a client wants it done, and to put aside one's own experience of how things should be done. 

If they are not asking for your advice, don't offer it. JFDI. 

**What Is Agile Testing?**

If you envision Agile Testing as being something that involves grooming a backlog of test-cases, assigning story points to test-steps, and sticking post-it notes all over the wall, you'd be wrong. 

Those kind of difficult project-managementy tasks are strictly for devs. Testers wouldn't understand. 

You'll still have to sit in on their meetings, but they will be telling you how it is to be tested. 

Because, on an Agile team that is all they want: A yes man. Somebody to generate log files for them, and somebody to offload their unit testing onto so that they can devote their precious time to the all-important story-point burn-down. 

No matter that unit testing requires a proximity to the code-face that only the developer has. 

In short, Agile Testing is pretty-much the same as anything else that's Agile: It's bullshit. A lackey to do developers' dirty work. 

**Happy-Path Functional Testing**

Agile testing will typically be done against a release build of the software, typically withheld until the end of the sprint. The story-points often require the testing of one or two internal methods that will frequently require a huge amount of effort and preparation to bring the system into a runtime state to perform such testing, and require a great deal of knowledge of programming. 

You might recognise this as functional testing, which it is. But don't go making a fool of yourself by asking for a functional spec. Agile devs write their own specs, and they usually do so after they've written the code. So they are worthless. 

You will need to reliably generate, document, and test a runtime condition that a developer claims to have fixed even though he doesn't know how to reproduce the issue. You will have no documentation to test against, nothing to tell you what the software is actually supposed to do, and what are you supposed to do to test it? Take a guess? Reassure him that everything is going to be ok? You'll be told, "_Just test the happy-path_", what could possibly go wrong? 

He has more important things on his mind: The next story-point, which is what Agile is all about. Most Agile projects tend to have pointed stories with sad endings where it all goes wrong, involving lay-offs, large sums of money wasted, angry customers, and impoverished investors. In a nutshell project failure. 

Put Agile into a safety-critical field, and they can add a couple of story points for defending themselves against medical malpractice, class action suits, and charges of criminal negligence, that last one being measured more in jail time than story points. 

So getting an Agile Tester on the team is vital, in order to have somebody to point your fingers at when it all goes tits-up and the customer pulls the plug. 

**Test Driven Developemt - Testers Driven Out**

Let's face it, developers have never got on with testers. Our job is, specifically, to find defects in their work and to raise issues about it. 

Many customers choose Independent V&V as way of building a wall of separation between the roles, to assure objectivity. 

But this is anathema to Agile. An independent and objective review of their work simply will not do. The product owner, who is also the scrum-master and SPL, can do that herself. 

So they have test-driven development. An amateurish approach to software development which involves ignoring the customer requirements entirely, and simply writing code so that it will pass a set of tests that you defined yourself. 

**Agile Tester Required**

We're seeing more and more of these contracts advertised, and we ignore them now. Don't think this is some reverse-pyschology where we are trying to enhance our own opportunities by driving others out of the market. If you want to apply for one of these contracts and you get it, don't come back here whining that you weren't warned. 

Here's what you'll get.

_Run this code for me and give me the logfiles._  
_I didn't ask you to test that bit, just the bit that works. _  
_It works on my PC, if it doesn't work for you it's because you're doing it wrong_  
_What do you mean it doesn't compile? _  
_We do happy-path testing here._  
_What means 'test data'? _

You'll also be getting undocumented changes handed to you late on Friday evening that have to go into Monday morning's build. The developer will not have factored-in any time for bug-fixing, and if Monday's build fails it will be because you didn't test it right. 

**Agile - No Need to Know the First Thing About Computing**

Essentially, you will have to write test-cases that cannot possibly fail, and swallow your professional integrity while doing so. Here's one of our favourites, captured from a safety-critical field rather foolishly put into Agile hands:

"_System doesn't take forever_"

To fail that test you have to first solve The Halting Problem. Good luck with that. 

But don't be down-hearted. If you've got a certificate proving that you can sit through a two-day power-point given by a fat old windbag who doesn't know dick about software without falling asleep, and that you can afford the $3,000 entry ticket, you're hired. 

