# How Accurately Can Prophet Project Website Traffic?

_Captured: 2017-06-08 at 01:56 from [pbpython.com](http://pbpython.com/prophet-accuracy.html)_

![article header image](http://pbpython.com/images/prophet_prediction.png)

## Introduction

In early March, I published an [article](http://pbpython.com/prophet-overview.html) introducing [prophet](https://facebookincubator.github.io/prophet/) which is an open source library released by Facebook that is used to automate the time series forecasting process. As I promised in that article, I'm going to see how well those predictions held up to the real world after 2.5 months of traffic on this site.

## Getting Started

Before going forward, please review the prior [article](http://pbpython.com/prophet-overview.html) on prophet. I also encourage you to review the [matplotlib article](http://pbpython.com/effective-matplotlib.html) which is a useful starting point for understanding how to plot these trends. Without further discussion, let's dive into the code. If you wish to follow along, the [notebook](https://github.com/chris1610/pbpython/blob/master/notebooks/Prophet-Accuracy-Check.ipynb) is posted on github.

First, let's get our imports setup, plotting configured and the forecast data read into our DataFrame:
    
    
    import pandas as pd
    import numpy as np
    import matplotlib.pyplot as plt
    
    %matplotlib inline
    plt.style.use('ggplot')
    
    proj = pd.read_excel('https://github.com/chris1610/pbpython/blob/master/data/March-2017-forecast-article.xlsx?raw=True')
    proj[['ds', 'yhat', 'yhat_lower', 'yhat_upper']].head()
    

The projected data is stored in the ` proj` DataFrame. There are many columns but we only care about a couple of them:

ds yhat yhat_lower yhat_upper

0
2014-09-25
3.294797
2.770241
3.856544

1
2014-09-26
3.129766
2.564662
3.677923

2
2014-09-27
3.152004
2.577474
3.670529

3
2014-09-28
3.659615
3.112663
4.191708

4
2014-09-29
3.823493
3.279714
4.376206

All of the projections are based on the log scale so we need to convert them back and filter through May 20th:
    
    
    proj["Projected_Sessions"] = np.exp(proj.yhat).round()
    proj["Projected_Sessions_lower"] = np.exp(proj.yhat_lower).round()
    proj["Projected_Sessions_upper"] = np.exp(proj.yhat_upper).round()
    
    final_proj = proj[(proj.ds > "3-5-2017") &
                      (proj.ds < "5-20-2017")][["ds", "Projected_Sessions_lower",
                                                "Projected_Sessions", "Projected_Sessions_upper"]]
    

Next, I'll read in the actual traffic from March 6th through May 20th and rename the columns for consistency sake:
    
    
    actual = pd.read_excel('Traffic_20170306-20170519.xlsx')
    actual.columns = ["ds", "Actual_Sessions"]
    actual.head()
    

ds Actual_Sessions

0
2017-03-06
2227

1
2017-03-07
2093

2
2017-03-08
2068

3
2017-03-09
2400

4
2017-03-10
1888

Pandas makes combining all of this into a single DataFrame simple:
    
    
    df = pd.merge(actual, final_proj)
    df.head()
    

ds Actual_Sessions Projected_Sessions_lower Projected_Sessions Projected_Sessions_upper

0
2017-03-06
2227
1427.0
2503.0
4289.0

1
2017-03-07
2093
1791.0
3194.0
5458.0

2
2017-03-08
2068
1162.0
1928.0
3273.0

3
2017-03-09
2400
1118.0
1886.0
3172.0

4
2017-03-10
1888
958.0
1642.0
2836.0

## Evaluating the Results

With the predictions and actuals in a single DataFrame, let's see how far our projections were off from actuals by calculating the difference and looking at the basic stats.
    
    
    df["Session_Delta"] = df.Actual_Sessions - df.Projected_Sessions
    df.Session_Delta.describe()
    
    
    
    count      75.000000
    mean      739.440000
    std       711.001829
    min     -1101.000000
    25%       377.500000
    50%       619.000000
    75%       927.000000
    max      4584.000000
    

This gives us a basic idea of the errors but visualizing will be more useful. Let's use the process described in the [matplotlib article](http://pbpython.com/effective-matplotlib.html) to plot the data.
    
    
    # Need to convert to just a date in order to keep plot from throwing errors
    df['ds'] = df['ds'].dt.date
    
    fig, ax = plt.subplots(figsize=(9, 6))
    df.plot("ds", "Session_Delta", ax=ax)
    fig.autofmt_xdate(bottom=0.2, rotation=30, ha='right');
    

![Delta between projection and actual values](http://pbpython.com/images/prophet_delta.png)

> _This visualization is helpful for understanding the data and highlights a couple of things:_

  * Most of the variance shows the actual traffic being higher than projected
  * There were two big spikes in April which correspond to publish dates for articles
  * The majority of the variance was less than 1000

On the surface this may seem a little disappointing. However, we should not look at the predicted value as much as the predicted range. Prophet gives us the range and we can use the ` fill_between` function in matplotlib to display the range around the predicted values:
    
    
    fig, ax = plt.subplots(figsize=(9, 6))
    df.plot(kind='line', x='ds', y=['Actual_Sessions', 'Projected_Sessions'], ax=ax, style=['-','--'])
    ax.fill_between(df['ds'].values, df['Projected_Sessions_lower'], df['Projected_Sessions_upper'], alpha=0.2)
    ax.set(title='Pbpython Traffic Prediction Accuracy', xlabel='', ylabel='Sessions')
    fig.autofmt_xdate(bottom=0.2, rotation=30, ha='right'
    

This view restores some more confidence in our model. It looks like we had a big over prediction at the beginning of the time frame but did not predict the impact of the two articles published in the subsequent weeks. More interestingly, the majority of the traffic was right at the upper end of our projection and the weekly variability is captured reasonably well.

## Final Thoughts

So, how good was the model? I think a lot depends on what we were hoping for. In my case, I was not making any multi-million dollar decisions based on the accuracy. Additionally, I did not have any other models in place so I have nothing to compare the prediction to. From that perspective, I am happy that I was able to develop a fairly robust model with only a little effort. Another way to think about this is that if I were trying to put this model together by hand, I am sure I would not have come up with a better approach. Additionally, the volume of the views with the April 25th article is nearly impossible to predict so I don't worry about that miss and the subsequent uptick in volume.

Predictive models are rarely a one shot affair. It takes some time to understand what makes them tick and how to interpret their output. I plan to look at some of the tuning options to see which parameters I could tweak to improve the accuracy for my use case.

I hope this is useful and would definitely like to hear what others have found with prophet or other tools to predict this type of activity. For those of you with experience predicting website traffic, would this have been a "good" outcome?
