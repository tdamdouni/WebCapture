# We Need to Talk About Dashboards

_Captured: 2018-03-29 at 14:35 from [dzone.com](https://dzone.com/articles/we-need-to-talk-about-dashboards?edition=370196&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=big%20data%202018-03-29)_

Access NoSQL and Big Data through SQL using standard drivers (ODBC, JDBC, ADO.NET). [Free Download ](https://dzone.com/go?i=250345&u=https%3A%2F%2Fwww.cdata.com%2Ftech%2Fbigdata%2F%3Futm_source%3Ddzone%26utm_medium%3Dbump3%2520)

![](https://thomaslarock.com/wp-content/uploads/2018/03/piechart-600x477.png?x74410)

> _Hey everyone, gather 'round. We need to talk about dashboards._

For C-level executives, dashboard reports are essential. Executives don't have time to review details for every decision they make -- they just want to consume a report that has red, yellow, and green to help them make decisions for the day. But the need for such dashboards is also true for the cubicle-dwelling system administrators. They also need dashboards to help them understand where to focus their efforts daily in order to keep operations running.

I'm here today to tell you that your dashboards are a failure.

## Why Dashboards Fail

More than 90% of the data in the world has been created in the past two years.

Don't take my word for it, though. I'm just citing a statement made [in this article](https://www.sciencedaily.com/releases/2013/05/130522085217.htm). Published more than four years ago, that article is the cited source in presentations on how data continues to grow at an exponential rate.

I believe we continue to create and curate data at an accelerated pace with each passing year. Today we have access to more data than ever before. Everyone I meet will say they manage more data today than a year ago.

The data explosion has given rise to a never-ending marketing lexicon. The first one I remember being used widely was a [data warehouse](http://searchsqlserver.techtarget.com/definition/data-warehouse). That was soon followed by a [data mart](http://searchsqlserver.techtarget.com/definition/data-mart). Today, we also have a [data factory](https://azure.microsoft.com/en-us/services/data-factory/) and a [data lake](http://searchaws.techtarget.com/definition/data-lake), which is a nice feature to have next to our [data estate](https://blogs.technet.microsoft.com/dataplatforminsider/2017/09/25/microsoft-for-the-modern-data-estate/), built with [data bricks](https://azure.microsoft.com/en-us/services/databricks/).

With so much data available, information is cheap. Today, it is easy to get data about anything. We are drowning in data, inundated with metrics with every step of our day.

The trouble with such easy access to data is this: When information is so cheap, attention becomes expensive.

## I'm Looking Through You

Here's an experiment for you to try. Watch this video and count the number of passes between the people in white shirts:

It's an old study, and you may have seen it before. If you haven't seen it before, let me know if you are surprised by the results.

This is part of the problem with dashboards: they are being read by humans. And humans, as it turns out, can have difficulty determining what is important. The experiment helps to show how there is an area of our visual cortex that determines what is important and filters out everything else. In other words, we gain a lot of data when we focus our attention, but we can miss a gorilla staring back at us.

Focusing is a great thing for us humans, and this experiment helps show why multi-tasking is something we shouldn't be doing. Dashboards are meant to provide that focus. We don't want to spend the time examining all the data streams.

## Spot the Difference

Here's another experiment for you. [Remember those "spot the difference" games? Here's why your brain is so bad at them](https://www.popsci.com/spot-difference-between-similar-pictures).

When we look at a dashboard, we don't take in everything that we see. Our brains don't bother logging details about something that is not important. Just like the gorilla. Of course, once we see it, we don't forget it.

Dashboards that contain an overload of information require more focus, which means less information is being consumed. This is not the desired outcome.

## Dashboards Are a Horrible Way to Communicate

The trouble with such dashboards is that they are a horrible way to communicate.

Dashboards need data in order to exist. Good dashboards are able to communicate the story the data is trying to tell. But the data contains the details necessary for that story, and those details are often left behind. Summaries, aggregations, and averages blur the details from our view. Offering users the ability to drill-through to get the details is a workaround, but the whole point of a dashboard is to avoid having to review the details. Remember, it is better for us humans to be able to focus.

A common example that I often use to explain when dashboards aren't useful involves disk space usage. Let's say that a disk is at 90% of capacity and the dashboard shows a big red circle for this metric. The trouble now is that you are missing important details. A 1TB disk at 90% is a different situation than a 10TB disk at 90% full. You also need to know how full the disk was yesterday, what the growth trend has been over time, and at what point the disk is completely full.

While those details might help you figure out what steps to take next, they do little for your end user. This dashboard reporting a disk at 90% has little meaning to the end user that only wants to be able to get their work done for the day.

## Summary

Dashboards are not new; they've been around for years. It's the ease in which they are created and consumed that has driven demand. You get a dashboard, and you get a dashboard, and everyone gets a dashboard. The phrase "pin it to your dashboard" has become common for users of tools such as [Power BI](https://powerbi.microsoft.com/en-us/).

But with so much data coming across our desk each day, we need the data to communicate with everyone in a way they can understand.

Saying your disk is 90% full is not nearly as effective as saying that you only have space for three more Netflix movie downloads. That's a story that anyone can understand. Even simple things like bar charts do a better job communicating the story that data is trying to tell. And I have yet to meet a manager that doesn't understand a bar chart.

Those of us that work in IT are always asking for more. We want more space, more memory, more CPU, more bandwidth.

It's time we also ask for more ways for our data to tell a story that everyone can understand.

And don't get me started on pie charts.

[The fastest databases need the fastest drivers](https://dzone.com/go?i=250346&u=https%3A%2F%2Fwww.cdata.com%2Fblog%2Fnews%2F20170601-bigquery-driver-comparison%3Futm_source%3Ddzone%26utm_medium%3Dbump4) \- learn how you can leverage CData Drivers for high performance NoSQL & Big Data Access.
