# What does a cross-functional Agile team look like?

_Captured: 2017-04-08 at 15:40 from [www.extremeuncertainty.com](http://www.extremeuncertainty.com/what-does-cross-functional-agile-team-look-like/)_

Although not declared in the [Agile Manifesto](http://agilemanifesto.org/), pretty much any Agile advocate will tell you that you need cross functional teams in Agile. What does that mean exactly? How wide does the scope of the team's skills need to be? This is an interesting question and one that touches on organisational design, DevOps, HR, and a bunch of other complex topics. Caveat: I'm here talking about large organisations implementing Agile. A small startup could probably skip a lot of these headaches and easily implement a truly cross-functional team in Agile.

## What are cross functional teams in Agile?

A cross-functional team is one with a variety of skills, abilities and experience, so that they can develop their scope (stories, features, "product backlog items", whatever) by themselves, without help from others. This is a good idea, and part of a smart but subtle agenda in Agile that we should move away from silo specialist teams that you usually get on Waterfall projects. The "database team", the "front-end team", the "integration team", etc.

![TeamStructure](http://www.extremeuncertainty.com/wp-content/uploads/2015/06/TeamStructure.gif)

> _The thinking here is that the team should have capability and responsibility to deliver it's scope end-to-end. Why?_

  * Dependencies on other teams or people means handover points, which are inefficient
  * Dependencies on other teams or people can involve communication problems (e.g. the team may be in another building or worse, another country and timezone)
  * The Scrum rituals such as the daily standup include everyone involved with delivering the work.

## How cross-functional is the team likely to be?

The problem is how wide this responsibility is assumed to be. At many organisations doing Agile, they will have cross-functional teams, but the border ends at the channel level. Beyond that is the SOA layer, and that involves the SOA team, who are their own people doing their own thing in their own way. From an engineering perspective, the SOA integration services are beyond the scope of the channel deliverables. Developers can work with stubs for these services, integrate with them and test against them in a SIT (System Integration Testing) environment, and declare our team to be cross-functional from a strict engineering perspective, but I think that's a bit of a cop-out. It's not what we should really call a "full stack" team. Full stack means your team builds and owns the functionality all the way to the backend systems.

![FullStack cross functional teams in Agile](http://www.extremeuncertainty.com/wp-content/uploads/2015/06/FullStack.gif)

It's not just about SOA or an integration layer: you might have a security layer, a logging layer, an analytics layer, and so on, depending on your application's pipeline. Full stack means you own it all, from the very top to the very bottom. Assembling a truly full stack team like that could be very difficult, depending on the size of the organisation and complexity of the technology.

## What about cross-functional people?

In an even more perfect world, you would not only have a full stack cross-functional team, but each person in the team would be able to fill (to a reasonable level of competency) any of the activities that any of the people in the team could do. They may not be experts, but they can fill in gaps; e.g. "Dave the DBA is on training today and tomorrow, Jenny can you drop the front-end dev stuff you've been working on and finish off those scripts? That would help us get this story over the line."

This would offer some clear benefits:

  * The team is less vulnerable to velocity disruptions from sick / annual leave, training, conferences, etc.
  * Anyone in the team can peer review anyone else's work
  * Anyone in the team can train up someone on any skill.

Finding ten people who can do just about anything is obviously going to be hard. If you can find such a team, consider yourself very fortunate. More likely, you will have to foster a culture of learning, cross-skilling and up-skilling. This is a key part of being a Learning Organisation and an Improving Organisation (I'll say a lot more about these in later posts).

## What about functions besides Build?

Releasing software isn't just about build though (and under build I include architect, design, test, and refactor). There are other functions, or activities: deploy, release, run, monitor, analyse, upgrade, repair. What about the infrastructure it runs on? What about the marketing? The training and change management? The customer relationship management and communications? These activities are getting pretty far away from the actual coding activities required to create software, but they are important.

We're now talking about skills extending sideways from the channel, rather than up or down the technology stack. In a perfect world, you'd be able to assemble a team that could do all of that, and keep it at or under 10 people, but I doubt that's possible in most organisations. And if your company's marketing team require a 3 month lead time for any new features, then being able to deliver it in two sprints is not such a useful ability (though it's certainly still a good thing). What you therefore want to do is:

  * Make sure the communication loops between your team and these outside (but important) people are very short. Everyone being in the same building helps a lot.
  * Try to reduce the lead time of these external teams so they don't become blockers to your work. If their lead time is as short or shorter than the lead time of your scrum, you're fine, but it's unlikely.

If you want to know more, have a read of my article on [common organizational barriers to agile adoption](http://www.extremeuncertainty.com/common-barriers-agile-adoption/).
