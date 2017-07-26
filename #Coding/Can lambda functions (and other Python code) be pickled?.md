# Can lambda functions (and other Python code) be pickled?

_Captured: 2016-02-28 at 12:09 from [www.quora.com](https://www.quora.com/Can-lambda-functions-and-other-Python-code-be-pickled)_

## Serializing arbitrary Python code using the cloud package

You can in fact pickle lambdas, functions, classes, and other code, as well as any pure-python dependencies. The _cloud_ package does this, itself being only pure python. It uses a combination of pickle, marshal, and introspection to discover and slurp up enough context to get the job done, and then it packages it into an ordinary python pickle. To use it, just 'pip install cloud' and then:
    
          1. import cloud, pickle
      2. def foo(x):
      3. bar =lambda z: foo(z)+1
      4. blob = cloud.serialization.cloudpickle.dumps(bar)
      5. func = pickle.loads(blob)
      6. print func(3)# displays "10"

In other words, call .cloudpickle.dump() or .cloudpickle.dumps() the same way you'd use pickle.*, then later use the native pickle.load() or pickle.loads() to thaw.

## Why this is amazing from a Computer Science standpoint

It's all about mobile code. In this case, "mobility" means both physical and temporal. Physical mobility means you can migrate running Python code between machines -- just pickle it up, send it over the wire, unpickle and resume. Temporal mobility means you can pickle running code, save it to disk, exit, even reboot, then later unpickle and resume.

Being able to do these things allows for HPCC uses such as checkpoint/resume of long-running processes, or business uses such as having workflow of a single production item represented by a single long-running process, said process lasting for the life of a single serial number. Think electronic travelers in a manufacturing plant, for instance, or executable CRM records with customized algorithms per-customer. In all of these cases, the process runtime can easily exceed the uptime of any parent host.

Each of these pickled processes can act as a very lightweight "virtual machine", much lighter than hypervisor-based VMs like Xen or KVM, while still supporting checkpointing and live migration. You could have millions of unique Python processes "running" simultaneously on one box, possibly for years, with most of them checkpointed to disk and consuming no CPU or RAM at any given time. They can also be scaled to more boxes by migrating one process at a time, instead of having to go though the all-or-nothing proposition of migrating an entire database or application to a new server.

One of the common complaints of mobile code is version control -- once launched, the code for a process can't be upgraded. In the workflow case above, that could be an advantage -- you might not want in-process workflows to be upgraded, depending on your change control procedures. But if you did want in-process upgrades, you can do that with Python anyway, since it's a dynamic language. (I would want to bring order to the chaos of "monkey patching" though, probably by using some of the same algorithms used for automated administration of entire hosts -- for a related Quora question, see [Distributed Systems: How and when is state machine replication useful in practice?](https://www.quora.com/Distributed-Systems-How-and-when-is-state-machine-replication-useful-in-practice))

## Background behind the cloud package

Picloud released the 'cloud' python package under the LGPL, and other open-source projects are already using it for pickling code (google for
    
    
    cloudpickle.py

to see a few). The [PiCloud Documentation](http://docs.picloud.com/) gives you an idea how powerful this code is, and why they had a good incentive to put the effort into finally making general-purpose code pickling work -- their whole business is built around it.

Picloud's idea is that if you have a cpu intensive function and want to run it on Amazon's EC2 grid, you just replace:
    
    
    cpu_intensive_function(some, args)

with:
    
    
    cloud.call(cpu_intensive_function, some, args)

The cloud module pickles up any dependent code, ships it to EC2, runs it, and returns the results to you when you call cloud.result(). Picloud bills you in millisecond increments for EC2 CPU usage, it's cheap as heck, and I use it all the time for monte carlo simulations and financial time series analysis, when I need hundreds of CPU cores for just a few seconds each. I can't say enough good things about it and I don't even work there.
