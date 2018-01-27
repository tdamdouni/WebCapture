# New algorithm generates folding patterns to produce any 3-D origami structure

_Captured: 2017-11-26 at 20:12 from [m.techxplore.com](https://m.techxplore.com/news/2017-06-algorithm-patterns-d-origami.html)_

[ ![New algorithm generates folding patterns to produce any 3-D origami structure](https://3c1703fe8d.site.internapcdn.net/newman/csz/news/800/2017/5-newalgorithm.jpg) ](https://3c1703fe8d.site.internapcdn.net/newman/gfx/news/2017/5-newalgorithm.jpg)

> _Researchers have created a universal algorithm for folding origami shapes that guarantees a minimum number of seams. Credit: Christine Daniloff/MIT_

In a 1999 paper, Erik Demaine--now an MIT professor of electrical engineering and computer science, but then an 18-year-old PhD student at the University of Waterloo, in Canada--described an algorithm that could determine how to fold a piece of paper into any conceivable 3-D shape.

It was a milestone paper in the field of computational origami, but the [algorithm](https://techxplore.com/tags/algorithm/) didn't yield very practical folding patterns. Essentially, it took a very long strip of paper and wound it into the desired shape. The resulting structures tended to have lots of seams where the strip doubled back on itself, so they weren't very sturdy.

At the Symposium on Computational Geometry in July, Demaine and Tomohiro Tachi of the University of Tokyo will announce the completion of a quest that began with that 1999 paper: a universal algorithm for folding origami shapes that guarantees a minimum number of seams.

"In 1999, we proved that you could fold any [polyhedron](https://techxplore.com/tags/polyhedron/), but the way that we showed how to do it was very inefficient," Demaine says. "It's efficient if your initial piece of paper is super-long and skinny. But if you were going to start with a square piece of paper, then that old method would basically fold the square paper down to a thin strip, wasting almost all the material. The new result promises to be much more efficient. It's a totally different strategy for thinking about how to make a polyhedron."

Demaine and Tachi are also working to implement the algorithm in a new version of [Origamizer](http://origami.c.u-tokyo.ac.jp/~tachi/software/), the free software for generating origami crease patterns whose first version Tachi released in 2008.

**Maintaining boundaries**

The researchers' algorithm designs crease patterns for producing any polyhedron--that is, a 3-D surface made up of many flat facets. Computer graphics software, for instance, models 3-D objects as polyhedra consisting of many tiny triangles. "Any curved shape you could approximate with lots of little flat sides," Demaine explains.

Technically speaking, the guarantee that the folding will involve the minimum number of seams means that it preserves the "boundaries" of the original piece of paper. Suppose, for instance, that you have a circular piece of paper and want to fold it into a cup. Leaving a smaller circle at the center of the piece of paper flat, you could bunch the sides together in a pleated pattern; in fact, some water-cooler cups are manufactured on this exact design.

In this case, the boundary of the cup--its rim--is the same as that of the unfolded circle--its outer edge. The same would not be true with the folding produced by Demaine and his colleagues' earlier algorithm. There, the cup would consist of a thin strip of paper wrapped round and round in a coil--and it probably wouldn't hold water.

"The [new algorithm](https://techxplore.com/tags/new+algorithm/) is supposed to give you much better, more practical foldings," Demaine says. "We don't know how to quantify that mathematically, exactly, other than it seems to work much better in practice. But we do have one mathematical property that nicely distinguishes the two methods. The new method keeps the boundary of the original piece of paper on the boundary of the surface you're trying to make. We call this watertightness."

A closed surface--such as a sphere--doesn't have a boundary, so an origami approximation of it will require a seam where boundaries meet. But "the user gets to choose where to put that boundary," Demaine says. "You can't get an entire closed surface to be watertight, because the boundary has to be somewhere, but you get to choose where that is."

**Lighting fires**

The algorithm begins by mapping the facets of the target polyhedron onto a flat surface. But whereas the facets will be touching when the folding is complete, they can be quite far apart from each other on the flat surface. "You fold away all the extra material and bring together the faces of the polyhedron," Demaine says.

Folding away the extra material can be a very complex process. Folds that draw together multiple faces could involve dozens or even hundreds of separate creases.

Developing a method for automatically calculating those crease patterns involved a number of different insights, but a central one was that they could be approximated by something called a Voronoi diagram. To understand this concept, imagine a grassy plain. A number of fires are set on it simultaneously, and they all spread in all directions at the same rate. The Voronoi diagram--named after the 19th-century Ukrainian mathematician Gyorgy Voronoi--describes both the location at which the fires are set and the boundaries at which adjacent fires meet. In Demaine and Tachi's algorithm, the boundaries of a Voronoi diagram define the creases in the paper.

"We have to tweak it a little bit in our setting," Demaine says. "We also imagine simultaneously lighting a fire on the entire polygon of the polyhedron and growing out from there. But that concept was really useful. The challenge is to set up where to light the fires, essentially, so that the Voronoi diagram has all the properties we need."

**Completed quest**

"It's very impressive stuff," says Robert Lang, one of the pioneers of computational origami and a fellow of the American Mathematical Society, who in 2001 abandoned a successful career in optical engineering to become a full-time origamist. "It completes what I would characterize as a quest that began some 20-plus years ago: a computational method for efficiently folding any specified shape from a sheet of paper. Along the way, there have been several nice demonstrations of pieces of the puzzle: an algorithm to fold any shape, but not very efficiently; an algorithm to efficiently fold particular families of tree-like shapes, but not surfaces; an algorithm to fold trees and surfaces, but not every shape. This one covers it all! The algorithm is surprisingly complex, but that arises because it is comprehensive. It truly covers every possibility. And it is not just an abstract proof; it is readily computationally implementable."

Joseph O'Rourke, a professor of mathematics and computer science at Smith College and the author of [How To Fold It: The Mathematics of Linkages, Origami, and Polyhedra](http://howtofoldit.org/), agrees. "What was known before was either 'cheating'--winding the polyhedron with a thin strip--or not guaranteed to succeed," he says. "Their new algorithm is guaranteed to produce a folding, and it is the opposite of cheating in that every facet of the polyhedron is covered by a 'seamless' facet of the paper, and the boundary of the paper maps to the boundary of the polyhedral manifold--their 'watertight' property. Finally, the extra structural 'flash' needed to achieve their folding can all be hidden on the inside and so is invisible."

_This story is republished courtesy of MIT News ([web.mit.edu/newsoffice/](http://web.mit.edu/newsoffice/)), a popular site that covers news about MIT research, innovation and teaching._

**Provided by:** Massachusetts Institute of Technology
