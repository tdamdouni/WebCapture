# The Dark Side of Git... - DZone Open Source

_Captured: 2019-09-02 at 09:52 from [Productivity is producing software that accomplishes the business purpose at a marginal cost that provides positive value. While that might have been wordy or even technically incorrect, the overall equality formula I want to use is: the sum of all activities to product the software must be less than the value the software provides. In other words, if it costs 2 million dollars to build/deploy some software, but the business can only recoup 1 million dollars in value (via cost-saving or new sales or whatever), then I would consider that a failure.](Productivity is producing software that accomplishes the business purpose at a marginal cost that provides positive value. While that might have been wordy or even technically incorrect, the overall equality formula I want to use is: the sum of all activities to product the software must be less than the value the software provides. In other words, if it costs 2 million dollars to build/deploy some software, but the business can only recoup 1 million dollars in value (via cost-saving or new sales or whatever), then I would consider that a failure.)_

As a distributed source code tool, Git is great. I love that when I'm on an airplane, I can commit code without a wireless connection and be able to unwind what I was doing. It was clearly designed with the "offline" model in mind. The idea I can create a quick branch, experiment, make massive sweeping changes, and just drop the whole thing if I realize it sucked...is AWERSOME! For a fact, this puts it ahead of its open-source predecessors (namely...SVN, CVS, and RCS).

What I've observed, however, is that a lot of folks have taken up a development model where "everything is a branch" and we end up with roles like "pull request approval engineer" (not a real title, but if you end up doing that job, you'll know that you're doing it). This problem happens when the number of public branches/forks reaches a count and complexity that far exceeds any value they could have possibly served.

I'm going to take a somewhat unpopular stance here, but in general, my stance is that branches are anti-productive... before everyone gets their pitchforks out, let me explain my version of "productivity" for a software project. Productivity is producing software that accomplishes the business purpose at a marginal cost that provides positive value. While that might have been wordy or even technically incorrect, the overall equality formula I want to use is: the sum of all activities to product the software must be less than the value the software provides. In other words, if it costs 2 million dollars to build/deploy some software, but the business can only recoup 1 million dollars in value (via cost-saving or new sales or whatever), then I would consider that a failure.

As a software engineer, I want to create a branch so that other developers cannot see my changes in their builds.

  1. First of all, the activity of creating the branch, merging in everyone else's branch to your branch (through possibly a different branch) is all stuff that you would get instantaneously for free if you were all working on the same mainline.
  2. Second, you're deliberately delaying visibility of changes from the rest of the team...which means the whole notion of continuous integration is getting thrown out the window
Which brings me to a key question: 

> I would contend: If you're branching for every feature or bug, and merging them back in, your codebase and/or process is more fragile than agile. Do you agree? 

Thoughts?
