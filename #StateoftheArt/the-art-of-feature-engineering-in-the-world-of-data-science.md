# The Art of Feature Engineering in the World of Data Science

_Captured: 2018-09-14 at 07:03 from [dzone.com](https://dzone.com/articles/art-of-feature-engineering-in-the-world-of-data-sc?edition=396191&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-09-13)_

###  A look at how data science and big data teams can use data analysis, data modeling, and other techniques to solve real-world problems. 

[Hortonworks Sandbox](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) for HDP and HDF is your chance to get started on learning, developing, testing and trying out new features. Each [download](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) comes preconfigured with interactive tutorials, sample data and developments from the Apache community.

Shubham Agrawal, CEO of Balludas Information Technology talks with Hari Shrawgi, Manager of Talent Acquisition team.

## **The Problem**

_Shubham:_ Hari, we have lot of open positions to be backfilled and our engineering teams are unhappy with the hiring turn-around.

_Hari:_ But boss, we are doing our best to bring in good candidates, scheduling interviews for the earliest possible date. The problem lies within the engineering team in interviewing and providing feedback for the next rounds as quickly as possible.

_Shubham:_ Hari, we are one team and I don't like excuses. You claim to have the best Data Scientists in your team. Why don't you work with them to come up with some level of analysis and recommendation? It will help us set expectations.

Hari meets his team, Bhawna Bhardwaj, Mohit Jain, Preeti Patel, and Vasu Sharma. The team has expertise in building various forecasting and prediction models leveraging Data Science tools and techniques.

## **Brainstorming**

_Hari:_ Let's discuss a high-level approach on how we can tackle the problem that Shubham brought up this morning.

_Vasu:_ We have tons of data in our system. Let's process them and perform time series analyses to build a forecast.

_Preeti:_ Yes! Also, we can use decision trees or rule-based classifiers for recommendations.

_Bhawna:_ I guess we need to take a step backwards before we rush into a solution. With Hari and couple of us knowing the entire process of hiring, we have enough domain knowledge amongst ourselves. Let's think of what to do next.

_Mohit:_ Before we get into modeling, how about brainstorming the attributes required and have them ready for further processing?

_Vasu:_ You mean, the feature engineering. But isn't it time consuming? You know our CEO, he wants results yesterday!

_Preeti:_ Let's bring a method to the madness. How about a fishbone diagram to identify all possible causes that could potentially influence the problem? This shouldn't take much time.

## **Feature Selection**

![Hiring Cycle Time - Fishbone](https://dzone.com/storage/temp/10194365-featureengg-1.png)

> _Hiring Cycle Time - Fishbone_

_Hari:_ It's amazing to see in a short time that we were able to cover all possible influencers.

_Bhawna:_ Though we have identified all attributes, we may not be able to get the data.

_Mohit:_ Yes, we have constraints such as data privacy, sanity of collected data, and more. But we will use data transformation techniques to minimize the challenges.

_Vasu:_ Hari, we need to set the expectation that if we are unable to get key features, even after the data transformation that Mohit is referring to, the accuracy and precision of the model may be less.

_Preeti:_ We also need to be careful about over-fitting the model since we have all possible attributes and data.

## **Transforming Features**

![Image title](https://dzone.com/storage/temp/10194366-featureengg-2.png)

_Bhawna:_ I just did descriptive statistics on the data set we got. Looks like we have a few records where the expected salaries and the location of job are missing.

_Mohit:_ For the salary, since this category only has a few records, we can work with the respective hiring team to fill it in. Regarding the missing location, we can do similarity-based imputation since we have data for same hiring manager, similar job, responsibilities, and other matching criteria.

_Vasu:_ There are some rows where the class label such as the time taken to shortlist the profile itself is missing. We can't do any imputation here. Hence, it's better to ignore the records.

_Preeti:_ We can convert the expected salary into 10 bins such as 25-50k, 50-75k, etc., and replace the numeric value with the categorical ID. This will help reduce the noise and fit for the models.

## **Identifying Key Features**

_Bhawna:_ We have so many features identified. It's important we select vital few for better goodness of our model and to limit the over-fitting.

_Mohit:_ Well, we have couple of options. We can identify variables that are related to each other through correlation analysis.

![Image title](https://dzone.com/storage/temp/10194374-featureengg-3.png)

_Vasu:_ Yes, but correlation doesn't mean causation. To ensure the impact, we can conduct statistical hypothesis testing.

_Preeti:_ We can also apply Design of Experiment. This not only helps in identifying key features also in optimizing the outcome, in our case the cycle time.

_Bhawna:_ Principal Component Analysis also helps in reducing the dimensionality. It works only for numeric data like correlation analysis. That's why the feature transformation helps to convert categorical data into numeric. For example, in our problem, instead of categorizing the level as 'Associate, Senior, Principal' we can number them.

## **Exploratory Data Analysis and Modeling**

_Mohit:_ Wow, even before we apply model, we can visualize the trend and oscillation for individual features as well as the relationships.

_Vasu:_ That's the power of Exploratory Data Analysis. Visualization helps in not just 'why it happened' but also some level of recommendation.

_Preeti:_ Very true. From our analysis, it seems to be difficult to get the profile for Senior SAP consultant especially from this vendor.

_Bhawna:_ Maybe we can check the alternate by different vendors as well as working with hiring manager for the need for senior level or if we can adjust with next level.

_Hari:_ Awesome work folks. Never knew feature engineering itself can help identifying the causes and recommendations. While we continue working on implementing suitable model, I'll share this with our CEO and the next steps.

## **Conclusion**

![CEO Appreciation](https://dzone.com/storage/temp/10194395-fe4.png)

> _CEO Appreciation_

_Shubham:_ This is absolutely fantastic team! Looks like lot of work has already been done to identify the key challenges. While we explore this further, I'll work with Engineering team on addressing some of the root causes. Good job again!

_We have great predictive modeling algorithms and techniques available but let's not forget the foundation. Feature Engineering helps understanding the problem from customer perspective for whom we are building those models. After all, "Well begun is half done."_

[Hortonworks Community Connection (HCC)](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295) is an online collaboration destination for developers, DevOps, customers and partners to get answers to questions, collaborate on technical articles and share code examples from GitHub. [Join the discussion.](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295)
