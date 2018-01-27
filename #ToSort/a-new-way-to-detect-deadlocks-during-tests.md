# A New Way to Detect Deadlocks During Tests

_Captured: 2017-10-27 at 17:12 from [dzone.com](https://dzone.com/articles/a-new-way-to-detect-deadlocks-during-tests?edition=334741&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202017-10-27)_

In the following article, I want to show you a new way to detect deadlocks during tests. A deadlock happens when two threads are trying to acquire a lock held by the other thread. To detect a deadlock, you need to reach the exact time point when both threads are waiting for the other lock. Let us look at an example:

The ConcurrentTestRunner runs the JUnit test methods by 4 threads in parallel. The test succeeds at least almost all the time.

One way to see the deadlock hidden in this test is to execute the test by more threads multiple times by a machine with many cores. The other way is to trace the test execution and to analyze the lock order afterward.

We can do this by adding the [vmlens](http://vmlens.com) agent to the VM arguments of our test. After analyzing the test run vmlens reports the following deadlock:
    
    
    - deadlock: Monitor@java.util.concurrent.ConcurrentHashMap.putVal()<->Monitor@java.util.concurrent.ConcurrentHashMap.putVal()
    
    
          - java.util.concurrent.ConcurrentHashMap.putVal <<Monitor@java.util.concurrent.ConcurrentHashMap.putVal()>>
    
    
          - com.anarsoft.vmlens.concurrent.example.TestConcurrentHashMapCompute$2.apply
    
    
          - com.anarsoft.vmlens.concurrent.example.TestConcurrentHashMapCompute$2.apply
    
    
          - java.util.concurrent.ConcurrentHashMap.compute <<Monitor@java.util.concurrent.ConcurrentHashMap.putVal()>>
    
    
          - com.anarsoft.vmlens.concurrent.example.TestConcurrentHashMapCompute.update21
    
    
          - java.util.concurrent.ConcurrentHashMap.putVal <<Monitor@java.util.concurrent.ConcurrentHashMap.putVal()>>
    
    
          - com.anarsoft.vmlens.concurrent.example.TestConcurrentHashMapCompute$1.apply
    
    
          - com.anarsoft.vmlens.concurrent.example.TestConcurrentHashMapCompute$1.apply
    
    
          - java.util.concurrent.ConcurrentHashMap.compute <<Monitor@java.util.concurrent.ConcurrentHashMap.putVal()>>
    
    
          - com.anarsoft.vmlens.concurrent.example.TestConcurrentHashMapCompute.update12

Here is the putVal method. The synchronized statement leading to the deadlock is in line 18:
    
    
    final V putVal(K key, V value, boolean onlyIfAbsent) {
    
    
          if (key == null || value == null) throw new NullPointerException();
    
    
          int hash = spread(key.hashCode());
    
    
          for (Node<K,V>[] tab = table;;) {
    
    
              Node<K,V> f; int n, i, fh;
    
    
              if (tab == null || (n = tab.length) == 0)
    
    
              else if ((f = tabAt(tab, i = (n - 1) & hash)) == null) {
    
    
                               new Node<K,V>(hash, key, value, null)))
    
    
              else if ((fh = f.hash) == MOVED)

and the compute method. The synchronized statement leading to the deadlock is in line 19:
    
    
                     BiFunction<? super K, ? super V, ? extends V> remappingFunction) {
    
    
        if (key == null || remappingFunction == null)
    
    
        for (Node<K,V>[] tab = table;;) {
    
    
            Node<K,V> f; int n, i, fh;
    
    
            if (tab == null || (n = tab.length) == 0)
    
    
            else if ((f = tabAt(tab, i = (n - 1) & h)) == null) {
    
    
            else if ((fh = f.hash) == MOVED)
