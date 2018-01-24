# The Whiteboard Interview: Adulthood Deferred

_Captured: 2017-12-17 at 20:05 from [dzone.com](https://dzone.com/articles/the-whiteboard-interview-adulthood-deferred?edition=345098&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-17)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

I haven't traveled this week (at least, not for work). As a result of that, I've sat at home, where I tend to have somewhat higher social media consumption. I, therefore, couldn't help but see [this post about "confessing coding sins."](https://theoutline.com/post/1166/programmers-are-confessing-their-coding-sins-to-protest-a-broken-job-interview-process)

Twitter has, apparently, overflowed with established software developers 'confessing' that they would fail Gigantech Inc.'s whiteboard/trivia interviews. I'd like to go on record to point out that [I ranted about the foolishness of this practice](http://www.daedtech.com/hiring-is-broken/) long before DHH made doing so cool with this tweet.

> Hello, my name is David. I would fail to write bubble sort on a whiteboard. I look code up on the internet all the time. I don't do riddles.

Here we have legendary techie David Heinemeier Hansson confessing that the Silicon Valley Gigantechs of the world would fail him out of their phone screens. His tweet offers a compelling symmetry. After all, when a cranky Thomas Edison invented the ineffective fad known as the "job interview" (that we haven't bothered to revisit in the last 100 years), his interview [would have failed Albert Einstein](http://paleofuture.gizmodo.com/take-the-intelligence-test-that-thomas-edison-gave-to-j-1689489019).

So, when it comes to the humble job interview, we at least know that it's consistent. It fails at its only job just as miserably today as it did in the beginning. All of the MegaTechs out there in The Valley (and emulators around the world) would have passed on hiring meteoric value-creator DHH, thus calling into question the ubiquitous and vacuous claim of every company out there that "we only hire the best and brightest."

But let's come back to DHH a little later. First, I want to talk about baseball.

![](http://www.daedtech.com/wp-content/uploads/2017/03/Baseball-player.jpg)

### Wins Above Replacement (WAR)

Even if you don't enjoy the sport of baseball, you should at least appreciate it for its _data_. Unlike many sports out there, baseball happens transactionally. The pitcher throws a pitch, and then a bunch of easily recorded stuff happens before play stops and this all starts over. Oh, and we've kept logs of this going back 150 years or so. This property has given rise to an entire discipline of statistics called [sabermetrics](https://en.wikipedia.org/wiki/Sabermetrics). So even if you don't like home runs and hot dogs, you can at least appreciate the Big Data.

Baseball has a fascinating stat known by industry nerds as "[Wins above Replacement (WAR).](http://www.fangraphs.com/library/misc/war/)" I'll quote them directly on the meaning.

WAR offers an estimate to answer the question, "If this player got injured and their team had to replace them with a freely available minor leaguer or a AAAA player from their bench, how much value would the team be losing?"

Let me parse out the baseball jargon and simplify. It asks, "how much value (in wins) does this player provide compared to an unremarkable replacement?" Modern baseball clubs wager _hundreds of millions_ of dollars answering this question. A player with WAR above 5 commands that kind of money whereas one with a negative WAR gets a pat on the butt and an imminently unremarkable minor league contract.

WAR ain't perfect. But it pretty reasonably approximates player financial value.

What does any of this have to do with the job interview or whiteboard coding algorithms? Well, the job interview represents the business world's ludicrous attempt to calculate VAR (value above replacement) of prospective hires.

### The Quixotic Pursuit of Corporate VAR

In baseball, if you want to evaluate the relative value of Hank Aaron and Joe Average, you have quite a corpus of data at your disposal. You can base assumptions about future performance on thorough, objective data about past performance of them doing their job. Baseball teams evaluate whether or not to pay them, and how much, on this basis.

The corporate world, on the other hand, lacks access to much, if any, past data. So, it attempts to compute VAR by handing them a marker and telling them to go to town on bubble sort for an hour. Of course, I understand that professional baseball teams risk far more money, thus calling for more of a due diligence budget. Nevertheless, though, the methodology differences are stark.

But going even beyond that, how much VAR does JuggerTech, Inc. really risk when hiring employee number 128,332? Let's call it 10X. After all, we frequently hear assertions that "ninjas" offer 10 times the "productivity," probably at times from the same companies that claim to hire these 10X-ers for 1.05X the pay. So, we'll just go with that.

This means that Alice and Bob wait in the corporate lobby, ready to pseudo-code bubble sort on a whiteboard. If they get it right and hire Alice, she'll bring 10 times the awesome. If they whiff and hire Bob, he'll bring just the standard amount of awesome. But, let's say they hire them both and put them both on the same project.

Alice will make the company 10 times as much money as Bob. Er, wait, probably not.

### The Fuzzy Value of Programmer N+1

Here's the thing. If HumongoTech sold "programmer awesomeness" at "X awesomes per dollar," then Alice makes them 10 times the money. But, for argument's sake, let's assume that HumongoTech sells things that actually exist in the real world.

Alice and Bob hire on and get their badges on day one. Then they get down to business, each working on a feature for some HumongoTech product. Except Alice brings 10 times the awesome.

Now, they both work on a feature that makes it into this iteration of the module if product manager Connie gives it the go ahead. Coin flip says she does, so Alice now has a 50% chance of offering 10 times the awesome and a 50% chance of offering no marginal awesome. So, Alice is down to a still-impressive 5X.

Except, ruh roh. VP Daniel will determine whether or not the module makes it into the next release. Flip another coin and Alice reduces to a respectable 2.5X. Now the only the chance of not shipping that release stands in the way. But, that's an actual thing, so let's shave Alice down to 1.25X.

And all of that comes before we figure out if that release will make or lose the company money. In the latter case, we get to throw a negative sign in front of marginally more productive Alice, who has now used her awesome to help the company lose money with 1.25 times the efficiency of Bob.

Are you seeing the trouble here? And are you starting to wrap your head around the preposterousness of HumongoTech figuring out and evaluating hiring VAR? Baseball teams have 9 starters whose every action gets measured. HumongoTech has more people than a small city with utterly unknowable contributions.

### Making It Up as We Go

So against this backdrop, what do we do in the corporate world? How do we hire? Truthfully speaking, we ask people to write about themselves on a piece of paper, pick a handful based on what they write, and then pick randomly. But we _tell_ ourselves that we totally have a process. We don't pick randomly. Instead, we channel Edison and say things like, "take this marker and draw me a doubly linked list with a blah, blah, blah" or "tell me why they make manhole covers round." Yep, that'll tell us who will help make MassiveTech more profitable.

We have no idea what we're doing with this stuff and no idea how to measure the results of our decisions. So, in the end, we just do what people have been doing since a guy made up the process out of thin air.

But we techies, unlike most other industries, [focus almost exclusively on the "technical" (read: VAR-theater) part of the interview](http://www.daedtech.com/journeyman-idealists-inside-of-companies/) at the expense of the part where you have a conversation about mutual fit like two human beings should. We _obsess_ over the meritocracy delusion that is this style of interview. And, I think I have a hypothesis as to why we do so.

### Adult Education as Never-Ending Juniority

We dwell on meritocracy and have no idea how to solve the probably-chaos-math-hard problem of measuring individual value contributions in non-trivial organizations. How to dispel this cognitive dissonance? Re-create an easy, familiar meritocracy. I can think of none better than school.

When you hit the entry level (assuming a CS degree), you've spent roughly 22 years doing "interviews." You get homework, take quizzes, and make presentations. Then, one of your betters evaluates your work and gives you a grade. Some answers allow for objective evaluation while others rest purely in the subjective eye of the teacher/professor. This happens endlessly and the same thing happens as you progress from one institution to the next: quizzes (standardized tests), applications (resumes), essays (interview questions), and the like.

So what do you do, lacking any reasonable criteria whatsoever for evaluating candidate VAR, but with a driving need to impose the illusion of meritocracy? You cast your senior team members as professors and keep the college dream alive right on through everyone's career and to the edge of retirement.

### The Office Political Ramifications of the Trivia Interview

Last fall, I borrowed a term from my upcoming book and [wrote about it on my blog: journeyman idealist](http://www.daedtech.com/journeyman-idealist-architect-programmer-paycuts/). That subject covers a ton of ground, but I can summarize relatively quickly. To move up in a company the "traditional" route, programmers have to run quite the gauntlet. First, they have to ace enough trivial interviews and peer posturing to earn titular distinction baubles like "tech lead," "architect," and "senior" and only _then_ can they pierce the next veil and get into management.

With just about every other position in pyramid-shaped companies, you become a thing and then, a few years later, you become a thing-manager (e.g. sales, account management, finance, etc). Only those of us in industries with intense penchants for stack ranking create a whole other obstacle course at the lowest possible rung of the company. But I digress a bit (If you're interested, you can [find a lot more of that in my book](http://www.daedtech.com/book/)).

Politically speaking, when you enter a company, you enter below both idealists (usually management) and journeyman idealists. You can tell the journeyman idealist from his gleeful administration of what DHH calls "whiteboard algorithm hazing." They become professor and you student as they grade you.

![](http://www.daedtech.com/wp-content/uploads/2017/03/Whiteboard.jpg)

And, once you enter the company, it's not like you suddenly become another professor. You _remain_ the student whenever that professor is present. And everyone knows it.

Sure, if you hang around long enough, they gradually extend an invite to the fraternity. But this takes years. And, if you leave, you start all over with new professors grading your entrance exam.

Trivia interviews don't just undermine your dignity while they happen. They establish you as a perpetual student.

### What's the Alternative?

I have a simple solution. Throw out the bathwater and don't sweat the baby. When talking to recruiters or whomever, state up front that you have a policy against trivia/algorithm/whiteboard style interviews. You understand that BureaucraTech does all of its interviews that way, but you hope they'll give you a call if they ever rethink their process.

But, I get it. Easy for me to say. I earn my living as a free agent and a content one at that. Your desires and ambitions differ from mine, and you _really_ want to head to The Valley and sign on with BureaucraTech. They have great perks. People you respect work there. You'll work with the cutting-edgiest stuff.

That's fair.

But you still don't have to agree to trivia interviews. I've previously offered the advice to start some kind of cool open source project or startup and wait for them to buy you out. Then you'll enter the mix as an organizational player, rather than a perpetual student (pragmatist grunt). But I recognize that's a long play.

So here's a thought instead. Identify what we free agents think of as "a buyer" at the company that presides over software developers. Buyers have budget and can make money decisions… like hiring. Follow that buyer and try to get to know her. Understand her group, her department, her challenges, and her gaps. Then conceive of a way that she could fill one of those gaps with a technical solution and approach her to talk about it.

Remember all of the talk earlier about VAR? Remember how BureaucraTech's VAR is completely unknowable for a one in 100K software developer hire? BureaucraTech's VAR is unknowable. Your buyer's is not. You can figure that out and make yourself valuable.

### VAR, Revisited for Your Next Interview

Once you do that, you will have an entirely different interview experience. You'll have a sales conversation, exchanging realistic discussions of mutual fit and opportunity. You'll slip past the mundane hiring machinery and enter the organization _mattering._

Every year I see discussions about how entirely broken the hiring process is, and every year I see companies more or less just keep doing the same, nonsensical things. This will continue happening as long as the candidate and company both punt on a meaningful value assessment and start playing professor-student games. VAR-theater drives these stupid interviews -- not a general agreement that they work. If you [go back and read my post](http://www.daedtech.com/hiring-is-broken/), you'll see that a BureaucraTech employee even _admits_ he doesn't think the process works.

We won't break this stalemate with undirected outrage or complaints about the process. But we can break it if we refuse to participate. And I can think of no better way to help your career and to refuse than by putting on your sales and delivery hat and figuring out how to deliver something to someone that matters.

As DHH himself said, he can't do a bubble sort. He isn't DHH because he won some programming mastery competition over 8 million other competitors and was awarded an internship at BureaucraTech for his trouble. He's DHH because he built something that made countless people more productive. He's DHH because he wears a really high VAR on his sleeve.

So leave the junior varsity games to people who like to amuse each other with riddles. Ace your next interview by refusing to have it in a context with penny ante table stakes.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
