# Important Machine Learning Algorithms

_Captured: 2017-12-29 at 20:19 from [dzone.com](https://dzone.com/articles/important-machine-learning-algorithms?edition=347143&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-29)_

Insight for I&O leaders on deploying AIOps platforms to enhance performance monitoring today. [Read the Guide](https://dzone.com/go?i=260321&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2Fgartner-market-guide-for-aiops-platforms-2017.html%3Fcid%3Dpt-PA_STA_All_FC_PT_Gartner_AIOps_Market_Guide_Dzone_Analyst_Report-AB-03-f-08232017%26cc%3Dpt%26elqcid%3D4114%26sfcid%3D7011O0000027wFd).

This article aims to take on a few of the [machine learning](http://whatis.techtarget.com/definition/machine-learning) algorithms for people who aim to gain knowledge on important machine learning concepts while using freely available materials and resources along the way. The prime objective of this outline is to help you wade through the numerous free options that are available. There are many, to be sure, but which are the best? Which complement one another? What is the best order in which to use selected resources?

Common machine learning algorithms include:

  1. Decision tree
  2. SVM
  3. Naive Bayes
  4. KNN
  5. K-Means
  6. Random forest
![Image title](https://dzone.com/storage/temp/7609718-machine-learning.jpg)

Below are the common machine learning Algorithms briefly explained with [Python](https://mindmajix.com/python-training) and R code.

## Decision Tree

This is one of my favorite algorithms and I use it quite frequently. It is a type of supervised learning algorithm that is mostly used for classification problems. Surprisingly, it works for both categorical and continuous dependent variables. In this algorithm, we split the population into two or more homogeneous sets. This is done based on significant attributes and independent variables to make groups as distinct as possible.

**Python code**:

**R code**:
    
    
    x <- cbind(x_train,y_train)
    
    
    fit <- rpart(y_train ~ ., data = x,method="class")

## SVM (Support Vector Machine)

This is a classification method. In this algorithm, we plot each data item as a point in an _n_-dimensional space (where _n_ is the number of features you have), with the value of each feature being the value of a particular coordinate.

For example, if we only had two features, like height and hair length of an individual, we'd first plot these two variables in a two-dimensional space where each point has two coordinates (which are known as support vectors).

Now, we will find some line that splits the data between the two differently classified groups of data. This will be the line from which the distances between the closest points in each of the two groups will be farthest away.

**Python code**:

**R code**:
    
    
    x <- cbind(x_train,y_train)
    
    
    fit <-svm(y_train ~ ., data = x)

## Naive Bayes

This is a classification technique based on Bayes' theorem with an assumption of independence between predictors. In simple terms, a Naive Bayes classifier assumes that the presence of a particular feature in a class is unrelated to the presence of any other feature. For example, a fruit may be considered to be an apple if it is red, round, and about three inches in diameter. Even if these features depend on each other or on the existence of the other features, a naive Bayes classifier would consider all of these properties to independently contribute to the probability that this fruit is an apple.

The Naive Bayes model is easy to build and is particularly useful for very large datasets. Along with simplicity, Naive Bayes is known to outperform even highly sophisticated classification methods.

Bayes theorem provides a way of calculating posterior probability: P(c|x) from P(c), P(x) and P(x|c).

  * P(c|x) is the posterior probability of class (target) given predictor (attribute).

  * P(c) is the prior probability of class.

  * P(x|c) is the likelihood which is the probability of predictor given class.

  * P(x) is the prior probability of predictor.

**Python code**:

**R code**:
    
    
    x <- cbind(x_train,y_train)
    
    
    fit <-naiveBayes(y_train ~ ., data = x)

## KNN (K-Nearest Neighbors)

This can be used for both classification and regression problems. However, it is more widely used in classification problems in the ML industry. K-nearest neighbors is a simple algorithm that stores all available cases and classifies new cases by a majority vote of its K neighbors. The case assigned to the class is the most common amongst its K-nearest neighbors, measured by a distance function.

These distance functions can be Euclidean, Manhattan, Minkowski, or Hamming distance. The first three functions are used for continuous functions and Hamming is used for categorical variables. If K = 1, then the case is simply assigned to the class of its nearest neighbor. At times, choosing K turns out to be a challenge while performing KNN modeling.

KNN can easily be mapped to our real lives. If you want to learn about a person about whom you have no information, you might like to find out about their close friends and the circles they move in to gain access to their information!

Things to consider before selecting KNN:

  * KNN is computationally expensive.
  * Variables should be normalized, or else higher-range variables can bias it.
  * Works on the pre-processing stage more before going for KNN, like outlier/noise removal.

**Python code**:

**R code**:
    
    
    x <- cbind(x_train,y_train)
    
    
    fit <-knn(y_train ~ ., data = x,k=5)
    
    
    predicted= predict(fit,x_test)

## K-Means

This is a type of unsupervised algorithm that solves clustering problems. Its procedure follows a simple and easy way to classify a given dataset through a certain number of clusters (assume K clusters). Data points inside a cluster are homogeneous and heterogeneous to peer groups.

Remember figuring out shapes from ink blots? K-means is somewhat similar this activity. You look at the shape and spread to decipher how many different clusters/populations are present!

How K-means forms a cluster:

  1. K-means picks K number of points for each cluster, known as centroids.
  2. Each data point forms a cluster with the closest centroids, i.e. K clusters.
  3. Finds the centroid of each cluster based on existing cluster members. Here, we have new centroids.
  4. As we have new centroids, repeat Steps 2 and 3. Find the closest distance for each data point from new centroids and get associated with new K clusters. Repeat this process until convergence occurs, i.e. centroids do not change.

### How to Determine the Value of K

In K-means, we have clusters and each cluster has its own centroid. The sum of the square of the difference between the centroid and the data points within a cluster constitutes the sum of the square value for that cluster. Also, when the sum of square values for all the clusters is added, it becomes the total within the sum of square values for the cluster solution.

We know that as the number of cluster increases, this value keeps decreasing, but if you plot the result, you may see that the sum of squared distance decreases sharply up to some value of K, and then much more slowly after that. Here, we can find the optimum number of cluster.

**Python code**:

**R code**:

## Random Forest

Random forest is a trademark term for an ensemble of decision trees. In a random forest, we have a collection of decision trees known as a forest. To classify a new object based on attributes, each tree gives a classification and we say the tree "votes" for that class. The forest chooses the classification with the most votes (over all the trees in the forest).

Each tree is planted and grown as follows:

  1. If the number of cases in the training set is N, then the sample of N cases is taken at random but with a replacement. This sample will be the training set for growing the tree.
  2. If there are M input variables, a number m<<M is specified such that at each m variable is selected at random out of the M and the best split on the m is used to split the node. The value of m is held constant during the forest's growth.
  3. Each tree is grown to the largest extent possible. There is no pruning.

**Python code**:

**R code**:

That's all for this time!

[TrueSight is an AIOps platform](https://dzone.com/go?i=247359&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html), powered by machine learning and analytics, that elevates IT operations to address multi-cloud complexity and the speed of digital transformation.

Topics:

python ,ai ,machine learning ,algorithms ,decision tree ,svm ,naive bayes ,knn ,k-means ,random forest
