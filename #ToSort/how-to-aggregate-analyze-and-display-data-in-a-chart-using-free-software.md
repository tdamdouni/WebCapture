# How to Aggregate, Analyze, and Display Data in a Chart Using Free Software

_Captured: 2018-07-13 at 19:21 from [dzone.com](https://dzone.com/articles/showcase-learn-how-to-aggregate-your-data-analyze?edition=386201&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-13)_

Having lots of great tools for data analysis, the task of finding the perfect match is quite complicated. To get some insight, it is often useful to have a look at the data from different vantage points. Today, I'd like to share a really simple tutorial explaining how to summarize your data and visualize in a grid and a chart.

I was choosing between data analysis tools available for free and made the following choices:

  * [WebDataRocks](https://www.webdatarocks.com/) for data aggregation. This tool is a web pivot table capable of summarizing the data and displaying it in a table.
  * [Google Charts](https://developers.google.com/chart/) for data visualization. This tool is a charting library capable of drawing interactive charts for browsers and mobile devices.

What I want to achieve is a dashboard where data is shown in a table and a chart at the same time. Moreover, when I change the data inside the table, I'd like the chart to be updated automatically.

Now I'm going to describe the whole process step-by-step. At the end of this tutorial I will share a link to a CodePen sample with all the configurations, so if you feel like you're not understanding one of the steps, just scroll down to the end and follow the CodePen link. So, here we go:

### Step 1: Get Your Data on the Page

My data is a JSON array of objects. I'll start by adding it directly to the page:

### Step 2: Aggregate the Data and Display it Inside a Table

I've read [WebDataRocks Quick Start](https://www.webdatarocks.com/doc/how-to-start-online-reporting/) and created the table based on my data:

Here you can select which data goes to rows, columns and measures, so I've put Category to rows, Revenue, and Quantity to measures. Inside the table, Revenue and Quantity are displayed as already summarized.

### Step 3: Connect the Charting Library

After checking out [Google Charts Quick Start](https://developers.google.com/chart/interactive/docs/quick_start), I've added the loader for the Google Visualization API:

### Step 4: Show the Data From the Table on Charts

I've used the `pivot.googlecharts.getData` method to get the data from the pivot table and created an Area chart:

Hurray! My JSON data is aggregated, shown inside the pivot table and displayed as charts within 4 simple steps. Here is my CodePen sample containing all the code: <https://codepen.io/TetianaHryshko/pen/YjKLZN>

When I change the data in the pivot table, e.g. apply filtering, the Area chart changes as well. This gives an opportunity to analyze the data inside the table and see the graphical changes at the same time. I hope you guys will find this tutorial useful for your cases!
