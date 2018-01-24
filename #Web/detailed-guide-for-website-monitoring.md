# Detailed Guide for Website Monitoring

_Captured: 2017-10-27 at 17:12 from [dzone.com](https://dzone.com/articles/detailed-guide-for-website-monitoring-2?edition=334741&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202017-10-27)_

Now more than ever, your web platform performance is weighty. Most online users expect less than a 2 second load time for your web resources. When customers are [satisfied with website speed](http://www.monitis.com/pageload/) they are more likely to follow survey, to register or make a purchase. Regardless of the fact whether it's a web page, online shop or [SaaS](https://www.monitis.com/blog/saas-integrations-trends-and-challenges-to-watch-for-in-2017-part-1/).

## What Is Website Monitoring?

Website monitoring is the process of checking web page or web application availability, performance and functional. It allows you to be sure that your online products are always available and your potential customers don't suffer unexpected downtimes.

## Why Is Website Monitoring Important?

According to the [European Ecommerce Page Speed and Web Performance Report](http://shop.oreilly.com/product/0636920041450.do), around the world, the speed with which websites and web applications perform is emerging as a critical business issue. While this awareness lags in some parts of the world more than others, what is certain is that internet users are very aware of the issue of poor website performance, regardless of their location.

If [page load time](http://www.monitis.com/pageload/) will be more than 3 seconds, 6-39 % of users will leave your page.

![](https://www.monitis.com/blog/wp-content/uploads/2017/10/page_load_site_rate.png)

According to the survey "['Need for Speed,' 1&1 Internet. 2011"](https://www.safaribooksonline.com/library/view/time-is-money/9781491928783/ch01.html) of 1500 internet customers, users who experience even a two-second slowdown from the speed they've come to expect are unsatisfied with performance and simply do less on the site.

## Internal and External Monitoring

There are many methods to **monitor your website performance** and they are divided into two main categories: internal and external monitoring.

### External Monitoring

External monitoring allows you to monitor all your web resource parameters. First of all, define what criteria you need to monitor.

  * Web page availability or uptime rate (Uptime Monitoring)
  * Average Web page load time (Full Page Monitoring)
  * Web page functionality (Synthetic Transaction Monitoring)
  * Web page and scenario stress resistance (Web Stress Tester)
  * Real User Monitoring (quantity of users)
  * API monitoring (JMeter)

### Internal Monitoring

Internal monitoring can be used in your local network when a resource which should be monitored is not available from global network. For Internal or server-device monitoring all you need to do is [download](http://www.monitis.com/support/server-device-monitoring/download-agents) and install Smart Agent for Linux or Windows, then add Server/Device monitors from your Monitis dashboard.

### What Can You Monitor?

Everything which is possible to monitor externally plus your local devices' performance like local network, server CPU, memory and drive utilization, bandwidth consumed by your network interfaces, different system processes, status of services running on your server or your system events.

## Uptime Monitoring

[Uptime monitoring](http://www.monitis.com/blog/uptime-monitoring-for-the-rest-of-us/) is a regular checkup of availability and response time of a website from a different location. It is critical for every business. If a page is not available, it means that your business is not available on the internet. Your potential customers will be dissatisfied or, even worse, will move to your competitors' page. You should be the first person who is informed about any issue connected to your web page in order to react as quick as possible. There are many tools and sources for web page monitoring.

![Image title](http://www.monitis.com/blog/wp-content/uploads/2017/10/uptime-locations-fin.png)

> _Location list from which you can monitor your web page._

![Image title](http://www.monitis.com/blog/wp-content/uploads/2017/10/uptime-monitor.png)

> _Uptime monitoring example from many locations_

There are many protocols which can be used for uptime monitoring like HTTP, HTTPS, PING, DNS, PING, FTP, TCP, UDP, SIP, etc..

## Full Page Load Monitoring

The average web users perceive load time as being 15% slower than it actually is. It gets worse. When recalling the experience, users remember load times as being 35% slower.

In average, users believe they spend 9 minutes per day waiting for slow websites. This translates to two full days [every year](https://www.slideshare.net/stoyan/psychology-of-performance/51).

With the growing demand for speed and all the psychology on top, knowing your site is up is not enough. You need to know what element, when and where becomes a showstopper. With the help of Monitis Full Page Load monitoring, you will get load time information on each element, for each hour. A comprehensive report on all the resources will instantly identify the cause of failure if a page is not loading during the expected period of time.

![Image title](http://www.monitis.com/blog/wp-content/uploads/2017/10/fplmoitor.png)

> _Net view of FPL monitor._

FPL monitor allows you export historical data for statistic and results analyzing. You can also exclude 3 rd part resources if there need be.

From monitor settings, you can choose preferable maximum load time for your page and if the load time is higher than the set maximum load time, the monitor will report a failure and you will receive a notification respectively.

With full page load monitoring, you can use the content matching feature to lookup text strings in the source code of your web page. From FPL monitor settings you can choose text or phrase which should be available on your page e.g. if the page is loading but the text doesn't exist on the page you will receive an alert notification.

![Image title](http://www.monitis.com/blog/wp-content/uploads/2017/10/fplmonitorsettings.png)

_FPL monitor settings._

Based on Full Page Load time statistic analyze you can predict further behavior of your hardware and consequently will be able to plan your hardware upgrade without having an impact on your page performance.

## Synthetic Transaction Monitoring

Another important factor is web page functional checking. For instance, you have an online e-commerce platform that must be available 24/7. Your customers certainly will do below mentioned actions: visit your web page, register, log in with their usernames and passwords, surf in the market, choose some products, add them into their basket and pay for them using one of your integrated payment methods. If one of these steps is not completed successfully you will lose both the potential clients and money.

So what can you do for avoiding such cases? You should regularly test and perform the same actions as your users do. It will take a lot of time and will be too boring. Instead, you can use [Synthetic Transaction](http://www.monitis.com/blog/what-is-synthetic-transaction-monitoring-and-who-needs-it/) monitoring.

![Image title](http://www.monitis.com/blog/wp-content/uploads/2017/10/transaction-monitor-view.png)

> _Transaction recorder_

Synthetic transaction monitoring uses a predefined script to perform the same actions as your users. You can easily record a script with transaction recorder and then set up monitor which will use the recorded script. If you need a custom script you ask Monitis [Support](http://support.monitis.com/) team will record and upload the script for you within 48 hours (intricate scripts may take longer).

The script will imitate web transaction flow and check the functionality of each step. You can choose loading time for each step or action and if time is higher than predefined, the monitor will generate an alert and notify you. In alert notifications, you will see all necessary information: the cause of the alert, in which step the script is failed and the screenshot of your page at the moment of failure.

It means that you will be immediately informed if your page or one of the steps will not function as expected. Monitis Synthetic Transaction Monitoring allows you to run the script starting from every 5 minutes. And different locations are also available for this type of monitoring, allowing you to keep control from all business-crucial locations. This will help you be safe 24/7/365 of any unusual behavior.

## Web Stress Tester

Your page can function normally till the moment it's overloaded. For understanding average acceptable load for your web resource, you can perform load testing. **Web stress testing** puts a predefined load on a service to show how it functions under unusual conditions, e.g. you can test your page during 5-15 minutes for up to 2000 users and understand whether the page stays stable. If you need to check page functionality during load time you can perform scenario stress testing.

## Real User Monitoring

[Real User Monitoring](https://www.monitis.com/blog/what-is-real-user-monitoring/) ([RUM](http://www.monitis.com/real-user-monitoring)) collects data from actual users to give your insight into the performance of your website.

Real User Monitoring allows you to monitor real user interaction with your website to determine if the users access different pages on your website quickly and without errors and to identify and troubleshoot performance problems.

RUM is collecting user data about your website page views and load time and where the time is spent, starting from the moment the user enters the page address or clicks the link until the web page has completely loaded and rendered to the user.

## API Monitoring

JMeter as a solution for **API monitoring**. [JMeter](http://www.apache.org/) is an open source testing software. It is 100% pure Java application for load and performance testing. JMeter is designed to cover categories of tests like load, functional, performance, regression, etc., and can be used to test performance both on static and dynamic resources like Web dynamic applications.

## **Conclusion**

Your site is an organic entity that needs constant care and monitoring to stay functional. My greatest hope in writing this article is that I've helped motivate you to embrace performance as an evergreen project, to enjoy the thrill of seeking out innovative fixes for new performance challenges, and to celebrate the impact of performance wins on your business.

Sure, implementing a few of them is better than implementing none, but the goal is to make your website so great that people would want to come back over and over again.

Write in the comments in what other ways you can make a website great.

Opinions expressed by DZone contributors are their own.
