# Use These 5 Tips to Help You Visualize Code

_Captured: 2017-11-28 at 13:44 from [dzone.com](https://dzone.com/articles/use-these-5-tips-to-help-you-visualize-code?edition=338993&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202017-11-28)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Source code doesn't have any physical weight - at least not until you print it out on paper. But it carries a lot of cognitive weight. It starts off simply enough. But before long, you have files upon files, folders upon folders, and more lines of code than you can ever keep straight. This is where the quest to visualize code comes in.

The solution file and namespaces organization make for a pretty unhelpful visualization aid. But that's nothing against those tools. It's just not what they're for. Nevertheless, if the only way you attempt to visualize code involves staring at hierarchical folders, you're gonna have a bad time.

How do most people handle this? Well, they turn to whiteboards, formal design documents, architecture diagrams, and the like. This represents a much more powerful visual aid, and it tends to serve as table stakes of meaningful software development.

But it's a siren song. It's a trap.

Why? Well, as [I've discussed previously](https://blog.ndepend.com/visualizing-software-architecture/), those visualization aids just represent someone's cartoon of what they think the code will look like when complete. You draw up a nice layer-cake architecture, and you wind up with something that looks more like six tumbleweeds glued to a barbed wire fence. Those visual aids are great...for visualizing what everyone wishes your code looked like.

What I want to talk about today are strategies to visualize code - your _actual_ code, as it exists.

### Generate Class Diagrams

Whoa, whoa. Put down your pencil or whiteboard marker. I'm not reversing myself immediately and suggesting that you hand-draw some UML. I'm talking about [actually creating class diagrams from your code](https://msdn.microsoft.com/en-us/library/ff657806.aspx).

Using this functionality, you can literally drag and drop your classes onto a canvas and start creating relationships between them. You can model both inheritance schemes and relationship cardinality. This represents a _vast_ improvement over following chains of inheritance across multiple files or taking notes to understand how a sequence of types relates.

Plus, unlike its hand-drawn cousin, this lightweight use of UML stays in sync with your code. This helps a lot with visualizing your class relationships.

### In-Editor Coverage Visualization

This tip is less about visualizing relationships among code elements and more about visualizing how comprehensive your automated tests are. Surely you've heard of [test coverage](https://www.ndepend.com/features/test-code-coverage). There's even a good chance [management somewhere has bludgeoned you](https://blog.ndepend.com/code-coverage-not-management-concern/) with it a bit.

But what everyone is after there is a number - a percentage. Get your code coverage up to 80% or whatever. That's no help for visualization.

Luckily, [Visual Studio offers an option](https://stackoverflow.com/questions/35092060/view-missed-branches-with-code-coverage-in-vs-2015) to help turn that number into something immediately useful to you. You can select an option to paint the editor with different colors for covered and uncovered lines. This means that you can glance through your files and easily visualize where your tests reach and where they don't.

Of course, you have a more powerful option for this particular visualization as well. I'm a huge fan of [NCrunch](http://www.ncrunch.net/), which continually runs your tests, updates coverage data, and paints the IDE accordingly.

### Heat Maps and Hot Spots

Since I originally wrote this for the NDepend blog, it'd be pretty weird if I didn't mention an NDepend feature or two. Well, fear not. Here that comes.

One your most powerful options to visualize code is the NDepend heat map. Here's an example.

![](https://blog.ndepend.com/wp-content/uploads/TypeRankHeatmap-1.jpg)

NDepend lets you compute [all sorts of metrics about your code](https://www.ndepend.com/docs/code-metrics). But without visualization, those metrics are just dusty data points hiding on your build server somewhere.

When you take them and plug them into a heat map, they come to life. You can pick a metric to use to vary box size and another to use to vary the color. This gives you striking visual representations of hot spots in your code: excessively complex methods, lots of dependency risk, [CRAP-y code](https://blog.ndepend.com/crap-metric-thing-tells-risk-code/), etc.

As the expression goes, a picture like this is worth a thousand words when trying to visualize code.

### Trend Graphs

Once you've figured out strategies to turn code metrics into visual representations of your codebase, you can realize another powerful visualization. This time I'm talking about the idea of [trend metrics](https://blog.ndepend.com/codebase-fit-trend-metrics/).

It's easiest to reason about our code by discounting any time other than the present. After all, as I mentioned before, codebases are already insanely complex and hard to picture without adding an entire other dimension to the mix. And yet, that dimension is critically important. Sure, your code has problematic pockets of cyclomatic complexity. But does it have more pockets than it did last month, or does it have fewer? That's an enormously important distinction.

Trend graphs let you visualize properties of code as they vary through time. Here are some examples that might interest you:

  * Are we maintaining a consistent level of test coverage?
  * Is our code growing more complex, normalized by codebase size, or are things getting more snarled?
  * What is the ratio of nodes to edges in our dependency graph (more on this shortly)?

You get the idea. It's one thing to keep track of this. But it's another altogether to visualize it with graphs over the course of time as you work in the codebase.

### Dependency Graphs

The last tip that I'll offer is the one that I find to be the most crucial of all. I'm talking about the [dependency graph](https://blog.ndepend.com/without-dependency-graph-flying-blind/). If you take nothing else away from this post, take away that it is utterly critical that you get a visual bead on how your code interrelates.

I once saw an actual dependency graph in the wild that looked like this.

![](https://blog.ndepend.com/wp-content/uploads/SnarledArchitecture-249x300.png)

You just see that giant mass of nodes, but if you could zoom in at the incredible magnitude, the edges put them to shame. I can't show you that because you'd need a mural-on-a-building-sized screen to get enough resolution. That's how jaw-droppingly snarled this code was.

How do you think that happens? I'll bet the people responsible have some impressively layered diagram somewhere of what this should look like. But it came to look like this instead. That happens because nobody's visualizing the real deal and incorporating that feedback into the development effort.

Your code's dependency graph models how things interrelate. Most commonly, you'll view this at the assembly level or (in the case above) at the namespace level. It shows you how all of the parts fit together when push comes to shove.

Use the dependency graph to inform you as to whether you're actually building something that's loosely coupled, rationally organized, and easy to maintain.

### Get Creative

I've given you five tips here on how to visualize your code. But there are no real definitive or canonical approaches. You have to get creative both with tooling and with your own imagination when you try to visualize code.

Building codebases is difficult and complex. Forming a clear mental image of them is even more so. Make sure always to be on the lookout for ways to make it easier and to help yourself reason clearly about your code.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
