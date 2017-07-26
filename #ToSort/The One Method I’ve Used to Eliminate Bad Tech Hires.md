# The One Method I’ve Used to Eliminate Bad Tech Hires

_Captured: 2015-09-26 at 19:34 from [medium.com](https://medium.com/swlh/the-one-method-to-eliminate-bad-tech-hires-630d539b2e1d)_

![](https://cdn-images-2.medium.com/freeze/max/30/1*WwAEyQ2_UgKf0EQsziHvjw.jpeg?q=20)![](https://cdn-images-2.medium.com/max/600/1*WwAEyQ2_UgKf0EQsziHvjw.jpeg)

Let's be real. Interviews are a terrible way to hire tech candidates. Not only do you not get a real sense of the candidate, they often weed out good candidates in favor of bad ones.

In this [fantastic article on Medium by Eric Elliott](https://medium.com/javascript-scene/why-hiring-is-so-hard-in-tech-c462c3230017), he talks about many of the techniques that work and don't work for interviewing engineers.

In regards to what works the best, I found that these 2 ideas work the best when combined.

  * _PAID Sample project assignment (err on the side of paying fairly -- say $100+/hour for estimated completion time -- if the problem should require 2 hours to complete, offer $200)_
  * _Bring the candidate in and discuss the solution. Let the candidate talk about their design decisions, challenge them as you would any team member and let them provide their reasoning._

Paying candidates to work on a simple project and then discuss it with our team has almost single handedly eliminated any bad hiring decisions. Paying a candidate that gives you a terrible solution (or no solution) is FAR cheaper (both financially and emotionally) than hiring the wrong person, going through a 3 month performance improvement plan to try to make them the right person and eventually firing them.

We have gone from "This candidate is exactly what we need" to "I have serious doubts about working with this candidate long term" and we've had candidates change our bad perception of them using this technique. It's very easy for someone to embellish (to put it generously) their resume, and coding trivia can be memorized, but it's really hard for someone to fake actual skill.

#### Here's why paying candidates to solve problems works

_For the Employer_

  * Since the candidate is getting paid, the candidate treats it as a legit consulting session and therefore gives her best effort in solving the problem.
  * It's an indication to the candidate how they will be treated in the near future if they decide to join.
  * It allows a mock work interaction with the candidate at a very low risk cost to you. After the project is complete, you can bring the candidate in and ask them questions about their actual design/coding decisions. This lets you get a sense of how they communicate, take criticism/questioning and if they are able to provide solid reasoning behind their choices.

_For the Candidate_

  * It gives the candidate a real life sense of how you interact with people on the team
  * Allows them to showcase some of the skills that are on their resume, but may not pop from just reading it
  * Allows them to give you a sense of what they feel is important in a non-judgemental way. For example, did the person write a test for every line of code? No? Maybe that's not really important to them and maybe that's totally valid. You'd never get that from just asking them do you do TDD? Everyone will say tests are important…and they are. The thing most people disagree about is how important, this will show that.

#### I have 6 rules when giving this interview method

**RULE #1 -- Give them the weekend to solve the problem.**

This is where I and Eric slightly disagree. 2 hours just isn't enough time to see how well someone can come up with an appropriate solution.

What I like to do is invite them to the office on a Friday and go over the problem at hand and how I would like for them to solve it. Then I'll hand it off to them and set up time on Monday to review their solution.

I'll provide them with certain technologies that should be used for the solution and let them use other tools or technologies at their discretion. For example, I may say please use functional reactive principals in JS to solve this problem, but the decision of using Kefir, Bacon, or RX is left up to them.

**RULE #2 -- DON'T use a real problem because of tribe knowledge needed to fix.**

This goes hand in hand with Rule #1, but unless you're hiring a customer service rep, it's almost impossible to hand someone a computer and say OK, Fix this issue happening in our proprietary system using the tools that normally everyone gets properly trained on.

Give a problem that is very self contained.

**RULE #3 -- The solution you're expecting should be clear, but open for improvement.**

For example. If I'm interviewing a web developer, I'll give him a sample clear scenario:

> Create a single page app that lets me enter movies in my home movie collection, store them in offline storage and search through them. I want to search by Genre, Title & Actors.

I actually don't tell them further directions like use web storage vs cookies, or make it responsive on multiple platforms and use a custom stylesheet. I leave that up to them. Some choose to do what we asked, and some do much more.

In the end, what matters is that we like the end result.

I don't say "I like movies, create me a nice movie website", or "How would you architect [IMDB](http://www.imdb.com) if you had to create it from scratch." I want the task to be simple enough that the engineer can provide a solution and challenging enough so they can use their skills to create something special.

**RULE #4 -- Let them present their solution to a group on Monday.**

The biggest issue I have seen with tech hires is that they can become very defensive over their solution. I will purposely challenge their solution to see how they react.

If they get defensive, it's an immediate no-go. Remember, there's a difference between defending which is good and being defensive which is bad. The difference is that the former is based on rational facts, the other is based on emotion.

A key aspect of this is that everyone in the group MUST come prepared, having looked through the solution.

**RULE #5 -- Write the problem down for them to take home.**

Be clear about what technologies, tools and look you're after, and the standards being judged. At the same time, leave the final solution open enough that the candidate can add their own flair. Let them ask you any questions they have on Friday, and make sure to be available for their questions via email over the weekend. The goal is to create an environment of success (hopefully like you would for an employee).

**RULE #6 -- Pay them immediately on Monday**

Hire them or not, something about giving them a check after they present their solution is the best way to start or end a relationship.

Another way to do this is to use [June](http://joinjune.com/) [disclaimer: I'm a co-founder there] to facilitate the interview and payment.

#### To hire or not to hire that is the question

_Indicators you should hire this person:_

  * During the meeting on Friday they asked a lot of clarifying questions
  * The questions were thought out and made sure that nothing was misunderstood
  * The solution addressed your problem using the technologies and techniques you prescribed
  * They read the entire problem and followed the instructions correctly (i.e. if the problem said use PostgreSQL, they didn't give you queries that only work on Oracle DBs).

_Indicators you shouldn't hire this person:_

  * They refuse to do the project because "someone will hire me without it".
  * Didn't complete the project correctly
  * They can't articulate their design/coding decisions and why they were made.
  * They get defensive when presenting their solution

#### In Summary

Your mileage may vary, but I found this technique to work wonders for hiring talented tech talent. While my sample size may not be huge, I've yet to have it lead to a bad hire.

#### About Me

I'm Amir Yasin, the CTO and Co-Founder of [June](http://joinjune.com/). Get Paid to speak with the best IT recruiters in the world.

I'm a polyglot developer deeply interested in high performance, scalability, software architecture and generally solving hard problems. You can [follow me on Medium](https://medium.com/@ayasin) where I blog about software engineering, [follow me on Twitter](https://twitter.com/ayasin) where I occasionally say interesting things, or check out [my contributions to the FOSS community on GitHub](https://github.com/ayasin).

If you enjoyed this post, I'd really appreciate a recommend (just click the heart below).

_Published in _**Startups, Wanderlust, and Life Hacking**
