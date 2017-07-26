# 8 Tips to Decide the Number of Concurrent Users for Your Test

_Captured: 2017-04-24 at 18:50 from [dzone.com](https://dzone.com/articles/8-tips-to-decide-the-number-of-concurrent-users-fo?oid=twitter&utm_content=bufferd232a&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

How many virtual users should you run on your performance tests for your website or app? That's not an easy question. Even if you know [Apache JMeterTM](http://jmeter.apache.org/) or [Gatling](http://gatling.io/) to the T, they still can't indicate the number of concurrent users you should have send requests to the URL you are testing.

This is because the number of users you should test is a business and product decision, that is based on past user scenario patterns, future expectations, marketing initiatives, and product requirements.

So what should you do if you are a tester? Here are a few tips that might help you get started:

## 1\. Check the Server Logs

The server logs will contain the history of web requests, including client IP address, date and time, and the page requests. You can use this data to paint a picture of the number of real users who visited your website and which actions they performed on it.

## 2\. Cross-reference the Information With APM Data

[APMs](https://www.blazemeter.com/blog/ultimate-devops-tools-ecosystem-tutorial-part-6-operate?utm_source=BM&utm_medium=BM_blog&utm_campaign=eight-tips-deciding-number-concurrent-users-your-test) provide an in-depth analysis of user information and help identify trends and scenario profiling. Compare the picture that came from the logs to the one you received from your APM tools, check if anything is missing or contradictory, and enrich your understanding of how users behaved on your website. You can also use Google Analytics.

![Image title](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/Screen%20Shot%202017-04-04%20at%204.15.15%20PM%20\(1\).png)

Identifying trends in website growth is also important. If your traffic is constantly growing by 10%, take this into account and add more users to your test accordingly.

## 3\. Look for Bottlenecks and High-Stress Points 

Look for places where user traffic spiked, chart different trends and check where your system was close to reaching its limit. Include those numbers in your testing, because they signify potential crashing points in real-time.

## 4\. Check Product Requirements

When your website or app were planned, and as they are being upgraded and improved, your product manager probably decided on their capacity. This decision was based on the company's business plan and business goals. Check the numbers with the product manager, and make sure they are included in the testing. Future plans are probably also based on those numbers, so it's important to ensure your app or website can handle the loads. If they can't, things should be planned accordingly.

## 5\. Find out if There Are Any Expected Campaigns or Big Events

Campaigns, [events](https://www.blazemeter.com/blog/your-site-or-app-ready-black-friday-2016-infographic?utm_source=BM&utm_medium=BM_blog&utm_campaign=eight-tips-deciding-number-concurrent-users-your-test), and [holidays](https://www.blazemeter.com/blog/5-valentines-day-tips-load-testing-dating-websites-and-apps?utm_source=BM&utm_medium=BM_blog&utm_campaign=eight-tips-deciding-number-concurrent-users-your-test) might bring joyous spikes of traffic that could increase your company's sales. But that won't happen if your website crashes. Check with marketing if anything is planned and increase the number of users you are testing when preparing for these events, accordingly.

## 6\. Start Out by Testing 80% of the Capacity

Once you decide on the numbers, run [load tests](https://www.blazemeter.com/jmeter-load-testing?utm_source=BM&utm_medium=BM_blog&utm_campaign=eight-tips-deciding-number-concurrent-users-your-test) for 80% of the capacity and monitor your [KPIs](https://www.blazemeter.com/blog/load-testing-kpis-part-1-what-are-kpis?utm_source=BM&utm_medium=BM_blog&utm_campaign=eight-tips-deciding-number-concurrent-users-your-test) and how your system reacts. Ensure everything is completely stable, memory capacity is mellow, CPU is low, and recovery from spikes is quick. Everything should be working perfectly for 80%. If something seems jittery at this point, you can be pretty sure that you won't be able to count on 100%.

## 7\. If the Test Succeeded, Slowly Climb Up to 100%

If the 80% test worked, climb up to 100%. If not, identify bottlenecks and errors and fix what needs fixing. Now, test your system. This is the number of users you are expecting on your website, according to previous user patterns, trend analysis, product requirements, and expected events. Check for memory leaks, high CPU usage, unusual server behaviour, and any errors. If things aren't working now, this means they probably won't be working in real-time. Fix what needs fixing. Run these tests again to be sure your fixes were implemented properly and no performance regression has taken place.

## 8\. Bring Your System to the Limit

Your system is working properly under the loads you defined - good job! But always expect the unexpected. What if your competitor's website crashes bringing you boatloads of traffic? What if a celebrity says something that suddenly causes huge interest in your product? Be ready. True, you can't prepare for an infinite number of users, but you can know what your system's weaknesses are.

To do that, [stress test and soak test](https://www.blazemeter.com/blog/performance-testing-vs-load-testing-vs-stress-testing?utm_source=BM&utm_medium=BM_blog&utm_campaign=eight-tips-deciding-number-concurrent-users-your-test) your system and make them crash. Then, analyze the results and see where your more sensitive points are. When you have that data, you can decide if you want to change your infrastructure or code or leave things as they are, and if anything happens in real-time you will know exactly where to go to address the issues.

That's it! I hope these tips assist you in building your performance scenarios.

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

### Like This Article? Read More From DZone
