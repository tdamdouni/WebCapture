# A Quick Primer on Python Concurrency

_Captured: 2017-10-30 at 20:11 from [dzone.com](https://dzone.com/articles/a-quick-primer-on-python-concurrency?edition=334817&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-30)_

[Intelligently automate your Big Data operations](https://dzone.com/go?i=255321&u=https%3A%2F%2Fpages.awscloud.com%2Fdatalakes-qubole-nov2017.html%3Fsc_channel%3Dem%26sc_campaign%3DAWS_Partner_namer_WEW_datalakes-qubole-oct2017_20171001%26sc_publisher%3Daws%26sc_country%3Dus%26sc_geo%3Dnamer%26sc_category%3Dmult%26sc_outcome%3Dawspartner%26source%3Dem_70138000000rRVQ%26trk%3Daws_ipc_solution_page) to lower your costs, make your team more productive, scale more efficiently, and lower the risk of failure. [Learn how >>](https://dzone.com/go?i=255321&u=https%3A%2F%2Fpages.awscloud.com%2Fdatalakes-qubole-nov2017.html%3Fsc_channel%3Dem%26sc_campaign%3DAWS_Partner_namer_WEW_datalakes-qubole-oct2017_20171001%26sc_publisher%3Daws%26sc_country%3Dus%26sc_geo%3Dnamer%26sc_category%3Dmult%26sc_outcome%3Dawspartner%26source%3Dem_70138000000rRVQ%26trk%3Daws_ipc_solution_page)

Python is often thought of as a single-threaded language, but there are several avenues for executing tasks concurrently.

The threading module allows us to spin up native operating system threads to execute multiple tasks concurrently. The threading API has methods for creating thread objects and then using the object to start and join on the underlying thread.
    
    
    t = threading.Thread(target=do_some_work, args=(val,)) 

The threading module also provides several synchronization and inter-thread communication mechanisms for when threads need to communicate and coordinate with each other, or for when multiple threads are mutating the same area of memory. Locks and queues are the most common of those synchronization methods but Python also provides RLocks, semaphores, conditions, events, and barrier implementations in the threading API.

However, the current implementation of Python has a global interpreter lock (GIL) to make Python easier to implement and faster to run for single threaded programs. But as a result of the GIL, which only allows one thread to run at a time, threading is not suitable for CPU-bound tasks (tasks in which most of the time is spent performing a computation instead of waiting on IO). So instead, we have the multiprocessing package. The multiprocessing package uses processes instead of threads as the actors of parallel execution. And the multiprocessing API tries to mimic the threading API as much as possible, to reduce the amount of dissonance between the two and to make switching easier.
    
    
          return hashlib.sha384(text).hexdigest()
    
    
        p = multiprocessing.Process(target= generate_hash,args=(text,))

One of the major areas where there is a difference between the threading and multiprocessing APIs is in the implementation of shared state. Threads automatically share memory with each other, but processes don't. So, special accommodations must be made to allow processes to communicate and share state. Processes can either allocate and use OS-shared memory areas or they can communicate with a server process which maintains shared data.

The `concurrent.futures` module provides a layer of abstraction over both concurrency mechanisms (threads and processes).

It was also the introduction of Futures into Python. In Python, a future represents a pending result and it also allows us to manage the execution of the computation that produces the result. Future API methods include `result()`, `cancel()`, and `add_done_callback(fn)`:

Finally, the most recent addition to the Python concurrency family is the `asyncio` module. `asyncio` brings single-threaded asynchronous programming to Python. It provides an event loop that runs specialized functions called coroutines. A coroutine has the ability to pause itself and yield control back to the event loop when it needs to wait for IO or some other long-running task. The event loop can then go on and execute other coroutines and resume the prior coroutine when an event occurs that indicates that the IO or long-running task is complete. As a result, we have multiple tasks running on the same thread and yielding to one another instead of blocking.

There are several resources that provided an in-depth look into Python concurrency, like the [Python Module of the Week](https://pymotw.com/3/threading/) blog and the Python Parallel Programming Cookbook. If you are a Pluralsight user, you can also check out my Pluralsight course, [Python Concurrency: Getting Started](https://app.pluralsight.com/library/courses/python-concurrency-getting-started).

Find the perfect platform for a scalable self-service model to manage Big Data workloads in the Cloud. [Download the free O'Reilly eBook to learn more](https://dzone.com/go?i=239230&u=http%3A%2F%2Fgo.qubole.com%2FLP---DataOps---Book-Offer.html%3Futm_campaign%3DCS-Dzone%26utm_content%3DDataOps_Book%26utm_medium%3DPartnerResource%26utm_term%3DQ317).
