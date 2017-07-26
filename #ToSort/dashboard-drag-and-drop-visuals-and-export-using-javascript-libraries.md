# Dashboard: Drag and Drop Visuals and Export Using JavaScript Libraries

_Captured: 2017-04-25 at 23:40 from [dzone.com](https://dzone.com/articles/dashboard-drag-and-drop-visuals-and-export-using-j?edition=292916&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-25)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190137&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190137&u=https%3A%2F%2Fwww.wakanda.io%2F).

Recently, I published an [article](https://dzone.com/articles/7-javascript-libraries-for-dashboards) on various JavaScript libraries for Dashboards. In this article, I am going to demonstrate how we can create a dashboard with drag-and-drop visuals and export it using JavaScript.

I am going to use the [Gridster](https://github.com/dsmorse/gridster.js) library to create the dashboard. I have used this library in my projects and found it easy to use and flexible.

There are many ways of presenting data. If your software product is data-intensive, then you will need to find a way to make that data easy to visualize. That's where the visualizations come in - such as presenting data in the form of charts, graphs, and so on. I will use [Chart.js](https://github.com/chartjs/Chart.js) to create charts, which is a simple and flexible JavaScript charting library.

To export the dashboard, I will use [jsPDF](https://github.com/MrRio/jsPDF) which is a client-side JavaScript library. It lets you export the static image of the web page into a PDF file. Additionally, I will need to use [html2canvas](https://github.com/niklasvh/html2canvas/releases) to get charts to be printed in PDF. But if you want to print simple images or data, [jsPDF](https://github.com/MrRio/jsPDF) alone is sufficient.

Without further ado, let's get into coding!

## Creating Dashboard

Add the Gridster dependency by downloading it from [GitHub](https://github.com/dsmorse/gridster.js) or just include the source from [cdnjs](https://cdnjs.com/libraries/jquery.gridster) links. Since Gridster is a jQuery plugin, you will have to include a [jQuery](https://code.jquery.com/) library as well!

First, let's add the following code snippet within `<body>`.
    
    
    < button id="export">Export< /button>
    
    
       <li data-row="1" data-col="1" data-sizex="5" data-sizey="6">
    
    
       <li data-row="1" data-col="5" data-sizex="5" data-sizey="6">
    
    
       <li data-row="7" data-col="1" data-sizex="5" data-sizey="5">
    
    
          < canvas id="chart3" >< /canvas>
    
    
       <li data-row="7" data-col="6" data-sizex="5" data-sizey="5">

I have defined canvas elements and `<button>`, which we will look at them later in this article. Gridster is instantiated as follows:

Here, the `<li>` elements will be converted into widgets. So far, we will only get empty widgets. Let's put some data into our widgets.

## Creating Charts

We are going to use previously defined canvas elements to create charts. Let's look at the implementation for the first widget.

First, add dependencies by downloading the latest version of [Chart.js on GitHub](https://github.com/chartjs/Chart.js/releases/latest) or just use these [Chart.js CDN](https://cdnjs.com/libraries/Chart.js) links. Here is our JavaScript code:
    
    
    var canvas = document.getElementById(“chart1”).getContext(“2 d”);
    
    
            labels: ["A", "B", "C", "O", "G", "W", "S"],

Here, the option `type` is important as it indicates the type of chart that we want to create. Our widget would be as follows.

![Screen Shot 2017-04-02 at 19.18.36](https://techshard.files.wordpress.com/2017/04/screen-shot-2017-04-02-at-19-18-36.png?w=700&h=492)

For the implementation of remaining widgets, refer the [source code](https://github.com/swathisprasad/dashboard) on GitHub.

## Export

Let's look at the export feature. Include references to [jsPdf](https://cdnjs.com/libraries/jspdf) and [html2canvas](https://cdnjs.com/libraries/html2canvas) in HTML. We will attach a click event to `<button>` and instantiate jsPdf. Here goes our code:

Here, we have specified the element `<ul>` within `addHTML()`, that means we want to print only contents of `<ul>` in the PDF file.

The screenshot of the dashboard is as follows:

![Screen Shot 2017-04-02 at 20.20.50](https://techshard.files.wordpress.com/2017/04/screen-shot-2017-04-02-at-20-20-50.png?w=700)

> _And the screenshot of PDF is as follows:_

![Screen Shot 2017-04-02 at 20.21.09](https://techshard.files.wordpress.com/2017/04/screen-shot-2017-04-02-at-20-21-09.png?w=700)

> _Check the live demo here and complete source code for the demo here._

## Summary

This was a detailed overview for implementing dashboard with a combination of few popular JavaScript libraries. It may not be necessary to use all of them together in your projects. Each library described here can be used independently depending on project needs.

Do post if you have any questions or comments in the comments section, I'd love to hear them.

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190138&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190138&u=https%3A%2F%2Fwww.wakanda.io%2F).
