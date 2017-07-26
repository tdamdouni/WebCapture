# Choosing Among Text Editors and IDEs

_Captured: 2017-07-02 at 11:51 from [dzone.com](https://dzone.com/articles/choosing-among-text-editors-and-ides?edition=306206&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-01)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

Few subjects in programming can get as contentious as quickly as, "what should I use to edit my code?" Before you even get to the subject of "which one," vigorous debates emerge over "what kind?" [This cordial Quora question](https://www.quora.com/Why-are-text-editors-more-popular-than-IDEs-with-the-engineers-in-the-software-industry) with roughly 6 billion answers serves as an example of this. A text editor or Integrated Development Environment (IDE)?

Only after that perilous decision do you arrive at the "which one debate." So furious has this debate proved that [Wikipedia has an "Editor War" entry](https://en.wikipedia.org/wiki/Editor_war). It describes the choice between the Emacs and VI editors. The usage of "war" is a joke. But only kind of.

So against this backdrop, you might regard the choice as one fraught with peril. Pick incorrectly and risk the scorn of your peers. That's a joke. But only kind of.

![Image title](http://www.daedtech.com/wp-content/uploads/2017/03/Choking.jpg)

Fortunately, for the purposes of guidance, at least, I count myself a pragmatist mercenary. In other words, I come from the relatively small camp of software developers without much strong preference about any of it. I have spent years with each of the following: Visual Studio, Eclipse, IntelliJ, Emacs, Pico, Nano, Scite, SublimeText, and Notepad++. And I'm probably forgetting some. All have their perks and foibles, but I prefer to keep my options open and let context guide me.

So, faced with the need to pick new tooling, how should you handle it? Today, I'll offer some advice on heuristics for selecting an IDE or text editor.

### Make a Quick List of Your Needs

First things first. Do what you would do when contemplating any sort of consumer decision. Make a list of your needs and wants.

For instance, say you were buying a refrigerator. You'd need a certain size to fit your space, and you'd need a certain amount of storage capacity. You might then _want_ a chrome finish and an ice maker. Contemplate the tool you'll use for writing code in this same fashion, for starters. You may have non-negotiable needs around the operating system and programming language, and more fluid wants around features.

But also bear in mind _context_. For example, do you specifically need a tool to work on one specific project at the office? Or do you want something versatile that you'll use everywhere, across various languages and technologies?

Now, combine these two lines of thinking and you will probably have narrowed the field considerably. And you _need_ to narrow the field since [a surprisingly daunting number of options exist out there.](https://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments) Easier to choose among 2 or 3 than from hundreds.

### Favor What Your Team Uses

With your options slimmed down, the time comes to look at some other, important heuristics. First up, I'll offer the guidance that you should favor what your team uses.

I don't offer this recommendation as some kind of endorsement of the herd mentality. In other words, don't take this as, "if most people do it, it must be right." As I said earlier, I consider myself a pragmatist mercenary of sorts, and "do what everyone else does" flies in the face of that.

The reason I suggest going with your teammates comes from practical experience. By way of contrast, I have done the opposite in my past, using IntelliJ when everyone else used Eclipse, for instance. And, while you can learn a lot doing this, it tends to create a great deal of _work_ for you.

Think back to school, when professors advised everyone to get specific editions of the book. Did you ever buck that wisdom and get a cheaper, used copy? Did you then struggle to find the right page when the professor told everyone, "flip to page 32, second paragraph"?

This comes to define your life when you have the oddball tool. Everyone else can just pull the latest code from source control and build it. You, on the other hand, have to add a bunch of XML files to something for some reason. And, when you finally get all of that right, someone commits something that breaks your whole setup. Why? Because they have no idea how it affects you.

Take it from someone who has walked this path. Decide to be a special snowflake and you have headaches and late nights in your future.

### Favor What Your Contemporaries Use

Next up, I'll offer wisdom in a similar vein. Let's say that you're working on a project as a solo contributor or that, for whatever reason, the tooling choice of those around you doesn't matter. You have freedom from the special snowflake headaches.

I would still recommend trying to sync with a decent sized community of people. In other words, seek out the opinions of your contemporaries and give weight to what the preponderance of them do. The reasoning is similar to the rationale for syncing with teammates if a bit more abstract.

To get somewhat concrete, let's say that you had an upcoming Ruby project. New to the language, you poke around to see what people use and you [discover this thread](http://stackoverflow.com/questions/16991/what-ruby-ide-do-you-prefer). Among others, Eclipse, RubyMine, TextMate, and Aptana all earn votes. But nobody stumps for Visual Studio, in spite of the existence of [a plugin that can make this work](https://marketplace.visualstudio.com/items?itemName=rebornix.Ruby).

But let's say that you really like Visual Studio and you opt to go this route. What do you think will happen in subsequent Google searches when you have issues with setup, use, debugging, etc? When you follow the community's usage patterns, you can find plenty of help. When you blaze your own, unusual trail… crickets.

### Keep an Eye on Cost

At this point, you have your list of needs and wants. You also know what your team uses and what the broader community tends to use. This should give you plenty of ammo to make an informed decision.

But if you still need a bit of help, I'll offer cost as the final heuristic. At first blush, this sounds exceedingly simple, but some complexity does arise in evaluating cost. Some tools have freemium models, while others have tiered features and pricing. Generally, when you evaluate their feature list, they'll offer up the most feature-rich version for consideration. But that doesn't mean you'll actually _get _those features, at least not without parting with some money.

Beyond that, also bear in mind that some extensions and plugins have cost as well. Perhaps the tool itself costs nothing, but to get, say, inline debugging, you have to buy a plugin that does have cost. This should also factor into your decision.

Finally, consider the total cost you might incur. You might say, "whatever, the company will buy me a license," and that might be true. But if you adjust to the tool and get to know and love it, you'll probably want to use it for your own personal projects and later, at other companies. Factor in not only what you'd pay now, but what you're willing to spend in the future.

### Choose One, but Keep Your Mind Open

The idea of future cost provides a nice segue to how I'd like to conclude my advice on selecting among text editors and IDEs. We, humans, have two relevant, built-in cognitive biases. The first, "[endowment effect](https://en.wikipedia.org/wiki/Endowment_effect)," causes you to value things _more _after you purchase them. For this reason, you will find yourself more likely to keep paying later than to make the decision to pay now. The second, "[choice-supportive bias](https://en.wikipedia.org/wiki/Choice-supportive_bias)" causes us to rewrite history to justify our past decisions.

These two human foibles team up to form a powerful behavior incentive. We fall in love with the things we pick and then get _really_ defensive about them. This leads to things like, oh, say, "editor wars" and knock-down, drag-out arguments on discussion forums.

Resist this impulse. Take the advice offered here, and any other wisdom you find on the subject, and do your best to make an informed and cost-savvy decision. But always keep your mind and eyes open after making that decision. You may have the best tool for today's job, but that does not guarantee you have the best tool for tomorrow's.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
