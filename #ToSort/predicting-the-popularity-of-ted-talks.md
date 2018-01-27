# Predicting the Popularity of TED Talks

_Captured: 2017-10-24 at 20:26 from [dzone.com](https://dzone.com/articles/predicting-ted-talks-popularity?edition=334723&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-24)_

[Bring the power of Artificial Intelligence to IT Operations](https://dzone.com/go?i=247358&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html). Brought to you in partnership with [BMC](https://dzone.com/go?i=247358&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html).

Everyone knows [TED Talks](https://www.ted.com/). TED started in 1984 as a conference series on technology, education, and design. In essence, TED Talks aim to democratize knowledge. Nowadays, it produces more than 200 talks per year addressing [dozens of different topics](https://www.ted.com/topics). Despite the [critics](https://www.theguardian.com/commentisfree/2013/dec/30/we-need-to-talk-about-ted) who claim that TED Talks reduce complex ideas to 20-minute autobiographical stories of inspiration, the [great influence](https://hbr.org/2014/04/what-i-learned-watching-150-hours-of-ted-talks) they have on the knowledge diffusion in our society is undeniable.

![](https://littleml.files.wordpress.com/2017/10/screen-shot-2017-10-19-at-8-02-10-am.png?w=497)

When I came across the [TED dataset in Kaggle](https://www.kaggle.com/rounakbanik/ted-data-analysis/data), the first thing that caught my attention was the great dispersion in the number of views: from _50K_ to over _47M_ (with a median of ~1M views). One can't help but wonder what makes some talks 20x more popular than others. Can the TED organizers and speakers do something to maximize the views in advance? In this blog post, we'll try to predict the popularity of TED Talks and analyze the most influential factors.

## The Data

![](https://littleml.files.wordpress.com/2017/10/dataset.png?w=497)

For text fields, we can inspect the word frequency in a tag cloud. For example, the most used words in the titles are "world," "life," and "future."

![](https://littleml.files.wordpress.com/2017/10/tag-cloud1.png?w=497)

When we take a look at the features, we see two main sets: one that_ informs us about the talk impact_ (comments, languages, and views [our objective field]) and another that _describes the talk characteristics_ (title, description, transcript, speakers, duration, etc). Apart from the original features, we came up with two additional ones: _the days between video creation and publishing_ and _the days between publishing and dataset collection_ on September 21, 2017.

## Extracting the Topics of TED Talks

The coolest thing about BigML topic models is that you don't need to worry about text pre-processing. It's very handy that BigML automatically cleans the punctuation marks, homogenizes the cases, excludes [stopwords](https://en.wikipedia.org/wiki/Stop_words), and applies [stemming](https://en.wikipedia.org/wiki/Stemming) during the topic model creation. You can also fine-tune those settings and include [bigrams](https://en.wikipedia.org/wiki/Bigram) as you wish by configuring your topic model in advance.

![](https://littleml.files.wordpress.com/2017/10/topic-model.png?w=497)

When our topic model is created, we can see that BigML has found 40 different topics in our TED Talks including technology, education, business, religion, politics, and family, among others. You can see all of them in a circle map visualization, in which each circle represents a topic. The size of the circle represents the importance of that topic in the dataset, and related topics are located closer in the graph. Each topic is a distribution over term probabilities. If you mouse over each topic, you can see the top 20 terms and their probabilities within that topic. BigML also provides another visualization in which you can see all the top terms per topic displayed in horizontal bars. You can observe both views below, or better yet, inspect the model by yourself [here](https://bigml.com/shared/topicmodel/3hHaAqxQuf3vJ99X3nUiW0uCiDJ)!

![](https://i0.wp.com/g.recordit.co/N0mNhF6BlL.gif)

BigML topic models are an optimized implementation of [latent Dirichlet allocation](https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation) (LDA), one of the most popular probabilistic methods for topic modeling. If you want to learn more about topic models, please read the [documentation](https://static.bigml.com/pdf/BigML_Topic_Modeling.pdf).

![](https://i2.wp.com/g.recordit.co/xZfeW0SKJz.gif)

Now, we want to do the same for our TED Talks. To calculate the topic probabilities for each TED Talk we use the option **Batch Topic Distribution** in the 1-click action menu. Then, we select our TED Talks dataset. We also need to make sure that the option to create a new dataset out of the topic distribution is enabled!

![](https://littleml.files.wordpress.com/2017/10/topic-distribution.png?w=497)

When the batch topic distribution is created, we can find the new dataset with additional numeric fields, containing the probabilities of each topic per TED Talk. These are the fields that we will use as inputs to predict the views replacing the transcript, title, description, and tags.

![](https://littleml.files.wordpress.com/2017/10/ted-dataset-topics.png?w=497)

## Predicting the TED Talks Views

![](https://littleml.files.wordpress.com/2017/10/discretization.png?w=497)

Then, we click the button to create a dataset. The dataset contains a new field with two classes -- the first class containing the talks below the median number of views (less than 1M views) and the second class containing the talks over the median number of views (more than 1M views).

![](https://littleml.files.wordpress.com/2017/10/views-discretize.png?w=497)

Before creating our classification model, we need to split our dataset into two subsets: the 80% for training and the remaining 20% for testing to ensure that our model generalizes well against data that the model has not seen before. We can easily do this in BigML by using the corresponding option in the 1-click action menu, as shown below.

![](https://littleml.files.wordpress.com/2017/10/split-dataset.png?w=497)

We proceed with the 80% of our dataset to create our predictive model. To compare how different algorithms perform, we create a single tree, an ensemble (random decision forest), a logistic regression, and the latest addition to BigML, Deepnets (an optimized implementation of the popular deep neural networks). You can easily create those models from the dataset menus. BigML automatically selects the last field in the dataset as the objective field **Views (discretized)** so we don't need to configure it differently. Then we use the 1-click action menu to easily create our models.

![](https://littleml.files.wordpress.com/2017/10/select-model.png?w=497)

Apart from the 1-click Deepnet, which uses an automatic parameter optimization option called Structure Suggestion, we also create another Deepnet by configuring an alternative automatic option called Network Search. BigML offers this unique capability for [automatic parameter optimization](https://blog.bigml.com/2017/10/04/deepnets-behind-the-scenes/) to eliminate the difficult and time-consuming work of hand-tuning your Deepnets.

![](https://littleml.files.wordpress.com/2017/10/deepnets-config.png?w=497)

After some iterations, we realize that the features related to the speaker have no effect on the number of views; therefore, we eliminate those along with the field "event" that seems to be causing overfitting. At the end, we use as input fields all the topics, the year of the published date, the duration of the talk, plus our calculated field that measures the number of days since the published date (until September 21, 2017).

After creating all the models with these selected features, we need to evaluate them by using the remaining 20% of the dataset that we set aside earlier. We can easily compare the performance of our models with the BigML evaluation comparison tool, where the can be analyzed altogether. As seen below, the winner with the highest [AUC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic#Area_under_the_curve) (0.776) is a Deepnet that uses the automatic parametrization option "Network Search." The second best performing model is again a Deepnet, but the one using the automatic option "Structure Suggestion." This one has an AUC value of 0.7557. In third place, we see the ensemble (AUC of 0.7469), followed by logistic regression (AUC of 0.7097) and finally the single tree (AUC of 0.6781).

![](https://littleml.files.wordpress.com/2017/10/compare-evals1.png?w=497)

When we take a look at the [confusion matrix](https://en.wikipedia.org/wiki/Confusion_matrix) of our top performing Deepnet, we can see that we are achieving over with a 70% precision for both classes of the objective field.

![](https://littleml.files.wordpress.com/2017/10/confusion-matrix.png?w=497)

## Inspecting the Deepnet

Usually, deep neural network predictions are hard to analyze. That's why BigML provides ways to make it easy for you to understand why your model is making particular decisions.

![](https://littleml.files.wordpress.com/2017/10/importances.png?w=497)

Great! We can state that our Deepnet found the topics as relevant predictors in deciding the number of views. But how exactly do these topics impact predictions? Will talks about psychology have more or fewer views than talks about science? To answer this question, BigML provides a Partial Dependence Plot view, where we can analyze the marginal impact of the input fields on the objective field. Let's see some examples (or play with the visualization [here](https://bigml.com/shared/deepnet/iKmcP9gp9kwJFhdwSyV26tq06Qo) at your leisure).

For example, see in the image below how the combination of the topics "entertainment" and "psychology" have a positive impact on the number of views. Higher probabilities of those topics result in the prediction of our second class (the blue one), which is the class over 1M number of views.

![](https://littleml.files.wordpress.com/2017/10/pdp1.png?w=497)

On the contrary, if we select **Health** instead, we can see how higher probabilities of this topic result in a higher probability of predicting the 1st class (the class below 1M number of views).

![](https://littleml.files.wordpress.com/2017/10/pdp2.png?w=497)

We can also see a change over time in the interest in some topics. As you can see below, the probability of the psychology topic to have more than 1M views has increased in the recent years given the period of 2012 to 2017.

![](https://littleml.files.wordpress.com/2017/10/pdp3.png?w=497)

## Conclusion

In summary, we have seen that topics _do_ have a significant influence on the number of views. After analyzing the impact of each topic in predictions, we observe that "positive" topics such as entertainment or motivation are more likely to have a greater number of views while talks with higher percentages of the "negative" topics like diseases, global issues, or war are more likely to have fewer views. In addition, it seems that the interest in individual human-centered topics such as psychology or relationships has increased over the years to the detriment of broader social issues like health or development.

[TrueSight is an AIOps platform](https://dzone.com/go?i=247359&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html), powered by machine learning and analytics, that elevates IT operations to address multi-cloud complexity and the speed of digital transformation.
