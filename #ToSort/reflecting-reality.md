# Reflecting Reality

_Captured: 2017-09-01 at 21:44 from [lizkeogh.com](https://lizkeogh.com/2017/08/31/reflecting-reality/)_

One of the things I often do as a coach is help people to set up their visual boards, whether physical or electronic. Sometimes that can be surprisingly hard for teams to do without a bit of guidance, so I wanted to provide some hints and tips for getting a board up and running, fast. A lot of these have come from the world of Kanban, and I think they really help with small, continuous improvements.

My most important hint of all:

### Make your board reflect reality.

If reality is ugly, your board will be ugly. If you have lots of places where work passes from one role to another, your board will have lots of phases too. If you have work piling up in one area like "Ready for Dev" or "In QA", your board will have a lot of work in that phase.

_Do not hide it._ I see a lot of teams aiming for some kind of Agile ideal, and when the work doesn't match the ideal, sometimes they think, "Well, we shouldn't really be doing it, then." And so, they hide the work, and things end up dropping through the cracks as a result. Sure, maybe the team shouldn't be working on five things at once. If you are, though, _put it on the board. _The first stage to fixing a problem is admitting that you have a problem!

Once when I was working as a dev, I was told not to put any work on the board without going through my team lead, who was often away. That resulted in each dev keeping a little file of stuff that we knew needed to be done. Our lead was very surprised to find that we weren't confident about meeting the sadline*… and even more surprised by the amount of work still left to do to go live. We'd love to have a small backlog and be releasing every week, but if that isn't possible, _put it on the board._

### Change the board.

If you find that your board doesn't reflect reality, or that you're having to adopt processes that feel wrong because of the board, _change the board_. If you're using a technology that isn't adaptable to change, _change the technology. _Your tools are there to support your work, not the other way round.

I love physical boards because they're so easy to change, and you can tweak them together until you get a result you like.

### Keep your metrics.

Most of the teams I work with actually have two: one physical, and one electronic. Often one of those is nominated as the "master"; usually the electronic one. If you only have a physical board, though, or your physical is the master, when you move a card, put the name of the phase / column and the date you moved it on the back.

This is invaluable in seeing how and whether the team is improving, and in making forecasts about when you're going to be finished, so you can manage things like stakeholder expectations and marketing and cross-programme dependencies.

### Make process policies explicit.

Often teams have a really organic process, which means that sometimes when things get a bit crazy, as they always do, bits of that process get missed and fall away. By adding a simple checklist for moving into each column, we remind ourselves of the other people involved in delivering our work, and have a better chance of delivering it well.

You can have different policies for different types of work. Just make it explicit. Scrum practitioners often agree on a definition of "done"**, but I like having this definition for each phase-change. Bonus points if the policy involves talking to someone else and showing them what you did rather than just ticking boxes.

If we have a physical board, the policy might just be a little bit of paper at the top of each column with reminders on it.

### Add all types of work, including improvements.

If the team are involved in something, and it's taking their time and energy and focus, put it on the board. I tend to differentiate between customer/stakeholder-facing work that needs to be done, technical tasks where the customer is future-you or another dev team member, information-gathering activities like spikes, and improvements of the kind that often come out of retrospectives.

It isn't totally necessary to put improvements on your board, and a lot of teams are successful without doing that, but the teams which I see continually improving tend to have those tasks listed visibly somewhere. The improvements might go outside of your team, so it's OK to put "please deliver a talk on your ways of working to the XYZ community" on the board. Flag it up as a different kind of ticket if you need to filter them out for some reason. "Improvement" is a ticket type in JIRA; get your admin to add it.

### Visualize (small) queues, and limit your work in progress.

I've seen a _lot_ of boards called "kanban board" that weren't actually pull-systems. "Kanban" comes from Lean manufacturing systems like Toyota's. It means a signal card, and it's a way of making sure that the inventory in the system (i.e.: the work in progress) is a good match for the throughput capacity.

That means, for instance, that if your tester is regularly overloaded, you won't be able to go faster than your tester. By putting WIP limits on your tester's column, you create a signal (a space in that column) that your tester has room for more work. If the tester doesn't have room, you know that rather than overloading the WIP limits, the right thing to do is to go help the tester. Or, if you can't, read a book! Or do something small and interruptible, so that when the tester comes back with feedback, the work is still relatively fresh and the knowledge hasn't rusted in the rest of the teams' heads.

This way of working may not be _productive_, but it is more _effective_. Knowledge rusts way faster than cars.

We expect that in knowledge work, we'll get a lot more variance in terms of how long things take than Toyota does in its factories. Because of that variance, and because human beings are capable of more than one skill (unlike factory machines), our constraints will sometimes shift. We want to keep the work flowing, which means that we never want the constraint to run out. So, we want _small_ queues of work before the constraint.

If you want to start putting WIP limits somewhere, put them wherever work seems to get "stuck". That's your constraint.

As a note, there's a pretty typical journey I see with teams adopting WIP limits for the first time:

  1. they ignore them completely
  2. they violate them reluctantly
  3. they fight to stay inside them.

At each of these stages, we have another conversation about why WIP limits will help. Coaching takes patience.

### Stop Starting, Start Finishing.

If you don't feel like your team is ready to start putting WIP limits in place, this litttle principle (from David J. Anderson) will help to get the mindset in place. Before starting work, look to see if there's any way to help finish other work that's ongoing.

That might be as simple as offering to get your tester a cup of tea!

Another way to start doing this is called "Walking the board". In the stand-up, rather than just going round each person, look at the cards starting from the ones closest to release, then working through each phase towards the new work to be pulled in (normally right-to-left). Ask what's needed to help finish it, and if anyone else could do that or learn that skill.

People will naturally start learning each other's skills, becoming T-shaped, with narrow expertise but general ability to help out in the basics elsewhere.

### Autonomy, Mastery and Purpose.

As Dan Pink says in his book / talk, "Drive", this is how people in creative spaces are motivated. These ideas should help you provide your teams with the ability to change their own ways of working, in context; with slack as the constraint moves around to pick up new, related skills and to deepen and improve their own; and with a renewed sense of purpose driven by meeting genuine customer need, quickly and effectively.

Who knew visualisation could be so much fun?

*Sometimes no person or project or opportunity dies as a result of missing a date. If nothing's going to die, it's not a deadline. Often it's just someone's reputation at stake, and missing the date means that someone will be sad. People tend to be surprisingly pragmatic with real deadlines in a way that they're not with sadlines. Humans are weird.

**You're not really "done" until the software has been retired and is no longer used at all. Make your board reflect reality. Call it what it really is, whether that's "ready for integration" or "ready for release" or "in production". Remember that there are other people still using, maintaining and updating that software, and be nice to your IT Ops teams.
