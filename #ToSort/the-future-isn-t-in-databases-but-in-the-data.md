# The Future Isn't in Databases, but in the Data

_Captured: 2018-06-08 at 17:29 from [dzone.com](https://dzone.com/articles/the-future-isnt-in-databases-but-in-the-data-thoma?edition=381200&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-07)_

**New whitepaper: Database DevOps - 6 Tips for Achieving Continuous Delivery.** Discover 6 tips for continuous delivery with Database DevOps in this new whitepaper from Redgate. In 9 pages, it covers version control for databases and configurations, branching and testing, automation, using NuGet packages, and advice for how to start a pioneering Database DevOps project. Also includes further research on the industry-wide state of Database DevOps, how application and database development compare, plus practical steps for bringing DevOps to your database. [Read it now free.](https://dzone.com/go?i=290463&u=https%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2Fentrypage%2F6-tips-for-achieving-continuous-delivery%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddb_devop_6tips%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-26336)

![](https://thomaslarock.com/wp-content/uploads/2018/06/data-science.jpg?x15556)

In the past year, you may have heard me mention my certificates from the Microsoft Professional Program. [One certificate was in Data Science](https://thomaslarock.com/2017/07/why-im-learning-data-science/), the [other in Big Data](https://thomaslarock.com/2018/04/big-data-certification/). I'm currently working on a third certificate, this one in Artificial Intelligence.

You might be wondering why a database guy would be spending so much time on data science, analytics, and AI. Well, I'll tell you.

The future isn't in databases, but in the data.

Let me explain why.

## Databases Are Cheap and Plentiful

Take a look at the latest [DB-Engines rankings](https://db-engines.com/en/ranking). You will find there are 343 distinct database systems listed, [138 of those are relational databases](https://db-engines.com/en/ranking_categories), and I'm not sure it is a complete list, either, but it should help make my point: you have no idea which one of 343 database systems is the right one. It could be none of them. It could be all of them.

Sure, you can narrow the list of options by looking at categories. You may know you want a relational, a key-value pair, or even a graph database. Each category will have multiple options, and it will be up to you to decide which one is the right one.

Decisions are made to go with whatever is easiest. And "easiest" doesn't always mean "best." It just means you've made a decision allowing the project to move forward.

Here's the fact I want you to understand: **Data doesn't care where or how it is stored**. Neither do the people curating the data. Nobody ever stops and says, "Wait, I can't use that, it's stored in JSON." If they want (or need) the data, they will take it, no matter what format it is stored in to start.

And the people curating the data don't care about endless debates on MAXDOP and NUMA and page splits. They just want their processing to work.

And then there is this #hardtruth -- It's often easier to throw hardware at a problem than to talk to the DBA.

## Technology Trends Over the Past Ten Years

Here's a handful of technology trends over the past ten years. These trends are the main technology drivers for the rise of data analytics during this timeframe.

### **Business Intelligence Software**

The ability to analyze and report on data has become easier with each passing year. The Undisputed King of all business analytics, Excel, is still going strong. Tableau shows no signs of slowing down. PowerBI has burst onto the scene in just the past few years. Data analytics is embedded into just about everything. You can even run R and Python through SQL Server.

### **Real-Time Analytics**

Software such as Hadoop, Spark, and Kafka allow for real-time analytic processing. This has allowed companies to gather quality insights into data at a faster rate than ever before. What used to take weeks or months can now be done in minutes.

### **Data-Driven Decisions **

Companies can use real-time analytics and enhanced BI reporting to build a data-driven culture. We can move away from, "Hey, I think I'm right, and I found data to prove me right" to a world of, "Hey, the data says we should make a change, so let's make the change and not worry about who was right or wrong." In other words, we can remove the human factor from decision making, and let the data help guide our decisions instead.

### **Cloud Computing**

It's easy to leverage cloud providers such as Microsoft Azure and Amazon Web Services to allocate hardware resources for our data analytic needs. Data warehousing can be achieved on a global scale with low latency and massive computing power. What once cost millions of dollars to implement can be done for a few hundred dollars and some PowerShell scripts.

## Technology Trends Over the Next Ten Years

Now, let's look at a handful of current trends. These trends will affect the data industry for the next ten years.

### **Predictive Analytics**

Artificial intelligence (AI), machine learning (ML), and deep learning (DL) are just starting to become mainstream. AWS is releasing [DeepLens](https://amzn.to/2Je1HbJ) this year. Azure Machine Learning makes it easy to deploy predictive web services. [Azure Machine Learning Workbench](https://docs.microsoft.com/en-us/azure/machine-learning/service/quickstart-installation) lets you build your own facial recognition program in just a few clicks. It's never been easier to develop and deploy predictive analytic solutions.

### **DBA as a Service**

Every company making database software (Microsoft, AWS, Google, Oracle, etc.) is actively building automation for common DBA tasks. Performance tuning and monitoring, disaster recovery, high availability, low latency, auto-scaling based upon historical workloads, the lists go on. The current DBA role, where lonely people work in a basement rebuilding indexes, is ending one page at a time.

### **Serverless Functions**

Serverless functions are also hip these days. Services such as [IFTTT](https://ifttt.com/) make it easy for a user to configure an automated response to whatever trigger they define. [Azure Functions](https://azure.microsoft.com/en-us/services/functions/) and [AWS Lambda](https://aws.amazon.com/lambda/) are where the hipster programmers hang out, building automated processes to help administrators do more with less.

### **More Chatbots**

We are starting to see a rise in the number of chatbots available. It won't be long before you are having a conversation with a chatbot playing the role of a DBA. The only way you'll know it is a chatbot and not a DBA is because it will be a pleasant conversation for a change. Chatbots are going to put a conversation on top of the automation of the systems underneath. As new people enter the workforce, interaction with chatbots will be seen as the norm.

## Summary

There is a dearth of people able to analyze data today.

Data analytics is the biggest growth opportunity I see for the next ten years. The industry needs people to help collect, curate, and analyze data.

We also need people to build data visualizations. Something more than an unreadable pie chart, but I will save that rant for a different post.

We are always going to need an administrator to help keep the lights on, but as time goes on, we will need fewer administrators. This is why I'm advocating a shift for data professionals to start learning more about data analytics.

Well, I'm not just advocating it, I'm doing it.

**New whitepaper: Database DevOps - 6 Tips for Achieving Continuous Delivery.** Discover 6 tips for continuous delivery with Database DevOps in this new whitepaper from Redgate. In 9 pages, it covers version control for databases and configurations, branching and testing, automation, using NuGet packages, and advice for how to start a pioneering Database DevOps project. Also includes further research on the industry-wide state of Database DevOps, how application and database development compare, plus practical steps for bringing DevOps to your database. [Read it now free.](https://dzone.com/go?i=290464&u=https%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2Fentrypage%2F6-tips-for-achieving-continuous-delivery%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddb_devop_6tips%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-26336)
