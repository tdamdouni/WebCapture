# Monitoring and Observability

_Captured: 2017-12-22 at 15:35 from [dzone.com](https://dzone.com/articles/monitoring-and-observability?edition=347102&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202017-12-22)_

Defining the term "monitoring" is a difficult task considering the performance space has evolved significantly over the years. Lately, there has been a shift in the monitoring world, sparking a healthy debate regarding the definition and purpose of monitoring, through which a new term has emerged: observability. Some of that debate can be found in blogs by [Charity Majors](https://honeycomb.io/blog/categories/observability/) and [Cindy Sridharan](https://medium.com/@copyconstruct).

Many organizations like AirBnB, Twitter, and Stripe are embracing the observability by creating observability teams or observability engineers.

So what is the difference between monitoring and observability, and how are they related? Is monitoring a subset of observability, is observability a subset of monitoring, or are they two terms that mean the same thing?

Performance monitoring is an umbrella term that can include system monitoring, component monitoring, web performance monitoring, application performance monitoring, digital experience monitoring, and end-user monitoring. The nature of your role will influence what monitoring means to you.

What is the purpose of monitoring?

The simple answer: To detect issues in a system and minimize the effect on end users. To put it differently, the point of monitoring is to discover:

  * Is something broken or is it going to break?
  * Why did it break?
  * When did it break?
  * How were users impacted by the break?
  * How long was it broken?

Monitoring is similar to taking your car to a mechanic for routine maintenance and when the check engine light comes on. You want to keep your car running as smoothly as possible and avoid breakdowns. On the web, you want to know whether users can access your application and services, and if they are performing within appropriate thresholds.

Alerts are configured to inform teams when something is not performing optimally or is broken. But before an alert can be configured, it is critical to create a baseline and understand the current state of the environment. To me, this is where observability first comes in. Without observing a system, it is not possible to know what is normal and what is not normal. Only by observing systems, services, and applications can we determine when something is wrong.

Organizations should constantly be observing the state of their services and applications to look for outliers and anomalies that wouldn't be detected from previously configured alerts. Aggregating data points to create means, medians, percentiles, or another consumable statistic is useful in some instances, but you also need access to the unaggregated data to find the anomalies and patterns that may reveal hidden insights.

Anomalies and outliers won't always trigger an alert and they shouldn't always trigger an alert. Anomalies can lead us to deeper insight into our systems, provide additional context, and help us identify key attributes. If the only thing we are focused on is whether an alert is generated we are missing large parts of the story.

What tools can be used to observe? Reading through job descriptions and blogs observability engineers rely on charts and visualizations, distributed tracing tools, logs, and monitoring services. Monitoring and observability are obviously closely related. Monitoring enables organizations to observe the performance, through this observation alerts and notifications can be configured, and deeper insights can be uncovered. These insights allow teams to make informed, data-driven decisions to maintain, improve, or replace services or systems.

Both monitoring and observability are essential components for high performing IT teams. Data needs to be collected from monitoring systems, analyzed, and acted upon.

For more information on what data to collect and report on, download our latest ebook, [Measure What Matters](http://pages.catchpoint.com/Measure-What-Matters-EBK.html).
