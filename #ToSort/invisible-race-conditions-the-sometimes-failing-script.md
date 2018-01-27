# Invisible Race Conditions: The Sometimes Failing Script

_Captured: 2018-01-05 at 14:42 from [dzone.com](https://dzone.com/articles/invisible-race-conditions-the-sometimes-failing-sc?edition=347160&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-01-05)_

You probably know that Chrome is a memory hog. I came up with the following extremely brute force manner to deal with it:

This works quite nicely in 99% of the cases, but sometimes, this fails. Can you see why?

I'll give you a hint, the `EmptyWorkingSet()` returns a failure and an invalid handle error. Why is that?

Well, the problem is a bit tricky. We first execute the Get-Process cmdlet, and extract the handles from the results. That is great, but we don't keep track of the Process instances that we get from Get-Process, which means that they are garbage.

That means that the GC might clean them, but they require finalization, so at some point, the finalizer will claim them, closing their handles, which means that the `EmptyWorkingSet` will fail sporadically in a very non obvious way. The "fix", by the way, is to iterate of the processes directly, not on their handles, because that keeps the process instance live for the duration (and thus its handle).
