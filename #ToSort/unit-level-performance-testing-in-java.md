# Unit-Level Performance Testing in Java

_Captured: 2017-05-13 at 08:55 from [dzone.com](https://dzone.com/articles/unit-level-performance-testing-in-java?edition=298091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-12)_

When it comes to performance testing, I hear a lot about having a dedicated environment, funky tools like JMeter or Apica, and complicated scenarios. These take a lot of effort to set up and maintain. Therefore, I like to first make sure that the most critical units are well-optimized without any of these tools. One way to make such promise is through unit-level performance test apps. What's great about these apps is that there is no need for any special tool; they can be ready to go within a minutes and they are proven to save a lot of time, money, and calls from angry customers.

In this article, I am going to share an example of such a test app. You can do the same in your projects.

Technology stack:

  * Netbeans IDE.
  * Java.
  * Maven.

## Testable Unit

In order to be able to run performance tests for a single unit, there is a need to have well-defined and testable units. Let's work with an example (I have cooked this one, but you will get the idea).

This example is a module for message broadcasting. There is a method that accepts pipe delimited `String` as an input. Inside the method, the module extracts parameters from the input, finds the appropriate username, and broadcasts the messages. This is an example of a unit and here is the implementation:
    
    
    package com.enterprisemath.articles.unitperformance;
    
    
    package com.enterprisemath.articles.unitperformance;
    
    
      String[] parts = message.split("\\|");
    
    
       String[] subs = part.split("=", 2);
    
    
       if (subs[0].equals("userId")) {
    
    
       } else if (subs[0].equals("timestamp")) {
    
    
        now = Dates.parse(subs[1], "yyyy/MM/dd HH:mm:ss");
    
    
       } else if (subs[0].equals("message")) {

If you want to compile this, here is a POM file with dependencies:

The core method, `processMessage`, starts on line 87. This method does following:

  1. Splits input into parts.

  2. Maps relevant parameters and finds the username.

  3. Validates that all mandatory parameters for this module are presented.

  4. Broadcasts the message.

As you can see, the module depends on `userProvider` and `broadcastService`. As the name suggests, `userProvider` exposes only _getter-_type methods. Calls to _getters _won't cause anything else other than delay. On the other hand, `broadcastService` exposes a method that would cause harm if it were called an inappropriate number of times. This is the expectation you will see in the following test case (`verifyNoMoreInteractions` is there only for `broadcastService` on line 82).
    
    
      when(userProvider.getUserName("1")).thenReturn("John Seaman");
    
    
       assertTrue(e.getMessage(), e.getMessage().contains("wrong input message, text is missing"));
    
    
      verify(broadcastService).broadcastMessage("John Seaman", Dates.createTime(2017, Month.JANUARY, 1, 12, 0, 0), "Hello world");

In the test method, you can see that there is one happy case and one case for each validation failure. An important point is to have the good unit tests _before_ doing optimizations. Ideally, no optimization should break the unit tests. If it does, then this should lead into further investigation.

That's the way how to prepare isolated unit with tests.

## Test Application and Profiler

Now, when you have a code separated to the isolated unit and well defined unit tests, you are ready to start optimizing the performance. Before writing anything, ask yourself a question: _Is this a critical part of the application?_ If answer is not, then it's better not to optimize. Examples of critical parts are:

  * Methods called hundreds of millions of times.

  * Methods that process a lot of records.

  * Methods aggregating data from third parties in (near) real-time.

If you evaluated your method as a critical part of the application, then it is time to write the test application. Typically, you can place the test application right next to the unit tests. Here is the example.
    
    
      when(userProvider.getUserName(any(String.class))).thenAnswer(new Answer < String > () {
    
    
      Date ts = Dates.createDate(2017, Month.JANUARY, 1);
    
    
      List < String > messages = new ArrayList < String > (1000000);
    
    
      for (int i = 0; i < 1000000; ++i) {
    
    
       messages.add("userId=" + usid + "|message=Hello world|timestamp=" + Dates.format(ts, "yyyy/MM/dd HH:mm:ss") +
    
    
       for (int i = 0; i < 20; ++i) {
    
    
      System.out.println("Num messages = " + messages.size());
    
    
      System.out.println("Duration = " + duration + "; referenceDuration = 14882");
    
    
      System.out.println("Duration / message = " + ((double) duration / messages.size()));

Usually, this is just small application containing four parts:

  1. Environment setup and data genaration (it is desired to exclude this from measurement).

  2. A waiting period to allow user connect profiler.

  3. Test execution.

  4. Result presentation.

As you can see I have used mockito to mock `userProvider` (line 38). And `broadcastService` (line 39) is implemented inline. Both ways allow you to create a unit performance test without even having the real implementation of dependent services. For this purpose, the difference in them is that the mock version carries additional overhead. The right choice depends on the particular use case. That's all about setup.

## Starting Profiler

When you have your application ready, you can run it and attach the profiler during the prepared waiting period (to get good results, you should attach the profiler during that time). In NetBeans, it is pretty easy. Application can be run by the right click and then _**_Run File_** _option. Profiler is attached from top menu bar as **Profile** > **Attach Profiler**, then choose _**_CPU_** _and click **_Attach_**. Finally, choose your application and click **_OK_**. For illustration, please see the images below.

![Attach Profiler - step 1](https://dzone.com/storage/temp/5233454-profiler-1.jpg)

> _Attach Profiler - step 1_

![Attach Profiler - step 2](https://dzone.com/storage/temp/5233455-profiler-2.jpg)

> _Attach Profiler - step 2_

![Image title](https://dzone.com/storage/temp/5233457-profiler-3.jpg)

## Analyzing Results

If everything is done everything correctly, then the console should look familiar to the following dump after the application finishes. See the profile attachment inside the waiting period (in the middle of the dots):

From the console output, you can see, among other things, that the whole test duration was around 15 seconds. In addition to the console output, there is a profiler result which looks similar to the following.

![Profiler result 1](https://dzone.com/storage/temp/5233480-profiler-4.jpg)

> _Profiler result 1_

It is possible to drill down within the profiler result and see how much time program spend in each method. The point of this test is to see details of the `processMessage` method. It is very clear that majority of time is taken by the `getUserName` method. In this case, it is caused by calling to the mock class. For simplicity, let's assume that it would look similar if underline implementation makes a call to the database (in such a case, SQL would need to be sent to the database and the database would need to parse it, pull data, and return the result over some protocol, which would definitelly take some time). So as the resolution, let's consider the method `getUserName` as a bottleneck to deal with.

## Bottleneck Optimization

As you probably know, the typical way to avoid expensive queries is some form of caching. Let's try the most primitive one: using `HashMap`. Here's how the optimized `processMessage` method looks:

When you run the performance test program with this adjustment, then the whole run takes around 4.4 seconds instead of the original 15 seconds (on the same machine). The profiler result looks like the following:

![Profiler result 2](https://dzone.com/storage/temp/5233590-profiler-5.jpg)

> _Profiler result 2_

Now the bottleneck becomes the function for parsing dates from the string. This would be the next step for optimization, if required. Before closing, let me add a few notes.

  * Using hash maps for caching is probably not what you want in most of real cases. 

  * Optimization introduced new branch of code which is not covered by current unit test. Good practice is to revisit unit test and get this case properly covered.

  * Optimization generally makes code more complex and less readable. Therefore focus first only on the parts of your application which are critical, use profiler to find the real bottleneck within the units and stop optimizing when performance is good enough for your case.

That's about this form of optimization.

## Summary

In this article, I have shown you one way how to do performance tuning of your application at the unit level. This type of optimization has an advantage in that that anyone can do it with only a laptop and a few basic tools and everything can be setup within a minutes. Therefore, this is the great first layer of the performance tuning, which will save you a lot of time and money during the later stages.

  * Always start with clean and unit-tested code.

  * Choose critical parts of your application and use a profiler to find the number-one bottleneck.

  * Repeat until needed and stop when performance is good enough.
