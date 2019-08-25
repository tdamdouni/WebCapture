# Software Quality: The Top 10 Metrics to Build Confidence - DZone Agile

_Captured: 2019-08-24 at 18:57 from [dzone.com](https://dzone.com/articles/software-quality-the-top-10-metrics-to-build-confi?edition=520325&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202019-08-24)_

How do you measure quality in software engineering? I guess this is the question there will always be a debate on. There are so many approaches to this question that finding only one answer is just impossible. In this article, we will be listing the quality-related metrics that the top engineering teams have been keeping track of, and see when and how you should use them. 

However, note that when you think about it, one can wonder if the quality is a goal in itself. **The confidence in being able to grow and change behaviors without disruption seems to be more what matters. **In that case, quality metrics are surely important, but their evolution over time is at least as important. 

Our goal with this article is to help engineering teams approach quality in a better way. Let’s get to the list of engineering quality metrics. 

## 1\. Number of Bugs — Possibly by Priority or Severity

The number of bugs will, in general, start increasing in the middle of a project’s lifecycle. A few days or weeks (depending on the size of the project) before the deadline, the team will focus on reducing the number of bugs, until the number of bugs reaches a kind of asymptote. This asymptote is eventually representative of the overall quality of the project’s product. So tracking the overall number of bugs (distinguishing their priorities) is a good indicator. 

However, not all bugs are equal. That’s why most teams assign a priority and/or severity to bugs. It could be interesting to track P1 bugs and P2 ones for instance, and only those. This depends on the maturity level of your product. For a new product, you will want to stay focused on P1s. Indeed, a product with lots of P1s will be perceived as just not working. 

If you don’t have any P1s anymore, but still P2s, users will still experience those bugs and that might impact their perception of the product negatively. 

If you want your product to be perceived as high-quality, at the level of Apple, for example, this actually happens when you have tackled a lot of those P3 and P4 bugs. This is the level you need to reach. So focus on tracking only what matters for you now.

![](https://lh3.googleusercontent.com/-fO2pbF3K98aCmGclP-BrRAIpccOizQrS92f3NThAdYxB7jws95wrtI8JzhSO4ZDiC4Z0uNY8NfGu1RkFe88EZKdIOgTQ0CFaUPwgajjCq_JeMGWrfwD-7D6PpJZTTUxKYJ6pyxH)

**When to use it?**

This metric is very helpful if your product quality is important to your business. And if so, you should constantly track it. However, if you got all P1s and P2s resolved, you might want to aim for a higher quality standard by tracking P3s for instance.

## 2\. Change Failure Percentage

[Accelerate](https://www.amazon.com/Accelerate-Software-Performing-Technology-Organizations/dp/1942788339/ref=sr_1_1?keywords=accelerate&qid=1561684287&s=gateway&sr=8-1) defines failure as a change that “results in degraded service or subsequently requires remediation (e.g., leads to service impairment or outage, requires a hotfix, a rollback, a fix-forward, or a patch.)”. So this rating is the number of deploys resulting in a failure on the total number of deploys.

Note that this definition does not include changes that failed to deploy. That information is useful, but not this KPI’s focus. 

**When to use it?**

If you focus on turning frequent deployments into an everyday habit, in order for this to have value, you need to keep the failure rate low. As a matter of fact, this rating should decrease over time, as the experience and capabilities of the DevOps teams increase. An increasing failure rate, or one that is high and does not go down over time, is an indication of problems in the overall DevOps process. It is a good proxy metric for quality throughout the process.

## 3\. Pull Request Quality

Pull requests can give you great visibility on the overall complexity of the codebase. The more complex the code base is, the higher the chances the following metrics will be high:

  * the percentage of times pull requests to break the build or fail to pass the test suite; 
  * the percentage of merged vs rejected pull requests; 
  * the number of comments by pull request – you don’t want a number that’s too low, but you also don’t want a number that is too high. These metrics show how your team collaborates and if there is enough attention drawn in your pull requests. It can be an indirect indication of the quality of the code pushed to production. 

**When to use them?**

This metric is not about measuring the quality of the DevOps process, as for [change failure percentage](https://anaxi.com/software-engineering-metrics-an-advanced-guide/#052), but how your team works and collaborates. How are code reviews used and are those useful? Measuring the evolution of the merged versus rejected pull requests will help you understand if your team is improving with time. You could also drill down by team members to see if they are improving too.

## 4\. Test Coverage Ratio

This metric is simply the ratio between the total lines of code in the piece of software you are testing, and the number of lines of code all test cases currently execute.

What is the generally accepted ‘sufficient’ test coverage when measured by the number of lines of code executed? The consensus hovers around 80% – higher for critical systems (definition of critical may vary by industry, geography, user base, etc.).

**When to use it?**

You don’t need 100% testing coverage, for sure. However, knowing where you stand and keeping track of it helps to see if you are trading velocity for quality. Keep in mind that “**a high-quality product built on bad requirements, is a poor quality product**”, especially with test coverage. 

## 5\. Mean Time Between Failures (MTBF) and Mean Time To Recover/Repair (MTTR)

Both metrics measure how the software performs in the production environment. Since software failures are almost unavoidable, these software metrics attempt to quantify how well the software recovers and preserves data.

![](https://lh4.googleusercontent.com/ivNAyDQKHe7ajrUn6UI9tWwnTjugjJqm_pji9mkMHPz-xMj4rnveUAPN9JoXnk2K8vm0RjyH9dps9aU6o3gHNYe46zy34-f05k1HGfO7qPOivIADWTodtqJMNtKtEa0gRM1M9PGU)

If the MTTR value grows smaller over time, that means developers are becoming more effective in understanding issues, such as bugs, and how to fix them.

**When to use them?**

These metrics are very interesting if used by the team with a specific goal: “We need to achieve this level of MTBF or MTTR on our product.” That will foster responsiveness from your team on important issues raised by customers and will help you keep a high-standard for your product, as well as for your team. To improve performance on these metrics, the team might understand they need to solve the real cause of issues, instead of easy patches. 

## 6\. Service-Level Agreement (SLA)

Every team has its own definition of SLA. But here is the one that Airbnb uses and that you could find very interesting. The SLA is the percentage of blocker bugs that your team fixed and deployed within a certain time (e.g., 24 hours for blocker bugs and five days for critical bugs). What you might really like about this metric is that it gives you a great understanding of **your product quality from a user’s standpoint**.

![](https://lh5.googleusercontent.com/q108aYD4Kjs1DGprmaCZJo9CcJjnSiZd8NF5LCz0HBSOtnTt8hEgo1PBEgB6FrDC6v4tb3ptjTvKREkOfXs1GaCbbTBzOppc-UNMd9zSrRKQ2pjY-AdIKb51S1jr-0li7D_x2UEs)

**When to use it?**

This metric is very close to the [MTTR](https://anaxi.com/software-engineering-metrics-an-advanced-guide/#055), but is not limited to software failures. It extends to any type of bugs. Similarly, this metric is very interesting if used by the team with a specific goal: “We need to achieve this SLA on our product.” This metric fosters product quality ownership and responsiveness from your team. That’s why Airbnb uses it.

## 7\. Defect Removal Efficiency (DRE)

[Defect Removal Efficiency](https://www.equinox.co.nz/blog/software-testing-metrics-defect-removal-efficiency) is used to quantify how many defects were found by the end-user after product delivery (D) in relation to the errors found before product delivery (E). The formula is: DRE = E / (E+D)

The closer to 1 DRE is, the fewer defects found after product delivery. An average DRE score is usually around 85% across a full testing program. However, with a thorough and comprehensive requirements and design inspection process, this can be expected to lift to around 95%.

**When to use it?**

This metric serves a similar purpose as keeping track of the evolution for your [number of bugs](https://anaxi.com/software-engineering-metrics-an-advanced-guide/#051). It might be redundant to track both of them. We have a preference for the number of bugs as you can differentiate which bug priority matters to you now and still have a notion of the overall amount (not just the trend).

## 8\. Application Crash Rate (ACR)

Application crash rate is calculated by dividing how many times an application fails (F) by how many times it is used (U). But there are actually several ways you can compute it.

  * **App crashes per user: ** This number shows how many users have ever faced a crash scenario. An acceptable range for this metric would be < 1%. This number should be lower for mature apps as the functions would be more stable. However, while calculating actual numbers of the whole app, faulty updates that end up in rollback instances can be ignored for an accurate representation.
  * **App crashes per session: **This number shows how many times an app crashed compared to the number of sessions. An acceptable range for this metric would be < 0.1%. However, it can be categorized into types of sessions and app flows for a better understanding of the issue.
  * **App crashes per screen view: **This number compares the total screen views that the app has received to the number of crashes. An acceptable range for this metric would be < 0.01%. This should necessarily be categorized to understand the impact of crashes on the delivery of the functionality.

**When to use it?**

This metric is interesting when you have a specific goal in mind. For instance, you could strive to reach an ACR that is [less than 0.25% in your software’s most critical user flows](https://www.apteligent.com/technical-resource/best-practice-2-maintain-a-crash-rate-of-less-than-0-25-in-your-apps-three-most-critical-userflows/).

## 9\. Defect Density

There are two different ways to look at defect density:

**Size-oriented metrics** focus on the size of the software and are usually expressed as kilo lines of code (KLOC). It is a fairly easy software metric to collect once decisions are made about what constitutes a line of code. **Unfortunately, it is not useful for comparing software projects written in different languages**. Some examples include errors per KLOC or defects per KLOC. 

**Function-oriented metrics** focus on how much functionality software offers. But the functionality cannot be measured directly. So function-oriented software metrics rely on [calculating the function point (FP)](https://www.totalmetrics.com/function-point-resources/what-are-function-points) — a unit of measurement that quantifies the business functionality provided by the product. Function points are also useful for comparing software projects written in different languages. That metric would look at errors per FP or defects per FP

Function points are not an easy concept to master and methods vary. This is why many software development managers and teams skip function points altogether. They do not perceive function points as worth the time.

**When to use it?**

Size-oriented metrics that rely on lines of code make them not useful per se. So you shouldn’t compare two different software projects with them. That’s why you might not be a big fan of using it. And function-oriented metrics are difficult to compute and agree on. You might want to introduce control measures with them, but there might be better indicators for that in the list.

## 10\. Age of Dependencies

Another indicator of the technical debt is how outdated the dependencies used in your codebase are. It could be interesting to track this, as an average of all dependencies, possibly with a variant, so you could identify when one is very old and should require your attention. 

![](https://lh4.googleusercontent.com/SD-Bu4leaZftxKoLKNfYIFXCAW-NM6fkrRXk-jwC9J47_5goA6vJTpLyRV36vIoCpCiYd5MHg8P2YTHjAlRlodpD2a33sitFGgRQAecfUnQQULfarufcOXji5ozakuFPj3nsK4l0)

**When to use it?**

This metric should be interesting to technical leads especially. This is too operational and linked to the code base to be used by a manager. If your projects have many dependencies, keeping track of the dependency age should definitely be considered.

Please note that some metrics may have not made the list because they were either not popular enough, or too far-fetched to draw any value from them. Remember software metrics should be easily understandable and should potentially lead to change and have business value. Otherwise, what’s the point?

Some metrics you may have in mind might also be part of [velocity-related metrics](https://anaxi.com/blog/2019/07/31/how-to-use-software-productivity-metrics-the-right-way/) and [process-related metrics](https://anaxi.com/blog/2019/07/31/how-to-use-data-to-improve-your-sprint-retrospectives/) that I address in [the advanced guide to software engineering metrics](https://anaxi.com/software-engineering-metrics-an-advanced-guide/). Whatever metrics you choose to use, you need to follow a few rules, if you ever want to use engineering metrics in a non-toxic and efficient way. For more on that topic,I would recommend reading [this article](https://anaxi.com/blog/2019/07/30/how-to-use-and-not-abuse-software-engineering-metrics/).

Let me know what you think, if I’ve missed any. The end goal is to build a comprehensive list of best practices concerning software engineering metrics to help teams improve their own processes.
