# Deep Learning and the Stock Market

_Captured: 2017-04-23 at 10:14 from [dzone.com](https://dzone.com/articles/deep-learning-and-the-stock-market?edition=292908&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-22)_

Need to build an application around your data? [Learn more](https://dzone.com/go?i=200129&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) about dataflow programming for rapid development and greater creativity.

The financial industry has been one of the more enthusiastic exponents of automation in recent years -- especially on the trading floor, where algorithmic trading is now commonplace. Indeed, [Commerzbank](https://www.commerzbank.de/en/hauptnavigation/presse/pressemitteilungen/archiv1/2016/quartal_16_03/presse_archiv_detail_16_03_61258.html) has been outspoken about its desire to automate 80% of its processes in the coming years.

A sign of the progress being made comes via a recent [paper](http://dx.doi.org/10.1016/j.ejor.2016.10.031) published by the School of Business and Economics at Friedrich-Alexander-Universitat Erlangen-Nurnberg (FAU). It shows the potential for algorithms to make extremely profitable investment decisions.

When the algorithm was applied to members of the S&P 500 between 1992 and 2015, the picks generated double-digit annual returns, with a particular strength during times of economic turmoil.

## AI and Capital Market Data

> "Equity markets exhibit complex, often non-linear dependencies," the team say. "However, when it comes to selecting stocks, established methods are mainly modeling simple relationships. For example, the momentum effect only focuses on a stock's return over the past months and assumes a continuation of that performance in the months to come. We saw the potential for improvements."

The researchers used a combination of Deep Learning, gradient boosting, and random forests to generate daily predictions for every stock in the S&P 500 during the time period.

Each method was trained using 180 million different data points, with the algorithms developing knowledge of a complex function that described the relationship between the price-based features of the stock, and its future performance, with impressive results.

> "Since the year 2000, we observed statistically and economically significant returns of more than 30% per annum. In the nineties, results were even higher, reflecting a time when our machine learning approaches had not yet been invented," the authors say. 

## Overcoming the Efficient Market

The authors believe their work poses a considerable challenge to the efficient-market hypothesis with returns from the algorithm particularly strong during turbulent periods such as the dot-com crash or the global credit crunch in 2008. The authors believe this is because such periods tend to see emotion driving investment decisions.

While the results are undoubtedly promising, the researchers urge a degree of caution, and not to go overboard in any belief that such an approach represents a holy grail.

> "In the latter years of the study profitability fell and even dipped into the negative at times. We assume that this decline was driven by the rising influence of artificial intelligence in modern trading - facilitated by increasing computing power and the popularization of Machine Learning. We assume that the downturn may have been caused by the increasing influence of Artificial Intelligence in modern trading," they say. 

They're looking to refine the process however by feeding the algorithms with much bigger data sets and deeper network architectures to help identify temporal dependencies. In early tests of this modified approach, the forecasting ability and quality rose significantly, even against modern algorithmic peers. It will be a project to watch with interest.

[Check out](https://dzone.com/go?i=200130&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) the Exaptive data application Studio. Technology agnostic. No glue code. Use what you know and rely on the community for what you don't. [Try the community version](https://dzone.com/go?i=200130&u=https%3A%2F%2Fexaptive.city%2F%23%2Flanding%3Freferrer%3DGeneral).
