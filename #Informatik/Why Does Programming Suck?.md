# Why Does Programming Suck?

_Captured: 2016-03-10 at 20:04 from [medium.com](https://medium.com/@luisobo/why-does-programming-suck-6b253ebfc607#.he26lts8p)_

![](https://cdn-images-1.medium.com/max/2000/1*n2cbLO47aGNnO5qduRWYsQ.png)

I'm a software developer and since the very beginning I've always had mixed feelings about programming. On one hand, you can accomplish so much with it. On the other, it's a completely frustrating tool to use--not only is the experience horrible, the worst part is feeling that much more could be accomplished if programming didn't suck.

In this text I want to dig deep into these problems, try to find their sources and see if there is anything we can do. Spoiler: there is.

Please, read this text with a critical eye. I'd love to hear constructive feedback or counterarguments; I'd be very interested in continuing a thorough discussion about this topic.

### Programming, not a solved problem

Before we dig into the "whys", we have to agree that programming sucks. Let's take a quick look at the dirty laundry of programming.

It costs a lot of time and money to make software. Software bugs costs $320 billion a year[1] and programmers spend half of their time finding and fixing bugs[1].

Hiring developers is an extremely difficult task. Learning to program is ridiculously difficult as well.

There is an obvious lack of diversity in our industry. The fact that software is taking over the world makes this claim extra concerning.

The nature of software today forces users to cope with whatever crap we come up with. If a user doesn't like my software, the most they can do is stop using it. There is no user-friendly way of making two programs interoperate.

The direct cause of these problems is the amount of complexity that us developers have to deal with, a lot of which is caused by programming itself. Analyzing these sources of complexity can, hopefully, reveal potential ways of fixing the problems described above. Let's take a look at some of the most common ones.

Lots of rework happens because of miscommunications with the user. Other times, the user doesn't fully understand their problem (there's not much we can do about this), but all the back and forth it requires add up to a lot of extra work and complexity.

Evolving software is at the core of programming--anywhere from 50 to 90% of the cost of building software goes towards maintaining it after the first release (adding features, fixing bugs, system updates, etc). This number is going up, thanks to updates delivered over the internet, like SaaS products or even car companies like Tesla. All good, but we are not equipped to perform all these changes cheaply and safely, and we end up having to spend a lot of time ensuring that newer versions of the software do not break the old ones (API versioning, database migrations, etc).

Since evolving software is so expensive, we try to make it cheaper by guessing the future. We add extra complexity now hoping that it will be useful in the future. Turns out, we are horrible at predicting the future and we end up discarding that extra complexity. Even in the cases where we guessed right, we had to deal with that extra complexity despite the fact we didn't have a use for it at the time.

Our tools don't make a good separation of essential and accidental complexity[2]--we are forced to crystalize the essential parts of our programs in a programming language and make them coexist with irrelevant, usually platform-specific code (accidental complexity). This mix proposes two problems. First, when you make a change to the essential part of your app you may break some inessential parts and viceversa. Second, it kills the option of reusing the essential parts of your code with other platforms (iOS, Android, web, etc). This forces us to duplicate code between each platform. A clear and strict separation between essential and accidental complexities would solve these problems.

These problems have been around since the beginning. We have come up with some workarounds, heuristics and palliative measures for these problems, but those are not _solutions_. **Programming is not a solved problem. **We cannot take these hacks as solutions because then we stop questioning things. If we stop questioning things, we risk turning these hacks into dogma[3]. For example, Agile has improved software development in many ways, but thinking that Agile is the definitive solution to our problems would be dangerous--we would stop looking for better ways. Another example; code. We have been writing code since the beginning. If we assume that typing code is _the way_ to program, we will never look for better alternatives.

As we've seen, programming has a lot of dirty laundry. If we want to tackle those problems we should question _everything._

### What happened!?

#### How did we get here?

Well, let's take a look. The idea here is to analyze what went wrong, what thing or things lead to this point, so later on we can think about a solution that will eradicate the different causes and amplify the value-generating powers of programming. What a life!

At the center of software is the computer--once machines that would fill entire rooms and now invisible devices of the size of your nail.

But let's dial it back, way back. A few thousand years ago, we created some cool gadgets to help us with our day-to-day problems. We had trouble counting and we invented the abacus. We wanted to keep tabs on the time and we got ourselves a clock. Predicting the location of various celestial bodies like the the sun? Not a problem, we made the Astrolabe. We struggled with math? Pascal came up with a mechanical calculator to make math less error-prone and faster[4].

All nice and cool -- single-purpose mechanical devices created for a specific need. It went something like this: we had a problem, we acknowledged our own limitations and we came up with a device that would help us solve the problem. It was all great and good.

#### The computer, the ultimate calculator

Around 1830, Charles Babbage, a mathematician and inventor among other things, was working on one of these single-purpose mechanical devices. The problem at hand was math, which was to slow and error-prone. To give you an idea, it involved _manually_ looking up values in _manually_ precomputed tables. Babbage was working on the Difference Engine, a machine meant to solve polynomial functions[5] when he realized could he turn it into a general-purpose math solver[6], the Analytical Engine, that would be configurable or programmable via punched cards. It had an arithmetic-logic unit, conditional branching, loop and memory[7], the same things we use today to make programs. The Analytical Engine was the first design of a Turing-complete machine--with this machine we could solve any problem, we didn't have to deal with many single-purpose devices or their physical limitations. One machine to rule them all. All the computations imaginable were solvable by this machine with the right configuration, with the right punched cards, with the right _software. _How cool is that?

Babbage's motivation to work in this field was to allow people to do math fast and without errors[8]. He even starts a text describing the Analytical Engine with the following quote:

> "Man wrongs, and Time avenges._"_

> _-- Charles Babbage on the Analytical Engine[6]_

which means quite literally "Mistakes? Ain't nobody got time for that".

Babbage' was focused on speed. He was obsessed with how to carry the tens as fast as possible:

> "The most important part of the Analytical Engine was undoubtedly the mechanical method of carrying the tens. On this I laboured incessantly, each succeeding improvement advancing me a step or two. The difficulty did not consist so much in the more or less complexity of the contrivance as in the reduction of the **time**required to effect the carriage."

In case you are one of those horrible people who skip quotes when reading, go back and read the damn quote ಠ_ಠ

Point being: he was focused on doing math fast and without errors. He didn't care how complex the machine was as long as it accomplished that. That is the opposite way in which we approach building software now; we try to make it simple first then try to make it fast _only_ if it is slow, which does not happen often. In programming we now say that _"premature optimization is the root of all evil"_. Well, check this out: Babbage did the first space vs time optimization ever _while inventing the computer:_

> "It is impossible to construct machinery occupying unlimited space; but it is possible to construct finite machinery, and to use it through unlimited time. It is this substitution of the infinity of time for the infinity of space which I have made use of, to limit the size of the engine and yet to retain its unlimited power."

He made the first tradeoffs for the software industry but he was thinking about automating math, not about programming.

Babbage was not pursuing simplicity, no wonder we are in this mess! He even created the first: "//TODO: this works for now, fix later":

> "I propose in the Engine I am constructing to have places for only a thousand constants, because I think it will be more than sufficient. But if it were required to have ten, or even a hundred times that number, it would be quite possible to make it, such is the simplicity of its structure of that portion of the Engine."

Cool story, Babbage.

These may have been the first signs that the computer is a leaky abstraction[9]. I mean, it had to be. After all, he was building a finite physical device to represent the infinite world of math. But my point is, when facing tradeoffs, he made decisions based on _his_ vision, doing math fast, and not on _our_ current vision, sharing photos with friends at scale or automating payroll. Just saying. This begs the question, is there another set of tradeoffs that would benefit our current use cases better? Is there another hardware, general-purpose or not, that would fit our needs more precisely while being cheaper to program?

The ease or simplicity of programming was never taken into account either, after all, the Analytical Engine, was originally conceived to do just math so the "programming language" was focused on doing math operations. At the same time, as medium for programs Babbage picked the punched card, which was not conceived for that purpose either. Punched cards originated in the textile industry for creating patterns in fabric. Moreoever, he had to make conscious tradeoffs and make the "programming language" more complicated in order to simplify the machine itself[10].

This trend of making hardware faster at the expense of making programming harder continued over the decades. In 1972 Dijkstra wrote:

> "[…] in one or two respects modern machinery is basically more difficult to handle than the old machinery. Firstly, we have got the I/O interrupts, occurring at unpredictable and irreproducible moments; compared with the old sequential machine that pretended to be a fully deterministic automaton, this has been a dramatic change and many a systems programmer's grey hair bears witness to the fact that we should not talk lightly about the logical problems created by that feature. Secondly, we have got machines equipped with multi-level stores, presenting us problems of management strategy that, in spite of the extensive literature on the subject, still remain rather elusive. So much for the added complication due to structural changes of the actual machines."

> _-- Dijkstra, The Humble Programmer[11]_

Since the origin of the computer, with Babbage and his tradeoffs for automating math, to 1972 we have been focusing on making the hardware faster, even at the expense of making programming more complicated.

And this trend continues today: when hardware designers couldn't figure out how to make a single processor faster they started making chips with multiple processors in them, putting the burden on the programmer. Now we have to write code that takes advantage of this parallelism, which is a huge source of accidental complexity.

But Babbage didn't know about any of this. He was operating the same way we operated for thousands of years before: he had a problem, acknowledged our limitations and he created a solution. He went from problem (math is slow and error prone) to the solution (automate math). Very nice.

But as part of this process he was making the decisions that were best for him and not for you and I. It was when we decided to use the computer for something it was not designed for that things started to go haywire.

#### Cool but what if…

Ada Lovelace, known as the first programmer, realized while studying the Analytic Engine that we could do things other than math, as long as we represented those things with numbers. And so, we started the business of trying to find the underlying mathematical representation of things, even though some things do not have a clear math representation. I believe this is the tipping point. From this point on we were not going from problem to solution anymore. We flipped this relationship. We started going from solution to problem. "I can do math really fast, how can I represent arbitrary problems as math so I can solve them really quickly?". Or in more general terms: "I have a computer, what problems could I solve with it?" (As a side note, the tech industry nowadays is the perfect representation of this backwards way of operating).

![](https://cdn-images-1.medium.com/max/800/1*K9pO1sC5JuM5dnVXYGFtWw.png)

> _With a solution in our hands, we started looking for problems to solve. The arrow now points in the wrong direction._

Another direct consequence of Babbage and Ada's work is that we no longer had to build mechanical solutions for each of our problems, like the abacus, the clock, etc. Solutions lost their physical nature. With a general-purpose machine, the solution was the stack of punched cards, the software, if you will. However, the physical nature of those pre-computer mechanical solutions had their advantages; because they belonged to the physical world, and we could use our senses to understand them--we could see them, touch them, even hear them. When something went wrong, we could find the source of the problem easily by using our senses. Debugging physical solutions was (and still is) easier. With the computer, we made a big tradeoff: we got the ability to solve more complex problems but we had to give up the most important tool known to humans for understanding--our senses. We could no longer perceive our solutions, we could only reason about them.

**The computer shifted the complexity of our solutions from the world of atoms to the world of ideas.** Building solutions was not longer about of assembling devices, it was about assembling ideas.

This shift created a whole new breed of problems. Printers, screens, keyboards, the mouse, user interfaces, debuggers… all of these are attempts to open a window to the world of ideas where software operates. This is a lot of effort just to restore our senses as a tool for understanding. See, now we are in the business of solving problems that were _caused_ by our initial solution: the computer--this is the definition of accidental complexity, which we're trying to eliminate.

To be fair, creating a physical device had its own accidental complexity-materials, manufacturing, physics, but check this out: first, we had thousands of years of experience with the physical world. Second, and most importantly, the fundamentals behind all the problems in the physical world were not human-made, while everything behind software is, indeed, human-made:

> Software people are not alone in facing complexity. Physics deals with terribly complex objects even at the "fundamental" particle level. The physicist labors on, however, in a firm faith that there are unifying principles to be found, whether in quarks or in unified field theories. Einstein argued that there must be simplified explanations of nature, because God is not capricious or arbitrary.

> No such faith comforts the software engineer. Much of the complexity that he must master is arbitrary complexity, forced without rhyme or reason by the many human institutions and systems to which his interfaces must conform. These differ from interface to interface, and from time to time, not because of necessity but only because they were designed by different people, rather than by God.

> _- Fred Brooks, No Silver Bullet[7]_

Furthermore, even the supposed advantage that we got from that tradeoff -- i.e. the ability to solve more complex problems -- was a double-edged sword. Yes, our solutions could grow bigger and be more complex, but they could also grow so big and complex that no human could understand them (hello non-trivial iOS app. Hello Artificial Intelligence 👋).

With a general-purpose machine on our hands, we started approaching problems with a preconceived solution in mind. We don't start designing solutions from the perspective of the problem anymore. Having a preconceived solution in mind fundamentally limits our solution space. What's more dangerous, this way of operating carries the risk of never questioning that solution at all. **We take the computer and programming as dogma. (**No wonder in this field there are holy wars about the most insignificant things)

Now, with our problem-solving process in reverse and a machine that can only understand numbers, all we do is try to find the underlying math in the problems we want to tackle so we can feed them to a computer. Some things have a good and simple mathematical representation, but others don't, like text (example later), speech or human thought. The problem comes when we try to _invent_ mathematical representations and they don't properly fit non-mathematical things (hello bugs! 👋).

In short, in order to solve our current ordinary problems -- like talking to people, sharing photos or requesting a cab -- **we are relying on a machine that was originally conceived for dealing exclusively with math. **But we figured out a sloppy way of representing non-mathematical concepts with numbers and used it to solve our ordinary problems. If I were to tell you to create a social network, a ride-sharing app or a website to share photos and all I handed you was a very fast calculator you'd laugh, but that's pretty much what we're doing here.

And so, misusing a machine built to do math, that was prematurely optimized, built without simplicity in mind, inspired by the textile industry, backed by no underlying fundamental laws, with no way for us to understand it, that could generate more complexity than we could possibly embrace and armed with zero experience and a completely backwards approach towards problem-solving, we started the business of dealing with accidental complexity in the name shipping features--known today as programming…

…and a shit-ton of wonderful things popped from the other end. Damn it.

#### Keep on stackin'

Since programming was so damn useful we caved and started dealing with the accidental complexity. Over the years, when we tried to solve actual problems with computers, we found some inconveniences. _"Ugh, punched cards are such a hassle"._ _"Ugh, machine code is so error-prone". _So we came up with ad-hoc solutions to those problems. We invented assembly code. This way, instead of writing "100101 0100 0111", that means " 4 + 7" you'd write "ADD 4 7". Hey, much nicer huh? Thanks to these types of languages, we were able to tackle more complex problems and create more complex programs.

But with that ability also came more sources of accidental complexity. To put it bluntly, we were giving ourselves more rope to hang ourselves with.

We encountered some other problems and we created some more ad-hoc solutions for these too. "_Ugh, it is so hard to understand the flow a program written in assembly". _Not to worry my friend, here is FORTRAN. We invented a high-level language that was easier for humans to understand. Same deal, easier to understand means easier to create more complex programs, which means more trouble for our limited minds. All well intended, but by solving a problem we created others.

![](https://cdn-images-1.medium.com/max/600/1*-nU6rHqBTKSpIw-WDBH0Og.png)

> _You'd be angry too_

We kept stacking sloppy solutions on top of each other but that only created more complexity and problems. In fact, I picture programmers as little people standing on top of a stack of poker chips so tall that we can't see the ground, clouds around us and all. These poker chips (ad-hoc solutions) are not perfectly shaped and the whole tower wobbles so much that a regular person would puke their guts out, we are kinda used to it, though. Every time we see an imperfection with the poker chip right below our feet we put a new chip on top of it trying to cover the problem and hoping that it will be the last poker chip we will ever add to the stack, even though we subconsciously know we are lying to ourselves. And while on the top of this wobbly stack of imperfect poker chips we try to solve some of the most complicated problems known to humanity.

One of the the most blatant examples I can think of is how we represent text using a computer. Letters don't have a mathematical origin but we needed to manipulate text with computers so, ¯\\_(ツ)_/¯ we shoehorned it in there. With our limited and simplistic minds, we went ahead and gave one number to each letter. Today the letter 'a' is represented by the number 97 and 'z' by 122 in the computer you are using right now. But, turns out that there are characters other than letters, digits and symbols. Other cultures have radically different writing systems where a character has multiple variations or different orders and all sort of things that do not fit the original one-letter- one-number model. This problem is far from solved, we are even inventing new characters today: 😩😡😂😭😭😭 or 🙄🤓🖕 or new variations: 💪🏿🤘🏼🖕🏽 (chances are you can't see all those emoji). Something so fundamental to modern computing like text does not have a clear mapping to our computers. This mismatch is a huge source of accidental complexity[12] and you, the user, are the one paying for that. Image how bad it is for things that aren't as basic as text.

And what do we do to mitigate these type of problems? We come up with (ever-expanding and ever-changing) standards! This is how it goes:

![](https://cdn-images-1.medium.com/max/800/1*9nMBMt-OugnruBr_M-WuEQ.png)

> _"Fortunately, the charging one has been solved now that we've all standardized on mini-USB. Or is it micro-USB? Shit" Source:_

In programming we have multiple solutions for a given problem, backed by multiple standards. Now the problem is which one to pick. Sometimes for political reasons, different vendors tend to use different standards. We have to translate between them in order to make machines interoperate or to target multiple platforms, like building an app for iOS and Android. All this leads full circle to the conversation depicted above.

An example of this happened a couple of weeks ago right in front of my eyes. GraphQL is an open source query language released by Facebook looking to unify the many different sources of data in a backend with a simple query language (GraphQL is a good example of a poker chip looking to hide the chips below). The programmer in me is actually very excited about it. Well, a developer didn't like some part of it so he forked the project and created his own version that'd satisfy his own needs:

And again, for a given problem we have multiple solutions. I want to be clear, we can't really blame the author of the fork, he may be trying to ship a feature. Maybe he even tries to contribute his changes back and it's all good. But maybe, and this happens, Facebook won't accept those changes because they don't consider them to be the right thing for their project. Chances are, that sooner rather than later, we will need another solution, a level above GraphQL, that encapsulates all the different dialects of GraphQL, just to have the problem repeat at that level as well.

You know where this is going. Either as a workaround for a leaky abstraction, because of politics or because the wind blows, we keep stacking more sloppy and ad-hoc solutions on top of each other without asking ourselves whether that is the right thing to do, we keep adding poker chips to the stack without asking ourselves where the stack should be taking us. _"Ugh, sharing code with other developers is so tedious, let me create a dependency manager"_. In the tiny context of "sharing code with other developers", a dependency manager may be considered a great solution, but is it a good solution in the global context of programming, or even better, in the global context of solving problems? **Are any of the ad-hoc solutions that we have been stacking for the past few decades good in the big scheme of things?**

_"Wait, do we have a big scheme of things?"_

### No end game

**No, we don't have a big scheme of things!** And that is exactly our problem. Since the very beginning of computers we have been in this vicious circle, exclusively solving what was right in front of our noses, the poker chips right below our feet--problems that _we_ created in the first place--without ever questioning if those were the right problems to solve to begin with. Without ever questioning the context in which the problem was presented. Without ever questioning whether the solutions we came up with were a step in the right direction, following the right path that would get us closer to the overall end goal.

Of course we have never questioned any of this. **We don't have a direction, a path or an overall goal for programming!**

We are chasing our own tail while complaining about it while making our tails more difficult to chase while being unaware of this situation. This is what progress in programming looks like.

Let me ask you this: **What would programming be to you in an ideal world?**

We don't know! We've never asked ourselves this question!

We've been so excited with the possibilities that we haven't weighed the caveats. We manage them in an ad-hoc fashion, but don't take them into consideration as a problem of their own right because we see programming as a solution -- not a problem.

And this goes on today--the web is a great example. The web brings so many wonderful things to the table that we can't see how horrible and ill-defined the technology stack powering it is. If something as important as the web were done right, we could be doing so much more! It could be so much better, so much cheaper and so much more accessible for everyone! Now, the programmers who have to deal with that mess need to go back and waste time fixing the web and, because evolvability was never take into account, we can only make very tiny, local and incremental steps since we cannot stop the system.

Truth is, defining a goal for the progress of programming would be liberating -- every programmer out there would have something to shoot for and a frame of reference for whether his or her ad-hoc solutions, libraries, frameworks, languages or tools were inline with that end goal.

But without an end goal, of course you have millions of developers releasing Javascript frameworks every day--everyone is pulling in whatever direction they may consider good. Innovation in programming is a big playground, with shiny things to play with, puzzles to solve, no rules, no schedules, no purpose--just play. This results in many more problems, like the huge sea of code impossible to navigate formed by open source libraries, frameworks, bug reports, deployment tools… for God's sake, there are even companies built around these things! And of course, this gives us more rope to hang ourselves with. _"Which JSON parsing library should I pick? Forget it, I'll make my own"._

This problem is aggravated by the following fact: developers secretly love all the mess they are in, we are like pigs in the mud. We won't tell you, but all these complex, yet uninteresting puzzles where we spend most of our time? Those are a lot of fun to solve! Since the beginning of programming, the role of the programmer was relegated to fit the impossible into the slow and clunky hardware: _"And in those days many a clever programmer derived an immense intellectual satisfaction from the cunning tricks by means of which he contrived to squeeze the impossible into the constraints of his equipment"_[11]. That was Dijkstra in 1972--little has changed since then. We may not know this consciously but it is not in our best interest to solve the problem of programming, we want to play.

On top of it, to improve this situation, programmers would be the only ones able to participate in the solution. Well, let's add electrical engineers for good measure. Never mind that users are the ones paying the consequences, there is nothing they can do. Users are going to have to wait until we decided we've had enough fun, if that ever happens.

All right, all right. I may make it sound like an evil plot, where programmers are capricious people who deliberately enjoy cracking puzzles while ruining your life. Not true, we don't do it _deliberately_. Really, we are not even aware of the mess we're in! For the most part, all we see are the local problems that exist right in front of our noses and nothing else. _"XML sucks, let's do JSON instead". _We don't perceive them as part of a larger problem. All we see is the poker chip right below our feet and we are not aware of the zillions of chips right below that one. We solve each local problem in order to continue shipping features to you. As an _industry_ we have never asked ourselves, _"are data exchange formats necessary at all?" _or _"are any of the problems I deal on a daily basis essential to programing?" or "instead of solving this local problem, could I just get rid of the problem to begin with?". _We will never ask ourselves these questions because we are busy shipping features to our users. But the fact that none of this is done deliberately does not make it less of a problem, it just suggests that we are not evil.

In any case, we can't really blame the developer trying to solve a piece of accidental complexity in an ad-hoc manner. Nobody hired her to "solve programming", she was trying to do her job and release a feature to users. We can't blame the company trying to make a profit, companies are created for that purpose and this seems to be a lucrative opportunity. We got to this point _organically_, over the decades, one little decision after another, and we never realized we were _creating_ a big problem due to our limited perception and scope. Just like frogs being slowly boiled alive. _Ribbit!_ 🐸[13]

From the perspective of a developer, one more programming language or one more javascript library or framework is a _solution_ to a (somewhat local) problem, not a _problem_ in and of itself, per se. A single developer would rarely perceive any negative consequences in his or her lifespan, at least consequences big enough to make him or her aware of the magnitude of the problem. You'd have to zoom out several decades to see a strong relationship between cause and consequence. Those consequences, like bugs or the ridiculous amount of time it takes to build software, are diluted in our day to day and have been engrained in our society little by little. Moreover, with those problems came huge gains in technological advancements, so we never paid attention to the bad side of things. Now, it's been five decades and everyone has a smartphone in their pocket. The cause of our trouble is deeply engrained in our lives, there's no way we could roll that back (not that we should, just that we couldn't if we wanted to).

These perception problems draw parallels to other big-scale problems we face. Global warming, for instance. The consequences also happen so incrementally that a single person cannot perceive them. Also, the actions of a single individual are not enough to produce any visible consequence, so it is going to be difficult to convince each individual to change their behavior. (Not looking to compare the magnitude or consequences of programming and global warming, just the perception problems 🐄💨)

#### Is it a problem worth solving?

Now, if you were to accept programming as a problem, hence, something that we could attempt to solve, you'd have all the right to ask: is it worth solving? Solving a problem takes time and we could spend that time creating more software that would solve more problems. Fair point. I'm going to say yes, I think it is worth solving. Let's see why.

Remember how we got into computers in the first place? We built the computer so we could tackle more complex problems. Oh the irony! I think we face the same problem all over again. We have gotten to a point where we can no longer solve bigger problems with software effectively. If we can't manage to make a very simple iOS app without bugs, who is telling you we can manage to make car software without bugs? We want to fly rockets and go to Mars, all this, controlled by software. That software could easily be the most complex ever built, are we sure it will work? How many more airplane or car crashes caused by software bugs do we need to convince ourselves that programming is a problem worth solving?

Remember why we invented machines in the first place? We were acknowledging the limitations of our human condition. We had trouble counting, we invented the abacus, we had trouble keeping tabs with the time we invented the clock. Well get this, in modern programming, the human is, yet again, the weaker link. **Building software is 90% a human problem. **Why? A software program can be so complicated that a single person cannot handle it, requiring teams of people to build it. The bigger the problem, the bigger the team. Now we are in the business of managing the (exponentially growing) communication channels in between developers. We have to ensure that everyone stays in sync to create a software system. To make it worse, we cannot point, see or listen to whatever part of the program we want to discuss in order to facilitate this communication, we are working in the world of ideas, remember? All this person-to-person communication and its coordination is a huge source of mistakes, but even if done perfectly, it would still take a lot of time. Have you ever played telephone?

Today, people are the fallible part of building software. Just like we use to do in the past, we should acknowledge our limitations and find a solution.

Plus, we could be doing so much more with all that time. You were wondering if putting some time aside to "solve the problem of programming" would be worth it. Well, developers spend 50% of their time finding and fixing bugs. If we invented better tools to create bug-free software that were _easy to use,_ you could do twice as much for the rest of time. That alone seems appealing to me, but that is just the tip of the iceberg. If we reduced the need for communication, you could spend all that time creating more software to solve other problems. Additionally, if we made programming so accessible that regular users could make modifications, you could spend less time adding and shipping features for only a small subset of users -- they could do that by themselves. Furthermore, imagine a world where the 20 million developers on earth today are freed from creating mundane and repetitive applications and they are put to solving the problems at the edge of human knowledge--the possibilities are immense.

Computers have brought us tremendous benefits. All the things we have created thanks to computers and all the problems we have solved are truly incredible. But that's exactly why we should solve this problem. There's so much more we could accomplish but it's unlikely we'll get there with our current tools. For example, there are a lot of great expectations around Artificial Intelligence, like human-level AI and beyond. Imagine that we managed to make AI with the level of intelligence of a monkey--that would certainly be a huge technological breakthrough. Now imagine that we _all_ went to play with the AI monkey and we _completely_ _stopped_ all development in the field of AI. You'd be pissed, right? You'd expect some people to keep working on improving AI because it could be much better, right? This is how I feel about computers and programming--there is an opportunity cost to not solve the problem of programming.

So, if you ask me whether programming is a problem worth solving, my answer is a straight yes. From a quantitative point of view, all the time saved in productivity in the years to come would outweigh the cost for finding a solution to programming. The returns will be much greater than the costs.

Now from a qualitative point of view. Back in the day math was slow and error-prone and we created the computer. Now, it's software development that is slow and error-prone. Back in they day math powered innovation. Today it's software that powers innovation. Solving the problem of programming is the next logical step.

The computer was created with practicality in mind. We must stick to this sentiment. We've used computers to create amazing things so far, but we shouldn't stop pushing the envelope. I am not suggesting that we stop the presses, have all programmers stop writing code and figure this thing out. We should continue extracting value from computing, but we must align our initiatives if we want to keep harvesting that value at a scale.
