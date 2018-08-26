# What is Real User Monitoring? Definition, Examples and Benefits

_Captured: 2018-03-02 at 14:09 from [dzone.com](https://dzone.com/articles/what-is-real-user-monitoring-definition-examples-a?edition=365213&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-03-02)_

It sucks to spend a long time building an app then get complaints about slow loading pages. You don't know where the performance problem is, let alone the environment it occurred in. So it gets ignored, and performance problems linger on in your app, causing havoc for end users and your bottom line.

[Real User Monitoring](https://raygun.com/platform/real-user-monitoring#hide-banner), (RUM), aims to prevent these problems and more. Using a small piece of code, RUM collects data on your end user via their browser then surfaces information like slow load times and performance bottlenecks in a central dashboard.

In this article, we'll take a look at how Real User Monitoring can help decipher performance problems with real-world examples.

## Synthetic Monitoring vs. Real User Monitoring

Let's start with a common comparison. Synthetic Monitoring, (also known as [synthetic testing)](https://raygun.com/blog/synthetic-testing/) creates synthetic interactions with your website to predict performance and monitor uptime. Because it uses scripts to predict behavior, it can't account for the complex ways users navigate your apps--it will only test for what you ask it to.

Real User Monitoring, on the other hand, takes data from _how real users_ are experiencing your app. RUM is a passive form of monitoring and sits in the background constantly analyzing how your application is performing for end users.

## Real User Monitoring vs. Google Analytics

A common question about RUM is "Can't I just use Google Analytics to find slow loading pages?"

Well, yes you can, but [Google Analytics (GA) isn't a competitor to RUM](https://raygun.com/blog/real-user-monitoring-google-analytics/), and you'll need to run both as part of your monitoring and analytics strategy. The main difference is that GA looks at where site visitors came from, and how effective marketing channels are in terms of traffic. RUM, on the other hand, is designed specifically for development teams to identify and solve problems within their control, for example, which assets are slowest.

A few more differences are:

  * GA uses sampled data for reporting purposes, which can show different results for large datasets
  * No code-level performance view. You can see that there is a slow loading page, but GA doesn't tell you why
  * GA can't give you any user identifiable information, unlike RUM, which allows you to reach out to frustrated users easily

Although both include browser, platform, and device data, RUM should be the choice for your development team.

## How Real User Monitoring Collects Performance Data

RUM collects data via a small piece of code embedded on each page. The code sends information directly from a user's browser. As the user explores your website or mobile app, the code collects the information, which is sent back to a centralized dashboard.

There is usually no performance overhead, as there is no agent, and data is collected both non-blocking and asynchronously.

Here's a rundown from Alistair Croll and Sean Power in the book [Complete Web Monitoring](http://archive.oreilly.com/pub/a/web-development/excerpts/9780596155131/chapter-10.html), published by O'Reilly.

![How most Real User Monitoring works](https://raygun.com/blog/wp-content/uploads/2018/02/2018-02-14_11-05-06.png)

> _Visualization of RUM data being collected and presented_

#### Data Collection Process

  1. **Capture.** The monitoring system captures page and object hits from several sources--JavaScript on a browser, a passive network tap, a load balancer, or a server and its log files.
  2. **Sessionization.** The system takes data about these hits and reassembles it into a record of the pages and components of individual visits, along with timing information.
  3. **Problem detection.** Objects, pages, and visits are examined for interesting occurrences--errors, periods of slowness, problems with navigation, and so on.
  4. **Individual visit reporting.** You can review individual visits re-created from captured data. Some solutions replay the screens as the visitors saw them; others just present a summary.
  5. **Reporting and segmentation.** You can look at aggregate data, such as the availability of a particular page or the performance on a specific browser.
  6. **Alerting.** Any urgent issues detected by the system may trigger alerting mechanisms.

Good presentation and customization of data is arguably the most important feature of a RUM tool, so the tool you choose needs to do the heavy lifting when presenting the data.

## Benefits of Real User Monitoring

  * Full visibility into software performance
  * Pinpoint the reason pages are slow
  * Track high-value customers and their experience
  * Reduces cost to acquire customers
  * One of the best ways to understand load times in different locations
  * Data visualizations on web and mobile performance

## Who is Real User Monitoring for?

### Front-end Developers

As a front-end developer, you spend most of your time in the thick of the code-base. You are all about code quality, and how performance issues are affecting end users. When it comes to page performance, [pinpointing where](https://raygun.com/blog/real-user-monitoring-matters/) the performance issue is usually the most time-consuming task. RUM gives you an easy way to see individual resources causing issues, fix issues across multiple pages, improve performance and prioritize fixes.

### Product Managers

If you are a product manager, you are responsible for ensuring your products are meeting the requirements set out in the roadmap. You don't need the deep code-level knowledge, but you do need to discover high-value pages that perform poorly. The dashboards in a RUM tool will be most important. Monitor trends over time, too.

![Real User Monitoring shows the page status and load times](https://raygun.com/blog/wp-content/uploads/2018/02/2018-02-14_12-56-14.png)

> _RAYGUN MAKES IT EASY TO SPOT SLOW LOADING PAGES WITH INSIGHTS_

### Technical Leads

Where RUM helps a technical lead the most is to assess the health of an application at a glance. There's no need to interrupt your development team and ask them to manually crawl your website for issues. Prioritize the worst pages in your backlog so you get peace of mind that users are having a great experience.

## Limitations of RUM

For all it's benefits, RUM does have some limitations:

  * RUM is useful in pre-production environments, just not many people may have the traffic here to get useful information. This is where synthetic testing can help
  * RUM can't track server performance or server level API calls. Rather, RUM tracks users where they are interacting with your application. Many teams use a Real User Monitoring tool alongside an [Application Performance Management](https://raygun.com/blog/what-is-application-performance-management/) tool for this reason.

## How Real User Monitoring Saved Our Customers 75 Hours per Month

Here at Raygun, we also leverage our own tools to make our product better. When we reviewed our [website performance using RUM](https://raygun.com/blog/saving-75-hours-with-real-user-monitoring/), we noticed that the XDReceiever calls were not very fast. The reason was that the connection limits to the same domain were saturated, and no caching occurred on the response.  
After checking why, it was because the file was being called a lot--which makes sense as every page load in the web app needs to call the API to fetch data.

Because Real User Monitoring collects all the timing data from every request and gives the average amount of time plus the total call count, we could see that even though the call wasn't expensive, it was called a lot:

![RUM revealed a high transfer time ](https://raygun.com/blog/wp-content/uploads/2018/02/2018-02-12_15-19-00.png)

> _Screenshot showing the speed breakdown_

USING RAYGUN, WE COULD SEE THE TIMING DATA EASILY

When I multiplied how often it was happening with the amount of time it took to load, it stacked up to a staggering 75 hours of time spent every month just to set up for the cross-domain calls!  
Turns out we added this code to support IE9. We cleaned the code, removed support and saved our customers 75 hours per month.

## 6 Essential Features of Real User Monitoring

For any monitoring tool to be useful in a development team, the huge amount of data should be presented in a way that the whole team can digest. The data must be both actionable and customizable to your needs.

So with those criteria in mind, let's look at the features a RUM tool must have for developers to improve their web and mobile performance.

### Detailed Page-By-Page Session Tracking

Are users getting stuck, and was the problem a third party script or a software error? As RUM tracks individual users, you'll also be able to see a user's journey through the application and see where they got stuck. Your development team should be able to isolate the problem from here so no-one else runs into the same issues.

![Real User Monitoring shows the interactions of a user in a Session Trace view](https://raygun.com/blog/wp-content/uploads/2018/02/2018-02-15_09-42-12.png)

> _RAYGUN'S SESSION TRACE SHOWS ALL THE INTERACTIONS A USER, MAKING IT EASY TO REPLICATE ISSUES_

### Performance Data for Every Asset, Web, and Mobile View

Real User Monitoring offers performance timings for every page of your application, with a full waterfall view of assets. This is important data but made even more powerful as it is from the _specific user sessions_ of customers interacting with your application.

### Integration with Crash and Error Data

Because each user gets their own user profile, RUM can record a full history of crashes and errors that user experienced. With Raygun's Real user monitoring integrated with crash reporting, you can cross reference user experience with crash reporting data.

### Customizable Dashboards

What does UX success look like in your team? Performance monitoring may look very different across job roles. High-level charts don't help developers, while code-snippets are useless for product managers. A RUM tool should present data in an easy-to-digest way but also provide the diagnostic details you need to fix an issue. [Customizable dashboards](https://raygun.com/blog/dashboard/) are a great way to do this.

### Filtering

If your development team knows there's a problem with a certain browser caused by a deployment, you can save a tremendous amount of time with a [filtering system. ](https://raygun.com/blog/real-user-monitoring-filters/)Raygun, for example, has filters for:

  * Anonymous user
  * Browser and browser version
  * Country code
  * Device
  * Operating system
  * Tags
  * URL
  * Version
  * Data comparison

Performance success is different for every development team, so customizing data is also an important feature of a RUM tool. Analysing and comparing performance data like browser, country, device, operating system, and version helps developers understand how these dimensions affect performance.

### Country, State, and City Geodata

For example, is your target market large shipping companies in Asia, specifically China? You need to make sure anyone accessing your website from large coastal cities is having an optimal experience. Real user monitoring will surface performance data and correlate it to a city so you can prioritize your target market, and spend your resources where they matter.

![Raygun's Real User Monitoring shows the geo breakdown, including city, state and country ](https://raygun.com/blog/wp-content/uploads/2018/02/2018-02-14_13-01-51.png)

> _RAYGUN SHOWS COMPREHENSIVE GEO DETAILS RELATING TO PERFORMANCE_

## So, What's the Future of Real User Monitoring?

All monitoring tools must provide details on your end users and give actionable data to help you improve customer experience.

[Raygun's Software Intelligence platform](https://raygun.com/), for example, uses both RUM and Crash Reporting to make discovering and resolving issues easy. Raygun then presents this in data customizable dashboards. You can see exactly who the problem affected, what caused the problem, how many users this problem affected, then all the details you need to fix it.
