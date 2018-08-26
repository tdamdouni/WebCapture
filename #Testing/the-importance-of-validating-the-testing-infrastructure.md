# The Importance of Validating the Testing Infrastructure

_Captured: 2018-04-20 at 19:47 from [dzone.com](https://dzone.com/articles/the-importance-of-validating-the-testing-infrastru?edition=374230&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-04-20)_

###  Your testing infrastructure is only good if it works as you expect it to. Let's take a look at why validating it before you begin actual testing is important. 

xMatters delivers integration-driven collaboration that relays data between systems, while engaging the right people to proactively resolve issues. Read the [Monitoring in a Connected Enterprise whitepaper](https://dzone.com/go?i=283436&u=https%3A%2F%2Fwww.xmatters.com%2Fresources%2Freports%2Fmonitoring-connected-enterprise%3Futm_campaign%3D70138000001C2pDAAS%26utm_source%3Ddzon%26utm_medium%3Dweb%26utm_content%3D3-steps-to-monitoring-in-a-connected-enterprise-wp) and learn about 3 tools for resolving incidents quickly.

## A Lesson to Learn the Easy Way

I'm a firm believer in learning from one's mistakes. When you make a mistake, and you are truly invested in what you do and strive to do it well, you naturally will want to analyze the mistake so you can learn how to avoid it in the future.

In this post, I want to share one such lesson. In more than one client project, the information we had about the infrastructure of the system was incorrect (or didn't paint the entire picture), so, when analyzing the results of our performance tests, there were things that just didn't measure up. There were some behaviors that we simply couldn't explain. In these cases, after a lot of research, we came to find that there was an extra component we were unaware of, or that the network path through which we were accessing a certain component was not as direct as we thought.

The two challenges were quite different, but the solution is one in the same: **validate the testing infrastructure.**

Lesson learned.

Sometimes when given something to test, some key details may be forgotten--and that's okay. That's why, as testers, it's on us to validate the test infrastructure before diving in. Fortunately, there are several ways to do so.

### Ways to Validate Your Testing Architecture

#### Validate Components and Their Versions

Access each node by checking the IPs of the components and that they have the indicated services. Validate the operating systems, and verify their versions, as well as the versions of the components (for example, Java, Apache, etc).

#### Validate Initial Configurations

In a performance test, looking for optimizations, different configurations are usually tested, trying to improve the results, comparing the performance of different options. So, to validate that what is documented in the results is accurate, it is necessary to review the initial configurations (at least the most relevant ones). For example, the size of each connection pool (in the database or the web server), the maximum and minimum allocated memory (in the case of JVM), etc.

#### Validate Connections and Network Routes

To do so, from each node, make a [traceroute](https://en.wikipedia.org/wiki/Traceroute) to the nodes with which they connect, to validate the network jumps. You should also do this from the load generating machines.

#### Validate Ports

I mention this in particular because it was what made us realize one of the problems we ran into. If you are accessing the web server to port 80 where there is a [Tomcat](https://tomcat.apache.org/), you should check that the Tomcat is configured in the port 80. What happened to us is that it was in the port 8080, and this was because they had placed the Tomcat _behind_ an Apache. This is a common practice*, but we weren't made aware because we were later told, _"the Apache is lightweight and does not add overhead."_ (Seriously!?) That is usually true, but it doesn't mean that it won't generate contention if something was configured wrong, as in this case. The number of connections it accepted was not enough for the load, so it would queue the requests. We were trying to understand why JMeter gave us certain results on the one hand, while in the Tomcat access log the times recorded in the time-taken were much smaller.

_*Combining Tomcat and Apache has certain advantages. It should allow for greater concurrency management and resource optimization through compression and caching._

## Closing

Clearly it involved some extra work to try to understand what was happening. Had we validated the infrastructure at the outset, we would not have had these problems. For the future, in order to provide a better service and not depend on the knowledge or transparency of the infrastructure that exists, it's best to carry out certain validations before starting to analyze a system's behavior.

#### **The Take-home Message:**

Don't skip the part where you validate the testing infrastructure, since at the end of the day, we're seeking information to reduce risk.

Is there anything else that you think is important to add to this list?

[3 Steps to Monitoring in a Connected Enterprise](https://dzone.com/go?i=283437&u=https%3A%2F%2Fwww.xmatters.com%2Fresources%2Freports%2Fmonitoring-connected-enterprise%3Futm_campaign%3D70138000001C2pDAAS%26utm_source%3Ddzon%26utm_medium%3Dweb%26utm_content%3D3-steps-to-monitoring-in-a-connected-enterprise-wp). Check out [xMatters](https://dzone.com/go?i=283437&u=https%3A%2F%2Fwww.xmatters.com%2Fsolutions%2Fmanagement%3Futm_campaign%3D70138000001C2tKAAS%26utm_source%3Ddzon%26utm_medium%3Dweb%26utm_content%3Dxmatters-website).

Topics:

performance ,testing ,infrastructure ,validation ,routes ,network ,components
