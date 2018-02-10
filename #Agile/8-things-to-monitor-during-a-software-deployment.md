# 8 Things to Monitor During a Software Deployment

_Captured: 2018-02-07 at 19:34 from [dzone.com](https://dzone.com/articles/8-things-to-monitor-during-a-software-deployment?edition=358124&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-07)_

### In this post, we take a look at eight areas to monitor during a software deployment, no matter what tools you're employing, for a smoother deployment.

**Best practices for [getting to continuous deployment](https://dzone.com/go?i=268427&u=https%3A%2F%2Finfo.rainforestqa.com%2Febook-getting-to-continuous-deployment%3Futm_campaign%3Dgetting-to-continuous-deployment%26utm_medium%3Ddisplay%26utm_source%3Ddzone) faster and with dramatic results in reduced outage minutes, development costs, and QA testing cycles. Brought to you by [Rainforest QA](https://dzone.com/go?i=268427&u=https%3A%2F%2Fwww.rainforestqa.com%3Futm_campaign%3Dhome-page%26utm_medium%3Ddisplay%26utm_source%3Ddzone).**

As software developers, our ultimate goal is to get our hard work deployed to production. Thanks to [agile development](https://stackify.com/agile-methodology/), [DevOps](https://stackify.com/what-is-devops/), and continuous [deployment tools](https://stackify.com/software-deployment-tools/), that process is quicker than ever! It is important to remember that a software deployment is more of a process and not a single event. As part of that process, you need to be monitoring your production servers and applications to ensure that everything is still running smoothly.

In this article, we are going to discuss **8 critical items you should monitor** during your software deployments.

### **1\. Know Your Error Rates**

Application errors are the first line of defense when it comes to identify application problems. It is really important that developers collect all of their errors across all of their servers to monitor them. They are especially critical during a deployment to quickly spot new application problems.

During a deployment they can also create a great deal of noise. As part of a deployment, it is common for applications to be restarted in mid-stream. This can cause a lot of transient errors like SQL connection issues, thread abort exceptions, and a wide array of other problems.

**Tip:** It is important to know what your standard application error rates are before the deployment, so you have an idea whether you are seeing an uptick in errors after the deployment or the error rate is normal.

**Tip:** Look for new application errors that you have never seen before. Odds are, there is a new null reference exception, SQL timeout, or some other error that will surface with the new deployment. Find it quickly and get ready to hot fix it.

Note: It is important to monitor your application for HTTP 4xx and 5xx errors along with exceptions being logged by your code itself.

### **2\. Compare Web Traffic Volume and Page Load Times**

How much traffic does your application get and what are normal page load times? These are key metrics that you should be monitoring before and after a deployment. If you suddenly get a lot more or less traffic, something could be really wrong.

A big dip in traffic could mean that users are getting errors and can't further navigate to additional pages within your application. This would reduce the overall volume of traffic to your site.

Sometimes this problem can also manifest itself in the application you didn't even deploy. For example, if your application uses a microservices architecture or makes a lot of internal HTTP web service calls, a new deployment could dramatically change the downstream traffic to your other applications. Keep an eye on their traffic levels to make sure nothing has change dramatically.

### **3\. Track Your Apdex or Customer Satisfaction Scores**

Monitoring the apdex score or customer satisfaction score for your application is a great way to keep the pulse on how well your application is performing. Stackify Retrace automatically tracks this as a customer satisfaction score.

This score is based on how many web requests were fast, sluggish, slow, and failed. It is a simple math formula that helps you understand the overall performance of your software. Tracking it is a great industry best practice.

At Stackify, our goal is for our score to be 99%. It is a metric that we monitor constantly. During a deployment you can expect your score to dip slightly. Just after a deployment you should check your score to make sure that it comes back to a normal level.

### **4\. Server Counts, Load, CPU Usage**

Even when deploying to the cloud, CPU usage and overall server load still matters. Sometimes a slight code change can cause huge differences in CPU usage and overall performance. This is especially true in applications that auto-scale across a lot of servers. A few code tweaks here and there can reduce the overall number of servers that you need.

It is important to keep an eye on the # of servers needed to run your application and the overall CPU usage on your servers.

### **5\. Database and SQL Query Performance**

If your application uses a SQL database, probably each deployment is going to include some changes to how your SQL database is used, including new SQL queries, changes to existing ones, etc.

You should always track which SQL queries are used the most and which use the most resources within your database server. A slight change to a SQL query could cause a major bottleneck in your performance!

### **6\. Performance of All Application Dependencies**

Today's applications use a wide variety of application dependencies. Including SQL & NoSQL databases, caching, queues, storage, HTTP web services, and much more. It is important to keep an eye on the performance of all of these dependencies. These include popular services like Redis, Elasticsearch, MongoDB, etc.

A slight code change to how your application access something like Redis or an HTTP web service could dramatically change the performance of your code in production. You want to keep an eye out before and after a deployment to see if any major changes have occurred.

### **7\. Internal Communications (Slack)**

One of the keys to a successful software deployment is communication. At Stackify, we rely heavily on Slack as the central hub of all communication within our company. This includes doing deployments.

We have a #deployments Slack channel that anyone can monitor to know exactly what is going on before, during, and after a deployment. We also utilize automated Slack alerts via Bamboo which we use for doing deployments.

As we know, doing a deployment isn't just the single push of a button. When we do deployments at Stackify, we have to first push SQL change scripts to over 1,000 databases. We also have to deploy up to 10 different web and background service applications that run our infrastructure. This is quite a process that takes time.

Communicating the progress over our Slack channels helps everyone keep in sync. Anyone who wants to monitor the progress can follow along.

### **8\. Regression Testing**

After you have pushed out new code, it is always a good idea to do some final regression testing. This could be via automated synthetic tests or by doing some quick tests of your own. Even if I have awesome application monitoring setup with a tool like Retrace, I always feel better knowing I have logged in myself and clicked around on a few critical pages within my application.

Many organizations also have entire processes around doing release validation and regression testing. They will re-run many of the tests they run in QA. It is also common to re-test bugs that were supposed to be fixed in the release before communicating to customers that the fixes have been deployed.

If you have automated tests, monitoring them definitely applies to this article. Even if you don't, be sure to monitor Slack to make sure that all the final regression and validation tests pass. That is your signal to have a beer and celebrate another successful software deployment!

## **Summary**

Software deployments are the end result of our hard work. They can also be stressful due to the risk of potentially deploying bad code. It is important to monitor your software at all times with solutions like [Retrace](https://stackify.com/retrace/). This helps you quickly identify when new problems arise or key metrics around error rates, performance, and others are abnormal.

**Discover how to [optimize your DevOps workflows](https://dzone.com/go?i=268430&u=https%3A%2F%2Finfo.rainforestqa.com%2Febook-getting-to-continuous-deployment%3Futm_campaign%3Dgetting-to-continuous-deployment%26utm_medium%3Ddisplay%26utm_source%3Ddzone) with our on-demand QA solution, brought to you in partnership with [Rainforest QA](https://dzone.com/go?i=268430&u=https%3A%2F%2Fwww.rainforestqa.com%3Futm_campaign%3Dhome-page%26utm_medium%3Ddisplay%26utm_source%3Ddzone). **
