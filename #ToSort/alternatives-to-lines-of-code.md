# Alternatives to Lines of Code

_Captured: 2017-02-19 at 21:17 from [dzone.com](https://dzone.com/articles/alternatives-to-lines-of-code?oid=twitter&utm_content=buffer360a5&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

It amazes me that in 2016, I still hear the occasional story of some software team manager measuring developer productivity by committed lines of code (LOC) per day. In fact, this reminds me of hearing about measles outbreaks. That this still takes place shocks and creates an intense sense of anachronism.

I don't have an original source, but Bill Gates is reputed to have offered pithy insight on this topic. "Measuring programming progress by lines of code is like measuring aircraft building progress by weight." This cuts right to the point that "more and faster" does not equal "fit for purpose." You can write an awful lot of code without any of it proving useful.

Before heading too far down the management criticism rabbit hole, let's pull back a bit. Let's take a look at why LOC represents such an attractive nuisance for management.

For many managers, years have passed since their days of slinging code (if those days ever existed in the first place). This puts them in the unenviable position of managing something relatively opaque to them. Opacity runs afoul of the standard management playbook wherein they take responsibility for evaluating performances, forecasting, and establishing metric-based incentives.

## The Attraction of Lines of Code

Let's consider a study in contrasts. Imagine that you took a job managing a team of ditch diggers. Each day you could stand there with your clipboard, evaluating visible progress and performance. The diggers that moved the most dirt per hour would represent your superstars and the ones that tired easily and took many breaks would represent the laggards. You could forecast milestones by observing yards dug per day and then extrapolating that over the course of days, weeks, and months. Your reports up to your superiors practically write themselves.

Let's change the game a bit. Imagine that all ditches were dug purely underground and that you had to remain on the surface at all times. Suddenly accounts or progress, metrics, and performance all come indirectly. You need to rely on anecdotes from your team about one another to understand performance. You only know whether or not you've hit a milestone on the day that water either starts draining or stays where it is.

If you found yourself in this position suddenly, wouldn't you cling to any semblance of measurability as if it were a life preserver? Even if you knew it was reductionist, wouldn't you cling? Even if you knew it might mislead you? Such is the plight of the dev manager.

In their world of opacity, lines of code represent something concrete and tangible. It offers the promise of making their job substantially more approachable. In order to take it away, we need to offer them something else instead.

## Measuring Developer Productivity

I most commonly see managers seize on lines of code as a way to judge the productivity of individual developers. This gives them something easy enough to measure -- if a developer delivers more code than her peers, she must be doing better. Of course, almost no manager is this obtuse, and they generally combine this with something like defect counts as a normalizing factor.

Nevertheless, this practice still serves up a heaping pile of fail. Developers can game such metrics trivially by inserting benign but useless code.

To make matters worse, this accumulation of extra code works against the long range goals of the team. I often explain to technical managers and executives that code is more like inventory than it is like an asset -- the more of it that you have lying around, the more liability you have. As an extreme example, ask yourself whether you'd rather have a 10 line program or a 1000 line program when both did exactly the same thing. Those extra 990 lines require maintenance and carry an ongoing burden while providing no value.

If you want to measure developer productivity, you need to do it indirectly. Rather than fighting that reality, embrace it.

Measure the team's performance only, and measure it by features or business value delivered. After all, these represent the only true metrics that count, from a business perspective. Considerations like lines of code are just proxies for value, often used when shops don't deliver anything for long periods of time. Even if you can't ship, cut releases more frequently, and measure the team by what it delivers.

From there, individual performance shakes out from the team dynamic, the way it did during your school days. When the team relies on one another to hit collaborative goals, social dynamics make it obvious who underperforms and who leads.

## Forecasting Effort

The second place managers seem to love the LOC metric is relative sizing of features and codebases. They take this and use it for forecasting purposes.

"Well, Feature X took 75 KLOC to implement, and we think that Feature Y will take twice as much effort. So, we're currently 15 KLOC in after a week, and figure it will take 10 total weeks." Or something like that.

This thinking attempts to reduce knowledge work to widget manufacturing. It presupposes that uniformity of problem solving and predictability of the work. Ironically, when software development becomes predictable enough to forecast this way, it also becomes inefficient. After all, anything that can easily be commoditized and repeated this way should be automated.

LOC can offer you insights about efforts, but as a lagging indicator. Managers trying to use it predictively just move the goalposts. Instead of using crystal balls to predict weeks and months, they use them to predict KLOC, which they convert to weeks and months.

My personal recommendation for predictive metrics? Get the teams accustomed to [relative sizing](https://www.scrum.org/About/All-Articles/articleType/ArticleView/articleId/838/Estimating-relative-sizes-eg-story-points) and use that for story mapping and forecasting purposes. Even if you have an MBA and love metrics, your software developers will do better forecasting effort than you will. Learn to trust them.

## What Lines of Code Can Really Tell You

As I mentioned earlier, you can learn things from measuring LOC. You just can't learn the things that managers hope to when they use it as I've described here.

LOC offers a great way to normalize trends in your codebase. For example, defects per module may offer some raw insight, but defects per module normalized over LOC per module will tell you more. When looking retroactively at trends, LOC makes a great equalizer.

On top of that, you can use LOC as a quick barometer for mounting complexity. Keep tabs on the amount of LOC per method and per class to make sure you don't produce ugly hot spots with high fan-in. Make sure you keep things modular.

I might extrapolate to say that you can find all sorts of creative uses. However, as you do, bear in mind a crucial theme: However you use it, it will never provide a shortcut to easy managerial understanding.

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).
