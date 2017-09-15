# Speed in Software Development.

_Captured: 2017-09-05 at 13:17 from [www.targetprocess.com](https://www.targetprocess.com/articles/speed-in-software-development/)_

# Speed in Software Development

[ ![Michael Dubakov](https://secure.gravatar.com/avatar/36bf9e248882252e192235cb745a28ec?s=25&d=mm&r=g) ](https://www.targetprocess.com/blog/author/admin/) [Michael Dubakov, Targetprocess Founder, June 2014](https://www.targetprocess.com/blog/author/admin/)

Every single CEO of any IT company wants to build software faster. Time is the most expensive and valuable resource. You can't waste it on re-work, refactoring, meetings, physical activities. Right? It depends...

Many companies grow up, slow down, and die. Good development pace is essential for surviving. Imagine, you have a really great vision proven in many circumstances by many people. You know for sure (well, that is rare in practice, but we'll fuel our imagination, OK?) that this product will be a real hit. All you need is to complete it.

You have a team of dozens talented and experienced developers, you crunch and ship something in two years. The team is exhausted. The product implements about 10% of the vision. There is a huge potential, everybody says that, but 10% is not enough to penetrate the market. You struggle for some more months, have average traction, have below average sales, have no money and, in the end, no company. Great vision is terminated by slow execution. Who to blame? Maybe the problem was too hard and two years is perfectly reasonable time frame for it. Maybe the team rushed too fast, had some good releases, but got buried by complexity and technical debt in the end. Speed in software development is an extremely complex entity. It is influenced by many things, often in a surprising way. In this article I'll try to share my thoughts about speed.

## Two Sides of Speed

Most people tend to think about Speed as a single entity, but it is not. There are two very different types of speed: Short-term speed (Sprint) and Long-term speed (Marathon). Sprint vs. Marathon is a perfect analogy here. In software development (and in running as well) you can't have both. Let's take some abstract effort unit, like point. Working full throttle in a Sprint mode you deliver 100 points per month. Here is my first argument:

You can't maintain a Sprint pace on a long product development distance.

Maybe you can maintain 100 pt/month pace 3-6 months, but it is extremely unlikely you can do that for a year. Moreover, recoil increases significantly with high-pace development. And some day you will regret everything.

![pace1](/content/uploads/2015/07/pace1.jpg)

At some point most of the developers will reach a "fuck it point" (red dot) and drop performance enormously.

Your goal is to run a very long distance (years) with the highest possible pace. That is what Marathon is about. You need endurance and evenness.

How to create software faster over a longer time stretch? That's a "1 million dollar" question. Most likely, the answer is unique for every company, but still we can construct a reasonable rough model that can be useful.

## Sprint, Marathon and... Intervals!

At first sight, there are just three options.

### Option 1. Extreme Sprint

You can run full speed, 12-14 hours/day, fueled by energetic drinks, caffeine, sugar and God knows what else. You can be an all-nighter, sleep for a few hours and spend minimum time on eating, washing, exercising, etc. I'll give you a month. Maybe three if you are in a perfect shape. The good thing about this mode is that everyone knows how bad it is. Burnout is rapid.

> **Sidenote**  
> I know a person who worked in this mode for a full year! He learnt many things and improved skills enormously, but it was not free. Most likely his current health problems were caused by this Extreme Sprint mode. Is it a good idea to trade health for experience? I don’t think so.

### Option 2. Moderate Sprint

You can work 8-10 hours/day, squeezing every drop of productivity. No small talks, no sport activities at work, no fun. Some companies do nothing to make work interesting, challenging and fun. Projects are always late and everybody is always under pressure. Unfortunately, this mode can last for years. People can get used to it and don’t notice how miserable they are. They try to find compensation at home with families and hobbies. That is a real danger, since after several months of such work productivity drops and nobody notices. It may take several years to think deep about yourself and have some insights.

### Option 3. Marathon

This mode looks optimal. You do your best working 6-8 hours/day, find time to relax and exercise. You don't catch every single minute and have the luxury to think about a problem for some time. No rush to push things out of the door RIGHT NOW! That sounds good. However, many managers are not satisfied with Marathon pace. They want to deliver things faster. I believe this pure mode is quite rare in reality. In most companies managers try to speed things up and do that in the most stupid way, using overtime, task pushing and “we are the heroes” motivation.

At the first sight, it looks like there is nothing more. But I think we have one more option. I had never heard about it, to be honest.

### Option 4. Intervals

I am not speaking about Iterative Development. In fact, iterative development can be equally applied to Moderate Sprint or Marathon modes. Interval development is when you mix modes. For a short period of time you can do Sprints, then switch to Marathon mode. In my opinion, good schedule can be:

1 month - Fast Pace Sprint  
3 months - Marathon  
1 month - Fast Pace Sprint  
...

![pace2](/content/uploads/2015/07/pace2.jpg)

Let me explain what I mean about Fast Pace Mode. In this mode the team (or a whole company) drops all secondary activities: all meetings about future, learning events, HR activities, etc. The team focuses on delivering value: writing code, testing, creating documentation and shipping.

Fast Pace Mode ends with relaxation week. This week dedicated to refactoring, discussions and thoughts about the future.

The benefit is clear — average pace will be higher than in Marathon mode. Fast Pace mode with a decent Marathon period afterward is not stressful. Moreover, it can be a motivational event, when team rolls up their sleeves, get shit done and ship fast. When you ship something — it makes you feel right. This is an accomplishment, a milestone. It is a narcotic. Maybe that’s why people can work in Extreme Speed mode for some time.

# Software Development Speed Model

Let's start from the overview. I'm going to frighten you right away. The picture definitely looks scary, but bear with me, I will explain every single bit of it. In the end you will have a powerful tool to analyze similar problems.

![map2](/content/uploads/2015/07/map2.jpg)

This diagram shows things and activities that affect development speed somehow. Green means that an activity increases speed. The more you have it, the better. Yellow indicates that some maximum exists. For example, you can accumulate technical debt and increase speed, but if you accumulate too much, it will slow you down significantly. Red shows things that slow down development, the less of them you have the better. Next. Green arrow indicates increasing effect. For example, focused work increases development speed.

![positive](/content/uploads/2015/07/positive.png)

Red arrow indicates decreasing effect. For example, better development skills decrease system complexity (good engineers create less complex systems).

![negative](/content/uploads/2015/07/negative.png)

Now you can look at the diagram and ask questions like: What increases development speed? What decreases it? What can we do to create software faster (and better!)? The model may be imperfect and that is OK. You are free to modify it.

Now I am going to explain various parts of the model, analyze them and provide some ideas about development speed. I hope it will be a good start to think about this problem deeper and generate more solutions. Let’s start.

# Skills and Experience

It is quite obvious that skills improve development speed. More skilled developers solve problems faster and create less complex solutions. Some say there can be 10x productivity difference between extremely skilled and less skilled developers. I don’t think it is a common case though.

![skills](/content/uploads/2015/07/skills.png)

The next trivial question is what can be done to increase developers’ skills? First, you can hire only skilled developers. That might work, but this model is not easily scalable. Skilled people tend to work on hard problems that demand their skills. How many companies in the world work on really hard problems? Not so many. On the other side, if your product is not rocket science, you don’t need teams full of PhD developers. So skill for any given company is different. A skilled developer at Google does not equal a skilled developer at some outsourcing company.

OK, you defined Skilled Developer for your company, but still struggle to find many of them. Scalability problem remains. So you have to hire not-so-skilled developers as well to grow. That is OK, but _it is absolutely required to hire people who like to learn new things_. How anyone will acquire skills if they don’t like to learn? Curiosity, lively mind, passion — these merits are major.

A company should provide anything it can to help people learn. Some options are below:

### Buy any book people ask for

Any company should have a [good library](https://www.targetprocess.com/blog/2014/02/our-library.html). Most great developers I know read a lot. There is no way to force people read books, but at least it should be extremely easy to go and grab a good book to read.

![library](/content/uploads/2015/07/library.jpg)

### Send people to conferences

Most people think that conferences are a source of new knowledge. Maybe, but I think about them as passion-drivers. Conferences motivate you to keep learning, keep trying new things and, in the best case, gives you some direction.

I like to visit conferences on topics that are new to me. For example, when I started to learn User Experience, I visited two large conferences. First one was especially useful, second one was not that good.

### Organize learning events

One of the best way to learn something is to write a book about the topic. Less extreme way is to prepare a presentation or a workshop. A company should organize internal conferences to boost this process. Not everyone is ready to speak in audience, but many will try. In our company [we have 2-day conferences every 6 months](https://www.targetprocess.com/blog/2013/03/time-for-tau-conf-5.html). There are no external speakers, all sessions are prepared by our team members.

![tau-conf](/content/uploads/2015/07/tau-conf.png)

Another good practice is provide a space for various community meet-ups. We have a small conference room for up to 80 people and are happy to shelter local UX community, .NET community and iOS community.

There are other ways to enable internal events for sure.

### Provide time to learn new things

That doesn’t sounds like a mandatory practice. Maybe it is not. Still if a company provides some free time exclusively dedicated to learning — that’s awesome. Famous 20% Google’s time is a good example (there are [rumors](http://www.huffingtonpost.com/2013/08/16/google-20-percent-time_n_3768586.html) that this practice was canceled already, but these rumors are not proved). At [Targetprocess](https://www.targetprocess.com/) we have Orange Fridays.

![orange-friday](/content/uploads/2015/07/orange-friday.jpg)

Each Friday is dedicated to personal projects or learning. Many people do Coursera courses, read articles, check new technologies. It is impossible to measure effectiveness of this practice, but there are many benefits:

  * In fact it means 4-day work weeks. At least the 5th day is not a usual working day.
  * It attracts people who like to learn, so it’s a big plus for hiring.
  * It is easier to retain people, since they have an option to try something new on their own.
  * People acquire new skills faster.

There is only one downside — it likely reduces overall development speed. People work one day a week less, which is a direct 20% hit on development speed. What is more important? It depends. If you are very close to release, tactically it is not wise to spend every Friday on education. If you are in a Marathon mode — it may be worth it.

![logo](/content/uploads/2015/07/logo-150x150.png)

_Shameless Ads_  
I work on Targetprocess — a pretty cool visual project management software. If you need an agile tool for your Scrum, Kanban or other projects, [give it a try](https://www.targetprocess.com/product).

 

 

 

### Help people to understand the domain better

Domain knowledge is crucial for any software developer. It helps to understand problems deeper, create better solutions faster and reduce re-work. It allows developers to spot bad solutions earlier. Without domain knowledge developers will blindly implement a solution provided by business analysts or product owners. With a good domain knowledge a developer can easily invent an excellent solution by himself or be a part of the UX team to brainstorm solutions.

Domain knowledge is especially important in product development. Life is short and it is hard to learn many domains in depth. So focus is a good thing in the end. You’d better find what drives you and get dirty.

OK. Now let’s talk about experience a bit.

## Experience

Work experience in most cases affects speed as well. A developer with 20 years of experience will typically solve problems faster than a developer with 5 years of experience (even if they somehow have equal skills). Note, however, that skill does not equal experience. You can have a lot of experience applying quite irrelevant skills and will not be able to solve most problems that the company has.

I personally think that **skills is the most influential factor in development speed improvement**. If you have a bunch of skilled developers, designers and testers — they have great chances to create something good. If you have novice developers only — almost nothing can help to speed development up.

Most companies have a wide range of problems: some of them are simple, some of them are challenging. Inexperienced developers are passionate about everything, almost any problem will bring some new knowledge to them. Experienced developers are more picky and it is better to give them problems of adequate complexity. So it is good to have wide range of skilled/experienced people inside a company, but the average skill level should be high. The good balance is unique for every company, but at least think about that problem.

# System Complexity

Software becomes more and more complex. 40 years ago there were dozens of technologies, now we have thousands. More LOC, modules, platforms. More everything.

![complexity](/content/uploads/2015/07/complexity.png)

 

Complexity is inevitable, that is how evolution works. Humans are much more complex than viruses (that doesn’t mean people survive better though). We can achieve more and more with complex software, so we have to live with that. Complexity will not go away. Developers should build as simple systems as possible, but not simpler.

Unnecessary complexity is a huge inhibitor. It is harder to add new features, to spot and fix bugs, it is harder to understand "what the hell is going on here!". As we discussed already, good skills allow people to build less complex systems. Respectively, novice developers tend to create fragile, overcomplicated solutions. For example, they like [Macaroni code](http://en.wikipedia.org/wiki/Spaghetti_code#Macaroni_code) and put everything into a single file: HTML, Javascript, ASP.NET and C# code — all in one! Single file may sound simpler than 4 files, but it’s much harder to modify and extend.

What makes software more complex?

## Technical Debt

As you may know, the Technical Debt concept was coined by Ward Cunningham. Technical Debt is a**deliberate** decision to implement not-the-best solution or write not-the-best code in order to release software faster. If you make bad solutions and are not aware of bad code you write — that’s not a technical debt, that’s just a bad architecture. It is not a debt if you are not aware that you took it.

Most people think that Technical Debt is always bad. It is not. The direct analogy with money reveals that debt is OK (sometimes). So it is OK to have **some** technical debt. Ward Cunningham himself supports this point of view:

> “I think borrowing money was a good idea. I think rushing software out the door to get some experience with it was a good idea.”

Technical debt can increase speed in a short run, but it adds to system complexity and that slows you down. There’s always a tradeoff to be aware of. How to deal with technical debt? First, it should be tracked somehow. Every decision about technical debt should be documented as a user story or something similar. That helps to understand how much you borrowed already. At some point you may wonder “Why the hell do we mark time?” But looking into huge backlog full of user stories with “technical debt” tag it is clear what went wrong. At this point the only option is to stop and pay the debt back. With interest.

Second, every decision about borrowing should be thought through. It is easy and appealing for a Product Owner to say “hey, we need this feature in 2 weeks, cut corners, folks”. Every single good developer is fully responsible for explaining all consequences this decision will lead to. It is your job, as a software developer, to provide argumentation and defend good architecture. Finally, you will have an agreement, but it is much better to have a deliberate decision.

Third, technical debt should be reduced via refactoring or full re-write. These activities can be periodic (scheduled) or ad-hoc.

Steve McConnell [provides an amazing reasoning](http://www.construx.com/10x_Software_Development/Technical_Debt/) about technical debt

> “One of the important implications of technical debt is that it must be serviced, i.e., once you incur a debt there will be interest charges. If the debt grows large enough, eventually the company will spend more on servicing its debt than it invests in increasing the value of its other assets”

Can technical debt be quantified? [It seems yes](http://www.sig.eu/blobs/Research/Scientific%20publication/2011/icsews11mtdfull-p005-nugroho-1.pdf):

> Technical debt is the cost of repairing quality issues in software systems to achieve an ideal quality level.

The picture shows technical debt and its interest grow over time if not resolved. Growth can be fast or slow, depending on the debt accumulation velocity. Overall, there is always some technical debt in a system and it is economically impractical to have zero debt, it will slow delivery of new features. Henrik Kniberg has an interesting perspective on technical debt as well.

![technical-debt](/content/uploads/2015/07/technical-debt.jpg)

## Refactoring

Refactoring is a natural way to reduce system complexity and pay technical debt back. However, refactoring is not possible without automated tests. I can’t imagine any serious system without automated tests. Development without unit/integration tests is like crossing the burning bridge over a chasm. There is no way back. Large system without automated tests is practically doomed in the long run.

Automated tests give a warm feeling of confidence — you can change the code by tiny bits and keep the system functional. That is what refactoring is about. There are quite rare cases when you may not create automated tests:

  1. Non-production code (prototypes, quick scripts).
  2. You are 100% sure that there will be no modification in the code and nobody will support the solution after the release. In all other situations automated tests are really helpful.

If refactoring is so good, can we refactor all the time? Definitely not. _Refactoring is a non-value added activity_. You are not adding any business value when you refactor the system. You reduce complexity, pay technical debt back — yes, but customers gain nothing. Business value is generated by new code. Could we write perfect code and create perfect solutions with a single shot? I wish we could. But we can’t. Moreover, requirements change and initial decisions no longer fit. That’s why we have to iterate and refactor.

## Slow or Unstable Automatic Tests

Automatic Tests are great, but they can be a real pain in the ass. Imagine you have a huge system and it takes 24 hours to run automated tests. Refactoring is no longer fun. Yes, you’ll find out what went wrong and will be able to fix things, but the feedback cycle becomes too long. Minutes are great, hours are bearable, days… it almost ruins usefulness of automated tests.

Another bad case is test instability. “It runs on my machine” is a traditional excuse, but this argument is hardly acceptable. Unstable tests drive people crazy. Is the build red because we made a real mistake or is it red because of instability? Can we mark this build as “pink” and make the release?

We have both problems in Targetprocess, to be honest. Slow tests were partially solved by parallelization. Now we have 60 virtual servers that run all tests, but still tests execution takes about 90 minutes (including unit tests, integration tests and functional UI tests). We have implemented an internal system that integrates together Jenkins, Git and Targetprocess:

![buildboard](/content/uploads/2015/07/buildboard.jpg)

The test stability problem is extremely hard to solve. Some functional automated tests are quite unstable and it is hard to localize the root of the problem. We spent enormous amount of time on test stabilization and re-writing, but still we have some unstable tests.

System complexity makes automated testing harder and slows down all development even more. So there is a very nasty feedback loop here.

## Cowboy Coding

Many developers don’t like processes. Some of them do, but in general most of them enjoy freedom and dislike rules. Experienced developers understand that some rules are really required. Cowboy coders just ignore the development process and move forward as they want. That is not always bad. If you work alone or in a tiny team it is OK, but in any serious development team it will lead to more complexity and more chaos.

[Cowboy coders](http://c2.com/cgi/wiki?CowboyCoder) tend to cut corners and move forward as fast as possible. I was a cowboy coder. I loved to see an implemented solution and I tended to sacrifice code quality for that goal. Now I understand the importance of good engineering practices and all problems that “cowboy coding” style generates.

In any company with 20+ people there should be a defined development process. Extreme Programming, for example, is a highly disciplined process. It demands full energy and maximum attention, but it delivers great pace and code quality in the end.

# Short term boosts

Sometimes it is absolutely necessary to boost development in a short run. For example, you have an important expo or an important customer that insists on a release at a specific date. From a business point of view it may be OK to trade quality for speed.

You should understand that there is [no free lunch](http://en.wikipedia.org/wiki/There_ain't_no_such_thing_as_a_free_lunch). Short term speed boosts may lead to long term deceleration.

![passion](/content/uploads/2015/07/passion.png)

## Deadlines

A deadline sets a goal and in most cases this goal is to release new functionality. I have never heard about a deadline like “We absolutely have to pay 40% of all technical debt by June 13” or “We should beautify inner architecture by June 13”. Instead I have heard deadlines like “We should release v.3 by April 11. No delays accepted”. Deadlines impose time pressure. Time pressure forces us to focus on a deadline goal — functionality. We cut corners, write not so good code and test less. This leads to higher technical debt and more complexity. Pretty clear.

Moreover, deadlines often work as a switch that turns on “Get Shit Done” mode, like “we are the heroes! We will ship this release or f***g die!” GSD mode increases technical debt even more. So deadlines can be used for short boosts, but with a great care.

### Deadlines and Iterative Development

Now I will share a quite controversial thought for all people familiar with agile software development:**iterative development is a set of mini-deadlines**. Indeed, timebox means we have to complete a defined set of work by the end of an iteration. Think about that. Does it imply the same consequences as a big fat Deadline? Not really, but similar. If a team committed to 9 user stories in sprint #4, it tries to complete all of them. The right solution is to reduce scope and drop stories that can’t be completed with good quality. But Scrum, for example, demands commitment, thus applying psychological pressure. People start to cut corners. On a small scale for sure, but still. It is not always bad, as we already know, but it is good to be aware about this counterproductive side effect.

## Overtime

An obvious and easy (well...) way to increase overall productivity is to work more. By working more hours we can complete more stuff and release earlier. Right? Jason Fried thinks that this approach is totally wrong:

> “Not only is this workaholism unnecessary, it’s stupid. Working more doesn’t mean you care more or get more done. It just means you work more. Workaholics wind up creating more problems than they solve. First off, working like that just isn’t sustainable over time. When the burnout crash comes–and it will–it’ll hit that much harder.

The balanced vision states that some overtime is OK. When you are trying to speed up a release and ready to make the final spurt — it is fine to work 2-4 weeks with 20% overtimes. But in the long run this practice will fail and recoil is inevitable.

We don’t use overtimes at [Targetprocess](https://www.targetprocess.com/). Never. The only extremely rare exception is when we have our production servers down or some blocking bug live.

Klint Finley wrote a [very interesting and deep article about overtimes](http://devopsangle.com/2012/04/18/what-research-says-about-working-long-hours/). Check it out.

## Passion

Passion is good. Passionate people really care about their work. They do all they can to write good code, invent great solutions and move things forward. Every employer wants to have as many passionate people as possible.

Passion is not all-shiny though. Passionate people tend to work more and [have a hard time](http://programmers.stackexchange.com/questions/129412/are-passionate-programmers-more-prone-to-burnout-than-others) finding the work/life balance. [Burnout](http://tech.onthis.net/2011/06/16/top-10-symptoms-of-developer-burnout/) is real, so it is much better to keep going in a balanced state. Otherwise you may have health problems, [psychological problems](http://sd.jtimothyking.com/2009/04/17/depression-and-the-software-developer/), family problems and depression.

Passion is good, it speeds projects up, but it should be balanced by some non-work activities.

# Focused Work

How many interruptions you have every day? Software development demands deep concentration and focus. Programmers build huge models in their minds and every single interruption can break the model state, so it will take time to rebuild it.

Focused work cuts all wasteful activities and helps developers to dive into [flow](http://en.wikipedia.org/wiki/Flow_\(psychology\)). Let’s review what diverts people from focused state.

![focused-work](/content/uploads/2015/07/focused-work.png)

## Unstable Teams / People Rotation

It is quite unclear how team stability affects productivity. Intuitively, we may think that stable teams perform better. In this case our intuition is right. Research done by Rally states that:

> “Keeping a team intact for the long term resulted in 60% more productivity; teams were more predictable and responsive.”

Why is that? Every team has a life-cycle. [Tuckman defines 4 phases of a team development](http://en.wikipedia.org/wiki/Tuckman's_stages_of_group_development): Forming - Storming - Norming - Performing. It is obvious that a team is most productive in the last phase — performing. If you rotate team members, you break the team and all these phases will repeat again. And again. And again. In the worst case there are no such things as Norming and Performing phases, just ongoing storms caused by rotation.

It is interesting to think about [pair rotations in pair programming](http://lmsgoncalves.com/2013/09/09/enable-pair-programming-rotation/). Every day developers work in different pairs. Is it really good? We tried that at Targetprocess and it was awful. Now I understand why. Firstly, there are personal preferences and some people are extremely unproductive in some pairs. Secondly, it is hard to build a good relations fast when you rotate every day. In fact you lengthen all the 4 phases mentioned above and the true Performing phase may never happen. So I don’t like pairs rotation.

How stable teams perform in other areas? How about soccer? Here is a fascinating research [Stability and Performance in Football Teams](http://www.professormarkvanvugt.com/site-oud/publications/stabilityfootmvv.pdf) (pdf).The conclusion is pretty clear:

> “These findings reveal that stability fosters team performance in professional football, possibly through promoting cognitive and physical cooperation.”

![teams](/content/uploads/2015/07/teams.jpg)

About a year ago we decided to form four stable teams. They worked for three months and it was obvious that two teams were OK, but the other two teams didn’t jell and their productivity was average. We decided to re-form these two teams. Looking back it was a very good decision. Now all four teams are demonstrating good productivity in Norming phase, but it took several months to overcome Storming phase.

## Open Space

I don’t like open space. It’s really hard to focus when there is a constant buzz around. As we already discussed, stable teams are better. Stable teams are quite independent and not very large. In our company typical size of a team is 6 people. Communication inside this team is really dense, however, communication between various teams is not so intensive.

![work-relations](/content/uploads/2015/07/work-relations.png)

It means each team should have a separate room (with walls).

Here is a typical open space. Many people in large areas. You hear voices from all directions. People pass by, and you inevitably switch your attention for a tiny moment (people tend to pay attention to moving things, that’s from our old instincts). Phones ring. Somebody crunches a cookies wrapper. Hot discussions born and spread between tables. People greet each other right near your workplace. Sounds familiar? It is hard to concentrate here. The only way to focus is to put on your headphones and make the music loud... Louder... Very loud… OMFG! I will go and buy thouse [expensive noise cancelling headphones](http://www.bose.com/controller?url=/shop_online/headphones/noise_cancelling_headphones/quietcomfort_15/index.jsp). Right now!

![open-space](/content/uploads/2015/07/open-space.jpg)

Now [compare that to the small rooms for 6-8 people working together as a team](https://www.targetprocess.com/blog/2013/02/hello-new-office-bye-bye-old-office.html). Phones ring not so often. There are less voices around. Most talks are quite important to hear and [osmotic communication](http://alistair.cockburn.us/Osmotic+communication) works, finally. Whiteboards are right there on the walls and hot discussions are relevant and immediate.

![team-rooms](/content/uploads/2015/07/team-rooms.jpg)

I think this setup is the best. It is true that private office enables maximum focus. However, it breaks communication. People are lazy enough to not get up and go ask a question. If you can ask a question in a snap, that makes a big difference. On my opinion, **“team-size rooms” is just the best balance we can have**.

## IM/Skype/Notifications/etc

Messaging services and various notifications can be remorselessly named “focus suckers”. Something pops up in the right corner and you move the eyes to check it. Focus is lost. Red balloon appears on a Skype icon, and you struggle with a sense of urgency that annoys you and forces you to open the Skype and check the message. Focus is lost. I bet you don’t pay attention to these interruptions. They are small and chronic,_they are embedded into your daily flow_. The truth is these small interruptions are dangerous enough to transform a productive day to the unproductive one. You check, reply, try to focus, check again, reply again, try to focus — all you have in the end of the day is several replied emails, many skype discussions, few lines of code and endless attempts to focus.

How to fight that? When you are really going to focus and code something, quit Mail, quit Skype, shut down all notifications services. Is it vital to see a new reply in Twitter or a new status update on Facebook? I bet it is not. Shut’em down.

It sounds easy, but try to do that and you’ll find that habits are hard to change. Suddenly you want to ask something, launch Skype again, ask the question, don’t quit and get interrupted by new notifications. I know that for sure since I have this problem myself.

In our company we used Skype a lot. There were various chat groups. Every team has a chat. We have Company Wide chat, Product chat, Sales chat, Operations team chart, Support chat, UX chat, etc.

![skype](/content/uploads/2015/07/skype-300x256.png)

Looks like all of them are required, but the amount of messages is enormous. I don’t know how to solve this problem on a system level. We need all those communication channels, but we pay a high price of constant interruptions every day.

A great communication channel is very targeted. The best scenario is when a message is received by people that really need it they can react somehow. However, it is not so easy to define this group of people. More smaller targeted chats maybe will work better than several generic chats. Recently we switched to Slack. It has better notifications system and is less annoying, but still there is intrinsic burden caused by chats.

![slack](/content/uploads/2015/07/slack.jpg)

## Multi-tasking

There are two types of multi-tasking: when you are coding and talking by phone and when you have several tasks to complete and switch from one task to another. First type is an obviously bad thing. Second type is bad as well, but we still multi-task. I personally work on several tasks every day. I know I shouldn’t, but I have failed to focus better so far. Context switch kills productive time easily:

![multi-tasking](/content/uploads/2015/07/multi-tasking.jpg)

How to solve this problem? Context switching should be reduced to a minimum. The best scenario is to work on a single task till completion and only then switch to a new task. Easy to say, hard to follow. I think some tricks can help us here. There are scientific proofs that [meditation helps](http://faculty.washington.edu/wobbrock/pubs/gi-12.02.pdf) (pdf).

A viable alternative is to split work into chunks. I have heard many people achieve good results with[Pomodoro technique](http://pomodorotechnique.com/) (but I haven't tried it for myself so far).

# Re-work

Any re-work reduces development speed for sure. It is impossible to have zero re-work, but we can try to minimize it.

![re-work](/content/uploads/2015/07/re-work.png)

There are three main sources of re-work:

  * Bugs
  * Unclear Requirements
  * Wrong things completed

Let’s start from Bugs.

## Bugs

I can’t imagine software development without bugs. Developers don’t like to test their code and most of them [can’t be good at testing](http://qablog.practitest.com/2010/05/why-cant-developers-be-good-testers/). Bugs in development are inevitable and testers work cooperatively with developers to find them as early as possible and get them fixed.

It is important to find bugs earlier. In this case the developer has a fresh memory about the code and most likely will fix bugs fast. If you have a long testing cycle (more than a week), it can severely reduce bug fixing speed. One week is enough to forget some parts of the code and context switching will play its role.

Bugs found in production are the most expensive to fix. Usually you receive an email from a customer with some weird behavior, spend some time communicating, reproducing the bug and adding a bug into a backlog. Then someone prioritizes this bug, asks about more details. Then developers fix the bug, communicate with testers again, etc. There is a **huge overhead** caused by a simple fact that a bug was found in production.

## Unclear Requirements

Most bugs are caused by unclear requirements. Usually developers read the specification, ask questions and start implementation. Quite often there are unclear statements in the specification. Quite often developers don’t spot them. Quite often Product Owners are not available to answer questions right away, so developers have to make educated guesses. Quite often their guesses are wrong and lead to re-work. Let’s briefly touch the most obvious solutions.

### UX to Development transition

First, developers should understand a feature’s context. You can’t just throw them THE SPEC and wait for the final solution next month. Developers have to understand real problems that customers face and why these problems were solved as described in a specification. There are several ways to fix this issue.

![ux-dev](/content/uploads/2015/07/ux-dev.jpg)

  * Developers can participate in UX from day one. It will help them to understand how the business works and why the proposed solutions are good.
  * Every feature or user story can have a “kick start meeting”. The goal of the meeting is to bring everybody on the same page: Developers, Testers, Product Owner. Feature or user story is discussed in details. Possible failure cases reviewed, developers ask questions they have. We have such meetings and they work like a charm. Often a solution changes during a kick start meeting!
  * Write good specifications (impossible!).

### Specifications

Good specifications are rare. Obviously, good specifications help to understand the solution better, reduce the number of bugs, decreasing re-work and saving time.

I wrote a [large article discussing why many specifications suck and how to improve them](https://www.targetprocess.com/articles/visual-specifications.html). In a nutshell, there are various techniques to describe and explain solutions to people and visual techniques are the best in many cases. The chart below shows all these techniques. The X-axis shows time and effort required to create a specification. Obviously, a live prototype takes more effort than sketching. The Y-axis shows a technique value. Pseudo-narrative specifications are of low value, whereas the design and prototypes are very useful.

![specs](/content/uploads/2015/07/specs.jpg)

## Do the Right Things

Bugs are bad, but how about a feature nobody uses? Imagine that? All the time you spent designing, implementing and testing was a waste. I personally designed and implemented several features in Targetprocess that almost nobody used.

How to do the right things? There is no easy solution, it is hard to know for sure what customers really want. It is even harder to say what they will really use. Still there are several things you can do to understand customers needs and priorities better.

### Communication channels

Give customers extremely easy ways to provide feedback. It’s easy to find good services for that purpose, like UserVoice or Desk.com.

### Usage statistic

How do you know what feature is popular and what is not? With every feature implementation it is helpful to think about usage metrics. How do we know that feature was a success? How many people use it daily/weekly? These metrics will help to verify initial hypothesis like “we believe 50% of our users will use this feature every day”. Thus you will learn from mistakes and make smarter decisions in the future.

### Feature ranking model

How do you know what feature to work on next? Product Owner’s intuition likely is not the best way to choose that. [Simple linear models outperform experts](http://lesswrong.com/lw/3gv/statistical_prediction_rules_outperform_expert/), so use them. Create a simple model, rank features with the model, verify it on several features, correct it and then trust it. We spent several months on Feature Ranking model in Targetprocess. We reviewed various sources, discussed priorities, accumulated feedback from customers and finally created a good model everybody believes in.

When we added all features with all parameters and calculated scores it appeared that for most of them our intuition worked good enough, but there were several surprising features that popped on top. We discussed them and discovered some obscure properties that changed our vision about these features. I don’t want to go into much details here, just provide a formula:

    
    
    Feature Score =   30% * Selling Point
            + 15% * Usage Spread
            + 15% * Customers Votes
            + 15% * Feature Size
            + 15% * Pain
            + 10% * Usage Frequency
        

Maximum Feature Score is 100%. It appeared, that two major features we were working on are in the middle of the list. They are not as important as we thought. Nevertheless, we completed these features. You know what? Initial perception of these features is quite cold. Not so many people actually use them as we expected. Now we are working on top features from the list and I believe they will be much more welcomed by customers.

### UX feedback

It is worth it to receive feedback on all major features and UX changes from customers. Create prototypes, share sketches, perform A/B testing, accumulate data and analyze it.

I’d say if you solve this problem, you will decrease re-work enormously.

# More people / More development teams

Large companies always work faster and release faster. Right? Not exactly. Small companies have better unit speed, while large companies have better overall speed, but usually it costs them. Let’s take a team (6 people) and put it into two different companies. I guarantee this team will work faster in a small company. But in a large company there are dozens of teams, so overall development output will be higher.

![hr](/content/uploads/2015/07/hr.png)

It is better to grow trying to keep the unit speed high. More people means more coordination, more meetings, more waste.

## Hiring

New people form new development teams and increase development speed in the long run. However, this process inevitably decreases current development speed. First, some developers will be distracted by technical interviews. Assuming you are trying to hire good people, there will be many interviews and most of them will lead to nothing. I think a single hire will take 10-40 hours of interviews.

Second, new people should be mentored. Somebody should help them to understand how things are running here. This process takes 1-3 months and during this time a developer is not very productive. I believe people start to work full throttle after 6 months only.

What does it mean? If you have an important tight deadline (let’s say, 6 month ahead) — don’t hire, it will slow you down. If you have no deadlines and are ready to slow down today to speed up tomorrow — then hire.

Interesting questions to think about are: Can we hire new people without developer distraction? Can we replace technical interviews with something else? How to spend less time on mentoring, but have the same result?

## Work coordination

Large companies are not very efficient. More people demand more coordination. Usually the solution is more management levels, deeper hierarchy, more meetings, more political games, less productive time and average development speed.

I’m not fond of deep hierarchies. I like networks and [flat organizations](http://en.wikipedia.org/wiki/Flat_organization) with autonomous cross-functional teams.

In Targetprocess we have 5 development teams that are completely independent. Every team includes feature owner, developers, testers and designers (often they are shared). The team is fully responsible for the feature implementation and make all important decisions about the feature.

The problem is that a product itself should be modular enough to support independent teams. There should be minimum relations between modules, otherwise integration will be an issue. Targetprocess is not there yet.

> **Sidenote**  
> Company architecture will be replicated in product architecture. I’m curious to compare products architectures in IBM and Atlassian, for example. Does IBM use deep inheritance models? Does Atlassian rely on association and composition more? It may happen, that flexible and flat companies create flexible products. If this is the case, then a company structure has huge influence on a product success.

# Waste and non-value added activities

We’ve talked about distractions like Facebook or Skype. However, there are many dangerous activities that look like real work, but don’t generate any value in the end.

![waste](/content/uploads/2015/07/waste.png)

## Meetings

Most meetings suck. Here is a good meeting test I read in some book:

> Think about how often you have stated "Wow. That was an awesome meeting!"

I bet it was not so often. Larger companies have more meetings. Small companies can live with zero meetings. Every single meeting can be wasteful. Daily stand-up meeting? Sure. UX meeting? Why not. I can easily imagine a completely wasteful daily meeting where everybody do status reporting and nobody cares what other people talk about. I attended many UX meetings that were painfully boring and generated nothing.

There are many books about efficient meetings. You know what? They really work. Every meeting should have an agenda, prepared participants, good facilitation, honest and open communication and clear results.

We can’t drop meetings completely, good meetings are fun and helpful. It is an activity where you can discuss problems with other people, focused and fully immersed into a discussion. I think meetings suck at idea generation, but they are useful for idea sifting. [Brainstorming is not the best way to invent new ideas](http://davebirss.wordpress.com/2008/06/23/10-reasons-why-brainstorming-sucks/). I believe in solitude, focused thinking and time.

To generate something new you have to spend time and think.

It is naive to believe you can go to a meeting unprepared and solve a problem.

## Sport at Work

I hope more and more companies trust people. I hope it is rare to see a scene like that now:

_Manager cames to a kitchen at 11 am and see two developers sipping coffee, chatting with each other, smiling and laughing of something. Manager becomes purple and shout “Why the hell you are doing here? We have a deadline this Friday!” Developers drop cups in a hurry and walk away._

Horrible... Work should not be a boring place where people code, test and release things. Creative work demands physical activities, pauses and talks. It is good to have a table tennis, trainers, yoga/dancing/whatever classes right in the office (and a shower of course). Exercises help to drop stress level and help people to be more productive in the end.

Do you really think people will completely exchange work for tennis, kicker or something else? If so, you have serious problems. Maybe they are bored to death and fed up with tasks they had last month. Or maybe you hired the wrong people. Anyway, this is a manifestation of something wrong happening there.

So sport at work is good. You may think about this time as a waste, but it is not.

## Learning at Work

Every software development company wants to have people who learn new things. Nonetheless, not so many companies provide opportunities to learn new things. We’ve already discussed learning in previous sections, but some companies believe that learning at work is a waste. Indeed it doesn’t generate any value, so this activity is non-value added. In software development we should focus on “work smarter, not harder” and from this perspective learning at work becomes quite intriguing.

Can we measure the outcome of Orange Fridays? Books? Conferences? Side projects? It’s really hard. The outcome is long term (years). And there is no obvious model to quantify knowledge into money.

# Work / Life balance

This section will be short. We mentioned burnout already. Software development is an activity you will think about all the time. When you have a complex problem in the software, you are thinking about it everywhere. It suddenly pops up when you are walking with your girlfriend, some thoughts appear in a shower and your brain even tries to reinforce the problem in, well, the most inappropriate moments. It is important to learn how to switch off. Sport, traveling, yoga and hobbies are the best candidates.

![work-life](/content/uploads/2015/07/work-life.png)

Companies should encourage people to have some hobbies and support them. This is true for sport activities as well.

Zero overtime rules should be advertised by top managers. If you work harder and harder at some point you will work dumber and dumber.

# Wrap-Up

I think it will be helpful to stress some points.

**Software development pace / productivity / speed is a complex, interdependent and multifaceted concept**. It has no easy solution. You can’t shout at people “work faster!” You can’t blindly cut corners and focus on value added activities only. The only solution is to think deeply about the company, development processes, people, tools, etc. Build a model and think.

I am curious to develop the Interval Development concept further. It feels very intriguing to me and may very well be just the right balance of good pace and good endurance. Marathon and Moderate Sprints mix analogy opens many new directions to explore.

And some words about the model.

![map](/content/uploads/2015/07/map-1024x644.jpg)

It is interesting to add weights to the model. Some activities affect speed greatly, while other not so much. Every company has unique weights, but if we can define them somehow we can focus on the most important things.

Thank you for your time.

