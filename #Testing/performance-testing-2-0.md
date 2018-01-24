# Performance Testing 2.0

_Captured: 2017-12-06 at 20:09 from [dzone.com](https://dzone.com/articles/performance-testing-20?edition=343098&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-06)_

Gone are the days when the applications one encountered were massive and N-tiered architecture based. Most of the applications today are massive alright, but they are all based on microservice architecture, built using Agile and Lean methodology. The pros are faster turnaround times, the product can be tweaked (noticed I say tweaked and not changed) during the build phase, QA happens almost in parallel to dev, and defects are found much earlier. All of this sounds good on paper, but if it is not properly implemented and co-ordinated, the whole thing will crumble like a sand castle hit by the first wave.

Of all the various challenges faced by the QA team, this article focuses on the challenges of performance testing such an application and the steps taken to transform performance testing 1.0 to 2.0. The very first question is what the heck is this performance testing 2.0?

In a traditional performance testing lifecycle (which would follow a traditional testing lifecycle) the requirements are gathered, the objective identified, a plan is penned down, scripts developed, data created and a couple of rounds of execution. If the project has enough budget and time left out, the dev team will help in fixing the top 2 performance issue and the application goes into UAT and production. The main difference in performance testing 2.0 is the rate at which things move. It is the same set of activities which need to be performed on the application but at a much quicker pace. No one has the time to take 2 days for data preparation and smoke testing, 1 full day for executing and load test for 6 hours and then 1-2 days for result collation and analysis. Everyone wants the results yesterday.

Below are steps which we had taken in the project to ensure that performance testing was transformed for the new age

## Performance From the Ground Up

Non-functional attributes have to be incorporated for a user story. Rather than simply ask what the user should do, the PT architect embedded with the team asked questions like how much time the user will wait for a response. How many concurrent connections are expected? Will this component be hosted on an independent server or will it be co-hosted with other components? From our experience, most of the time none of the teams were aware of how to answer these questions. The business simply wanted a fast application, but they could not break it down at such a granular level. One way we overcame this issue was by running a stand-alone baseline test on the component.

## Scripting

Any half decent product owner or scrum master will want performance testing for each and every sprint. Since most of the applications are built on microservices, the communication protocol is web services, REST services or message based. In the project, we relied on HP LoadRunner for scripting and execution

  * For the web services & REST based communication, we have no issues as they were either 1 request or a couple of requests which were easily scripted and parameterized. Once the dev team created an XSD it was simple job of making a script out of it
  * Message-based communication was a bit more complex. We had to get a sample message and then ported it to LoadRunner. Scripts were made in the Java Vuser protocol. Eventually, it became too tedious to port the message to the LR script. Eventually, we wrote an Excel utility which would port the message into LR script, i.e. it would add a double quote at the start and end of a line, put in an escape sequence for special characters, etc. Though this was a simple fix, it saved us quite some time during the script phase.

## Data

This was the toughest challenge which we had to face, and to this day, it is not fully met. The key was to virtualize. Thankfully, we had the skills needed to virtualize dependant services using CA LISA. For the ones which we could not, we wrote simple stubs (a server which would return a random number for price and quantity). This approach worked very well for component level testing. For the more end to end testing, we tried to backup prod data, mask it, and then dump it in the performance test env, but that failed utterly due to various reasons. This prompted us to go through the round-about way of pushing the data from the front end and moving it along to various states. Though this took some time to set up and run, it was well worth the time spent. For one, it ensured that the data integrity was maintained. And, since we had set up virtualization for the component tests, we did not need all the components in the ready state before we ran a test.

## Execution

Some of the tests were manually triggered and some were scheduled via Jenkins. There were a total of six dev teams working on various components. They were using Jenkins, Maven, and Ant to build and deploy the code. We were given a hook into their pipeline and linked performance Center with Jenkins. Below is the flow chart we followed for running a load test after every major deployment:

![Image title](https://dzone.com/storage/temp/7347163-devops1.jpg)

> _Image title_

Using Jenkins saved quite some time in either helping understand what went wrong, or passing a build with a successful run without waste of time. There was an ongoing piece of work to integrate all testing activity in a sequence starting all the way from deploying a build in the dev env, run smoke test, run an automation script pack and if everything was successful, execute a PT regression pack.

![Image title](https://dzone.com/storage/temp/7347187-devops2.jpg)

> _Image title_

The actions to take were straightforward, either sending an email or extracting the log files into a path or restarting the application. It was determining the metrics to be measured which deemed a test as a "PASS" or "FAIL." To help this activity the dev team created health check pages which displayed version numbers and deployed dates. They also logged in specific strings om the log file which would ensure that the deployment was a success.

## Analysis

We did have access to HP Performance View and AppDynamics to peek under the hood during a performance test, but the choicest data was always hidden away under a ton of log. We tried to pull logs after the test and parse them after each round, but that was ineffective. Finally, we got fed up and wrote a custom log parser which pulled in data we needed from the log file and loaded it into ElasticDB. We connected this database to Grafana and rendered the data in glorious color.

After all of this you may ask, "So whats new? You are still gathering requirements, creating scripting, manufacturing data, running tests and analyzing results? Where is the performance testing 2.0?" To that question, I answer "It's everywhere." The core of performance testing has not changed (and I don't think it will change for some time). It is the way we do performance testing which has changed. The majority of the steps which we had automated used to be done manually, be it deployment or data creation or even simply smoke testing. All of it has to be done by someone. Now it's all rule driven. That's performance testing 2.0.

P.S. - Setting up such a sequence is not the end of the line for things to do. Given the constraints, this was one of the ways which suited everybody's needs. This can be (and possibly will be) tweaked as new technology emerges and new challenges arise. As "Mad Eye" Moody from Harry Potter put it, "constant vigilance."

Opinions expressed by DZone contributors are their own.
