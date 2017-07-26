# Trying to Fill in Missing Values

_Captured: 2017-06-12 at 13:50 from [dzone.com](https://dzone.com/articles/trying-to-fill-in-missing-values?edition=304169&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-11)_

Need to build an application around your data? [Learn more](https://dzone.com/go?i=200129&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) about dataflow programming for rapid development and greater creativity.

I've been playing around with the data in Kaggle's [House Prices: Advanced Regression Techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques) and while replicating [Poonam Ligade's exploratory analysis](https://www.kaggle.com/poonaml/house-prices-data-exploration-and-visualisation), I wanted to see if I could create a model to fill in some of the missing values.

Poonam wrote the following code to identify which columns in the dataset had the most missing values:
    
    
    null_columns=train.columns[train.isnull().any()]
    
    
    >>> print(train[null_columns].isnull().sum())

The one that I'm most interested in is `LotFrontage`, which describes "linear feet of street connected to property." There are a few other columns related to lots so I thought I might be able to use them to fill in the missing `LotFrontage` values.

We can write the following code to find a selection of the rows missing a `LotFrontage` value:
    
    
    cols = [col for col in train.columns if col.startswith("Lot")]
    
    
    missing_frontage = train[cols][train["LotFrontage"].isnull()]
    
    
    >>> print(missing_frontage.head())

I want to use [scikit-learn](http://scikit-learn.org/)'s [linear regression model](http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html), which only works with numeric values, so we need to convert our categorical variables into numeric equivalents. We can use the pandas `[get_dummies](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.get_dummies.html)` function for this.

Let's try it out on the `LotShape` column:
    
    
    sub_train = train[train.LotFrontage.notnull()]
    
    
    dummies = pd.get_dummies(sub_train[cols].LotShape)
    
    
    >>> print(dummies.head())

Cool, that looks good. We can do the same with `LotConfig` and then we need to add these new columns onto the original DataFrame. We can use pandas `[concat](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.concat.html)` function to do this.
    
    
            pd.get_dummies(sub_train[cols].LotShape),
    
    
            pd.get_dummies(sub_train[cols].LotConfig)
    
    
        ], axis=1).select_dtypes(include=[np.number])
    
    
    >>> print(data.head())

We can now split data into train and test sets and create a model.
    
    
    X = data.drop(["LotFrontage"], axis=1)
    
    
    X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=42, test_size=.33)
    
    
    model = lr.fit(X_train, y_train)

Now it's time to give it a try on the test set:

Hmm, that didn't work too well. An R^2 score of less than 0 suggests that we'd be better off just predicting the average `LotFrontage` regardless of any of the other features. We can confirm that with the following code:
    
    
    >>> print(r2_score(y_test, np.repeat(y_test.mean(), len(y_test))))

Whereas if we had all of the values correct, we'd get a score of 1:

In summary, not a very successful experiment. Poonam derives a value for `LotFrontage` based on the square root of `LotArea`, so perhaps that's the best we can do here.

[Check out](https://dzone.com/go?i=200130&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) the Exaptive data application Studio. Technology agnostic. No glue code. Use what you know and rely on the community for what you don't. [Try the community version](https://dzone.com/go?i=200130&u=https%3A%2F%2Fexaptive.city%2F%23%2Flanding%3Freferrer%3DGeneral).
