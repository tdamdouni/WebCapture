# The Relationship Between Team Size and Code Quality

_Captured: 2017-02-06 at 12:39 from [dzone.com](https://dzone.com/articles/the-relationship-between-team-size-and-code-qualit?oid=twitter&utm_content=bufferd2995&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

### The optimal team size when it comes to code quality is simply however many people that work well together as you can afford.

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

Over the last few years, I've had the occasion to observe lots of software teams. These teams come in all shapes and sizes, as the saying goes. Not surprisingly, they produce output that covers the entire spectrum of software quality.

It would hardly make headline news to cite team members' collective skill level and training as a prominent factor in determining quality level...but what else affects it? Does team size? Recently, I found myself pondering this during a bit of downtime ahead of a meeting.

Does some team size optimize for code quality If so, how many people belong in a team? This line of thinking led me to consider my own experience for examples.

## A Case Study in Large Team Dysfunction

Years and years ago, I spent some time with a large team. For its methodology, this shop unambiguously chose Waterfall, though I imagine that, like many such shops, they called it "SDLC" or something like that. Any way you slice it, requirements and design documents preceded the implementation phase.

In addition to big upfront planning, the codebase had little in the way of meaningful abstractions to partition it architecturally. As a result, you had the perfect incubator for a massive team. The big upfront planning ensured the illusion of appropriate resource allocation. Then, the tangled code base ensured that "illusion" was the best way to describe the notion that people could be assigned tasks where they didn't severely impact one another much.

On top of all that, the entire software organization had a code review mandate for compliance purposes. This meant that someone needed to review each line of code committed. Absent a better scheme, this generally meant that the longest tenured team members did the reviewing. The same longest tenured team members that had created an architecture with no meaningful partitioning abstractions.

This cauldron of circumstances boiled up a mess. Team members bickered over minutiae as code sprawled, rotted, and tangled. Based solely on this experience, less is more.

## A Case Study in Large Team Harmony

However, then I thought of something else I saw years later. At the time, I had taken to cooling my heels in a really large enterprise, helping the various software departments and programs with a push for software craftsmanship. This meant leveraging my experience to teach them things like test-driven development, Continuous Integration, constant refactoring, etc.

Usually, the delivery mechanism for this sort of thing had two components: group workshops and individual practice (I'd pair with them). The group workshops often involved a presentation and then group practice using [a technique called Randori](http://dojo.wikidot.com/randori). This involved a pair of people participating in the coding while the rest of the group observed. Every so often, one of the pair would head to the peanut gallery, and someone new would take the wheel.

We could generalize Randori to the idea of "[mob programming](http://mobprogramming.org/)," wherein an entire team or group of people all work on the same problem. Sometimes, teams at this client site did exactly that, either while trying to grok a new technique or while working on a particularly difficult problem.

Teams taking this approach can seem comically over-allocated. Eight or 10 people spend the entire day working on a single class or even a single method. Setting aside efficiency considerations, though, these teams produced code with excellent quality.

## It's All About the Interactions

So, what gives? We have two teams with high developer-to-code ratios. One of them produces a defect factory while the other produces high-quality code.

We could posit that Waterfall versus Agile makes the difference, but I don't buy it. Those methodologies deal more with adapting to change and feedback loops than with the actual makeup of the source code. Besides, the mobbing teams were transitioning to an agile approach, so it's less cut and dry. We could also posit different skill levels for the teams, but on paper, the first team averaged more experience by far than the second.

The answer comes from the nature of the interactions. The first team each went off and worked in a vacuum for weeks or months at a time. Then, they circled back to bicker over details at code review time, with duration of tenure serving as the ultimate dispute arbiter.

The second team came together without a set concept of roles. From this egalitarian footing, they hashed out philosophical disagreements the moment they first cropped up. This didn't allow the team members weeks or months to become attached to and defensive of their ideas.

So at one end of the quality spectrum, we have individual contributor silos and politically charged forums for bringing them together. At the opposite end, we have relatively minimized group politics and a forum for allowing the best ideas to bubble quickly to the top.

## Code Quality as the Team Scales

Let's now engage in a bit of inductive reasoning. Consider a single person team, where that single person has years of experience writing high-quality code. One might argue for this as an optimal team size for quality, given that one person's skill.

Let's say that reality presents an unwelcome intrusion. One person can't deliver according to the necessary schedule, so the project requires more team members. Inductively speaking, we can preserve the high quality of team output under the following two conditions.

  * We hire reasonably skilled team members.
  * We create productive collaboration models.

If those hold true, more folks means more quality, as demonstrated by the mob programming story. More people collaborating means more eyes to catch mistakes and more minds with more chances of generating the best idea.

## The Answer to Team Size and Code Quality

After all of this analysis about team size, I can't help but bring cost into the discussion to close out. After all, whoever holds the purse strings will have a lot to say about "optimal team size."

Your team's code quality will only be as good as the skill levels of the team members and the productiveness of their interactions. So, if cost didn't matter, the answer for optimal team size would be, "define productive collaborations, and then the more the better." Get enough skilled developers to cover the needed functionality, then keep adding. If you run out of "room," have them pair. If the pairs run out of room, have them "triple." And so on.

However, then cost enters the discussion. You can't hire every developer on Earth (and, in reality, mobbing would eventually reach some point of diminishing returns) because you will ultimately have a limited budget. Instead, establish good collaboration practices and then hire as many skilled, compatible folks as budget allows.

To put it more succinctly, the optimal team size vis a vis code quality is "as many people that work well together as you can afford."

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).
