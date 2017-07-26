# Test-Driven Development as Pragmatic Deliberate Practice

_Captured: 2017-03-11 at 01:38 from [blog.jbrains.ca](http://blog.jbrains.ca/permalink/test-driven-development-as-pragmatic-deliberate-practice?utm_content=buffere71f1&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

I use TDD as a method for learning the fundamentals of modular design, but I have to admit that I've mostly relied on the emerging discipline of the student for its effectiveness. I'd like to do this better, and I've kept an eye out for ways to script the critical moves[1](http://blog.jbrains.ca/permalink/test-driven-development-as-pragmatic-deliberate-practice?utm_content=buffere71f1&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer) in adopting TDD as a learning method. I believe I have found a microtechnique to help do exactly that, and I wanted to share it with you immediately.

##  TL;DR? 

Many TDD proponents promote "deliberate practice", but you probably don't feel like you can afford to spend time at work practising. I advise people to "practise TDD mindfully", but haven't really had a good way to describe what that means, limiting the value of that advice. You can start doing both by fixing bugs test-first. Even if you can't (yet) design like an expert, you can at least _learn_ like an expert, and fixing bugs test-first can give you a natural, relatively low-risk opportunity to do just that. You'll have the opportunity to practise TDD diligently and mindfully. Since you can typically implement bug fixes alone, you can do these things quietly and under the radar, avoiding the raised eyebrows that come with talking too loudly about "deliberate practice" at work. Just tell everyone that you're fixing bugs. They'll like that.

You can start simply by writing a test that will fail until you fix the bug. If you'd like more details before you start, then read on.

> if you have legacy code and want to write unit tests, concentrate on writing them when you fix a bug. Best possible use of your time 
> 
> -- Chris Hartjes (@grmpyprogrammer) [June 12, 2014](https://twitter.com/grmpyprogrammer/statuses/477081748036399104)

##  The Details 

In reading Gary Klein's _[Sources of Power_](http://link.jbrains.ca/1mIEU4I), which describes how people learn about making decisions, I reached a section on deliberate practice which caught my attention. (I took the next few quotes from page 104 of the book.)

> Because the key to effective decision making is to build up expertise, one temptation is to develop training to teach people to think like experts. 

I imagine that a lot of people have succumbed to this temptation, structuring their training to maximise the amount of expert-level information they can transmit to the participants. I have done this, and stopped when I began experiencing this kind of training as a participant myself. If you open the firehose on me and spray me with conclusions and dozens of rules to follow, I "fill up" in only a few hours before I stop listening.

> But in most settings, this can be too time-consuming and expensive. 

Yup.

> However, if we cannot teach people to think like experts, perhaps we can teach them to learn like experts. 

Go on…

> After reviewing the literature, I identified number of ways that experts in different fields learn: 
> 
>   * They engage in deliberate practice, so that each opportunity for practice has a goal and evaluation criteria. 
>   * They compile an extensive experience bank. 
>   * They obtain feedback that is accurate, diagnostic, and reasonably timely. 
>   * They enrich their experiences by reviewing prior experience to derive new insights and lessons from mistakes. 

Some of this sounds familiar, and some of it presents an opportunity to get more out of TDD as a pracitioner.

##  Three Out of Four Ain't Bad 

I've written about deliberate practice before. In "[Don't Waste Your Golden Learning Opportunity!"](http://link.jbrains.ca/QWtA8S) I wrote about treating new practices like etudes, a metaphor taken from music, which roughly corresponds to "performance-worthy practice". Athletes might think of this as practising at game speed. Since most programmers will probably never practise outside the bounds of their day jobs, it makes sense to look for a practice regimen that they can use while they "perform".

I learned test-first programming, and later test-driven development, _in anger_, meaning while working in a real, industrial-strength, time-sensitive context for a paying employer who expected results from me. Looking back, I managed to do three of the four things that Klein listed as ways experts learn.

  * I compiled an extensive experience bank by using TDD to write almost all my production code starting in early 2000 until I left IBM in November 2001. 
  * I obtained accurate, diagnostic, timely feedback by asking hundreds of questions and engaging in deep discussions in the various mailing lists of the time. (No StackOverflow back then.) I also answered a lot of others' questions, which involved reading, writing, and improving a lot of code. 
  * In answering questions on mailing lists, at conferences, at user group meetings, I often went over old ground, honing my message as well as finding new insights. All this eventually became my first book, _[JUnit Recipes: Practical Methods for Programmer Testing_](http://link.jbrains.ca/TEDGGm). 

Even so, while I practised deliberately and diligently and even mindfully, I did not go so far as to articulate a goal and evaluation criteria for my practce sessions. Well--I did and I didn't. I certainly didn't do so intentionally; when I did so, I did so accidentally. So let me reflect on my prior experience and derive a new insight from it.

##  Practising TDD Deliberately 

If you'd like to practise TDD as a way to learn more about how to design systems well, try this at work.

Sign up to fix a bug. You probably already know the mechanics of using test-first programming to fix a bug, but in case you don't, I summarise it this way:

  1. Write an integrated test that fails because of the bug. The test doesn't have to run end to end, but feel free to expand the test's scope as far as you want, as long as it fails because of the bug. 
  2. Start writing smaller and smaller (more focused) tests to zoom in on the location of the bug. You might use the [Saff Squeeze](http://link.jbrains.ca/QWvN42) to do this, but any technique will do. You may even use the debugger, if you like. 
  3. Stop when you have a minimal test (or tests--some bugs have multiple causes) that describes the essence of the mistake that causes the bug. 
  4. Fix the mistake, watch all the tests pass, then commit everything. 
  5. Make yourself some coffee. 

Now let's return to Klein's four points and consider how this method can help you learn like an expert in software design.

**Does this seem like deliberate practice?** Yes. When I sit down to fix a bug with this method, I treat it as an opportunity practise writing tests first, to rely less on the debugger to rely less on tracing program execution in my head, as well as to both articulate and document (as tests) what I learn about the code as I debug.

**Do I have a clear goal and evaluation criteria?** I see a clear goal: fix the bug, learn how to write tests (at all), learn how to write more-focused tests, and document what I learn so that that knowledge doesn't start decaying the moment I commit my changes to the code base. As for evaluation criteria, I can think of a few:

  * How easily can I return to these tests after forgetting the debugging session and understand what I did? 
  * How easily can someone else read my tests and understand what I did? 
  * How easily did I move from larger tests to smaller tests? 
  * What information, if any, did I lose un going from larger tests to smaller tests? 
  * How confident do I feel that this particular bug will not recur? 
  * How calm and comfortable did I feel during the debugging session? 

I don't know whether you'd call these criteria _clear_, but they represent a starting point. We can probably develop even clearer evaluation criteria together.

**Does this help me compile an extensive experience bank?** It does if I fix 50 bugs this way in the next several months. At a minimum, if I decide to fix all bugs this way, then I will steadily compile an extensive experience bank, as long as I fix bugs throughout the system, and even perhaps in multiple systems.

**Do I obtain accurate, diagnostic, timely feedback?** I think so. At every step, when I write a new test, it either passes or fails, and so at least I know right away whether I'm stomping around a faulty part of the code base. I can't say with supreme confidence that I've found the relevant faulty part of the code base until my tests become small enough to make that evident one way or the other, but I'll get there.

**Does this help me review my prior experiences to gain new insights?** Yes and no. No, because I hope that I never fix the same bug twice; but yes, because I work this way every time I fix a bug, and I will have to tread at least the same part of the system multiple times. As I fix more bugs in the same part of the system, I will think back to my last time there, and relate my new experiences to my old ones. I can't help but spend some time noticing what I'm doing differently this time compared to last time, and that gives me at least the opportunity for new insight.

So this method of fixing bugs seems like it would help the practitioner learn like an expert, at least according to this interpretation of both the method and Klein's model of learning like an expert. It passes the Laugh Test and you can probably feel comfortable trying it.

##  Beyond Fixing Bugs 

How can you use TDD to learn modular design techniques like an expert? I have to admit some malpractice here. Not serious malpractice, but rather well-meaning-but-ignorant malpractice. I have made a big deal about "mindful practice" over the years. Whenever someone has claimed that TDD "doesn't work" or "hurts" or "does damage", I've stepped in to say the same thing over and over again:

> Rules don't do things; people do things. TDD, like any practice, still requires the practitioner to switch the brain on. They need to practise mindfully. 

True, but useless… until now. I believe that Klein has introduced me to a more precise and actionable way to say "mindful practice". I plan to use this in my training starting today. It turns out that I stumbled upon learning TDD (and modular design) this way, but never had a memorable way to explain it until now. Thank you, Gary Klein.

##  How to Practise TDD "mindfully"

Take a few moments and think about when and where you intend to practise TDD. On which code? At which time? In which circumstances? You don't need to have air-tight rules, but some idea would help. I find it just as important to decide when you _won't_ practise TDD and when you will. For now, decide this for only yourself. You can negotiate this with your co-workers later.[2](http://blog.jbrains.ca/permalink/test-driven-development-as-pragmatic-deliberate-practice?utm_content=buffere71f1&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)

Once you have decided the boundaries of when and where you'll practise TDD, you can decide some goals and evaluation criteria for your practice sessions. Let me give you a few ideas.

**Goals for TDD practise sessions**.

  * Test-drive the integration point to a library you haven't worked with before. 
  * Isolate more of your code from the integration point to a framework. 
  * Write fewer tests that need a framework testing library (like Robolectric, NUnitASP, rspec-rails, or JSFUnit) and more that use the plain testing framework (plain JUnit, RSpec, or pytest). 
  * Reduce the time it takes to write the next test. 

**Evaluation criteria for TDD practise sessions**.

  * Did I build this part of the system more easily than usual? 
  * Do the names in this part of the system make it easier for others to understand how to change this code? 
  * Can I extend this part of the system more easily by only adding code, rather than having to change it? 
  * Does the setup code that I need to run my tests involve only the parts of the system that I've just designed? 
  * If I have multiple assertions in a test, do I consider this very strongly related to each other? 
  * Did the pace at which new tests passed feel fast to me? or at least faster than before? 

If we sat down for ten minutes together, we'd probably identify a dozen other useful criteria. Pick a few and have those in mind for the next programming session in which you practise TDD.

Let me jump ahead to **gaining new insights from prior experiences**, because I do this by teaching and practising with others. You don't have to run training classes to teach others: you can answer people's questions. More specifically, I answer the same questions over and over to different people. (I used to hate the repetitiveness, but I appreciate it much more now.) The more I answer those questions, the more I reflect on my understanding. Over time I address increasingly diverse challenges to my ideas and they either become stronger or give way to better ones. I also participate in Code Retreats specifically so that I can work on the same little problems over and over again with more and more people. Every year I find more insights in working on Conway's Game of Life and the Trivia Game.

Now to the big one over Gary Klein's four-point model for learning like an expert: the one that led me to write this article specifically today.

###  The Extensive Experience Bank 

I've described TDD for years as a "learning-to-design technique", in which we can use a mechanism similar to the one we use to acquire language skills. How did you learn to speak your native language? You probably did something like this:

  * You mostly listened for a long time to people speaking the language around you. 
  * At some point, you began speaking very simple sentences. 
  * As you spoke sentences, you noticed how people reacted to what you said, looking for signs that they understood you. 
  * Some people corrected you, instructing you to say _this_ instead of _that_. 
  * As people corrected you, you extracted rules, guidelines, and principles to build "correct" sentences. (This part gets fuzzy; stay with me.) 
  * You used these rules, guidelines, and principles to inform how you constructed new sentences. 

You've never stopped doing this. The language you speak became an ongoing negotiation with other speakers, involving experiments, evaluations, mutual feedback, attempts at correction, extracting new rules, guidelines, and principles, repeating until death.

I think that TDD provides a way to learn design this way. It goes beyond merely programming because it presents the programmer with example after example of code subject to constraints like "I can easily test this" or "I can extract this from its context to run it in isolation" or "I can add new behavior by adding code rather than changing it". You can argue that one gets these benefits from merely reading and talking about code, but TDD encourages the programmer to carry on a conversation with the code, thinking alternately about "how should this behave?" and "how should I design this part?" I think that this conversational style builds up the experience bank more steadily and more extensively than a more traditional write-lots, read-rarely approach. If nothing else, TDD encourages the programmer to think differently about the code.

Refactoring plays the central role in this approach. Refactoring involves evaluating the code as it stands, looking for problems, articulating those problems, proposing an specific improvement, then changing the code gradually to make that improvement. (I wouldn't want to refactor much without tests, and I probably wouldn't write enough tests if I didn't write those tests first.) Refactoring exposes the programmer to example after example of designs that might or might not have problems, and helps the programmer compare those to examples of designs that don't have those same problems. The programmer has the opportunity to compare "before" and "after" and reflect on whether the "after" represents a true improvement over the "before".

You can think of the "before" designs as being incorrect or correct-but-poor-style sentences. You can think of the specific microrefactoring techniques (Replace Inheritance with Delegation or Introduce Temporary Variable) as rules, guidelines, and principles from correcting or improving the style of those sentences. You can think of the act of refactoring as trying to apply these rules, guidelines, and principles to specific code (sentences). You can then evaluate the changes by thinking about them from the perspective of a programmer having to read and understand what you've done. If you can't evaluate your own work, or you feel unsure, then you try your design out on others, asking for their evaluation. They might correct you, or at least point out poor style. Just like you use this method for learning your native language, you can use it to learn the language of good modular design.

  1. Read especially chapter 3 of _[Switch_](http://link.jbrains.ca/TeSr30) for more about helping people start changing their behavior.[↩](http://blog.jbrains.ca/permalink/test-driven-development-as-pragmatic-deliberate-practice?utm_content=buffere71f1&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)

  2. I teach a technique for teams to adopt practices as safe-fail experiments as part of guiding teams to improve their work. I haven't written about it in detail yet, but I will. If you can't wait and want to learn it directly from me, then [contact me](http://ask.jbrains.ca) to discuss how we can work together.[↩](http://blog.jbrains.ca/permalink/test-driven-development-as-pragmatic-deliberate-practice?utm_content=buffere71f1&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)
