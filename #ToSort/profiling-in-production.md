# Profiling in Production

_Captured: 2018-03-16 at 13:15 from [dzone.com](https://dzone.com/articles/profiling-in-production?edition=368203&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-03-16)_

Maintain Application Performance with real-time monitoring and instrumentation for any application. [Learn More!](https://dzone.com/go?i=281422&u=https%3A%2F%2Fwww.nastel.com%2Fapplication-performance-monitoring%2F%3Futm_source%3DDZone%26utm_medium%3DPrePostRoll%26utm_campaign%3DDZone2018%2520for%2520all%2520pre%2Fpost-roll%2520text%2520ads%3A)

If you've ever had some serious issues with the performance of your Java application, you probably know how valuable thread profiling can be. But do you know which profiler you should use?

There are two basic techniques used by profilers: sampling and instrumentation.

## Sampling Profilers

A sampling profiler involves periodically asking the JVM for the current point of execution of all currently alive threads. This type of profiler carries the least amount of overhead. This is important because introducing heavy measurement into the application can change the performance characteristics significantly. Using a sampling technique, we get a snapshot of the next stack trace when the timer fires. So, the profiler looks at each thread and determines which method the thread is executing at that moment. As there are gaps between consecutive measurements, the sampling profiler achieves a trade-off between the level of accuracy obtained vs. the overhead involved in actually taking the measurement. This is illustrated in the following figure:

![](http://performantcode.com/wp-content/uploads/2018/03/sampling_profiler-300x83.png)

As you can see, the thread spent most of its time in the save method and a little bit in the read method. If the sampling happens only when the thread is in the save method (more probable, as this method dominates), the profiler will report that the thread spent 100% of its time in the save method, which is, of course, not accurate.

A rather logical way to minimize this sampling error is to reduce the time interval between sampling and increase the profiling time. However, as we discussed earlier, this solution might impact the performance characteristics of the application, so a balance is key.

## Instrumented Profilers

Instrumented profilers introduce a much larger performance overhead into the application. This method usually involves injecting bytecode into the classes for the purpose of profiling. This approach involves a higher performance impact but generates a more accurate measurement when compared to the result from the sampling profiler. Another problem that may arise as a result of the way an instrumented profiler modifies the bytecode is the following; as you may know, the [JIT compiler inlines small methods](http://performantcode.com/compiler/jit-inlining/). Because the instrumentation is introduced by the profiler, some small methods might not be eligible to be inlined anymore. This can have a serious impact on application performance. If you decide to use instrumented profilers, make sure that you instrument only a small section of the code.

## Production Profilers

Profiling in a development environment is easy. However, it might not be enough. When dealing with production data, we are exposed to a different scale and thus, we might observe different bottlenecks in our application. That's why profiling in production is so important. As discussed earlier, both sampling and instrumented profilers have their pros and cons. If you want to profile in a production environment, a low overhead sampling profiler seems to be a better choice. There are many sampling profilers available such as async-profiler, JProfiler, YourKit, VisualVM Profiler, and [FusionReactor's Production Code Profiler](https://www.fusion-reactor.com/production-java-profiler/). The really cool thing about FusionReactor's profiler is that it can be configured in a way that it will automatically profile your application if it detects a long-running request or thread. What is a long-running request? It's up to you to define, but three seconds is the default value. If you monitor some sort of latency-sensitive application, then you might want to decrease this value. Similarly, if your application performs some time-consuming computations, then most probably you don't want to be notified all the time and increasing [Minimum Transaction Time ](https://docs.fusion-reactor.com/display/FR70/Profiler+Settings#ProfilerSettings-MinimumTransactionTime) will be necessary.

It's not always easy to pinpoint a performance issue in a running application, but profilers are usually a good place to start.

Collect, analyze, and visualize performance data from mobile to mainframe with AutoPilot APM. [Get a Demo!](https://dzone.com/go?i=281423&u=https%3A%2F%2Fwww.nastel.com%2Fapplication-performance-monitoring%2F%3Futm_source%3DDZone%26utm_medium%3DPrePostRoll%26utm_campaign%3DDZone2018%2520for%2520all%2520pre%2Fpost-roll%2520text%2520ads%3A)
