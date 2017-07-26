# Programming With Mob Rule?

_Captured: 2017-05-06 at 00:30 from [dzone.com](https://dzone.com/articles/programming-with-mob-rule?oid=twitter&utm_content=buffere4b77&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

I was at a conference last year where I saw Woody Zuill talking about "Mob Programming." You can see that talk [here](https://www.youtube.com/watch?v=hpxDHNgdZTA).

A very simple description of Mob Programming, for those of you who don't have time to watch Woody's presentation, is "All the team working together on the same stuff." Instead of dividing work up and allocating it to individuals or pairs, the whole team sits together and advises a "Driver" who has the only keyboard.

## Interested but Skeptical

I thought it was an interesting, thought-provoking, even challenging idea. I confess that my first reaction was skepticism. To be honest, as a grumpy old man in my 50s, with a scientific-rationalist world-view, my reaction to most things is skepticism. I think of it as a healthy first response.

I thought about my skeptical responses, "That can't possibly be as efficient as the team dividing the work"; "Surely some people will just sit back and not really contribute"; "It is going to be dominated by a few forceful individuals"; "How could you design anything complex?" Once I started voicing them, they seemed familiar. These are precisely the kind of responses that I get when I talk to teams about adopting Pair Programming.

Now, I am a passionate advocate for Pair Programming. I believe that it makes teams stronger, more efficient, more cohesive and allows them to produce significantly higher-quality work. So I was in a quandary.

On one hand, "this can't possibly be efficient, can it?" on the other "Working collaboratively produces better results." I am enough of a scientific rationalist to retain an open-mind. Given the nature of my work as a consultant, I assumed that I would never experience Mob Programming personally and so would only ever see it from the perspective of a distant, outside observer. I was wrong.

## Invited to Join the Mob

I have some friends working in a start-up company, [Navetas](http://www.navetas.com/), who have recently experimented with Mob Programming and have been practicing it for a few months now. I know them through my good friend, Dave Hounslow, who used to work there. The team very kindly invited both of us to spend the day with them and "join the mob."

Before trying Mob Programming, the team was already fairly advanced in their use of agile development and Continuous Delivery. Dave had helped them to establish a strong culture of automated testing and an effective deployment pipeline. They were used to working collaboratively and doing pair programming, TDD and automated acceptance testing.

The team is fairly small, with only 5 developers. They saw a presentation on Mob Programming and decided to try it as an experiment for a single iteration, and have never gone back to their previous mode of work, pair-programming.

## Introductions, Process, and People

Dave and I arrived, and after coffee and introductions we attended the team stand-up meeting. The team is thinking of changing the stand-up because it no longer has a role of establishing a shared understanding, they do that all day, every day, working together in the Mob. However there is one team member who works remotely on customer service and so this is an opportunity to catch-up with her.

We then spent a bit of time in front of a whiteboard while the team described their system to us. Dave knew it a bit from when he used to work there, but it was new to me. They described their architecture and the story that we would be working on, and then we began.

The team had invested a bit of time and infrastructure to support their Mob Programming. They have a couple of nice big monitors so that everyone can see what is going on as the code evolves and a timer that reminds them when to swap who is driving.

The approach works by giving everyone a turn at the keyboard, including newbies like Dave and I. The timer is set for 15 minutes. Each person gets 15 minutes at the keyboard and then everyone shifts where they are sitting with a new person taking the keyboard. It is not totally rigid, so if you are at the keyboard and in the middle of typing a word you can finish, but the team tries to respect the time-slots to avoid one person hogging the keyboard.

We sat in a loose semi-circle with the person at the keyboard placed at the center. We all then offered advice on what to do and where to go next. When the time was up everyone shuffled round one place, like musical chairs without the music. The next person in sequence would take the keyboard and we would continue the conversation and design of the code. I think that the simple act of getting up and shifting seats helped keep the engagement going throughout the day. Tiny as it was, the act of moving sharpened the focus, even if just a little bit.

![Mob Programming1](http://www.davefarley.net/wp-content/uploads/2017/01/Mob-Programming1-300x225.jpg)

Sounds chaotic doesn't it? However, it wasn't. There were occasions when the discussion went on long enough that there was no typing during the 15 minute period, but on the whole that wasn't the case. We typically made steady progress toward the aims of the story.

![Mob Programming2](http://www.davefarley.net/wp-content/uploads/2017/01/Mob-Programming2-300x225.jpg)

Though there was a lot of talking, this wasn't dominated by one or two people - everyone had their say. There was inevitably some variance, however, as the level of experience of the team varied widely both in terms of general software development experience and experience on this project. So at different points different people had more or less to contribute. I was a complete newby to the system and so I asked more questions than the others and could mostly contribute on general issues of design and coding rather than specifics of the existing system. Others knew the system very well and so would contribute more when specific questions arose. This is one of the benefits!

## Optimize for Thinking, Not Typing

The story we were working on was one of those stories that was exploring some new ideas in the system. It was gently challenging existing architectural assumptions. At least that was the way that I perceived it. This was a good thing. This wasn't a trivial change, we had new territory to explore. We certainly spent more time talking than typing, but then I have never admired "lines of code" as a useful metric for software. I much prefer to optimise for thinking rather than typing. So while the amount of code that we produced during the day was relatively small, I think that it was higher quality than any of us would have produced alone.

The conversations were wide ranging, and often I felt that the presence of two outsiders, Dave and I, tilted the conversation more in the direction of reviewing some past decision than may otherwise have been the case. However, I also felt as though we both added some value to the discussions and the final output of the day - working code.

## Assumptions Fulfilled?

So what about the questions that I started with?

  * **"It can't possibly be as efficient."** Well the team has tracked their velocity and has seen a significant increase in the number of stories that they produce. I know that velocity is really only a pseudo-measure of progress, who is to say that this weeks stories are the same size as last? Nevertheless, the team feels that they are now moving significantly quicker and producing a higher-quality output. And the data that they have seems to back this up.

  * **"People will sit back and not contribute." **There were some people that spoke less than others, but everyone was engaged throughout the day and everyone contributed to some degree.

  * **"It will be dominated by forceful individuals."** There were a few "forceful personalities" present, myself and Dave included. Nevertheless the team seemed to me to listen carefully and consider ideas from everyone. It is certainly true that some of us talked more and were a bit more directive than others in the group, nevertheless I felt as though the outcome was a group-driven result.

  * **"How could you design anything complex?"** This is an old chestnut that people new to TDD and Pair Programming raise all the time. I am completely relaxed about the ideas of incremental design. In fact I believe that it is the only way that we can solve complex problems with high quality. I was pleased that the story that was chosen for the day had a bit of substance to it. It wasn't a deeply challenging problem, but did stress some architectural assumptions. I am confident that we, the whole group, moved the thinking about the architecture of the system forward during the course of our work that day.

## Justified Skepticism?

So what do I think about Mob Programming now that I have tried it? Well, I am still on the fence. I finished that day having had my beliefs challenged. This is not a crazy, inappropriate waste of time by any stretch of the imagination.

This was a small team that was considerably disrupted by having two newbys, Dave and I, drop-in for the day. I think that for any team this small, this would have been disruptive. I seriously doubt that, for most teams, the new people would have made much of a contribution. Dave and I are both experienced software developers and both used to working as consultants and adding value quickly. Nevertheless, I think that we added value quicker than would usually be the case. We made suggestions that the team tried immediately. We learned about the system more quickly, to a level of detail that surprised me. Again, on our first day in any other process, I think that we would have spent more time either doing introductory stuff or applied a narrower focus and worked in a smaller area of the code.

I was extremely impressed that this small team could accommodate the disruption of, nearly, doubling in size for a day and not only do useful work, but actually do so in a way that moved on their thinking.

At the human level this is a nice way to work. You have the conversations that are important. You share the context of every decision with the whole team all the time. You laugh and joke and share the successes as well as the disappointments.

These days I work as an independent consultant, advising people on how to create better software faster. I am intrigued at the prospect of using Mob Programming as a mechanism to introduce small teams to new ideas. I think it could be a wonderful instructional/learning tool. If anyone fancies carrying out that experiment you should give me a call.

So where are my reservations, why do I feel like I am still "on the fence" rather than a true believer? Well, there was a bit of coaching by one of the participants to organise the others. I honestly don't know if the process would have worked better or worse without him directing it quite so strongly, but I can imagine it breaking down if you had the wrong mix of people. That is a weak criticism, any process or approach can be disrupted by the wrong person or group of people. My point is that if you have a bad pair, you can move on and pair with someone else the next day. If you have a bad mob you have to be fairly strong minded to face the problem and fix it. It will force you to have some difficult conversations. Perhaps no bad thing if you do it, but I know of many teams that would shy away from such a social challenge.

There must be some natural limit. The idea of a mob of 200 people working on the same thing is ludicrous. So where is the boundary? I am a believer in the effectiveness of small teams. So I wouldn't have a team of 200 people in the first place. However, I wonder how well this would work with larger, yet still small, teams? There were 6 of us in this mob and it worked well. Would it have continued to do so with 8, 10, or 12? If I am honest I think that a team of 12 is too big anyway, but it is a valid question.

There are times when I want some time to think. If I am pairing and I hit such a point it is simple to say to my pair - "let's take a break and come back to this in 30 minutes." It is harder to make that call if everyone is working in a mob.

On the whole I had a fascinating day. I would like to extend my thanks to the folks at Navetas for inviting me to join their mob and experience this approach first hand. It was a lot of fun and I learned a lot.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
