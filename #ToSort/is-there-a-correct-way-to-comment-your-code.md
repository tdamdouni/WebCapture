# Is There a Correct Way to Comment Your Code?

_Captured: 2017-05-22 at 10:27 from [dzone.com](https://dzone.com/articles/is-there-a-correct-way-to-comment-your-code?edition=299093&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-21)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Given that I both consult and do a number of public things (like blogging), I field a lot of questions. As a result, the subject of code comments comes up from time to time. I'll offer my take on the correct way to comment code. But remember that I _am_ a consultant, so I always have a knee-jerk response to say that it depends.

Before we get to my take, though, [let's go watch programmers do what we love to do on subjects like this: argue angrily](http://stackoverflow.com/questions/20922/do-you-comment-your-code). On the subject of comments, programmers seem to fall roughly into two camps. These include the "clean code needs no comments" camp and the "professionalism means commenting" camp. To wit:

> Chances are, if you need to comment then something needs to be refactored. If that which needs to be refactored is not under your control then the comment is warranted.

And then, on the other side:

> If you're seriously questioning the value of writing comments, then I'd have to include you in the group of "junior programmers," too. Comments are absolutely crucial.

Things would probably go downhill from there fast, except that people curate Stack Overflow against overt squabbling.

### Splitting the Difference on Commenting

Whenever two sides entrench on a matter, diplomats of the community seek to find common ground. When it comes to code comments, this generally takes the form of adages about expressing the why in comments. For example, consider this pithy rule of thumb from the Stack Overflow thread.

> Good programmers comment their code.
> 
> Great programmers tell you _why_ a particular implementation was chosen.
> 
> Master programmers tell you why other implementations were not chosen.

Jeff Atwood has [addressed this subject](https://blog.codinghorror.com/coding-without-comments/) a few [different times](https://blog.codinghorror.com/code-tells-you-how-comments-tell-you-why/).

> When you've rewritten, refactored, and rearchitected your code a dozen times to make it easy for your fellow developers to read and understand -- when you can't possibly imagine any conceivable way your code could be changed to become more straightforward and obvious -- then, and _only then_, should you feel compelled to add a comment explaining what your code does.
> 
> …
> 
> Junior developers rely on comments to tell the story when they should be relying on the _code_ to tell the story.

And so, as with any middle ground compromise, both entrenched sides have something to like (and hate). Thus, you might say that whatever consensus exists among programmers, it leans toward a "correct way" that involves commenting about why.

### The Main Problem With Comments

So far, I've offered adages and people's opinions. But I've done so without really diving into their underlying rationale. In some cases, I couldn't because they omitted it. And, in other cases, I simply didn't fit it into the quote. Presumably, they all have their rationale. But I'll speak in broader terms here.

Comments have an obvious purpose: communication and clarity. And they have an obvious downside: time spent writing them. If the problem were simply a matter of weighing the time investment in commenting against the benefit in clarity, then they'd be something of a no-brainer. But comments have a far more destructive downside. On a long enough timeline, they often lie.

What happened here? When you put on your code archaeology hat, you'll probably conclude that a guard condition once existed. Someone deleted that guard condition but didn't think to update the now-nonsensical comment. Oops.

This hints at the inherent underlying problem. Specifically, comments represent a non-compiled, non-enforced relationship between code and meta-knowledge about code. Adding comments adds cognitive maintenance burden for everyone that touches the code in the future. And since nothing forces people to update the comments, they get out of sync. This creates the possibility for negative returns on the effort of commenting.

### Addressing the Burden of Comment Maintenance

At this point, I have yet to say anything controversial. I think all parties can agree that commenting creates additional maintenance burden and seeks to pay for that burden with the clarity it provides. Where people diverge, I suspect, has to do with the burden of the maintenance work.

Proponents of the code comment would argue that maintaining comments simply comes as part of maintaining code. Opponents would counter that all such effort should go toward making the code itself clearer. No comments, no comment maintenance burden, and no chance for comments to lie.

While I can see both perspectives, I'll point out that only one lies counter to human nature. Saying that all developers have a duty to comment places burden on people, some of whom will never accept that burden. In doing this, you become the guy at the office demanding that everyone keep the single serving coffee pods in alphabetical order. People won't do it, and you will only achieve satisfaction by stamping your foot, getting angry, and haranguing people.

Even if you win, it would require draconian measures and result in resentment. You might find yourself winning a pyrrhic victory. The people you badger have no natural incentive to comply with your demands.

### A Main Heuristic for Commenting Code

Perhaps you can demand this high standard of professionalism. And perhaps you find yourself in a like-minded group where this works. But most likely, it just results in endless contention between you and others. And, if you don't execute the comment diligence flawlessly, the comments age poorly and have negative value.

As a result, I offer the heuristic that the correct way to comment is to avoid them as much as humanly possible.

Note now that I haven't offered any sort of absolutes. I haven't said that you _shouldn't _write comments. Rather, I'm offering something a lot more nuanced. The most likely outcome for a comment involves negative value on a long timeline, like playing games in a casino. But I won't tell you not to play blackjack and I won't tell you not to comment. I'll just point out that minimizing these activities makes for a good life strategy.

So approach commenting skeptically.

### Sometimes You Need Comments

That said, you do have situations that absolutely demand code comments. For instance, some organizations have mandates for legal/copyright comments in each file. By all means, add those comments when required (for this purpose, you might want to enlist a generator or something to avoid wasting your time).

In addition, you'll want to add method header comments for the sake of documentation and Intellisense. When you write code for consumption by others, these comments constitute _de facto_ end user documentation. In this situation, the value tends to outweigh the maintenance burden, since it impacts your product's usability.

And, finally, sometimes you have something mind boggling in your code. Sometimes you've refactored, cleaned up, and done everything humanly possible. But you still have something that will confuse and stymie. Far be it for me to say you shouldn't explain with a couple of slashes and some prose. Do what you need to do.

But as you go, recognize comments for what they are. They create a maintenance burden and have a negative expected outcome. So use them cautiously, pick better options when you can, and understand that no amount of righteous indignation on your part will alter the human nature of others.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
