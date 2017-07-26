# Locking Files in Java

_Captured: 2017-05-21 at 12:40 from [dzone.com](https://dzone.com/articles/locking-files-in-java?edition=299092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-20)_

[Bitbucket](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

In most `I/O`-based applications, we deal with concurrency, where several processes do reads/writes to a file. While reading/writing to a file, we need to ensure that it is not being used by other processes to ensure data integrity. The Java `NIO API` provides file locking at the operating system level (hence it is visible to other processes) so that other processes cannot access the file. The `NIO API` allows the obtaining of shared or exclusive locks on either whole file or part of the file.

In Java, a file lock can be obtained using `FileChannel`, which provides two methods -- `lock()` and `tryLock()` -- for this purpose.

The `lock()` method acquires an exclusive lock on entire file, whereas the `lock(long position, long size, boolean shared)` method can be used to acquire a lock on the given region of a ile. These two methods will block until the lock is obtained. Meanwhile, the methods `tryLock()` and `tryLock(long position, long size, boolean shared)` do the same, but they don't block and they return immediately.

These methods return a `FileLock` object, which can be used further to control the lock and, at the end, to release a lock. In the case of the `tryLock()` method, if it fails to acquire a lock due to overlapping (lock already held by other process), then it returns null; if it fails due to some other reason, then an appropriate exception is thrown.

Now let us look at an example:
    
    
    package com.test.nio.filelock;
    
    
    import org.apache.commons.logging.Log;
    
    
        private static final Log LOG = LogFactory.getLog(FileLockTest.class);
    
    
                    buffer = ByteBuffer.wrap(data.getBytes());
    
    
                    buffer.put(data.toString().getBytes());
    
    
                LOG.error("Exception occured while trying to get a lock on File... " + ex.getMessage());

Don't forget to lock the file when your application has several processes that can read/write. Happy learning!

[Bitbucket is the Git solution](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

Opinions expressed by DZone contributors are their own.
