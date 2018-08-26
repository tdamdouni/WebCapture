# 6 Common Performance Testing Mistakes

_Captured: 2018-07-06 at 19:28 from [dzone.com](https://dzone.com/articles/6-common-performance-testing-mistakes?edition=385206&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-07-06)_

Container Monitoring and Management eBook: [Read about the new realities of containerization.](https://dzone.com/go?i=291440&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fcontainer-monitoring-and-management.html%3Fcid%3DNA-DSP-APM-AEJ-000195-00001663-000000492%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_eb1-container-monitoring-mgmt-articlepreroll%26mrm%3D)

As a performance testing consultant for the last 15 years, you could say that it's second nature for me to look for performance patterns. One of the patterns I have observed over my career is that, regardless of the project size, company, or the technology being used, the same types of performance testing mistakes get made over, and over, and over.

This is fundamentally unsurprising, as human nature is the same regardless of the company, and every project and business environment has deadlines. Sometimes those deadlines mean testing simply _has to get done_, making it easy to cut corners to get the results "over the line." Unfortunately, however, those short-cuts can lead to costly performance testing mistakes and oversights.

With a bit of self-awareness, however, not to mention helpful accompanying tools like Flood, you can often mitigate these mistakes quite easily.

## **1\. Inadequate User Think Time in Scripts**

Hitting your application with hundreds or thousands of requests per second without any think time should only be used in rare cases where you need to simulate this type of behavior (perhaps a Denial of Service attack?). I'd like to think that 99% of people are not testing for this scenario all the time, and are just trying to verify that their site can handle a particular target load, so your user think time is very important.

I've seen many people run tests without any think time, with thousands of users, using 1 load injection node, and then proceed to ask: "Why are my response times really slow? When I manually visit the site using my browser, it seems to be responding just fine?"

The cause of this is almost always due to the sheer volume of requests that the load injection node is tasked with, which subsequently runs into maxing out machine resources and triggering local exceptions fairly quickly.

The way to address this is to simply add some sort of think/wait time in between your virtual user's steps - which will effectively slow the user down to a more realistic pace. A real-world user would never make back to back page requests within 1 second. Think time allows you to add a human pause, mimicking a real person who would wait a few seconds before further interacting with the site.

Using a tool like JMeter, I generally like to use something like a Gaussian Random Timer - which allows your users to interact in a random fashion just as they would in a real-world scenario. (A Gaussian Random Timer is used by default within all tests built in Flood's Test Builder tool for this very purpose.)

## **2\. Using an Inaccurate Workload Model**

A workload model is essentially the detailed plan that you should be writing your scripts against. This workload model should outline your business processes, the steps involved, number of users, number of transactions per user, and calculated pacing for each user.

As you can probably see, having an accurate workload model is critical to the overall success of your testing. Often this is easier said than done - there have been many projects where business requirements simply don't exist because they just weren't considered beyond, "the system should be fast".

It's almost become part of the job description of a performance tester to assist in nailing down these requirements - often sitting with the analyst or business representative involved to flesh these out in order to have something accurate to test against.

It is also very common that non-functional requirements tend to have lofty and ambitious target transaction and response time figures, often proposed by an overly enthusiastic business team or representative. This is typically related to the buzz created for a new application and target functionality that the business is eager to release.

For existing applications: it's always worthwhile to have access to production statistics, which will show a wealth of information, such as:

  1. What are the most common/popular transactions?
  2. How many of each transaction happens on a typical business day?
  3. How many of each transaction happens on a peak day?
  4. What are the general times or periods that these transactions tend to occur?
  5. What are the transactions that have a high business cost if they were to fail under load?

From these criteria, you can assemble a picture of the workload model you need to simulate.

For new applications: the general rule is to work as much as possible with the business representatives to ascertain realistic and agreed figures that are well defined, simple, and testable.

After the first testing cycle and once the application is released: on-going monitoring of usage in the production environment will help feedback for the next round of testing where the workload model can be tuned further.

## **3\. Setting Up Inadequate Infrastructure Monitoring**

Load generation isn't the only important part of a performance testing scenario. The execution results gained from a scenario such as throughput, transaction response times, and error information isn't overly helpful unless you can see how your target infrastructure is actually coping with the scenario.

It's a common problem - I have heard many testers ask why their response times are taking minutes instead of seconds. The problem can lie either in the load generation or the target application infrastructure.

So how do you solve this problem? The ideal solution is to have custom monitoring dashboards (which are available upon request from some load testing platforms, like Flood IO) for all of your on-demand load injection infrastructure. This enables you to view system resource utilization while running your tests, ensuring that no bottlenecks are present on the load generation side.

On the target application side, there are quite a few tools that can be implemented to help diagnose bottlenecks or sluggish performance during a load test.

There are actually at least 100+ application monitoring services available[1] right now - all with differing price points and features. I have used a number of the more popular services such as New Relic, AppDynamics, and Splunk, but these can get quite expensive for a full stack monitoring option.

There are also a few open-source, free alternatives such as Nagios and InspectIT. They are not as polished but with a little know-how and time spent setting these up, it can be worthwhile and very cost effective.

## **4\. Use of Hardcoded Data in Every Request**

Another common pitfall is when customers test their websites with the same exact request repeatedly. The goal of load testing is to be as realistic as possible - so the usage of the same data in your HTTP request for every one of your users is not how this scenario would play out in reality. Often smarter applications and existing database technology will recognize these exact same requests and start automatically caching them, which will have the effect of the overall system appearing faster than it actually is. This leads to an invalid performance test.

Let's take the simple act of registering a new user for a typical online shopping website. Most (if not all of these sites) will not let the same user be registered more than once without some unique information being specified.

Let's look at an example JSON payload that can be used within a JMeter request for adding a new customer:

For this request, you would not be able to keep submitting this into a shopping website as there would most likely be some verification, particularly on the mobile and email fields.

So let's make these 2 fields unique so we can run this request successfully each time.

With JMeter, we can easily use some built-in random number generators to ensure that fields like phone numbers and email addresses can be unique.

Here we have made two simple code changes:

  1. We replaced the mobile field with a JMeter Random function that will generate a ten-digit random number for the mobile phone number field.

  2. We replaced the email filed with a JMeter RandomString function that will generate a ten character email username along with '@domain.ext'

So, when we run this payload within an HTTP request in a load test, every single request will have a different mobile number and email address.

Some further notes about doing this:

  * We can easily extend this so that we can make the other fields unique, as well.
  * It's always important to use an adequate range of random numbers -- using a ten-digit random number range will allow you to run with thousands of users and be extremely unlikely to generate the same unique number more than once. This also goes for using a large set of possible characters to generate a random string from for the email field.

This is a great and simple example of using dynamic data for all of your requests. If you need something more substantial or perhaps you'd like to use some pre-prepared data - you are able to use CSV files with each column being available as a parameter that can be used to dynamically enter any data into a request.

More information on the CSV Data Set Config add-in for JMeter is available [here](http://jmeter.apache.org/usermanual/component_reference.html#CSV_Data_Set_Config).

## **5\. Ignoring System or Script Errors Even Though Response Times and Throughput May Look Fine**

When running a load test - there are several things to keep an eye on to ensure you are running a valid test. It is quite easy to gloss over some details that may have a huge impact on your test's validity. Take the following example that can be seen quite often:

A load test runs with a target number of users and the user observes response times and error rates to be in acceptable ranges. However, expected throughput is lower than expected. How can this be when Flood is reporting very little transaction related errors?

![](https://flood.io/blog/content/images/2018/02/part5-1.png)

System-related errors that may be encountered are not reported on the transaction pass/fail counts so this is the reason why everything looks OK to the untrained eye. The telltale sign is the number of transactions per minute or RPM value is lower than anticipated.

![](https://flood.io/blog/content/images/2018/02/part5-2.png)

Delving into the Flood runtime Logs will reveal the issue on the scripting side.

From the logs, we can see a number of script related issues that are causing the script replay to exit out of a substantial amount of iterations due to script errors. This will significantly impact your target throughput and is the primary source for observed throughput to be lower than expected. These will need to be fixed.

So once we have a fairly successful looking test with transaction response times, error rates, and throughput rates all in the expected zone -- are we in the clear?

Well, not just yet -- you see, there is an almost always overlooked area that can still impact your load tests. Verification of actual system or application logs during the test.

This can be easily monitored if using a purpose-built APM (Application Performance Monitoring) tool such as New Relic or Appdynamics but a lot of the time you will probably need to do this manually.

Exceptions can be caused by a number of different factors - but the careful analysis of these exceptions is needed in order to understand if they were caused by your load test scenario and what impacts they have to your system's performance and stability.

Exceptions often carry an enormous performance overhead due to exception handling routines as well as any related logging to disk or memory operations. This might not be much of an issue with a single transaction but multiply this over 1,000 concurrent users and it can severely impact your system's responsiveness.

We don't aim to totally eradicate exceptions as nothing is ever error-free but minimizing when they occur especially during high load scenarios is a great approach to take. Many people are surprised at how many exceptions are generated by their system when shown during a load test and it certainly warrants further investigation.[2]

## **6\. Overloading Load Generators**

The last of our 6 common performance testing mistakes is the overloading of load generators due to one or more of the following:

  * Too many concurrent users on a single load injection node.

  * The target site is very image-heavy or CSS-heavy, which impacts the number of concurrent users you can fit on a load injection node.

  * Load injection node hardware limitations.

At Flood, we have base-lined our load generation nodes to a point where we know we can successfully support up to 1,000 concurrent users per load node for JMeter and Gatling tests. This is a general rule of thumb and your mileage may vary depending on the target site. A site heavy in CSS and lots of images will cause a larger footprint in resource utilization than a very simple text-only site or API calls.

This has an effect on the number of threads/users we can support per node.

So how do we know what the actual number of supported threads/users to use comfortable per node?

We generally recommend running initial tests with a low amount of users (1-100) as a scaling test. You can either work with one of the Flood customer success engineers to help monitor load injection nodes or we can provide a node resource dashboard which shows CPU & Memory metrics that you can use for node capacity planning.

To be able to pinpoint if you are overloading a load injector the following telltale signs would be present:

![](https://flood.io/blog/content/images/2018/02/part6-1-1.png)

### CPU and Network Utilization

CPU usage in the 80%+ region for a sustained period is a telltale sign that the load injection node is being saturated. The network Rx throughput figure is also an issue in this case as each of load injection nodes have a limit of approximately 50 Mbps so anything above this will mean network saturation.

### Out of Memory Exceptions

Memory Usage on a load injection node can easily be observed in the Memory usage stats graph and you should also see 'UncaughtExceptionjava.lang.OutOfMemoryError: Java heap space.' error messages in the JMeter execution logs.

### Error Logging

Errors are often represented as I/O Exceptions reported in the Test Execution logs similar to the following:

Take the Chaos Out of Container Monitoring. [View the webcast on-demand!](https://dzone.com/go?i=291441&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcompany%2Fevents%2Fwebcasts%2Fapplication-performance-monitoring-and-management.html%3Fcommid%3D286663%26cid%3DNA-DSP-APM-AEJ-000195-00001663-000000493%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_webcast1-apm-taming-chaos-articlepostroll%26mrm%3D)
