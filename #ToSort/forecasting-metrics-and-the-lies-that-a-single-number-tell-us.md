# Forecasting, Metrics and the Lies that a Single Number Tell Us

_Captured: 2017-03-05 at 11:53 from [agilepainrelief.com](https://agilepainrelief.com/notesfromatooluser/2016/07/forecasting-metrics-and-the-lies-that-a-single-number-tell-us.html#.WLvuFru1KaM)_

We've previously seen that our [mental models](http://agilepainrelief.com/notesfromatooluser/2016/03/bell-curves-and-measuring-badly.html) often make false assumptions due to cognitive bias. Giving a Single number in a report has a similar problem.

The classic Agile number is 'Velocity': the average rate at which your team delivers work. It is often shared as just one number. E.g. our team achieves 20 pts a Sprint.

You're walking and come to a river - there is a sign that says the average depth is 1 foot. Can you safely walk across? You don't know. For most of its width, the river may be only 6 inches deep, but for a critical 1 foot stretch, it's 6 feet deep. Not safe to cross.

You're told the average grade on a test in your class is 75%. What does this tell you about your own mark? Nothing.

The problem with reporting velocity as a single number is that it implies the average number will continue into the future at the same rate. It implies that there will never be any variance.

Consider reporting a range[[1]](https://agilepainrelief.com/notesfromatooluser/2016/07/forecasting-metrics-and-the-lies-that-a-single-number-tell-us.html)[[2]](https://agilepainrelief.com/notesfromatooluser/2016/07/forecasting-metrics-and-the-lies-that-a-single-number-tell-us.html).

  * Best three sprints in the past year - this is the highest you're likely to achieve
  * Last three sprints - you're 50% likely to achieve this number
  * Worst three sprints in the past year - the least you're likely to achieve
![Forecasting Metrics burndown](https://agilepainrelief.com/wp-content/uploads/2016/07/Forecasting-Metrics-burndown-e1468266364183.jpg)

Along with projecting a cone of uncertainty in your burndown/burnup/cumulative flow diagram, it can also be used to illustrate which items in the product backlog are more or less likely to be achieved by drawing lines in the product backlog.

If you need a more sophisticated model than these, consider using a Monte Carlo simulation. Larry Maccherone has a Chrome only example: <http://lumenize.com/> and code showing how he uses it: <https://jsfiddle.net/lmaccherone/j3wh61r7/>.

![Forecasting Metrics confidence line](https://agilepainrelief.com/wp-content/uploads/2016/07/Forecasting-Metrics-confidence-line.jpg)

With five Sprints to go, we have a clear picture of where in the product backlog we will likely get.

So instead of forecasting a number, now we're forecasting which items will be delivered, i.e. we're forecasting value. This drives a better quality conversation because we can have real discussions about which stories or features to sort into which part of the Product Backlog.

This brings up the final problem with velocity as a number (or even range). The number of Product Backlog Items, Features, or User Stories don't necessarily correlate with how happy the customer is. A small feature may delight the customer if it's done well (example: ability to freeze the first row in Excel), while a large feature (example: SmartArt in Word) may not make the customer(s) happy.

So even with ranges and probabilities, the use of numbers can still hide the most important thing: **Is the customer happy?**

_Image attribution: Agile Pain Relief Consulting_

[1] Note that even this model of reporting velocity has an implicit bell curve behind it.  
[2] Even elections are now forecast with ranges by the better forecasters: Eric Grenier: <http://www.threehundredeight.com/2015/10/final-federal-projection-likely-liberal.html>
