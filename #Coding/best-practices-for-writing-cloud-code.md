# Best Practices for Writing Cloud Code

_Captured: 2017-08-24 at 23:54 from [dzone.com](https://dzone.com/articles/best-practices-for-writing-cloud-code?edition=317404&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-20)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

Many of our customers at ShepHertz have written custom cloud code and encountered performance issues once they hit the production. A particularly common problem was that their cloud code was throwing error code 1904 (Execution Time Threshold Exception). Any custom code must be executed within 10 seconds -- otherwise, it will be killed and the client will receive the 1904 error code. But don't worry! Here are a few guidelines that will help you in optimizing your custom cloud code so that you can avoid these time-out exceptions.

## **Avoid Too Many Server API Calls**

We have seen the instances where too many cloud API calls were made within a single flow of custom code. More API calls will result in more latency and will cascade to the Execution Time Threshold Exception. Ideally, there should no be more than 3-4 API calls per custom cloud code.

## **Avoid Too Many Conditions in Single Query for Storage**

There are some instances where storage queries were written with 10-15 conditional operators in a single storage query. Putting too many conditions in a single query will result in latency and, hence, might result in the Execution Time Threshold Exception. For example, say you're finding docs where name=nick and age >30 and country=US and gender=Male and so on. Ideally, there should not be more than 3-4 conditional operators in a single query.

## **Using Static Variable Does Not Make Any Difference**

Your deployed custom code runs in different clusters. Using static variables will not improve performance. Also, you should not use this variable as a global variable to calculate something because it will result in inconsistent results.

## **Keep an Eye on Metering Data**

You should keep an eye on metering data and look for the execution time for your custom code. If it is continuously going above 5 seconds, it means you need to re-examine and optimize it for better performance.

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

Topics:

cloud ,cloud code ,best practices ,api calls ,static variable ,data meter
