# Modeling Performance Tests

_Captured: 2018-03-16 at 13:16 from [dzone.com](https://dzone.com/articles/modeling-performance-tests?edition=368203&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-03-16)_

Maintain Application Performance with real-time monitoring and instrumentation for any application. [Learn More!](https://dzone.com/go?i=281422&u=https%3A%2F%2Fwww.nastel.com%2Fapplication-performance-monitoring%2F%3Futm_source%3DDZone%26utm_medium%3DPrePostRoll%26utm_campaign%3DDZone2018%2520for%2520all%2520pre%2Fpost-roll%2520text%2520ads%3A)

The objective of [load testing](https://www.neotys.com/insights/load-testing) is to simulate realistic user activity on the application. If a non-representative user journey is used, or if the appropriate load policy is undefined, the behavior of the app under load will not be able to be properly validated. **Modeling Performance tests** doesn't require a technical skill set, just the time to fully understand the ins and outs of the application:

  * How users work on the system; their habits.
  * When/where/how often they're using the application?
  * Is there any relation between external events and activity peaks?
  * Is the company business plan related to application activity?
  * Is the user community going to expand in different geographies?
  * Is there a marketing plan focused on app promotion? If yes, who is the audience?
  * Are there any layers of architecture shared with other systems?

To fully understand the application during **performance modeling**, the following roles should be involved:

  * Functional Architect
  * Business Analyst(s)
  * Project Leader

Of course, having different functional representation will provide varied feedback. The goal should be to understand the application, the end users' habits, and the relation of the application to the current/future state of the organization.

System logs or database extractions can also be useful. These easily point out the main components and functional areas currently used in production. Also, they will retrieve the number of transactions/hour per business process.

  * When considering the user load, it is important to be aware of the difference between the number of concurrent users and the number of users within the expected audience. An application delivered to 5,000 users may only have 500 users accessing it simultaneously.
  * If there isn't any estimation on the maximum concurrent user volume, the number of users can be calculated based on the number of transactions/hour per business actions.

## Establish Service Level Agreements (SLAs) and Service Level Objectives (SLOs)

Service Level Agreements and Service Level Objectives are the keys to [automation](https://www.neotys.com/blog/automation-across-the-full-performance-testing-cycle-better-user-experience-for-them-speedier-release-time-for-you/) and [performance validation](https://www.neotys.com/solutions/continuous-performance-validation). The project leader and functional architect need to define ideal response times for the application as there are no standards to leverage.

SLAs/SLOs enable the Performance Engineer to provide a [performance testing](https://www.neotys.com/insights/performance-testing) results status perspective. With these, performance testing can be easily automated to identify performance regression between several releases of the application.

If the importance of [component testing](https://www.neotys.com/blog/shifting-left-with-api-load-testing-and-component-testing-webinar/) and performance testing in an early project stage is properly understood, the component level SLA or SLO must be defined to enable successful automation.

## Test Selection

Each test run will address one risk--status on the performance requirements.

Most projects only focus on reaching an application's limit. This is important to validate sizing and architecture configuration. However, it most likely will not answer all of the performance requirements.

There are other tests that need to run properly to qualify app performance. These tests will help validate performance requirements:

![](https://www.neotys.com/blog/wp-content/uploads/2018/01/Unit-test-300x150.png)

  * **Unit Test:** Many projects overlook the power of unit testing. Don't start running load tests if the performance is not acceptable with one single user. Unit testing allows the application to be instrumented with deep-dive analytics tools and provides useful information to the devs. This step should be a mandatory part of any load testing strategy.
  * **Connection Test:** Let's say that each morning, all of the application users connect to the system at roughly the same time, then grab a coffee or have a conversation with a colleague. Even if there are no major activities on the business components of the application, the architecture has to handle this peak user session scenario. It should be obvious - to ensure that the system won't break every time this happens. Lives will be much easier for the ops team members by validating this point. This test will ramp up all the expected users.
  * **Production Activity Test:** Every application has major business actions. These actions often result in data being updated or inserted into the database. Therefore, there should be a good understanding of the number of records created per day/hour. Production activity testing ensures that the system can handle the load related to the number of transactions/hour expected in production. This test will load/validate the behavior of the business components within the database. Two main requirements for this type of test include the number of transactions/hour per user journey; appropriate think times.
  * **Peak Test:** Every application experiences peak volumes. Even if those peaks appear as infrequently as once or twice a year, it is mandatory to ensure that the application can handle it. Peak testing's purpose is to simulate an important increase of users during a short period (e.g., a retail site's simulation of activity resulting from typical holiday sales frenzy).
![](https://www.neotys.com/blog/wp-content/uploads/2018/01/Peak-Test-300x200.png)

  * **Soak Test:** The application/architecture will most likely be available for several days or even weeks on end. In the absence of dedicated times set for maintenance tasks, it is important that the architecture will run without failure over a long period. Soak testing runs a constant number of users over extended timeframes. With this test practice, it will be easy to identify any memory leak/network conjunction so that you can easily monitor the stability of the environment's current configuration.
![](https://www.neotys.com/blog/wp-content/uploads/2018/01/Batch-Test-300x150.png)

Some other load tests could be utilized depending on the constraints of the business and the locations of the users. There are always events related to the company/organization that will affect the application load.

For example, the load designed for a trading application will depend on the opening hours of different markets. The app will have three typical phases: one for Asian users, a second for European users combined with additional Asian users, and the third for the U.S., which combines users from all three. Every time the markets open or close, there are peaks on trading activity. Therefore, testing would include different load types combining various business case combinations.

On the other hand, there are also tests that are designed to validate the platform availability during maintenance tasks or a production incident:

  * **Failover Test:** The purpose of this test is to simulate a production failure on the environment. This test type is mandatory to validate the availability of the environment and to make sure the failover cluster mechanism reacts properly. When the architecture has N nodes, it is important to validate that the N-1 or N-2 nodes can handle the expected load (to avoid event cascading during production issues). The ops team is probably also interested in whether they can complete their maintenance tasks without having to set the app into a maintenance state. Most high-availability applications have many nodes on different layers of the architecture: Web Servers, Application Servers, Database, etc. There should be one test/layer.
  * **Recovery Test:** The opposite of the degradation test, the recovery test is initiated by stopping one of the nodes and then restarting while the app is loaded. Its purpose is to see how the node reacts to a heavy load post-restart.

Additionally, there may be operational situations to include during the load test to measure application behavior when the cache is being cleaned.

There is yet another point that could affect the performance of the application: the data. Often when load testing a test database less data is used, or at least a DB anonymized for security purposes. The anonymous process usually creates records starting with the same letters/digit. So, all of the indexes used during the load test will be incomparable to those of the normal production database.

Data grows rapidly in production. DB behavior is quite different depending on its size. If the lifetime of the database is long, then it might make sense to validate the performance of different sized DBs to determine if there is a limit differential between a light/heavy database. To achieve this, a large dataset pointing to various areas of the database should be used (e.g., never use a list of names where all the accounts start with AA or AAA2). Instead, keep a representative set of data from A to Z.

The type and complexity of the test will change during the project lifecycle:

## Include Think Times

  * An important element of performance design, 'think time' is the time needed by a real user between two business actions: 
    * Time to read information displayed on-screen.
    * Time to fill out information in a form.
  * Other real user actions that do not cause interaction with the application servers.

Because every real-world user behaves differently, think times will always be different. Therefore, it is important:

  * To gather the think time of each business step in each scenario. Avoid using the same think time for each step. There are always screens displaying information that end users need to read or forms they need to fill out before step progression takes place. There should be a specific think time for each action.
  * To calculate the average minimum think time and the average maximum think time/action.
  * Let the load testing tool randomly choose a think time from a specified range (min and max).

Imagine the application is a castle with big walls and doors. Components that will be validated (via load testing) are inside the castle. The wall will represent proxy servers, load balancers, caching layers, firewalls, etc.

If a test is run without including think times, then only the main door would be hit. Okay, it may break, but there is a big chance that it would lock everything out after a short time. Be gentle and smart, and hide from the defense. The main door will allow entrance, and the components located inside of the castle will be able to be properly load tested.

## Validate the User Experience

As mentioned earlier, once the application is assembled, testing objectives will change. At some point, the quality of the user experience too needs validation.

Mobile applications, rich Internet applications (RIA), and complex AJAX frameworks are challenging in the way most are used to measure response times. In the past, measurements have been limited to download time and Time to first byte ( TTFB).

![](https://www.neotys.com/blog/wp-content/uploads/2018/01/Validate-User-Experience-300x171.png)

This approach does not make sense because much of the rendering time that contributes to user experience depends on local ActiveX/JavaScript or native application logic. As such, testing measurements cannot be limited to TTFB and download time because the main objective is to validate the global user experience on the application.

Measuring the user experience is possible by combining two solutions: load testing software ([NeoLoad](https://www.neotys.com/neoload/overview)) and a browser-based or mobile testing tool.

The [load testing tool](https://www.neotys.com/neoload/how-teams-use-it) will generate 98% of the load on the application. The browser-based or mobile-based testing tool will generate the other 2% of the load to retrieve the real user experience (including the rendering time) while the application is loaded.

This means that the business processes and transactions to be monitored by the browser/mobile-based solutions need to be carefully identified.

Running tests without monitoring is like watching a horror movie on the radio. You will hear people scream without knowing why. Monitoring is the only way to get metrics related to the behavior of the architecture.

However, many projects tend to lack performance monitoring due to:

  * The lack of tools.
  * The fear of the requirements needed to enable monitoring.

Though monitoring is not limited to the operating system of the different server(s), its purpose is to validate that each layer of the architecture is available and stable. Architects took time to build the smartest architecture, so it is necessary to measure the behavior of the different layers.

Monitoring allows for a more comprehensive understanding of the architecture and the investigation into the behavior of the various pieces of the environment:

  * Operating System: CPU, memory, disk, and network utilization.
  * Application Server: memory utilization, garbage collector, thread utilization, sessions.
  * Web Server: worker, number of sessions.
  * Database: buffer pool, cache utilization, number of transactions, number of commits, % indexed queries.
  * Caching Server: hit ratio.

Many projects use production monitoring tools to retrieve metrics from the architecture. This approach is not recommended since production monitoring has a large granularity between each data point (every 2-5 minutes). In load testing, it is important to have monitored data collected at least every five seconds. The Performance Engineer needs to be given every opportunity to identify bottlenecks. When a peak appears for only a few seconds during a test, it is vital to have enough granularity to point out the bottleneck.

Monitoring requires technical requirements such as a system account, which services are to be started, firewall ports to be opened, etc. Even if it seems difficult to meet those requirements, monitoring is possible if there is proper communication with operations; sending them these requirements in advance will facilitate that communication.

_**A key takeaway for monitoring:**_ Anticipate requirements at an early stage.

Collect, analyze, and visualize performance data from mobile to mainframe with AutoPilot APM. [Get a Demo!](https://dzone.com/go?i=281423&u=https%3A%2F%2Fwww.nastel.com%2Fapplication-performance-monitoring%2F%3Futm_source%3DDZone%26utm_medium%3DPrePostRoll%26utm_campaign%3DDZone2018%2520for%2520all%2520pre%2Fpost-roll%2520text%2520ads%3A)
