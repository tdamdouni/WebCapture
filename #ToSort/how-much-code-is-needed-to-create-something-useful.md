# How Much Code Is Needed to Create Something Useful?

_Captured: 2018-08-18 at 13:08 from [dzone.com](https://dzone.com/articles/how-much-code-is-needed-to-create-something-useful?edition=387216&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-17)_

Your business likely requires customized views of the data that is core to the creation of your product. Decades ago, accomplishing this involved development of large data analysis software libraries that were customized to a company's particular needs, along with user interfaces that enabled employees to view the data, so they could respond to anomalies.

Much has changed in recent decades. Data analysis code that had to be custom-developed decades ago is now available in software libraries such as Python's [NumPy](http://www.numpy.org/) and [SciPy](https://www.scipy.org/). Similarly, modern data display libraries available, for example, [Matplotlib](https://matplotlib.org/). This code is well tested and verified by a large user community. By utilizing these libraries, developers can simply call verified functions, rather than developing new custom code.

Meanwhile, [Application Programming Interfaces](https://en.wikipedia.org/wiki/Application_programming_interface) (APIs) have immensely simplified the programming effort required to access large amounts of important data. In particular, [JavaScript Object Notation](https://json.org/) (JSON) facilitates downloading data from APIs in a format that is easily ingested by most modern programming languages that are suited to data analysis, for example, Java and Python.

In this post, I illustrate how a mere ~50 lines of code (including documentation comments and blank lines added for readability) can gather the past week's performance of an API from a given geographical location and create a website that illustrates when a company's product was perceived by their customers as being slow, or down.

## How to Use cron and curl to Regularly Download API Performance Data

API performance is critical for modern applications. People use their phones and tablets to immediately access information that is relevant to what they're doing or thinking about _right now._ If your company's objective is to provide this information, then you need to know how your product appears to your customers. If your product is down, but your competitor's product is up, the result is simple: you'll lose customers.

API monitoring provides your company with a means to observe how your product is being perceived by your customers right now (is it up, or not?) and lets you analyze the performance of your product over time.

The [API Science API](https://www.apiscience.com/docs/api) provides the capability for your team to monitor the performance of all APIs that are relevant to your product, at a time cadence as low as one second, if that is what your customers expect and need.

The [API Science Performance Report API](https://www.apiscience.com/docs/api#performance-report) provides metrics on API performance over a selectable period of time. You can choose to bin monitor results on an hourly basis or on a daily basis. In the example that is presented in this blog series, we assume that you are interested in looking at performance data on an hourly basis over the past week.

## **Get the Data**

The first step, if your goal is to create an API performance report that is customized for your own product, is to get the data for the APIs that are critical for your product. API Science aggregates all the data from your API monitors, and this data is available in multiple formats. In this example, we download the data in [JSON](https://json.org/) format using a [Linux cron](https://en.wikipedia.org/wiki/Cron) that executes a [curl](https://curl.haxx.se/) command to download API performance data to a local server.

Ultimately, we'll use this data to create an example custom website that provides your team with the essential information that would allow them to monitor critical API performance and recognize when immediate action is required.

But first, we need to get the data (which is where _curl_ comes in) on a regular schedule (this is where _cron_ comes in, assuming you're working on a Unix/Linux-like operating system; note that other operating systems have similar chronological job schedulers).

### **The _curl_ Code**

The following _curl_ command gathers the API performance data for the past week:

> curl 'https://api.apiscience.com/v1/monitors/1572020/performance.json?preset=lastWeek&resolution=hour' -H 'Authorization: Bearer xyzq...'

Here, the numeric 1572020 is the identity of the particular monitor for which you're seeking performance data. `preset=lastWeek` means we're accessing the monitor data for the past week. `resolution=hour` states that we want the monitor data binned by hour - for example, if the monitor is executed every minute, the 60 monitor results for each minute in that hour will be averaged to produce the cumulative data statistic. The `Bearer` variable is your authorization code for accessing the API Science API.

### **The _cron_ Code**

The _cron_ code simply specifies the schedule for when the _curl_ code is to be run. Specifying this varies by operating system. In many varieties of Linux, one can edit the _/etc/crontab_ file and add a new command along with its scheduled timing.

For most modern operating systems, defining execution of a timed job is accomplished by adding a line to a text file that defines when the job should be executed and the program that is to be run at those times. It is up to the developer to ensure that the executable can find all necessary inputs and write its results to an appropriate output location.

## How to Use Python to Extract JSON API Performance Data

Once you have the raw data, you can use your company's preferred programming languages and the custom libraries your company has developed to deliver API performance data to your team in a familiar format.

The entire resultant JSON from the _curl_ is too long to present here, but it can be described. The JSON begins with a _meta_ element that defines the success or failure of the request, the number of results, and the time span. Additionally, it includes performance data for all API checks for the past week, binned by hour (that is, the performance in an individual hour is averaged). Here is an example of the returned JSON heading:
    
    
    "meta":{"status":"success","numberOfResults":168,"resolution":"hour","startPeriod":"2018-05-27T19:49:04.602Z","endPeriod":"2018-05-20T21:49:04.602Z"}

The JSON in this file continues in its `data` body with 168 results (because we requested one week of data binned at an hourly resolution) like this:
    
    
    {"averageResolve":51.17,"averageConnect":0.93,"averageProcessing":8.52,"averageTransfer":0.13,"averageTotal":60.74,"startPeriod":"2018-05-27T19:49:04.602Z","endPeriod":"2018-05-27T20:49:04.602Z"}

Each entry contains the averaged data for the time period specified by the `resolution` defined in the _curl_ request.

### **Python and JSON**

Python is one of the major scientific data analysis programming languages today. There are other languages well suited for scientific data analysis, including Java and C. In this example, we use Python as the language that reads the JSON and produces the view of the data your team needs to see. The same type of coding can be implemented in other languages, if your corporate development platform doesn't include Python.

The following Python code reads this JSON into a Python dictionary, and prints the number of results from the `meta` heading data set:

The _perf.json_ file that was downloaded using the curl script is read and inserted into the Python `perf` dictionary. The data in the `perf` Python dictionary is then available for display and manipulation by any Python code. For example, Python can create the variable `n_results` based on the JSON, and print the number of results stated in the JSON `meta` heading:

The `data` body is loaded into Python as multiple arrays within the Python dictionary. Thus, information like "averageConnect" can be accessed from within the Python dictionary and used to provide your team with reports that can be used to optimize your product's performance.

### How to Use MatPlotLib to Display API Performance Data

The JSON data contains 168 results (one week of data for our example monitor) that look like this:
    
    
    {"averageResolve":51.17,"averageConnect":0.93,"averageProcessing":8.52,"averageTransfer":0.13,"averageTotal":60.74,"startPeriod":"2018-05-27T19:49:04.602Z","endPeriod":"2018-05-27T20:49:04.602Z"}

The Python dictionary allows us to access this data using the JSON titles for each data item. In other words, the Python dictionary contains individual arrays titled _averageResolve_, _averageConnect_, etc.

In this MatPlotLib example, we plot the _averageTotal_ data, that is the total number of milliseconds between the initiation of the request to the API and the completed download of the response.

Here's the complete script for reading the API performance data JSON file and creating a plot of the _averageTotal_ data:

_perf_ is the Python dictionary into which the JSON is read. _n_results_ is the number of results stated in the JSON download from the API Science API (a week of data averaged in one-hour time bins).

Following the printing of _n_results_, we initialize _hourly_perf_total,_ a floating point array sized at the number of results. Then, in the `for i in range(n_results)` loop, we copy the 168 _averageTotal_ values into the _hourly_perf_total_ variable (programmers well-versed in Python will note that this is an unnecessary step, but I did it this way to provide clarity to non-Python programmers who might read this post).

Now we have an _hourly_perf_total_ array that contains 168 values representing the total performance data for the API binned hourly over the past week.

The remaining lines use MatPlotLib to produce a plot of the past week's total performance, for example:

![](https://www.apiscience.com/blog/wp-content/uploads/2018/06/MatPlotLib_Monitor_perf1.png)

The average total milliseconds are plotted in a logarithmic scale to point out to the team instances where the API's performance was particularly poor. For example, the two peaks that touch and exceed 1000 milliseconds (one second) could represent times when your product will have been seen as down by many customers, especially if access to this API is but one of many APIs your product depends on.

## How to Create an Automated Custom Web Site that Displays API Performance Data

Now we need to bring all of this together in order to create a constantly-updated web page that your entire team, including management, can observe at any moment to review the recent performance of an API.

### **Creating a Constantly-Updated Web Page**

The MatPlotLib image is output as a PNG file. To make a constantly-updated web page, we need to write HTML that embeds the PNG image and updates automatically as new API performance becomes available and new PNG images are generated. Here is an example of HTML that accomplishes this:

![](https://www.apiscience.com/blog/wp-content/uploads/2018/07/custom_html.png)

The _body_ section displays the latest image that was produced by MatPlotLib. The _head_ section defines the title that is displayed on the web browser window.

But the _head_ section also includes the `meta http-equiv` line. This tells the user's browser to refresh the page every 60 seconds. That is, the user's local web browser will automatically reload the page content every minute. So, whenever a new API performance PNG image becomes available as a result of the batch processing that is producing the images, the web page will be automatically updated with no user interaction required.

## Conclusion

This technique provides the capability for displaying critical API status views that can be observed at any time by any member of your company in an automated manner. The same technique could be replicated for any number of your critical APIs. The results could easily be agglomerated into a single summary web page suitable for managers.

Meanwhile, the status page could be created such that the developer team could easily click to review the lower-level details of recent anomalous performance in a particular API.

Total lines of code:

  * **_cron:_** 1
  * _**curl:**_ 1
  * _**csh:**_ 5 (including 2 lines that launch the _**curl**_ and **python** commands)
  * _**python:**_ 37
  * _**HTML:**_ 10

So, utilizing modern programming libraries and APIs, around 50 lines of code provides your team with constantly updated, concise, important information about how your customers have recently been perceiving your product.
