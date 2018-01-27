# Deep Dive Into Machine Learning

_Captured: 2017-11-03 at 18:41 from [dzone.com](https://dzone.com/articles/deep-dive-into-machine-learning?edition=334833&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-03)_

[Find out how AI-Fueled APIs from Neura](https://dzone.com/go?i=244221&u=https%3A%2F%2Fhubs.ly%2FH08wTJ10) can make interesting products more exciting and engaging.

We now live in an age where machine learning is a hot topic. Machines can learn on their own without human intervention, and at the same time, it can bring humans closer to machines by enabling humans to "teach" machines. Machine learning has been around for several decades, but only recently have we been able to take advantage of this technology thanks to the recent advancements made in computing power.

> "Machine learning is the field of study that gives computers the ability to learn without being explicitly programmed." -- Arthur Samuel, machine learning pioneer 

Now, let's look at a quick timeline of machine learning:

![Image title](https://dzone.com/storage/temp/7047865-screen-shot-2017-10-27-at-43929-pm.png)

![Image title](https://dzone.com/storage/temp/7047877-screen-shot-2017-10-27-at-44212-pm.png)

## How It Works

Machine learning (ML) deals with systems and algorithms focused on identifying patterns within data and making predictions by finding hidden patterns in data. It is worth mentioning here that machine learning falls under the artificial intelligence (AI) umbrella, which in turn intersects with the broader fields of data mining and knowledge discovery.

![Image title](https://dzone.com/storage/temp/7047891-screen-shot-2017-10-27-at-44728-pm.png)

## Other Examples of ML Usage

Other examples of machine learning include the following:

  * **Healthcare**: Identifying at-risk customers; optimizing diagnostic accuracy; health plan cost improvements.

  * **Social**: Ad campaign performance predictions; consumer sentiments/feedback predictions.

  * **Aeronautics**: Rocket engine explosion predictions; pilot aptitude predictions; flight route predictions.

There are other industries, as well, with high hopes for how they can be used to garner business value by utilizing this technology. In fact, according to the [PwC 2017 Global Digital IQ Survey](http://www.pwc.com/us/en/advisory-services/digital-iq.html?WT.mc_id=CT10-PL101-DM2-TR2-LS2-ND30-BPA1-CN_2017DigitalIQ2-US), 54% of organizations are investing substantially in AI and machine learning.

## How It Is Done

Machine learning tasks are divided into three categories.

### 1\. Supervised ML

Most of the time, machine learning relies on data being labeled as true or false.

**Example**: Teaching a computer to identify a potential fraudulent or non-fraudulent transaction based on the transaction labels done by humans to guarantee high-quality data. Having learned the difference between a fraudulent and non-fraudulent transaction, the ML will automatically classify the new transaction data to get hold of a potentially fraudulent activity.

### 2\. Unsupervised ML

This type of algorithm doesn't depend on data label the way that supervised learning does. Usually, it involves provisioning the ML algorithm with a large amount of data on every aspect of an object.

**Example**: Presented with various attributes of a fraudster along with some transactional values where a fraud has happened, unsupervised ML can separate the transactions into two distinct groups based on the inherent and described characteristics of the transaction.

### 3\. Reinforced ML

**Example**: Learning to play Othello, a very popular board game, ML receives information on whether a player won or lost. The program doesn't have all the moves in its database marked as won or lost but _does_ know the end result of the entire game. The ML can then play a number of games, each time giving importance to those moves which are resulting in a winning combination.

## Some Popular Approaches

There is a multitude of approaches employed in ML. Here are some of the most common ones.

### Decision Tree Learning

A predictive model that maps observations about an item to draw conclusions; uses a hierarchy of decision nodes that, when answered step-by-step, can classify a transaction as fraudulent or not.

![Image title](https://dzone.com/storage/temp/7047921-screen-shot-2017-10-27-at-45916-pm.png)

### Regression Learning

Regression learning is one of the most important and broadly used machien learning and statistical tools. It has the ability to make predictions from data by learning the relationship between the dependent and predictor variables.

![Image title](https://dzone.com/storage/temp/7047932-screen-shot-2017-10-27-at-50214-pm.png)

### Naive Bayes Learning

This is a probabilistic graphical model that represents a set of random variables and their conditional independencies; for example, the probabilistic relationships in between a fraudster and transaction amount, age, behavior, etc.

![Image title](https://dzone.com/storage/temp/7047943-screen-shot-2017-10-27-at-50515-pm.png)

### Neural Net Learning

Neural net learning consists of multiple hidden layers and mimics the behavior of the human brain. Deep learning included multiple neural networks put one after the other.

![Image title](https://dzone.com/storage/temp/7047954-screen-shot-2017-10-27-at-50756-pm.png)

## Use Case: Fight Financial Fraud Using Machine Learning

Financial fraud has posed a big concern across the globe for many organizations in various countries, as it brings a lot of credibility loss and financial devastation to a business. Millions of families suffer every year due to financial fraud; financial damage extends to hundreds of millions of US dollars.

In the past, a leading financial institution agreed to pay $16.5 billion dollars to settle a financial fraud case. Considering all these cases, it becomes very important to bring data mining tools and techniques to detect a probable fraudulent activity or an incident.

Before we look at the data mining techniques that can help us identify a fraudulent activity, it's a good idea to look at the fraud landscape based on the [economic crime survey conducted by PwC in 2016](https://www.pwc.com/gx/en/services/advisory/forensics/economic-crime-survey.html).

![Image title](https://dzone.com/storage/temp/7047955-screen-shot-2017-10-27-at-51040-pm.png)

![Image title](https://dzone.com/storage/temp/7047969-screen-shot-2017-10-27-at-51237-pm.png)

> _For the detailed PwC report, click here._

## Top 3 Risk Prediction Algorithms and Use Cases

The top three risk prediction algorithms and use cases are:

  * **Classification method**: Used to generate possible values (i.e. true, false, yes, no, 0, 1, etc.). This machine learning technique can be use to classify whether a particular debt will turn out to be "good" or "bad" based on various predictor variables.

  * **Neural nets**: Show better results on large datasets consisting of neurons and nodes with input, output, and hidden layers. This method is often used to perform _credit ratings predictions _using various demographic, age, and other variables as inputs.

  * **Random decision forests**: An ensemble learning method for classification. They construct numerous decision trees at the time of training and outputting the class (that is, the mode of classes). This is extensively used to perform _credit risk predictions_.

Another emerging mathematical model that is gaining a lot of popularity in the area of financial statement fraud is the Beneish M-Score. This model uses financial ratios and eight variables to identify whether an organization has manipulated its earnings. The variables are constructed from the data in the company's financial statements and, once calculated, create an M-Score to describe the degree to which the earnings have been manipulated. Note that, being a probabilistic model, it will not identify manipulators with 100% accuracy.

## Conclusion

In conclusion, the key benefits of machine learning are:

  * **Data-driven decisions via quick integration**: With its capability to consume every sort of data, structured or unstructured, machine learning can help businesses continuously upgrade their strategies based on the most recent and up-to-date data patterns.

  * **Speed to insight**: The speed at which machine learning can identify and churn relevant data enables stakeholders to act in real-time. For example, machine learning can constantly optimize the next best offer for the customer, so what the customer might see at noon may be different than what that same customer sees in the evening.

  * **Risk aversion**: Given the fact that it's not an ideal world out there, ML gives businesses the capability to keep fraudsters at bay and mitigates potential monetary and regulatory complications.

To find out how AI-Fueled APIs can increase engagement and retention, [download Six Ways to Boost Engagement for Your IoT Device or App with AI](https://dzone.com/go?i=244222&u=https%3A%2F%2Fhubs.ly%2FH08wTJ50) today.

Opinions expressed by DZone contributors are their own.
