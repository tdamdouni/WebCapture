# Same Stats, Different Graphs: Generating Datasets with Varied Appearance and Identical Statistics through Simulated Annealing

_Captured: 2017-05-02 at 09:32 from [www.autodeskresearch.com](https://www.autodeskresearch.com/publications/samestats)_

> ...make both calculations and graphs. Both sorts of output should be studied; each will contribute to understanding. F. J. Anscombe, 1973   
(and echoed in nearly all talks about data visualization...) 

It can be difficult to demonstrate the importance of data visualization. Some people are of the impression that charts are simply "pretty pictures", while all of the important information can be divined through statistical analysis. An effective (and often used) tool used to demonstrate that visualizing your data is in fact important is [Anscome's Quartet](https://en.wikipedia.org/wiki/Anscombe%27s_quartet). Developed by F.J. Anscombe in 1973, Anscombe's Quartet is a set of four datasets, where each produces the same summary statistics (mean, standard deviation, and correlation), which could lead one to believe the datasets are quite similar. However, after visualizing (plotting) the data, it becomes clear that the datasets are markedly different. The effectiveness of Anscombe's Quartet is not due to simply having four different datasets which generate the same statistical properties, it is that four **clearly different** and **visually distinct** datasets are producing the same statistical properties. In contrast the "Unstructured Quartet" on the right in Figure 1 also shares the same statistical properties as Anscombe's Quartet, however without any obvious underlying structure to the individual datasets, this quartet is not nearly as effective at demonstrating the importance of visualizing your data.

![](https://d2f99xq7vri1nk.cloudfront.net/Anscombe_1_0_0.png)

> _Fig 1. Anscombe's Quartet (left), and a "Unstructured Quartet" on the right, where the datasets have the same summary statistics as those in Anscombe's Quartet, but lack underlying structure or visual distinction._

While very popular and effective for illustrating the importance of visualizing your data, they have been around for nearly 45 years, and it is [not known](https://doi.org/10.2307/2682899) how Anscombe came up with his datasets. So, we developed a technique to create these types of datasets - those which are identical over a range of statistical properties, yet produce dissimilar graphics.

Recently, [Alberto Cairo](http://albertocairo.com/) created the [Datasaurus](http://www.thefunctionalart.com/2016/08/download-datasaurus-never-trust-summary.html) dataset which urges people to "never trust summary statistics alone; always visualize your data", since, while the data exhibits normal seeming statistics, plotting the data reveals a picture of a dinosaur. Inspired by Anscombe's Quartet and the Datasaurus, we present, **The Datasaurus Dozen**:

![](https://d2f99xq7vri1nk.cloudfront.net/AllDinosGrey_1.png)

> _Fig 2. The Datasaurus Dozen. While different in appearance, each dataset has the same summary statistics (mean, standard deviation, and Pearson's correlation) to two decimal places._

These 13 datasets (the Datasaurus, plus 12 others) each have the same summary statistics (x/y mean, x/y standard deviation, and Pearson's correlation) to two decimal places, while being drastically different in appearance. This work describes the technique we developed to create this dataset, and others like it.

The key insight behind our approach is that while it is relatively **difficult** to generate a dataset from scratch with particular statistical properties, it is relatively **easy** to take an existing dataset, modify it slightly, and maintain those statistical properties. We do this by choosing a point at random, moving it a little bit, then checking that the statistical properties of the set haven't strayed outside of the acceptable bounds (in this particular case, we are ensuring that the means, standard deviations, and correlations remain the same to two decimal places.)

![](https://d2f99xq7vri1nk.cloudfront.net/SmallChange.gif)

> _Fig 3. Making a number of small changes to a dataset on the left, while maintaining the same overall statistical properties (to two decimal places), shown on the right._

Repeating this subtle "perturbation" process enough times, results in a completely different dataset. However, as mentioned above, in order for these datasets to be effective tools for underscoring the importance of visualizing your data, they need to be **visually distinct** and **clearly different**. We accomplish this by biasing the random point movements towards a particular shape. In the animation below, we show the process of 200,000 iterations of perturbations towards a 'circle' shape:

![](https://d2f99xq7vri1nk.cloudfront.net/CloudToCircle.gif)

> _Fig 4. Transforming a random cloud of points into a circle, while maintaining the same statistical properties._

To move the points towards a particular shape, we perform an additional check at each random perturbation. Besides checking that the statistical properties are still valid, we also check to see if the point has moved closer to the target shape. If both of those conditions are met, we "accept" the new position, and move to the next iteration. To mitigate the possibility of getting stuck in a locally-optimal solution, where other, more globally-optimal solutions closer to the target shape are possible, we use a [simulated annealing](https://en.wikipedia.org/wiki/Simulated_annealing) technique which begins by accepting some solutions where the point moves away from the target in the early iterations, and reduces the frequency of such acceptances over time.

To generate the Datasaurus Dozen, we created 12 shapes to direct the dots towards. Each of the resulting plots has the same summary statistics as the original Datasaurus, and in fact, all of the intermediate frames do as well. The process of converting the Datasaurus into each of these shapes can be seen below. Of course, the technique is not limited to these shapes, any collection of line segments could be used as a target.

![](https://d2f99xq7vri1nk.cloudfront.net/AllDinosAnimatedSmaller.gif)

> _Fig 5. Creating all of the datasets for the Datasaurus Dozen. The inputs are the Datasaurus dataset on the left, and a set of target shapes in the middle. The iterations leading to the final datasets are shown on the right. All datasets, and all frames of the animations, have the same summary statistics (x mean=54.26, y mean=47.83, x SD=16.76, y SD=26.93, Pearson's R=-0.06)._

Iterating through the datasets sequentially, we can see how the data points morph from one shape to another, all the while maintaining the same summary statistical values to two decimal places throughout the entire process.

![](https://d2f99xq7vri1nk.cloudfront.net/DinoSequentialSmaller.gif)

> _Fig 6. Animation showing the progression of the Datasaurus Dozen dataset through all of the target shapes._

Besides the Datasaurus Dozen, we have created several other example datasets using our technique. They are explained in more detail in the [paper](https://www.autodeskresearch.com/sites/default/files/SameStats-DifferentGraphs.pdf), and can be [downloaded](https://www.autodeskresearch.com/sites/default/files/SameStatsDataAndImages.zip) for your own visualizations.

One interesting property of our technique is that it can work for visualizations other than 2D scatter plots, and statistical properties besides the standard summary statistics. In the example below each of the datasets start out as a normal distribution of points. The boxplot shown at the bottom is a standard "Tukey Boxplot" which shows the 1st quartile, median, and 3rd quartile values on the "box", and the "whiskers" showing the location of the furthest data points within 1.5 interquartile ranges from the 1st and 3rd quartiles. Boxplots are commonly used to show the distribution of a dataset, and are better than simply showing the mean or median value. However, here we can see as the distribution of points changes, the box-plot remains the same.

![](https://d2f99xq7vri1nk.cloudfront.net/boxplots.gif)

> _Fig 7. Three varying 1D distributions of data, all with the same boxplot representation._

The datasets presented on this page (and in the paper) are available for [download](https://www.autodeskresearch.com/sites/default/files/SameStatsDataAndImages.zip). The Python source code will be released and available shortly.

A special thanks to Alberto Cairo for creating the Datasaurus. When I [asked](https://twitter.com/albertocairo/status/770257879689404416) if he had saved the datapoints from his original tweet, he hadn't, but he very graciously (and quickly!) created a new (and even better) dinosaur drawing I could use. Also thanks to [Fraser Anderson](https://www.autodeskresearch.com/people/fraser-anderson) for the idea to start with an existing dataset which has the desired statistical properties, rather than try to create one from scratch.

For more information, please see the [research paper](https://www.autodeskresearch.com/sites/default/files/SameStats-DifferentGraphs.pdf) or watch the longer video embedded below.   
For questions, please contact Justin Matejka through email [Justin.Matejka@Autodesk.com](mailto:Justin.Matejka@Autodesk.com?subject=Video Lens) or on Twitter [@JustinMatejka](https://twitter.com/JustinMatejka). I will be presenting this work at the [CHI 2017](https://chi2017.acm.org/) conference, so if you'll be there, come and see the talk.
