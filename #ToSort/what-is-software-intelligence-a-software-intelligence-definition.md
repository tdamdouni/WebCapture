# What is Software Intelligence? A Software Intelligence Definition

_Captured: 2017-05-07 at 21:48 from [dzone.com](https://dzone.com/articles/what-is-software-intelligence-a-software-intellige?oid=twitter&utm_content=buffer5d5a3&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

Software intelligence is a full-stack monitoring platform that discovers, diagnoses, and helps you resolve software issues both in production, and those affecting end users.

Instead of using disparate monitoring tools that don't communicate with each other, software intelligence combines features like crash reporting, real user monitoring, deployment tracking, and user tracking to build a more 'intelligent' view of your overall software health.

By using local agents or a small piece of code, software intelligence focuses directly on understanding the activity of your application, providing your team with valuable insights into the overall health of your software.

## **How is Software Intelligence Different From Business Intelligence Software? **

The best answer is they both have different functions and are not related, but can be used side by side.

While business intelligence software (or BI) analyzes day to day business metrics and trends, [software intelligence](https://raygun.com/blog/software-intelligence-benefits/) provides actionable data on how your application is performing in real time.

In the same way a company uses BI to coagulate disparate spreadsheeting and resource management tools, software intelligence combines several monitoring tools into one platform.

By reducing the amount of tools you need, software intelligence makes your technology stack much neater and more efficient at communicating.

## **How Does it Help Your Team? **

From server-side crashes to slow-performing pages and discovering bad deployments, software intelligence is a top down view of issues affecting end users. It offers insights into backend, front end, and server level issues in real time - as they are affecting your end users - right now.

A cornerstone of a software intelligence platform is that it is able to identify when a user has taken actions that have resulted in an unhandled exception. Using features like crash reporting's breadcrumbs, developers are able to see what exactly what happened leading up to the crash. Real user monitoring gives the who_, _with data on load times and live sessions (shown below in the Raygun platform):

![Raygun dashboards](https://raygun.com/blog/wp-content/uploads/2017/03/dashboard-1.png)

The issue can then be identified and brought to a developer's attention within seconds using integrations with ChatOps and task management software such as JIRA. Detailed diagnostic details, including the stack trace information, are then made available to the developer in order to replicate the issue quickly, fix it, and deploy the update to production. The issue is then resolved before it affects any further users, who otherwise would have run into the same problem.

The same is true for issues that aren't triggered by a user. With software intelligence in place, if a database time-outs, or poorly executed code triggers errors in backend systems, it is picked up immediately. Developers can then fix up these issues before any users are affected.

## **Understanding the components of software intelligence**

All software has problems - in fact, 'zero bug' software is not the aim. You'll find that it's how those problems are handled that set development teams apart. In traditional team settings, multiple teams are involved in the detection and resolution of software problems. This inevitably leads to a breakdown in communication and possible confusion in your team.

Software intelligence aims to breaks down these communication walls by leveraging integrations with ChatOps and deployment software to automate low-value work (like looking through log files).

![](https://raygun.com/blog/wp-content/uploads/2017/04/icon-crash-reporting-1.png)

![](https://raygun.com/blog/wp-content/uploads/2017/04/icon-deployment-1.png)

![](https://raygun.com/blog/wp-content/uploads/2017/04/icon-rum-1.png)

![](https://raygun.com/blog/wp-content/uploads/2017/04/icon-user-tracking-1.png)

A software intelligence platform has the following key characteristics that all work together:

  * Crash reporting.
  * Real user monitoring.
  * Deployment tracking.
  * User tracking.

Let's go into detail below.

### **Crash Reporting: Discover What Happened and When **

Generally speaking, only 1% of users report errors and issues with their software. Crash reporting uses an SDK piece of code to continually monitor both web and mobile applications to collect detailed diagnostics on any crashes and errors that are happening - in real time - including a detailed stack trace.

![](https://raygun.com/blog/wp-content/uploads/2017/04/crash-reporting.png)

Crash reporting software aims to give context to developers around the root cause of issues for faster triage and resolution. Without crash reporting, developers rely on reproducing issues manually - a time-intensive and sometimes fruitless process. Crash reporting software answers questions like:

  * Just how many software errors and crashes do our software applications have?
  * Where exactly in our codebase is the problem stemming from?
  * When we made a deployment, did it improve things or create a new problem?
  * Which team members are introducing and solving the most issues?
  * How is our application performing for end users in production? 

When paired with real user monitoring, deployment tracking, and user tracking, crash reporting data gains more context.

For example, you will be able to send an email to the individuals who experienced the crash without them having to report the error. This can be especially important when improving the customer's perceived value of your software. Even though they are online, they still get personal attention. If you have a business goal of improving customer service across your company, this could be a vital differentiator to success.

### **Real User Monitoring: Discover Performance Problems **

To explain real user monitoring (or RUM), the most familiar and common comparison is with Google Analytics.

Google Analytics monitors a variety of basic user interactions, including time on page and how many visitors you are getting. Google Analytics was originally built for small to medium sized retail businesses, therefore it lacks certain insights for complex enterprise websites. For example, Google Analytics relies on cookies, so if anyone has disabled them in their browser, the information is lost.

Google also sample their data rather than analyzing all available data, simply for convenience and scale. This works well for a generalized view of how your website is performing, however, professional developers generally need more specialized tools to drill down into the location and cause of performance problems.

Furthermore, some security experts have raised concerns about privacy issues in Google Analytics. Through the Google Analytics Dashboard, users can collect information on people whose websites link to social networking sites such as Facebook and Twitter.

Real user monitoring, on the other hand, tracks individual people, not just data. When used as part of a software intelligence platform like Raygun, RUM should also be HIPAA compliant, so there are little to no security risks around sensitive data.

![](https://raygun.com/blog/wp-content/uploads/2017/04/RUM.png)

RUM specifically allows you to drill into individual sessions to see what the user's navigation path was. This includes device details, operating system, location and where they encountered problems. With Raygun, for example, the data is collected using the user's browser. The IP address is used to determine the location of the customer, but that data is never stored.

![](https://raygun.com/blog/wp-content/uploads/2017/04/RUM-1.png)

> _This micro-level view allows software professionals to answer questions like:_

  * Where exactly did a user encounter a slow-loading page?
  * What caused the problem to happen to this user?
  * What was their journey path before encountering the problem?
  * Was their whole session poor or just a single page/view?
  * Was their device, connection speed, or location a factor?

When combined with crash reporting, user tracking, and deployment tracking, real user monitoring can give all sorts of diagnostic details on how decisions you made during production are affecting your users in real time. These aren't vanity metrics either - page load speed really affects your bottom line.

Pinterest is one Fortune 500 company that directly attributes 'their biggest user acquisition win' to discovering and fixing performance issues affecting end users. Amazon also followed suit quickly when they discovered that addressing performance problems in their software was the most lucrative way to make improvements to their software.

### **Deployment Tracking: Spot Bad Deployments**

The deployment process is the biggest pain point for [29% of software professionals](https://dzone.com/guides/devops-continuous-delivery-and-automation) using a continuous delivery model. Deployment tracking helps to directly address errors in deployment by surfacing them quickly alongside error charts.

![](https://raygun.com/blog/wp-content/uploads/2017/04/Deployment-process.png)

Most organizations use multiple testing environments before release. Only after each environment passes the requirements for each stage does it get moved to the next.

If the deployment is rejected, it gets rolled back to the previous phase and starts again with developers correcting any defects found. The more defects that are found and fixed, the more stable the software becomes.

Deployment tracking helps to track deployments through the multiple test environments, automatically discovering errors aiding software developers in building more robust and stable software.

Software intelligence, in turn, uses deployment tracking to deliver data on which deployments caused which errors, and how they are being received by end users. Therefore a strategic decision can be made to either fix the errors or roll back a release.

[Deployment tracking](https://www.ibm.com/support/knowledgecenter/SSSH27_8.0.1/com.ibm.rational.clearcase.books.cc_rrd.doc/introduction_to_deployment_tracking.htm) is mainly designed to give teams peace of mind that problematic deployments are picked up immediately - including the commits that made them.

### **User Tracking: It's About People, Not Numbers**

User tracking connects crash reporting data to the data collected by real user monitoring and is a key component of software intelligence. [User tracking](https://raygun.com/blog/affected-user-tracking-find-out-who-why-and-when/) is specifically designed to provide a way for organizations to effectively do damage control for performance issues that have already affected an end user.

![What is software intelligence - software intelligence usually includes real user monitoring](https://raygun.com/blog/wp-content/uploads/2017/04/globe.png)

When a large outage affects thousands of customers, it's standard practice to send an email to the customer base, or even to publicly release a statement to apologize. User tracking offers a more elegant way to manage the damage control by making use of custom segments.

This segment of email addresses can then be handed off to marketing or customer support. This way, businesses need only communicate recent outages to those that were impacted, saving notifying the entire user base and running the risk of a wider loss of confidence than is necessary.

## **Does My Company Need Software Intelligence? **

With a plethora of monitoring tools on the market, it can be confusing for businesses to make purchasing decisions and deliver strong business cases for implementing application monitoring.

However, when we start to think about the direct benefits to the business (especially large scale software projects in enterprise), it's much easier justify the implementation of a tool like a software intelligence platform. Software errors and performance problems cost money and can be the [death of an application.](https://raygun.com/blog/software-errors-killing-app/)

For example, software intelligence complements many business goals, including:

  * Migrating to cloud services.
  * Moving to microservice architecture.
  * Migrating old enterprise systems.
  * Improving customer response times.
  * Creating multi-platform software.
  * Creating agile systems.

More vitally, software intelligence provides the data needed to measure these goals. The software intelligence platform does the heavy lifting, then presents data in a way that is easy to digest:

![](https://raygun.com/blog/wp-content/uploads/2017/03/Exceptions.png)

## **Limitations of a Software Intelligence Platform **

If you are looking simply for a crash reporting solution for an IOS mobile application, software intelligence may not be the right solution (unless you build multiple applications for an agency). In this case, an open source crash reporting tool could be the best option.

## **The Future of Software Intelligence**

At the end of the day, all monitoring tools must be able to offer detailed information about end users, and implementing any tool must be weighed against real business objectives.

Depending on your business needs, you may just need a light solution such as Google Analytics or an open source logging tool. However, businesses need to focus on high-value activities in order to reduce spend and drive forward with business goals.

To achieve and maintain balance in a software development team, the data you receive is only as good as how effectively your team responds. Therefore, thorough data presented with actionable insights will lead the way for all business software.

This is precisely why [Raygun ](https://raygun.com/platform)built our platform with software intelligence at the front of mind. Tools like crash reporting and real user monitoring are more powerful when they work together to provide a holistic view of how software quality affects real people and their experiences.

Directly linking software quality to ROI is a pipe dream for so many businesses. Software businesses reliant on healthy software to make revenue fly blind without software intelligence, and issues that affect end users just never get addressed.

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
