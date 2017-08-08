# ScrumMaster for Three Teams? What are the Alternatives?

_Captured: 2017-08-08 at 18:55 from [agilepainrelief.com](https://agilepainrelief.com/notesfromatooluser/2014/04/scrummaster-for-three-teams-what-are-the-alternatives.html#.WYntA6CbGaN)_

![Source: http://www.freeimages.com/browse.phtml?f=view&id=1060296](http://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2014/04/PulledInManyDirections-small.jpg)

> _ScrumMaster being pulled in many directions_

_The Scrum By Example is a series of stories about ScrumMaster John who attended one of my courses. He is the ScrumMaster for the __[WorldsSmallestOnlineBookstore_](http://agilepainrelief.com/notesfromatooluser/category/agile/scrum/scrummaster-tales)_._

Scrum succeeds because it helps build a high performance team, i.e. a team that is capable of delivering significantly more work than the individuals are capable of separately. The role of the ScrumMaster is to help build the high performing team through observing their relationships, helping them understand Scrum, improving their technical practices, improving their relationship with their product owner, and improving the organization they're part of. Read this story through the lens of building team(s) and ask what John could have done.

After the stress of the [last release](http://agilepainrelief.com/notesfromatooluser/2014/03/scrummaster-tales-overtime-on-a-scrum-team-is-an-unhealthy-sign.html), John and his team are slowly paying down the [technical debt (mess)](http://www.infoq.com/articles/technical-debt-levison) they created. They maintain a technical debt backlog, knocking off a few items every sprint in addition to the work they do creating new features. If they keep this up it will take only another three to four months before they're as productive as they were before the release.

Jeff (CTO - Jeff -> Don -> John) calls John and Don, into his office. He says, "I have great news. The VCs have given us the go ahead to hire two new teams right now. Unfortunately they don't think there is enough need to justify the hiring of any more ScrumMasters". He continues, "John, I'm sure you can play this role for all of our teams. There can't be anything more than scheduling a few meetings. John, we're counting on you to make this a success."

John has learned to speak up more than he had in the past, and he tries to explain that the role is far more involved than just booking a few meetings. Jeff, however, stands his ground. "I've just attended SAFe training and my trainer told me we could get away with a 1:4 ScrumMaster to Team ratio." He continues, "John, I know you can make this work for us."

In the following weeks, two additional teams are hired and John does his best to split his time fairly between them. He mostly abandons his own team (we will call them Alpha) and splits his time between the other two new teams. John, being an aficionado of personal improvement, keeps track of roughly how much truly productive time he has for each team just by measuring the number of [Pomodoro](http://en.wikipedia.org/wiki/Pomodoro_Technique) he completes. Perhaps unsurprisingly, this number goes down. He used to average six a day, and now he only achieves four. (John has just discovered [Multitasking - which is a great way to get everything done later](http://www.infoq.com/articles/multitasking-problems) at both the team and individual level.) Luckily, he's figured out that he can mostly ignore his existing team since they're already so far along the team performance curve.

Three months in, and let's see how the teams are doing. The two new teams, Beta and Gamma, are struggling. Team Beta run all the mechanical elements of Scrum correctly, and they have all the meetings (Sprint Planning, Review, Retrospective and Daily Scrum). They have - and consistently meet - their definition of done, but it is so weak and watered down as to be useless. So the letter of the Scrum law is being practiced, with no spirit. There is limited collaboration and everyone is working in silos. Worst of all, the Beta Product Owner writes all the user stories for team members, treating them as order takers and not partners.

Our fearless ScrumMaster John has a fair idea about what needs to be done, but little time to act. Complicating things further, team Beta have decided that they're really not a big fan of John since he never removes any of their [impediments directly](http://agilepainrelief.com/notesfromatooluser/2011/12/scrummaster-tales-impediments-are-holding-back-the-team.html), instead challenging them to solve their own problems.

Team Gamma are off to a better start. They're trying to follow not just the letter of Scrum law, but also appreciate that there is a spirit of collaboration. They're really struggling to make it happen. They've heard all about Test Driven Development, Acceptance Test Driven Development, Continuous Integration, Collective Code Ownership, Refactoring, Simple Design, etc, however they're having trouble getting past rudimentary Unit Testing. It took them several weeks to get a Continuous Integration server up and running as they were snowed under with requests from the Product Owner.

They need someone to hold their hands and act as a backbone when required. They need someone who can coach their collaborative skills, in addition to the technical ones. This team has a fair chance of becoming high performing, but are unlikely to do so by stumbling towards their goal. Their issues are two fold: they don't really understand what's going wrong, and John doesn't have the time to coach them correctly.

Meanwhile John's regular team is suffering under his almost complete absence. In an attempt to get the other teams up and running, John is only booking meetings for Alpha, he helicopters in to facilitate meetings, and then disappears again. As a result, Retrospective meetings are happening but the action items aren't being completed.

The team had been focusing on improving their technical practices, but this has fallen by the wayside. They've been using [Sonar](http://www.sonarsource.com/products/benefits/product-benefits/) to track historical information around their builds including: Build Failures, # of Unit Tests run, Code Coverage, PMD warnings, and more. In the past few months it's easy enough to see that their technical quality has slipped. It would appear that, without John to question, they struggle to finish their commitment every sprint, even when it's clear that they overcommitted. Worst of all, they seem to have forgotten about the importance of regular [backlog refinement](http://agilepainrelief.com/notesfromatooluser/2012/06/scrummaster-tales-learning-how-to-estimate.html), because the product backlog has hardly changed in the past six weeks. This makes it increasingly likely that the team isn't actually working to meet the current needs of the customers. Since they spent limited time collaborating on [acceptance criteria](http://agilepainrelief.com/notesfromatooluser/2013/02/scrummaster-tales-team-collaborate-acceptance-criteria.html), they've had more surprises where Product Owner Sue says that feature doesn't work the way she wanted and it needs to be fixed.

### Analysis

What happened? John can't possibly win here. His boss, Jeff, thinks that the role is part time. But he can illustrate that the role requires a lot more than part time, and help people around him see the costs of their choices:

  * Use Sonar history from Team Alpha to show the general decline in technical quality _(Be careful to make it clear that these are just general indicators.)_
  * Demonstrate that Alpha is achieving fewer backlog items per sprint than they did in the past. _(You can measure velocity to do this but I would just count stories.)_
  * Demonstrate that the code being produced by the Beta and Gamma teams is harder to follow and making it more difficult to add new features.
  * Show that all the teams are struggling to deliver features at all, and when they do, the features aren't what the customer wanted.
  * Show that Alpha team hasn't made any real changes in the past few sprints.

…

In all cases, John can focus on the outcomes that business cares about: Happy Customers, Useful Features Delivered, Quality and Ongoing Improvement. Don't focus on Scrum words, as the management couldn't care less about those.

When you're responsible for many teams, you don't have time. So you will need to:

  * Facilitate well - instead of taking the time to facilitate, John fell back to his prior command and control habits (alienating team Beta).
  * [Coach the Product Owner](http://agilepainrelief.com/notesfromatooluser/2011/07/the-scrummaster-tales.html) - a Scrum Team that doesn't have a close relationship with their Product Owner will do a brilliant job of building the wrong thing.
  * [Coach the Technical Practices](http://agilepainrelief.com/notesfromatooluser/2012/03/scrummaster-talesthe-team-learn-how-to-learn.html) of the Team - once the mechanics of Scrum are in place, much of the productivity improvement comes from team members learning Test Driven Development, Acceptance Test Driven Development, Continuous Integration, Collective Code Ownership, Refactoring, Simple Design, et al.
  * Coach the Scrum Process - John only has time to run meetings at this stage, not facilitate retrospectives, and certainly not to work with individual team members. _(Normally I expect ScrumMasters to facilitate meetings, in this case John is so rushed he doesn't have time to facilitate, and instead he just tells people what to do in the meetings. Running meetings will quickly impinge on the team's ability to self organize.)_
  * Witness the Team in Action - part of coaching effectively is just observing - seeing what is happening both as individuals and between team members. Without witnessing the activities and actions, it's harder to facilitate an effective retrospective that gets to the heart of matters.
  * Definition of Done - the team needs to be consistently reminded what they've already agreed with respect to 'Done'. They need to be consistently challenged to ensure that they honour their definition.
  * Retrospective Action Items - it's easy to commit to take action in the retrospective, but harder to follow through. The ScrumMaster provides the reminder of the importance of following through.
  * Team Impediments Backlog - the ScrumMaster is responsible for maintaining the team's impediments backlog, for keeping it up to date, and for highlighting problems that team members themselves can take.
  * Technical Mess (or Debt) Backlog - effective teams maintain a list of their worst pain points in the code and are always paying them. Their goal is to extend the useful life of their codebase and lower the cost of change.
  * Discipline and Focus - helps the team stay focused on the highest priority work and helps provide them with the discipline and backbone to make it work.
  * Change the Organization - many of the problems that the team faces are at the organizational level, and any fixes we make at the team level are sub-optimizations. A good ScrumMaster is always thinking about the big picture as well as their own team.

This is far from an exhaustive list - just a start.

When you're faced with the tough situation like this, what is the best way you could handle it? Some options in rough priority order:

  1. Full time, Dedicated ScrumMaster - gold standard.
  2. If one team is already doing well, have one full time ScrumMaster split over two teams. We have one person learning to play the role of the ScrumMaster more effectively and we already have one team working well. In this case our ScrumMaster can focus much of their time on growing the capacity of the new team.
  3. Full time ScrumMaster split over two teams - similar to number #2 - one person focused on playing the role well **might** be a better option than part timers. _In this case the organization needs to acknowledge that it is delaying (possibly forever) both teams' achieving high performance._
  4. Team member playing part time ScrumMaster at least 50% of their time focused on their team. Guarantees some time for the role to be played adequately well. **Problem:** the team won't perceive you as neutral in dealing with conflict; personal task work often takes priority over the team. **Solution:** wear a hat when playing the ScrumMaster to remind yourself to stay neutral; work for the team trumps individual task work. _In this case the organization needs to acknowledge that it is delaying the team's achieving high performance._
  5. ScrumMaster for three or more teams - doesn't work, refuse the role and ask for one of the above options.

If you need more help in showing someone the full time nature of the ScrumMaster role, try:

  * ScrumMaster Checklist from Michael James: <http://scrummasterchecklist.org/>
  * Cases for Dedicated ScrumMaster - Melinda Stelzer Jacobson: <http://www.infoq.com/articles/case-dedicated-scrum-master>
  * Seven Things I wish I had known starting out as ScrumMaster: <http://www.scrumalliance.org/community/articles/2012/may/seven-things-i-wish-i-d-known-when-i-started-out-a>

Scrum is difficult enough to do in the first place. Don't stack the deck against yourself by accepting more than you can possible handle.
