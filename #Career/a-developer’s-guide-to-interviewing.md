# A developer’s guide to interviewing

_Captured: 2017-09-05 at 12:32 from [medium.freecodecamp.org](https://medium.freecodecamp.org/how-to-interview-as-a-developer-candidate-b666734f12dd)_

## Alternate title: How to interview a company

Have you ever been in a job interview, and the interviewer looks across the table and says, "do you have any questions?", and you just stare back and say, "umm, I don't think so". If this has happened to you, there's a good chance you took a pretty one-sided view of the interview experience.

![](https://cdn-images-1.medium.com/freeze/max/60/1*CTlZ73vo9IM0Crz_NhSL3Q.png?q=20)![](https://cdn-images-1.medium.com/max/1200/1*CTlZ73vo9IM0Crz_NhSL3Q.png)

As a candidate, you are understandably focused on one outcome: getting the job offer. But don't forget that job interviews are not one-way. You should be just as focused on **interviewing the company** as they are focused on interviewing you.

But what should you ask them?

Lots of job seeking developers have asked me this question. Over the past 15 years, I've worked for 7 companies (counting 2 internships and a 6-month stint at a startup), and I've interviewed at a dozen others. I've finally decided to write down all the questions I ask during these interviews in hopes others find them helpful.

> Side note: We cover this topic and many others in our weekly developer advice podcast [Soft Skills Engineering](https://softskills.audio/). Subscribe!

### Who will you talk to?

While interviewing, you'll usually get to meet three personas. Depending on the size of the company, these might be one human being or multiple:

  * Software Engineers
  * Engineering Managers (technical lead, middle manager, director)
  * Company Leadership (VP, CTO, CEO, department manager)

I have different questions for each of these personas, which I will list below. Note that I sometimes repeat the same question to multiple personas to see how their answers compare.

This is a pretty long article, and it's meant more as a reference than a read-through piece. If I were interviewing today, I would bring this with me and (discreetly) refer to it during my interview.

Most of these questions do not have a "right" or "wrong" answer. They are designed to help you learn about the company, its culture, processes, and organization. They also serve as conversation starters, which can be quite helpful during an interview when your brain has shut down.

As a matter of courtesy, I usually tell interviewers at the beginning of the interview that I would like to have some time to ask questions. This will help them plan accordingly. Usually, they let me ask questions at the end of the interview, so be sensitive to the interviews' schedule, and make them aware of your intentions early in the process. After each question, pause to ask if it's ok for you to continue asking questions, and how much time the interviewers have.

#### 1\. How do you know what to work on each day?

The purpose of this question is to identify dysfunction. I want to get answers from 2 or 3 engineers. If company leadership says they follow a certain process, but the engineers don't talk about the process, that's a sign of dysfunction. If you get different answers from different engineers, that's another sign of dysfunction.

In a high quality team, I get consistent answers to this question. Every developer knows the process, and the process is light weight enough to be supportive of the engineers rather than oppressive to them.

Example of a good answer (there are many others): "We do N-week sprints wherein each engineer commits to a set of features and bug fixes to deliver. Each day we report progress on our commitments to each other. We have an amazing product manager who interfaces with customers to help us prioritize features and bug fixes."

Example of a bad answer (there are many others): "I come into the office and see what fires are burning. Most days, I get interrupted with an emergency."

Notice I don't mention "Scrum" or any other specific methodology. I'm much less interested in the labels the company uses for their engineering process than the actual day-to-day "how stuff gets done".

#### 2\. What do you use for revision control?

Good tooling is a strong indicator of a good team. If a team is using an ancient revision control system, they are probably using a bunch of other outdated tools. Furthermore, they probably don't value the efficiency gains that can be achieved by investing in good tooling.

A good follow-up question is to ask about workflows. Do you use branches? Do you prefer rebasing or merging (git terms)? These questions will tell you how expert they are with their chosen tools, which will tell you a lot about their level of proficiency, which will in turn tell you what to expect if you take the job. For example, will you be the "local git expert" or will you be learning from a veritable Linus Torvalds?

This question can start a discussion about tools in general, which will often give you some good insight.

#### 3\. What do you like about working here?

Strong answer: I get a lot of satisfaction from the work I do.  
Strong answer: We have a lot of fun at work.  
Strong answer: I love working with really smart, friendly co-workers.  
Strong answer: Management respects engineering.

The more good answers the better. I don't have to get all the answers above to give high marks to the company. Keep in mind that some people are not naturally "gushy", so you may not get stellar responses here, and that might be just fine.

But if I hear the following kinds of answers, and very few from the strong answer list, I get nervous:

Weak answer: It pays the bills.  
Weak answer: I don't have to work very hard.  
Weak answer: There is not a lot of pressure to deliver.  
Weak answer: It doesn't matter if I make big mistakes.  
Weak answer: (silence)

Don't think I am making those answers up. I've actually heard those in real interviews.

I don't automatically consider it a bad company if I hear those weak answers, but if those are the only answers, I usually look elsewhere.

#### 4\. Do you write unit tests?

Be careful when making conclusions about an engineering team based on their unit testing practices. If a team gets excited when I ask about unit testing, it's generally a good sign. Though on the other hand, if they can't explain **why **they unit test, or the drawbacks of unit testing, this can be an indication of blind sheep dogma. If they provide bad excuses for why they don't write tests, especially excuses like "we don't have time", that is a bad sign for me.

If the engineers tell me they write unit tests, and they are able to tell me metrics about their tests, such as how long they take to run, how many tests they have, and their code coverage, that is pretty attractive to me. It tells me that they have good tools, and they know how to use them. On the other hand, if they believe that 100% code coverage ensures a bug-free code base, I am leery.

I want to know beforehand if I will be working on a large, old, untested codebase at this company. This will help me manage my own expectations and decide if that's something I want to do.

Follow-up questions:

  * Do you prefer unit tests or integration tests?
  * Do you have acceptance tests?
  * What testing framework(s) do you use? Do you like it?
  * How long do your unit tests take to run?

#### 5\. Do you have continuous integration?

The best software development teams I know use tools like Jenkins, Travis, and Buildbot. If the team has no continuous integration, I try to gauge whether they are familiar with the concept. If they aren't, this is a bad sign in my experience. Having a continuous integration system means that the team probably believes in automation, which is usually a very good sign in my experience.

For some teams, this naturally leads to a discussion about [continuous delivery](http://www.amazon.com/Continuous-Delivery-Deployment-Automation-Signature/dp/0321601912), which is a related but different concept from continuous integration. If it's a web developer position, I expect the team to at least have **heard **about CD, and strong teams tend to put it in place, at least in part.

Follow-up questions:

  * When CI reports a failure, how long does your team take to get it fixed?
  * What do you like/dislike about your CI system?
  * How long do your CI runs take? Are you making them faster?

#### 6\. What do you measure?

This is an open-ended question meant to find out if the team has put effort into measuring their software. For web development teams, the answers tend to focus on performance metrics like server response times, request throughput, number of users, client-side responsiveness, etc. But the discussion can go to things like number of users who speak different languages, browser breakdown, cache hit/miss rates, and myriad other topics. If the team hasn't taken the time to measure, it can be an indicator that they don't use real data to inform their decisions. They may be premature optimizers. I value a team that uses real, measured data to make decisions, especially about performance, but it applies to so many other things.

If the interviewer knows answers to many of these questions, it's a good sign that the team is high quality. If they have no idea why they would even care about any of these measurements, it could be a negative indicator.

Again, the rule about dogma applies here. If the team seems to have latched onto a metric that doesn't necessarily yield valuable, actionable information, and they can't explain this to your satisfaction, this may be a warning sign.

Follow-up questions:

#### 7\. How do you find and fix bugs?

A strong team usually has dedicated testers, and the team's developers focus on quality. A really strong team has impressive test automation. Some teams are too small for dedicated testers or test automation, but that doesn't necessarily mean they are a bad team. When I ask this question, I'm trying to get a feel for their process. Is their hair always on fire? Do they have a sane process for finding and prioritizing bugs? Do they rely on users to find bugs?

Follow-up questions:

  * How do you prioritize bugs?
  * What bug tracker do you use? (and what do you hate about it)
  * How many bugs do you have in your bug tracker?
  * How long do your bugs take to fix (min/max/typical)?

#### 8\. What collaboration tools do you use?

In my experience, high functioning teams use lots of collaboration tools. They often use chat services (Slack, IRC, HipChat, Jabber), code review services (Gerrit, GitHub, GitLab, Review Board), and of course, the venerable-but-showing-its-age Email. I am looking for indicators that each developer knows what the other developers are doing. I'm not looking for insane levels of detail, but more for a general awareness. Also, I like to see integrations with collaboration tools. The simplest example is an automatic email sent any time there's an automated build failure. Another example for web-dev teams is automated error logging services that notify the team's chat room when serious errors occur, or when key metrics cross a certain threshold.

#### 9\. What frameworks do you use?

My personal preference with frameworks is two fold:

  1. I like modern stuff.
  2. I like new-to-me stuff.

So if a team is building an [AIX](https://en.wikipedia.org/wiki/IBM_AIX) desktop application in [Motif](https://en.wikipedia.org/wiki/Widget_toolkit), I am probably not interested. But maybe you are. This is a deeply personal topic, and you should approach it with a solid understanding of your own preferences.

Regardless of your framework preferences, it's important to understand **why **the team has chosen their framework(s). Are they hype-driven? Do they change frameworks like their underwear? Is their codebase littered with shrapnel from framework-of-the-month churn? Are they stuck on an ancient version?

On the topic of **why**, I like to understand how much latitude developers have in choosing technologies. Does management mandate technology choice? Does management defer to developers? To get to the bottom of these questions, I usually ask, "How did you come to use framework X in your project?". If developers don't know the answer, that might be a bad sign, or it may mean they are just new enough to the company that they weren't around for the decision.

I like to see teams make contributions to open source projects they use. This tells me they are not only able to **use **open source code, but they are proficient enough to contribute to it as well. These are the kinds of developers I like to work with. If the company is willing to pay them to do this, even better. That tells me the company understands what it means to be an open source citizen.

If the team is reinventing the wheel rather than using readily available tools to help them build their product, I get nervous. There are exceptions to this rule. For example, when Facebook [was working on their own framework](https://facebook.github.io/react/blog/2013/06/05/why-react.html), I wouldn't have held it against them (or would I).

#### 10\. When can we pair?

If you want to get a really clear picture of what it's like to work with this team, then try actually working with them. I've never personally done this, but I have a friend who has (a likely story, right). I think it's a fantastic idea. If you want to learn almost anything about the team, go work with them for a half day. It might require you to sign an NDA. If the team is even willing to consider this idea, I think it's a very good sign.

You will probably have to arrange this with someone from management, so this question is more designed to get a reaction from the developers. They may be so appalled by the idea that it's not worth bringing up with management.

#### 11\. When is your next deadline?

This question is designed to tell you more about the development process the company actually follows. This question, alone, is not very informative, but when you add these questions, things get much more interesting:

  * Who set this deadline?
  * Did you meet your last deadline? If not, why not?

High quality teams agree on and commit to deadlines together. Deadlines that are handed down arbitrarily can be a sign of dysfunction, or at least that engineers don't have a seat at the table when determining schedule.

#### 12\. How long does it take to set up a new development environment?

This question serves to help gauge how much effort the company has put into developer experience. Does it take hours, days, or weeks for new developers to have their computer set up and ready to start coding? Is it automated or manual? This will tell you how proficient the team is at "supporting activities" that aren't directly related to writing software, but that help support it. Does the team take this seriously?

Some companies pride themselves on having a dev setup process that is so fast that new developers can put code into production on day 1. This shows that the company takes providing a frictionless experience for developers pretty serious.

#### 1\. When was the last time you wrote code?

I like managers with a strong technical background. No offense to my MBA friends, but I've found the managers I really like are those who have done what I do.

#### 2\. How did you become a manager?

I like managers who chose to become a manager because they truly enjoy it and have a knack for it, rather than being forced into it. I also like it when managers seem to be focused on serving their team. My favorite managers are those who focus on making life better for their team, rather than "managing up". They see themselves as a helper and protector for their team. They have an attitude of service, and they consider their most important job to make their team members' work lives better.

#### 3\. How do your engineers know what to work on each day?

Since I ask the engineers this same question, I like to compare the manager's answer to see if they match. If they don't match, it can mean there's dysfunction. The worst kind of dysfunction is unrecognized dysfunction. I believe it's the manager's job to identify disparity like this and fix it.

#### 4\. What is your team's biggest challenge right now?

They usually answer that it's a shortage of staff. Because this is a common and obvious answer (they are hiring after all), I like to ask for their second biggest challenge. I'm looking for red flags like slipping schedules, product quality problems, and interpersonal drama. You'll know the red flags when you see them. Every team has problems, so the answers you get will depend on several factors:

  * The manager's awareness of problems
  * The manager's willingness to be honest with you
  * The seriousness of the problems on the team

#### 5\. How do you measure individual performance?

A skilled manager will have a good technique for doing this. The best managers will carefully gather feedback from the whole team when assessing an individual team member's performance. A bad manager will make a call based on their own observations, without consulting the team.

#### 6\. Do you do formal performance reviews?

I like to work for managers who value giving feedback and helping their team members improve. Performance reviews can be painful or positive experiences. Based on my own observations, I think most people consider them painful. A really great manager will know this, and will have taken measures to make performance reviews great in some way that leaves you impressed and want to work for them.

Follow-up questions:

  * Can you tell me about a time you helped someone improve their performance?
  * How do you coach people during these reviews?

#### 7\. Do you do annual salary increases?

I like to know that my compensation will be adjusted to match my contribution to the company, and that we'll take an official look at it at least once a year. For companies where it applies, I like to ask about equity. Will you give me stock options? Will you give me more stock options every year?

Some engineers are uncomfortable asking financial questions like this. Don't be. Engineers generally spend a very small percentage of their time thinking about these topics, but managers have these conversations **all the time**. These questions should not be uncomfortable for a manager:

  * How do you budget for raises?
  * What was last year's median raise on your team (in percent)?
  * How much salary increase could I expect one year from now? Best case, worst case?

I don't ask these questions as a signed-in-blood contract or guarantee of future raises. Instead, I want to understand how the company operates. Will I have to go out of my way to ask for raises, or is there a standard process already in place?

#### 8\. Can I get some take-home material describing company benefits?

I figure most people already know to ask this, but it's worth mentioning for the sake of completeness. Most companies are prepared to give you a bunch of paper, or a web site, that describes the company benefits. It's important to know, because it's often a pretty big part of your compensation. This might only apply in the USA. I'm not certain how company-provided medical insurance incentives work in other countries.

#### 9\. Do you rank employees against one another?

Some companies determine raises and bonuses (I'm not making this up) by ranking every employee in a big sorted list, from best to worst, and then forcing a certain percentage of employees into "good", "average", and "bad" sub-lists.

I've never met an engineer who likes this. This is particularly common among big companies. It can influence how you interact with your peers, because you know that one day you will have to compete with them for money.

When I encounter this, it might not immediately mean the company is a terrible place to work. There are often small pockets of awesomeness flying under the radar" in companies like this. Ask the interviewers how they like the system. Some managers will be quite candid about their dislike for the system, and some will even tell you about strategies they use to "game" the system for the benefit of their team. If you find this kind of manager, you might be able to overlook the ranking system.

Keep in mind, also, that not everyone hates this system. Just because I haven't met someone who likes it doesn't mean they don't exist.

Follow up questions:

  * Do you really think X % of your employees are "bad"? What does that say about your hiring process? (this is a bold question -- tread cautiously)
  * Do you apply some kind of curve to determine top performers?
  * What metrics do you use to rank the employees?
  * How do you know these metrics are collected accurately?
  * How do you know these metrics actually identify top performers?

#### 10\. Do you do regular team retrospectives?

If so, what are they like? How often do you receive feedback from members of your team? When was the last time you changed something about the way you run your team based on feedback you received?

These questions will give you a feel for how responsive you can expect management to be, and whether the team contributes much feedback to management.

If retrospectives aren't happening, it's difficult for a team to identify problems, let alone shift gears to correct for them. And if a manager doesn't feel like they receive feedback for how the team could be going better, then they are probably either tone deaf to the issues of the team, or building an atmosphere where people don't feel safe to speak up with problems.

I don't always get to talk to the company's senior leadership, especially for larger companies, but when I do, I take it as an opportunity to assess the company's financial viability. I'm not really qualified to do this, but there are some obvious problems that I can sometimes discover in an interview. Also, I like to know what the top-down culture is like, because this information can tell me how the company values its engineers, both positively and negatively.

#### 1\. How are you funded?

I'm trying to gain insight into the money behind the company. If they are funded by venture capital, private equity, public stock, or self funded via revenue, I want to know it. Often I can figure this out before the interview pretty easily, but company leadership will often add insights that I can't find via Google or [CrunchBase](http://crunchbase.com/).

If profitable, great! If not profitable, what's your plan for becoming profitable? Some startups have a plan for this, while others are looking for an exit via acquisition or IPO.

Follow-up topics:

  * Historical revenue for the past few quarters/years. Is it trending upward?
  * Risks to profitability like competition, surprise expenses, and surprise revenue shortfalls.
  * Runway: How long could the company operate before raising more capital.

#### 3\. What is your opinion on outsourcing?

I want to know if the job I'm applying for is likely to get outsourced in the future, or if the job could turn into a position managing outsourced engineers.

I'm not just talking about offshore outsourcing here. This includes contractors as well.

#### 4\. Tell me about the company culture.

This is another question I use to reconcile the engineers' perspective against leadership's perspective. I'm looking for discrepancies as a sign of dysfunction. If leadership and engineering are on the same page, that indicates good top-to-bottom communication. I want to know if senior leadership is out of touch with the in-the-trenches employees. I also want to see if the leadership has solid vision that is well communicated. My favorite companies to work for have a strong, shared vision.

Some companies [take culture very seriously](http://www.slideshare.net/reed2001/culture-1798664), and this can be a good thing. At least you'll be clear on what the company values. For other companies, you'll have to suss it out through implicit, sometimes unspoken nuances. Culture can be very important. Is there political infighting? Is professionalism valued? Is honesty valued? Is overtime valued?

#### 5\. What assurance do you have that this company will be successful?

With this question I'm looking for real evidence, not just marketing hype. If senior leadership gives me actual numbers, like revenue, market size, and capitalization, that is a good sign. Also, if I can verify this information from other sources, that is an even better sign. On the other hand, the numbers may indicate something very bad, like a one-month runway with no funding on the horizon.

#### 6\. Tell me about your reporting structure.

For me, the best answer to this question is a simple one. If the person can draw a simple org chart that explains the reporting structure, I am satisfied. My personal preference is to work for small, nimble companies with minimal organizational and communication overhead. Your preference may differ, and that's ok. No matter your preference, this question is designed to give you the information you need to make an informed decision about the company.

Interviews are bidirectional. Make sure you get everything out of the experience you need to make an informed decision if you are fortunate enough to get an offer. Good luck!
