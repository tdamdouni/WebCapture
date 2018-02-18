# Machine Learning: An Introduction

_Captured: 2018-02-14 at 14:10 from [dzone.com](https://dzone.com/articles/machine-learning-in-finance?edition=361103&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-02-14)_

Insight for I&O leaders on deploying AIOps platforms to enhance performance monitoring today. [Read the Guide](https://dzone.com/go?i=260321&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2Fgartner-market-guide-for-aiops-platforms-2017.html%3Fcid%3Dpt-PA_STA_All_FC_PT_Gartner_AIOps_Market_Guide_Dzone_Analyst_Report-AB-03-f-08232017%26cc%3Dpt%26elqcid%3D4114%26sfcid%3D7011O0000027wFd).

Machine learning is a method of data analysis that automates analytical model building. It uses algorithms that iteratively learn from data. It basically allows computers to find hidden insights and patterns without being explicitly programmed on where to look.

A formal definition by Tom Mitchell:

> A computer program is said to learn from experience E with respect to some task T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E. 

Facebook face recognition is a good example of machine learning. If you are posting a group picture of ten people and all these people are a member of Facebook and have their own profile picture, Facebook face recognition will advise you to tag specific friends; even though lighting, poses, and other factors make the people look different.

## **Machine Learning Categorization**

  * Text categorization, i.e. spam filtering

  * Fraud detection, i.e. credit card fraud

  * Machine vision, i.e. image processing/face detection

  * Natural language processing, i.e. spoken language understanding

  * Market segmentation, i.e. predict if customer will respond to a promotion

  * Bioinformatics, i.e. pharmacy trying to understand if an antibiotic will treat a cold

## **Types of Machine Learning**

  * **Supervised learning**: The algorithm has training data with a known expected output. Example: credit card fraud detector.

  * **Unsupervised learning**: The algorithm identifies patterns in the data without being told the expected outcome. Example: anomaly detection.

  * **Reinforcement learning**: The algorithm learns from interactions with the environment. It uses trial-and-error and memorizes strategy for further improvement. Example: chess program.

**Note**: Supervised learning is best suited for the finance domain.

## **Types of Machine Learning Algorithms**

  * **Classification**: A set of data is given, and your answer is one of the pieces of data.

  * **Regression**: Used to find numbers (numeric value).

  * **Anomaly detection**: Analyzes patterns, i.e. credit card fraud detection.

  * **Clustering**: Used if we need to know about structure; forms groups to interpret the data.

  * **Reinforcement**: Used when a decision needs to be made based on past experience and the environment.

## **Linear Classification**

Classification and regression are two types of machine learning problems and are categorized by desired output. First, we should identify our problem in either of these two to find a suitable algorithm.

### **Regression**

We are modeling the relationship between a continuous input variable X and a continuous target variable T.

For example, suppose you want to predict if the market will go high or low, but the desired output is a price series. Mid-price, volume, and continuous volatility will be used to get the target variable price series.

### **Classification**

The input variable X may still be continuous, but the target variable X is discrete.

  * T=1 if assigned to C1.

  * T=0 if assigned to C2.

For example, suppose you want to predict if the market will go high or low. Mid-price, volume, and continuous volatility will be used to get the discrete target variable price. In this case, if the price goes up, it's +1; if the price goes down, it's 0 or -1.

### **Regression vs. Classification**

  * Classification is more advisable if we see what we do with prediction.

  * Long-term trading organizations use classification.

  * Regression is advisable when the cost of a few mistakes doesn't cancel out being right most of the time.

  * Most high-frequency trading organizations use regression.

## **Steps of Machine Learning**

It doesn't matter that which machine learning model you use, these 4 steps are pretty common.

  * **Prepare the data**: Get the raw data and structure it. 

  * **Train the model**: Use the data and train the model.

  * **Test the model**: Test the model with some test data; do the model fitting and test it again. Repeat to get the best model.

  * **Deploy the model**: Once satisfied with the model, deploy it to use.

## **Collateral Management Scenario**

In the case of collateral management where the collateral is a security (let's say a house) that needs to be priced.

Here, if we have 70K pieces of data about houses, we will split the data into three parts:

  1. **Training set**: Train model (60% training)

  2. **Cross-validation**: 20% 

  3. ** Test set**: Test the model (20% test)

If this doesn't give you a satisfactory result, then adjust the model (known as model fitting).

Happy learning!

[TrueSight is an AIOps platform](https://dzone.com/go?i=247359&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html), powered by machine learning and analytics, that elevates IT operations to address multi-cloud complexity and the speed of digital transformation.

Topics:

machine learning ,ai ,classification ,linear regression ,tutorial ,algorithms ,image recognition ,data analytics

Opinions expressed by DZone contributors are their own.
