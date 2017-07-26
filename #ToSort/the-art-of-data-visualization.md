# The Art of Data Visualization

_Captured: 2017-06-15 at 01:14 from [dzone.com](https://dzone.com/articles/the-art-of-data-visualization?edition=305092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-14)_

Effortlessly power IoT, predictive analytics, and machine learning applications with an [elastic, resilient data infrastructure](https://dzone.com/go?i=207144&u=https%3A%2F%2Fmesosphere.com%2Fsolutions%2Fdata%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_term%3Dpre-article%26utm_content%3D101). Learn how with [Mesosphere DC/OS](https://dzone.com/go?i=207144&u=https%3A%2F%2Fmesosphere.com%2Fproduct%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_term%3Dpre-article%26utm_content%3D101).

In my last blog, we looked at [how data is aggregated based on the trend of data](http://blog.catchpoint.com/2017/05/18/using-mean-performance-analysis/). In this article, we discuss how this data is represented to users in a more meaningful way.

The raw data for thousands of websites across different geographies that are measuring network components, page performance, availability, and page content metrics is saved in huge databases. When this data is presented to humans without organizing and categorizing properly, it's difficult to read, analyze, and identify conclusions.

Presenting these data sets by organizing and categorizing in a graphical format makes it easier to achieve your goals. Here, we will look at different chart types that are used more frequently in performance analytics and that are used in various scenarios based on the data type.

Most commonly used chart types:

  1. Bar chart.
  2. Line chart.
  3. Scatterplot chart.
  4. Histogram.
  5. Cumulative distribution chart.
  6. Geo chart.
  7. Bubble chart.

To determine the chart types that represent a set of data accurately, let's look at some real-world scenarios in performance analytics.

## **Use Case 1**

Often when analyzing performance data, we come across situations where we need to rank the data based on certain qualitative data. For example, consider the qualitative data for performance of a website across different cities in the US; let's try to determine which chart would help interpret the data in the best way.

Bar charts display the data in the form of vertical bars. This works in scenarios where we need to compare different qualitative data that can be categorized. So, bar graphs are appropriate when we want to represent ranking data in performance analysis.

Catchpoint's digital experience intelligence platform provides the option to generate bar graphs at distinct levels of breakdown which is an effective way to represent qualitative data in a ranking order.

![](http://blog.catchpoint.com/wp-content/uploads/2017/06/chart1.png)

The above bar chart shows web page load time ranking across different cities in the US; it is easy to figure out which city performed well over others looking at this chart.

## **Use Case 2**

Consider another scenario where performance data needs to be studied over a period to see if there is any change in performance.

A line graph can be used to represent the continued distribution of quantitative performance data of a website over a specific period. This can determine the range of time when the performance was affected. Catchpoint can provide flexibility to plot line graph for 10 different metrics at once to provide an in-depth detail to find the root cause of the issue.

![](http://blog.catchpoint.com/wp-content/uploads/2017/06/chart2.png)

From the above line graph chart, we see that there was a change in the performance in the month of October as there was an increase in the total number of contents on the page.

So, a line graph can help understand performance variations and to analyze the root cause behind the change in performance over a period of time.

## **Use Case 3**

Error filtering is an important part of data analytics. It helps identify different errors, and the time the errors occurred to evaluate the availability of the website. This also helps in evaluating website availability; hence, this chart type is frequently used in performance analysis to monitor the availability of a website.

Some solutions offer an effortless way to filter different error types in a specific time frame. A scatterplot chart is a straightforward way to visualize all these errors, it plots every test run that had a failure.

![](http://blog.catchpoint.com/wp-content/uploads/2017/06/chart3.png)

The above graph shows all the errors which occurred in a specified time interval for a web test, each data point can be analyzed further by clicking on a data point and viewing the waterfall data.

A scatterplot can also be used to visualize different patterns of data for an in-depth root cause analysis. For example, consider a scenario where the page performance is impacted by the high response time of a file. Analyzing the data points reveals that the file was served from different servers and some of these servers were sending the file uncompressed and these uncompressed files added latency to the page load.

The scatterplot graph below shows different bands of data for file 1 and file 2, each of which has an uncompressed and compressed version served from different servers. The response time of the compressed file was much better than the larger uncompressed file as it takes longer to deliver higher bytes of data to the client from the server.

![](http://blog.catchpoint.com/wp-content/uploads/2017/06/chart4.png)

## **Use Case 4**

In performance analytics, it is important to know the number of data points present in the threshold range of a performance metric. This would be useful to evaluate how many users were affected by low performance and how many experienced reliable performance.

Categorizing data into range buckets will help you understand how many data points were within the desired threshold range for that website. It can also help with further analysis for the data sets that had low performance.

A histogram chart can be used to represent data distribution in range buckets. Each bucket depicts the performance metric range and the number of data sets which fall in that range.

![](http://blog.catchpoint.com/wp-content/uploads/2017/06/chart5.png)

The histogram graph above shows the number of data runs on the Y axis and the range of web page load time on the X axis. The second bar shows that there were 232 runs which had web page response time in the range of 5.3-6 seconds.

The histogram gives a range bucket for looking at the number of affected users while a cumulative distribution graph gives the percent of users who crossed the threshold value for that performance metric.

Cumulative distribution graph is a commonly used chart type to express the performance metrics in percentile; it plots the percent of users who had performance metric greater or lesser than the threshold for the website.

The graph below shows the CDF graph for web page response time

![](http://blog.catchpoint.com/wp-content/uploads/2017/06/chart6.png)

From the CDF graph above, we see that at the 90th percentile, the web page response time of a website is 10.3 seconds. This means that 10% of the users in the time frame that the data was collected in had an overall web page load time of more than 10.3 seconds.

## **Use Case 5**

When a website is hosted at multiple locations, it becomes necessary to evaluate its performance from different geographic points. Catchpoint offers geo charts that display performance based on the data point's magnitude from green for good to red for bad performance.

![](http://blog.catchpoint.com/wp-content/uploads/2017/06/chart7.png)

The geo chart above shows how the performance of a single website varies across geographies. From the graph, we see users in USA and Europe experienced the best web page load time, whereas the user in China experienced higher web page load time.

## **Use Case 6**

The chart types we discussed so far focus on a single metric which can be selected for evaluating the performance. What if we want to evaluate the performance of more than 1 metric or for a set of different websites?

In such scenarios, Bubble charts are a good option to evaluate multiple performance metrics for different websites in a single view.

![](http://blog.catchpoint.com/wp-content/uploads/2017/06/chart8.png)

The above bubble chart gives the performance (Document Complete, Webpage Response) of 3 different websites under a single view.

## **Conclusion**

From the above-mentioned scenarios, visualization is a powerful way to express data in a more meaningful manner. It helps in finding the root cause of an issue and drawing conclusions to narrow the areas that require optimization.

The different charts types available in Catchpoint helps you slice and dice the data in diverse ways to analyze the data. In addition to analyzing the data, it is also important to monitor the trend in performance across different web pages or competitor's website to know how the system behaves over time.

![](http://blog.catchpoint.com/wp-content/uploads/2017/06/chart9.png)

Learn to design and build better data-rich applications with this [free eBook from O'Reilly](https://dzone.com/go?i=207145&u=https%3A%2F%2Fmesosphere.com%2Fresources%2Fdesigning-data-intensive-applications%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_campaign%3Doreilly-data-apps-ebook%26utm_term%3Dpost-article%26utm_content%3D202). Brought to you by [Mesosphere DC/OS](https://dzone.com/go?i=207145&u=https%3A%2F%2Fmesosphere.com%2Fproduct%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_campaign%3Doreilly-data-apps-ebook%26utm_term%3Dpost-article%26utm_content%3D202).
