# How we break things at Twitter: failure testing

_Captured: 2017-08-08 at 19:00 from [blog.twitter.com](https://blog.twitter.com/engineering/en_us/a/2015/how-we-break-things-at-twitter-failure-testing.html)_

When you run an infrastructure at Twitter scale, hardware and network failures become unavoidable. Each of these failures has the potential to negatively impact the user experience, so it's important that we design our systems to be as resilient to failure as possible.

To test how our services react to unexpected failures, we created a framework that can inject controlled failure conditions into the Twitter infrastructure. This allows us to discover vulnerabilities so that we're better prepared to handle a site-wide incident. By causing failures in our own system, we're able to build more resilient services.

**Framework**

Our framework consists of a Python library and a command-line executable which is designed to directly introduce failure conditions into production infrastructure, monitor site-wide health metrics, and notify systems with status updates during the testing procedure. It provides a flexible, YAML-based configuration syntax and is trivially extensible with additional functionality, based around a modular design.

The framework consists of three module types:

  * **Mischief modules** introduce and reverse failure conditions within production services and infrastructure.
  * **Monitors modules** are designed to check [sources of health metrics](https://blog.twitter.com/2013/observability-at-twitter) for Twitter services, looking for states that may lead to a site-wide incident. If at least one of these states is detected, the framework will immediately reverse the failure conditions which have been introduced.
  * **Notifiers modules** are designed to interface with systems such as HipChat and JIRA to provide live status updates during the execution of a failure test.

Targets for failure testing within Twitter's infrastructure are selected by querying Twitter's asset inventory database, which is the source of information for all data center hardware and associated attributes. The framework combines these queries, allowing tests to be precisely targeted against machines supporting a single Twitter service (if running on our internal cloud) or machine role.

At the moment, the framework supports the introduction of the following failure conditions:

  * Power loss via issuing commands to IPMI controllers and PDUs
  * Network loss via pushing new switch configurations which includes switch port failure, partial packet loss, denial of all IP traffic, all traffic to one or more TCP/UDP ports, and more

To demonstrate how an engineer might use the framework to test a failure condition, here's an example of a configuration which will introduce a power loss for 30 minutes across all Hadoop DataNodes in rack abc, monitor health metrics during the test's execution, and send status updates to a chat room:
    
    
    failure_test:
      name: Power loss within rack abc in datacenter abcd
      duration_mins: 30
    
      mischief:
        - power_loss:
            datacenter: abcd
            selectors:
              - group:
                  type: role
                  name: hadoop.datanode
              - group:
                  type: rack
                  name: abc
    
      notifiers:
        - chat:
            rooms:
              - Failure Testing
    
      monitors:
        - observability:
            datacenter: abcd
            queries: !snippet

Upon passing this configuration to the framework's command-line tool, it will gather all information necessary to introduce the failure conditions, such as the target machine hostnames and the addresses of their IPMI BMC interfaces. If this mischief preparation step succeeds, the framework will ensure that all systems under test are healthy via checking the configured monitors. It will then attempt to introduce the requested failure conditions. If these conditions are introduced successfully, the framework will pause for the configured test length, checking the configured monitors on a minute-by-minute basis to ensure that all remain in a healthy state.

If any monitor detects an unhealthy infrastructure condition, the framework will consider the failure test to be unsuccessful. Otherwise, if monitors have reported healthy conditions throughout the test's duration, the framework will consider the test to be successful. In both cases, the framework will then immediately reverse all induced failure conditions, terminating the test.

A visualization of the testing process:

![How we break things at Twitter: failure testing](https://blog.twitter.com/content/dam/blog-twitter/archive/how_we_break_thingsattwitterfailuretesting95.thumb.1280.1280.png)

**Challenges**

Introducing a failure condition that targets a specific service requires careful design and planning due to the heterogeneous dynamic infrastructure we run at Twitter. Services hosted in Apache Aurora are different from those that run directly on hardware as they are dynamically scheduled.

To determine the root cause of unexpected service behavior, we need to capture the full testing environment, which can include rack profiles, service types, service diversity stats, traffic volume, and more. In some cases, the anomaly we detect is simply a side effect of upstream or downstream issues or a service's recovery behavior.

**Usage and lessons learned**

This framework has driven all failure testing at Twitter over the past six months and has helped us discover numerous vulnerabilities in our stack. In addition, it's given us confidence in the failure resiliency of several of our primary systems, such as [Apache Mesos](http://mesos.apache.org) and [Apache Aurora](http://aurora.apache.org), where we have tested large-scale failures which resulted in no user-facing impact.

An example of a common failure condition seen in our infrastructure is when a Top of Rack (TOR) switch goes bad. When this situation occurs, services running within this rack will experience either a total network loss or a partial packet loss. We learned that our services handle the total network loss case well whereas a partial packet loss will almost always cause some internal impact. We additionally found that the severity of this impact varies based on both the rack's profile and what services are running on Mesos slaves in that rack.

The framework is able to identify how Twitter services respond to a wide variety of common hardware failure scenarios, providing site reliability engineers with substantial practical data. Much of this data surrounds how inter-service RPCs, mediated by the powerful [Finagle](http://twitter.github.io/finagle/) library, behave in the face of failure conditions.

Finagle imbues all inter-service RPCs with logic to ensure that each is facilitated as successfully as possible; however, to take full advantage of this logic, downstream service clients need to be properly tuned with correct request timeout and retry values. Using data precipitated by the framework failure testing, our engineers can provide tuning values and graceful degradation logic that can better maintain SLAs and prevent user-facing incidents.

**Future work**

Of course, we'll continue to test our infrastructure's ability to withstand random failures. This framework has been used to drive exploratory failure testing to help us find and push the limits of Twitter infrastructure. As the scope of our failure testing program increases over the next few months, the framework will run continuously during work hours. By doing so, this framework will help us ensure that our resiliency to hardware failure conditions does not regress from scenarios where it has been repeatedly demonstrated. In addition, we are investigating the injection of failure conditions at the layer of our extensible RPC system, [Finagle](https://twitter.github.io/finagle/).

Through injecting controlled failure conditions into Twitter infrastructure, we can ensure that our systems will better tolerate unintended failures in production. This allows us to write services that better endure failures and gracefully degrade when needed. And ultimately by running these tests, we're able to locate and address these vulnerabilities in our infrastructure.

If failure and reliability testing sounds like an interesting challenge, we could use your help -- [join the flock](https://about.twitter.com/careers)!

_Special thanks to [Steven Salevan](https://twitter.com/stevesalevan) for his contributions to this framework and blog post._
