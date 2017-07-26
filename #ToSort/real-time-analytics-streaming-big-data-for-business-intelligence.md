# Real-Time Analytics: Streaming Big Data for Business Intelligence

_Captured: 2017-03-30 at 20:20 from [dzone.com](https://dzone.com/articles/real-time-analytics-streaming-big-data-for-busines?edition=287891&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-30)_

By 2020, as Bernard Marr [notes](http://www.forbes.com/sites/bernardmarr/2015/09/30/big-data-20-mind-boggling-facts-everyone-must-read/#79e5125d6c1d), an estimated 1.7 megabytes of new information will be created every second for every human being on the planet.

The prominence of real-time and streaming analytics is increasing every year. Two recent examples are the upgrade of [Thomson Reuters Velocity Analytics](http://www.financemagnates.com/institutional-forex/execution/thomson-reuters-rolls-mifid-ii-compliant-data-analytics-platform/) and the release of the [Oracle Data Integrator Cloud](http://www.zdnet.com/article/oracle-launches-data-integration-cloud-service/) in February. Overall, the rise of these types of business intelligence data and platforms will fuel the growth of the global analytics market, which [Gartner predicts](http://www.gartner.com/newsroom/id/3612617) will reach $18.3 billion this year.

To understand the greater significance, it's important to look at the history of data analysis and the use of historical data in descriptive, predictive, and prescriptive analytics.

## Historical Data Analysis

Historical data analysis, as the name implies, focuses on looking at the past. Analysts can export the relevant data from the prior day, month, quarter, or some other period of time and then perform at least one of three different types of analyses.

### Descriptive Analytics

Descriptive analytics condenses historical data into a story that has an overall theme that is relevant and useful. Examples include "sales rose 25% this quarter" and "failure prevention software resulted in 50% less server downtime in 2016." Descriptive analytics is the type of business intelligence activity with which most people are familiar.

In general, descriptive analytics is used to understand what happened in the past as well as to assist with the building of predictive or prescriptive analytical models -- which are two other types of analytics.

### Predictive Analytics

Predictive analytics is the process of using historical trends to make future predictions and present likely scenarios with the assistance of data mining, machine learning, and statistics.

One of the best examples is Amazon's well-known "recommendations" that present various products to customers based on what they have purchased in the past and therefore what may interest them in the future. Other examples include the now-defunct [Google Flu Trends](https://en.wikipedia.org/wiki/Google_Flu_Trends) and _The New York Times_ deciding [what website articles to promote to which visitors](http://searchbusinessanalytics.techtarget.com/feature/How-The-New-York-Times-uses-predictive-analytics-algorithms).

### Prescriptive Analytics

Descriptive analytics tell what happened. Predictive analytic tells what may happen if the historical trends continue. Prescriptive analytics tell what to do -- the process takes the data and then prescribes real-world decisions.

Examples include the InterContinental Hotel Group [using more than 600 variables](https://datafloq.com/read/big-data-enables-intercontinental-hotel-group-to-b/507) to determine what price and product combinations to give to customers. UPS [centralizes and analyzes information](https://datafloq.com/read/ups-spends-1-billion-big-data-annually/273) from hundreds of data sources to optimize the exact routes that trucks should take -- thereby saving millions of dollars on fuel every year. The Aurora Health Care Centre [combined and analyzed numerous data sets](https://datafloq.com/read/big-data-ensures-a-healthy-financial-position-at-a/480) to lower readmission by 10% and save $6 million every year.

So, as _The ERP Channel _[notes](http://erpchannel.com/website/item/162-real-time-analytics-or-history-based-which-is-most-suitable), the typical use cases for historical data analysis and descriptive, predictive, or prescriptive analytics include:

  * To make big-picture operational and business decisions outside the immediate flow of production.
  * To build or modify predictive or prescriptive models based on static, historical data.
  * To produce periodic reports, perform interactive data discovery, and do "what if" modeling.

## Real-Time Analytics

Historical data analysis is not that new (although prescriptive analytics is the newest type of batch analytics). Streaming analytics (also called real-time analytics) is comparatively new. Dataversity [summarizes](http://www.dataversity.net/streaming-analytics-101/):

> Stream processing analyzes and performs actions on real-time data through the use of continuous queries. Streaming analytics connects to external data sources, enabling applications to integrate certain data into the application flow, or to update an external database with processed information. 

In descriptive, predictive, and prescriptive analytics, one exports a set of historical data for batch analysis. In streaming analytics, one analyzes and visualizes data in real time. As ERP also notes, real-time analytics can be used for purposes such as these:

  * To make operational decisions and apply them to business processes, transactions, or other production activities in real time and on an ongoing basis.
  * To apply pre-existing predictive or prescriptive models.
  * To report current and historical data concurrently.
  * To receive alerts based on certain, predefined parameters.
  * To view real-time displays or dashboards in real time on constantly changing transactional data sets such as the hourly sales of a set of regional grocery stores.

### The Advantages of Streaming Analytics

Simply put, historical data tells you what happened _in the past_ while real-time analytics tells you what is happening _right now_. This essential difference [explains](http://www.dataversity.net/streaming-analytics-101/) the advantages of looking at real-time data:

  * **Data visualization**. A set of historical data can be placed into a single chart to communicate an overall point -- but streaming data can be visualized in a way that updates in real time to show what is occurring at every single moment
  * **Business insights**. Whenever an important business event occurs, it will first appear in the relevant dashboard. If the hourly sales at one of the aforementioned grocery stories plummets at an unusual time, then an alert can be triggered to tell management of a serious problem at that branch location
  * **Increased competitiveness**. Businesses can discern trends and set benchmarks much more quickly, allowing them to use this data to surpass competitors who are still using the slower process of batch analysis.

### The Disadvantages of Real-Time Analytics

Of course, nothing is perfect -- including streaming data analytics. There are reasons that certain companies may not want to use it:

  * **Hadoop is not compatible**. Hadoop is a widely used tool for historical big data analytics, but it is not designed to handle streaming, real-time data. Better options include Spark Streaming, Storm, Apache Flink, or Apache Samza. MongoDB is an open source database that can also be used in Big Data analysis, and we show elsewhere [how to monitor it with the ELK Stack](http://logz.io/blog/mongodb-performance-monitoring-elk-stack/).
  * **A new approach is required**. If your company is used to receiving in a single batch of insights one time every week, then a constant inflow of real-time Big Data can overwhelm business processes. If a single person or automated system would normally direct information from the insights to the relevant parties on a weekly basis, he will need to know what to do when he starts to receive insights every minute. Information workflows need to be reworked appropriately.
  * **Systems can fail**. Some think that Big Data analytics is easy to implement. But if a business is not used to handling data at rapid rates, it could lead to faulty analysis -- and even system failure. Despite all of the fanfare over streaming data, smaller businesses might not actually need it -- and they might not even be able to handle it.

## The Uses of Streaming Big Data

So-called "real-time business intelligence" (RTBI) is the process of using real-time analytics to deliver information on business operations as they occur. ("Real-time" refers to near-zero latency. In practical terms, the phrase means that information becomes available anywhere from milliseconds to five seconds after the fact.)

In a presentation, Impetus Technologies [explains](https://www.slideshare.net/ImpetusInfo/realtime-streaming-analytics-business-value-use-cases-and-architectural-considerations-impetus-webinar) real-time streaming analytics (RTSA) as follows:

> Data analyzed in motion as it arrives. Every incoming event is processable. Events can be stored later or in parallel. Immediate actions are possible after processing. 

RTSA, the company notes, has the following value to businesses (in descending order of importance):

  1. **Cutting preventable losses**. Streaming analytics can prevent or at least lessen the damage of incidents such as security breaches, stock exchange meltdowns, airplane crashes, manufacturing defects, customer churn, and social media meltdowns.
  2. **Analyzing routine business operations**. All of these can be monitored in real time: manufacturing closed-loop control systems; IT systems; field assets such as trucks, oil rigs, vending machines and radio towers; and financial transactions such as authentications and validations.
  3. **Finding missed opportunities**. The streaming and analyzing of Big Data can help companies to learn from customers as well as immediately recommend, upsell, and cross-sell to them based on what the information presents.
  4. **Create new opportunities**. The existence of streaming data technology has led to the invention of new business models, product innovations, and revenue streams. Tractors could be implemented with soil sensors. Clothing manufacturers could add wearable health technology to its products.

One example of business intelligence usage is Viacom [building a real-time analytics platform](http://www.forbes.com/sites/bernardmarr/2017/01/26/how-mtv-and-nickelodeon-use-real-time-big-data-analytics-to-improve-customer-experience/3/#3206a7e024d9) with Apache Spark and Databricks to monitor the quality of video feeds of the petabytes of data that the company transmits around the world. Viacom's goal is to improve the viewer experience and thereby increase customer retention.

The City of Chicago has a platform -- named the "WindyGrid" -- built with MongoDB that [centralizes seven million data points](https://www.em360tech.com/tech-news/real-world-use-cases-real-time-data-analytics/) from municipal departments. City staff can analyze the data to predict where resources such as emergency vehicles will be needed and then allocate them accordingly.

BuzzFeed [uses MongoDB](https://www.em360tech.com/tech-news/real-world-use-cases-real-time-data-analytics/) to see when articles are viewed and shared and how website visitors are interacting with the more than 400 million news items that are published every month. BuzzFeed can then analyze these metrics to see how to increase website engagement.

The website of Germany's largest retailer, Otto, generates some 10,000 events per second. Every single interaction with every single part of the website is [tracked and stored in a database](https://www.em360tech.com/tech-news/real-world-use-cases-real-time-data-analytics/). The company then uses real-time data analytics to give a unique and personalized experience to every single person who visits the website. (For more information on this, see our posts on [server log analysis](http://logz.io/blog/server-log-analysis/) as well as [Apache](http://logz.io/blog/apache-log-analyzer/), [IIS](http://logz.io/blog/iis-log-analyzer/), or [NGINX](http://logz.io/blog/nginx-log-analysis/) log analysis.)

Marketing departments [can use](https://blog.kissmetrics.com/real-time-analytics/) real-time analytics to monitor digital campaigns in real-time, conduct A/B and multivariate tests and see results quickly, and provide personalized website experiences. (For more on this topic, I recommend [reading this post](https://www.martechadvisor.com/articles/databases-big-data/a-marketers-guide-to-real-time-streaming-analytics/) on MarTech Advisor.)

## The Future of Real-Time Analytics

Both the number of machines in the world and the amount of information that they create are increasing every single month. As a result, it's becoming harder and harder to gain insights that are valuable from all of this data.

One solution that is [increasing in popularity](http://logz.io/blog/is-open-source-overtaking-splunk/) is using the open-source [ELK Stack](http://logz.io/learn/complete-guide-elk-stack/), which centralizes any desired log and machine data with Logstash, stores it in Elasticsearch, and then displays it with real-time [Kibana visualizations](http://logz.io/blog/kibana-visualizations/). ELK, for example, can be used [to analyze Salesforce](http://logz.io/blog/analyze-salesforce-elk-stack/).

Open source is the future, especially in a data-driven area such as business intelligence.
