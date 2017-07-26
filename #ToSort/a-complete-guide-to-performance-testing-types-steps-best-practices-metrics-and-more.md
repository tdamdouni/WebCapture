# A Complete Guide to Performance Testing Types: Steps, Best Practices, Metrics, and More

_Captured: 2017-05-03 at 00:58 from [dzone.com](https://dzone.com/articles/a-complete-guide-to-performance-testing-types-test?edition=294991&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-02)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Performance testing is a form of software testing that focuses on how a system running the system performs under a particular load. This is not about finding software bugs or defects. Performance testing measures according to benchmarks and standards. [Performance testing](http://searchsoftwarequality.techtarget.com/tutorial/Software-testing-fundamentals-Performance-testing) should give developers the diagnostic information they need to eliminate bottlenecks.

## Types of Performance Testing for Software

To understand how software will perform on users' systems, there different types of performance tests that can be applied during software testing. This is [non-functional testing](http://reqtest.com/testing-blog/functional-vs-non-functional-testing/), which is designed to determine the readiness of a system. ([Functional testing](https://stackify.com/functional-testing-types-tips-limitations/) focuses on individual functions of software.)

![Testing Types](https://stackify.com/wp-content/uploads/2017/04/TestingTypes.png)

_ Image credit [MindsMapped](http://blogs.mindsmapped.com/tag/system-testing-integration-testing/)._

### Load Testing

[Load testing](http://searchsoftwarequality.techtarget.com/definition/load-testing) measures system performance as the workload increases. That workload could mean concurrent users or transactions. The system is monitored to measure response time and system staying power as workload increases. That workload falls within the parameters of normal working conditions.

### Stress Testing

Unlike load testing, [stress testing](http://searchsoftwarequality.techtarget.com/definition/stress-testing) -- also known as fatigue testing -- is meant to measure system performance outside of the parameters of normal working conditions. The software is given more users or transactions that can be handled. The goal of stress testing is to measure the software stability. At what point does software fail, and how does the software recover from failure?

### Spike Testing

Spike testing is a type of stress testing that evaluates software performance when workloads are substantially increased quickly and repeatedly. The workload is beyond normal expectations for short amounts of time.

### Endurance Testing

Endurance testing -- also known as soak testing -- is an evaluation of how software performs with a normal workload over an extended amount of time. The goal of endurance testing is to check for [system problems such as memory leaks](https://msdn.microsoft.com/en-us/library/ms859408.aspx). (A memory leak occurs when a system fails to release discarded memory. The memory leak can impair system performance or cause it to fail.)

### Scalability Testing

Scalability testing is used to determine if software is effectively handling increasing workloads. This can be determined by gradually adding to the user load or data volume while monitoring system performance. Also, the workload may stay at the same level while resources such as CPUs and memory are changed.

### Volume Testing

Volume testing determines how efficiently software performs with a large, projected amounts of data. It is also known as flood testing because the test floods the system with data.

## Most Common Problems Observed in Performance Testing

During performance testing of software, developers are looking for [performance symptoms and issues](http://www.agileload.com/performance-testing/performance-testing-methodology/performance-symptoms-and-issues). Speed issues -- slow responses and long load times for example -- often are observed and addressed. But there are other performance problems that can be observed:

  * **Bottlenecking** -- This occurs when data flow is interrupted or halted because there is not enough capacity to handle the workload.
  * **Poor scalability** -- If software cannot handle the desired number of concurrent tasks, results could be delayed, errors could increase, or other unexpected behavior could happen that affects: 
    * Disk usage.
    * CPU usage.
    * Memory leaks.
    * Operating system limitations.
    * Poor network configuration.
  * **Software configuration issues** -- Often settings are not set at a sufficient level to handle the workload.
  * **Insufficient hardware resources** -- Performance testing may reveal physical memory constraints or low-performing CPUs.

## Seven Performance Testing Steps

![Performance Testing Process](https://stackify.com/wp-content/uploads/2017/04/Performance-Testing-Process.jpg)

Also known as the test bed, a testing environment is where software, hardware, and networks are set up to execute performance tests. To use [a testing environment for performance testing](https://msdn.microsoft.com/en-us/library/bb924376.aspx), developers can use these seven steps:

### 1\. Identify the Testing Environment

Identify the hardware, software, network configurations and tools available allows the testing team design the test and identify performance testing challenges early. [Performance testing environment options](http://www.kualitatem.com/blog/performance-test-environment-setup) include:

  * Subset of production system with fewer servers of lower specification.
  * Subset of production system with fewer servers of the same specification.
  * Replica of productions system.
  * Actual production system.

### 2\. Identify Performance Metrics

In addition to identifying metrics such as response time, throughput and constraints, identify what are the success criteria for performance testing.

### 3\. Plan and Design Performance Tests

Identify performance test scenarios that take into account user variability, test data, and target metrics. This will create one or two models.

### 4\. Configure the Test Environment

Prepare the elements of the test environment and instruments needed to monitor resources.

### 5\. Implement Your Test Design

Develop the tests.

### 6\. Execute Tests

In addition to running the performance tests, monitor and capture the data generated.

### 7\. Analyze, Report, Retest

Analyze the data and share the findings. Run the performance tests again using the same parameters and different parameters.

## What Performance Testing Metrics are Measured

[Metrics are needed to understand the quality and effectiveness](http://www.guru99.com/software-testing-metrics-complete-tutorial.html) of performance testing. Improvements cannot be made unless there are measurements. There are two definitions that need to be explained:

  * **Measurements** -- The data being collected such as the seconds it takes to respond to a request.
  * **Metrics** -- A calculation that uses measurements to define the quality of results such as average response time (total response time/requests).

There are many ways to measure speed, scalability, and stability, but each round of performance testing cannot be expected to use all of them. Among the [metrics used in performance testing](https://loadstorm.com/load-testing-metrics/), the following often are used:

### Response Time

Total time to send a request and get a response.

### Wait Time

Also known as average latency, this tells developers how long it takes to receive the first byte after a request is sent.

### Average Load Time

The average amount of time it takes to deliver every request is a major indicator of quality from a user's perspective.

### Peak Response Time

This is the measurement of the longest amount of time it takes to fulfill a request. A peak response time that is significantly longer than average may indicate an anomaly that will create problems.

### Error Rate 

This calculation is a percentage of requests resulting in errors compared to all requests. These errors usually occur when the load exceeds capacity.

### ![Software Testing](https://stackify.com/wp-content/uploads/2017/04/stockfresh_4526889_bug-in-the-programming-code_sizeXS.jpg)

Concurrent Users

This the most common measure of load -- how many active users at any point. Also known as load size.

### Requests per Second

How many requests are handled.

### Transactions Passed/Failed

A measurement of the total numbers of successful or unsuccessful requests.

### Throughput

Measured by kilobytes per second, throughput shows the amount of bandwidth used during the test.

### CPU Utilization

How much time the CPU needs to process requests.

### Memory Utilization

How much memory is needed to process the request.

## Performance Testing Best Practices

Perhaps the most important tip for performance testing is testing early, test often. A single test will not tell developers all they need to know. [Successful performance testing is a collection of repeated and smaller tests](http://www.orasi.com/wp-content/uploads/2016/08/Orasi_10_Best_Practices_App_Performance_Testing_WP.pdf):

  * Test as early as possible in development. Do not wait and rush performance testing as the project winds down.
  * Performance testing isn't just for completed projects. There is value in testing individual units or modules.
  * Conduct multiple performance tests to ensure consistent findings and determine metrics averages.
  * Applications often involve multiple systems such as databases, servers, and services. Test the individual units separately as well as together.
![Testing Lifecycle](https://stackify.com/wp-content/uploads/2017/04/Testing-Life-Cycle.jpg)

In addition to repeated testing, performance testing will be more successful by following a series of performance testing best practices:

  * Involve developers, IT and testers in creating a performance testing environment.
  * Remember real people will be using the software that is undergoing performance testing. Determine how the results will affect users not just test environment servers.
  * Go beyond performance test parameters. Develop a model by planning a test environment that takes into account as much user activity as possible.
  * Baseline measurements provide a starting point for determining success or failure.
  * Performance tests are best conducted in test environments that are as close to the production systems as possible.
  * Isolate the performance test environment from the environment used for quality assurance testing.
  * No performance testing tool will do everything needed. And limited resources may restrict choice even further. Research performance testing tools for the right fit.
  * Keep the test environment as consistent as possible.
  * Calculating averages will deliver actionable metrics. There is value in tracking outliers also. Those extreme measurements could reveal possible failures.
  * Consider the audience when preparing reports that share performance testing findings. Also, include any system and software changes in reports.

### Five Common Performance Testing Mistakes

There are also some mistakes that can lead to less-than-reliable results when performance testing:

  1. Not enough time for testing.
  2. Not involving developers.
  3. Not using a QA system similar to the production system.
  4. Not sufficiently tuning software.
  5. Not having a troubleshooting plan.

## Performance Testing Fallacies

Performance testing fallacies can lead to mistakes or failure to follow performance testing best practices. According to Sofia Palamarchuk, these [beliefs can cost significant money and resources when developing software](https://abstracta.us/2015/08/10/software-performance-testing-fallacies-part-1/):

### Performance Testing is the Last Step in Development

As mentioned in the section on performance testing best practices, anticipating and solving performance issues should be an early part of software development. Implementing solutions early will less costly than major fixes at the end of software development.

### More Hardware Can Fix Performance Issues

Adding processors, servers or memory simply adds to the cost without solving any problems. More efficient software will run better and avoid potential problems that can occur even when hardware is increased or upgraded.

### The Testing Environment is "Close Enough"

Conducting performance testing in a test environment that is similar to the production environment is a performance testing best practice for a reason. The differences between the elements can significantly affect system performance. It may not be possible to conduct performance testing in the exact production environment, but try to match:

  * Hardware components.
  * Operating system and settings.
  * Other applications used on the system.
  * Databases.![Software Development Lifecycle](https://stackify.com/wp-content/uploads/2017/04/stockfresh_7449840_software-development-cycle-infographic_sizeXS.jpg)

### What Works Now, Works Across the Board

Be careful about extrapolating results. Don't take the small set of performance testing results and assume that they will be the same when elements change. Also, it works in the opposite direction. Do not infer minimum performance and requirements based upon load testing. All assumptions should be verified through performance testing.

### One Performance Testing Scenario is Enough

Not every performance problem can be detected in one performance testing scenario. But resources do limit the amount of testing that can happen. In the middle are a series of performance tests that target the riskiest situations and have the greatest impact on performance. Also, problems can arise outside of well-planned and well-designed performance testing. Monitoring the production environment also can detect performance issues.

### Testing Each Part Equals Testing the Whole System

While it is important to isolate functions for performance testing, the individual component test results do not add up to a system-wide assessment. But it may not be feasible to test all the functionalities of a system. A complete-as-possible performance test must be designed using the resources available. But be aware of what has not been tested.

### What Works for Them, Works for Us

If a given set of users does experience complications or performance issues, do not consider that a performance test for all users. Use performance testing to make sure the platform and configurations work as expected.

### Software Developers Are Too Experienced to Need Performance Testing

Lack of experience is not the only reason behind performance issues. Mistakes are made -- even by developers who have created issue-free software in the past. Many more variables come into play -- especially when multiple concurrent users are in the system.

### A Full Load Test Tells Everything

It's tempting to just run a test at the total load to find all the performance issues. Except for that kind of test tends to reveal so many performance issues that it's hard to focus on individual solutions. Starting at a lower load and scaling up incrementally may seem like an unnecessarily slow process, but it produces easier results that are more efficient to troubleshoot.

### Test Scripts Are Actual Users

Make sure the test automations are using the software in ways that real users would. This is especially important when performance test parameters are changed.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
