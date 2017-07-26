# How to Crash the Java Virtual Machine With a Race Condition

_Captured: 2017-03-16 at 21:30 from [dzone.com](https://dzone.com/articles/how-to-crash-the-java-virtual-machine-with-a-race?edition=283884&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-16)_

[Bitbucket](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

This is a how-to guide for crashing the Java virtual machine. It gives you an introduction to race conditions and shows you what errors can happen if your code contains such bugs.

# Create a Race Condition

Let us start with the following [method](https://github.com/vmlens/stress-test/blob/master/src/main/java/com/vmlens/stressTest/examples/dataRace/DataRaceTest.java):
    
    
             ts[0] = Object.class; instance = ts;  

If this method is executed by multiple threads it leads to a race condition. More specifically, it leads to a data race. Data races are defined in the [Java memory model](https://docs.oracle.com/javase/specs/jls/se7/html/jls-17.html#jls-17.4) as access to a shared field without correct synchronization.

According to the Java memory model, data races lead to platform dependent undefined behavior. Without correct synchronization, very strange, confusing, and counterintuitive behaviors are possible.

If the code is executed in the given order, everything is O.K. But if some component reorders the statements, the array might not be completely initialized. One such component is the cache system of the CPU.

Intel Processors, for example, have a cache system with strong memory guarantees. The cache system makes sure that the values written by the cores are almost always seen in the same order as they have been written by the other cores. But [ARM](https://en.wikipedia.org/wiki/ARM_architecture)-compatible processors like in smartphones or the Raspberry Pi do not have this guarantee.

## Create a Nullpointer Exception

To see what is happening, I'll execute the method multiple times by multiple threads. To do this, I use a tool to reproduce race conditions called [stress test](https://github.com/vmlens/stress-test). I run it with the following command line options:

Using the following [test setup class](https://github.com/vmlens/stress-test/blob/master/src/main/java/com/vmlens/stressTest/examples/dataRace/DataRaceTestSetup.java):

This runs the DataRaceTest method for 5 iterations. Each iteration consists of 16,000 tests run by 16 threads.

If I run this on my Intel i5 workstation, I could not create an exception. If I run this on my Raspberry Pi, I see the following Nullpointer Exception for every 2000 tests:
    
    
      at com.vmlens.stressTest.examples.dataRace.DataRaceTest.run(DataRaceTest.java:78) 
    
    
      at com.vmlens.stressTest.internal.TestCall.call(TestCall.java:36) 
    
    
      at com.vmlens.stressTest.internal.TestCall.call(TestCall.java:7) 
    
    
      at com.vmlens.stressTest.internal.WorkerThread.run(WorkerThread.java:22)

## Crash the Java Virtual Machine

Now let us add some native calls. Let us clone the [array](https://github.com/vmlens/stress-test/blob/master/src/main/java/com/vmlens/stressTest/examples/clone/CloneTest.java):
    
    
         ts[0] = Object.class; instance = ts; 

This time I'll run the test until I see at least one error. This is done by using the -e option:
    
    
    java -cp stress-test-0.0.1-SNAPSHOT-jar-with-dependencies.jar 
    
    
      com.vmlens.StressTest -e 1 -w 16

If I run this code on a Raspberry Pi, I'll see the Java virtual machine crash after some time. It takes between half an hour and a day:
    
    
    # A fatal error has been detected by the Java Runtime Environment: 
    
    
    # SIGSEGV (0xb) at pc=0x741ab340, pid=26364, tid=1682633824 
    
    
    # JRE version: Java(TM) SE Runtime Environment (8.0_65-b17) (build 1.8.0_65-b17) 
    
    
    # Java VM: Java HotSpot(TM) Client VM (25.65-b01 mixed mode linux-arm ) 
    
    
    # J 38 C1 com.vmlens.stressTest.internal.TestSetupCall.call()Lcom/vmlens/stressTest/internal/Result; (45 bytes) @ 0x741ab340 [0x741ab250+0xf0]

## Conclusion

Data races are hard to reproduce. You need different types of hardware, and even then it takes time until you see an error occur.

That is the reason I developed [vmlens](http://vmlens.com), a tool to detect data races in the execution trace of an application.

[Bitbucket is the Git solution](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)
